---
title: "Trabajando con Propiedades MAPI usando la Biblioteca de Correo C++"
description: "Usando la API de la Biblioteca de Correo C++, puedes acceder y establecer propiedades MAPI de Outlook y leer Propiedades MAPI Nombradas de archivos MSG."
url: /es/cpp/working-with-mapi-properties/
weight: 60
type: docs
linktitle: "Trabajando con Propiedades MAPI"
---

## **Accediendo y Estableciendo Propiedades MAPI de Outlook**
La clase MapiProperty representa una propiedad MAPI, que contiene:

- Nombre: una cadena que representa el nombre de la propiedad.
- Etiqueta: un largo que representa la etiqueta de la propiedad.
- Datos: un arreglo de bytes que representa los datos de la propiedad.

### **Obteniendo la Propiedad MAPI usando la Etiqueta de Propiedad MAPI**
Para obtener propiedades MAPI:

1. Crea una instancia de MapiMessage cargando desde archivos o flujo.
1. Obtén el MapiProperty de MapiMessage.Properties mediante las claves MapiPropertyTag.
1. Obtén los Datos del MapiProperty mediante el método GetX.

El siguiente fragmento de código te muestra cómo obtener la propiedad MAPI usando la etiqueta de propiedad MAPI con la Biblioteca de Análisis de Correo C++.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-GetMAPIProperty-GetMAPIProperty.cpp" >}}

### **Estableciendo Propiedades MAPI**
El siguiente fragmento de código te muestra cómo establecer propiedades MAPI.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SetMAPIProperties-SetMAPIProperties.cpp" >}}

donde la definición del método convertDateTime es la siguiente:

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

## **Leyendo Propiedades MAPI Nombradas de Archivos MSG de Outlook**
Microsoft Outlook admite la adición de propiedades MAPI nombradas a un archivo MSG. Estas propiedades MAPI nombradas son agregadas por el usuario. Puedes agregar una propiedad nombrada, por ejemplo “MyProp”, a un archivo MSG usando Aspose.Email. Este artículo ilustra las capacidades de Aspose.Email para:

- Leer Propiedades MAPI Nombradas de un archivo MSG de Outlook
- Leer Propiedades de Archivos Adjuntos
- Eliminar Propiedades de MSGs y Archivos Adjuntos

### **Leer Propiedades MAPI Nombradas de un archivo MSG**
El siguiente fragmento de código te muestra cómo leer propiedades MAPI nombradas de un archivo MSG.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadNamedMAPIProperties-ReadNamedMAPIProperties.cpp" >}}

### **Leyendo la Propiedad MAPI Nombrada de un Archivo Adjunto**
Aspose.Email también te permite recorrer las propiedades de un MapiAttachment y buscar una propiedad nombrada, de manera similar al ejemplo anterior, para MapiMessage. El siguiente fragmento de código te muestra cómo buscar una propiedad nombrada a través de la colección de propiedades del adjunto.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadingNamedMAPIPropertyFromAttachment-ReadingNamedMAPIPropertyFromAttachment.cpp" >}}

### **Eliminar Propiedades de MSGs y Archivos Adjuntos**
El siguiente fragmento de código te muestra cómo eliminar propiedades de MSGs y adjuntos.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-RemovePropertiesFromMSGAndAttachments-RemovePropertiesFromMSGAndAttachments.cpp" >}}