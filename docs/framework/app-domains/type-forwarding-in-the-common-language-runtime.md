---
title: Reenvío de tipos en Common Language Runtime
ms.date: 03/30/2017
dev_langs:
- csharp
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ad6c87dcec55a332bced00370fe6ea888508793
ms.sourcegitcommit: 5fd80619c760fa8c25d33a6f5661247cb65da465
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2018
ms.locfileid: "50744379"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a>Reenvío de tipos en Common Language Runtime
El reenvío de tipos le permite mover un tipo a otro ensamblado sin tener que volver a compilar las aplicaciones que utilizan el ensamblado original.  
  
 Por ejemplo, suponga que una aplicación utiliza la clase `Example` en un ensamblado denominado `Utility.dll`. Los desarrolladores de `Utility.dll` podrían decidir refactorizar el ensamblado y, en el proceso, podrían mover la clase `Example` a otro ensamblado. Si la versión anterior de `Utility.dll` se reemplaza por la nueva versión de `Utility.dll` y su ensamblado complementario, la aplicación que usa la clase `Example` produce un error porque no se puede encontrar la clase `Example` en la nueva versión de `Utility.dll`.  
  
 Los desarrolladores de `Utility.dll` pueden evitarlo mediante el reenvío de las solicitudes a la clase `Example` con el uso del atributo <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>. Si se ha aplicado el atributo a la nueva versión de `Utility.dll`, las solicitudes para la clase `Example` se reenvían al ensamblado que contiene la clase. La aplicación existente continuará funcionando normalmente, sin necesidad de volver a compilarla.  
  
> [!NOTE]
>  En la versión 2.0 de .NET Framework, no se pueden reenviar tipos desde ensamblados escritos en Visual Basic. Sin embargo, una aplicación escrita en Visual Basic puede utilizar tipos reenviados. Es decir, si la aplicación utiliza un ensamblado codificado en C# o C++ y se reenvía un tipo de ese ensamblado a otro ensamblado, la aplicación de Visual Basic puede utilizar el tipo reenviado.  
  
## <a name="forwarding-types"></a>Reenvío de tipos  
 Hay cuatro pasos para reenviar un tipo:  
  
1.  Traslade el código fuente del tipo desde el ensamblado original al ensamblado de destino.  
  
2.  En el ensamblado en el que solía estar ubicado el tipo, agregue un atributo <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> para el tipo que se ha movido. El código siguiente muestra el atributo para un tipo denominado `Example` que se ha movido.  
  
    ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
    ```  
  
    ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
    ```  
  
3.  Compile el ensamblado que contiene el tipo ahora.  
  
4.  Vuelva a compilar el ensamblado donde se encontraba antes el tipo, con una referencia al ensamblado que contiene el tipo ahora. Por ejemplo, si está compilando un archivo de C# desde la línea de comandos, utilice la opción [/reference (opciones del compilador de C#)](~/docs/csharp/language-reference/compiler-options/reference-compiler-option.md) para especificar el ensamblado que contiene el tipo. En C++, utilice la directiva [#using](/cpp/preprocessor/hash-using-directive-cpp) en el archivo de código fuente para especificar el ensamblado que contiene el tipo.  
  
## <a name="see-also"></a>Vea también  
- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>  
- [Reenvío de tipos (C++/CLI)](/cpp/windows/type-forwarding-cpp-cli)  
- [#using (directiva)](/cpp/preprocessor/hash-using-directive-cpp)
