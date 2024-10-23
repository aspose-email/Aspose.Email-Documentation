---
title: "Trabalhando com Atributos Estendidos de Exchange de Itens do Exchange"
url: /pt/net/trabalhando-com-atributos-estendidos-de-exchange-de-itens-do-exchange/
weight: 140
type: docs
---

A API Aspose.Email permite que você crie, recupere e atualize propriedades estendidas de mensagens utilizando o cliente EWS da API. O seguinte exemplo de código ilustra isso ao criar um atributo estendido, adicioná-lo à mensagem no servidor e recuperar a mensagem como [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) do servidor Exchange usando o cliente [FetchItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitem/).

```csharp
// Define uma propriedade estendida PidTagBodyContentId
var extendedProperty = KnownPropertyList.BodyContentId;

// Crie uma mensagem e defina um valor para a propriedade estendida
var msg = new MapiMessage("from@from.com", "to@to.com", "Mensagem de teste", "Esta é uma mensagem de teste");
msg.SetProperty(extendedProperty, "03454432-6230-4e4b-887f-a498ea223599");

// Anexar mensagem
var uri = ewsClient.AppendMessage(ewsClient.MailboxInfo.InboxUri, msg, true);

// Buscar item anexado. Passe o descritor da propriedade estendida como parâmetro do método.
var fetchedMsg = ewsClient.FetchItem(uri, new PropertyDescriptor[] { extendedProperty });

// Imprimir o valor da propriedade estendida
Console.WriteLine(fetchedMsg.Properties[extendedProperty].GetString());
```