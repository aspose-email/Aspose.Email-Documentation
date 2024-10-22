---
title: "Trabajando con Propiedades MAPI"
url: /es/python-net/working-with-mapi-properties/
weight: 60
type: docs
---


## **Accediendo y Estableciendo Propiedades MAPI de Outlook**

La clase MapiProperty representa una propiedad MAPI, que contiene:

- Nombre: una cadena que representa el nombre de la propiedad.
- Etiqueta: un largo que representa la etiqueta de la propiedad.
- Datos: un arreglo de bytes que representa los datos de la propiedad.

### **Obteniendo Propiedad MAPI usando la Etiqueta de Propiedad MAPI**

Para obtener propiedades MAPI:

1. Crea una instancia de MapiMessage cargando desde archivos o transmisión.
1. Obtén el MapiProperty de MapiMessage.Properties mediante las claves MapiPropertyTag.
1. Obtén los Datos del MapiProperty mediante el método GetX.

El siguiente fragmento de código muestra cómo obtener la propiedad MAPI usando la etiqueta de propiedad MAPI.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-GetMapiProperty-GetMapiProperty.py" >}}

### **Estableciendo Propiedades MAPI**

El siguiente fragmento de código muestra cómo establecer propiedades MAPI.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-SetMapiProperties-SetMapiProperties.py" >}}



donde la definición del método convertDateTime es la siguiente:



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-ConvertDateTime-ConvertDateTime.py" >}}

## **Leyendo Propiedades MAPI Nombradas desde Archivos MSG de Outlook**

Aspose.Email proporciona un conjunto de API para trabajar con archivos MSG, incluyendo la extracción de propiedades MAPI nombradas.

### **Leer Propiedades MAPI Nombradas desde un archivo MSG**

Para leer propiedades MAPI nombradas, podemos usar la propiedad **named_properties** de la clase [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/#mapimessage-class). El siguiente ejemplo de código muestra cómo cargar un mensaje, recuperar todas las propiedades MAPI nombradas, iterar sobre cada propiedad para verificar su valor:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("my.msg")

# Obtener todas las propiedades MAPI nombradas
properties = msg.named_properties.values
# Leer todas las propiedades en un bucle foreach
for prop in properties:
    # Leer cualquier propiedad específica
    if prop.descriptor.canonical_name == "PidLidSideEffects":
        print(f"{prop.descriptor.canonical_name} = {prop}")
    if prop.descriptor.canonical_name == "PidLidInternetAccountName":
        print(f"{prop.descriptor.canonical_name} = {prop}")
```

## **Leyendo Propiedad MAPI Nombrada desde un Adjunto**

Aspose.Email hace posible recuperar todas las propiedades MAPI nombradas de un adjunto. El siguiente ejemplo de código muestra cómo leer propiedades MAPI nombradas desde adjuntos:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("my.msg")

# Obtener todas las propiedades MAPI nombradas
attach_properties = msg.attachments[0].named_properties.values
# Leer todas las propiedades en un bucle foreach
for prop in attach_properties:
    # Leer cualquier propiedad específica
    if prop.descriptor.name == "AttachmentOriginalUrl":
        print(f"{prop.descriptor.name} = {prop.get_string()}")
    if prop.descriptor.name == "AttachmentWasSavedToCloud":
        print(f"{prop.descriptor.name} = {prop.get_boolean()}")
```

## **Eliminar Propiedades de MSGs y Adjuntos**

Este ejemplo de código demuestra la creación de un mensaje de Outlook MSG con un contenido en el cuerpo y un archivo de mensaje adjunto. También muestra cómo eliminar una propiedad de adjunto del mensaje creado.

```python
import aspose.email as ae

# crear un MSG
msg = ae.mapi.MapiMessage("from@doamin.com", "to@domain.com", "subject", "body");
msg.set_body_content("<html><body><h1>Este es el contenido del cuerpo</h1></body></html>", ae.mapi.BodyContentType.HTML)

# cargar el mensaje y agregarlo al MSG creado como adjunto
attachment = ae.mapi.MapiMessage.load("attach.msg")
msg.attachments.add("Outlook2 Test subject.msg", attachment)

# cantidad de propiedades de adjunto antes de la eliminación
print(f"Antes de la eliminación = {msg.attachments[0].properties.count}")

# Eliminar cualquier propiedad de adjunto
msg.attachments[0].remove_property(923467779)

# cantidad de propiedades de adjunto después de la eliminación
print(f"Después de la eliminación = {msg.attachments[0].properties.count}")
```