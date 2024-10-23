---
title: "Mudanças na API Pública no Aspose.Email 5.2.0"
url: /pt/java/public-api-changes-in-aspose-email-5-2-0/
weight: 130
type: docs
---

A seguir está uma lista de quaisquer alterações feitas na API pública, como membros adicionados, renomeados, removidos ou obsoletos, bem como qualquer alteração não compatível com versões anteriores feita no Aspose.Email para .NET. Se você tiver preocupações sobre alguma alteração listada, por favor, levante-a no fórum de suporte do Aspose.Email.

## **APIs Adicionadas**

- Classe `CanonicalizationType`
- Classe `DKIMHashAlgorithm`
- Classe `DKIMSignatureInfo`
- Classe `HeaderList`
- Classe `PemReader`

- Campo/Enum `CanonicalizationType.Relaxed`
- Campo/Enum `CanonicalizationType.Simple`
- Campo/Enum `DKIMHashAlgorithm.RSASha1`
- Campo/Enum `DKIMHashAlgorithm.RSASha256`

- Método `DKIMSignatureInfo.#ctor(String publicKeyDnsSelector, String publicKeyDnsDomain)`
- Propriedade `DKIMSignatureInfo.getBodyCanonicalization(), setBodyCanonicalization(int value)`
- Propriedade `DKIMSignatureInfo.getDomain(), setDomain(String value)`
- Propriedade `DKIMSignatureInfo.getHashAlgorithm, setHashAlgorithm(int value)`
- Propriedade `DKIMSignatureInfo.getHeaderCanonicalization(), setHeaderCanonicalization(int value)`
- Propriedade `DKIMSignatureInfo.getHeaders()`
- Propriedade `DKIMSignatureInfo.getSelector(), setSelector(String value)`
- Propriedade `DKIMSignatureInfo.getTime(), setTime(DateTime value)`

- Método `HeaderList.#ctor`
- Método `PemReader.GetPrivateKey(InputStream pem)`
- Método `PemReader.GetPrivateKey(String path)`

- Método `MailMessage.dKIMSign(RSACryptoServiceProvider rsa, DKIMSignatureInfo signatureInfo)`

- Classe `TokenProvider`
- Classe `TokenProvider.Google`
- Classe `TokenProvider.Outlook`
- Método `BaseTokenProvider.#ctor`
- Método `TokenProvider.dispose()`
- Método `TokenProvider.getAccessToken()`
- Método `TokenProvider.getAccessToken(boolean)`
- Método `TokenProvider.getInstance(String,String,String,String)`
- Método `TokenProvider.Google.getInstance(String,String,String)`
- Método `TokenProvider.Outlook.getInstance(String,String,String)`
- Propriedade `TokenProvider.getClientId`
- Propriedade `TokenProvider.getClientSecret`
- Propriedade `TokenProvider.getExtraParameters`
- Propriedade `TokenProvider.getLogin`
- Propriedade `TokenProvider.getPassword`
- Propriedade `TokenProvider.getRefreshToken`
- Propriedade `TokenProvider.getRequestUrl`
- Propriedade `TokenProvider.getUseBasicAuthorization`

- Método `ImapQueryBuilder.#ctor(Encoding)`
- Método `MailQueryBuilder.#ctor(Encoding)`
- Propriedade `MailQueryBuilder.getDefaultEncoding()`