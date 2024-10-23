---
title: "Trabalhando com MapiJournal em PST"
url: /pt/net/trabalhando-com-mapijournal-em-pst/
weight: 70
type: docs
---


## **Adicionando MapiJournal ao PST**

O artigo [Criar um Novo Arquivo PST e Adicionar Subpastas](https://docs.aspose.com/email/pt/net/create-new-pst-add-sub-folders-and-messages/#creating-a-new-pst-file-and-add-subfolders) mostra como criar um arquivo PST e adicionar uma subpasta a ele. Com Aspose.Email, você pode adicionar [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/) à subpasta Journal de um arquivo PST que você criou ou carregou. Abaixo estão os passos para adicionar [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/) a um PST:

1. Crie um objeto [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/)
2. Defina as propriedades do [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/) usando um construtor e métodos.
3. Crie um PST usando o método [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create/).
4. Crie uma pasta pré-definida (Journals) na raiz do arquivo PST acessando a pasta raiz e chamando o método [AddMapiMessageItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmapimessageitem/#addmapimessageitem).

O seguinte trecho de código mostra como criar um [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/) e então adicioná-lo à pasta de journal de um arquivo PST recém-criado.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreateNewMapiJournalAndAddToSubfolder-CreateNewMapiJournalAndAddToSubfolder.cs" >}}

## **Adicionando Anexos ao MapiJournal**

O seguinte trecho de código mostra como adicionar anexos ao [MapiJournal](https://reference.aspose.com/email/net/aspose.email.mapi/mapijournal/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddAttachmentsToMapiJournal-AddAttachmentsToMapiJournal.cs" >}}