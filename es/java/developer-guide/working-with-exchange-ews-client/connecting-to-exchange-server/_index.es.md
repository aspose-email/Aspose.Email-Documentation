---
title: "Conectándose al Servidor de Exchange"
url: /es/java/conectando-al-servidor-de-exchange/
weight: 10
type: docs
---

Para conectarse a los servidores de Exchange 2007, 2010 y 2013 utilizando Exchange Web Service, Aspose.Email proporciona la interfaz [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) que implementa la clase [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient). El método [EWSClient.getEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/EWSClient#getEWSClient\(java.lang.String,%20java.lang.String,%20java.lang.String,%20java.lang.String\)) instancía y devuelve un objeto [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) que se utiliza posteriormente para realizar operaciones relacionadas con un buzón de Exchange y otras carpetas. Este artículo muestra cómo instanciar objetos de [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient).
## **Conectándose al Servidor de Exchange usando EWS**
El siguiente fragmento de código muestra cómo conectarse utilizando Exchange Web Service (EWS).

~~~Java
private static IEWSClient getExchangeEWSClient() {
    final String mailboxUri = "https://outlook.office365.com/ews/exchange.asmx";
    final String domain = "";
    final String username = "username@onmicrosoft.com";
    final String password = "password";
    NetworkCredential credentials = new NetworkCredential(username, password, domain);
    IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);
    return client;
}
~~~
## **Conectándose al Servidor de Exchange usando IMAP**
Microsoft Exchange Server admite el protocolo IMAP para acceder a elementos en un buzón. Utilice la clase [ImapClient](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient) de Aspose.Email para conectarse al Servidor de Exchange utilizando el protocolo IMAP. Para más información sobre la clase [ImapClient](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient). Primero, asegúrese de que los servicios IMAP estén habilitados en su Servidor de Exchange:

1. Abra el Panel de Control.
1. Vaya a Herramientas de Administrador, luego Servicios.
1. Verifique el estado del servicio Microsoft Exchange IMAP4.
1. Si no está en funcionamiento, habilítelo/inícielo.

El siguiente fragmento de código muestra cómo conectarse y listar mensajes de la carpeta Bandeja de entrada del servidor de Microsoft Exchange utilizando el protocolo IMAP.

~~~Java
// Conectarse al Servidor de Exchange usando la clase ImapClient
ImapClient imapClient = new ImapClient("ex07sp1", "Administrator", "Evaluation1");
imapClient.setSecurityOptions(SecurityOptions.Auto);

// Seleccionar la carpeta Bandeja de entrada
imapClient.selectFolder(ImapFolderInfo.IN_BOX);

// Obtener la lista de mensajes
ImapMessageInfoCollection msgCollection = imapClient.listMessages();
for (ImapMessageInfo msgInfo : (Iterable<ImapMessageInfo>) msgCollection) {
    System.out.println(msgInfo.getSubject());
}
// Desconectarse del servidor
imapClient.dispose();
~~~

El siguiente fragmento de código muestra cómo utilizar SSL.

~~~Java
public static void run() {
    // Conectarse al Servidor de Exchange usando la clase ImapClient
    ImapClient imapClient = new ImapClient("ex07sp1", 993, "Administrator", "Evaluation1");
    imapClient.setSecurityOptions(SecurityOptions.SSLExplicit);

    // Seleccionar la carpeta Bandeja de entrada
    imapClient.selectFolder(ImapFolderInfo.IN_BOX);

    // Obtener la lista de mensajes
    ImapMessageInfoCollection msgCollection = imapClient.listMessages();
    for (ImapMessageInfo msgInfo : (Iterable<ImapMessageInfo>) msgCollection) {
        System.out.println(msgInfo.getSubject());
    }
    // Desconectarse del servidor
    imapClient.dispose();
}
~~~

Después de conectarse a un servidor de Exchange utilizando IMAP y obtener la [IMapMessageInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/ImapMessageInfoCollection), el siguiente fragmento de código muestra cómo utilizar el número de secuencia del objeto [MessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/MessageInfo) para guardar un mensaje específico.

~~~Java
// Seleccionar la carpeta Bandeja de entrada
imapClient.selectFolder(ImapFolderInfo.IN_BOX);
// Obtener la lista de mensajes
ImapMessageInfoCollection msgCollection = imapClient.listMessages();
for (ImapMessageInfo msgInfo : (Iterable<ImapMessageInfo>) msgCollection) {
    // Obtener el mensaje de la bandeja de entrada usando su SequenceNumber de msgInfo
    MailMessage message = imapClient.fetchMessage(msgInfo.getSequenceNumber());

    // Guardar el mensaje en disco ahora
    message.save(dataDir + msgInfo.getSequenceNumber() + "_out.msg", SaveOptions.getDefaultMsgUnicode());
}
~~~