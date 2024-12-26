---
title: Comparison of Aspose.Email.Mail with MS APIs
ArticleTitle: Comparison of Aspose.Email.Mail with MS APIs
type: docs
weight: 20
url: /net/comparison-of-aspose-email-mail-with-ms-apis/
---

## **Comparison of Aspose Email Mail with MS APIs**
System.Web.Mail is simply a wrapper around two COM libraries: CDONTS.NewMail (found in the cdonts.dll) and CDO.Message (found in the cdosys.dll). You will also need them installed on your server. By default, cdonts.dll and cdosys.dll are installed with WindowsNT/2000/XP/2003.
### **SmtpMail Specifics**
If you trace into the class System.Web.Mail.SmtpMail, you'll find some odd behaviors:

- It only supports Win32NT operation systems, for example, windows 2000, windows 2003, windows XP.
- When the SmtpMail class sends a mail message, it checks the OS version. If the version is <= 4, the CDONTS.Newmail object is used; for all operating systems greater than 4, the CDO.Message object is used.

These peculiarities makes troubleshooting much more difficult, especially when moving code to different operating systems. The application may get unexpected results on different OSs. Aspose.Email.Mail is a .NET component written in fully managed code in pure C#. It has zero reliance on any COM libraries, including CDONTS.NewMail, or CDO.Message. With Aspose.Email.Mail you avoid invoking any unmanaged code in your applications, increasing reliability and freeing yourself from boring COM debugging. Aspose.Email.Mail is feature rich and provides many more services than those provided by the System.Web.Mail architecture. System.Net.Mail is a new SMTP protocol client implementation in .NET 2.0. It is also a pure managed code implementation in C#.
### **Comparision Matrix**

|**Features** |**Aspose.Email.Mail** |**System.Web.Mail** |**System.Net.Mail** |
| :- | :- | :- | :- |
|Compatibility Features | | | |
|Supports .NET 2.0 |X |X |X |
|Common Features | | | |
|CDO/CDONTS Dependency | |X | |
|Pure Managed Code |X | |X |
|Authentication |X |X |X |
|Sender address |X |X |X |
|Recipients address |X |X |X |
|HTML Body |X |X |X |
|Text Body |X |X |X |
|Bcc/Cc |X |X |X |
|Send Attachment |X |X |X |
|Linked Image |X | |X |
|Body Encoding (Unicode/ASCII) |X |X |X |
|Subject Encoding (Unicode/ASCII) |X | |X |
|Synchronous programming model |X | |X |
|Asynchronous programming model |X | |X |
|Unique Features | | | |
|Customized Mail Header |X | | |
|Importance Header |X | | |
|Sensitivity Header |X | | |
|X-Mailer Header |X | | |
|Reply to |X | | |
|Send Date |X | | |
|Template-based Mail Merge |X | | |
|Mail Merge from DataSet |X | | |
|Mail Merge from DataTable |X | | |
|Mail Merge from DataReader |X | | |
|Bulk Send with Multi-threading |X | | |
|Send Calendar |X | | |
|Send Meeting request |X | | |
|Load from Microsoft Msg format |X | | |
|Load from Microsoft Mht format |X | | |
|Save to Microsoft Mht format |X | | |
|Save to Eml format |X | | |
|Load from Eml format |X | | |
|Load from RFC 822 compliant file |X | | |
|Interoperation Features | | | |
|Works with Aspose.Email.Pop3 |X | | |
|Works with Aspose.Email.Imap |X | | |
|Works with Aspose.Email.Mime |X | | |

