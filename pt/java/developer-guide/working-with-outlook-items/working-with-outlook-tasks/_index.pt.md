---
title: "Trabalhando com Tarefas do Outlook"
url: /pt/java/trabalhando-com-tarefas-do-outlook/
weight: 90
type: docs
---

## **Criando, Salvando e Lendo Tarefas do Outlook**

Aspose.Email para Java permite que desenvolvedores criem tarefas do Outlook e as salvem no formato MSG. A classe [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) fornece uma série de propriedades, como [PercentComplete](https://reference.aspose.com/email/java/com.aspose.email/mapitask/#getPercentComplete--), [EstimatedEffort](https://reference.aspose.com/email/java/com.aspose.email/mapitask/#getEstimatedEffort--), [ActualEffort](https://reference.aspose.com/email/java/com.aspose.email/mapitask/#getActualEffort--), [History](https://reference.aspose.com/email/java/com.aspose.email/mapitask/#getHistory--), [LastUpdate](https://reference.aspose.com/email/java/com.aspose.email/mapitask/#getLastUpdate--), etc., para acomodar e definir as informações necessárias para uma tarefa do Outlook. Este artigo mostra como criar, salvar e ler uma [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) do disco.

### **Criar e Salvar uma MapiTask**

Os seguintes passos podem ser usados para criar e salvar uma tarefa no disco.

1. Instanciar um novo objeto da classe [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).
1. Inserir informações para as várias propriedades da tarefa.
1. Salvar a tarefa no disco no formato MSG.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-OutlookTasks-CreateAndSaveMapiTask.java" >}}

#### **Ler uma MapiTask**

O objeto da classe [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) é usado para converter o objeto [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) que carrega uma tarefa do disco no formato MSG.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-OutlookTasks-ReadingAMapiTask.java" >}}

#### **Ler uma Tarefa VToDo**

As Tarefas do Google exportadas no formato iCalendar como eventos VToDo podem ser carregadas usando a classe [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) conforme mostrado no seguinte exemplo de código.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-OutlookTasks-ReadingAVToDoTask.java" >}}

### **Adicionar Informações de Lembrete a uma MapiTask**

Semelhante ao Microsoft Outlook, Aspose.Email pode adicionar informações de lembrete a uma [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/). O seguinte trecho de código mostra como adicionar informações de lembrete a uma [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-OutlookTasks-AddReminderInformationToAMapiTask.java" >}}

### **Adicionar Anexo a uma MapiTask**

O seguinte trecho de código mostra como adicionar anexos a uma [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-OutlookTasks-AddingAttachmentToAMapiTask.java" >}}

### **Convertendo Tarefa do Outlook para MHT**

Aspose.Email pode gerar uma saída semelhante a [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) durante a conversão de uma [MapiTask](https://reference.aspose.com/email/java/com.aspose.email/mapitask/) para MHT.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-ConvertMapiTaskToMHT-convertMapiTaskToMHT.java" >}}