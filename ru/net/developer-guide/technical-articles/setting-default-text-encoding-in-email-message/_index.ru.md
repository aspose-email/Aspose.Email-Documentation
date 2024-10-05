---
title: "Установка кодировки текста по умолчанию в email-сообщении"
url: /ru/net/setting-default-text-encoding-in-email-message/
weight: 120
type: docs
---


В этой статье представлено свойство [MailMessage.PreferredTextEncoding](http://www.aspose.com/api/net/email/aspose.email/mailmessage/properties/preferredtextencoding) и объясняется, как оно используется. С помощью этого свойства вы можете установить кодировку текста по умолчанию для следующих свойств:

- From: Имя отправителя
- To: Имя получателя
- Subject: Тема
- Body: Тело
## **Установка кодировки текста по умолчанию**
В предыдущих версиях Aspose.Email кодировка текста для свойств from, to, subject и body задавалась отдельно. Для улучшения удобства использования мы добавили свойство [PreferredTextEncoding](http://www.aspose.com/api/net/email/aspose.email/mailmessage/properties/preferredtextencoding), которое устанавливает все сразу. Теперь проще гарантировать, что весь текст в вышеуказанных свойствах правильно закодирован в email-сообщении. Следующий код демонстрирует, как использовать французское слово в качестве имени отправителя, темы и тела email-адресов.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Email-SetDefaultTextEncoding-SetDefaultTextEncoding.cs" >}}