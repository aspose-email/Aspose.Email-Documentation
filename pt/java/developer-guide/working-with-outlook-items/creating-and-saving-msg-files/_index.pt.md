---
title: "Criando e Salvando Arquivos MSG"
url: /pt/java/creating-and-saving-msg-files/
weight: 10
type: docs
---


Aspose.Email suporta a criação de arquivos de mensagem do Outlook (MSG). Este artigo explica como:

- Criar mensagens MSG.
- Criar mensagens MSG com anexos.
- Criar uma mensagem MSG com corpo RTF.
- Salvar uma mensagem como um rascunho.
- Trabalhar com compressão de corpo.
  
## **Criando e Salvando Mensagens do Outlook**

A classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) possui o método [save](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#save-java.lang.String-) que pode salvar arquivos MSG do Outlook no disco ou em um stream. Os trechos de código abaixo criam uma instância da classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/), definem propriedades como de, para, assunto e corpo. O método [save](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#save-java.lang.String-) recebe o nome do arquivo como argumento. Além disso, as Mensagens do Outlook podem ser criadas com um [corpo RTF comprimido](#creating-msg-files-with-rtf-body) usando as [MapiConversionOptions](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/).

1. Crie uma nova instância da classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) e defina as propriedades From, To, Subject e Body.
1. Chame o método [fromMailMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#fromMailMessage-com.aspose.email.MailMessage-) da classe [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) que aceita o objeto do tipo [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). O método [fromMailMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#fromMailMessage-com.aspose.email.MailMessage-) converte o [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) em um [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) (MSG).
1. Chame o método [MapiMessage.save](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#save-java.lang.String-) para salvar o arquivo MSG.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = "outlook/";

// Crie uma instância da classe MailMessage
MailMessage mailMsg = new MailMessage();

// Defina as propriedades de, para, assunto e corpo
mailMsg.setFrom(MailAddress.to_MailAddress("sender@domain.com"));
mailMsg.setTo(MailAddressCollection.to_MailAddressCollection("receiver@domain.com"));
mailMsg.setSubject("Esta é uma mensagem de teste");
mailMsg.setBody("Este é o corpo da mensagem de teste");

// Crie uma instância da classe MapiMessage e passe MailMessage como argumento
MapiMessage outlookMsg = MapiMessage.fromMailMessage(mailMsg);

// Salve a mensagem (arquivo MSG)
String strMsgFile = "CreatingAndSavingOutlookMessages_out.msg";
outlookMsg.save(dataDir + strMsgFile);
~~~ 

## **Criando Arquivos MSG Com Anexos**

[No exemplo acima](#creating-and-saving-outlook-messages), criamos um arquivo MSG simples. Aspose.Email também suporta salvar arquivos de mensagem com anexos. Tudo o que você precisa fazer é adicionar os anexos à instância [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). Adicione anexos chamando o método *addItem* na coleção [MailMessage.Attachments](https://reference.aspose.com/email/java/com.aspose.email/attachmentcollection/).

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = "outlook/";

String[] files = new String[2];
files[0] = "attachment.doc";
files[1] = "attachment.png";

// Crie uma instância da classe MailMessage
MailMessage mailMsg = new MailMessage();

// Defina as propriedades de, para, assunto e corpo
mailMsg.setFrom(MailAddress.to_MailAddress("sender@domain.com"));
mailMsg.setTo(MailAddressCollection.to_MailAddressCollection("receiver@domain.com"));
mailMsg.setSubject("Esta é uma mensagem de teste");
mailMsg.setBody("Este é o corpo da mensagem de teste");

// Adicione os anexos
for (String strFileName : files)
{
    mailMsg.getAttachments().addItem(new Attachment(strFileName));
}

// Crie uma instância da classe MapiMessage e passe MailMessage como argumento
MapiMessage outlookMsg = MapiMessage.fromMailMessage(mailMsg);
String strMsgFile = "CreateMessagesWithAttachments.msg";
outlookMsg.save(dataDir + strMsgFile);
~~~ 

## **Criando Arquivos MSG Com Corpo RTF**

Você também pode criar arquivos de Mensagem do Outlook (MSG) com corpos em texto rico (RTF) com Aspose.Email. O corpo RTF suporta formatação de texto. Crie um definindo a propriedade [MailMessage.HtmlBody](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setHtmlBody-java.lang.String-). Quando você converte uma instância [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) em uma instância [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/), o corpo HTML é convertido em RTF. Dessa forma, a formatação do corpo do e-mail é preservada.

O exemplo a seguir cria um arquivo MSG com um corpo RTF. Há um cabeçalho, formatação em negrito e sublinhado aplicados no corpo HTML. Essa formatação é mantida quando o HTML é convertido em RTF.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = "outlook/";

// Crie uma instância da classe MailMessage
MailMessage mailMsg = new MailMessage();

// Defina as propriedades de, para, assunto e corpo
mailMsg.setFrom(MailAddress.to_MailAddress("sender@domain.com"));
mailMsg.setTo(MailAddressCollection.to_MailAddressCollection("receiver@domain.com"));
mailMsg.setSubject("Esta é uma mensagem de teste");
mailMsg.setHtmlBody("<h3>exemplo rtf</h3><p>criando um <b><u>arquivo de mensagem do outlook (msg)</u></b> usando Aspose.Email.</p>");

MapiMessage outlookMsg = MapiMessage.fromMailMessage(mailMsg);
outlookMsg.save(dataDir + "CreatingMSGFilesWithRTFBody_out.msg");
~~~ 

## **Salvando Mensagem em Status de Rascunho**

E-mails são salvos como rascunhos quando alguém começou a editá-los, mas deseja retorná-los para completá-los mais tarde. Aspose.Email suporta salvar mensagens de e-mail em status de rascunho configurando uma flag de mensagem. Abaixo está o código de exemplo para salvar uma mensagem de e-mail do Outlook (MSG) como um rascunho.

{{% alert %}}
Por favor, note que no status de rascunho, o Outlook não exibe nenhuma informação do remetente atribuída ao MapiMessage.
Se precisarmos exibir informações do remetente, devemos configurar a flag MSGFLAG_READ.
{{% /alert %}}


~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = "outlook/";

// Altere as propriedades de um arquivo MSG existente
String strExistingMsg = "message.msg";

// Carregue o arquivo existente em MailMessage e altere as propriedades
MailMessage msg = MailMessage.load(dataDir + strExistingMsg, new MsgLoadOptions());
msg.setSubject(msg.getSubject() + " NOVO ASSUNTO (atualizado por Aspose.Email)");
msg.setHtmlBody(msg.getHtmlBody() + " NOVO CORPO (atualizado por Aspose.Email)");

// Crie uma instância do tipo MapiMessage a partir de MailMessage, configure a flag da mensagem para não enviada (status de rascunho) e salve
MapiMessage mapiMsg = MapiMessage.fromMailMessage(msg);
mapiMsg.setMessageFlags(MapiMessageFlags.MSGFLAG_UNSENT);
mapiMsg.save(dataDir + "SavingMessageInDraftStatus_out.msg");
~~~ 

## **Implicações da Compressão de Corpo**

O método de compressão de corpo RTF pode ser usado para gerar um MSG de tamanho menor. No entanto, isso resulta em uma velocidade de criação mais lenta. Para criar mensagens com velocidade melhorada, defina a flag como **false**. Essa flag, por sua vez, tem um efeito nos PSTs criados: arquivos MSG menores resultam em PSTs menores, e arquivos MSG grandes resultam em uma criação de PST mais lenta.

~~~Java
// Para exemplos completos e arquivos de dados, acesse https://github.com/aspose-email/Aspose.Email-for-Java
String fileName = "outlook/test.msg";

MailMessage message = MailMessage.load(fileName);
MapiConversionOptions options = new MapiConversionOptions();
options.setUseBodyCompression(true);
MapiMessage ae_mapi = MapiMessage.fromMailMessage(message, options);
~~~