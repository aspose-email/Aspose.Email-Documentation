---
title: "Trabajo con las Bandas de Mensaje en el Servidor"
url: /es/python-net/working-with-message-flags-on-server/
weight: 60
type: docs
---


## **Cambiando las Bandas de Mensaje**
Puedes cambiar las bandas de mensaje utilizando el método ChangeMessageFlags(). Este método toma dos parámetros.

1. El número de secuencia del mensaje o ID único.
1. MessageFlag.

Las siguientes bandas se pueden establecer:

- Respondido
- Eliminado
- Borrador
- Vacío
- Marcado
- EsLeído
- Reciente
### **Estableciendo Bandas de Mensaje**
El siguiente fragmento de código te muestra cómo cambiar las bandas de mensaje en un servidor IMAP con Aspose.Email.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-SettingMessageFlags-SettingMessageFlags.py" >}}

### **Eliminando Bandas de Mensaje**

La API también proporciona el método 'remove_message_flags' de la clase [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) para eliminar bandas de sistema predefinidas como \Seen (que corresponde a que el mensaje ha sido leído), \Answered (mensaje al que se ha respondido), \Flagged (mensaje marcado como importante), \Deleted (mensaje marcado para eliminación), y \Draft (mensaje guardado como borrador), así como bandas de palabras clave personalizadas definidas por los usuarios. El método toma los siguientes parámetros: identificador único (UID) o número de secuencia del mensaje junto con las bandas que deseas eliminar. El siguiente ejemplo de código demuestra cómo eliminar la banda 'is_read' con solo una línea de código:

```py
# Eliminar la banda del mensaje
client.remove_message_flags(1, ae.clients.imap.ImapMessageFlags.is_read)
```
### **Estableciendo Bandas Personalizadas**
También puedes establecer bandas personalizadas en un mensaje utilizando el [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) de la API. Su método 'add_message_flags' proporciona la capacidad de establecer bandas personalizadas en los mensajes.

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

# Crear un mensaje
message = ae.MailMessage("user@domain1.com", "user@domain2.com", "subject", "message")

# Agregar el mensaje al buzón
uid = client.append_message(ae.clients.imap.ImapFolderInfo.IN_BOX, message)

# Agregar bandas personalizadas al mensaje añadido
client.add_message_flags(uid, ae.clients.imap.ImapMessageFlags.keyword("custom1") | ae.clients.imap.ImapMessageFlags.keyword("custom1_0"))

# Recuperar los mensajes para verificar la presencia de la banda personalizada
client.select_folder(ae.clients.imap.ImapFolderInfo.IN_BOX)

messageInfos = client.ListMessages()

for inf in messageInfos:
  flags = inf.flags.split()
  if inf.contains_keyword("custom1"):
        print("Palabra clave encontrada")
```