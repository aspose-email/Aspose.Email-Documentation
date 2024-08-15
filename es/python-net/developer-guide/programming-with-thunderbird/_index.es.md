---
title: "Programación con Thunderbird"
url: /es/python-net/programming-with-thunderbird/
weight: 80
type: docs
---


## **Lectura de mensajes**
Mozilla Thunderbird es un cliente de correo electrónico multiplataforma de código abierto, desarrollado por la Fundación Mozilla. Almacena los correos electrónicos en su propia estructura de archivos y administra los índices y subcarpetas de los mensajes a través de formatos de archivo propietarios. Aspose.Email puede funcionar con las estructuras de almacenamiento de correo de Thunderbird. La clase mboxRDStorageReader permite a los desarrolladores leer los mensajes del archivo de almacenamiento de correo de Mozilla Thunderbird. En este artículo se muestra cómo leer los mensajes del almacenamiento de correo electrónico de Thunderbird:

1. Abre el archivo de almacenamiento de Thunderbird
1. Cree una instancia de la clase mboxRDStorageReader y pase la secuencia anterior al constructor.
1. Llama a read_next_message () para recibir el primer mensaje.
1. Usa el mismo read_next_message () en un bucle while para leer todos los mensajes.
1. Cierra todos los canales.

El siguiente fragmento de código muestra cómo leer todos los mensajes de un almacenamiento de correo de Thunderbird.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-Thunderbird-ReadMessagesFromThunderbird-ReadMessagesFromThunderbird.py" >}}

### **Recuperar las propiedades del mensaje**

