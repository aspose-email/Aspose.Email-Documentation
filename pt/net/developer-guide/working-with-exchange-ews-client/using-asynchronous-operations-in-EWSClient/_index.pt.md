---
title: "Usando Operações Assíncronas no EWSClient"
url: /pt/net/usando-operacoes-assincronas-no-ewsclient/
weight: 42
type: docs
---

Ao contrário dos métodos síncronos, os métodos assíncronos são não bloqueadores e permitem realizar várias solicitações simultaneamente. Os métodos assíncronos são nomeados com o sufixo Async.

> **_NOTA:_** Métodos Async estão disponíveis em versões que visam .NET Core, .NET Framework 4.5 e posteriores.

## Implementando IAsyncTokenProvider para obter Tokens OAuth Assincronamente

O seguinte exemplo de código define uma classe `SomeAsyncTokenProvider`, que implementa a interface [IAsyncTokenProvider](https://reference.aspose.com/email/net/aspose.email.clients/iasynctokenprovider/).
A classe implementa o método assíncrono [GetAccessTokenAsync](https://reference.aspose.com/email/net/aspose.email.clients/iasynctokenprovider/getaccesstokenasync/) que retorna uma Task do tipo OAuthToken. Este método busca um [OAuthToken](https://reference.aspose.com/email/net/aspose.email.clients/oauthtoken/) válido de forma assíncrona.

```cs
private class SomeAsyncTokenProvider : IAsyncTokenProvider
{
    public SomeAsyncTokenProvider( /*alguns parâmetros*/)
    {
        ...
    }

    public async Task<OAuthToken> GetAccessTokenAsync(bool ignoreExistingToken = false,
        CancellationToken cancellationToken = default)
    {
        //Algum código assíncrono para obter um OAuthToken válido
        ...
    }

    public void Dispose()
    {
        ...
    }
}
```

## Criando a IAsyncEwsClientInstance

O próximo exemplo de código obtém um cliente Exchange Web Services (EWS) de forma assíncrona usando autenticação OAuth. O código executa os seguintes passos:

1. Cria um novo objeto [CancellationToken](https://reference.aspose.com/tasks/net/aspose.tasks/loadoptions/cancellationtoken/) que pode ser usado para cancelar operações assíncronas.
2. Instancia a classe `SomeAsyncTokenProvider` que implementa a interface [IAsyncTokenProvider](https://reference.aspose.com/email/net/aspose.email.clients/iasynctokenprovider/). Esta classe é usada como um parâmetro para construir um novo objeto [OAuthNetworkCredential](https://reference.aspose.com/email/net/aspose.email.clients/oauthnetworkcredential/oauthnetworkcredential/).
3. Define a URI da caixa de correio para o endpoint do Exchange Web Services.
4. Chama o método [GetEwsClientAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/getewsclientasync/) da classe [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) com a `mailboxUri` e o objeto `OAuthNetworkCredential` como parâmetros. Este método retorna um objeto Task, portanto, aguarda o resultado antes de continuar. O objeto `cancellationToken` é passado como um parâmetro opcional para o método [GetEwsClientAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/getewsclientasync/).

```cs
//O cancellationToken pode ser usado
var cancellationToken = new CancellationToken();

//Criar IAsyncEwsClientInstance
IAsyncTokenProvider tokenProvider = new SomeAsyncTokenProvider(/*alguns parâmetros*/);
const string mailboxUri = "https://outlook.office365.com/ews/exchange.asmx";
var ewsClient = await EWSClient.GetEwsClientAsync(mailboxUri, new OAuthNetworkCredential(tokenProvider),
    cancellationToken: cancellationToken);
```

## Enviando uma Mensagem

O exemplo de código abaixo está tentando enviar uma mensagem de email de forma assíncrona. O código executa os seguintes passos:

1. Cria um novo objeto [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) com os parâmetros da mensagem.
2. Chama o método [SendAsync](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice.sendgrid/sendgridclient/sendasync/) do objeto [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/), passando o MailMessage como parâmetro. O método é aguardado, pois retorna um objeto Task. O objeto `cancellationToken` é passado como um parâmetro opcional para o método [SendAsync](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice.sendgrid/sendgridclient/sendasync/).

```cs
MailMessage message = new MailMessage("from@aspose.com", "to@aspose.com", "Algum assunto", "Algum corpo");
await ewsClient.SendAsync(message, cancellationToken: cancellationToken);
```

## Buscando uma Mensagem com Anexos

Para buscar uma mensagem de email de forma assíncrona, use o seguinte exemplo de código com os passos descritos abaixo:

1. Chame o método [FetchItemAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iasyncewsclient/fetchitemasync/) de um EWSclient. O método leva dois parâmetros:

   - `messageUri` é uma string que representa a URI da mensagem a ser buscada
   - `cancellationToken` é um parâmetro opcional que pode ser usado para cancelar a operação assíncrona. O método retorna um objeto Task que resolve para um objeto [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) quando a operação assíncrona estiver completa. A palavra-chave "await" é usada para esperar que o objeto Task seja concluído antes de prosseguir.

2. Atribua à variável `fetched` o resultado da Task concluída, que é um objeto [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) contendo os dados da mensagem buscada.

   ```cs
      var fetched = await ewsClient.FetchItemAsync(messageUri, cancellationToken: cancellationToken);
   ```

## Anexando Mensagens

O exemplo de código abaixo está tentando anexar mensagens de email de forma assíncrona. O código executa os seguintes passos:

1. Chama o método [AppendMessagesAsync](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/appendmessagesasync/) do objeto [EWSclient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/). O método leva um objeto [EwsAppendMessage](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/) que contém parâmetros: as mensagens a serem anexadas, a URI da pasta de destino e o token de cancelamento.
2. Cria o objeto [EwsAppendMessage](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/) usando o método [Create](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/create/) e o configura com as seguintes chamadas de método:

   - [AddMessage](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/addmessage/) adiciona uma mensagem à operação de anexo.
   - [SetFolder](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/setfolder/) define a URI da pasta de destino para a operação de anexo.
   - [SetCancellationToken](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/setcancellationtoken/) define o token de cancelamento que pode ser usado para cancelar a operação assíncrona.

3. O método [AppendMessagesAsync](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/appendmessagesasync/) retorna um objeto Task que resolve para um objeto IEnumerable<string> quando a operação assíncrona estiver completa. A palavra-chave "await" é usada para esperar que o objeto Task seja concluído antes de prosseguir.
4. A variável `uris` é atribuída ao resultado da Task concluída, que é um objeto IEnumerable<string> contendo as URIs das mensagens anexadas.

```cs
IEnumerable<string> uris = await ewsClient.AppendMessagesAsync(
    EwsAppendMessage.Create()
        .AddMessage(message)
        .AddMessage(fetched)
        .SetFolder(folderUri)
        .SetCancellationToken(cancellationToken));
```

## Copiando Itens

O exemplo de código abaixo mostra como copiar itens e executa os seguintes passos:

1. Chama o método [CopyItemAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iasyncewsclient/copyitemasync/) do objeto [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/). O método leva três parâmetros: 

   - `messageUri` é uma string que representa a URI da mensagem a ser copiada 
   - `destinationFolderUri` é uma string que representa a URI da pasta de destino
   - `cancellationToken` é um parâmetro opcional que pode ser usado para cancelar a operação assíncrona. 

   O método retorna um objeto Task que resolve para uma string quando a operação assíncrona estiver completa. A palavra-chave "await" é usada para esperar que o objeto Task seja concluído antes de prosseguir.

2. A variável `newItemUri` é atribuída ao resultado da Task concluída, que é uma string contendo a URI da nova cópia da mensagem.

```cs
string newItemUri = await ewsClient.CopyItemAsync(messageUri, destinationFolderUri, cancellationToken);
```

## Deletando Itens

O seguinte código está tentando deletar uma mensagem de email de forma assíncrona.

Ele chama o método [DeleteItemAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iasyncewsclient/deleteitemasync/) de um objeto EWSClient. O método leva três parâmetros:

- `newItemUri` é uma string que representa a URI do item a ser deletado
- `DeletionOptions.DeletePermanently` especifica que o item deve ser deletado permanentemente
- `cancellationToken` é um parâmetro opcional que pode ser usado para cancelar a operação assíncrona. 

O método retorna um objeto Task que é concluído quando a operação assíncrona estiver completa. A palavra-chave "await" é usada para esperar que o objeto Task seja concluído antes de prosseguir.

```cs
await ewsClient.DeleteItemAsync(newItemUri, DeletionOptions.DeletePermanently, cancellationToken);
```

## Deletando Pastas

O seguinte código está tentando deletar uma pasta de forma assíncrona.

Ele chama o método [DeleteFolderAsync](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/deletefolderasync/) de um objeto EWSClient. O método leva três parâmetros:

- `folderUri` é uma string que representa a URI da pasta a ser deletada
- `deletePermanently` especifica se a pasta deve ser deletada permanentemente ou movida para a pasta "Itens Excluídos"
- `cancellationToken` é um parâmetro opcional que pode ser usado para cancelar a operação assíncrona. 

O método retorna um objeto Task que é concluído quando a operação assíncrona estiver completa. A palavra-chave "await" é usada para esperar que o objeto Task seja concluído antes de prosseguir.

```cs
const bool deletePermanently = true;
await ewsClient.DeleteFolderAsync(folderUri, deletePermanently, cancellationToken);
```

## Atualizando Itens

O exemplo de código abaixo está tentando atualizar um item de forma assíncrona. Ele executa os seguintes passos:

1. Cria um objeto [EwsUpdateItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsupdateitem/) usando o método [Create](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsupdateitem/create/#create_2), passando um objeto item. O EwsUpdateItem representa os parâmetros da operação de atualização. O método [SetCancellationToken](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/setcancellationtoken/) é chamado no objeto [EwsUpdateItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsupdateitem/), passando o parâmetro `cancellationToken`, que é um parâmetro opcional que pode ser usado para cancelar a operação assíncrona.
2. Passa o objeto [EwsUpdateItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsupdateitem/) como parâmetro para o método [UpdateItemAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iasyncewsclient/updateitemasync/) de um objeto [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/).
3. O método [UpdateItemAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iasyncewsclient/updateitemasync/) retorna um objeto Task que é concluído quando a operação assíncrona estiver completa. A palavra-chave "await" é usada para esperar que o objeto Task seja concluído antes de prosseguir.

```cs
await ewsClient.UpdateItemAsync(
    EwsUpdateItem.Create(mapiNote)
        .SetCancellationToken(cancellationToken));
```