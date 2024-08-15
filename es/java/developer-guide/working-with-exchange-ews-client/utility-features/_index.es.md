---
title: "Características de utilidad"
url: /es/java/utility-features/
weight: 120
type: docs
---


## **Enviar un mensaje con opción de votación**
Microsoft Outlook permite a los usuarios crear una encuesta al redactar un mensaje nuevo. Esto se hace incluyendo opciones de votación como Sí, No, Quizás, etc. La clase FollowupOptions que ofrece Aspose.Email proporciona la propiedad VotingButtons que se puede usar para establecer u obtener el valor de las opciones de votación. Este artículo proporciona un ejemplo detallado de cómo crear un MapiMessage con opciones de votación para crear una encuesta y, a continuación, enviar el mensaje mediante el cliente de Exchange Web Service (EWS).
### **Crear y enviar un mensaje con opciones de votación**
El siguiente fragmento de código muestra cómo crear un mensaje nuevo y, a continuación, enviarlo con opciones de votación.



~~~Java
String address = "firstname.lastname@aspose.com";

IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
MailMessage message = createTestMessage(address);

// Set FollowUpOptions Buttons
FollowUpOptions options = new FollowUpOptions();
options.setVotingButtons("Yes;No;Maybe;Exactly!");

client.send(message, options);
~~~
### **Métodos de muestra utilizados en los ejemplos**
El siguiente fragmento de código muestra cómo usar los métodos utilizados en el ejemplo anterior.



~~~Java
private static MailMessage createTestMessage(String address) {
    MailMessage eml = new MailMessage(address, address, "Flagged message",
            "Make it nice and short, but descriptive. The description may appear in search engines' search results pages...");

    return eml;
}
~~~
## **Creación de mensajes RE y FW a partir de archivos MSG**
[IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) permite a los desarrolladores crear mensajes RE (Responder/Responder a todos) y FW (Reenviar) a partir de un mensaje fuente. El mensaje de origen se identifica seleccionando un mensaje en particular [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo) from [ExchangeMessageInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfoCollection) obtenido por iewsClient.listMessages (). El otro argumento es el actual [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) para enviarse como mensaje RE o FW. En el siguiente fragmento de código se muestra cómo crear una cuenta de ejemplo para enviar un mensaje y, a continuación, se muestran las funciones de respuesta y reenvío de mensajes comparándolas con ese mensaje de ejemplo. Para realizar esta tarea:

1. Inicialice el objeto IewsClient proporcionando credenciales válidas.
1. Envía algunos mensajes de muestra.
1. Llame a las funciones IewsClient.reply (), IewsClient.replyAll () e IewsClient.forward () para enviar mensajes.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credential);

