---
title: Delete (función) (referencia de API no administrada)
description: La función de eliminación elimina la propiedad especificada y todas sus calificadores de una definición de clase CIM.
ms.date: 11/06/2017
api_name:
- Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Delete
helpviewer_keywords:
- Delete function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 791e75aa60fd651dde1555339e31664a3523e1eb
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2018
ms.locfileid: "46578923"
---
# <a name="delete-function"></a>Delete (función)
Elimina la propiedad especificada y todas sus calificadores de una definición de clase CIM.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT Delete (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName 
); 
```  

## <a name="parameters"></a>Parámetros

`vFunc`  
[in] Este parámetro se usa.

`ptr`  
[in] Un puntero a un [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instancia.

`wszName`  
[in] El nombre de la propiedad que se va a eliminar. `wszName` debe ser un puntero a una `LPCWSTR`.

## <a name="return-value"></a>Valor devuelto

Los siguientes valores devueltos por esta función se definen en el *WbemCli.h* archivo de encabezado, también puede definir como constantes en el código:

|Constante  |Valor  |Descripción  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0 x 80041001 | Se ha producido un error no especificado. |
| `WBEM_E_INVALID_OPERATION` | 0x80041016 | No se puede eliminar la propiedad. |
| `WBEM_E_INVALID_PARAMETER` | 0 x 80041008 | `wszzName` no es válido. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | La propiedad especificada no existe. |
| `WBEM_E_OUT_OF_MEMORY` | 0 x 80041006 | No hay memoria suficiente para completar la operación. |
| `WBEM_E_PROPAGATED_PROPERTY` | 0x8004101c | La propiedad se hereda de una clase base. |
| `WBEM_E_SYSTEM_PROPERTY` | | La propiedad es una propiedad del sistema. |
|`WBEM_S_NO_ERROR` | 0 | La llamada de función fue correcta.  |
| `WBEM_E_RESET_TO_DEFAULT` | 0x80041030 | La función eliminó un valor predeterminado de invalidación de la clase actual. El valor predeterminado para esta propiedad en la clase primaria ha sido reactiviated. | 

## <a name="remarks"></a>Comentarios

Esta función contiene una llamada a la [IWbemClassObject::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-delete) método.

## <a name="requirements"></a>Requisitos  
 **Plataformas:** Vea [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** WMINet_Utils.idl  
  
 **Versiones de .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Vea también  
[WMI y contadores de rendimiento (referencia de API no administrada)](index.md)
