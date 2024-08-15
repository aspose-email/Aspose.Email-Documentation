---
title: "Trabajar con las propiedades de MAPI mediante la biblioteca C++ de correo electrónico"
description: "Con la API de biblioteca de correo electrónico de C++, puede acceder y configurar las propiedades de MAPI de Outlook y leer las propiedades de MAPI con nombre desde el archivo MSG."
url: /es/cpp/working-with-mapi-properties/
weight: 60
type: docs
linktitle: "Trabajando con propiedades de MAPI"
---

## **Acceso y configuración de la propiedad MAPI de Outlook**
La clase MapiProperty representa una propiedad MAPI, que contiene:

- Nombre: cadena que representa el nombre de la propiedad.
- Etiqueta: un largo que representa la etiqueta de la propiedad.
- Datos: una matriz de bytes que representa los datos de la propiedad.

### **Obtener la propiedad MAPI mediante la etiqueta de propiedad MAPI**
Para obtener las propiedades de MAPI:

1. Crea una instancia de MapiMessage cargándola desde archivos o transmisiones.
1. Obtenga la propiedad MapiProperty de MapiMessage.properties mediante las claves MapiPropertyTag.
1. Obtenga los datos de MapiProperty mediante el método getX.

El siguiente fragmento de código muestra cómo obtener la propiedad MAPI mediante la etiqueta de propiedad MAPI con la biblioteca de analizadores de correo electrónico de C++.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-GetMAPIProperty-GetMAPIProperty.cpp" >}}

### **Configuración de las propiedades de MAPI**
El siguiente fragmento de código muestra cómo configurar las propiedades de MAPI.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SetMAPIProperties-SetMAPIProperties.cpp" >}}

donde la definición del método ConvertDateTime es la siguiente:

``` java

 int64_t filetime = t.ToFileTime();

System::ArrayPtr<uint8_t> d = System::MakeArray<uint8_t>(8, 0);

d[0] = (uint8_t)(filetime & 0xFF);

d[1] = (uint8_t)((filetime & 0xFF00) >> 8);

d[2] = (uint8_t)((filetime & 0xFF0000) >> 16);

d[3] = (uint8_t)((filetime & 0xFF000000) >> 24);

d[4] = (uint8_t)((filetime & 0xFF00000000) >> 32);

d[5] = (uint8_t)((filetime & 0xFF0000000000) >> 40);

d[6] = (uint8_t)((filetime & 0xFF000000000000) >> 48);

d[7] = (uint8_t)(((uint64_t)filetime & 0xFF00000000000000) >> 56);

```

## **Lectura de propiedades MAPI con nombre de archivos MSG de Outlook**
Microsoft Outlook admite la adición de propiedades MAPI con nombre a un archivo MSG. El usuario agrega estas propiedades de MAPI con nombre. Puede agregar una propiedad con nombre, por ejemplo, «MyProp», a un archivo MSG mediante Aspose.Email. Este artículo ilustra las capacidades de Aspose.Email para:

- Lea las propiedades de Nombre MAPI de un archivo MSG de Outlook
- Leer propiedades de los archivos adjuntos
- Eliminar propiedades de mensajes y archivos adjuntos

### **Lea las propiedades de MAPI con nombre del archivo MSG**
El siguiente fragmento de código muestra cómo leer las propiedades de MAPI con nombre del archivo MSG.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadNamedMAPIProperties-ReadNamedMAPIProperties.cpp" >}}

### **Lectura de una propiedad MAPI con nombre desde un archivo adjunto**
Aspose.Email también le permite recorrer las propiedades de un MapiAttachment y buscar una propiedad con nombre, de forma similar al ejemplo anterior, para mapiMessage. En el siguiente fragmento de código, se muestra cómo buscar una propiedad con nombre en la colección de propiedades del adjunto.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadingNamedMAPIPropertyFromAttachment-ReadingNamedMAPIPropertyFromAttachment.cpp" >}}

### **Eliminar propiedades de mensajes y archivos adjuntos**
El siguiente fragmento de código muestra cómo eliminar propiedades de los mensajes y los archivos adjuntos.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-RemovePropertiesFromMSGAndAttachments-RemovePropertiesFromMSGAndAttachments.cpp" >}}
