---
title: "Использование асинхронных операций в EWSClient"
url: /ru/net/using-asynchronous-operations-in-ewsclient/
weight: 42
type: docs
---

В отличие от синхронных методов, асинхронные методы не блокируют и позволяют выполнять несколько запросов одновременно. Асинхронные методы называются постфиксом Async.

> **_NOTE:_** Асинхронные методы доступны в версиях, ориентированных на .NET Core, .NET Framework 4.5 и более поздних.

## Внедрение IAsyncTokenProvider для асинхронного получения токенов OAuth

Следующий пример кода определяет `SomeAsyncTokenProvider` класс, который реализует [IAsyncTokenProvider](https://reference.aspose.com/email/net/aspose.email.clients/iasynctokenprovider/) интерфейс.
Класс реализует [GetAccessTokenAsync](https://reference.aspose.com/email/net/aspose.email.clients/iasynctokenprovider/getaccesstokenasync/) асинхронный метод, возвращающий задачу типа OAuthToken. Этот метод выбирает действительное [OAuthToken](https://reference.aspose.com/email/net/aspose.email.clients/oauthtoken/) asynchronously.

```cs
private class SomeAsyncTokenProvider : IAsyncTokenProvider
{
    public SomeAsyncTokenProvider( /*some parameters*/)
    {
        ...
    }

    public async Task<OAuthToken> GetAccessTokenAsync(bool ignoreExistingToken = false,
        CancellationToken cancellationToken = default)
    {
        //Some asynchronous code to get a valid OAuthToken
        ...
    }

    public void Dispose()
    {
        ...
    }
}
```

## Создание экземпляра IAsyncewsClient

В следующем примере кода клиент Exchange Web Services (EWS) асинхронно используется аутентификация OAuth. В коде выполняются следующие шаги:

1. Создает новое [CancellationToken](https://reference.aspose.com/tasks/net/aspose.tasks/loadoptions/cancellationtoken/) объект, который можно использовать для отмены асинхронных операций.
2. Instantiates `SomeAsyncTokenProvider` класс, реализующий [IAsyncTokenProvider](https://reference.aspose.com/email/net/aspose.email.clients/iasynctokenprovider/) интерфейс. Этот класс используется в качестве параметра для построения нового [OAuthNetworkCredential](https://reference.aspose.com/email/net/aspose.email.clients/oauthnetworkcredential/oauthnetworkcredential/) object.
3. Присваивает URI почтового ящика конечной точке веб-служб Exchange.
4. Звонит [GetEwsClientAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/getewsclientasync/) метод [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) класс с `mailboxUri` and `OAuthNetworkCredential` объект в качестве параметров. Этот метод возвращает объект Task, поэтому он ожидает результата, прежде чем продолжить. `cancellationToken` объект передается в качестве необязательного параметра в [GetEwsClientAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/getewsclientasync/) method.

```cs
//The cancellationToken can be used
var cancellationToken = new CancellationToken();

//Create IAsyncEwsClientInstance
IAsyncTokenProvider tokenProvider = new SomeAsyncTokenProvider(/*some parameters*/);
const string mailboxUri = "https://outlook.office365.com/ews/exchange.asmx";
var ewsClient = await EWSClient.GetEwsClientAsync(mailboxUri, new OAuthNetworkCredential(tokenProvider),
    cancellationToken: cancellationToken);
```

## Отправка сообщения

В приведенном ниже примере кода предпринята попытка асинхронной отправки сообщения электронной почты. Код выполняет следующие шаги:

1. Создает новое [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) объект с параметрами сообщения.
2. Звонит [SendAsync](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice.sendgrid/sendgridclient/sendasync/) метод [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) объект, передающий MailMessage в качестве параметра. Метод ожидается, так как он возвращает объект Task. `cancellationToken` объект передается в качестве необязательного параметра в [SendAsync](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice.sendgrid/sendgridclient/sendasync/) method.

```cs
MailMessage message = new MailMessage("from@aspose.com", "to@aspose.com", "Some subject", "Some body");
await ewsClient.SendAsync(message, cancellationToken: cancellationToken);
```

## Получение сообщения с вложениями

Чтобы получить сообщение электронной почты в асинхронном режиме, используйте следующий пример кода с описанными ниже шагами:

1. Позвоните [FetchItemAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iasyncewsclient/fetchitemasync/) метод EWSClient. Метод принимает два параметра:

   - `messageUri` это строка, представляющая URI сообщения, которое нужно получить
   - `cancellationToken` необязательный параметр, который можно использовать для отмены асинхронной операции. Метод возвращает объект Task, который преобразуется в [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) объект после завершения асинхронной операции. Ключевое слово «await» используется для ожидания завершения объекта Task перед продолжением.

2. Присвоить `fetched` переменная — результат выполнения Задачи, который представляет собой [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) объект, содержащий данные полученного сообщения.

   ```cs
      var fetched = await ewsClient.FetchItemAsync(messageUri, cancellationToken: cancellationToken);
   ```

## Добавление сообщений

В приведенном ниже примере кода предпринимается попытка асинхронного добавления сообщений электронной почты. Код выполняет следующие шаги:

1. Звонит [AppendMessagesAsync](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/appendmessagesasync/) метод [EWSclient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) объект. Метод принимает [EwsAppendMessage](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/) объект, содержащий параметры: добавляемые сообщения, URI целевой папки и токен отмены.
2. Создает [EwsAppendMessage](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/) объект, использующий [Create](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/create/) метод и настраивает его с помощью следующих вызовов методов:

   - [AddMessage](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/addmessage/) добавляет сообщение к операции добавления.
   - [SetFolder](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/setfolder/) задает URI целевой папки для операции добавления.
   - [SetCancellationToken](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/setcancellationtoken/) задает токен отмены, который можно использовать для отмены асинхронной операции.

3. The [AppendMessagesAsync](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/appendmessagesasync/) метод возвращает объект Task, который преобразуется в IEnumerable<string> объект после завершения асинхронной операции. Ключевое слово «await» используется для ожидания завершения объекта Task перед продолжением.
4. The `uris` переменной присваивается результат выполнения Задачи, который представляет собой IEnumerable<string> объект, содержащий URI добавленных сообщений.

```cs
IEnumerable<string> uris = await ewsClient.AppendMessagesAsync(
    EwsAppendMessage.Create()
        .AddMessage(message)
        .AddMessage(fetched)
        .SetFolder(folderUri)
        .SetCancellationToken(cancellationToken));
```

## Копирование элементов

В приведенном ниже примере кода показано, как копировать элементы, и выполняются следующие шаги:

1. Звонит [CopyItemAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iasyncewsclient/copyitemasync/) метод [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) объект. Метод принимает три параметра:

   - `messageUri` строка, представляющая URI копируемого сообщения
   - `destinationFolderUri` это строка, представляющая URI целевой папки
   - `cancellationToken` необязательный параметр, который можно использовать для отмены асинхронной операции.

   Метод возвращает объект Task, который после завершения асинхронной операции преобразуется в строку. Ключевое слово «await» используется для ожидания завершения объекта Task перед продолжением.

2. `newItemUri` переменной присваивается результат выполнения Задачи, представляющий собой строку, содержащую URI вновь созданной копии сообщения.

```cs
string newItemUri = await ewsClient.CopyItemAsync(messageUri, destinationFolderUri, cancellationToken);
```

## Удаление элементов

Следующий код пытается асинхронно удалить сообщение электронной почты.

Оно называет [DeleteItemAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iasyncewsclient/deleteitemasync/) метод объекта EWSClient. Метод принимает три параметра:

- `newItemUri` строка, представляющая URI удаляемого элемента
- `DeletionOptions.DeletePermanently` указывает, что элемент должен быть удален навсегда
- `cancellationToken` необязательный параметр, который можно использовать для отмены асинхронной операции.

Метод возвращает объект Task, который завершается после завершения асинхронной операции. Ключевое слово «await» используется для ожидания завершения объекта Task перед продолжением.

```cs
await ewsClient.DeleteItemAsync(newItemUri, DeletionOptions.DeletePermanently, cancellationToken);
```

## Удаление папок

Следующий код пытается асинхронно удалить папку.

Оно называет [DeleteFolderAsync](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/deletefolderasync/) метод объекта EWSClient. Метод принимает три параметра:

- `folderUri` строка, представляющая URI удаляемой папки
- `deletePermanently` указывает, следует ли удалить папку навсегда или переместить ее в папку «Удаленные элементы»
- `cancellationToken` необязательный параметр, который можно использовать для отмены асинхронной операции.

Метод возвращает объект Task, который завершается после завершения асинхронной операции. Ключевое слово «await» используется для ожидания завершения объекта Task перед продолжением.

```cs
const bool deletePermanently = true;
await ewsClient.DeleteFolderAsync(folderUri, deletePermanently, cancellationToken);
```

## Обновление элементов

В приведенном ниже примере кода предпринята попытка асинхронного обновления элемента. Он выполняет следующие шаги:

1. Создает [EwsUpdateItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsupdateitem/) объект, использующий [Create](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsupdateitem/create/#create_2) метод, передающий объект элемента. EWSupdateItem представляет собой параметры операции обновления. [SetCancellationToken](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/setcancellationtoken/) метод вызывается на [EwsUpdateItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsupdateitem/) объект, проходящий в `cancellationToken` параметр, который является необязательным параметром, который можно использовать для отмены асинхронной операции.
2. Передает [EwsUpdateItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsupdateitem/) объект в качестве параметра для [UpdateItemAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iasyncewsclient/updateitemasync/) метод [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/).
3. The [UpdateItemAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iasyncewsclient/updateitemasync/) метод возвращает объект Task, который завершается после завершения асинхронной операции. Ключевое слово «await» используется для ожидания завершения объекта Task перед продолжением.

```cs
await ewsClient.UpdateItemAsync(
    EwsUpdateItem.Create(mapiNote)
        .SetCancellationToken(cancellationToken));
```
