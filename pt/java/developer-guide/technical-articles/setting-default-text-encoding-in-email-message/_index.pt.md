---
title: "Configurando a Codificação de Texto Padrão em Mensagens de E-mail"
url: /pt/java/setting-default-text-encoding-in-email-message/
weight: 120
type: docs
---


Este artigo introduz a propriedade [MailMessage.PreferredTextEncoding](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage#setPreferredTextEncoding\(java.nio.charset.Charset\)) e explica como ela é usada. Usando esta propriedade, você pode definir a codificação de texto padrão para as seguintes propriedades:

- De: Nome de exibição
- Para: Nome de exibição
- Assunto
- Corpo
## **Configurando a Codificação de Texto Padrão**
Nas versões anteriores do Aspose.Email, a codificação de texto para as propriedades de de, para, assunto e corpo era definida separadamente. Para melhorar a usabilidade, adicionamos a propriedade [PreferredTextEncoding](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage#setPreferredTextEncoding\(java.nio.charset.Charset\)) que define todas de uma vez. Agora é mais fácil garantir que todo o texto nas propriedades acima esteja codificado corretamente na mensagem de e-mail. O seguinte trecho de código mostra como usar uma palavra francesa como nome de exibição para endereços de e-mail, assunto e corpo.



~~~Java
// Create an instance of MailMessage
String fileName = "data/";
MailMessage msg = new MailMessage();

// Set the default or preferred encoding. This encoding will be used as the default for the from/to email addresses, subject and body of message.
msg.setPreferredTextEncoding(Charset.forName("cp1252"));

// Set email addresses, subject and body
msg.setFrom(new MailAddress("dmo@domain.com", "démo"));
msg.getTo().addItem(new MailAddress("dmo@domain.com", "démo"));
msg.setSubject("démo");
msg.setHtmlBody("démo");
msg.save(fileName + "SetDefaultTextEncoding_out.msg", SaveOptions.getDefaultMsg());
~~~