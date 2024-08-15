---
title: "Настройка кодировки текста по умолчанию в сообщении электронной почты"
url: /ru/net/setting-default-text-encoding-in-email-message/
weight: 120
type: docs
---


В этой статье представлены [MailMessage.PreferredTextEncoding](http://www.aspose.com/api/net/email/aspose.email/mailmessage/properties/preferredtextencoding) свойство и объясняет, как оно используется. С помощью этого свойства можно задать кодировку текста по умолчанию для следующих свойств:

- Откуда: Отображаемое имя
- Кому: Отображаемое имя
- Subject
- Body
## **Настройка кодировки текста по умолчанию**
В предыдущих версиях Aspose.Email кодировка текста для свойств «от», «до», «тема» и «тело» задавалась отдельно. Чтобы повысить удобство использования, мы добавили [PreferredTextEncoding](http://www.aspose.com/api/net/email/aspose.email/mailmessage/properties/preferredtextencoding) свойство, которое устанавливает все сразу. Теперь стало проще убедиться, что весь текст в вышеуказанных свойствах правильно закодирован в сообщении электронной почты. В следующем фрагменте кода показано, как использовать французское слово в качестве отображаемого имени для адресов электронной почты, темы и текста.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Email-SetDefaultTextEncoding-SetDefaultTextEncoding.cs" >}}
