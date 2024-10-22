---
title: "Trabalhando com Tarefas no Exchange Server"
url: /pt/net/trabalhando-com-tarefas-no-exchange-server/
weight: 100
type: docs
---


## **Trabalhando com Tarefas**

Aspose.Email suporta o processamento de tarefas no Exchange usando a classe [ExchangeTask](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/exchangetask/). Diferentes propriedades expostas pela [ExchangeTask](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/exchangetask/), como [Subject](https://reference.aspose.com/email/net/aspose.email.calendar/task/subject/), [Status](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/exchangetask/status/), [DueDate](https://reference.aspose.com/email/net/aspose.email.calendar/task/duedate/) e [Priority](https://reference.aspose.com/email/net/aspose.email.calendar/task/priority/), podem ser usadas para configurar a tarefa no Exchange. A classe [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) expõe funções como [CreateTask](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createtask/#createtask/), [UpdateTask](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/updatetask/#updatetask/), e [DeleteTask](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/deleteitem/) que são usadas para processar tarefas no Exchange. Este artigo mostra como:

- Criar uma nova tarefa.
- Definir o fuso horário de uma tarefa.
- Atualizar uma tarefa.
- Excluir uma tarefa.
- Enviar solicitação de tarefa.
- Salvar tarefa no disco.
  
### **Criar Nova Tarefa**

O seguinte trecho de código mostra como criar uma nova tarefa.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ProcessExchangeTasksUsingIEWSClient-ProcessExchangeTasksUsingIEWSClient.cs" >}}

### **Especificando o Fuso Horário**

A interface [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) e [ExchangeTask](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/exchangetask/) fornecem a propriedade [TimeZoneId](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/timezoneid/) para definir informações de fuso horário ao criar uma tarefa. O seguinte trecho de código mostra como especificar o fuso horário.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SpecifyTimeZoneForExchange-SpecifyTimeZoneForExchange.cs" >}}

### **Atualizar Tarefa**

Os seguintes trechos de código mostram como atualizar uma tarefa em um servidor Exchange.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-UpdateTaskOnExchange-UpdateTaskOnExchange.cs" >}}

### **Excluir Tarefa**

O seguinte trecho de código mostra como excluir uma tarefa em um servidor Exchange.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-DeleteTaskOnExchange-DeleteTaskOnExchange.cs" >}}

### **Enviando Solicitação de Tarefa**

O serviço Exchange do Aspose.Email fornece a capacidade de enviar solicitações de tarefa semelhantes ao Outlook. O seguinte trecho de código mostra como carregar uma mensagem de solicitação de tarefa do disco e enviá-la usando o [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SendTaskRequestUsingIEWSClient-SendTaskRequestUsingIEWSClient.cs" >}}

### **Salvando Tarefa no Disco**

Aspose.Email também permite salvar Tarefas do Exchange no disco no formato MSG do Outlook. O seguinte trecho de código mostra como salvar uma tarefa no disco.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SaveExchangeTaskToDisc-SaveExchangeTaskToDisc.cs" >}}

### **Listando Tarefas do Servidor Exchange**

O [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) fornece o método [ListTasks](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listtasks/#listtasks/) que pode ser usado para buscar tarefas de um Serviço Web do Exchange. Possui várias sobrecargas que podem ser usadas para recuperar a lista de tarefas de uma pasta específica ou usando algum critério de pesquisa. O exemplo de código abaixo ilustra como obter todas ou tarefas específicas da pasta de Tarefas.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ListTasksFromExchangeServer-ListTasksFromExchangeServerWithEWS.cs" >}}

### **Filtrando Tarefas do Servidor Exchange**

Aspose.Email fornece a capacidade de recuperar tarefas específicas do servidor em vez de recuperar todas as tarefas do servidor. A API pode ser usada para recuperar tarefas por status da tarefa, como Concluída, Adiada, Em Progresso, Não iniciada ou Aguardando outros. A classe [ExchangeQueryBuilder](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangequerybuilder/) pode ser usada para especificar o critério desejado utilizando a propriedade Status. Ela também permite especificar várias condições para recuperar as tarefas desejadas do Servidor Exchange. Isso é demonstrado pelo seguinte exemplo de código.