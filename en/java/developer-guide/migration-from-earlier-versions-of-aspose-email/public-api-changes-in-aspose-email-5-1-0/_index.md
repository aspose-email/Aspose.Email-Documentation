---
title: Public API Changes in Aspose.Email 5.1.0
type: docs
weight: 120
url: /java/public-api-changes-in-aspose-email-5-1-0/
---

The following is a list of any changes made to the public API such as added, renamed, removed or deprecated members as well as any non-backward compatible change made to Aspose.Email for .NET. If you have concerns about any change listed, please raise it on the Aspose.Email support forum.
## **Added APIs**
Class BaseTokenProvider
Class OutlookTokenProvider

Method HeaderCollection.getDecodedValue(String)

Method BaseTokenProvider.getAccessToken()
Method BaseTokenProvider.getAccessToken(boolean)
Method OutlookTokenProvider.getInstance(String,String,String)

Property MailMessage.getHtmlBodyText
Property BaseTokenProvider.getClientId()
Property BaseTokenProvider.getClientSecret()
Property BaseTokenProvider.getRefreshToken()
Property MapiConversionOptions.getPreserveOriginalAddresses(), MapiConversionOptions.setPreserveOriginalAddresses(boolean)
## **Removed APIs**
Method GoogleTokenProvider.getAccessToken()
Method GoogleTokenProvider.getAccessToken(boolean)
Method AppointmentMailMessageInterpretor.loadMessageHeader(MailMessage,MapiMessage)
Property GoogleTokenProvider.getClientId()
Property GoogleTokenProvider.getClientSecret()
Property GoogleTokenProvider.getRefreshToken()
