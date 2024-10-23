---
title: "Trabalhando com Tarefas do Outlook"
url: /pt/python-net/trabalhando-com-tarefas-do-outlook/
weight: 110
type: docs
---


## **Criando, Salvando e Lendo Tarefas**
Aspose.Email para .NET permite que você crie tarefas do Outlook e as salve no formato MSG. A classe MapiTask fornece uma série de propriedades, como Percentcomplete, Estimatedeffort, ActualEffort, History, LastUpdate e outras, para acomodar e definir informações necessárias para uma tarefa do Outlook. Este artigo mostra como criar, salvar e ler uma MapiTask do disco. Para criar e salvar uma tarefa no disco:

1. Instanciar um novo objeto da classe MapiContact.
1. Inserir informações das propriedades da tarefa.
1. Salvar a tarefa no disco no formato MSG.

O seguinte trecho de código mostra como criar, salvar e ler Tarefas.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-CreatingAndSavingOutlookTask-CreatingAndSavingOutlookTask.py" >}}
### **Lendo uma MapiTask**
O objeto da classe MapiContact é usado para converter o objeto MapiMessage que carrega uma tarefa do disco no formato MSG. O seguinte trecho de código mostra como ler uma MapiTask.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-LoadingContactFromMSG-LoadingContactFromMSG.py" >}}
### **Lendo uma Tarefa VToDo**
Tarefas do Google exportadas no formato iCalendar como eventos VToDo podem ser carregadas usando a classe MapiTask, como mostrado no seguinte exemplo de código. O seguinte trecho de código mostra como ler uma Tarefa VToDo.

```py
import aspose.email as ae

data_dir = "path/to/data/directory"

task = ae.mapi.MapiTask.from_v_todo(data_dir + "VToDoTask.ics")
task.save(data_dir + "VToDo_out.msg", ae.TaskSaveFormat.Msg)
```
### **Adicionando Informações de Lembrete a uma MapiTask**
Semelhante ao Microsoft Outlook, Aspose.Email pode adicionar informações de lembrete a uma MapiTask. O seguinte trecho de código mostra como adicionar informações de lembrete a uma MapiTask.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddReminderInformationToMapiTask-AddReminderInformationToMapiTask.py" >}}

### **Adicionando Anexos a uma MapiTask**

Use o método [Add](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/add/#add) da classe [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/#mapiattachmentcollection-class) para adicionar um anexo a uma MapiTask. O seguinte exemplo de código ajudará você com isso:

```python
import aspose.email as ae
import datetime as dt

task = ae.mapi.MapiTask("Tarefa com anexo", "Corpo de teste da tarefa com anexo", dt.datetime.now(), dt.datetime.now());
task.attachments.add("Attachment.txt", str.encode("dados do anexo"))
task.save("AddAttachmentsToMapiTask_out", ae.mapi.TaskSaveFormat.MSG)
```

### **Adicionando Recorrência a MapiTask**
Aspose.Email permite criar uma tarefa recorrente onde a recorrência pode ser diária, semanal, mensal ou anual. O seguinte trecho de código mostra como criar uma tarefa com diferentes tipos de recorrência.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddRecurrenceToMapiTask-AddRecurrenceToMapiTask.py" >}}

### **Convertendo uma Tarefa para MHT**

O seguinte exemplo de código demonstra como converter uma tarefa para o formato MHT especificando opções adicionais para o formato MHT quando campos específicos da tarefa devem ser renderizados (RENDER_TASK_FIELDS) e que as informações do cabeçalho devem ser incluídas (WRITE_HEADER). A propriedade *mht_format_options* da classe [MhtSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/mhtsaveoptions/#mhtsaveoptions-class) é usada para definir opções adicionais ao salvar no formato MHTML.

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("MapiTask.msg")

opt = ae.SaveOptions.default_mhtml
opt.mht_format_options = ae.MhtFormatOptions.RENDER_TASK_FIELDS | ae.MhtFormatOptions.WRITE_HEADER

msg.save("MapiTask_out.mht", opt)
```