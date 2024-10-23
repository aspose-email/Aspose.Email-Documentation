---
title: "Trabalhando com Contatos do Outlook usando a Biblioteca C++ Email Parser"
description: "A Biblioteca C++ Email Parser permite criar, salvar e ler contatos do Outlook e importar contatos dos formatos de arquivo MSG e VCard."
url: /pt/cpp/trabalhando-com-contatos-do-outlook/
weight: 90
type: docs
linktitle: "Trabalhando com Contatos do Outlook"
---

## **Criando, Salvando e Lendo Contatos**
Assim como o MapiMessage, a Aspose.Email permite criar contatos do Outlook. A classe MapiContact fornece todas as propriedades relacionadas a contatos necessárias para criar um contato do Outlook. Este artigo mostra como criar, salvar e ler um contato do Outlook usando a classe MapiContact.

### **Criar e Salvar Contato do Outlook**
Para criar um contato e salvá-lo no disco:

1. Instanciar um novo objeto da classe MapiContact.
1. Inserir informações das propriedades do contato.
1. Adicionar dados da foto (se houver).
1. Salvar o contato no formato MSG ou VCard.

O seguinte trecho de código mostra como criar e salvar um contato do Outlook com a Biblioteca ou API C++ Email Parser.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateAndSaveOutlookContact-CreateAndSaveOutlookContact.cpp" >}}

### **Lendo um MapiContact**
A classe MapiContact pode ser usada para carregar contatos do Outlook nos formatos MSG e VCard. O seguinte trecho de código mostra como carregar contatos do Outlook salvos como MSG e VCF em um MapiContact.

#### **Carregando um Contato de MSG**
O seguinte trecho de código mostra como carregar um contato de MSG.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-LoadingContactFromMSG-LoadingContactFromMSG.cpp" >}}

#### **Carregando um Contato de VCard**
O seguinte trecho de código mostra como carregar um contato de vCard.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-LoadingContactFromVCard-LoadingContactFromVCard.cpp" >}}