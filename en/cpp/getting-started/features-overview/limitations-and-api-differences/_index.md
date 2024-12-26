---
title: Limitations and API Differences
ArticleTitle: Limitations and API Differences
type: docs
weight: 10
url: /cpp/limitations-and-api-differences/
description: C++ Email Parser Library has some differences as compared to its equivalent .NET version. This page contains information about all such functionality that is not available in the API.
---

Aspose.Email for C++ has some differences as compared to its equivalent .NET version of the API. This page contains information about all such functionality that is not available in the API.
## **API Limitations**
Aspose.Email for C++ has following limitations that make it different from other APIs of Aspose.Email Product family. These are:

- At the moment, the API supports given below communication protocols:
  - SMTP
  - POP3
  - IMAP
- The API doesn't support Exchange (WebDav as well as EWS)
- No support for Thunderbird MBox file formats
- It doesn't support Message Encryption/Decryption
- Support for conversion of MapiMessage to MailMessage is also not present
- Receive notifications and Read Receipts
- Creating TNEF emails form MSG files
- Detecting message type is also not supported
- Working with recurrences including EndAfterNoccurrences, WeeklyEndAfterNoccurrences, EndAfterNoccurrenceSelectMultipleDaysInweek, MonthlyEndAfterNoccurrences
- Detecting Message as TNEF
- Detecting Embedded message using Embedded flag
- Remove Linked Resources at specific location
- Rendering calendar events based on format templates
- Deleting children items from folders of PST file
- Changing message properties in PST's Folder using ChangeMessages
