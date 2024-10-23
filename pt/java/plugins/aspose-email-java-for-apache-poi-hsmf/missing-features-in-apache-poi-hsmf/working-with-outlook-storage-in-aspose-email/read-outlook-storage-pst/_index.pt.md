---
title: "Ler Armazenamento PST do Outlook"
url: /pt/java/read-outlook-storage-pst/
weight: 30
type: docs
---

## **Aspose.Email - Ler Armazenamento PST do Outlook**
Um arquivo PST do Outlook pode ser carregado em uma instância da classe [PersonalStorage](https://apireference.aspose.com/email/java/com.aspose.email.class-use/PersonalStorage).

**Java**

``` java

 // Carregar o arquivo PST do Outlook

String pstFileName = dataDir + "archive.pst";

PersonalStorage pst = PersonalStorage.fromFile(pstFileName);

// Obter o Nome de Exibição do arquivo PST

System.out.println("Nome de Exibição: " + pst.getDisplayName());


```
## **Baixar Código em Execução**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Baixar Código de Exemplo**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/readpst/AsposeReadOutlookPST.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/readpst/AsposeReadOutlookPST.java)

{{% alert color="primary" %}} 

Para mais detalhes, visite [Ler Arquivo PST do Outlook e Obter Informações de Pastas e Subpastas](/email/java/read-outlook-pst-file-and-get-folders-and-subfolders-information/).

{{% /alert %}}