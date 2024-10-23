---
title: "Analisando Arquivos de Mensagens do Outlook"
url: /pt/net/parsing-outlook-message-files/
weight: 40
type: docs
---

{{% alert color="primary" %}} 

Usando Aspose.Email para .NET, os desenvolvedores podem não apenas carregar, mas também analisar conteúdos de arquivos de mensagens do Outlook.

- Para carregar arquivos MSG do disco, use o método estático [MapiMessage.Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/) da classe [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/).
- Para analisar o conteúdo do arquivo MSG, a classe [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) expõe uma série de métodos e propriedades.

Este tópico mostra como carregar e analisar um arquivo MSG para exibir seu conteúdo.

{{% /alert %}} 

Aspose.Email para .NET fornece a classe [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) que é usada para abrir e analisar um arquivo MSG. Como pode haver muitos destinatários em um arquivo MSG, a classe [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) expõe a propriedade [Recipients](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/recipients/) que retorna uma [MapiRecipientCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipientcollection/) que representa uma coleção de objetos [MapiRecipient](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipient/). O objeto [MapiRecipient](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipient/) também expõe métodos para trabalhar com atributos do destinatário.

A seguinte sequência de etapas serve a esse propósito:

1. Crie uma instância da classe [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) usando o método estático [MapiMessage.Load](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/).
1. Exiba o nome do remetente, o assunto e o corpo do arquivo MSG usando as propriedades [SenderName](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/sendername/), [Subject](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/subject/) e [Body](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/body/).
1. Use a propriedade [Recipients](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/recipients/) para obter uma referência à coleção de objetos [MapiRecipient](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipient/) associados ao arquivo MSG.
1. Percorra a coleção [MapiRecipientCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipientcollection/) para exibir o conteúdo de cada objeto [MapiRecipient](https://reference.aspose.com/email/net/aspose.email.mapi/mapirecipient/) através de seus métodos públicos.

```cs
// O caminho para o diretório de recursos.
string dataDir = RunExamples.GetDataDir_Email();

//Instanciar um arquivo MSG para carregar um arquivo MSG do disco
var outlookMessageFile = MapiMessage.Load(dataDir + "message.msg");
//Exibir o nome do remetente
Console.WriteLine("Nome do Remetente : " + outlookMessageFile.SenderName);
//Exibir Assunto
Console.WriteLine("Assunto : " + outlookMessageFile.Subject);
//Exibir Corpo
Console.WriteLine("Corpo : " + outlookMessageFile.Body);
//Exibir informações do Destinatário
Console.WriteLine("Destinatários : \n");

//Percorrer a coleção de destinatários associada ao objeto MapiMessage
foreach (var rcp in outlookMessageFile.Recipients)
{
	//Exibir endereço de e-mail do destinatário
	Console.WriteLine("Email : " + rcp.EmailAddress);
	//Exibir nome do destinatário
	Console.WriteLine("Nome : " + rcp.DisplayName);
	//Exibir tipo de destinatário
	Console.WriteLine("Tipo de Destinatário : " + rcp.RecipientType);
}
```

{{% alert %}}
**Experimente!**

Analise arquivos de e-mail online com o gratuito [**Aspose.Email Parser App**](https://products.aspose.app/email/pt/parser).
{{% /alert %}}