---
title: "Настройка кодировки текста по умолчанию в сообщении электронной почты"
url: /ru/java/setting-default-text-encoding-in-email-message/
weight: 120
type: docs
---


В этой статье представлены [MailMessage.PreferredTextEncoding](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage#setPreferredTextEncoding\(java.nio.charset.Charset\)) свойство и объясняет, как оно используется. С помощью этого свойства можно задать кодировку текста по умолчанию для следующих свойств:

- Откуда: Отображаемое имя
- Кому: Отображаемое имя
- Subject
- Body
## **Настройка кодировки текста по умолчанию**
В предыдущих версиях Aspose.Email кодировка текста для свойств «от», «до», «тема» и «тело» задавалась отдельно. Чтобы повысить удобство использования, мы добавили [PreferredTextEncoding](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage#setPreferredTextEncoding\(java.nio.charset.Charset\)) свойство, которое устанавливает все сразу. Теперь стало проще убедиться, что весь текст в вышеуказанных свойствах правильно закодирован в сообщении электронной почты. В следующем фрагменте кода показано, как использовать французское слово в качестве отображаемого имени для адресов электронной почты, темы и текста.



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