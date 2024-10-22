---
title: "Trabalhando com Sinalizador de Acompanhamento e Data de Vencimento para Arquivos MSG do Outlook em C++"
description: "O sinalizador de Acompanhamento para Recipientes e a Data de Vencimento para Arquivos MSG do Outlook podem ser definidos ou removidos usando a API da Biblioteca de Parser de Email em C++."
url: /pt/cpp/trabalhando-com-sinalizador-de-acompanhamento-e-data-de-vencimento-para-arquivos-msg-do-outlook/
weight: 50
type: docs
linktitle: "Trabalhando com Sinalizador de Acompanhamento e Data de Vencimento para Arquivos MSG do Outlook"
---

## **Definindo Sinalizador de Acompanhamento e Data de Vencimento para Arquivos MSG do Outlook**
Um sinalizador de acompanhamento marca uma mensagem de e-mail para algum tipo de ação. O Microsoft Outlook permite que os usuários sinalizem mensagens e, na configuração do sinalizador, atribuam uma data de vencimento para o acompanhamento. O Microsoft Outlook envia um lembrete para o destinatário para incentivá-lo a acompanhar o e-mail. Sinalizar e-mails e definir datas de vencimento programaticamente permite que desenvolvedores de software automatem certos tipos de e-mails e ajudem os recipientes a se lembrarem de tomar uma ação. Por exemplo, poderia ser usado para enviar mensagens mensais para uma equipe de vendas para lembrá-los de completar seus relatórios; ou para enviar uma mensagem a todos os funcionários para lembrá-los de uma reunião da empresa. Aspose.Email para C++ suporta a definição de sinalizador de acompanhamento e data de vencimento para objetos MapiMessage usando FollowUpManager e FollowUpOptions. Existem várias variantes nas quais o sinalizador de acompanhamento pode ser definido em uma mensagem. Todas são usadas no exemplo de código abaixo:

1. Definir um sinalizador de acompanhamento para uma mensagem
1. Adicionar uma data de vencimento e data de lembrete a uma mensagem
1. Adicionar um sinalizador à mensagem de um destinatário.
1. Marcar como completo.
1. Remover sinalizador.
1. Ler opções de acompanhamento.

### **Definindo um sinalizador de FollowUp**
O seguinte trecho de código mostra como definir um sinalizador de FollowUp usando a API da Biblioteca de Parser de Email em C++.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SetFollowUpflag-SetFollowUpflag.cpp" >}}

### **Definindo Acompanhamento para Recipientes**
O seguinte trecho de código mostra como definir acompanhamento para recipientes.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SetFollowUpForRecipients-SetFollowUpForRecipients.cpp" >}}

### **Marcando um sinalizador de FollowUp como Completo**
O seguinte trecho de código mostra como marcar o sinalizador de FollowUp como completo.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-MarkFollowUpFlagAsCompleted-MarkFollowUpFlagAsCompleted.cpp" >}}

### **Removendo um sinalizador de FollowUp**
O seguinte trecho de código mostra como remover o sinalizador de FollowUp.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-RemoveFollowUpflag-RemoveFollowUpflag.cpp" >}}

### **Ler opções de sinalizador de acompanhamento para uma mensagem**
O seguinte trecho de código mostra como ler opções de sinalizador de acompanhamento para uma mensagem.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadFollowupFlagOptionsForMessage-ReadFollowupFlagOptionsForMessage.cpp" >}}