---
title: "Acceso a Gmail con SSL"
url: /es/net/accessing-gmail-on-ssl/
weight: 40
type: docs
---

## **SMTP**
Este artículo muestra cómo realizar [conectarse a un servidor de Gmail](#connecting-to-gmail-smtp-server) and [enviar un correo electrónico](#sending-an-email-message) mediante el protocolo SMTP en SSL.
### **Conexión al servidor SMTP de Gmail**
El siguiente fragmento de código muestra cómo conectarse a un servidor SMTP con SSL habilitado.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-ConnectingGmailSMTPServer-ConnectingGmailSMTPServer.cs" >}}
### **Envío de un mensaje de correo electrónico**
El código anterior configura el objeto SMTPClient para que se conecte al servidor de Gmail. Para enviar un mensaje con el mismo objeto de cliente, crea un [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) objeto de clase y envía el mensaje mediante el objeto de cliente SMTP. El siguiente fragmento de código muestra cómo establecer las propiedades del mensaje (por ejemplo, el asunto) y el cuerpo:



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-SendEmailMessage-SendEmailMessage.cs" >}}
## **IMAP**
En este artículo se muestra cómo realizar una serie de actividades en un servidor de correo con SSL habilitado mediante el protocolo IMAP:

- Conéctese a un servidor de correo.
- Obtén el número total de mensajes de una bandeja de entrada.
- Guarda los mensajes de forma local.
- Crea un mensaje y agrégalo a una carpeta.
### **Conexión al servidor de correo**
Utilice Aspos.Email [ImapClient](https://apireference.aspose.com/email/net/aspose.email.clients.imap/imapclient) objeto de clase para conectarse al servidor de correo. La dirección, el puerto, el nombre de usuario y la contraseña del servidor son necesarios para establecer una conexión. Gmail usa el puerto 993 para el protocolo IMAP. En el siguiente fragmento de código, se muestra cómo se conecta a Gmail a través de ese puerto.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-ConnectToGmailUsingIMAP-ConnectToGmailUsingIMAP.cs" >}}
### **Selección de una carpeta y obtención del número total de mensajes**
Revisar la carpeta Bandeja de entrada es la tarea más frecuente al revisar el correo electrónico. Con Aspose.Email, esto se puede hacer usando solo dos líneas simples de código. El siguiente fragmento de código muestra cómo acceder a la carpeta Bandeja de entrada y obtener el número total de mensajes de la carpeta.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-GetGmailMessageCountUsingIMAP-GetGmailMessageCountUsingIMAP.cs" >}}
### **Guardar mensajes en un disco duro local**
Una vez seleccionada una carpeta con el método SelectFolder, utilice la función ListMessages para obtener una lista de todos los mensajes de la carpeta en un objeto IMAPMessagesInfoCollection. Recorra esta colección y guarde los mensajes de correo electrónico en la unidad local del equipo de la siguiente manera:



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-SaveGmailMessages-SaveGmailMessages.cs" >}}
### **Creación de una carpeta nueva**
El protocolo IMAP también permite crear una nueva carpeta en el servidor de correo electrónico. Esto se puede hacer mediante una simple llamada a una función.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-CreateNewGmailFolderUsingIMAP-CreateNewGmailFolderUsingIMAP.cs" >}}
### **Crear un mensaje nuevo en una carpeta**
Añada un mensaje nuevo a la carpeta mediante el [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) and [ImapClient](https://apireference.aspose.com/email/net/aspose.email.clients.imap/imapclient) clases. Los ejemplos siguientes crean primero un objeto MailMessage proporcionando los valores de asunto, ida y vuelta. A continuación, se suscribe a una carpeta y le agrega el mensaje. En el siguiente fragmento de código, se muestra cómo crear un mensaje nuevo en una carpeta.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AddingMessageToGmailFolderUsingIMAP-AddingMessageToGmailFolderUsingIMAP.cs" >}}
## **POP3**
En este artículo se muestran algunos ejemplos de uso del protocolo POP3 en SSL. Para conectarnos a un servidor protegido por SSL, necesitamos definir el puerto SSL y dos propiedades adicionales. El resto del código es el mismo que para conectarse a un servidor POP3 normal.

Los ejemplos de código que aparecen a continuación muestran cómo:

- Conéctese a un servidor SSL.
- Comprobar el estado del buzón
- Obtenga información sobre el mensaje
- Recuperar correos electrónicos.
### **Conexión al servidor de correo**
Conéctese al servidor de correo con SSL activado mediante [Pop3client](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client) clase como se describe a continuación.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-ConnectToGmailUsingPOP3-ConnectToGmailUsingPOP3.cs" >}}
### **Comprobar el estado del buzón**
El siguiente fragmento de código muestra cómo comprobar la cantidad de mensajes almacenados en el buzón y el tamaño del buzón. Utilice [Pop3MailboxInfo](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3mailboxinfo) clase para este propósito.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-CheckGmailMailboxStatus-CheckGmailMailboxStatus.cs" >}}
### **Comprobar la información del mensaje**
En este ejemplo se comprueban todos los mensajes del buzón de correo mediante el [Pop3MessageInfoCollection](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3messageinfocollection) clase. Usa el [Pop3Client.ListMessages()](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/methods/listmessages/index) función para obtener el [Pop3MessageInfoCollection](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3messageinfocollection) colección. A continuación, recorre la colección para leer la información del mensaje: el identificador, el índice, el asunto y el tamaño del mensaje



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-CheckGmailMessageInformation-CheckGmailMessageInformation.cs" >}}
### **Recuperación de mensajes**
Para obtener los mensajes del buzón, utilice la [Pop3Client](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client) método fetchMessage () de la clase para obtener el mensaje en un [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) escriba objeto. En el siguiente fragmento de código se muestra cómo contar el número de correos electrónicos del buzón y, a continuación, recorrerlos en iteración para recuperar cada uno de ellos.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-RetrieveGmailMessages-RetrieveGmailMessages.cs" >}}
