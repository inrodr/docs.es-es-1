---
title: Tipos de datos básicos
ms.date: 03/30/2017
ms.assetid: eca2c472-9548-4800-bd31-5d8d9f11752b
ms.openlocfilehash: 977f99f129d591898953ed24ad5acdaa3ae9a88a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365998"
---
# <a name="basic-data-types"></a>Tipos de datos básicos
Como las consultas de LINQ to SQL se convierten a Transact-SQL antes de ejecutarlas en Microsoft SQL Server, LINQ to SQL admite una funcionalidad muy similar a la integrada en SQL Server para los tipos de datos básicos.  
  
## <a name="casting"></a>Convertir  
 Se habilitan las conversiones implícitas o explícitas de tipos CLR de origen a tipos CLR de destino si hay una conversión similar válida en SQL Server. Para obtener más información acerca de la conversión de CLR, vea [CType (función)](~/docs/visual-basic/language-reference/functions/ctype-function.md) (Visual Basic) y [como](~/docs/csharp/language-reference/keywords/as.md). Después de la conversión, las conversiones de tipos cambian el comportamiento de las operaciones realizadas en una expresión CLR para coincidir con el comportamiento de otras expresiones CLR que tienen una asignación natural al tipo de destino. Las conversiones de tipos también se pueden convertir en el contexto de la asignación de herencia. Los tipos de los objetos se pueden convertir a subtipos de entidad más específicos de forma que se pueda tener acceso a los datos específicos de su subtipo.  
  
## <a name="equality-operators"></a>Operadores de igualdad  
 LINQ to SQL admite los siguientes operadores de igualdad en los tipos de datos básicos dentro de las consultas de LINQ to SQL:  
  
-   Operador de igualdad y desigualdad: se admiten operadores de igualdad y desigualdad para los tipos numéricos <xref:System.Boolean>, <xref:System.DateTime> y <xref:System.TimeSpan>. Para obtener más información acerca de los operadores de Visual Basic `=` y `<>`, consulte [operadores de comparación](~/docs/visual-basic/language-reference/operators/comparison-operators.md). Para obtener más información acerca de los operadores de comparación de C# `==` y `!=`, consulte [== (operador)](~/docs/csharp/language-reference/operators/equality-comparison-operator.md) y [! = (operador)](~/docs/csharp/language-reference/operators/not-equal-operator.md), respectivamente  
  
-   Operador Is: el operador `IS` tiene un equivalente compatible cuando se utiliza la asignación de herencia. Se puede utilizar en lugar de probar directamente la columna discriminadora para determinar si un objeto es de un tipo de entidad concreto, y se convierte en una marca de verificación en la columna discriminadora. Para obtener más información acerca de los operadores de Visual Basic y C# es, consulte [operador Is](~/docs/visual-basic/language-reference/operators/is-operator.md) y [es](~/docs/csharp/language-reference/keywords/is.md).  
  
## <a name="see-also"></a>Vea también  
 [Asignación de tipos entre CLR y SQL](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)  
 [Tipos de datos y funciones](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
