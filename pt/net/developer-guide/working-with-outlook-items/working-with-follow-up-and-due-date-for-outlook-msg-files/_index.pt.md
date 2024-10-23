---
title: "Trabalhando com Acompanhamento e Data de Vencimento para Arquivos MSG do Outlook"
url: /pt/net/trabalhando-com-acompanhamento-e-data-de-vencimento-para-arquivos-msg-do-outlook/
weight: 60
type: docs
---


## **Configurando Acompanhamento e Data de Vencimento para Arquivos MSG do Outlook**

Uma bandeira de acompanhamento marca uma mensagem de email para algum tipo de ação. O Microsoft Outlook permite que os usuários marquem mensagens e, na configuração da bandeira, atribuam uma data de vencimento para o acompanhamento. O Microsoft Outlook envia um lembrete ao destinatário para solicitar que ele faça o acompanhamento do email. Marcar emails e definir datas de vencimento programaticamente permite que desenvolvedores de software automatizem certos tipos de emails e ajudem os destinatários a se lembrarem de tomar ações. Por exemplo, pode ser usado para enviar mensagens mensais a uma equipe de vendas para lembrá-los de completar seus relatórios; ou para enviar uma mensagem a todos os funcionários para lembrá-los de uma reunião da empresa. A Aspose.Email para .NET suporta a configuração de bandeira de acompanhamento e data de vencimento para os objetos [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) usando [FollowUpManager](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/) e [FollowUpOptions](https://reference.aspose.com/email/net/aspose.email.mapi/followupoptions/). Existem várias variantes nas quais a bandeira de acompanhamento pode ser configurada em uma mensagem. Todas são usadas no exemplo de código abaixo:

1. Definir uma bandeira de acompanhamento para uma mensagem
1. Adicionar uma data de vencimento e data de lembrete a uma mensagem
1. Adicionar uma bandeira à mensagem de um destinatário.
1. Marcar como concluído.
1. Remover bandeira.
1. Ler opções de acompanhamento.

### **Configurando uma bandeira de Acompanhamento**

O seguinte trecho de código mostra como configurar uma bandeira de acompanhamento.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetFollowUpflag-SetFollowUpflag.cs" >}}

### **Configurando Acompanhamento para Destinatários**

O seguinte trecho de código mostra como configurar acompanhamento para destinatários.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetFollowUpForRecipients-SetFollowUpForRecipients.cs" >}}

### **Marcando uma bandeira de Acompanhamento como Concluída**

O seguinte trecho de código mostra como marcar a bandeira de acompanhamento como concluída.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-MarkFollowUpFlagAsCompleted-MarkFollowUpFlagAsCompleted.cs" >}}

### **Removendo uma bandeira de Acompanhamento**

O seguinte trecho de código mostra como remover a bandeira de acompanhamento.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-RemoveFollowUpflag-RemoveFollowUpflag.cs" >}}

### **Ler opções de bandeira de acompanhamento para uma mensagem**

O seguinte trecho de código mostra como ler as opções de bandeira de acompanhamento para uma mensagem.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadFollowupFlagOptionsForMessage-ReadFollowupFlagOptionsForMessage.cs" >}}