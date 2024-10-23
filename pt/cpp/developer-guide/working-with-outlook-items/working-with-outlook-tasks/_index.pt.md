---
title: "Trabalhando com Tarefas do Outlook"
url: /pt/cpp/trabalhando-com-tarefas-do-outlook/
weight: 110
type: docs
---

## **Criando, Salvando e Lendo Tarefas**
Aspose.Email para C++ permite que você crie tarefas do Outlook e as salve no formato MSG. A classe MapiTask fornece uma série de propriedades, como Percentcomplete, Estimatedeffort, ActualEffort, History, LastUpdate, entre outras, para acomodar e definir informações necessárias para uma tarefa do Outlook. Este artigo mostra como criar, salvar e ler uma MapiTask do disco. Para criar e salvar uma tarefa no disco:

1. Instanciar um novo objeto da classe MapiTask.
1. Inserir informações sobre as propriedades da tarefa.
1. Salvar a tarefa no disco no formato MSG.

O seguinte trecho de código mostra como criar, salvar e ler Tarefas.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreatingAndSavingOutlookTasks-CreatingAndSavingOutlookTasks.cpp" >}}
### **Lendo uma MapiTask**
O objeto da classe MapiTask é usado para converter o objeto MapiMessage que carrega uma tarefa do disco no formato MSG. O seguinte trecho de código mostra como ler uma MapiTask.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-LoadingContactFromMSG-LoadingContactFromMSG.cpp" >}}
### **Lendo uma Tarefa VToDo**
As Tarefas do Google exportadas no formato iCalendar como eventos VToDo podem ser carregadas usando a classe MapiTask, como mostrado no seguinte exemplo de código. O seguinte trecho de código mostra como ler uma Tarefa VToDo.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadingVToDoTask-ReadingVToDoTask.cpp" >}}
### **Adicionando Informações de Lembrete a uma MapiTask**
Semelhante ao Microsoft Outlook, Aspose.Email pode adicionar informações de lembrete a uma MapiTask. O seguinte trecho de código mostra como adicionar informações de lembrete a uma MapiTask.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddReminderInformationToMapiTask-AddReminderInformationToMapiTask.cpp" >}}
### **Adicionando Anexos a uma MapiTask**
O seguinte trecho de código mostra como adicionar anexos a uma MapiTask.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddAttachmentsToMapiTask-AddAttachmentsToMapiTask.cpp" >}}
### **Adicionando Recorrência a MapiTask**
Aspose.Email permite criar uma tarefa recorrente onde a recorrência pode ser diária, semanal, mensal ou anual. O seguinte trecho de código mostra como criar uma tarefa com diferentes tipos de recorrência.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddRecurrenceToMapiTask-AddRecurrenceToMapiTask.cpp" >}}