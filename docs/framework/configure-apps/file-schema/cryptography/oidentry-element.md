---
title: '&lt;oidEntry&gt; elemento'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap/oidEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidEntry
helpviewer_keywords:
- <oidEntry> element
- oidEntry element
ms.assetid: 22fb88b0-bf27-489c-9ca0-e65950ac136c
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 1729ad4d07fdc0d3dbb31c2bfc29edce647373d4
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2018
ms.locfileid: "50193661"
---
# <a name="ltoidentrygt-element"></a>&lt;oidEntry&gt; elemento
Asigna un identificador de objeto (OID) ASN.1 a un nombre descriptivo.  
  
 \<configuration>  
\<mscorlib >  
\<cryptographySettings >  
\<oidMap >  
\<oidEntry >  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|**OID**|Atributo necesario.<br /><br /> Especifica el OID ASN.1 correspondiente al algoritmo implementado por la clase.|  
|**name**|Atributo necesario.<br /><br /> Especifica el valor de la **nombre** atributo en el [ \<nameEntry >](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) etiqueta.|  
  
### <a name="child-elements"></a>Elementos secundarios  
 Ninguno.  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|`configuration`|Elemento raíz de cada archivo de configuración usado por las aplicaciones de Common Language Runtime y .NET Framework.|  
|`cryptographySettings`|Contiene la configuración de criptografía.|  
|`mscorlib`|Contiene el `cryptographySettings` elemento.|  
|`oidMap`|Contiene asignaciones de identificador (OID) de objeto ASN.1 a clases.|  
  
## <a name="remarks"></a>Comentarios  
 Los identificadores de objeto ASN.1 identifican algoritmos en algunos formatos criptográficos. Los identificadores de objetos se asignan a nombres descriptivos para los algoritmos que desea identificar.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo usar el  **\<oidEntry >** elemento para asignar un identificador de objeto para el algoritmo de hash RIPEMD-160 a una implementación del algoritmo hash.  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RIPEMD-160" class="MyCrypto"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a>Vea también  
- [Esquema de los archivos de configuración](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [Esquema de la configuración de criptografía](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
- [Cryptographic Services](../../../../../docs/standard/security/cryptographic-services.md)  
- [Configurar clases de criptografía](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)  
- [Asignar identificadores de objeto a algoritmos de criptografía](../../../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)