try {
    MailMessage message = new MailMessage("user@domain.com", "user@domain.com", "TestMailRefw - " + UUID.randomUUID().toString(),
            "TestMailRefw Implement ability to create RE and FW messages from source MSG file");

    client.send(message);

    ExchangeMessageInfoCollection messageInfoCol = client.listMessages(client.getMailboxInfo().getInboxUri());
    if (messageInfoCol.size() == 1)
        System.out.println("1 message in Inbox");
    else
        System.out.println("Error! No message in Inbox");

    MailMessage message1 = new MailMessage("user@domain.com", "user@domain.com", "TestMailRefw - " + UUID.randomUUID().toString(),
            "TestMailRefw Implement ability to create RE and FW messages from source MSG file");

    client.send(message1);
    messageInfoCol = client.listMessages(client.getMailboxInfo().getInboxUri());

    if (messageInfoCol.size() == 2)
        System.out.println("2 messages in Inbox");
    else
        System.out.println("Error! No new message in Inbox");

    MailMessage message2 = new MailMessage("user@domain.com", "user@domain.com", "TestMailRefw - " + UUID.randomUUID().toString(),
            "TestMailRefw Implement ability to create RE and FW messages from source MSG file");
    message2.getAttachments().addItem(Attachment.createAttachmentFromString("Test attachment 1", "Attachment Name 1"));
    message2.getAttachments().addItem(Attachment.createAttachmentFromString("Test attachment 2", "Attachment Name 2"));

    // Reply, Replay All and forward Message
    client.reply(message2, messageInfoCol.get_Item(0));
    client.replyAll(message2, messageInfoCol.get_Item(0));
    client.forward(message2, messageInfoCol.get_Item(0));
} catch (java.lang.RuntimeException ex) {
    System.out.println("Error in program" + ex.getMessage());
}
~~~
## **Soporte de OAuth para EWS con Office 365**
La API Aspose.Email brinda soporte para Exchange Web Service (EWS) con Office 365. Las API [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) la interfaz proporciona un método de sobrecarga que proporciona [OAuthNetworkCredential](https://apireference.aspose.com/email/java/com.aspose.email/OAuthNetworkCredential) como entrada para acceder a la cuenta de Exchange mediante OAuth. El usuario debe proporcionar los parámetros de autoridad, ID de cliente, URI de la aplicación cliente y recurso para que esto funcione. El siguiente fragmento de código muestra la compatibilidad de OAuth con EWS con Office 365.


~~~Java
// token provider
/*ITokenProvider provider = new ITokenProvider() {

    @Override
    public void dispose() {
    }

    @Override
    public OAuthToken getAccessToken(boolean ignoreExistingToken) {
        return null;
    }

    @Override
    public OAuthToken getAccessToken() {
        return null;
    }
};

NetworkCredential credentials = new OAuthNetworkCredential(provider);*/

// accessToken
NetworkCredential credentials = new OAuthNetworkCredential("accessToken");

IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", credentials);
client.listMessages();
~~~
## **Soporte para iniciar sesión en clientes de Exchange**
La API Aspose.Email brinda la capacidad de proporcionar la función de registro del cliente de Exchange Web Service.
### **Registro para el cliente EWS**


~~~Java
client.setLogFileName("logs/ews");
// OR
EWSClient.setCommonLogFileName("logs/ews");
~~~
## **Agregar encabezados en las solicitudes de EWS**
La API Aspose.Email permite agregar encabezados a las solicitudes de Exchange. Esto se puede usar para agregar encabezados a las solicitudes de EWS para diferentes encabezados que se pueden usar para diferentes propósitos. Un ejemplo de este tipo podría ser agregar el encabezado X-AnchorMailbox, que se usa para gestionar los problemas de limitación en el servidor Exchange. El método addHeader del IEWSClient se usa para agregar encabezados a las solicitudes de EWS, como se muestra en el siguiente fragmento de código.



~~~Java
final IEWSClient client = EWSClient.getEWSClient("exchange.domain.com/ews/Exchange.asmx", "username", "password", "");
try {
    client.addHeader("X-AnchorMailbox", "username@domain.com");
    ExchangeMessageInfoCollection messageInfoCol = client.listMessages(client.getMailboxInfo().getInboxUri());
} finally {
    client.dispose();
}
~~~

## **Devuelve el ID de solicitud del cliente en el encabezado**

The ```return-client-request-id``` el encabezado se envía en la solicitud y el servidor lo utiliza para determinar si el ```client-request-id``` el encabezado especificado por el cliente debe devolverse en la respuesta del servidor. En esta operación se utilizan los siguientes métodos:

- [getReturnClientRequestId()](https://reference.aspose.com/email/java/com.aspose.email/iewsclient/#getReturnClientRequestId--)
- [setReturnClientRequestId (valor booleano)](https://reference.aspose.com/email/java/com.aspose.email/iewsclient/#setReturnClientRequestId-boolean-) - Obtenga o establezca un indicador para indicar si el cliente requiere que el servidor devuelva el identificador de la solicitud.

```java
try (IEWSClient client = createEWSClient())
{
    // Client will create random id and pass it to the server.
    // The server should include this id in request-id header of all responses.
    client.setReturnClientRequestId(true);
   
    client.setLogFileName("ews.log");
    client.getMailboxInfo();
}
```

## **Trabajando con mensajería unificada**
Aspose.Email puede recuperar información de mensajería unificada de Exchange Server 2010. En la actualidad, se admite la mensajería unificada, como la obtención de información de configuración, el inicio de una llamada saliente, la recuperación de la información de llamadas telefónicas por identificador de llamada y la desconexión de una llamada telefónica por ID. En el siguiente ejemplo de código se muestra cómo recuperar la información de configuración de la mensajería unificada de Microsoft Exchange Server 2010.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credential);
UnifiedMessagingConfiguration umConf = client.getUMConfiguration();
~~~
## **Consejos para recibir correo**
Microsoft Exchange Server agregó varias funciones nuevas con Exchange Server 2010 y 2013. Una de ellas permite a los usuarios recibir consejos sobre el correo electrónico a la hora de redactar un mensaje de correo electrónico. Estos consejos son muy útiles ya que proporcionan información antes de enviar el correo electrónico. Por ejemplo, si una dirección de correo electrónico es incorrecta en la lista de destinatarios, se muestra una sugerencia para hacerle saber que la dirección de correo electrónico no es válida. Las sugerencias de correo también le permiten ver las respuestas de los usuarios de fuera de la oficina antes de enviar un correo electrónico: Exchange Server (2010 y 2013) envía la sugerencia de correo cuando se redacta el correo electrónico si uno o más de los destinatarios han enviado las respuestas de fuera de la oficina. Todas las funciones que se muestran en este artículo requieren el Service Pack 1 de Microsoft Exchange Server 2010. En el siguiente fragmento de código se muestra cómo utilizar el [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) clase que usa los servicios web de Exchange, disponible en Microsoft Exchange Server 2007 y versiones posteriores.



~~~Java
// Create instance of EWSClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
System.out.println("Connected to Exchange server...");
// Provide mail tips options
MailAddressCollection addrColl = new MailAddressCollection();
addrColl.addMailAddress(new MailAddress("test.exchange@ex2010.local", true));
addrColl.addMailAddress(new MailAddress("invalid.recipient@ex2010.local", true));
GetMailTipsOptions options = new GetMailTipsOptions(MailAddress.to_MailAddress("administrator@ex2010.local"), addrColl, MailTipsType.All);

// Get Mail Tips
MailTips[] tips = client.getMailTips(options);

// Display information about each Mail Tip
for (MailTips tip : tips) {
    // Display Out of office message, if present
    if (tip.getOutOfOffice() != null) {
        System.out.println("Out of office: " + tip.getOutOfOffice().getReplyBody().getMessage());
    }

    // Display the invalid email address in recipient, if present
    if (tip.getInvalidRecipient() == true) {
        System.out.println("The recipient address is invalid: " + tip.getRecipientAddress());
    }
}
~~~
## **Suplantación de identidad de Exchange**
La suplantación de identidad de Exchange permite a alguien hacerse pasar por otra cuenta y realizar tareas y operaciones con los permisos de la cuenta suplantada en lugar de los suyos propios. Mientras que la delegación permite a los usuarios actuar en nombre de otros usuarios, la suplantación les permite actuar como otros usuarios. Aspose.Email admite la suplantación de identidad en Exchange. El [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) La clase proporciona los métodos ImpersonateUser y ResetImpersonation para facilitar esta función.

Para realizar esta tarea:

1. Inicialice el ExchangeWebServiceClient para el usuario 1.
1. Inicialice el ExchangeWebServiceClient para el usuario 2.
1. Añada mensajes de prueba a las cuentas.
1. Habilite la suplantación de identidad.
1. Restablecer la suplantación de identidad.

El siguiente fragmento de código muestra cómo usar el [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) clase para implementar la función de suplantación.



~~~Java
// Create instance's of EWSClient class by giving credentials
IEWSClient client1 = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser1", "pwd", "domain");
IEWSClient client2 = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser2", "pwd", "domain");
{
    String folder = "Drafts";
    try {
        for (ExchangeMessageInfo messageInfo : (Iterable<ExchangeMessageInfo>) client1.listMessages(folder))
            client1.deleteItem(messageInfo.getUniqueUri(), DeletionOptions.getDeletePermanently());
        String subj1 = "NETWORKNET_33354 User User1";
        client1.appendMessage(folder, new MailMessage("User1@exchange.conholdate.local", "To@aspsoe.com", subj1, ""));

        for (ExchangeMessageInfo messageInfo : (Iterable<ExchangeMessageInfo>) client2.listMessages(folder))
            client2.deleteItem(messageInfo.getUniqueUri(), DeletionOptions.getDeletePermanently());
        String subj2 = "NETWORKNET_33354 User User2";
        client2.appendMessage(folder, new MailMessage("User2@exchange.conholdate.local", "To@aspose.com", subj2, ""));

        ExchangeMessageInfoCollection messInfoColl = client1.listMessages(folder);
        // Assert.AreEqual(1, messInfoColl.Count);
        // Assert.AreEqual(subj1, messInfoColl[0].Subject);

        client1.impersonateUser(ItemChoice.PrimarySmtpAddress, "User2@exchange.conholdate.local");
        ExchangeMessageInfoCollection messInfoColl1 = client1.listMessages(folder);
        // Assert.AreEqual(1, messInfoColl1.Count);
        // Assert.AreEqual(subj2, messInfoColl1[0].Subject);

        client1.resetImpersonation();
        ExchangeMessageInfoCollection messInfoColl2 = client1.listMessages(folder);
        // Assert.AreEqual(1, messInfoColl2.Count);
        // Assert.AreEqual(subj1, messInfoColl2[0].Subject);
    } finally {
        try {
            for (ExchangeMessageInfo messageInfo : (Iterable<ExchangeMessageInfo>) client1.listMessages(folder))
                client1.deleteItem(messageInfo.getUniqueUri(), DeletionOptions.getDeletePermanently());
            for (ExchangeMessageInfo messageInfo : (Iterable<ExchangeMessageInfo>) client2.listMessages(folder))
                client2.deleteItem(messageInfo.getUniqueUri(), DeletionOptions.getDeletePermanently());
        } catch (java.lang.RuntimeException e) {
        }
    }
}
~~~
## **Función de detección automática mediante EWS**
La API Aspose.Email le permite conocer la configuración del servidor Exchange mediante el cliente EWS. 


~~~Java
AutodiscoverService svc = new AutodiscoverService();
svc.setCredentials(new NetworkCredential(email, password));

IGenericDictionary</* UserSettingName */Integer, Object> userSettings = svc.getUserSettings(email, UserSettingName.ExternalEwsUrl).getSettings();
String ewsUrl = (String) userSettings.get_Item(UserSettingName.ExternalEwsUrl);
System.out.println("Auto discovered EWS Url: " + ewsUrl);
~~~
## **Abortar la operación de restauración de PST a Exchange Server**
La API Aspose.Email le permite restaurar un archivo PST en Exchange Server. Sin embargo, si la operación tarda mucho debido a que el archivo PST es de gran tamaño, es posible que sea necesario especificar un criterio para abortar la operación. Esto se puede lograr mediante la API, tal y como se muestra en el siguiente código de ejemplo.


~~~Java
final IEWSClient client = EWSClient.getEWSClient("https://exchange.office365.com/ews/exchange.asmx", "username", "password");
try {
    final long startTime = System.currentTimeMillis();
    final AtomicInteger processedItems = new AtomicInteger(0);
    final long S15 = 15 * 1000;

    BeforeItemCallback callback = new BeforeItemCallback() {
        public void invoke(ItemCallbackArgs item) {
            if (System.currentTimeMillis() - startTime > S15) {
                throw new AbortRestoreException();
            }

            processedItems.incrementAndGet();
        }
    };

    try {
        // create a test pst and add some test messages to it
        PersonalStorage pst = PersonalStorage.create(new ByteArrayOutputStream(), FileFormatVersion.Unicode);
        FolderInfo folder = pst.getRootFolder().addSubFolder("My test folder");
        for (int i = 0; i < 20; i++) {
            MapiMessage message = new MapiMessage("from@gmail.com", "to@gmail.com", "subj", "body");
            folder.addMessage(message);
        }
        RestoreSettings rs = new RestoreSettings();
        rs.setBeforeItemCallback(callback);

        // now restore the PST with callback
        client.restore(pst, rs);
        System.out.println("Success!");
    } catch (AbortRestoreException e) {
        System.out.println("Timeout! " + processedItems.get());
    }
} finally {
    client.dispose();
}
~~~