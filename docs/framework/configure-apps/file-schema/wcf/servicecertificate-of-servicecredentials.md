---
title: Elemento &lt;serviceCertificate&gt; de &lt;serviceCredentials&gt;
ms.date: 03/30/2017
ms.assetid: 597ae6d5-4938-4950-9f5e-b2280e816182
ms.openlocfilehash: 3bd6d392b15c37e22fd2a3639c99396e0e3d1749
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750874"
---
# <a name="ltservicecertificategt-of-ltservicecredentialsgt"></a>Elemento &lt;serviceCertificate&gt; de &lt;serviceCredentials&gt;
Especifique un certificado X.509 que se vaya a utilizar para autenticar el servicio a los clientes utilizando el modo de seguridad de mensajes.  
  
 \<system.ServiceModel>  
\<comportamientos >  
\<serviceBehaviors >  
\<comportamiento >  
\<serviceCredentials >  
\<serviceCertificate >  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
<serviceCertificate findValue="String"   
    storeLocation="LocalMachine/CurrentUser"  
    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`findValue`|Una cadena que contiene el valor que se va a buscar en el almacén de certificados X.509. El tipo contenido en el atributo debe satisfacer los requisitos del X509FindType especificado. El valor predeterminado es una cadena vacía.|  
|`storeLocation`|Especifica la ubicación del almacén de certificados X.509 que el cliente utiliza para validar el certificado del servidor. Los valores válidos son los siguientes:<br /><br /> -LocalMachine: el almacén de certificados asignado al equipo local.<br />-CurrentUser: el almacén de certificados asignado al usuario actual.<br /><br /> El valor predeterminado es LocalMachine.|  
|`storeName`|Especifica el nombre del almacén del certificado X.509 que se va a abrir. Los valores válidos son los siguientes:<br /><br /> -AddressBook: Almacén de certificados para otros usuarios.<br />-AuthRoot: Almacén de certificados para entidades de certificación (CA) de terceros.<br />-CertificatAuthority: Almacén de certificados para entidades de certificación intermedias (CA).<br />-Disallowed: Almacén de certificados para certificados revocados.<br />-My: Almacén de certificados para los certificados personales.<br />-Root: Almacén de certificados para entidades de certificación raíz de confianza (CA).<br />-TrustedPeople: Almacén de certificados para las personas de confianza directa y recursos.<br />-TrustedPublisher: Almacén de certificados para publicadores de confianza directa.<br /><br /> El valor predeterminado es My.|  
|`x509FindType`|Define el tipo de búsqueda de X.509 que se va a ejecutar. Los valores válidos son los siguientes:<br /><br /> -FindByThumbprint<br />-FindBySubjectName<br />-FindBySubjectDistinguishedName<br />-FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-FindByTimeValid<br />-   FindByTimeNotYetValid<br />-FindByTemplateName<br />-FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-FindByKeyUsage<br />-FindBySubjectKeyIdentifier<br /><br /> El tipo contenido en el atributo `findValue` debe satisfacer los requisitos del X509FindType especificado.<br /><br /> El valor predeterminado es FindBySubjectDistinguishedName.|  
  
### <a name="child-elements"></a>Elementos secundarios  
 Ninguna  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[\<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Especifica la credencial que se va a utilizar para autenticar el servicio y los valores relacionados con la validación de la credencial del cliente.|  
  
## <a name="remarks"></a>Comentarios  
 Utilice este elemento para especificar un certificado X.509 que se utilizará para autenticar el servicio a los clientes utilizando el modo de seguridad de mensajes. Si está utilizando un certificado que se renovará periódicamente, su huella digital cambiará. En ese caso, utilice el nombre del asunto como el `x509FindType` porque el certificado se puede volver a emitir con el mismo nombre de asunto.  
  
 Para obtener más información acerca de cómo utilizar el elemento, consulte [Cómo: especificar valores de credencial de cliente](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
## <a name="see-also"></a>Vea también  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ServiceCertificate%2A>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>  
 <xref:System.ServiceModel.Description.ServiceCredentials.ServiceCertificate%2A>  
 [Cómo especificar los valores de credenciales de cliente](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)  
 [Comportamientos de seguridad](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