Para leer y recuperar información de un archivo Mbox, Aspose.Email proporciona [MboxStorageReader](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) clase para crear un objeto lector para el archivo Mbox y el [MboxLoadOptions](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxloadoptions/#mboxloadoptions-class) clase para cargar el archivo. Las siguientes propiedades del [MboxMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxmessageinfo/#mboxmessageinfo-class) la clase se puede usar para acceder y mostrar detalles específicos del mensaje:

- 'fecha': obtiene la fecha del mensaje.
- 'from_address': obtiene la dirección de origen.
- 'asunto': obtiene el asunto del mensaje.
- 'to': obtiene la colección de direcciones que contiene los destinatarios del mensaje.
- 'cc': obtiene la colección de direcciones que contiene los destinatarios de CC.
- 'bcc': obtiene la colección de direcciones que contiene los destinatarios BCC del mensaje.

El siguiente ejemplo de código muestra el uso de estas propiedades para leer y extraer la información de los mensajes de un archivo Mbox:

```py
import aspose.email as ae

reader = ae.storage.mbox.MboxStorageReader.create_reader(file_name, ae.storage.mbox.MboxLoadOptions())

for mbox_message_info in reader.enumerate_message_info():
    print(f"Subject: {mbox_message_info.subject}")
    print(f"Date: {mbox_message_info.date}")
    print(f"From: {mbox_message_info.from_address}")
    print(f"To: {mbox_message_info.to}")
    print(f"CC: {mbox_message_info.cc}")
    print(f"Bcc: {mbox_message_info.bcc}")
```
### **Extraer mensajes de MBOX mediante identificadores**

Para leer los mensajes de un archivo MBOX, Aspose.Email proporciona el método 'create_reader () 'del [MboxStorageReader](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) clase para crear un objeto lector para el archivo. Toma el nombre del archivo y [MboxLoadOptions](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxloadoptions/#mboxloadoptions-class) como argumentos, lo que permite al usuario cargar el archivo MBOX con opciones específicas si es necesario.

Para extraer los mensajes, se utilizan los siguientes métodos y propiedades:

- método 'enumerate_message_info () 'del [MboxStorageReader](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) class: recorre en iteración cada mensaje del archivo MBOX.
- método 'extract_message ()» del [MboxStorageReader](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) class: extrae cada mensaje por su ID de entrada.
- propiedad 'entry_id' del [MboxMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxmessageinfo/#mboxmessageinfo-class) class: obtiene el identificador de entrada.

Por último, el mensaje se convierte a un formato EML mediante [EmlLoadOptions](https://reference.aspose.com/email/python-net/aspose.email/emlloadoptions/#emlloadoptions-class).

El ejemplo de código siguiente muestra el uso de estas funciones para leer y extraer mensajes de un archivo MBOX:

```py
import aspose.email as ae

reader = ae.storage.mbox.MboxStorageReader.create_reader("my.mbox", ae.storage.mbox.MboxLoadOptions())

for mbox_message_info in reader.enumerate_message_info():
    eml = reader.extract_message(mbox_message_info.entry_id, ae.EmlLoadOptions())

```
### **Configuración de las opciones de carga al leer mensajes de MBOX**

Con Aspose.Email [EmlLoadOptions](https://reference.aspose.com/email/python-net/aspose.email/emlloadoptions/#emlloadoptions-class) clase, puede especificar opciones adicionales al cargar MailMessage desde el formato Eml. Por ejemplo, puedes configurar una opción para conservar los archivos adjuntos de TNEF al cargar un archivo EML con la propiedad 'preserve_tnef_attachments' del [EmlLoadOptions](https://reference.aspose.com/email/python-net/aspose.email/emlloadoptions/#emlloadoptions-class) class.

Puede leer el siguiente mensaje de correo electrónico del archivo mbox mediante las opciones de carga especificadas con el método 'read_next_message' del [MboxStorageReader](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) clase y convierta el archivo a formato PST con el método 'mbox_to_pst' del [MailStorageConverter](https://reference.aspose.com/email/python-net/aspose.email.storage/mailstorageconverter/#mailstorageconverter-class) clase.

El ejemplo de código siguiente muestra el uso de estos métodos y propiedades para trabajar con archivos de almacenamiento de correo electrónico, incluida la lectura de mensajes en formato mbox, la conservación de los archivos adjuntos TNEF y la conversión de mensajes del formato mbox al formato pst:

```py
import aspose.email as ae

reader = ae.storage.mbox.MboxrdStorageReader(fileName, ae.storage.mbox.MboxLoadOptions())
# Read messages preserving tnef attachments.
load_options = ae.EmlLoadOptions()
load_options.preserve_tnef_attachments = True
eml = reader.read_next_message(load_options)
ae.storage.MailStorageConverter.MboxMessageOptions(load_options)
# Convert messages from mbox to pst preserving tnef attachments.
pst = ae.storage.MailStorageConverter.mbox_to_pst("Input.mbox", "Output.pst")
```
### **Configuración de la codificación de texto preferida al cargar archivos Mbox para su lectura**

Puede especificar la codificación de texto que se utilizará al cargar un archivo MBOX. La propiedad 'preferred_text_encoding' está disponible para [MboxLoadOptions](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxloadoptions/#mboxloadoptions-class) La clase establece una opción adicional y garantiza que un mensaje con el contenido codificado se lea y procese correctamente.

El siguiente fragmento de código muestra cómo usar esta función en un proyecto:

```py
import aspose.email as ae

load_options = ae.storage.mbox.MboxLoadOptions()
load_options.preferred_text_encoding = 'utf-8'
reader = ae.storage.mbox.MboxrdStorageReader("sample.mbox", load_options)
message = reader.read_next_message()
```
### **Conversión de MBOX a PST Conservar o eliminar una firma**

Para eliminar la firma de un archivo durante el proceso de conversión, establezca la propiedad mboxTopstConversionOptions.remove_signature en true.

El siguiente ejemplo de código muestra cómo utilizar esta propiedad:
```py
import aspose.email as ae

personalStorage = ae.storage.pst.PersonalStorage.create("target.pst", ae.storage.pst.FileFormatVersion.UNICODE)
conversion_options = ae.storage.MboxToPstConversionOptions()
conversion_options.remove_signature = True
ae.storage.MailStorageConverter.mbox_to_pst( ae.storage.mbox.MboxrdStorageReader("source.mbox", ae.storage.mbox.MboxLoadOptions()), personalStorage, "Inbox", conversion_options)
```

## **Redacción de mensajes**
La clase mboxRDStorageWriter ofrece la posibilidad de escribir nuevos mensajes en el archivo de almacenamiento de correo de Thunderbird. Para escribir mensajes:

1. Abre el archivo de almacenamiento de Thunderbird en FileStream.
1. Cree una instancia de la clase mboxRDStorageWriter y pase la secuencia anterior al constructor.
1. Prepara un mensaje nuevo con la clase MailMessage.
1. Llama al método write_message () y pasa la instancia de MailMessage anterior para añadir el mensaje al almacenamiento de Thunderbird.
1. Cierra todas las transmisiones.

El siguiente fragmento de código muestra cómo escribir mensajes en el almacenamiento de correo de Thunderbird.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-Thunderbird-CreateNewMessagesToThunderbird-CreateNewMessagesToThunderbird.py" >}}
## **Obtener el número total de mensajes del archivo MBox**
La clase mboxRDStorageReader permite leer el número de elementos disponibles en un archivo mBox. Esto se puede usar para desarrollar aplicaciones que muestren el progreso de la actividad mientras se procesa un archivo de este tipo.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-Thunderbird-GetNumberOfItemsFromMBox-GetNumberOfItemsFromMBox.py" >}}
## **Obtener el tamaño actual del mensaje**
{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-Thunderbird-GetCurrentMessageSize-GetCurrentMessageSize.py" >}}
