---
title: "Accediendo a Gmail en SSL"
url: /es/net/accessing-gmail-on-ssl/
weight: 40
type: docs
---

## **SMTP**
Este artículo muestra cómo [conectarse a un servidor de Gmail](#connecting-to-gmail-smtp-server) y [enviar un correo electrónico](#sending-an-email-message) utilizando el protocolo SMTP sobre SSL.
### **Conectándose al servidor SMTP de Gmail**
El siguiente fragmento de código muestra cómo conectarse a un servidor SMTP habilitado para SSL.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-ConnectingGmailSMTPServer-ConnectingGmailSMTPServer.cs" >}}
### **Enviando un Mensaje de Correo Electrónico**
El código anterior configura el objeto SMTPClient para conectarse al servidor de Gmail. Para enviar un mensaje utilizando el mismo objeto cliente, crea un objeto de clase [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) y envía el mensaje utilizando el objeto cliente SMTP. El siguiente fragmento de código muestra cómo establecer las propiedades del mensaje, por ejemplo, el asunto, a y cuerpo:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-SendEmailMessage-SendEmailMessage.cs" >}}
## **IMAP**
Este artículo muestra cómo realizar una serie de actividades en un servidor de correo habilitado para SSL utilizando el protocolo IMAP:

- Conectarse a un servidor de correo.
- Obtener el número total de mensajes en una bandeja de entrada.
- Guardar mensajes localmente.
- Crear un mensaje y agregarlo a una carpeta.
### **Conectándose al Servidor de Correo**
Utiliza el objeto de clase [ImapClient](https://apireference.aspose.com/email/net/aspose.email.clients.imap/imapclient) de Aspos.Email para conectarte al servidor de correo. Se requiere la dirección del servidor, puerto, nombre de usuario y contraseña para establecer una conexión. Gmail utiliza el puerto 993 para el protocolo IMAP, el siguiente fragmento de código muestra cómo conectarse a Gmail utilizando ese puerto.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-ConnectToGmailUsingIMAP-ConnectToGmailUsingIMAP.cs" >}}
### **Seleccionando una Carpeta y Obteniendo el Número Total de Mensajes**
Comprobar la carpeta de la Bandeja de Entrada es la tarea más frecuente al revisar el correo electrónico. Usando Aspose.Email, esto se puede hacer con solo dos líneas de código simples. El siguiente fragmento de código muestra cómo acceder a la carpeta de la bandeja de entrada y obtener el número total de mensajes en la carpeta.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-GetGmailMessageCountUsingIMAP-GetGmailMessageCountUsingIMAP.cs" >}}
### **Guardando Mensajes en un Disco Duro Local**
Una vez que se ha seleccionado una carpeta con el método SelectFolder, utiliza la función ListMessages para obtener una lista de todos los mensajes en la carpeta en un objeto ImapMessagesInfoCollection. Recorre esta colección y guarda los mensajes de correo electrónico en el disco local de la computadora de la siguiente manera:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-SaveGmailMessages-SaveGmailMessages.cs" >}}
### **Creando una Nueva Carpeta**
El protocolo IMAP también te permite crear una nueva carpeta en el servidor de correo electrónico. Esto se puede hacer utilizando una simple llamada a la función.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-CreateNewGmailFolderUsingIMAP-CreateNewGmailFolderUsingIMAP.cs" >}}
### **Creando un Nuevo Mensaje en una Carpeta**
Agrega un nuevo mensaje a la carpeta utilizando las clases [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) e [ImapClient](https://apireference.aspose.com/email/net/aspose.email.clients.imap/imapclient). Los ejemplos a continuación crean primero un objeto MailMessage proporcionando los valores de asunto, a y de. Luego se suscribe a una carpeta y agrega el mensaje a ella. El siguiente fragmento de código muestra cómo crear un nuevo mensaje en una carpeta.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AddingMessageToGmailFolderUsingIMAP-AddingMessageToGmailFolderUsingIMAP.cs" >}}
## **POP3**
Este artículo muestra algunos ejemplos que utilizan el protocolo POP3 sobre SSL. Para conectarse a un servidor protegido por SSL, necesitamos definir el puerto SSL y dos propiedades adicionales. El resto del código es el mismo que para conectarse a un servidor POP3 normal.

Los ejemplos de código a continuación muestran cómo:

- Conectarse a un servidor SSL.
- Comprobar el estado del buzón
- Obtener información sobre el mensaje
- Recuperar correos electrónicos.
### **Conectándose al Servidor de Correo**
Conéctate al servidor de correo habilitado para SSL utilizando la clase [Pop3client](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client) como se describe a continuación.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-ConnectToGmailUsingPOP3-ConnectToGmailUsingPOP3.cs" >}}
### **Comprobando el Estado del Buzón**
El siguiente fragmento de código muestra cómo comprobar el número de mensajes almacenados en el buzón y el tamaño del buzón. Utiliza la clase [Pop3MailboxInfo](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3mailboxinfo) para este propósito.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-CheckGmailMailboxStatus-CheckGmailMailboxStatus.cs" >}}
### **Comprobando la Información del Mensaje**
Este ejemplo verifica todos los mensajes en el buzón utilizando la clase [Pop3MessageInfoCollection](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3messageinfocollection). Utiliza la función [Pop3Client.ListMessages()](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/methods/listmessages/index) para obtener la colección [Pop3MessageInfoCollection](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3messageinfocollection). Luego recorre la colección para leer la información del mensaje: ID del mensaje, índice, asunto y tamaño.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-CheckGmailMessageInformation-CheckGmailMessageInformation.cs" >}}
### **Recuperando Mensajes**
Para obtener los mensajes del buzón, utiliza el método FetchMessage() de la clase [Pop3Client](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client) para obtener el mensaje en un objeto de tipo [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage). El siguiente fragmento de código muestra cómo contar el número de correos electrónicos en el buzón y luego recorrerlos para recuperar cada uno.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-RetrieveGmailMessages-RetrieveGmailMessages.cs" >}}