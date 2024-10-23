---
title: "Trabalhando com Compromissos"
url: /pt/python-net/trabalhando-com-compromissos/
weight: 20
type: docs
---


## **Carregar e Salvar Compromisso no Formato ICS**
A classe Appointment na API Aspose.Email pode ser utilizada para carregar um compromisso no formato ICS, bem como para criar um novo compromisso e salvá-lo no disco no formato ICS. Neste artigo, primeiro criamos um compromisso e o salvamos no disco em formato ICS, e depois o carregamos.
### **Criar Compromisso e Salvar no Disco no Formato ICS**
Os seguintes passos são necessários para criar um compromisso e salvá-lo em formato ICS.

1. Crie uma instância da classe Appointment e inicialize-a com este construtor.
1. Passe os seguintes argumentos no construtor acima:
   1. Participantes
   1. Descrição
   1. Data de Término
   1. Localização
   1. Organizador
   1. Data de Início
   1. Resumo
1. Chame o método Save() e especifique o nome do arquivo e o formato nos argumentos.

O compromisso pode ser aberto no Microsoft Outlook ou em qualquer programa que possa carregar um arquivo ICS. Se o arquivo for aberto no Microsoft Outlook, ele adiciona automaticamente o compromisso ao calendário do Outlook.

Os seguintes trechos de código mostram como criar e salvar um compromisso no disco em formato ICS.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-CreateAppointment-CreateAppointment.py" >}}
### **Carregar Compromisso no Formato ICS**
Para carregar um compromisso no formato ICS, os seguintes passos são necessários:

1. Crie uma instância da classe Appointment.
1. Chame o método Load() fornecendo o caminho do arquivo ICS.
1. Leia qualquer propriedade para obter qualquer informação do compromisso (arquivo ICS).

Os seguintes trechos de código mostram como carregar um compromisso no formato ICS.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-LoadAppointment-LoadAppointment.py" >}}
## **Ler Vários Eventos de um Arquivo ICS**
{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-ReadMultipleEventsFromICS-ReadMultipleEventsFromICS.py" >}}
## **Escrever Vários Eventos em um Arquivo ICS**
{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-WriteMultipleEventsToICS-WriteMultipleEventsToICS.py" >}}
## **Criar um Pedido de Compromisso em Rascunho**
Foi mostrado em nossos artigos anteriores como criar e salvar um compromisso no formato ICS. Muitas vezes é necessário criar um pedido de Compromisso em modo Rascunho, para que as informações básicas sejam adicionadas e depois o mesmo Compromisso em rascunho seja encaminhado para outros usuários para alterações necessárias de acordo com os usuários individuais. Para salvar um Compromisso em modo Rascunho, a propriedade **Method** da classe Appointment deve ser definida como **Publish**. O seguinte trecho de código mostra como criar um pedido de compromisso em rascunho.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-DraftAppointmentRequest-DraftAppointmentRequest.py" >}}
### **Criação de Compromisso em Rascunho a Partir de Texto**
O seguinte trecho de código mostra como criar um compromisso em rascunho a partir de um texto. 

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-CreateAppointmentFromString-CreateAppointmentFromString.py" >}}
## **Definir o Status dos Participantes dos Atendentes do Compromisso**
A API Aspose.Email para .NET permite que você defina o status dos atendentes do compromisso enquanto formula uma mensagem de resposta. Isso adiciona a propriedade PARTSTAT ao arquivo ICS.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-SetParticipantStatusOfAppointmentAttendees-SetParticipantStatusOfAppointmentAttendees.py" >}}