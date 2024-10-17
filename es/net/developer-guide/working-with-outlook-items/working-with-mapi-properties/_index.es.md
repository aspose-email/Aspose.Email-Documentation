---
title: "Trabajando con propiedades MAPI"
url: /es/net/working-with-mapi-properties/
weight: 70
type: docs
---

## **Acceso y Configuración de Propiedades MAPI de Outlook**

La clase [MapiProperty](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/) representa una propiedad MAPI, que contiene:

- [Nombre](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/name/): una cadena que representa la propiedad del nombre.
- [Etiqueta](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/tag/): un valor de tipo largo que representa la propiedad de la etiqueta.
- [Datos](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/data/): una matriz de bytes que representa la propiedad de datos.
  
### **Obteniendo Propiedades MAPI utilizando la Etiqueta de Propiedad MAPI**

Para obtener propiedades MAPI:

1. Cree una instancia de [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) al [cargar desde archivos o flujo](https://docs.aspose.com/email/es/net/loading-viewing-and-parsing-msg-file/#loading-from-stream).
2. Obtenga la [MapiProperty](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/) del [MapiMessage.Properties](https://reference.aspose.com/email/net/aspose.email.mapi/mapiproperty/) mediante las claves de [MapiPropertyTag](https://reference.aspose.com/email/net/aspose.email.mapi/mapipropertytag/).

El siguiente fragmento de código muestra cómo obtener la propiedad MAPI utilizando la etiqueta de propiedad MAPI.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-GetMAPIProperty-GetMAPIProperty.cs" >}}

### **Configurando Propiedades MAPI**

El siguiente fragmento de código muestra cómo establecer propiedades MAPI.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetMAPIProperties-SetMAPIProperties.cs" >}}

donde la definición del método convertDateTime es la siguiente:

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetMAPIProperties-ConvertDateTime.cs" >}}

### **Algunas Propiedades Adicionales**

El siguiente fragmento de código muestra cómo establecer propiedades MAPI adicionales.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetAdditionalMAPIProperties-SetAdditionalMAPIProperties.cs" >}}

## **Lectura de Propiedades MAPI Nombradas desde Archivos MSG de Outlook**

Microsoft Outlook admite la adición de propiedades MAPI nombradas a un archivo MSG. Estas propiedades MAPI nombradas son agregadas por el usuario. Puedes agregar una propiedad nombrada, por ejemplo, "MyProp", a un archivo MSG utilizando Aspose.Email. Este artículo ilustra las capacidades de Aspose.Email para:

- [**Acceso y Configuración de Propiedades MAPI de Outlook**](#accessing-and-setting-outlook-mapi-property)
  - [**Obteniendo Propiedades MAPI utilizando la Etiqueta de Propiedad MAPI**](#getting-mapi-property-using-the-mapi-property-tag)
  - [**Configurando Propiedades MAPI**](#setting-mapi-properties)
  - [**Algunas Propiedades Adicionales**](#some-additional-properties)
- [**Lectura de Propiedades MAPI Nombradas desde Archivos MSG de Outlook**](#reading-named-mapi-properties-from-outlook-msg-files)
  - [**Leer Propiedades MAPI Nombradas desde un archivo MSG**](#read-named-mapi-properties-from-msg-file)
  - [**Lectura de Propiedad MAPI Nombrada desde un Adjunto**](#reading-named-mapi-property-from-attachment)
  - [**Eliminar Propiedades de MSG y Adjuntos**](#remove-properties-from-msgs-and-attachments)
  
### **Leer Propiedades MAPI Nombradas desde un archivo MSG**

El siguiente fragmento de código muestra cómo leer propiedades MAPI nombradas desde el archivo MSG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadNamedMAPIProperties-ReadNamedMAPIProperties.cs" >}}

### **Lectura de Propiedad MAPI Nombrada desde un Adjunto**

Aspose.Email también te permite recorrer las propiedades de un [MapiAttachment](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachment/) y buscar una propiedad nombrada, de una manera similar al ejemplo anterior, para [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/). El siguiente fragmento de código muestra cómo buscar una propiedad nombrada a través de la colección de propiedades del adjunto.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadingNamedMAPIPropertyFromAttachment-ReadingNamedMAPIPropertyFromAttachment.cs" >}}

### **Eliminar Propiedades de MSG y Adjuntos**

El siguiente fragmento de código muestra cómo eliminar propiedades de MSG y adjuntos.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-RemovePropertiesFromMSGAndAttachments-RemovePropertiesFromMSGAndAttachments.cs" >}}