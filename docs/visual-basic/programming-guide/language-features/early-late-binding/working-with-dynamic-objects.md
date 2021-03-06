---
title: Trabajar con objetos dinámicos (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
ms.openlocfilehash: 78b17a379ea219cc24842322703caaa9d29eeb2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647354"
---
# <a name="working-with-dynamic-objects-visual-basic"></a>Trabajar con objetos dinámicos (Visual Basic)
Objetos dinámicos proporcionan otro mecanismo, excepto el `Object` tipo en tiempo de ejecución y enlazarlo a un objeto en tiempo de ejecución. Un objeto dinámico expone miembros, como propiedades y métodos en tiempo de ejecución usando interfaces dinámicas que se definen en el <xref:System.Dynamic> espacio de nombres. Puede utilizar las clases en el <xref:System.Dynamic> espacio de nombres para crear objetos que trabajar con estructuras de datos que no coincide con un tipo o formato estático. También puede usar los objetos dinámicos que se definen en lenguajes dinámicos, como IronPython e IronRuby. Para obtener ejemplos que muestran cómo crear objetos dinámicos o utilizar un objeto dinámico definido en un lenguaje dinámico, vea [Tutorial: crear y utilizar objetos dinámicos](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>, o <xref:System.Dynamic.ExpandoObject>.  
  
 Visual Basic se enlaza a los objetos en el tiempo de ejecución de lenguaje dinámico y lenguajes dinámicos, como IronPython e IronRuby mediante el <xref:System.Dynamic.IDynamicMetaObjectProvider> interfaz. Algunos ejemplos de clases que implementan la `IDynamicMetaObjectProvider` interfaz son el <xref:System.Dynamic.DynamicObject> y <xref:System.Dynamic.ExpandoObject> clases.  
  
 Si se realiza una llamada enlazada en tiempo de ejecución de ejecución a un objeto que implementa la `IDynamicMetaObjectProvider` de la interfaz, Visual Basic se enlaza al objeto dinámico mediante esa interfaz. Si se realiza una llamada en tiempo de ejecución a un objeto que no implementa la `IDynamicMetaObjectProvider` interfaz, o si la llamada a la `IDynamicMetaObjectProvider` se produce un error en la interfaz, Visual Basic se enlaza al objeto utilizando las capacidades de enlace en tiempo de ejecución de Visual Basic.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Dynamic.DynamicObject>  
 <xref:System.Dynamic.ExpandoObject>  
 [Walkthrough: Creating and Using Dynamic Objects](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md) (Tutorial: Crear y usar objetos dinámicos [C# y Visual Basic])  
 [Enlace en tiempo de compilación y en tiempo de ejecución](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
