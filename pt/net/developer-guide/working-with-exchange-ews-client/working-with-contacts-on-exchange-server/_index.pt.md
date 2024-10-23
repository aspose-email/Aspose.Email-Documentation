---
title: "Trabalhando com Contatos no Exchange Server"
url: /pt/net/trabalhando-com-contatos-no-exchange-server/
weight: 60
type: docs
---


{{% alert color="primary" %}} As contas do Exchange Server contêm mais do que apenas mensagens de e-mail. Além de [recuperar](https://docs.aspose.com/email/pt/net/working-with-exchange-mailbox-and-messages/#fetch-messages-from-an-exchange-server-mailbox), [mover](https://docs.aspose.com/email/pt/net/working-with-exchange-mailbox-and-messages/#moving-messages), [enviar](https://docs.aspose.com/email/pt/net/working-with-exchange-mailbox-and-messages/#sending-email-messages) e [deletar mensagens de e-mail](https://docs.aspose.com/email/pt/net/working-with-exchange-mailbox-and-messages/#deleting-messages) de servidores do Exchange, o Aspose.Email permite que você trabalhe com contatos. Este artigo explica como recuperar informações de contato usando os Serviços Web do Exchange. Este artigo também mostra como você pode listar contatos da pasta de Contatos ou resolver contatos com base no nome do contato. {{% /alert %}} 

## **Obtendo Contatos com EWS**

O Aspose.Email fornece a classe [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) para se conectar ao Microsoft Exchange Server usando os Serviços Web do Exchange. Os exemplos de código a seguir usam os Serviços Web do Exchange para ler todos os contatos. O seguinte exemplo de código mostra como obter contatos com EWS.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-GettingContactsUsingEWS-GettingContactsUsingEWS.cs" >}}

## **Resolver Contatos usando o Nome do Contato**

O seguinte exemplo de código mostra como obter contatos com EWS.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-ResolveContactsUsingContactName-ResolveContactsUsingContactName.cs" >}}

## **Determinar o Formato das Notas de Contato**

O Aspose.Email.Mail.Contact.NotesFormat especifica o tipo de formato de texto das notas de contato definido pelo enumerador Aspose.Email.TextFormat.

## **Buscar Contato usando o Id**

Um contato específico pode ser recuperado do servidor usando seu id de contato, conforme mostrado no seguinte exemplo de código.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-FetchContactUsingId-FetchContactUsingId.cs" >}}

## **Adicionando Contatos**

A classe [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/#ewsclient-class) pode usar o método [CreateContact()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createcontact/) para adicionar informações de contato a um Exchange Server. O método [CreateContact()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createcontact/) recebe um objeto Contact como parâmetro de entrada.

Para adicionar contatos a um Exchange Server:

1. Inicialize o EWSClient com o endereço e credenciais.
1. Inicialize o objeto Contact com as propriedades desejadas.
1. Chame o método CreateContact para adicionar o contato ao Exchange Server.

O Aspose.Email fornece a classe [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/#ewsclient-class) para se conectar ao Microsoft Exchange Server usando os Serviços Web do Exchange. Os exemplos de código mostram como usar os Serviços Web do Exchange para adicionar contatos a um Exchange Server.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-AddContactsToExchangeServerUsingEWS-AddContactsToExchangeServerUsingEWS.cs" >}}

## **Atualizando Contatos**

As informações de contato podem ser atualizadas usando o Microsoft Outlook. O Aspose.Email também pode atualizar informações de contato no Exchange Server usando o Serviço Web do Exchange (EWS). O método IEWSClient [UpdateContact](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/updatecontact/) pode atualizar informações de contato no Exchange Server.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-UpdateContactInformationUsingEWS-UpdateContactInformationUsingEWS.cs" >}}

## **Deletando Contatos**

A classe [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) permite que o método DeleteContact acesse e delete contatos da pasta de contatos de um Exchange Server. Este método recebe o ID do contato ou MapiContact como parâmetro de entrada.

Para deletar contatos de um Exchange Server:

1. Inicialize o ExchangeWebServiceClient com o endereço e credenciais.
1. Delete um contato usando seu ID.
1. Delete um contato chamando o método [DeleteContact](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/deletecontact/) com [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/mapicontact/) como parâmetro de entrada.

Os seguintes exemplos de código mostram como deletar contatos de um servidor Exchange usando o serviço web do Exchange.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-DeleteContactsFromExchangeServerUsingEWS-DeleteContactsFromExchangeServerUsingEWS.cs" >}}

## **Trabalhando com Propriedades Estendidas de Contatos no Exchange Server**

``` cs

 IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
 
//As propriedades estendidas necessárias devem ser adicionadas para criá-las ou lê-las do Exchange Server

string[] extraFields = new string[] {{ "User Field 1", "User Field 2", "User Field 3", "User Field 4" }};

foreach (string extraField in extraFields)

    client.ContactExtendedPropertiesDefinition.Add(extraField);

//Criar um contato de teste no Exchange Server

Contact contact = new Contact();

contact.DisplayName = "EMAILNET-38433 - " + Guid.NewGuid().ToString();

foreach (string extraField in extraFields)

    contact.ExtendedProperties.Add(extraField, extraField);

string contactId = client.CreateContact(contact);

//recuperar o contato de volta do servidor após algum tempo

Thread.Sleep(5000);

contact = client.GetContact(contactId);

//Analisar as propriedades estendidas do contato

foreach (string extraField in extraFields)

    if (contact.ExtendedProperties.ContainsKey(extraField))

        Console.WriteLine(contact.ExtendedProperties[extraField].ToString());

```