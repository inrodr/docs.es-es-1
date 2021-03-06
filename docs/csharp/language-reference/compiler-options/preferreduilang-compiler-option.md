---
title: -preferreduilang (Opciones del compilador de C#)
ms.date: 07/20/2015
f1_keywords:
- /preferreduilang
helpviewer_keywords:
- preferreduilang compiler option [C#]
- /preferreduilang compiler option [C#]
- -preferreduilang compiler option [C#]
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
ms.openlocfilehash: a1fbbb8415e5e3405f039489aa071b0624065a9d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43530148"
---
# <a name="-preferreduilang-c-compiler-options"></a>-preferreduilang (Opciones del compilador de C#)
Mediante la opción del compilador `-preferreduilang`, puede especificar el idioma en el que el compilador de C# muestra el resultado, como los mensajes de error.  
  
## <a name="syntax"></a>Sintaxis  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a>Argumentos  
 `language`  
 El [nombre del idioma](/windows/desktop/Intl/language-names) del idioma que se va a usar para los resultados del compilador.  
  
## <a name="remarks"></a>Comentarios  
 Puede usar la opción del compilador `-preferreduilang` para especificar el idioma que quiere que use el compilador de C# para los mensajes de error y otros resultados de la línea de comandos. Si el paquete de idioma para el idioma no está instalado, se usa la configuración del idioma del sistema operativo en su lugar, y no se notifica ningún error.  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a>Requisitos  
  
## <a name="see-also"></a>Vea también

- [Opciones del compilador de C#](../../../csharp/language-reference/compiler-options/index.md)
