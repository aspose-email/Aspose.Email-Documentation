---
title: "Trabajando con propiedades de MAPI"
url: /es/python-net/working-with-mapi-properties/
weight: 60
type: docs
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

El siguiente fragmento de código muestra cómo obtener la propiedad MAPI mediante la etiqueta de propiedad MAPI.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-GetMapiProperty-GetMapiProperty.py" >}}

### **Configuración de las propiedades de MAPI**

El siguiente fragmento de código muestra cómo configurar las propiedades de MAPI.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-SetMapiProperties-SetMapiProperties.py" >}}



donde la definición del método ConvertDateTime es la siguiente:



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-ConvertDateTime-ConvertDateTime.py" >}}

## **Lectura de propiedades MAPI con nombre de archivos MSG de Outlook**

Aspose.Email proporciona un conjunto de API para trabajar con archivos MSG, incluida la extracción de propiedades MAPI con nombre.

### **Lea las propiedades de MAPI con nombre del archivo MSG**

Para leer las propiedades de MAPI con nombre, podemos usar **named_properties** propiedad del [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/#mapimessage-class) clase. El siguiente ejemplo de código muestra cómo cargar un mensaje, recuperar todas las propiedades de MAPI con nombre y recorrer cada propiedad para comprobar su valor:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("my.msg")

# Get all named MAPI properties
properties = msg.named_properties.values
# Read all properties in foreach loop
for prop in properties:
    #  Read any specific property
    if prop.descriptor.canonical_name == "PidLidSideEffects":
        print(f"{prop.descriptor.canonical_name} = {prop}")
    if prop.descriptor.canonical_name == "PidLidInternetAccountName":
        print(f"{prop.descriptor.canonical_name} = {prop}")
```

## **Lectura de una propiedad MAPI con nombre desde un archivo adjunto**

Aspose.Email permite recuperar todas las propiedades MAPI nombradas de un adjunto. El siguiente ejemplo de código muestra cómo leer las propiedades MAPI con nombre de los archivos adjuntos:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("my.msg")

# Get all named MAPI properties
attach_properties = msg.attachments[0].named_properties.values
# Read all properties in foreach loop
for prop in attach_properties:
    #  Read any specific property
    if prop.descriptor.name == "AttachmentOriginalUrl":
        print(f"{prop.descriptor.name} = {prop.get_string()}")
    if prop.descriptor.name == "AttachmentWasSavedToCloud":
        print(f"{prop.descriptor.name} = {prop.get_boolean()}")
```

## **Eliminar propiedades de mensajes y archivos adjuntos**

En este ejemplo de código se muestra la creación de un mensaje MSG de Outlook con un cuerpo y un archivo de mensaje adjunto. También muestra cómo eliminar una propiedad de datos adjuntos del mensaje creado.

```python
import aspose.email as ae

# create an MSG
msg = ae.mapi.MapiMessage("from@doamin.com", "to@domain.com", "subject", "body");
msg.set_body_content("<html><body><h1>This is the body content</h1></body></html>", ae.mapi.BodyContentType.HTML)

# load message and add it to created MSG as attachment
attachment = ae.mapi.MapiMessage.load(attach.msg")
msg.attachments.add("Outlook2 Test subject.msg", attachment)

# count of attachment properties before removal
print(f"Before removal = {msg.attachments[0].properties.count}")

# Delete anyone attachment property
msg.attachments[0].remove_property(923467779)

# count of attachment properties after removal
print(f"Before removal = {msg.attachments[0].properties.count}")
```