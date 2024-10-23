---
title: "Trabalhando com Tarefas no Exchange Server"
url: /pt/java/trabalhando-com-tarefas-no-exchange-server/
weight: 100
type: docs
---


## **Trabalhando com Tarefas**
Aspose.Email suporta o processamento de tarefas no Exchange usando a classe [ExchangeTask](https://apireference.aspose.com/email/java/com.aspose.email/exchangetask). Diferentes propriedades expostas por [ExchangeTask](https://apireference.aspose.com/email/java/com.aspose.email/exchangetask), como [Subject](https://apireference.aspose.com/email/java/com.aspose.email/Task#getSubject\(\)), [Status](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeTask#getStatus\(\)), [DueDate](https://apireference.aspose.com/email/java/com.aspose.email/Task#getDueDate\(\)), e [Priority](https://apireference.aspose.com/email/java/com.aspose.email/Task#getPriority\(\)), podem ser usados para configurar a tarefa no Exchange. A classe [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) expõe funções como [createTask](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#createTask\(com.aspose.email.ExchangeTask\)), [updateTask](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#updateTask\(com.aspose.email.ExchangeTask\)), e [deleteTask](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#deleteTask\(java.lang.String\)) que são usadas para processar tarefas no Exchange. Este artigo mostra como:

- Criar uma nova tarefa.
- Definir o fuso horário de uma tarefa.
- Atualizar uma tarefa.
- Deletar uma tarefa.
- Enviar solicitação de tarefa.
- Salvar tarefa no disco.
### **Criar Nova Tarefa**
O seguinte trecho de código mostra como criar uma nova tarefa.



~~~Java
// Criar uma instância da classe EWSClient fornecendo credenciais
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Criar objeto de tarefa do Exchange
ExchangeTask task = new ExchangeTask();

// Definir assunto e status da tarefa como Em progresso
task.setSubject("Novo-Teste");
task.setStatus(ExchangeTaskStatus.InProgress);
client.createTask(client.getMailboxInfo().getTasksUri(), task);
~~~
### **Especificando Fuso Horário**
A interface [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) e [ExchangeTask](https://apireference.aspose.com/email/java/com.aspose.email/exchangetask) fornecem a propriedade TimeZoneId para definir as informações do fuso horário ao criar uma tarefa. O seguinte trecho de código mostra como especificar o fuso horário.



~~~Java
client.setTimezoneId("Hora Padrão da Europa Central");
~~~    
### **Atualizar Tarefa**
Os seguintes trechos de código mostram como atualizar uma tarefa em um servidor Exchange.



~~~Java
// Criar uma instância da classe ExchangeClient fornecendo credenciais
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Obter toda a coleção de informações de tarefas do exchange
ExchangeMessageInfoCollection tasks = client.listMessages(client.getMailboxInfo().getTasksUri());

// Analisar todas as informações das tarefas na lista
for (ExchangeMessageInfo info : (Iterable<ExchangeMessageInfo>) tasks) {
    // Buscar tarefa do exchange usando as informações da tarefa atual
    ExchangeTask task = client.fetchTask(info.getUniqueUri());

    // Atualizar o status da tarefa para Não Iniciada
    task.setStatus(ExchangeTaskStatus.NotStarted);

    // Definir a data de vencimento da tarefa
    SimpleDateFormat sdf = new SimpleDateFormat("dd/MM/yyyy HH:mm:ss");
    task.setDueDate(sdf.parse("26/02/2013 00:00:00"));

    // Definir prioridade da tarefa
    task.setPriority(MailPriority.Low.getValue());

    // Atualizar tarefa no exchange
    client.updateTask(task);
}
~~~    
### **Deletar Tarefa**
O seguinte trecho de código mostra como deletar uma tarefa em um servidor Exchange.



~~~Java
// Criar uma instância da classe ExchangeClient fornecendo credenciais
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Obter toda a coleção de informações de tarefas do exchange
ExchangeMessageInfoCollection tasks = client.listMessages(client.getMailboxInfo().getTasksUri());

// Analisar todas as informações das tarefas na lista
for (ExchangeMessageInfo info : (Iterable<ExchangeMessageInfo>) tasks) {
    // Buscar tarefa do exchange usando as informações da tarefa atual
    ExchangeTask task = client.fetchTask(info.getUniqueUri());

    // Verificar se a tarefa atual atende aos critérios de pesquisa
    if (task.getSubject().equals("teste")) {
        // Deletar tarefa do exchange
        client.deleteItem(task.getUniqueUri(), DeletionOptions.getDeletePermanently());
    }
}
~~~    
### **Enviar Solicitação de Tarefa**
O serviço Exchange da Aspose.Email fornece a capacidade de enviar solicitações de tarefas semelhantes ao Outlook. O seguinte trecho de código mostra como carregar uma mensagem de solicitação de tarefa do disco e enviá-la usando o [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient).



~~~Java
// Criar uma instância da classe ExchangeClient fornecendo credenciais
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

MsgLoadOptions options = new MsgLoadOptions();
options.setPreserveTnefAttachments(true);

// carregar tarefa do arquivo .msg
MailMessage eml = MailMessage.load(dataDir + "task.msg", options);
eml.setFrom(MailAddress.to_MailAddress("firstname.lastname@domain.com"));
eml.getTo().clear();
eml.getTo().addMailAddress(new MailAddress("firstname.lastname@domain.com"));
client.send(eml);
~~~    
### **Salvar Tarefa no Disco**
Aspose.Email também permite salvar Tarefas do Exchange no disco no formato MSG do Outlook. O seguinte trecho de código mostra como salvar uma tarefa no disco.



~~~Java
ExchangeTask task = new ExchangeTask();
task.setSubject("TASK-ID - " + UUID.randomUUID());
task.setStatus(ExchangeTaskStatus.InProgress);

Calendar cal = Calendar.getInstance();
task.setStartDate(cal.getTime());
cal.add(Calendar.DATE, 3);
task.setDueDate(cal.getTime());
task.save(dstEmail);
~~~    
### **Listando Tarefas do Servidor Exchange**
[IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) fornece o método [listTasks](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listTasks\(\)) que pode ser usado para buscar tarefas de um Serviço Web Exchange. Ele possui várias sobrecargas que podem ser usadas para recuperar a lista de tarefas de uma pasta específica ou usando algum critério de pesquisa. O código abaixo ilustra como obter todas ou tarefas específicas da pasta de Tarefas.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);

// Listando Tarefas do Servidor
client.setTimezoneId("Hora Padrão da Europa Central");
TaskCollection taskCollection = client.listTasks(client.getMailboxInfo().getTasksUri());

// imprimir detalhes das tarefas recuperadas
int iTasksCount = taskCollection.size();
for (int i = 0; i < iTasksCount; i++) {
    ExchangeTask task = (ExchangeTask) taskCollection.get_Item(i);
    System.out.println(task.getSubject());
    System.out.println(task.getStartDate());
    System.out.println(task.getDueDate());
}

// Listando Tarefas do servidor com base na Consulta - Concluída e Em Progresso
Integer[] selectedStatuses = new Integer[] { ExchangeTaskStatus.Completed, ExchangeTaskStatus.InProgress };
ExchangeQueryBuilder queryBuilder = new ExchangeQueryBuilder();
queryBuilder.getTaskStatus().in(Arrays.asList(selectedStatuses));
MailQuery query = queryBuilder.getQuery();

taskCollection = client.listTasks(client.getMailboxInfo().getTasksUri(), query);

// imprimir detalhes das tarefas recuperadas
iTasksCount = taskCollection.size();
for (int i = 0; i < iTasksCount; i++) {
    ExchangeTask task = (ExchangeTask) taskCollection.get_Item(i);
    System.out.println(task.getSubject());
    System.out.println(task.getStartDate());
    System.out.println(task.getDueDate());
}
~~~    
### **Filtrando Tarefas do Servidor Exchange**
Aspose.Email fornece a capacidade de recuperar tarefas específicas do servidor em vez de recuperar todas as tarefas. A API pode ser usada para recuperar tarefas pelo status da tarefa, como Concluídas, Adiadas, Em Progresso, Não Iniciadas ou Aguardando Outros. A classe [ExchangeQueryBuilder](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeQueryBuilder) pode ser usada para especificar o critério desejado utilizando a propriedade Status. Ela também permite especificar múltiplas condições para a recuperação das tarefas desejadas do Servidor Exchange. Isso é demonstrado pelo seguinte exemplo de código.



~~~Java
// Criar uma instância da classe ExchangeClient fornecendo credenciais
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Definir fuso horário para tarefas
client.setTimezoneId("Hora Padrão da Europa Central");

// Usamos esses valores de status para especificar nas consultas
Integer[] values = new Integer[] { ExchangeTaskStatus.Completed, ExchangeTaskStatus.Deferred, ExchangeTaskStatus.InProgress, ExchangeTaskStatus.NotStarted,
        ExchangeTaskStatus.WaitingOnOthers };

messageInfoCol = client.listMessages(client.getMailboxInfo().getTasksUri());

// Agora recuperar as tarefas com status específicos
for (int status : values) {
    queryBuilder = new ExchangeQueryBuilder();
    queryBuilder.getTaskStatus().equals(status);
    query = queryBuilder.getQuery();
    messageInfoCol = client.listMessages(client.getMailboxInfo().getTasksUri(), query);
    fetchedTask = client.fetchTask(messageInfoCol.get_Item(0).getUniqueUri());
}

// recuperar todas as outras que não estão especificadas
for (int status : values) {
    queryBuilder = new ExchangeQueryBuilder();
    queryBuilder.getTaskStatus().notEquals((int) status);
    query = queryBuilder.getQuery();
    messageInfoCol = client.listMessages(client.getMailboxInfo().getTasksUri(), query);
}

// especificando múltiplos critérios
Integer[] selectedStatuses = new Integer[] { ExchangeTaskStatus.Completed, ExchangeTaskStatus.InProgress };

queryBuilder = new ExchangeQueryBuilder();
queryBuilder.getTaskStatus().in(Arrays.asList(selectedStatuses));
query = queryBuilder.getQuery();
messageInfoCol = client.listMessages(client.getMailboxInfo().getTasksUri(), query);

// listar todas aquelas que não estão nos nossos status especificados
queryBuilder = new ExchangeQueryBuilder();
queryBuilder.getTaskStatus().notIn(Arrays.asList(selectedStatuses));
query = queryBuilder.getQuery();
messageInfoCol = client.listMessages(client.getMailboxInfo().getTasksUri(), query);
~~~