---
title: 'Cómo: Serializar un objeto como secuencia XML con codificación SOAP'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
ms.assetid: af406e0a-fa3a-46dd-a7ba-c80731eba3a0
ms.openlocfilehash: cdfa2c8c7a27806873217495ac09f7f20e82b6bc
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45698585"
---
# <a name="how-to-serialize-an-object-as-a-soap-encoded-xml-stream"></a>Cómo: Serializar un objeto como secuencia XML con codificación SOAP
  
 Dado que un mensaje SOAP se genera mediante XML, se puede usar la clase <xref:System.Xml.Serialization.XmlSerializer> para serializar las clases y generar mensajes SOAP codificados. El XML resultante se ajusta a la [sección 5 del documento de World Wide Web Consortium, "Protocolo simple de acceso a objetos (SOAP) 1.1"](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512). Si está creando un servicio Web XML que se comunica a través de mensajes SOAP, puede personalizar la secuencia XML aplicando un conjunto de atributos SOAP especiales a las clases y miembros de clases. Para obtener más información, vea [Atributos que controlan la serialización SOAP codificada](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).  
  
### <a name="to-serialize-an-object-as-a-soap-encoded-xml-stream"></a>Para serializar un objeto como secuencia XML con codificación SOAP  
  
1.  Cree la clase mediante la [herramienta de definición de esquema XML (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).  
  
2.  Aplique uno o más de los atributos especiales situados en `System.Xml.Serialization`. Vea la lista en "Atributos que controlan la serialización SOAP codificada".  
  
3.  Cree `XmlTypeMapping` creando un nuevo `SoapReflectionImporter`e invocando el método `ImportTypeMapping` con el tipo de la clase serializada.  
  
     En el ejemplo de código siguiente se llama al método `ImportTypeMapping` de la clase `SoapReflectionImporter` para crear `XmlTypeMapping`.  
  
    ```vb  
    ' Serializes a class named Group as a SOAP message.  
    Dim myTypeMapping As XmlTypeMapping =
        New SoapReflectionImporter().ImportTypeMapping(GetType(Group))  
    ```  
  
    ```csharp  
    // Serializes a class named Group as a SOAP message.  
    XmlTypeMapping myTypeMapping =
        new SoapReflectionImporter().ImportTypeMapping(typeof(Group));
    ```  
  
4.  Cree una instancia de la clase `XmlSerializer` pasando `XmlTypeMapping` al constructor <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29>.  
  
    ```vb  
    Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
    ```  
  
    ```csharp  
    XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
    ```  
  
5.  Llame al método `Serialize` o `Deserialize`.  
  
## <a name="example"></a>Ejemplo  
  
```vb  
' Serializes a class named Group as a SOAP message.  
Dim myTypeMapping As XmlTypeMapping =
    New SoapReflectionImporter().ImportTypeMapping(GetType(Group))
Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
```  
  
```csharp  
// Serializes a class named Group as a SOAP message.  
XmlTypeMapping myTypeMapping =
    new SoapReflectionImporter().ImportTypeMapping(typeof(Group));
XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
```  
  
## <a name="see-also"></a>Vea también

- [Serialización SOAP y XML](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
- [Atributos que controlan la serialización SOAP codificada](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)  
- [Serialización XML con servicios web XML](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)  
- [Cómo: Serializar un objeto](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
- [Cómo: Deserializar un objeto](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
- [Cómo: Invalidar la serialización XML SOAP codificada](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)
