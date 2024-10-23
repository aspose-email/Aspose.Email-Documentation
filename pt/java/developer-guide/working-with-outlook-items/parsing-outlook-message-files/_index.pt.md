---
title: "Análise de Arquivos de Mensagens do Outlook"
url: /pt/java/analise-arquivos-mensagens-outlook/
weight: 40
type: docs
---

{{% alert color="primary" %}} 

Usando Aspose.Email para Java, os desenvolvedores podem não apenas carregar, mas também analisar conteúdos de arquivos de mensagens do Outlook.

- Para carregar arquivos MSG do disco, use o método estático [Load](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#load-java.lang.String-) da classe [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/).
- Para analisar o conteúdo do arquivo MSG, a [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) expõe um número de métodos.

Este tópico mostra como carregar e, em seguida, analisar um arquivo MSG para exibir seu conteúdo.

{{% /alert %}} 

Aspose.Email para Java fornece a classe [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) que é usada para abrir e analisar um arquivo MSG. Como pode haver muitos destinatários em um arquivo MSG, a classe [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) expõe o método [getRecipients()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getRecipients--) que retorna uma [MapiRecipientCollection](https://reference.aspose.com/email/java/com.aspose.email/mapirecipientcollection/) que representa uma coleção de objetos [MapiRecipient](https://reference.aspose.com/email/java/com.aspose.email/mapirecipient/). O objeto [MapiRecipient](https://reference.aspose.com/email/java/com.aspose.email/mapirecipient/) também expõe métodos para trabalhar com atributos de destinatários.

A seguinte sequência de etapas serve a esse propósito:

1. Crie uma instância da classe [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) para carregar um arquivo MSG do método estático [Load](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#load-java.lang.String-).
2. Exiba o nome do remetente, o assunto e o corpo do arquivo MSG usando os métodos [getSenderName()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getSenderName--), [getSubject()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getSubject--) e [getBody()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getBody--) .
3. Chame o método [getRecipients()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getRecipients--) exposto pela classe [MapiRecipient](https://reference.aspose.com/email/java/com.aspose.email/mapirecipient/) para obter uma referência à coleção de objetos [MapiRecipient](https://reference.aspose.com/email/java/com.aspose.email/mapirecipient/) associados ao arquivo MSG.
4. Percorra a coleção [MapiRecipientCollection](https://reference.aspose.com/email/java/com.aspose.email/mapirecipientcollection/) para exibir o conteúdo de cada objeto [MapiRecipient](https://reference.aspose.com/email/java/com.aspose.email/mapirecipient/) por meio de seus métodos públicos.

```java
// O caminho para o diretório de recursos.
String dataDir = Utils.getSharedDataDir(ParsingOutlookMessageFiles.class) + "outlook/";

//Instanciar um arquivo MSG para carregar um arquivo MSG do disco
MapiMessage outlookMessageFile = MapiMessage.fromFile(dataDir + "message.msg");
//Exibir nome do remetente
System.out.println("Nome do Remetente : " + outlookMessageFile.getSenderName());
//Exibir Assunto
System.out.println("Assunto : " + outlookMessageFile.getSubject());
//Exibir Corpo
System.out.println("Corpo : " + outlookMessageFile.getBody());
//Exibir informações do Destinatário
System.out.println("Destinatários : \n");

//Percorrer a coleção de destinatários associada ao objeto MapiMessage
for (int i = 0; i < outlookMessageFile.getRecipients().size(); i++) {
	//Definir uma referência ao objeto MapiRecipient
	MapiRecipient rcp = (MapiRecipient) outlookMessageFile.getRecipients().get_Item(i);
	//Exibir endereço de email do destinatário
	System.out.println("Email : " + rcp.getEmailAddress());
	//Exibir nome do destinatário
	System.out.println("Nome : " + rcp.getDisplayName());
	//Exibir tipo do destinatário
	System.out.println("Tipo do Destinatário : " + rcp.getRecipientType());
}
```

{{% alert %}}
**Experimente!**

Analise arquivos de e-mail online com o gratuito [**Aspose.Email Parser App**](https://products.aspose.app/email/pt/parser).
{{% /alert %}}

## **Obtenha um Tipo de Item de uma Mensagem MAPI**

Aspose.Email oferece um enum [MapiItemType](https://reference.aspose.com/email/java/com.aspose.email/mapiitemtype/) que representa um tipo de item. Ele pode ser usado para conversão de mensagens em um objeto da classe correspondente derivada da interface [IMapiMessageItem](https://reference.aspose.com/email/java/com.aspose.email/imapimessageitem). Isso evita que os usuários verifiquem o valor da propriedade MessageClass antes da conversão da mensagem.

O seguinte exemplo de código demonstra como iterar pelas mensagens em uma pasta e converter cada mensagem MAPI em um tipo de item MAPI correspondente, dependendo do tipo da mensagem:

```java
for (MessageInfo messageInfo : folder.enumerateMessages()) {
    MapiMessage msg = pst.extractMessage(messageInfo);

    switch (msg.getSupportedType()) {
        // Tipo não suportado. MapiMessage não pode ser convertido em um tipo de item apropriado.
        // Apenas use no formato MSG.
        case MapiItemType.None:
            break;
        // Uma mensagem de e-mail. A conversão não é necessária.
        case MapiItemType.Message:
            break;
        // Um item de contato. Pode ser convertido em MapiContact.
        case MapiItemType.Contact:
            MapiContact contact = (MapiContact) msg.toMapiMessageItem();
            break;
        // Um item de calendário. Pode ser convertido em MapiCalendar.
        case MapiItemType.Calendar:
            MapiCalendar calendar = (MapiCalendar) msg.toMapiMessageItem();
            break;
        // Uma lista de distribuição. Pode ser convertida em MapiDistributionList.
        case MapiItemType.DistList:
            MapiDistributionList dl = (MapiDistributionList) msg.toMapiMessageItem();
            break;
        // Uma entrada de diário. Pode ser convertida em MapiJournal.
        case MapiItemType.Journal:
            MapiJournal journal = (MapiJournal) msg.toMapiMessageItem();
            break;
        // Um StickyNote. Pode ser convertido em MapiNote.
        case MapiItemType.Note:
            MapiNote note = (MapiNote) msg.toMapiMessageItem();
            break;
        // Um item de Tarefa. Pode ser convertido em MapiTask.
        case MapiItemType.Task:
            MapiTask task = (MapiTask) msg.toMapiMessageItem();
            break;
    }
}
```