---
title: 'Cómo: Animar un control Popup'
ms.date: 03/30/2017
helpviewer_keywords:
- Popup control [WPF], animating
- animation [WPF], Popup controls
ms.assetid: acaa2a0a-6137-4efd-9cd1-75ece222e390
ms.openlocfilehash: 05b84eea7fe983340ebb8c5cdb20ff39eb2f0858
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553759"
---
# <a name="how-to-animate-a-popup"></a>Cómo: Animar un control Popup
Este ejemplo muestra dos maneras de animar un <xref:System.Windows.Controls.Primitives.Popup> control.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente se establece la <xref:System.Windows.Controls.Primitives.PopupAnimation> en un valor de <xref:System.Windows.Controls.Primitives.PopupAnimation.Slide>, lo que hace que la <xref:System.Windows.Controls.Primitives.Popup> en "presentación" cuando aparezca.  
  
 Para girar el <xref:System.Windows.Controls.Primitives.Popup>, este ejemplo se asigna un <xref:System.Windows.Media.RotateTransform> a la <xref:System.Windows.UIElement.RenderTransform%2A> propiedad en el <xref:System.Windows.Controls.Canvas>, que es el elemento secundario de la <xref:System.Windows.Controls.Primitives.Popup>.  
  
 Para que la transformación funcione correctamente, debe establecer en el ejemplo el <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> propiedad `true`. Además, el <xref:System.Windows.FrameworkElement.Margin%2A> en el <xref:System.Windows.Controls.Canvas> contenido debe especificar el suficiente espacio para el <xref:System.Windows.Controls.Primitives.Popup> va a girar.  
  
 [!code-xaml[AnimatedPopup#RotateTransform2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform2)]  
  
 El siguiente ejemplo se muestra cómo un <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento, que se produce cuando un <xref:System.Windows.Controls.Button> se hace clic, desencadenadores el <xref:System.Windows.Media.Animation.Storyboard> que comienza la animación.  
  
 [!code-xaml[AnimatedPopup#RotateTransform1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform1)]  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Windows.UIElement.RenderTransform%2A>  
 <xref:System.Windows.Controls.Primitives.BulletDecorator>  
 <xref:System.Windows.Media.RotateTransform>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 <xref:System.Windows.Controls.Primitives.Popup>  
 [Temas "Cómo..."](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)  
 [Información general sobre el control Popup](../../../../docs/framework/wpf/controls/popup-overview.md)
