---
title: 'Cómo: Utilizar componentes que admitan el modelo asincrónico basado en eventos'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 35e9549c-1568-4768-ad07-17cc6dff11e1
ms.openlocfilehash: e11bf8af6f56cbdcdcc920cafe145edcf744efed
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46003404"
---
# <a name="how-to-use-components-that-support-the-event-based-asynchronous-pattern"></a>Cómo: Utilizar componentes que admitan el modelo asincrónico basado en eventos
Muchos componentes le ofrecen la opción de realizar su trabajo de forma asincrónica. Por ejemplo, los componentes <xref:System.Media.SoundPlayer> y <xref:System.Windows.Forms.PictureBox> permiten cargas sonidos e imágenes "en segundo plano" mientras el subproceso principal continúa ejecutándose sin interrupción.  
  
 Usar métodos asincrónicos en una clase que admite la [Información general sobre el modelo asincrónico basado en eventos](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md) puede ser tan sencillo como adjuntar un controlador de eventos al evento _MethodName_**Completed** del componente, como lo haría para cualquier otro evento. Cuando se llama al método _MethodName_**Async**, la aplicación continuará ejecutándose sin interrupción hasta que se genere el evento _MethodName_**Completed**. En el controlador de eventos, puede examinar el parámetro <xref:System.ComponentModel.AsyncCompletedEventArgs> para determinar si la operación asincrónica se completó correctamente o si se canceló.  
  
 Para más información sobre el uso de los controladores de eventos, vea [Información general sobre controladores de eventos](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).  
  
 En el siguiente procedimiento se explica cómo usar la funcionalidad de carga de imágenes asincrónica de un control <xref:System.Windows.Forms.PictureBox>.  
  
### <a name="to-enable-a-picturebox-control-to-asynchronously-load-an-image"></a>Para permitir que un control PictureBox cargue una imagen de manera asincrónica  
  
1.  Cree una instancia del componente <xref:System.Windows.Forms.PictureBox> en el formulario.  
  
2.  Asigne un controlador de eventos al evento <xref:System.Windows.Forms.PictureBox.LoadCompleted>.  
  
     Compruebe si hay errores que puedan haberse producido durante la descarga asincrónica aquí. También es donde puede comprobar posibles cancelaciones.  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#2)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#5)]  
  
3.  Agregue dos botones, denominados `loadButton` y `cancelLoadButton`, al formulario. Agregue los controladores de eventos <xref:System.Windows.Forms.Control.Click> para iniciar y cancelar la descarga.  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#4)]  
  
4.  Ejecute la aplicación.  
  
     Mientras se realiza la descarga de la imagen, puede mover libremente el formulario, minimizarlo y maximizarlo.  
  
## <a name="see-also"></a>Vea también

- [Ejecutar una operación en segundo plano](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
- [Información general sobre el modelo asincrónico basado en eventos](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
