---
title: "UI Automation Support for the TitleBar Control Type | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "control types, Title Bar"
  - "Title Bar control type"
  - "UI Automation, Title Bar control type"
ms.assetid: 3b7a4e13-0305-45d5-bc33-1f4133c50782
caps.latest.revision: 21
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 21
---
# UI Automation Support for the TitleBar Control Type
> [!NOTE]
>  Esta documentación está dirigida a los desarrolladores de .NET Framework que quieran usar las clases [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] administradas definidas en el espacio de nombres <xref:System.Windows.Automation>. Para ver la información más reciente acerca de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: automatización de la interfaz de usuario](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 En este tema se ofrece información sobre la compatibilidad de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] con el tipo de control TitleBar. En [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], un tipo de control es un conjunto de condiciones que un control debe cumplir para poder usar la propiedad <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>. Entre las condiciones se incluyen instrucciones específicas para la estructura de árbol [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], valores de propiedad [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] y patrones de control.  
  
 Los controles de barra de título representan títulos o barras de título de una ventana.  
  
 En las secciones siguientes se definen la estructura de árbol [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] necesaria, las propiedades, los patrones de control y los eventos para el tipo de control TitleBar. Los requisitos [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] se aplican a todos los controles de barra de título, ya sean [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] o [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## Estructura de árbol de automatización de interfaz de usuario necesaria  
 En la tabla siguiente se describe la vista de control y la vista de contenido del árbol [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] que pertenece a los controles de barra de título y se describe lo que puede incluirse en cada vista. Para más información sobre el árbol [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], vea [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Vista de control|Vista de contenido|  
|----------------------|------------------------|  
|TitleBar<br /><br /> -   Menú \(0 o 1\)<br />-   Botón \(0 o más\)|No es aplicable. \(el control de barra de título no tiene contenido.\)|  
  
<a name="Required_UI_Automation_Properties"></a>   
## Propiedades necesarias para la automatización de la interfaz de usuario  
 En la tabla siguiente se muestran las propiedades [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] cuyo valor o definición es especialmente relevante para los controles TitleBar. Para más información sobre propiedades [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], vea [UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|Propiedad [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Valor|Notas|  
|-------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Vea las notas.|El valor de esta propiedad debe ser único en todos los controles de una aplicación.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Vea las notas.|El rectángulo delimitador de una barra de título debe abarcar todos los controles que incluye.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Vea las notas.|Se admite si hay un rectángulo delimitador. Si no todos los puntos que se encuentran dentro del rectángulo delimitador son seleccionables, y realiza pruebas de aciertos especializadas, invalide y ofrezca un punto en el que hacer clic.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|False|Las barras de título nunca tienen enfoque de teclado.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|""|La barra de título no es contenido; su información de texto se expone en la ventana primaria.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Vea las notas.|Normalmente, el control de barra de título no tiene una etiqueta.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|TitleBar|Este valor es el mismo para todos los marcos de trabajo de la interfaz de usuario.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"barra de título"|Cadena localizada que corresponde al tipo de control TitleBar.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|False|El control de barra de título nunca es contenido.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|El control de barra de título siempre debe ser un control.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Depende|Este control devolverá un valor dependiendo de si la barra de título está visible en la pantalla.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|""|No es necesario exponer el texto de ayuda.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>|""|Las barras de título nunca tienen teclas de aceleración.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AccessKeyProperty>|""|El control de barra de título no tiene una clave de acceso.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## Patrones de control necesarios para la automatización de la interfaz de usuario  
 El tipo de control TitleBar no debe admitir ningún patrón de control. Su funcionalidad se expone a través del patrón de control Window en el control Window.  
  
## Eventos de automatización de la interfaz de usuario necesarios  
 En la tabla siguiente se muestran los eventos [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] que se deben admitir por todos los controles de barra de título. Para más información sobre eventos, vea [UI Automation Events Overview](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|Evento [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Compatibilidad|Notas|  
|----------------------------------------------------------------------------------|--------------------|-----------|  
|Evento cambiado por propiedad <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.|Obligatorio|Ninguna|  
|Evento cambiado por propiedad <xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>.|Obligatorio|Ninguna|  
|Evento cambiado por propiedad <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>.|Never|Ninguna|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Nunca|Ninguna|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Requerido|Ninguna|  
  
## Vea también  
 <xref:System.Windows.Automation.ControlType.TitleBar>   
 [UI Automation Control Types Overview](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)   
 [UI Automation Overview](../../../docs/framework/ui-automation/ui-automation-overview.md)