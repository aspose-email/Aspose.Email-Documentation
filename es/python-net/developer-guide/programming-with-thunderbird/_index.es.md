---
title: "Programación con Thunderbird"
url: /es/python-net/programming-with-thunderbird/
weight: 80
type: docs
---

## **Lectura de Mensajes**
Mozilla Thunderbird es un cliente de correo electrónico de código abierto y multiplataforma, desarrollado por la Fundación Mozilla. Almacena correos electrónicos en su propia estructura de archivos, gestionando índices de mensajes y subcarpetas a través de formatos de archivo propietarios. Aspose.Email puede trabajar con estructuras de almacenamiento de correo de Thunderbird. La clase MboxrdStorageReader permite a los desarrolladores leer mensajes del archivo de almacenamiento de correo de Mozilla Thunderbird. Este artículo muestra cómo leer los mensajes del almacenamiento de correo de Thunderbird:

1. Abrir el archivo de almacenamiento de Thunderbird
1. Crear una instancia de la clase MboxrdStorageReader y pasar el flujo anterior al constructor.
1. Llamar a read_next_message() para obtener el primer mensaje.
1. Usar el mismo read_next_message() en un bucle while para leer todos los mensajes.
1. Cerrar todos los flujos.

El siguiente fragmento de código muestra cómo leer todos los mensajes de un almacenamiento de correo de Thunderbird.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-Thunderbird-ReadMessagesFromThunderbird-ReadMessagesFromThunderbird.py" >}}

### **Recuperar propiedades del mensaje**

