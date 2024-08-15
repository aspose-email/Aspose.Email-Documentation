---
title: "Показать и скрыть дополнительные заголовки для печати с помощью MHTFormatOptions"
url: /ru/java/show-and-hide-extra-print-headers-using-mhtformatoptions/
weight: 40
type: docs
---

## **Aspose.Email - отображение и скрытие дополнительных заголовков для печати с помощью MHTFormatOptions**
Дополнительные заголовки для печати можно показать или скрыть с помощью MhtFormatOptions и MailMessageSaveOptions. MHTFormatOptions — это перечислитель, состоящий из двух элементов: «Записать полный адрес электронной почты в HT» и «HideExtraPrintHeader». MhtFormatOptions используется вместе с MHTMessageFormatter в качестве публичного метода MHTMessageFormatter.Формат с аргументом WriteCompleteEmailAddress теперь устарел.

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
## **Загрузить рабочий код**
Download **Показать и скрыть дополнительные заголовки для печати с помощью MHTFormatOptions** с любого из нижеперечисленных сайтов социального программирования:

- [CodePlex](https://asposeapachepoi.codeplex.com/releases)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases)
