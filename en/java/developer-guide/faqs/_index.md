---
title: FAQs
ArticleTitle: FAQs
type: docs
weight: 220
url: /java/faqs/
---

**Question**

Hi! for the following code:

~~~Java

ContentType ct = new ContentType();

ct.setMediaType("application/msword");

ct.setCharSet("ISO-2022-JP");

Attachment att = new Attachment("Test.doc", ct);

System.out.println(att.getContentType().getName());

~~~

att.getContentType().getName() returns the name of the attached document. Is this an expected behavior?

**Answer**: 
Yes, it is an expected behavior. If getContentType().getName() is not set explicitly, the value of the file name will be taken as a name.

**Question:** 
How do I extract data from "oleData.mso" attachment that I get as a result of reading a MapiMessage having OLE object embedded in it?

**Answer**: 
Files like "oleData.mso" refer to Microsoft Compound Document file (MCDF) format and, unfortunately, support for such files is beyond the occupation of Aspose.Email. However, there are certain open source .NET libraries, for example OpenMCDF, which can be used for reading the contents of such files for saving to disc.

**Question:** 
Can we write to the same PST file in Parallel threads using the same objects?

**Answer:** 
No, thread safety is not guarenteed in such case. Messages writing should be done in a single thread. However, the product must work correctly with different objects from different threads.
