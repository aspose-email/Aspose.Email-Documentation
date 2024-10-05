---
title: Показать и скрыть дополнительные заголовки печати с использованием MHTFormatOptions
type: docs
weight: 40
url: /java/show-and-hide-extra-print-headers-using-mhtformatoptions/
---

## **Aspose.Email - Показать и скрыть дополнительные заголовки печати с использованием MHTFormatOptions**
Дополнительные заголовки печати можно показать или скрыть с помощью MhtFormatOptions и MailMessageSaveOptions. MhtFormatOptions - это перечисление, которое содержит два члена - WriteCompleteEmailAddressToMht и HideExtraPrintHeader. MhtFormatOptions используется с MhtMessageFormatter, так как публичный метод MhtMessageFormatter.Format с аргументом writeCompleteEmailAddress теперь устарел.

**Java**

```java

 String dataPath = "src/asposefeatures/programmingemail/showhideextraprintheaders/data/";

String pageHeader = "<div><div class='pageHeader'>&quot;Panditharatne, Mithra&quot; &lt;mithra.panditharatne@cibc.com&gt;<hr/></div>";

MailMessage message = MailMessage.load(dataPath + "message.eml");

MhtMessageFormatter mailFormatter = new MhtMessageFormatter();

int options =  MhtFormatOptions.HideExtraPrintHeader | MhtFormatOptions.WriteCompleteEmailAddressToMht;

mailFormatter.format(message, options);

if(!message.getHtmlBody().contains(pageHeader))

	System.out.println("True");

else

	System.out.println("False");

```
## **Скачать работающий код**
Скачайте **Показать и скрыть дополнительные заголовки печати с использованием MHTFormatOptions** с любого из указанных ниже сайтов социального программирования:

- [CodePlex](https://asposeapachepoi.codeplex.com/releases)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases)