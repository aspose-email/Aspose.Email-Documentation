---
title: "Trabajando con marcas de mensajes en el servidor"
url: /es/python-net/working-with-message-flags-on-server/
weight: 60
type: docs
---


## **Cambiar las banderas de los mensajes**
Puedes cambiar las marcas de los mensajes mediante el método changeMessageFlags (). Este método utiliza dos parámetros.

1. El número de secuencia o el identificador único del mensaje.
1. MessageFlag.

Se pueden configurar los siguientes indicadores:

- Answered
- Deleted
- Draft
- Empty
- Flagged
- IsRead
- Recent
### **Configuración de banderas de mensajes**
El siguiente fragmento de código muestra cómo cambiar las marcas de mensajes en un servidor IMAP con Aspose.Email.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-SettingMessageFlags-SettingMessageFlags.py" >}}

### **Eliminar marcas de mensajes**

La API también proporciona el método «remove_message_flags» del [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) clase para eliminar los indicadores del sistema predefinidos, como\ Seen (que corresponde al mensaje que se está leyendo),\ Answered (se ha respondido al mensaje),\ Flagged (el mensaje se marca como importante),\ Deleted (el mensaje está marcado para su eliminación) y\ Draft (el mensaje se guarda como borrador), así como los indicadores de palabras clave personalizados definidos por los usuarios. El método toma los siguientes parámetros: identificador único (UID) o número de secuencia del mensaje junto con las marcas que desea eliminar. El siguiente ejemplo de código muestra cómo eliminar la marca 'is_read' con solo una línea de código:

```py
# Remove the message flag
client.remove_message_flags(1, ae.clients.imap.ImapMessageFlags.is_read)
```
### **Configuración de banderas personalizadas**
También puedes configurar marcas personalizadas para un mensaje mediante el [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) de la API. Su método 'add_message_flags' permite establecer marcas personalizadas en los mensajes.

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

# Create a message
message = ae.MailMessage("user@domain1.com", "user@domain2.com", "subject", "message")

# Append the message to mailbox
uid = client.append_message(ae.clients.imap.ImapFolderInfo.IN_BOX, message)

# Add custom flags to the added message
client.add_message_flags(uid, ae.clients.imap.ImapMessageFlags.keyword("custom1") | ae.clients.imap.ImapMessageFlags.keyword("custom1_0"))

# Retreive the messages for checking the presence of custom flag
client.select_folder(ae.clients.imap.ImapFolderInfo.IN_BOX)

messageInfos = client.ListMessages()

for inf in messageInfos:
  flags = inf.flags.split()
  if inf.contains_keyword("custom1"):
        print("Keyword found")
```