Para leer y recuperar información de un archivo Mbox, Aspose.Email proporciona la clase [MboxStorageReader](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) para crear un objeto lector para el archivo Mbox y la clase [MboxLoadOptions](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxloadoptions/#mboxloadoptions-class) para cargar el archivo. Las siguientes propiedades de la clase [MboxMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxmessageinfo/#mboxmessageinfo-class) pueden usarse para acceder y mostrar detalles específicos del mensaje:

- 'date' - Obtiene la fecha del mensaje.
- 'from_address' - Obtiene la dirección de origen.
- 'subject' - Obtiene el asunto del mensaje.
- 'to' - Obtiene la colección de direcciones que contiene a los destinatarios del mensaje.
- 'cc' - Obtiene la colección de direcciones que contiene a los destinatarios en copia (CC).
- 'bcc' - Obtiene la colección de direcciones que contiene a los destinatarios en copia oculta (BCC) del mensaje.

El siguiente ejemplo de código demuestra el uso de estas propiedades para leer y extraer información del mensaje de un archivo Mbox:

```py
import aspose.email as ae

reader = ae.storage.mbox.MboxStorageReader.create_reader(file_name, ae.storage.mbox.MboxLoadOptions())

for mbox_message_info in reader.enumerate_message_info():
    print(f"Asunto: {mbox_message_info.subject}")
    print(f"Fecha: {mbox_message_info.date}")
    print(f"De: {mbox_message_info.from_address}")
    print(f"Para: {mbox_message_info.to}")
    print(f"CC: {mbox_message_info.cc}")
    print(f"Bcc: {mbox_message_info.bcc}")
```
### **Extraer Mensajes de MBOX por Identificadores**

Para leer mensajes de un archivo MBOX, Aspose.Email proporciona el método 'create_reader()' de la clase [MboxStorageReader](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) para crear un objeto lector para el archivo. Toma el nombre del archivo y [MboxLoadOptions](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxloadoptions/#mboxloadoptions-class) como argumentos, permitiendo al usuario cargar el archivo MBOX con opciones específicas si es necesario.

Para extraer mensajes, se utilizan los siguientes métodos y propiedades:

- Método 'enumerate_message_info()' de la clase [MboxStorageReader](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) - Itera a través de cada mensaje en el archivo MBOX.
- Método 'extract_message()' de la clase [MboxStorageReader](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) - Extrae cada mensaje por su ID de entrada.
- Propiedad 'entry_id' de la clase [MboxMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxmessageinfo/#mboxmessageinfo-class) - Obtiene el identificador de entrada.

Finalmente, el mensaje se convierte en formato EML utilizando [EmlLoadOptions](https://reference.aspose.com/email/python-net/aspose.email/emlloadoptions/#emlloadoptions-class).

El siguiente fragmento de código demuestra el uso de estas características para leer y extraer mensajes de un archivo MBOX:

```py
import aspose.email as ae

reader = ae.storage.mbox.MboxStorageReader.create_reader("my.mbox", ae.storage.mbox.MboxLoadOptions())

for mbox_message_info in reader.enumerate_message_info():
    eml = reader.extract_message(mbox_message_info.entry_id, ae.EmlLoadOptions())
```
### **Configurando las opciones de carga al leer mensajes de MBOX**

Con la clase Aspose.Email [EmlLoadOptions](https://reference.aspose.com/email/python-net/aspose.email/emlloadoptions/#emlloadoptions-class), puedes especificar opciones adicionales al cargar MailMessage desde el formato Eml. Por ejemplo, puedes establecer una opción para preservar los archivos adjuntos TNEF al cargar un archivo EML con la propiedad 'preserve_tnef_attachments' de la clase [EmlLoadOptions](https://reference.aspose.com/email/python-net/aspose.email/emlloadoptions/#emlloadoptions-class).

Puedes leer el siguiente mensaje de correo electrónico del archivo mbox utilizando las opciones de carga especificadas con el método 'read_next_message' de la clase [MboxStorageReader](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) y convertir el archivo a formato PST con el método 'mbox_to_pst' de la clase [MailStorageConverter](https://reference.aspose.com/email/python-net/aspose.email.storage/mailstorageconverter/#mailstorageconverter-class).

El siguiente fragmento de código demuestra el uso de estos métodos y propiedades para trabajar con archivos de almacenamiento de correos electrónicos, incluyendo la lectura de mensajes desde el formato mbox, preservando los archivos adjuntos TNEF, y convirtiendo mensajes de mbox a formato pst:

```py
import aspose.email as ae

reader = ae.storage.mbox.MboxrdStorageReader(fileName, ae.storage.mbox.MboxLoadOptions())
# Leer mensajes preservando los archivos adjuntos tnef.
load_options = ae.EmlLoadOptions()
load_options.preserve_tnef_attachments = True
eml = reader.read_next_message(load_options)
ae.storage.MailStorageConverter.MboxMessageOptions(load_options)
# Convertir mensajes de mbox a pst preservando archivos adjuntos tnef.
pst = ae.storage.MailStorageConverter.mbox_to_pst("Input.mbox", "Output.pst")
```
### **Estableciendo la Codificación de Texto Preferida al Cargar Archivos Mbox para Lectura**

Puedes especificar la codificación de texto que se utilizará al cargar un archivo MBOX. La propiedad 'preferred_text_encoding' disponible para la clase [MboxLoadOptions](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxloadoptions/#mboxloadoptions-class) establece una opción adicional y asegura que un mensaje con contenido codificado sea leído y procesado correctamente.

El siguiente fragmento de código muestra cómo utilizar esta característica en un proyecto:

```py
import aspose.email as ae

load_options = ae.storage.mbox.MboxLoadOptions()
load_options.preferred_text_encoding = 'utf-8'
reader = ae.storage.mbox.MboxrdStorageReader("sample.mbox", load_options)
message = reader.read_next_message()
```
### **Convertir MBOX a PST Preservando o Eliminando una Firma**

Para eliminar la firma de un archivo durante el proceso de conversión, establece la propiedad MboxToPstConversionOptions.remove_signature en true.

El siguiente ejemplo de código muestra cómo utilizar esta propiedad:
```py
import aspose.email as ae

personalStorage = ae.storage.pst.PersonalStorage.create("target.pst", ae.storage.pst.FileFormatVersion.UNICODE)
conversion_options = ae.storage.MboxToPstConversionOptions()
conversion_options.remove_signature = True
ae.storage.MailStorageConverter.mbox_to_pst( ae.storage.mbox.MboxrdStorageReader("source.mbox", ae.storage.mbox.MboxLoadOptions()), personalStorage, "Inbox", conversion_options)
```

## **Escribiendo Mensajes**
La clase MboxrdStorageWriter proporciona la facilidad de escribir nuevos mensajes en el archivo de almacenamiento de correo de Thunderbird. Para escribir mensajes:

1. Abrir el archivo de almacenamiento de Thunderbird en FileStream.
1. Crear una instancia de la clase MboxrdStorageWriter y pasar el flujo anterior al constructor.
1. Preparar un nuevo mensaje utilizando la clase MailMessage.
1. Llamar al método write_message() y pasar la instancia de MailMessage anterior para agregar el mensaje al almacenamiento de Thunderbird.
1. Cerrar todos los flujos.

El siguiente fragmento de código muestra cómo escribir mensajes en el almacenamiento de correo de Thunderbird.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-Thunderbird-CreateNewMessagesToThunderbird-CreateNewMessagesToThunderbird.py" >}}
## **Obtener el Número Total de Mensajes desde un Archivo MBox**
La clase MboxrdStorageReader proporciona la capacidad de leer el número de elementos disponibles en un archivo MBox. Esto se puede utilizar para desarrollar aplicaciones que muestren el progreso de la actividad al procesar dicho archivo.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-Thunderbird-GetNumberOfItemsFromMBox-GetNumberOfItemsFromMBox.py" >}}
## **Obtener el Tamaño del Mensaje Actual**
{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-Thunderbird-GetCurrentMessageSize-GetCurrentMessageSize.py" >}}