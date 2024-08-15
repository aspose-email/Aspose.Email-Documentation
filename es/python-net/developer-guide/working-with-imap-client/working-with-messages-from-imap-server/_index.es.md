---
title: "Trabajando con mensajes del servidor IMAP"
url: /es/python-net/working-with-messages-from-imap-server/
weight: 70
type: docs
---


## **Obtención de la información de identificación de los mensajes recibidos de un buzón**

Al recuperar y procesar mensajes de correo electrónico, puede obtener los detalles de los mensajes utilizando sus números de secuencia.

Las siguientes funciones se utilizan para interactuar con un buzón IMAP:

- [Aspose.Email.ImapMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapmessageinfo/#imapmessageinfo-class) clase: representa la información de identificación sobre el mensaje de un buzón.

- [Aspose.Email.ImapMessageInfo.sequence_number](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapmessageinfo/#imapmessageinfo-class) propiedad: el número de secuencia de un mensaje.

- [Aspose.Email.ImapMessageInfo.unique_id](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapmessageinfo/#imapmessageinfo-class) propiedad: el identificador único de un mensaje.


El siguiente fragmento de código muestra cómo obtener información de identificación sobre los mensajes:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

msg_infos = client.list_messages("INBOX")

for msg_info in msg_infos:
    # fetch by sequence number
    msg = client.fetch_message(msg_info.sequence_number)

    # fetch by unique id
    msg = client.fetch_message(msg_info.unique_id)
```


## **Listado de identificadores de mensajes MIME del servidor**
IMAPMessageInfo proporciona el MessageID MIME para la identificación del mensaje sin extraer el mensaje completo. En el siguiente fragmento de código, se muestra cómo incluir el MessageID MIME.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-ListingMIMEMessageIdInImapMessageInfo-ListingMIMEMessageIdInImapMessageInfo.py" >}}

## **Listado de mensajes del servidor**

El método 'list_messages' del [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) la clase obtiene una lista de todos los mensajes de la carpeta actualmente seleccionada (la «Bandeja de entrada» en este caso). Esta lista contiene objetos de metadatos de mensajes, que normalmente incluyen información como los identificadores de los mensajes, los números de secuencia, los UID y, posiblemente, datos resumidos, como las líneas de asunto o la información del remitente.

El siguiente fragmento de código muestra cómo recuperar los metadatos de los mensajes de la bandeja de entrada e imprimir el número total de mensajes que contiene:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

client.select_folder("Inbox")

messages = client.list_messages()
print(f"Total Messages: {len(messages)}")
```

## **Listar los mensajes del servidor de forma recursiva**
El protocolo IMAP admite la enumeración recursiva de los mensajes de una carpeta de buzones de correo. Esto también ayuda a enumerar los mensajes de las subcarpetas de una carpeta. En el siguiente fragmento de código, se muestra cómo enumerar los mensajes de forma recursiva.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-ListingMessagesRecursively-ListingMessagesRecursively.py" >}}

## **Listar mensajes con MultiConnection**

The [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) La clase proporciona una propiedad 'use_multi_connection' para usar múltiples conexiones para operaciones de gran carga. También puede establecer el número de conexiones en el modo de conexión múltiple mediante la propiedad 'connections_quantity'. El siguiente fragmento de código muestra el uso del modo de conexión múltiple para listar los mensajes: 

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

client.select_folder("Inbox")
client.connections_quantity = 5
client.use_multi_connection = ae.clients.MultiConnectionMode.ENABLE

message_info_col = client.list_messages(True)
```
*Tenga en cuenta que el uso de este modo no tiene por qué conducir necesariamente a un aumento del rendimiento.*

## **Recibe los mensajes en orden descendente**

La tarea se logra definiendo la configuración de paginación para la recuperación de mensajes. Para ello, utilice la propiedad 'ascending_sorting' del [PageSettings](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/pagesettings/#pagesettings-class) clase que forma parte del módulo del cliente IMAP. Establezca el atributo 'ascending_sorting' del objeto PageSettings en False. Esto indica que los mensajes se deben ordenar en orden descendente de forma predeterminada durante la recuperación. El siguiente fragmento de código muestra cómo recuperar los mensajes en orden descendente:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

page_settings = ae.clients.imap.PageSettings
page_settings.ascending_sorting = False
page_info = client.list_messages_by_page(5, page_settings)
messages = page_info.items

for message in messages:
    print(message.subject)
```

## **Recuperar mensajes del servidor y guardarlos en el disco**
La clase ImapClient puede obtener mensajes de un servidor IMAP y guardar los mensajes en formato EML en un disco local. Se requieren los siguientes pasos para guardar los mensajes en el disco:

1. Crea una instancia de la clase ImapClient.
1. Especifique el nombre de host, el nombre de usuario y la contraseña en el constructor IMAPClient.
1. Seleccione la carpeta mediante el método selectFolder ().
1. Llame al método ListMessages para obtener el objeto IMAPMessageInfoCollection.
1. Recorra la colección IMAPMessageInfoCollection, llame al método saveMessage () y proporcione la ruta de salida y el nombre del archivo.

El siguiente fragmento de código muestra cómo obtener mensajes de correo electrónico de un servidor y guardarlos.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-FetchEmailMessageFromServer-FetchEmailMessageFromServer.py" >}}
## **Guardar mensajes en formato MSG**
En el ejemplo anterior, los correos electrónicos se guardan en formato EML. Para guardar los correos electrónicos en formato MSG, es necesario llamar al método IMAPClient.fetchMessage (). Devuelve el mensaje en una instancia de la clase MailMessage. A continuación, se puede llamar al método MailMessage.save () para guardar el mensaje en MSG. El siguiente fragmento de código muestra cómo guardar mensajes en formato MSG.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-SavingMessageFromIMAPServer-SavingMessageFromIMAPServer.py" >}}

## **Obtenga mensajes por número de secuencia o identificador único**

La biblioteca le permite generar dos listas de mensajes, una que contiene los números de secuencia y otra que contiene los ID únicos de todos los mensajes de la bandeja de entrada. Para obtener mensajes del servidor IMAP mediante estos identificadores, utilice el método «fetch_messages» del [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) clase. El siguiente fragmento de código muestra cómo enumerar los mensajes por identificadores:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

# List messages
message_info_col = client.list_messages()
print("ListMessages Count:", message_info_col.count)

# Get sequence numbers and unique IDs
sequence_number_ar = [mi.sequence_number for mi in message_info_col]
unique_id_ar = [mi.unique_id for mi in message_info_col]

# Fetch messages by sequence number
fetched_messages_by_snum = client.fetch_messages(sequence_number_ar)
print("FetchMessages-sequenceNumberAr Count:", len(fetched_messages_by_snum))

# Fetch messages by UID
fetched_messages_by_uid = client.fetch_messages(unique_id_ar)
print("FetchMessages-uniqueIdAr Count:", len(fetched_messages_by_uid))
```

## **Listar mensajes con soporte de paginación**
En situaciones en las que el servidor de correo electrónico contiene una gran cantidad de mensajes en el buzón, a menudo se desea enumerar o recuperar los mensajes con soporte de paginación. El ImapClient de la API Aspose.Email te permite recuperar los mensajes del servidor con soporte de paginación.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-ListingMessagesWithPagingSupport-ListingMessagesWithPagingSupport.py" >}}

## **Listar los archivos adjuntos de los mensajes**

Para obtener información sobre los archivos adjuntos, como el nombre y el tamaño, sin obtener los datos de los archivos adjuntos, utilice los siguientes recursos de la biblioteca:

- [ImapAttachmentInfo](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapattachmentinfo/#imapattachmentinfo-class) clase: representa la información de un archivo adjunto (tamaño, nombre, tipo de medio).

- [ImapAttachmentInfoCollection](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapattachmentinfocollection/#imapattachmentinfocollection-class) class: representa la colección de [ImapAttachmentInfo](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapattachmentinfo/#imapattachmentinfo-class).

- '`list_attachments(sequence_number)`'método del [`ImapClient`](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class: obtiene un iterable o una colección de información adjunta para el mensaje.

```py
# List messages
message_info_col = client.list_messages()

# Iterate through each message
for message_info in message_info_col:
    print(f"Attachments for message with sequence number {message_info.sequence_number}:")

    # List attachments for the current message
    attachment_info_col = client.list_attachments(message_info.sequence_number)

    # Iterate through each attachment
    for attachment_info in attachment_info_col:
        print(f"Attachment: {attachment_info.name} (size: {attachment_info.size})")
```
## **Obtener carpetas y leer mensajes de forma recursiva**

[ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) usa el método recursivo para enumerar las carpetas y subcarpetas del servidor IMAP. El mismo método también se usa para leer y guardar mensajes en el disco local en formato MSG. Las carpetas y los mensajes se crean y guardan en la misma estructura jerárquica que en el servidor IMAP. El siguiente fragmento de código muestra cómo obtener carpetas y mensajes de forma recursiva:

```py
import aspose.email as ae
import os

# Recursive method to get messages from folders and sub-folders
def list_messages_in_folder(folder_info, root_folder, client):
    # Create the folder on disk (same name as on the IMAP server)
    current_folder = os.path.join(root_folder, folder_info.name)
    os.makedirs(current_folder, exist_ok=True)

    # Read the messages from the current folder, if it is selectable
    if folder_info.selectable:
        # Send a status command to get folder info
        folder_info_status = client.get_folder_info(folder_info.name)
        print(
            f"{folder_info_status.name} folder selected. New messages: {folder_info_status.new_message_count}, "
            f"Total messages: {folder_info_status.total_message_count}"
        )

        # Select the current folder and list messages
        client.select_folder(folder_info.name)
        msg_info_coll = client.list_messages()
        print("Listing messages....")
        for msg_info in msg_info_coll:
            # Get subject and other properties of the message
            print("Subject:", msg_info.subject)
            print(
                f"Read: {msg_info.is_read}, Recent: {msg_info.recent}, Answered: {msg_info.answered}"
            )

            # Get rid of characters like ? and :, which should not be included in a file name
            # Save the message in MSG format
            file_name = (
                msg_info.subject.replace(":", " ").replace("?", " ")
                + "-"
                + str(msg_info.sequence_number)
                + ".msg"
            )
            msg = client.fetch_message(msg_info.sequence_number)
            msg.save(
                os.path.join(current_folder, file_name),
                ae.SaveOptions.default_msg_unicode,
            )
        print("============================\n")
    else:
        print(f"{folder_info.name} is not selectable.")

    try:
        # If this folder has sub-folders, call this method recursively to get messages
        folder_info_collection = client.list_folders(folder_info.name)
        for subfolder_info in folder_info_collection:
            list_messages_in_folder(subfolder_info, root_folder, client)
    except Exception:
        pass



client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

try:
    # The root folder (which will be created on disk) consists of host and username
    root_folder = f"{client.host}-{client.username}"

    # Create the root folder and list all the folders from the IMAP server
    os.makedirs(root_folder, exist_ok=True)
    folder_info_collection = client.list_folders()
    for folder_info in folder_info_collection:
        # Call the recursive method to read messages and get sub-folders
        list_messages_in_folder(folder_info, root_folder, client)
except Exception as ex:
        print("\n", ex)

print("\nDownloaded messages recursively from IMAP server.")
```


## **Recuperación de parámetros adicionales como información resumida**


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-RetreiveExtraParametersAsSummaryInformation-RetreiveExtraParametersAsSummaryInformation.py" >}}

## **Obtener información sobre el encabezado de la lista para cancelar la suscripción**

El encabezado «ListUnsubscribe» se incluye comúnmente en los encabezados de los mensajes de correo electrónico enviados por listas de correo o sistemas de correo electrónico automatizados. Proporciona un enlace o una dirección de correo electrónico que los destinatarios pueden usar para darse de baja de la lista de correo o de los correos electrónicos automatizados. Aspose.Email proporciona la propiedad 'list_unsubscribe' del [ImapMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapmessageinfo/#imapmessageinfo-class) clase para recuperar este encabezado. El siguiente fragmento de código muestra el uso de la propiedad y puede usarse como parte de un sistema para automatizar el proceso de cancelación de la suscripción a correos electrónicos no deseados:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

message_info_col = client.list_messages()

# Iterate through each message
for imap_message_info in message_info_col:
    print("ListUnsubscribe Header:", imap_message_info.list_unsubscribe)
```
