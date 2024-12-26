---
title: Public API Changes in Aspose.Email 5.2.0
ArticleTitle: Public API Changes in Aspose.Email 5.2.0
type: docs
weight: 130
url: /java/public-api-changes-in-aspose-email-5-2-0/
---

The following is a list of any changes made to the public API such as added, renamed, removed or deprecated members as well as any non-backward compatible change made to Aspose.Email for .NET. If you have concerns about any change listed, please raise it on the Aspose.Email support forum.
## **Added APIs**
Class CanonicalizationType
Class DKIMHashAlgorithm
Class DKIMSignatureInfo
Class HeaderList
Class PemReader

Field/Enum CanonicalizationType.Relaxed
Field/Enum CanonicalizationType.Simple
Field/Enum DKIMHashAlgorithm.RSASha1
Field/Enum DKIMHashAlgorithm.RSASha256

Method DKIMSignatureInfo.#ctor(String publicKeyDnsSelector, String publicKeyDnsDomain)
Property DKIMSignatureInfo.getBodyCanonicalization(), setBodyCanonicalization(int value)
Property DKIMSignatureInfo.getDomain(), setDomain(String value)
Property DKIMSignatureInfo.getHashAlgorithm, setHashAlgorithm(int value)
Property DKIMSignatureInfo.getHeaderCanonicalization(), setHeaderCanonicalization(int value)
Property DKIMSignatureInfo.getHeaders()
Property DKIMSignatureInfo.getSelector(), setSelector(String value)
Property DKIMSignatureInfo.getTime(), setTime(DateTime value)

Method HeaderList.#ctor
Method PemReader.GetPrivateKey(InputStream pem)
Method PemReader.GetPrivateKey(String path)

Method MailMessage.dKIMSign(RSACryptoServiceProvider rsa, DKIMSignatureInfo signatureInfo)

Class TokenProvider
Class TokenProvider.Google
Class TokenProvider.Outlook
Method BaseTokenProvider.#ctor
Method TokenProvider.dispose()
Method TokenProvider.getAccessToken()
Method TokenProvider.getAccessToken(boolean)
Method TokenProvider.getInstance(String,String,String,String)
Method TokenProvider.Google.getInstance(String,String,String)
Method TokenProvider.Outlook.getInstance(String,String,String)
Property TokenProvider.getClientId
Property TokenProvider.getClientSecret
Property TokenProvider.getExtraParameters
Property TokenProvider.getLogin
Property TokenProvider.getPassword
Property TokenProvider.getRefreshToken
Property TokenProvider.getRequestUrl
Property TokenProvider.getUseBasicAuthorization

Method ImapQueryBuilder.#ctor(Encoding)
Method MailQueryBuilder.#ctor(Encoding)
Property MailQueryBuilder.getDefaultEncoding()
