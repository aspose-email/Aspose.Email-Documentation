---
title: "Trabalhando com Tarefas do Outlook"
url: /pt/net/trabalhando-com-tarefas-do-outlook/
weight: 100
type: docs
---


## **Criando, Salvando e Lendo Tarefas**

Aspose.Email para .NET permite que você crie tarefas do Outlook e as salve no formato MSG. A classe [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) fornece uma série de propriedades como [PercentComplete](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/percentcomplete/), [EstimatedEffort](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/estimatedeffort/), [ActualEffort](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/actualeffort/), [History](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/history/), [LastUpdate](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/lastupdate/) e outras, para acomodar e definir as informações necessárias para uma tarefa do Outlook. Este artigo mostra como criar, salvar e ler um [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) do disco. Para criar e salvar uma tarefa no disco:

1. Instancie um novo objeto da classe [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/).
1. Insira as informações das propriedades da tarefa.
1. Salve a tarefa no disco no formato MSG.

O seguinte trecho de código mostra como criar, salvar e ler tarefas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreatingAndSavingOutlookTasks-CreatingAndSavingOutlookTasks.cs" >}}

### **Lendo um MapiTask**

O objeto da classe [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) é usado para fazer o cast do objeto [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) que carrega uma tarefa do disco no formato MSG. O seguinte trecho de código mostra como ler um [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-LoadingContactFromMSG-LoadingContactFromMSG.cs" >}}

### **Lendo uma Tarefa VToDo**

As Tarefas do Google exportadas no formato iCalendar como eventos VToDo podem ser carregadas usando a classe [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) como mostrado no seguinte exemplo de código. O seguinte trecho de código mostra como ler uma Tarefa VToDo.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadingVToDoTask-ReadingVToDoTask.cs" >}}

### **Adicionando Informações de Lembrete a um MapiTask**

Semelhante ao Microsoft Outlook, Aspose.Email pode adicionar informações de lembrete a um [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/). O seguinte trecho de código mostra como adicionar informações de lembrete a um [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddReminderInformationToMapiTask-AddReminderInformationToMapiTask.cs" >}}

### **Adicionando Anexos a um MapiTask**

O seguinte trecho de código mostra como adicionar anexos a um [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddAttachmentsToMapiTask-AddAttachmentsToMapiTask.cs" >}}

### **Adicionando Recorrência a um MapiTask**

Aspose.Email permite criar uma tarefa recorrente onde a recorrência pode ser diária, semanal, mensal ou anual. O seguinte trecho de código mostra como criar uma tarefa com diferentes tipos de recorrência.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddRecurrenceToMapiTask-AddRecurrenceToMapiTask.cs" >}}

### **Convertendo Tarefa para MHT**

Aspose.Email pode gerar uma saída semelhante a [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) durante a conversão de um [MapiTask](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/) para MHT.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ConvertMapiTaskToMHT-ConvertMapiTaskToMHT.cs" >}}