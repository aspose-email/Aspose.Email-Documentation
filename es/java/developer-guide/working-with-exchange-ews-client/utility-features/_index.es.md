---
title: "Funciones de Utilidad"
url: /es/java/utility-features/
weight: 120
type: docs
---


## **Enviar un Mensaje con Opción de Votación**
Microsoft Outlook permite a los usuarios crear una encuesta al redactar un nuevo mensaje. Esto se realiza incluyendo opciones de votación como Sí, No, Quizás, etc. La clase FollowUpOptions ofrecida por Aspose.Email proporciona la propiedad VotingButtons que se puede usar para establecer o obtener el valor de las opciones de votación. Este artículo ofrece un ejemplo detallado de cómo crear un MapiMessage con opciones de votación para crear una encuesta y luego enviar el mensaje utilizando el cliente de Exchange Web Service (EWS).
### **Crear y Enviar un Mensaje con Opciones de Votación**
El siguiente fragmento de código muestra cómo crear un nuevo mensaje y luego enviarlo con opciones de votación.



~~~Java
String address = "firstname.lastname@aspose.com";

IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
MailMessage message = createTestMessage(address);

// Establecer Botones FollowUpOptions
FollowUpOptions options = new FollowUpOptions();
options.setVotingButtons("Sí;No;Quizás;¡Exactamente!");

client.send(message, options);
~~~
### **Métodos de Ejemplo Utilizados en Ejemplos**
El siguiente fragmento de código muestra cómo usar los métodos utilizados en el ejemplo anterior.



~~~Java
private static MailMessage createTestMessage(String address) {
    MailMessage eml = new MailMessage(address, address, "Mensaje marcado",
            "Hazlo bonito y breve, pero descriptivo. La descripción puede aparecer en las páginas de resultados de búsqueda de los motores de búsqueda...");

    return eml;
}
~~~ 
## **Crear mensajes RE y FW a partir de archivos MSG**
[IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) permite a los desarrolladores crear mensajes RE (Responder/Responder a Todos) y FW (Reenviar) a partir de un mensaje fuente. El mensaje fuente se identifica seleccionando un [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo) particular de la [ExchangeMessageInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfoCollection) obtenida mediante IEWSClient.listMessages(). El otro argumento es el [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) que se enviará como mensaje RE o FW. El siguiente fragmento de código muestra cómo crear una cuenta de muestra que se usa para enviar un mensaje y luego las características de respuesta y reenvío se demuestran contra ese mensaje de muestra. Para realizar esta tarea:

1. Inicializar el objeto IEWSClient proporcionando credenciales válidas.
1. Enviar unos mensajes de muestra.
1. Llamar a las funciones IEWSClient.reply(), IEWSClient.replyAll() y IEWSClient.forward() para enviar mensajes.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credential);

