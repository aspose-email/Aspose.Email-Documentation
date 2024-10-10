---
title: "Чтение встроенных вложений электронной почты из сообщения в Aspose.Email"
url: /ru/java/read-embedded-email-attachments-from-message-in-aspose-email/
weight: 30
type: docs
---

## **Aspose.Email - Чтение встроенных вложений электронной почты из сообщения**
Иногда мы получаем электронные письма с другими письмами, встроенными в них в качестве вложений. Эти встроенные письма представляют собой полные сообщения с собственным списком получателей, темой, текстом и даже вложениями. Каждое из этих сообщений также может содержать встроенные сообщения.
Используя Aspose.Email Java, разработчики могут получить доступ к каждому встроенному сообщению как к отдельному сообщению. Этот пример демонстрирует использование рекурсивной функциональности.

**Java**

```java

 MailMessage message = MailMessage.load(dataDir + "embedded.msg", MessageFormat.getMsg());

for (int i = 0; i < message.getAttachments().size(); i++)

{

    Attachment att = (Attachment) message.getAttachments().get_Item(i);

    System.out.println("Имя вложения: " + att.getName());

    // Получите имя вложения. Если тема сообщения содержит символы такие как :, /, \ и т.д., замените их пробелом

    // потому что windows не может сохранять файлы с этими символами

    // также сохраните первые 50 символов как имя файла, чтобы избежать длинных имен файлов

    String attFileName = att.getName().replace(".eml", "").replace(":", " ").replace("\\", " ").replace("/", " ").replace("?", "");

    if (attFileName.length() > 50)

    {

        attFileName = attFileName.substring(0, 50);

    }

    String attExt = (att.getName().substring(att.getName().lastIndexOf("."), att.getName().lastIndexOf(".") + 4));

    // Сохраните вложение на диск

    att.save(dataPath + attFileName + attExt);

    // Проверьте, является ли это сиротским текстовым файлом-вложением (ATT00001.txt....) и типом eml

    if ((attExt.equals(".eml")) || (att.getContentType().getMediaType().equals("text/plain") && att.getName().contains(".txt") == true && att.getName().contains("ATT") == true))

    {

        // Попробуйте загрузить этот текстовый файл в MailMessage

        MailMessage attMsg = MailMessage.load(dataPath + attFileName + attExt, MessageFormat.getEml());

        // Вызовите функцию рекурсивно, чтобы разобрать это сообщение и вложения

        ParseMessage(attMsg);

    }

}

```
## **Скачать работающий код**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Скачать образец кода**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/programmingemail/readembeddedattachments/AsposeReadEmbeddedAttachments.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/programmingemail/readembeddedattachments/AsposeReadEmbeddedAttachments.java)

{{% alert color="primary" %}} 

Для получения дополнительной информации посетите [Чтение встроенных вложений электронной почты из сообщения](/email/java/working-with-attachments-and-embedded-objects/).

{{% /alert %}}