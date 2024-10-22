---
title: "Cambios en la API Pública en Aspose.Email 5.2.0"
url: /es/java/public-api-changes-in-aspose-email-5-2-0/
weight: 130
type: docs
---

La siguiente es una lista de los cambios realizados en la API pública, tales como miembros añadidos, renombrados, eliminados o desaprobados, así como cualquier cambio no compatible con versiones anteriores realizado en Aspose.Email para .NET. Si tiene preocupaciones sobre algún cambio listado, por favor plantee su inquietud en el foro de soporte de Aspose.Email.

## **APIs Añadidas**

- Clase `CanonicalizationType`
- Clase `DKIMHashAlgorithm`
- Clase `DKIMSignatureInfo`
- Clase `HeaderList`
- Clase `PemReader`

- Campo/Enum `CanonicalizationType.Relaxed`
- Campo/Enum `CanonicalizationType.Simple`
- Campo/Enum `DKIMHashAlgorithm.RSASha1`
- Campo/Enum `DKIMHashAlgorithm.RSASha256`

- Método `DKIMSignatureInfo.#ctor(String publicKeyDnsSelector, String publicKeyDnsDomain)`
- Propiedad `DKIMSignatureInfo.getBodyCanonicalization(), setBodyCanonicalization(int value)`
- Propiedad `DKIMSignatureInfo.getDomain(), setDomain(String value)`
- Propiedad `DKIMSignatureInfo.getHashAlgorithm, setHashAlgorithm(int value)`
- Propiedad `DKIMSignatureInfo.getHeaderCanonicalization(), setHeaderCanonicalization(int value)`
- Propiedad `DKIMSignatureInfo.getHeaders()`
- Propiedad `DKIMSignatureInfo.getSelector(), setSelector(String value)`
- Propiedad `DKIMSignatureInfo.getTime(), setTime(DateTime value)`

- Método `HeaderList.#ctor`
- Método `PemReader.GetPrivateKey(InputStream pem)`
- Método `PemReader.GetPrivateKey(String path)`

- Método `MailMessage.dKIMSign(RSACryptoServiceProvider rsa, DKIMSignatureInfo signatureInfo)`

- Clase `TokenProvider`
- Clase `TokenProvider.Google`
- Clase `TokenProvider.Outlook`
- Método `BaseTokenProvider.#ctor`
- Método `TokenProvider.dispose()`
- Método `TokenProvider.getAccessToken()`
- Método `TokenProvider.getAccessToken(boolean)`
- Método `TokenProvider.getInstance(String,String,String,String)`
- Método `TokenProvider.Google.getInstance(String,String,String)`
- Método `TokenProvider.Outlook.getInstance(String,String,String)`
- Propiedad `TokenProvider.getClientId`
- Propiedad `TokenProvider.getClientSecret`
- Propiedad `TokenProvider.getExtraParameters`
- Propiedad `TokenProvider.getLogin`
- Propiedad `TokenProvider.getPassword`
- Propiedad `TokenProvider.getRefreshToken`
- Propiedad `TokenProvider.getRequestUrl`
- Propiedad `TokenProvider.getUseBasicAuthorization`

- Método `ImapQueryBuilder.#ctor(Encoding)`
- Método `MailQueryBuilder.#ctor(Encoding)`
- Propiedad `MailQueryBuilder.getDefaultEncoding()`