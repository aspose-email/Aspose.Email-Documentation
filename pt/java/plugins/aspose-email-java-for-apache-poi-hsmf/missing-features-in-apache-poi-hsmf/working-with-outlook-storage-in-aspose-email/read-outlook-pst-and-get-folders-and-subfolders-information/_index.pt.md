---
title: "Ler PST do Outlook e Obter Informações sobre Pastas e Subpastas"
url: /pt/java/read-outlook-pst-and-get-folders-and-subfolders-information/
weight: 20
type: docs
---

## **Aspose.Email - Ler PST do Outlook e Obter Informações sobre Pastas e Subpastas**
Aspose.Email para Java permite que você leia arquivos PST do Microsoft Outlook. Você pode carregar um arquivo PST do disco ou fluxo em uma instância da classe [PersonalStorage](https://apireference.aspose.com/email/java/com.aspose.email.class-use/PersonalStorage) e obter informações sobre seu conteúdo, por exemplo, pastas, subpastas e mensagens.

Após carregar o arquivo PST na classe [PersonalStorage](https://apireference.aspose.com/email/java/com.aspose.email.class-use/PersonalStorage), você pode obter informações sobre o nome de exibição do arquivo, pasta raiz, subpastas e contagem de mensagens.

**Java**

```java

 // Carregar o arquivo PST do Outlook

PersonalStorage pst = PersonalStorage.fromFile(dataDir + "personalStorage.pst");
 
// Obter o Nome de Exibição do arquivo PST

System.out.println("Nome de Exibição: " + pst.getDisplayName());
 
// Obter as informações das pastas

FolderInfoCollection folderInfoCollection = pst.getRootFolder().getSubFolders();
 
// Navegar por cada pasta para exibir o nome da pasta e o número de mensagens

for (int i = 0; i < folderInfoCollection.size(); i++)

{

    FolderInfo folderInfo = (FolderInfo) folderInfoCollection.get_Item(i);

    System.out.println("Pasta: " + folderInfo.getDisplayName());

    System.out.println("Total de itens: " + folderInfo.getContentCount());

    System.out.println("Total de itens não lidos: " + folderInfo.getContentUnreadCount());

    System.out.println("-----------------------------------");

}

```
## **Baixar Código em Execução**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/releases/view/618811)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Baixar Código de Exemplo**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/SourceControl/latest#src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/readpstfoldernsubfolders/AsposeReadFoldersSubFoldersOfPST.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/readpstfoldernsubfolders/AsposeReadFoldersSubFoldersOfPST.java)

{{% alert color="primary" %}} 

Para mais detalhes, visite [Ler Arquivo PST do Outlook e Obter Informações sobre Pastas e Subpastas](/email/java/read-outlook-pst-file-and-get-folders-and-subfolders-information/).

{{% /alert %}}