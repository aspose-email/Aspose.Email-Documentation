---
title: FAQs
type: docs
weight: 210
url: /net/faqs/
---

**Question**

Hi! for the following code:

``` java

 Aspose.Email.Mime.ContentType ct = new Aspose.Email.Mime.ContentType();

ct.MediaType = "application/msword";

ct.CharSet = "ISO-2022-JP";

Attachment att = new Attachment("Test.doc", ct);

Console.WriteLine(att.ContentType.Name);

```

att.ContentType.Name returns the name of the attached document. Is this an expected behavior?

**Answer**: 
Yes, it is an expected behavior. If ContentType.Name is not set explicitly, the value of the file name will be taken as a name.

**Question:**

Why is it that ExchangeWebServiceClient.FetchMessage makes the embedded images as attachments?

**Answer**: 
Microsoft Exchange Server has such functionality as '[Content Conversion](http://technet.microsoft.com/en-us/library/bb232174\(EXCHG.80\).aspx), which is the process of correctly formatting a message for each recipient. The decision to perform content conversion on a message depends on the destination and format of the message being processed.

In other words for unknown clients, server can perform message formatting according to server settings(to select most appropriated message format). As you understand, most universal format for any client is 'text/plain' and these settings are configurable on the server.

Please note: Outlook is well known email client for Microsoft Exchange Server (in case if MS Outlook has more older version than server). This means that Exchange Server passes format of message according to capabilities of Outlook. In our case when ExchangeWebServiceClient tries to retrieve message, capabilities of our components unknown for MS Exchange. Server passes message to the components in simplest format (text/plain). In other words there aren't any html parts in server response. In this situation, images are included in message like attachments.

There is a way to avoid the described problem. If message on the server has Content-Type: multipart/alternative and one of its parts is text/plain, in this case this message passes to client as it is. Images in this case are shown in message body because message also contains html part.In current scenario, message is added to MS Exchange with help of MS Outlook and as result Content-Type of message is not 'multipart/alternative'. As result we have a problem when we try to fetch message.For instance here are samples of similar problems: one(<http://support.risualblogs.com/blog/2011/02/24/html-mails-sent-via-owa-and-outlook-2011-are-received-as-plain-text-mails-externally/>), two(<http://forums.mozillazine.org/viewtopic.php?f=39&t=628678>), three(<http://stackoverflow.com/questions/4681798/how-do-i-send-html-multipart-alternative-from-exchange-web-services-2010-sp1)As> a conclusion, situation which is described in issue (images included in message as attachments) is not a bug of aspose components. This is exchenge server specific feature.

**Question:** 
How do I extract data from "oleData.mso" attachment that I get as a result of reading a MapiMessage having OLE object embedded in it?

**Answer**: 
Files like "oleData.mso" refer to Microsoft Compound Document file (MCDF) format and, unfortunately, support for such files is beyond the occupation of Aspose.Email. However, there are certain open source .NET libraries, for example OpenMCDF, which can be used for reading the contents of such files for saving to disc.

**Question:** 
Can we write to the same PST file in Parallel threads using the same objects?

**Answer:** 
No, thread safety is not guarenteed in such case. Messages writing should be done in a single thread. However, the product must work correctly with different objects from different threads.
