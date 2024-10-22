---
title: "Trabajando con Mensajes desde el Servidor IMAP"
url: /es/python-net/working-with-messages-from-imap-server/
weight: 70
type: docs
---

## **Obtención de la Información de Identificación para Mensajes Recibidos de un Buzón**

Al recuperar y procesar mensajes de correo electrónico, puedes obtener los detalles de los mensajes utilizando sus números de secuencia.

Las siguientes características se utilizan para interactuar con un buzón IMAP:

- [Aspose.Email.ImapMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapmessageinfo/#imapmessageinfo-class) clase - Representa la información de identificación sobre el mensaje en un buzón.

- [Aspose.Email.ImapMessageInfo.sequence_number](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapmessageinfo/#imapmessageinfo-class) propiedad - El número de secuencia de un mensaje.

- [Aspose.Email.ImapMessageInfo.unique_id](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapmessageinfo/#imapmessageinfo-class) propiedad - La ID única de un mensaje.

El siguiente fragmento de código muestra cómo obtener la información de identificación sobre los mensajes:

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

## **Listado de IDs de Mensajes MIME desde el Servidor**
ImapMessageInfo proporciona el MIME MessageId para la identificación de mensajes sin extraer el mensaje completo. El siguiente fragmento de código muestra cómo listar el messageId MIME.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-ListingMIMEMessageIdInImapMessageInfo-ListingMIMEMessageIdInImapMessageInfo.py" >}}

## **Listado de Mensajes desde el Servidor**

El método 'list_messages' de la clase [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) obtiene una lista de todos los mensajes de la carpeta actualmente seleccionada (la "Bandeja de entrada" en este caso). Esta lista contiene objetos de metadatos de mensajes, que típicamente incluyen información como IDs de mensajes, números de secuencia, UIDs y posiblemente datos de resumen como líneas de asunto o información del remitente.

El siguiente fragmento de código demuestra cómo recuperar los metadatos de los mensajes de la Bandeja de entrada e imprimir el número total de mensajes que contiene:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

client.select_folder("Inbox")

messages = client.list_messages()
print(f"Total Messages: {len(messages)}")
```

## **Listado de Mensajes desde el Servidor Recursivamente**
El protocolo IMAP soporta el listado de mensajes recursivamente desde una carpeta de buzón. Esto ayuda a listar mensajes de subcarpetas de una carpeta también. El siguiente fragmento de código muestra cómo listar mensajes recursivamente.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-ListingMessagesRecursively-ListingMessagesRecursively.py" >}}

## **Listado de Mensajes con MultiConexión**

La clase [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) proporciona una propiedad 'use_multi_connection' para usar múltiples conexiones para operaciones de alta carga. También puedes establecer la cantidad de conexiones en modo multi-conexión usando la propiedad 'connections_quantity'. El siguiente fragmento de código demuestra el uso del modo multi-conexión al listar mensajes:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

client.select_folder("Inbox")
client.connections_quantity = 5
client.use_multi_connection = ae.clients.MultiConnectionMode.ENABLE

message_info_col = client.list_messages(True)
```
*Por favor ten en cuenta que usar este modo no necesariamente tiene que resultar en un aumento de rendimiento.*

## **Obtener Mensajes en Orden Descendente**

La tarea se logra definiendo configuraciones de paginación para la recuperación de mensajes. Para este propósito, utiliza la propiedad 'ascending_sorting' de la clase [PageSettings](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/pagesettings/#pagesettings-class), que forma parte del módulo del cliente IMAP. Establece el atributo 'ascending_sorting' en el objeto PageSettings a False. Esto indica que los mensajes deben ser ordenados en orden descendente por defecto durante la recuperación. El siguiente fragmento de código muestra cómo recuperar mensajes en orden descendente:

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

## **Recuperar Mensajes desde el Servidor y Guardar en Disco**
La clase ImapClient puede recuperar mensajes desde un servidor IMAP y guardar los mensajes en formato EML en un disco local. Los siguientes pasos son necesarios para guardar los mensajes en disco:

1. Crear una instancia de la clase ImapClient.
1. Especificar hostname, nombre de usuario y contraseña en el constructor de ImapClient.
1. Seleccionar la carpeta usando el método SelectFolder().
1. Llamar al método ListMessages para obtener el objeto ImapMessageInfoCollection.
1. Iterar a través de la colección ImapMessageInfoCollection, llamar al método SaveMessage() y proporcionar la ruta de salida y el nombre del archivo.

El siguiente fragmento de código muestra cómo recuperar mensajes de correo electrónico desde un servidor y guardarlos.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-FetchEmailMessageFromServer-FetchEmailMessageFromServer.py" >}}

## **Guardar Mensajes en Formato MSG**
En el ejemplo anterior, los correos electrónicos se guardan en formato EML. Para guardar correos electrónicos en formato MSG, es necesario llamar al método ImapClient.FetchMessage(). Este devuelve el mensaje en una instancia de la clase MailMessage. Luego se puede llamar al método MailMessage.Save() para guardar el mensaje en MSG. El siguiente fragmento de código muestra cómo guardar mensajes en formato MSG.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-SavingMessageFromIMAPServer-SavingMessageFromIMAPServer.py" >}}

## **Recuperar Mensajes por Número de Secuencia o ID Único**

La biblioteca te permite generar dos listas de mensajes, una que contiene los números de secuencia y otra que contiene los IDs únicos de todos los mensajes en la bandeja de entrada. Para recuperar mensajes del servidor IMAP por estos identificadores, utiliza el método 'fetch_messages' de la clase [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class). El siguiente fragmento de código demuestra cómo listar mensajes por identificadores:

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

## **Listado de Mensajes con Soporte de Paginación**
En escenarios donde el servidor de correo electrónico contiene una gran cantidad de mensajes en el buzón, a menudo se desea listar o recuperar los mensajes con soporte de paginación. El ImapClient de la API Aspose.Email te permite recuperar los mensajes del servidor con soporte de paginación.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-ListingMessagesWithPagingSupport-ListingMessagesWithPagingSupport.py" >}}

## **Listado de Adjuntos de Mensajes**

Para obtener información sobre adjuntos como nombre, tamaño sin recuperar los datos del adjunto, utiliza los siguientes recursos de la biblioteca:

- [ImapAttachmentInfo](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapattachmentinfo/#imapattachmentinfo-class) clase - Representa la información de un adjunto (tamaño, nombre, tipo de medio).

- [ImapAttachmentInfoCollection](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapattachmentinfocollection/#imapattachmentinfocollection-class) clase - Representa la colección de [ImapAttachmentInfo](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapattachmentinfo/#imapattachmentinfo-class).

- '`list_attachments(sequence_number)`' método de la clase [`ImapClient`](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) - Obtiene una colección iterable de información sobre los adjuntos para el mensaje.

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

## **Obteniendo Carpetas y Leyendo Mensajes Recursivamente**

[ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) utiliza el método recursivo para listar carpetas y subcarpetas del servidor IMAP. El mismo método también se utiliza para leer y guardar mensajes en el disco local en formato MSG. Las carpetas y mensajes se crean y guardan en la misma estructura jerárquica que en el servidor IMAP. El siguiente fragmento de código muestra cómo obtener carpetas y mensajes recursivamente:

```py
import aspose.email as ae
import os

# Método recursivo para obtener mensajes de carpetas y subcarpetas
def list_messages_in_folder(folder_info, root_folder, client):
    # Crear la carpeta en disco (mismo nombre que en el servidor IMAP)
    current_folder = os.path.join(root_folder, folder_info.name)
    os.makedirs(current_folder, exist_ok=True)

    # Leer los mensajes de la carpeta actual, si es seleccionable
    if folder_info.selectable:
        # Enviar un comando de estado para obtener información de la carpeta
        folder_info_status = client.get_folder_info(folder_info.name)
        print(
            f"Carpeta {folder_info_status.name} seleccionada. Nuevos mensajes: {folder_info_status.new_message_count}, "
            f"Total de mensajes: {folder_info_status.total_message_count}"
        )

        # Seleccionar la carpeta actual y listar mensajes
        client.select_folder(folder_info.name)
        msg_info_coll = client.list_messages()
        print("Listando mensajes....")
        for msg_info in msg_info_coll:
            # Obtener asunto y otras propiedades del mensaje
            print("Asunto:", msg_info.subject)
            print(
                f"Leído: {msg_info.is_read}, Reciente: {msg_info.recent}, Respondido: {msg_info.answered}"
            )

            # Eliminar caracteres como ? y :, que no deben incluirse en un nombre de archivo
            # Guardar el mensaje en formato MSG
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
        print(f"{folder_info.name} no es seleccionable.")

    try:
        # Si esta carpeta tiene subcarpetas, llamar a este método recursivamente para obtener mensajes
        folder_info_collection = client.list_folders(folder_info.name)
        for subfolder_info in folder_info_collection:
            list_messages_in_folder(subfolder_info, root_folder, client)
    except Exception:
        pass

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

try:
    # La carpeta raíz (que será creada en disco) consiste en el host y el nombre de usuario
    root_folder = f"{client.host}-{client.username}"

    # Crear la carpeta raíz y listar todas las carpetas del servidor IMAP
    os.makedirs(root_folder, exist_ok=True)
    folder_info_collection = client.list_folders()
    for folder_info in folder_info_collection:
        # Llamar al método recursivo para leer mensajes y obtener subcarpetas
        list_messages_in_folder(folder_info, root_folder, client)
except Exception as ex:
        print("\n", ex)

print("\nMensajes descargados recursivamente del servidor IMAP.")
```

## **Recuperando Parámetros Extra como Información de Resumen**

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-RetreiveExtraParametersAsSummaryInformation-RetreiveExtraParametersAsSummaryInformation.py" >}}

## **Obteniendo Información del Encabezado List-Unsubscribe**

El encabezado "ListUnsubscribe" se incluye comúnmente en los encabezados de los mensajes de correo electrónico enviados por listas de correo o sistemas de correo electrónico automatizados. Proporciona un enlace o dirección de correo electrónico que los destinatarios pueden utilizar para darse de baja de la lista de correo o de los correos electrónicos automatizados. Aspose.Email proporciona la propiedad 'list_unsubscribe' de la clase [ImapMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapmessageinfo/#imapmessageinfo-class) para recuperar este encabezado. El siguiente fragmento de código muestra el uso de la propiedad y se puede utilizar como parte de un sistema para automatizar el proceso de cancelación de suscripción a correos electrónicos no deseados:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

message_info_col = client.list_messages()

# Iterar a través de cada mensaje
for imap_message_info in message_info_col:
    print("Encabezado ListUnsubscribe:", imap_message_info.list_unsubscribe)
```