---
title: -nologo (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: 21c708ef632cc0ed923713cd49e22d44848b4db3
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2018
ms.locfileid: "52297236"
---
# <a name="-nologo-visual-basic"></a>-nologo (Visual Basic)
Suprime la presentación de la pancarta de copyright y mensajes informativos durante la compilación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
-nologo  
```  
  
## <a name="remarks"></a>Comentarios  
 Si especifica `-nologo`, el compilador no mostrará un aviso de copyright. De forma predeterminada, `-nologo` no está en vigor.  
  
> [!NOTE]
>  El `-nologo` opción no está disponible en el entorno de desarrollo de Visual Studio; está disponible solo cuando se compila desde la línea de comandos.  
  
## <a name="example"></a>Ejemplo  
 El siguiente código compila `T2.vb` y no se muestra un aviso de copyright.  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a>Vea también  
 [Compilador de línea de comandos de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Líneas de comandos de compilación de ejemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
