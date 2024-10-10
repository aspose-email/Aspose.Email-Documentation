---
title: "Изменения в публичном API в Aspose.Email 5.2.0"
url: /ru/java/public-api-changes-in-aspose-email-5-2-0/
weight: 130
type: docs
---

В следующем списке перечислены все изменения, внесенные в публичный API, такие как добавленные, переименованные, удаленные или устаревшие члены, а также любые изменения, несовместимые с предыдущими версиями, внесенные в Aspose.Email для .NET. Если у вас есть замечания по поводу какого-либо изменения из списка, пожалуйста, сообщите об этом на форуме поддержки Aspose.Email.

## **Добавленные API**

- Класс `CanonicalizationType`
- Класс `DKIMHashAlgorithm`
- Класс `DKIMSignatureInfo`
- Класс `HeaderList`
- Класс `PemReader`

- Поле/Перечисление `CanonicalizationType.Relaxed`
- Поле/Перечисление `CanonicalizationType.Simple`
- Поле/Перечисление `DKIMHashAlgorithm.RSASha1`
- Поле/Перечисление `DKIMHashAlgorithm.RSASha256`

- Метод `DKIMSignatureInfo.#ctor(String publicKeyDnsSelector, String publicKeyDnsDomain)`
- Свойство `DKIMSignatureInfo.getBodyCanonicalization(), setBodyCanonicalization(int value)`
- Свойство `DKIMSignatureInfo.getDomain(), setDomain(String value)`
- Свойство `DKIMSignatureInfo.getHashAlgorithm, setHashAlgorithm(int value)`
- Свойство `DKIMSignatureInfo.getHeaderCanonicalization(), setHeaderCanonicalization(int value)`
- Свойство `DKIMSignatureInfo.getHeaders()`
- Свойство `DKIMSignatureInfo.getSelector(), setSelector(String value)`
- Свойство `DKIMSignatureInfo.getTime(), setTime(DateTime value)`

- Метод `HeaderList.#ctor`
- Метод `PemReader.GetPrivateKey(InputStream pem)`
- Метод `PemReader.GetPrivateKey(String path)`

- Метод `MailMessage.dKIMSign(RSACryptoServiceProvider rsa, DKIMSignatureInfo signatureInfo)`

- Класс `TokenProvider`
- Класс `TokenProvider.Google`
- Класс `TokenProvider.Outlook`
- Метод `BaseTokenProvider.#ctor`
- Метод `TokenProvider.dispose()`
- Метод `TokenProvider.getAccessToken()`
- Метод `TokenProvider.getAccessToken(boolean)`
- Метод `TokenProvider.getInstance(String,String,String,String)`
- Метод `TokenProvider.Google.getInstance(String,String,String)`
- Метод `TokenProvider.Outlook.getInstance(String,String,String)`
- Свойство `TokenProvider.getClientId`
- Свойство `TokenProvider.getClientSecret`
- Свойство `TokenProvider.getExtraParameters`
- Свойство `TokenProvider.getLogin`
- Свойство `TokenProvider.getPassword`
- Свойство `TokenProvider.getRefreshToken`
- Свойство `TokenProvider.getRequestUrl`
- Свойство `TokenProvider.getUseBasicAuthorization`

- Метод `ImapQueryBuilder.#ctor(Encoding)`
- Метод `MailQueryBuilder.#ctor(Encoding)`
- Свойство `MailQueryBuilder.getDefaultEncoding()`