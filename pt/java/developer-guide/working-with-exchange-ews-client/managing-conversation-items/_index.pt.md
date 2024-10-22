---
title: "Gerenciando Itens de Conversação"
url: /pt/java/gerenciando-itens-de-conversacao/
weight: 40
type: docs
---


Aspose.Email para Java pode ser usado para gerenciar os itens de conversação no Exchange Server com a classe [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient). Esta classe utiliza os Serviços Web do Exchange, que estão disponíveis apenas no Exchange Server 2007 e versões posteriores. Este artigo mostra como [encontrar](#finding-conversations), [copiar](#copying-conversations), [mover](#moving-conversations) e [deletar](#deleting-conversations) itens de conversação no Exchange Server 2010. O Microsoft Exchange Server 2010 Service Pack 1 é necessário para todos os recursos incluídos nesta seção.
## **Encontrando Conversas**
Para obter as informações da conversa de uma pasta específica no Exchange Server:

1. Conecte-se ao Exchange Server usando a classe IEWSClient.
1. Chame o método IEWSClient.findConversations() para encontrar todos os itens de conversação de uma pasta.
1. Exiba as propriedades do item de conversação, como ID, tópico da conversa e status da flag.

O seguinte trecho de código mostra como encontrar conversas.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);
System.out.println("Conectado ao Exchange 2010");

// Encontrar Itens de Conversa na pasta Caixa de Entrada
ExchangeConversation[] conversations = client.findConversations(client.getMailboxInfo().getInboxUri());
// Mostrar todas as conversas
for (ExchangeConversation conversation : conversations) {
    // Exibir propriedades da conversa como Id e Tópico
    System.out.println("Tópico: " + conversation.getConversationTopic());
    System.out.println("Status da Flag: " + conversation.getFlagStatus());
    System.out.println();
}
~~~
## **Copiando Conversas**
Para copiar conversas de uma pasta para outra:

1. Conecte-se ao Exchange Server usando a classe IEWSClient.
1. Chame o método IEWSClient.copyConversationItems() para copiar o item de conversação da pasta de origem para a pasta de destino.

O seguinte trecho de código mostra como copiar conversas.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);
System.out.println("Conectado ao Exchange 2010");

// Encontrar aqueles Itens de Conversa na pasta Caixa de Entrada que queremos copiar
ExchangeConversation[] conversations = client.findConversations(client.getMailboxInfo().getInboxUri());
for (ExchangeConversation conversation : conversations) {
    System.out.println("Tópico: " + conversation.getConversationTopic());
    // Copiar o item de conversa com base em alguma condição
    if (conversation.getConversationTopic().contains("teste email")) {
        client.copyConversationItems(conversation.getConversationId(), client.getMailboxInfo().getDeletedItemsUri());
        System.out.println("Item de conversa copiado para outra pasta");
    }
}
~~~
## **Movendo Conversas**
Para mover conversas de uma pasta para outra:

1. Conecte-se ao Exchange Server usando a classe IEWSClient.
1. Chame o método IEWSClient.moveConversationItems() para mover uma conversa da pasta de origem para a pasta de destino.

O seguinte trecho de código mostra como mover conversas.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);
System.out.println("Conectado ao Exchange 2010");

// Encontrar aqueles Itens de Conversa na pasta Caixa de Entrada que queremos mover
ExchangeConversation[] conversations = client.findConversations(client.getMailboxInfo().getInboxUri());

for (ExchangeConversation conversation : conversations) {
    System.out.println("Tópico: " + conversation.getConversationTopic());
    // Mover o item de conversa com base em alguma condição
    if (conversation.getConversationTopic().contains("teste email") == true) {
        client.moveConversationItems(conversation.getConversationId(), client.getMailboxInfo().getDeletedItemsUri());
        System.out.println("Item de conversa movido para outra pasta");
    }
}
~~~
## **Deletando Conversas**
Para deletar conversas de uma pasta:

1. Conecte-se ao Exchange Server usando a classe IEWSClient.
1. Chame o método IEWSClient.deleteConversationItems() para deletar o item de conversação da pasta de origem.

O seguinte trecho de código mostra como deletar conversas.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);
System.out.println("Conectado ao Exchange 2010");

// Encontrar aqueles Itens de Conversa na pasta Caixa de Entrada que queremos deletar
ExchangeConversation[] conversations = client.findConversations(client.getMailboxInfo().getInboxUri());
for (ExchangeConversation conversation : conversations) {
    System.out.println("Tópico: " + conversation.getConversationTopic());
    // Deletar o item de conversa com base em alguma condição
    if (conversation.getConversationTopic().contains("teste email") == true) {
        client.deleteConversationItems(conversation.getConversationId());
        System.out.println("Item de conversa deletado");
    }
}
~~~