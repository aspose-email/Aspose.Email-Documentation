---
title: "Установка Кодировки Текста по Умолчанию в Электронном Сообщении"
url: /ru/java/setting-default-text-encoding-in-email-message/
weight: 120
type: docs
---

В этой статье представлено свойство [MailMessage.PreferredTextEncoding](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage#setPreferredTextEncoding\(java.nio.charset.Charset\)) и объясняется, как его использовать. С помощью этого свойства вы можете установить кодировку текста по умолчанию для следующих свойств:

- От: Отображаемое имя
- Кому: Отображаемое имя
- Тема
- Тело
## **Установка Кодировки Текста по Умолчанию**
В предыдущих версиях Aspose.Email кодировка текста для свойств от, кому, тема и тело устанавливали отдельно. Для улучшения удобства мы добавили свойство [PreferredTextEncoding](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage#setPreferredTextEncoding\(java.nio.charset.Charset\)), которое устанавливает все сразу. Теперь проще убедиться, что весь текст в указанных свойствах закодирован правильно в электронном сообщении. Следующий фрагмент кода показывает, как использовать французское слово в качестве отображаемого имени для адресов электронной почты, темы и тела.

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