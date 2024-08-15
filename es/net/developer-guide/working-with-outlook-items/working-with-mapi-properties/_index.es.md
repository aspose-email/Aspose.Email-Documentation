---
title: "Trabajando con propiedades de MAPI"
url: /es/net/working-with-mapi-properties/
weight: 70
type: docs
---


## **Acceso y configuración de la propiedad MAPI de Outlook**

The [MapiProperty](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/) la clase representa una propiedad MAPI, que contiene:

- [Name](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/name/): una cadena que representa la propiedad del nombre.
- [Tag](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/tag/): un valor de tipo largo que representa la propiedad de la etiqueta.
- [Data](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/data/): una matriz de bytes que representa la propiedad de los datos.
 
### **Obtener la propiedad MAPI mediante la etiqueta de propiedad MAPI**

Para obtener las propiedades de MAPI:

1. Crea una instancia de [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) by [cargar desde archivos o transmisiones](https://docs.aspose.com/email/es/net/loading-viewing-and-parsing-msg-file/#loading-from-stream).
2. Obtenga el [MapiProperty](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/) from [MapiMessage.Properties](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/) by [MapiPropertyTag](https://reference.aspose.com/email/net/aspose.email.mapi/mapipropertytag/) keys.

El siguiente fragmento de código muestra cómo obtener la propiedad MAPI mediante la etiqueta de propiedad MAPI.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-GetMAPIProperty-GetMAPIProperty.cs" >}}

### **Configuración de las propiedades de MAPI**

El siguiente fragmento de código muestra cómo configurar las propiedades de MAPI.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetMAPIProperties-SetMAPIProperties.cs" >}}

donde la definición del método ConvertDateTime es la siguiente:

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetMAPIProperties-ConvertDateTime.cs" >}}

### **Algunas propiedades adicionales**

El siguiente fragmento de código muestra cómo establecer propiedades MAPI adicionales.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetAdditionalMAPIProperties-SetAdditionalMAPIProperties.cs" >}}

## **Lectura de propiedades MAPI con nombre de archivos MSG de Outlook**

Microsoft Outlook admite la adición de propiedades MAPI con nombre a un archivo MSG. El usuario agrega estas propiedades de MAPI con nombre. Puede agregar una propiedad con nombre, por ejemplo, «MyProp», a un archivo MSG mediante Aspose.Email. Este artículo ilustra las capacidades de Aspose.Email para:

- [**Acceso y configuración de la propiedad MAPI de Outlook**](#accessing-and-setting-outlook-mapi-property)
  - [**Obtener la propiedad MAPI mediante la etiqueta de propiedad MAPI**](#getting-mapi-property-using-the-mapi-property-tag)
  - [**Configuración de las propiedades de MAPI**](#setting-mapi-properties)
  - [**Algunas propiedades adicionales**](#some-additional-properties)
- [**Lectura de propiedades MAPI con nombre de archivos MSG de Outlook**](#reading-named-mapi-properties-from-outlook-msg-files)
  - [**Lea las propiedades de MAPI con nombre del archivo MSG**](#read-named-mapi-properties-from-msg-file)
  - [**Lectura de una propiedad MAPI con nombre desde un archivo adjunto**](#reading-named-mapi-property-from-attachment)
  - [**Eliminar propiedades de mensajes y archivos adjuntos**](#remove-properties-from-msgs-and-attachments)
 
### **Lea las propiedades de MAPI con nombre del archivo MSG**

El siguiente fragmento de código muestra cómo leer las propiedades de MAPI con nombre del archivo MSG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadNamedMAPIProperties-ReadNamedMAPIProperties.cs" >}}

### **Lectura de una propiedad MAPI con nombre desde un archivo adjunto**

Aspose.Email también le permite recorrer las propiedades de un [MapiAttachment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachment/) y busque una propiedad con nombre, de forma similar al ejemplo anterior, para [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/). El siguiente fragmento de código muestra cómo buscar una propiedad con nombre en la colección de propiedades del archivo adjunto.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadingNamedMAPIPropertyFromAttachment-ReadingNamedMAPIPropertyFromAttachment.cs" >}}

### **Eliminar propiedades de mensajes y archivos adjuntos**

El siguiente fragmento de código muestra cómo eliminar propiedades de los mensajes y los archivos adjuntos.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-RemovePropertiesFromMSGAndAttachments-RemovePropertiesFromMSGAndAttachments.cs" >}}
