---
title: "Converter Arquivo de Pasta Offline do Outlook (OST) para Outros Formatos"
url: /pt/java/convert-outlook-offline-folder-file-ost-to-other-formats/
weight: 20
type: docs
---

## **Aspose.Email - Converter OST para Outros Formatos**
{{% alert color="primary" %}} 

O Microsoft Outlook cria um arquivo PST para armazenamento de e-mail quando você usa servidores de e-mail POP3 ou IMAP para baixar mensagens. Ele cria um arquivo OST quando você usa o Microsoft Exchange como seu servidor de e-mail. OST suporta tamanhos de arquivo maiores em comparação com PST.

{{% /alert %}} 

Aspose.Email torna possível converter um arquivo OST para PST com uma única linha de código. Da mesma forma, um arquivo OST pode ser criado a partir de um arquivo PST usando a mesma linha de código com o enumerador FileFormat.

**Java**

```java

 PersonalStorage ost = PersonalStorage.fromFile(dataDir + "outlook.ost");

ost.saveAs(dataDir + "AsposeOST-PST.pst", FileFormat.Pst);

```
## **Baixar Código em Execução**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Baixar Código de Exemplo**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/conversion/osttopst/AsposeOSTtoPST.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/conversion/osttopst/AsposeOSTtoPST.java)