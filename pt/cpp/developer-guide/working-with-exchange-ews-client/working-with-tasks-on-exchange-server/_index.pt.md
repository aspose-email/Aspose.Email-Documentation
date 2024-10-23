---
title: "Trabalhando com Tarefas no Exchange Server"
url: /pt/cpp/trabalhando-com-tarefas-no-exchange-server/
weight: 100
type: docs
---

## **Trabalhando com Tarefas**
Aspose.Email suporta o processamento de tarefas no Exchange Server usando a classe *ExchangeTask*. Diferentes propriedades expostas pelo *ExchangeTask*, como *Subject*, *Status*, *DueDate* e *Priority*, podem ser usadas para configurar a tarefa no Exchange. A classe [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) expõe funções como [CreateTask](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a25420465dd38d784ce78428818ea2b78), [UpdateTask](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a4ed6fe13e1278778cc28b867c3ef9dea) e [DeleteTask](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a2bd114b07afa5e97649788a9a9dd9cda) que são usados para processar tarefas no Exchange Server. Este artigo mostra como:

- Criar uma nova tarefa.
- Definir o fuso horário de uma tarefa.
- Atualizar uma tarefa.
- Excluir uma tarefa.
- Enviar solicitação de tarefa.
- Salvar a tarefa no disco.
### **Criar Nova Tarefa**
O seguinte trecho de código mostra como criar uma nova tarefa.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ProcessExchangeTasksUsingIEWSClient-ProcessExchangeTasksUsingIEWSClient.cpp" >}}
### **Especificando o Fuso Horário**
A interface [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) e *ExchangeTask* fornecem a propriedade [TimeZoneId](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a650927ee2f7ae45babc217f148640148) para definir informações de fuso horário ao criar uma tarefa. O seguinte trecho de código mostra como especificar o fuso horário.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SpecifyTimeZoneForExchange-SpecifyTimeZoneForExchange.cpp" >}}
### **Atualizar Tarefa**
O seguinte trecho de código mostra como atualizar uma tarefa no servidor Exchange.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-UpdateTaskOnExchange-UpdateTaskOnExchange.cpp" >}}
### **Excluir Tarefa**
O seguinte trecho de código mostra como excluir uma tarefa no servidor Exchange.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteTaskOnExchange-DeleteTaskOnExchange.cpp" >}}
### **Enviando Solicitação de Tarefa**
O serviço Exchange do Aspose.Email fornece a capacidade de enviar solicitações de tarefa semelhantes ao Outlook. O seguinte trecho de código mostra como carregar uma mensagem de solicitação de tarefa do disco e enviá-la usando o [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SendTaskRequestUsingIEWSClient-SendTaskRequestUsingIEWSClient.cpp" >}}
### **Salvando Tarefa no Disco**
Aspose.Email também permite salvar Tarefas do Exchange no disco no formato MSG do Outlook. O seguinte trecho de código mostra como salvar uma tarefa no disco.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SaveExchangeTaskToDisc-SaveExchangeTaskToDisc.cpp" >}}