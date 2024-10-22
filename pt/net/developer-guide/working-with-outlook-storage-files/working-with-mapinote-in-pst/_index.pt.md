---
title: "Trabalhando com MapiNote em PST"
url: /pt/net/trabalhando-com-mapinote-em-pst/
weight: 80
type: docs
---


## **Adicionando MapiNote ao PST**

O artigo [Criar um Novo Arquivo PST e Adicionar Subpastas](https://docs.aspose.com/email/pt/net/create-new-pst-add-sub-folders-and-messages/#creating-a-new-pst-file-and-add-subfolders) mostra como criar um arquivo PST e adicionar uma subpasta a ele. Com o Aspose.Email, você pode adicionar um [MapiNote](https://reference.aspose.com/email/net/aspose.email.mapi/mapinote/) à subpasta Notas de um arquivo PST que você criou ou carregou. Para adicionar um [MapiNote](https://reference.aspose.com/email/net/aspose.email.mapi/mapinote/) a um PST:

1. Crie um modelo de [MapiNote](https://reference.aspose.com/email/net/aspose.email.mapi/mapinote/) usando o Microsoft Outlook e salve-o como um arquivo MSG.
2. Carregue a nota MSG salva em um objeto [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/).
3. Crie um objeto [MapiNote](https://reference.aspose.com/email/net/aspose.email.mapi/mapinote/) e carregue a nota MSG do modelo.
4. Defina as [propriedades do MapiNote](https://reference.aspose.com/email/net/aspose.email.mapi/mapinote/).
5. Crie um PST usando o método [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create/).
6. Crie uma pasta predefinida (Notas) na raiz do arquivo PST acessando a pasta raiz e, em seguida, chamando o método [AddMapiMessageItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmapimessageitem/#addmapimessageitem).

O seguinte trecho de código mostra como criar um [MapiNote](https://reference.aspose.com/email/net/aspose.email.mapi/mapinote/) e, em seguida, adicioná-lo à pasta de notas de um arquivo PST recém-criado.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddMapiNoteToPST-AddMapiNoteToPST.cs" >}}