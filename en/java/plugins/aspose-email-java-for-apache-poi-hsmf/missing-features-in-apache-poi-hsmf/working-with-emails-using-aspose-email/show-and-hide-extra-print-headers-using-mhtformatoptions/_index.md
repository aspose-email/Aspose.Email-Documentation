---
title: Show and Hide Extra Print Headers using MHTFormatOptions
type: docs
weight: 40
url: /java/show-and-hide-extra-print-headers-using-mhtformatoptions/
---

## **Aspose.Email - Show and Hide Extra Print Headers using MHTFormatOptions**
Extra print headers can be shown or hidden with MhtFormatOptions and MailMessageSaveOptions. MhtFormatOptions is an enumerator which contains two members - WriteCompleteEmailAddressToMht and HideExtraPrintHeader. MhtFormatOptions is used with MhtMessageFormatter as the public method MhtMessageFormatter.Format with argument writeCompleteEmailAddress is obsolete now.

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
## **Download Running Code**
Download **Show and Hide Extra Print Headers using MHTFormatOptions** from any of the below mentioned social coding sites:

- [CodePlex](https://asposeapachepoi.codeplex.com/releases)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases)
