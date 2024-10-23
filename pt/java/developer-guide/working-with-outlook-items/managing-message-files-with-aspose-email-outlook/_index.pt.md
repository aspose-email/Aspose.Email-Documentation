---
title: "Gerenciando Arquivos de Mensagem com Aspose.Email.Outlook"
url: /pt/java/gerenciando-arquivos-de-mensagem-com-aspose-email-outlook/
weight: 30
type: docs
---


## **Convertendo MSG para mensagem MIME**

A API Aspose.Email oferece a capacidade de converter arquivos MSG em mensagens MIME usando o método [toMailMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#toMailMessage-com.aspose.email.MailConversionOptions-).

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
MapiMessage msg = new MapiMessage(
                            "remetente@test.com",
                            "destinatario1@test.com; destinatario2@test.com",
                            "Assunto do Teste",
                            "Este é o corpo da mensagem.");
MailConversionOptions options = new MailConversionOptions();
options.setConvertAsTnef(true);
MailMessage mail = msg.toMailMessage(options);
~~~

## **Convertendo MSG para EML Preservando Corpo RTF**

A API fornece os seguintes métodos para preservar o corpo RTF ao converter MSG em EML:

- [MsgLoadOptions.PreserveRtfContent](https://reference.aspose.com/email/java/com.aspose.email/msgloadoptions/#setPreserveRtfContent-boolean-) - Obtém ou define um valor indicando se deve manter o corpo rtf em MailMessage.
- [MailConversionOptions.PreserveRtfContent](https://reference.aspose.com/email/java/com.aspose.email/mailconversionoptions/#setPreserveRtfContent-boolean-) - Obtém ou define um valor indicando se deve manter o corpo rtf em MailMessage.

Os seguintes exemplos de código demonstram como manter o corpo rtf em MailMessage:

- usando [MsgLoadOptions.PreserveRtfContent](https://reference.aspose.com/email/java/com.aspose.email/msgloadoptions/#setPreserveRtfContent-boolean-)

```java
MsgLoadOptions options = new MsgLoadOptions();
options.setPreserveRtfContent(true);
MailMessage message = MailMessage.load("fileName", options);
```
- usando [MailConversionOptions.PreserveRtfContent](https://reference.aspose.com/email/java/com.aspose.email/mailconversionoptions/#setPreserveRtfContent-boolean-)

```java
MapiMessage mapi = MapiMessage.load("fileName");
MailConversionOptions options = new MailConversionOptions();
options.setPreserveRtfContent(true);
MailMessage message = mapi.toMailMessage(options);
```
## **Convertendo MSG para MHTML Preservando Cabeçalho de Categoria**

A API Aspose.Email fornece a capacidade de adicionar um cabeçalho de categoria ao converter uma mensagem para MHTML. Esse recurso é especificado pela classe [MhtSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions/) como uma opção adicional ao salvar MailMessage no formato Mhtml.

O seguinte exemplo de código demonstra como criar um arquivo MHT (MHTML) a partir de um objeto MapiMessage, personalizar a formatação e os cabeçalhos do arquivo MHT usando MhtSaveOptions, definir categorias para a mensagem de e-mail e, em seguida, modificar os modelos de formato e os cabeçalhos de renderização para o arquivo MHT antes de salvá-lo.

```java
 MapiMessage msg = new MapiMessage("de@aaa.com", "para@aaa.com", "subj", "corpo");

msg.setCategories(new String[] { "Urgentemente", "Importante" });

MhtSaveOptions saveOptions = new MhtSaveOptions();

saveOptions.getFormatTemplates().set_Item(MhtTemplateName.CATEGORIES,

    saveOptions.getFormatTemplates().get_Item(MhtTemplateName.CATEGORIES).replace("Categories", "As categorias"));

saveOptions.getRenderingHeaders().add(MhtTemplateName.CATEGORIES);

msg.save("fileName.mhtml", saveOptions);
```

## **Lendo e Escrevendo Arquivo de Template do Outlook (.OFT)**

Os templates do Outlook são muito úteis quando você deseja enviar uma mensagem de e-mail semelhante repetidamente. Em vez de preparar a mensagem do zero a cada vez, primeiro prepare a mensagem no Outlook e salve-a como um Template do Outlook (OFT). Depois disso, sempre que precisar enviar a mensagem, você pode criá-la a partir do template, economizando tempo escrevendo o mesmo texto no corpo ou na linha de assunto, definindo formatação e assim por diante. A classe Aspose.Email [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) pode ser usada para carregar e ler um arquivo de template do Outlook (OFT). Uma vez que o template do Outlook é carregado em uma instância da classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/), você pode atualizar o remetente, destinatário, corpo, assunto e outras propriedades. Após a atualização das propriedades:

- Envie o e-mail usando a classe [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) ou
- Salve a mensagem como MSG e faça mais atualizações/validações usando o Microsoft Outlook.

Nos exemplos de código abaixo, nós:

1. Carregamos o template usando a classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Atualizamos algumas das propriedades.
1. Salvamos a mensagem no formato MSG.

O seguinte trecho de código mostra como carregar o arquivo OFT, atualizar a mensagem e salvá-la no formato MSG.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = "outlook/";

// Carregar o arquivo de template do Outlook (OFT) na instância de MailMessage
MailMessage message = MailMessage.load(dataDir + "sample.oft", new MsgLoadOptions());

// Definir as informações do remetente e destinatários
String senderDisplayName = "John";
String senderEmailAddress = "john@abc.com";
String recipientDisplayName = "William";
String recipientEmailAddress = "william@xzy.com";

message.setSender(new MailAddress(senderEmailAddress, senderDisplayName));
message.getTo().addMailAddress(new MailAddress(recipientEmailAddress, recipientDisplayName));
message.setHtmlBody(message.getHtmlBody().replace("DisplayName", "<b>" + recipientDisplayName + "</b>"));

// Definir o nome, a localização e a hora no corpo do e-mail
String meetingLocation = "<u>" + "Sala 1, Centro de Convenções, Nova York, EUA" + "</u>";
String meetingTime = "<u>" + "Segunda-feira, 28 de junho de 2010" + "</u>";
message.setHtmlBody(message.getHtmlBody().replace("MeetingPlace", meetingLocation));
message.setHtmlBody(message.getHtmlBody().replace("MeetingTime", meetingTime));

// Salvar a mensagem no formato MSG e abrir no Office Outlook
MapiMessage mapimessage = MapiMessage.fromMailMessage(message);
mapimessage.setMessageFlags(MapiMessageFlags.MSGFLAG_UNSENT);
mapimessage.save(dataDir + "LeituraEEscritaDoArquivoTemplateDoOutlook_out.msg");
~~~

### **Salvando Arquivo MSG do Outlook como Template**

O seguinte trecho de código mostra como salvar o arquivo MSG do outlook como um template.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = "outlook/";

try (MapiMessage mapi = new MapiMessage("test@from.to", "test@to.to", "assunto do template", "Corpo do template")) {
    mapi.saveAsTemplate(dataDir + "mapiToOft.msg");
}
~~~ 

## **Configurando Categoria de Cor para Arquivos MSG do Outlook**

Uma categoria de cor marca uma mensagem de e-mail como de certa importância ou categoria. O Microsoft Outlook permite que os usuários atribuam categorias de cor para diferenciar e-mails. Para lidar com a categoria de cor, use o [FollowUpManager](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/). Ele contém funções como [addCategory](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#addCategory-com.aspose.email.MapiMessage-java.lang.String-), [removeCategory](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#removeCategory-com.aspose.email.MapiMessage-java.lang.String-), [clearCategories](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#clearCategories-com.aspose.email.MapiMessage-) e [getCategories](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#getCategories-com.aspose.email.MapiMessage-).

- [addCategory](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#addCategory-com.aspose.email.MapiMessage-java.lang.String-) aceita [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) e a string de categoria de cor, por exemplo, "Categoria Roxa" ou "Categoria Vermelha" como argumentos.
- [removeCategory](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#removeCategory-com.aspose.email.MapiMessage-java.lang.String-) aceita [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) e a string da categoria de cor a ser removida da mensagem.
- [clearCategories](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#clearCategories-com.aspose.email.MapiMessage-) é usado para remover todas as categorias de cor da mensagem.
- [getCategories](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#getCategories-com.aspose.email.MapiMessage-) é usado para recuperar todas as categorias de cor de uma mensagem específica.

O seguinte exemplo realiza as tarefas conforme indicado abaixo:

1. Adiciona uma categoria de cor.
2. Adiciona outra categoria de cor.
3. Recupera a lista de todas as categorias.
4. Remove todas as categorias.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = "outlook/";

MapiMessage msg = MapiMessage.fromFile(dataDir + "message.msg");

// Adicionar duas categorias
FollowUpManager.addCategory(msg, "Categoria Roxa");
FollowUpManager.addCategory(msg, "Categoria Vermelha");

// Recuperar a lista de categorias disponíveis
IList categories = FollowUpManager.getCategories(msg);

// Remover a categoria especificada e limpar todas as categorias
FollowUpManager.removeCategory(msg, "Categoria Vermelha");
FollowUpManager.clearCategories(msg);
~~~ 

## **Acessando Informações de Acompanhamento do arquivo MSG**

A API Aspose.Email fornece a capacidade de acessar as informações de acompanhamento de uma mensagem enviada ou recebida. Ela pode recuperar a informação de Read, Delivery Read Receipt e os resultados de voto de um arquivo de mensagem.

### **Recuperando Informações de Recibo de Leitura e Entrega**

O seguinte trecho de código mostra como recuperar informações de recibo de leitura e entrega.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = "outlook/";

MapiMessage msg = MapiMessage.fromFile(dataDir + "message.msg");
for (MapiRecipient recipient : msg.getRecipients()) {
    System.out.println("Destinatário: " + recipient.getDisplayName());

    // Obter a propriedade PR_RECIPIENT_TRACKSTATUS_TIME_DELIVERY
    System.out.println("Hora de entrega: " + recipient.getProperties().get_Item(MapiPropertyTag.PR_RECIPIENT_TRACKSTATUS_TIME_DELIVERY).getDateTime());

    // Obter a propriedade PR_RECIPIENT_TRACKSTATUS_TIME_READ
    System.out.println("Hora de leitura" + recipient.getProperties().get_Item(MapiPropertyTag.PR_RECIPIENT_TRACKSTATUS_TIME_READ).getDateTime());
}
~~~ 

## **Criando Mensagens de Encaminhamento e Resposta**

A API Aspose.Email oferece a capacidade de criar e formatar mensagens de encaminhamento e resposta. As classes [ReplyMessageBuilder](https://reference.aspose.com/email/java/com.aspose.email/replymessagebuilder/) e [ForwardMessageBuilder](https://reference.aspose.com/email/java/com.aspose.email/forwardmessagebuilder/) da API são usadas para criar as mensagens de Resposta e Encaminhamento, respectivamente. Uma mensagem de Resposta ou Encaminhamento pode ser criada usando qualquer um dos modos do enum [OriginalMessageAdditionMode](https://reference.aspose.com/email/java/com.aspose.email/originalmessageadditionmode/). Esse enum possui os seguintes valores:

- **OriginalMessageAdditionMode.None** - A mensagem original não está incluída na mensagem de resposta.
- **OriginalMessageAdditionMode.Attachment** - A mensagem original está incluída como um anexo na mensagem de resposta
- **OriginalMessageAdditionMode.Textpart** - A mensagem original está incluída como um texto no corpo da mensagem de resposta

### **Criando Mensagem de Resposta**

O seguinte trecho de código mostra como criar uma mensagem de resposta.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = "outlook/";

MapiMessage originalMsg = MapiMessage.fromFile(dataDir + "message1.msg");
ReplyMessageBuilder builder = new ReplyMessageBuilder();

// Definir propriedades do ReplyMessageBuilder
builder.setReplyAll(true);
builder.setAdditionMode(OriginalMessageAdditionMode.Textpart);
builder.setResponseText(
        "<p><b>Caro Amigo,</b></p> O que quero fazer é apresentar meu co-autor e co-professor. <p><a href=\"www.google.com\">Este é o primeiro link</a></p><p><a href=\"www.google.com\">Este é o segundo link</a></p>");

MapiMessage replyMsg = builder.buildResponse(originalMsg);
replyMsg.save(dataDir + "resposta_out.msg");
~~~ 

### **Criando uma Mensagem de Encaminhamento**

O seguinte trecho de código mostra como criar uma mensagem de encaminhamento.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = "outlook/";

MapiMessage originalMsg = MapiMessage.fromFile(dataDir + "message1.msg");
ForwardMessageBuilder builder = new ForwardMessageBuilder();
builder.setAdditionMode(OriginalMessageAdditionMode.Textpart);
MapiMessage forwardMsg = builder.buildResponse(originalMsg);
forwardMsg.save(dataDir + "encaminhar_out.msg");
~~~ 

## **Preservar Datas Vazias ao Converter uma Mensagem**

A propriedade [MapiConversionOptions.setPreserveEmptyDates(boolean)](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/#setPreserveEmptyDates-boolean-) indica se é necessário manter datas vazias ao converter uma mensagem. Esta API aparece no Aspose.Email 21.5. O seguinte trecho de código mostra como preservar datas vazias.

~~~java
MailMessage mailMessage = MailMessage.load("message.eml");
System.out.println(mailMessage.getDate()); // data zero
MapiConversionOptions mco = MapiConversionOptions.getUnicodeFormat();
// manter datas vazias ao converter uma mensagem
mco.setPreserveEmptyDates(true);
MapiMessage mapiMessage = MapiMessage.fromMailMessage(mailMessage, mco);
System.out.println(mapiMessage.getClientSubmitTime()); // data zero
// verificar data zero
if (mapiMessage.getClientSubmitTime().equals(JavaHelper.ZERO_DATE))
    System.out.println("DATA ZERO");
~~~