---
title: "Trabalhando com Contatos no Exchange Server"
url: /pt/cpp/trabalhando-com-contatos-no-exchange-server/
weight: 60
type: docs
---

{{% alert color="primary" %}} As contas do Exchange Server mantêm mais do que apenas mensagens de e-mail. Além de buscar, mover, enviar e excluir mensagens de e-mail dos servidores Exchange, Aspose.Email permite que você trabalhe com contatos. Este artigo explica como recuperar informações de contato usando os Serviços Web do Exchange. Este artigo também mostra como você pode listar contatos da pasta de Contatos ou resolver contatos com base no nome do contato. {{% /alert %}} 
## **Obtendo Contatos com EWS**
Aspose.Email fornece a [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client) classe para se conectar ao Microsoft Exchange Server usando os Serviços Web do Exchange. Os trechos de código a seguir usam os Serviços Web do Exchange para ler todos os contatos. O seguinte trecho de código mostra como obter Contatos com EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GettingContactsUsingEWS-GettingContactsUsingEWS.cpp" >}}
## **Resolver Contatos usando o Nome do Contato**
O seguinte trecho de código mostra como obter contatos usando o nome do contato.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ResolveContactsUsingContactName-ResolveContactsUsingContactName.cpp" >}}
## **Determinando o Formato das Notas do Contato**
O [Contact->get_NotesFormat](https://apireference.aspose.com/email/cpp/class/aspose.email.personal_info.contact) especifica o tipo de formato de texto das notas dos contatos definido pelo enumerador [TextFormat](https://apireference.aspose.com/email/cpp/namespace/aspose.email.personal_info).
## **Buscar Contato usando Id**
Um contato específico pode ser recuperado do servidor usando seu ID de contato, conforme mostrado no seguinte exemplo de código.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FetchContactUsingId-FetchContactUsingId.cpp" >}}
## **Adicionando Contatos**
O método [CreateContact()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) da classe [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) pode ser usado para adicionar informações de Contato a um servidor Exchange. O método [CreateContact()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) recebe um objeto [Contact](https://apireference.aspose.com/email/cpp/class/aspose.email.personal_info.contact) como parâmetro de entrada.

Para adicionar contatos a um servidor Exchange:

1. Inicialize o [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) com endereço e credenciais.
1. Inicialize o [Contact](https://apireference.aspose.com/email/cpp/class/aspose.email.personal_info.contact) objeto com as propriedades desejadas.
1. Chame o [CreateContact()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) método e passe o contato para adicionar ao servidor Exchange.

O seguinte trecho de código demonstra a adição de contatos ao servidor Exchange.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-AddContactsToExchangeServerUsingEWS-1.cpp" >}}
## **Atualizando Contatos**
As informações de contato podem ser atualizadas usando o Microsoft Outlook. Aspose.Email também pode atualizar informações de contato no servidor Exchange usando os Serviços Web do Exchange (EWS). O método [IEWSClient->UpdateContact](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) pode atualizar informações de contato no servidor Exchange.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-UpdateContactInformationUsingEWS-UpdateContactInformationUsingEWS.cpp" >}}
## **Excluindo Contatos**
A classe [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) fornece o [DeleteContact](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) para acessar e excluir contatos da pasta de contatos de um servidor Exchange. Este método recebe o ID do contato ou o [Contact](https://apireference.aspose.com/email/cpp/class/aspose.email.personal_info.contact) como parâmetro de entrada.

Para excluir contatos de um servidor Exchange:

1. Inicialize o [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) com endereço e credenciais.
1. Exclua um contato usando seu ID.
1. Exclua um contato chamando o [DeleteContact](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) método com [Contact](https://apireference.aspose.com/email/cpp/class/aspose.email.personal_info.contact) como parâmetro de entrada.

O seguinte trecho de código mostra como excluir contatos de um servidor Exchange usando [IEWSClient->DeleteContact](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteContactsFromExchangeServerUsingEWS-DeleteContactsFromExchangeServerUsingEWS.cpp" >}}