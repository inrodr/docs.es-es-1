---
title: ServiceMetadataBehavior
ms.date: 03/30/2017
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
ms.openlocfilehash: 19a04b6432f1ecc38a3b906b7e677175863134db
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188838"
---
# <a name="servicemetadatabehavior"></a>ServiceMetadataBehavior
ServiceMetadataBehavior  
  
## <a name="syntax"></a>Sintaxis  
  
```csharp
class ServiceMetadataBehavior : Behavior  
{  
  string ExternalMetadataLocation;  
  boolean HttpGetEnabled;  
  string HttpGetUrl;  
  boolean HttpsGetEnabled;  
  string HttpsGetUrl;  
};  
```  
  
## <a name="methods"></a>Métodos  
 La clase ServiceMetadataBehavior no define ningún método.  
  
## <a name="properties"></a>Propiedades  
 La clase ServiceMetadataBehavior tiene las propiedades siguientes:  
  
### <a name="externalmetadatalocation"></a>ExternalMetadataLocation  
 Tipo de datos: cadena  
  
 Tipo de acceso: solo lectura  
  
 Establece la ubicación a la que el servicio redirige las solicitudes de los metadatos.  
  
### <a name="httpgetenabled"></a>HttpGetEnabled  
 Tipo de datos: booleano  
  
 Tipo de acceso: solo lectura  
  
 Controla si el servicio publica su WSDL en la dirección controlada por el atributo `HttpGetUrl`.  
  
### <a name="httpgeturl"></a>HttpGetUrl  
 Tipo de datos: cadena  
  
 Tipo de acceso: solo lectura  
  
 Establece la ubicación en la que el WSDL del servicio se publica para la recuperación mediante HTTP.  
  
### <a name="httpsgetenabled"></a>HttpsGetEnabled  
 Tipo de datos: booleano  
  
 Tipo de acceso: solo lectura  
  
 Controla si el servicio publica su WSDL sobre HTTPS en la dirección controlada por el atributo `HttpsGetUrl`.  
  
### <a name="httpsgeturl"></a>HttpsGetUrl  
 Tipo de datos: cadena  
  
 Tipo de acceso: solo lectura  
  
 Establece la ubicación en la que el WSDL del servicio se publica para la recuperación mediante HTTPS.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Se declara en Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espacio de nombres|Se define en root\ServiceModel|  
  
## <a name="see-also"></a>Vea también  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
