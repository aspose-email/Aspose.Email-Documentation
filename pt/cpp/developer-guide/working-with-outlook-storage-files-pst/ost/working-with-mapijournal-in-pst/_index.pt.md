---
title: "Trabalhando com MapiJournal em PST"
url: /pt/cpp/trabalhando-com-mapijournal-em-pst/
weight: 70
type: docs
---
  
## **Adicionando MapiJournal ao PST**  
Com Aspose.Email, você pode adicionar MapiJournal à subpasta Journal de um arquivo PST que você criou ou carregou. Abaixo estão os passos para adicionar MapiJournal a um PST:  
  
1. Crie um objeto MapiJournal  
1. Defina as propriedades do MapiJournal usando um construtor e métodos.  
1. Crie um PST usando o método PersonalStorage.Create().  
1. Crie uma pasta pré-definida (Journals) na raiz do arquivo PST acessando a pasta raiz e, em seguida, chamando o método AddMapiMessageItem().  
  
O seguinte trecho de código mostra como criar um MapiJournal e, em seguida, adicioná-lo à pasta de diário de um arquivo PST recém-criado.  
  
  
{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateNewMapiJournalAndAddToSubfolder-CreateNewMapiJournalAndAddToSubfolder.cpp" >}}  
## **Adicionando Anexos ao MapiJournal**  
O seguinte trecho de código mostra como adicionar anexos ao MapiJournal.  
  
  
{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddAttachmentsToMapiJournal-AddAttachmentsToMapiJournal.cpp" >}}  