try {
    MailMessage message = new MailMessage("user@domain.com", "user@domain.com", "TestMailRefw - " + UUID.randomUUID().toString(),
            "TestMailRefw Implementar la capacidad de crear mensajes RE y FW a partir de un archivo MSG fuente");

    client.send(message);

    ExchangeMessageInfoCollection messageInfoCol = client.listMessages(client.getMailboxInfo().getInboxUri());
    if (messageInfoCol.size() == 1)
        System.out.println("1 mensaje en la Bandeja de entrada");
    else
        System.out.println("¡Error! No hay mensaje en la Bandeja de entrada");

    MailMessage message1 = new MailMessage("user@domain.com", "user@domain.com", "TestMailRefw - " + UUID.randomUUID().toString(),
            "TestMailRefw Implementar la capacidad de crear mensajes RE y FW a partir de un archivo MSG fuente");

    client.send(message1);
    messageInfoCol = client.listMessages(client.getMailboxInfo().getInboxUri());

    if (messageInfoCol.size() == 2)
        System.out.println("2 mensajes en la Bandeja de entrada");
    else
        System.out.println("¡Error! No hay nuevo mensaje en la Bandeja de entrada");

    MailMessage message2 = new MailMessage("user@domain.com", "user@domain.com", "TestMailRefw - " + UUID.randomUUID().toString(),
            "TestMailRefw Implementar la capacidad de crear mensajes RE y FW a partir de un archivo MSG fuente");
    message2.getAttachments().addItem(Attachment.createAttachmentFromString("Prueba de adjunto 1", "Nombre del adjunto 1"));
    message2.getAttachments().addItem(Attachment.createAttachmentFromString("Prueba de adjunto 2", "Nombre del adjunto 2"));

    // Responder, Responder a Todos y reenviar Mensaje
    client.reply(message2, messageInfoCol.get_Item(0));
    client.replyAll(message2, messageInfoCol.get_Item(0));
    client.forward(message2, messageInfoCol.get_Item(0));
} catch (java.lang.RuntimeException ex) {
    System.out.println("Error en el programa" + ex.getMessage());
}
~~~ 
## **Soporte OAuth para EWS con Office 365**
El API de Aspose.Email proporciona soporte para Exchange Web Service (EWS) con Office 365. La interfaz [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) del API proporciona un método sobrecargado que proporciona el [OAuthNetworkCredential](https://apireference.aspose.com/email/java/com.aspose.email/OAuthNetworkCredential) como entrada para acceder a la cuenta de Exchange a través de OAuth. El usuario necesita proporcionar los parámetros Authority, Client Id, Client App Uri y Resource para que esto funcione. El siguiente fragmento de código muestra el soporte OAuth para EWS con Office 365.


~~~Java
// proveedor de token
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
## **Soporte para Registro en Clientes de Exchange**
El API de Aspose.Email proporciona la capacidad de ofrecer una instalación de registro para el cliente de Exchange Web Service.
### **Registro para Cliente EWS**


~~~Java
client.setLogFileName("logs/ews");
// O
EWSClient.setCommonLogFileName("logs/ews");
~~~ 
## **Agregar Encabezados en Solicitudes EWS**
El API de Aspose.Email permite agregar encabezados a las solicitudes de Exchange. Esto se puede usar para agregar encabezados a las solicitudes de EWS para diferentes encabezados que se pueden usar para diferentes propósitos. Un ejemplo de esto podría ser agregar el encabezado X-AnchorMailbox que se utiliza para gestionar los problemas de limitación en el servidor de Exchange. El método addHeader de IEWSClient se utiliza para agregar encabezados a las solicitudes de EWS como se muestra en el siguiente fragmento de código.



~~~Java
final IEWSClient client = EWSClient.getEWSClient("exchange.domain.com/ews/Exchange.asmx", "username", "password", "");
try {
    client.addHeader("X-AnchorMailbox", "username@domain.com");
    ExchangeMessageInfoCollection messageInfoCol = client.listMessages(client.getMailboxInfo().getInboxUri());
} finally {
    client.dispose();
}
~~~ 

## **Devolver el ID de Solicitud del Cliente en el Encabezado**

El encabezado ```return-client-request-id``` se envía en la solicitud y es utilizado por el servidor para determinar si el encabezado ```client-request-id``` especificado por el cliente debe ser devuelto en la respuesta del servidor. Los siguientes métodos se utilizan en esta operación:

- [getReturnClientRequestId()](https://reference.aspose.com/email/java/com.aspose.email/iewsclient/#getReturnClientRequestId--) 
- [setReturnClientRequestId(boolean value)](https://reference.aspose.com/email/java/com.aspose.email/iewsclient/#setReturnClientRequestId-boolean-) - Obtener o establecer una bandera que indique si el cliente requiere que el servidor devuelva el ID de solicitud.

```java
try (IEWSClient client = createEWSClient())
{
    // El cliente creará un ID aleatorio y lo pasará al servidor.
    // El servidor debe incluir este ID en el encabezado request-id de todas las respuestas.
    client.setReturnClientRequestId(true);
    
    client.setLogFileName("ews.log");
    client.getMailboxInfo();
}
``` 

## **Trabajar con Mensajería Unificada**
Aspose.Email puede recuperar información de mensajería unificada del servidor de Exchange 2010. Actualmente se admite la mensajería unificada, como obtener información de configuración, iniciar una llamada saliente, recuperar información de llamadas telefónicas por ID de llamada y desconectar una llamada telefónica por ID. El siguiente ejemplo de código muestra cómo recuperar información de configuración de mensajería unificada del Microsoft Exchange Server 2010.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credential);
UnifiedMessagingConfiguration umConf = client.getUMConfiguration();
~~~ 
## **Obtener Consejos de Correo**
Microsoft Exchange Server agregó varias nuevas funciones con Exchange Server 2010 y 2013. Una de ellas permite a los usuarios obtener consejos de correo al redactar un mensaje de correo electrónico. Estos consejos son muy útiles ya que proporcionan información antes de que se envíe el correo electrónico. Por ejemplo, si una dirección de correo electrónico es incorrecta en la lista de destinatarios, se muestra un consejo para hacerle saber que la dirección de correo electrónico no es válida. Los consejos de correo también permiten ver respuestas de fuera de la oficina antes de enviar un correo electrónico: el servidor Exchange (2010 y 2013) envía el consejo de correo cuando se compone el correo electrónico si uno o más de los destinatarios han establecido respuestas de fuera de la oficina. Se requiere el Service Pack 1 de Microsoft Exchange Server 2010 para todas las funciones demostradas en este artículo. El siguiente fragmento de código muestra cómo usar la clase [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) que utiliza Exchange Web Services, disponibles en Microsoft Exchange Server 2007 y versiones posteriores.



~~~Java
// Crear instancia de la clase EWSClient dando credenciales
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
System.out.println("Conectado al servidor Exchange...");
// Proporcionar opciones de consejos de correo
MailAddressCollection addrColl = new MailAddressCollection();
addrColl.addMailAddress(new MailAddress("test.exchange@ex2010.local", true));
addrColl.addMailAddress(new MailAddress("invalid.recipient@ex2010.local", true));
GetMailTipsOptions options = new GetMailTipsOptions(MailAddress.to_MailAddress("administrator@ex2010.local"), addrColl, MailTipsType.All);

// Obtener Consejos de Correo
MailTips[] tips = client.getMailTips(options);

// Mostrar información sobre cada Consejo de Correo
for (MailTips tip : tips) {
    // Mostrar mensaje de fuera de la oficina, si está presente
    if (tip.getOutOfOffice() != null) {
        System.out.println("Fuera de la oficina: " + tip.getOutOfOffice().getReplyBody().getMessage());
    }

    // Mostrar la dirección de correo electrónico inválida en el destinatario, si está presente
    if (tip.getInvalidRecipient() == true) {
        System.out.println("La dirección del destinatario es inválida: " + tip.getRecipientAddress());
    }
}
~~~ 
## **Impersonación de Exchange**
La impersonación de Exchange permite a alguien impersonar otra cuenta y realizar tareas y operaciones utilizando los permisos de la cuenta impersonada en lugar de los suyos. Mientras que la delegación permite a los usuarios actuar en nombre de otros usuarios, la impersonación les permite actuar como otros usuarios. Aspose.Email admite la impersonación de Exchange. La clase [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) proporciona los métodos ImpersonateUser y ResetImpersonation para facilitar esta función.

Para realizar esta tarea:

1. Inicializa el ExchangeWebServiceClient para el usuario 1.
1. Inicializa el ExchangeWebServiceClient para el usuario 2.
1. Agrega mensajes de prueba a las cuentas.
1. Habilita la Impersonación.
1. Restablece la Impersonación.

El siguiente fragmento de código muestra cómo usar la clase [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) para implementar la función de Impersonación.



~~~Java
// Crear instancias de la clase EWSClient dando credenciales
IEWSClient client1 = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser1", "pwd", "domain");
IEWSClient client2 = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser2", "pwd", "domain");
{
    String folder = "Borradores";
    try {
        for (ExchangeMessageInfo messageInfo : (Iterable<ExchangeMessageInfo>) client1.listMessages(folder))
            client1.deleteItem(messageInfo.getUniqueUri(), DeletionOptions.getDeletePermanently());
        String subj1 = "NETWORKNET_33354 Usuario Usuario1";
        client1.appendMessage(folder, new MailMessage("User1@exchange.conholdate.local", "To@aspsoe.com", subj1, ""));

        for (ExchangeMessageInfo messageInfo : (Iterable<ExchangeMessageInfo>) client2.listMessages(folder))
            client2.deleteItem(messageInfo.getUniqueUri(), DeletionOptions.getDeletePermanently());
        String subj2 = "NETWORKNET_33354 Usuario Usuario2";
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
## **Función de Autodiscover usando EWS**
El API de Aspose.Email te permite descubrir la configuración del servidor Exchange utilizando el cliente EWS. 


~~~Java
AutodiscoverService svc = new AutodiscoverService();
svc.setCredentials(new NetworkCredential(email, password));

IGenericDictionary</* UserSettingName */Integer, Object> userSettings = svc.getUserSettings(email, UserSettingName.ExternalEwsUrl).getSettings();
String ewsUrl = (String) userSettings.get_Item(UserSettingName.ExternalEwsUrl);
System.out.println("URL de EWS autodetectada: " + ewsUrl);
~~~ 
## **Cancelar la operación de restauración de PST al Servidor de Exchange**
El API de Aspose.Email te permite restaurar un archivo PST al servidor de Exchange. Sin embargo, si la operación se está prolongando debido al gran tamaño del archivo PST, puede ser necesario especificar un criterio para cancelar la operación. Esto se puede lograr utilizando el API como se muestra en el siguiente código de muestra.


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
        // crear un pst de prueba y agregarle algunos mensajes de prueba
        PersonalStorage pst = PersonalStorage.create(new ByteArrayOutputStream(), FileFormatVersion.Unicode);
        FolderInfo folder = pst.getRootFolder().addSubFolder("Mi carpeta de prueba");
        for (int i = 0; i < 20; i++) {
            MapiMessage message = new MapiMessage("from@gmail.com", "to@gmail.com", "subj", "body");
            folder.addMessage(message);
        }
        RestoreSettings rs = new RestoreSettings();
        rs.setBeforeItemCallback(callback);

        // ahora restaurar el PST con callback
        client.restore(pst, rs);
        System.out.println("¡Éxito!");
    } catch (AbortRestoreException e) {
        System.out.println("¡Tiempo de espera! " + processedItems.get());
    }
} finally {
    client.dispose();
}
~~~