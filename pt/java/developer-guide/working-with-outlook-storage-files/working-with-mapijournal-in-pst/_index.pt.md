---
title: "Trabalhando com MapiJournal em PST"
url: /pt/java/trabalhando-com-mapijournal-em-pst/
weight: 70
type: docs
---

## **Adicionando MapiJournal ao PST**

[Criar Novo PST, Adicionar Subpastas e Mensagens](/email/java/criar-novo-pst-adicionar-subpastas-e-mensagens/) mostrou como criar um arquivo PST e adicionar uma subpasta a ele. Com o Aspose.Email, você pode adicionar MapiJournal à subpasta Journal de um arquivo PST que você criou ou carregou. Abaixo estão os passos para adicionar MapiJournal a um PST:

1. Crie um objeto [MapiJournal](https://reference.aspose.com/email/java/com.aspose.email/mapijournal/).
1. Defina as propriedades do [MapiJournal](https://reference.aspose.com/email/java/com.aspose.email/mapijournal/) usando um construtor e métodos.
1. Crie um PST usando o método [PersonalStorage.create()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#create-java.io.OutputStream-int-).
1. Crie uma pasta pré-definida (Journals) na raiz do arquivo PST acessando a pasta raiz e, em seguida, chamando o método [addMapiMessageItem()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMapiMessageItem-com.aspose.email.IMapiMessageItem-).

O snippet de código abaixo mostra como criar um [MapiJournal](https://reference.aspose.com/email/java/com.aspose.email/mapijournal/) e, em seguida, adicioná-lo à pasta Journal de um arquivo PST recém-criado.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiJournalToPST-AddMapiJournalToPST.java" >}}

## **Adicionando Anexos ao MapiJournal**

Também é possível adicionar anexos a itens de diário MAPI. O código abaixo mostra como.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiJournalToPST-AddAttachmentsToMapiJournal.java" >}}