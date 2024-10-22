---
title: "Trabalhando com Atributos Estendidos de Exchange de Itens do Exchange"
url: /pt/java/trabalhando-com-Atributos-Estendidos-de-Exchange-de-Itens-do-Exchange/
weight: 140
type: docs
---


A API Aspose.Email permite que você crie, recupere e atualize propriedades estendidas de mensagens usando o cliente EWS da API. O seguinte exemplo de código ilustra isso criando um atributo estendido, adicionando-o à mensagem no servidor e recuperando a mensagem como [MapiMessage](https://apireference.aspose.com/email/java/com.aspose.email/mapimessage) do servidor Exchange usando o método [fetchItem](https://reference.aspose.com/email/java/com.aspose.email/IEWSClient#fetchItem\(java.lang.String,%20java.lang.Iterable\)) do cliente.

~~~Java
// Defina uma propriedade estendida PidTagBodyContentId
PropertyDescriptor extendedProperty = KnownPropertyList.BODY_CONTENT_ID;

// Crie uma mensagem e defina um valor de propriedade estendida
MapiMessage msg = new MapiMessage("from@from.com", "to@to.com",
        "Mensagem de teste", "Esta é uma mensagem de teste");
msg.setProperty(extendedProperty, "03454432-6230-4e4b-887f-a498ea223599");

// Anexar mensagem
String uri = ewsClient.appendMessage(ewsClient.getMailboxInfo().getInboxUri(), msg, true);

// Recuperar item anexado. Passe o descritor de propriedade estendida como parâmetro do método.
MapiMessage fetchedMsg = ewsClient.fetchItem(uri, Arrays.asList(new PropertyDescriptor[] { extendedProperty }));

// Imprimir o valor da propriedade estendida
System.out.println(fetchedMsg.getProperties().get_Item(extendedProperty).getString());
~~~