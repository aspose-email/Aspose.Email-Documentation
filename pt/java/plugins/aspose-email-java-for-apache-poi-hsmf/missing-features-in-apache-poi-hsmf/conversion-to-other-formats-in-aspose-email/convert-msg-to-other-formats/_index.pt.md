---
title: "Converter MSG para Outros Formatos"
url: /pt/java/converter-msg-para-outros-formatos/
weight: 10
type: docs
---

## **Aspose.Email - Converter MSG para Outros Formatos**
Conversão

**Java**

``` java

 // Inicialize e carregue um arquivo MSG existente especificando o MessageFormat

MailMessage msg = MailMessage.load(dataDir + "message.msg");

// Salve a mensagem de email no disco especificando os tipos de salvamento EML e MHT

msg.save(dataDir + "AsposeMessage.eml");

msg.save(dataDir + "Asposemessage.mhtml");

```

Aspose.Email facilita a conversão de qualquer tipo de mensagem para outro formato. Para demonstrar esse recurso, diferentes tipos de mensagens podem ser carregados do disco e salvos novamente em outros formatos. A classe base SaveOptions e as classes EmlSaveOptions, MsgSaveOptions, MhtSaveOptions, HtmlSaveOptions para configurações adicionais ao salvar MailMessage podem ser usadas para salvar mensagens em outros formatos. O artigo mostra como usar essas classes para salvar um e-mail de exemplo como:

- [Formato EML](/email/java/loading-and-saving-message/#loading-eml-and-saving-as-eml)).
- [Outlook MSG](/email/java/loading-and-saving-message/#loading-eml-saving-to-msg).
- [Formato MHTML](/email/java/loading-and-saving-message/#saving-mailmessage-as-mhtml).
- [Formato HTML](/email/java/loading-and-saving-message/#exporting-email-to-eml).

E também mostra como preservar o endereço de e-mail original

- [Preservar Endereço de E-mail Original](/email/java/loading-and-saving-message/)

## **Baixar Código em Execução**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Baixar Código de Exemplo**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/conversion/msgtootherformats/AsposeConverter.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/conversion/msgtootherformats/AsposeConverter.java)