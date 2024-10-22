---
title: "Gerenciando Mensagens Assinadas Digitalmente"
url: /pt/java/working-with-outlook-notes/
weight: 100
type: docs
---

Aspose.Email implementa o algoritmo completo do objeto de email S/MIME. Isso dá à API total poder para adicionar assinaturas digitais a mensagens de email, preservá-las ao converter mensagens entre formatos, removê-las, etc.

## **Anexar uma Assinatura a um Email**

O método [SecureEmailManager.attachSignature](https://reference.aspose.com/email/java/com.aspose.email/secureemailmanager/#attachSignature-com.aspose.email.MapiMessage-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-com.aspose.email.SignatureOptions-) permite anexar assinaturas digitais a mensagens de email. Após anexar a assinatura, verifique os resultados por meio de propriedades como [IsSigned](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#isSigned--), [MessageClass](https://reference.aspose.com/email/java/com.aspose.email/knownpropertylist/#MESSAGE-CLASS), e detalhes do anexo.

Você pode fornecer um MailMessage ou MapiMessage, um certificado privado e opções de assinatura para personalizar o processo de anexação de assinatura com a classe [SignatureOptions](https://reference.aspose.com/email/java/com.aspose.email/signatureoptions/) que permite aos usuários especificar várias opções para a anexação de assinatura, incluindo assinaturas destacadas ou não destacadas.

O seguinte exemplo de código mostrará como carregar uma mensagem de um arquivo, anexar uma assinatura digital destacada e não destacada usando um certificado privado e, em seguida, verificar se as assinaturas foram anexadas com sucesso.

```java
String fileName = "message.msg";
String privateCertFile = "certFile.pfx";
X509Certificate2 privateCert = new X509Certificate2(privateCertFile, "password");

MapiMessage msg = MapiMessage.load(fileName);

SignatureOptions opt = new SignatureOptions();
opt.setDetached(true);
MapiMessage signedDetached = new SecureEmailManager().attachSignature(msg, privateCert, opt);

if (signedDetached.isSigned()) {
    System.out.println("Assinatura Destacada Anexada com Sucesso.");
}

opt.setDetached(false);
MapiMessage signedNonDetached = new SecureEmailManager().attachSignature(msg, privateCert, opt);

if (signedNonDetached.isSigned()) {
    System.out.println("Assinatura Não Destacada Anexada com Sucesso.");
}
```

## **Preservando a Assinatura ao Converter de EML para MSG**

Aspose.Email preserva a assinatura digital ao converter de EML para MSG. O seguinte trecho de código mostra como converter de EML para MSG.

~~~Java
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = "outlook/";

// Carregar mensagem de email
MailMessage message = MailMessage.load(dataDir + "Message.eml", new EmlLoadOptions());
// Salvar como MSG
message.save(dataDir + "ConvertEMLToMSG_out.msg", SaveOptions.getDefaultMsgUnicode());
~~~
## **Remover Assinatura de um Arquivo de Mensagem do Outlook**

Se você está enfrentando a necessidade de remover a assinatura de uma mensagem em um formato MAPI, por exemplo, por motivos de compatibilidade, Aspose.Email oferece o método [MapiMessage.removeSignature](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#removeSignature--) e a propriedade [MapiMessage.isSigned](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#isSigned--).

O seguinte trecho de código mostra como carregar uma mensagem MAPI de um arquivo, verificar se está assinada digitalmente e, se estiver, criar uma nova mensagem sem a assinatura digital:

```java
MapiMessage msg = MapiMessage.load(fileName);

if (msg.isSigned()) {
    MapiMessage unsignedMsg = msg.removeSignature();
}
```
## **Convertendo Mensagens S/MIME de MSG para EML**

Aspose.Email preserva a assinatura digital ao converter de MSG para EML, como mostrado no seguinte trecho de código.

~~~Java
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-Java
// O caminho para o diretório de arquivos.
String dataDir = "outlook/";

MailMessage msg = MailMessage.load(dataDir + "message.eml");
MapiMessage mapi = MapiMessage.fromMailMessage(msg, new MapiConversionOptions(OutlookMessageFormat.Unicode));
// Salvar arquivo no disco
mapi.save(dataDir + "ConvertMIMEMessagesFromMSGToEML_out.msg");
~~~

## **Descriptografar um Arquivo MSG com Certificado**

Se você tem mensagens MAPI criptografadas e precisa descriptografá-las usando a chave privada armazenada em um certificado, os seguintes recursos do Aspose.Email podem ser úteis:

- [MapiMessage.isEncrypted](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#isEncrypted--) - Obtém um valor que indica se a mensagem está criptografada.
- [MapiMessage.decrypt()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#decrypt--) - Descriptografa esta mensagem (o método procura os armazenamentos de certificados e chaves privadas apropriados para o usuário e computador atuais).
- [MapiMessage.decrypt(X509Certificate2 certificate)](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#decrypt-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-) - Descriptografa esta mensagem com o certificado.

O seguinte trecho de código mostra como trabalhar com mensagens MAPI criptografadas:

```java
X509Certificate2 privateCert = new X509Certificate2("privateCertFile", "password");
MapiMessage msg = MapiMessage.load("encrypted.msg");

if (msg.isEncrypted()) {
    MapiMessage decryptedMsg = msg.decrypt(privateCert);
    //MapiMessage decryptedMsg = msg.decrypt(/*byte[]*/rawPrivateCert, "password");
}
```