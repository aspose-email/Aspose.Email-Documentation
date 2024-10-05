---
title: "Использование асинхронных операций в EWSClient"
url: /ru/net/using-asynchronous-operations-in-ewsclient/
weight: 42
type: docs
---

В отличие от синхронных методов, асинхронные методы не блокируют выполнение и позволяют выполнять несколько запросов одновременно. Асинхронные методы имеют суффикс Async.

> **_ЗАМЕТКА:_** Асинхронные методы доступны в версиях, совместимых с .NET Core, .NET Framework 4.5 и выше.

## Реализация IAsyncTokenProvider для получения OAuth токенов асинхронно

Следующий пример кода определяет класс `SomeAsyncTokenProvider`, который реализует интерфейс [IAsyncTokenProvider](https://reference.aspose.com/email/net/aspose.email.clients/iasynctokenprovider/).
Класс реализует асинхронный метод [GetAccessTokenAsync](https://reference.aspose.com/email/net/aspose.email.clients/iasynctokenprovider/getaccesstokenasync/), который возвращает Task типа OAuthToken. Этот метод асинхронно получает действительный [OAuthToken](https://reference.aspose.com/email/net/aspose.email.clients/oauthtoken/).

```cs
private class SomeAsyncTokenProvider : IAsyncTokenProvider
{
    public SomeAsyncTokenProvider( /*некоторые параметры*/)
    {
        ...
    }

    public async Task<OAuthToken> GetAccessTokenAsync(bool ignoreExistingToken = false,
        CancellationToken cancellationToken = default)
    {
        //Некоторый асинхронный код для получения действительного OAuthToken
        ...
    }

    public void Dispose()
    {
        ...
    }
}
```

## Создание IAsyncEwsClientInstance

Следующий пример кода асинхронно получает клиент Exchange Web Services (EWS) с использованием OAuth аутентификации. Код выполняет следующие шаги:

1. Создает новый объект [CancellationToken](https://reference.aspose.com/tasks/net/aspose.tasks/loadoptions/cancellationtoken/), который можно использовать для отмены асинхронных операций.
2. Создает экземпляр класса `SomeAsyncTokenProvider`, который реализует интерфейс [IAsyncTokenProvider](https://reference.aspose.com/email/net/aspose.email.clients/iasynctokenprovider/). Этот класс используется в качестве параметра для создания нового объекта [OAuthNetworkCredential](https://reference.aspose.com/email/net/aspose.email.clients/oauthnetworkcredential/oauthnetworkcredential/).
3. Устанавливает URI почтового ящика для конечной точки Exchange Web Services.
4. Вызывает метод [GetEwsClientAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/getewsclientasync/) класса [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) с параметрами `mailboxUri` и `OAuthNetworkCredential`. Этот метод возвращает объект Task, поэтому он ожидает результат перед продолжением. Объект `cancellationToken` передается как необязательный параметр в метод [GetEwsClientAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/getewsclientasync/).

```cs
//Объект cancellationToken можно использовать
var cancellationToken = new CancellationToken();

//Создание IAsyncEwsClientInstance
IAsyncTokenProvider tokenProvider = new SomeAsyncTokenProvider(/*некоторые параметры*/);
const string mailboxUri = "https://outlook.office365.com/ews/exchange.asmx";
var ewsClient = await EWSClient.GetEwsClientAsync(mailboxUri, new OAuthNetworkCredential(tokenProvider),
    cancellationToken: cancellationToken);
```

## Отправка сообщения

Пример кода ниже пытается асинхронно отправить электронное сообщение. Код выполняет следующие шаги:

1. Создает новый объект [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) с параметрами сообщения.
2. Вызывает метод [SendAsync](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice.sendgrid/sendgridclient/sendasync/) объекта [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/), передавая MailMessage в качестве параметра. Метод ожидается, так как он возвращает объект Task. Объект `cancellationToken` передается как необязательный параметр в метод [SendAsync](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice.sendgrid/sendgridclient/sendasync/).

```cs
MailMessage message = new MailMessage("from@aspose.com", "to@aspose.com", "Тема", "Текст сообщения");
await ewsClient.SendAsync(message, cancellationToken: cancellationToken);
```

## Получение сообщения с вложениями

Чтобы асинхронно получить электронное сообщение, используйте следующий пример кода с описанными ниже шагами:

1. Вызывается метод [FetchItemAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iasyncewsclient/fetchitemasync/) EWSclient. Метод принимает два параметра:

   - `messageUri` — строка, представляющая URI сообщения для получения
   - `cancellationToken` — необязательный параметр, который можно использовать для отмены асинхронной операции. Метод возвращает объект Task, который разрешается в объект [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) по завершении асинхронной операции. Ключевое слово "await" используется для ожидания завершения объекта Task перед продолжением.

2. Присваивает переменной `fetched` результат завершенного Task, который является объектом [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/), содержащим данные полученного сообщения.

   ```cs
      var fetched = await ewsClient.FetchItemAsync(messageUri, cancellationToken: cancellationToken);
   ```

## Добавление сообщений

Пример кода ниже пытается асинхронно добавить электронные сообщения. Код выполняет следующие шаги:

1. Вызывает метод [AppendMessagesAsync](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/appendmessagesasync/) объекта [EWSclient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/). Метод принимает объект [EwsAppendMessage](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/), содержащий параметры: сообщения для добавления, URI целевой папки и токен отмены.
2. Создает объект [EwsAppendMessage](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/) с использованием метода [Create](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/create/) и настраивает его с помощью следующих вызовов методов:

   - [AddMessage](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/addmessage/) добавляет сообщение к операции добавления.
   - [SetFolder](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/setfolder/) устанавливает URI целевой папки для операции добавления.
   - [SetCancellationToken](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/setcancellationtoken/) устанавливает токен отмены, который можно использовать для отмены асинхронной операции.

3. Метод [AppendMessagesAsync](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/appendmessagesasync/) возвращает объект Task, который разрешается в объект IEnumerable<string> по завершении асинхронной операции. Ключевое слово "await" используется для ожидания завершения объекта Task перед продолжением.
4. Переменной `uris` присваивается результат завершенного Task, который является объектом IEnumerable<string>, содержащим URI добавленных сообщений.

```cs
IEnumerable<string> uris = await ewsClient.AppendMessagesAsync(
    EwsAppendMessage.Create()
        .AddMessage(message)
        .AddMessage(fetched)
        .SetFolder(folderUri)
        .SetCancellationToken(cancellationToken));
```

## Копирование элементов

Пример кода ниже показывает, как копировать элементы и выполняет следующие шаги:

1. Вызывает метод [CopyItemAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iasyncewsclient/copyitemasync/) объекта [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/). Метод принимает три параметра:

   - `messageUri` — строка, представляющая URI сообщения для копирования
   - `destinationFolderUri` — строка, представляющая URI целевой папки
   - `cancellationToken` — необязательный параметр, который можно использовать для отмены асинхронной операции.

   Метод возвращает объект Task, который разрешается в строку по завершении асинхронной операции. Ключевое слово "await" используется для ожидания завершения объекта Task перед продолжением.

2. Переменной `newItemUri` присваивается результат завершенного Task, который является строкой, содержащей URI новой созданной копии сообщения.

```cs
string newItemUri = await ewsClient.CopyItemAsync(messageUri, destinationFolderUri, cancellationToken);
```

## Удаление элементов

Следующий код пытается асинхронно удалить электронное сообщение.

Он вызывает метод [DeleteItemAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iasyncewsclient/deleteitemasync/) объекта EWSClient. Метод принимает три параметра:

- `newItemUri` — строка, представляющая URI элемента для удаления
- `DeletionOptions.DeletePermanently` указывает, что элемент должен быть удален навсегда
- `cancellationToken` — необязательный параметр, который можно использовать для отмены асинхронной операции.

Метод возвращает объект Task, который завершается по завершении асинхронной операции. Ключевое слово "await" используется для ожидания завершения объекта Task перед продолжением.

```cs
await ewsClient.DeleteItemAsync(newItemUri, DeletionOptions.DeletePermanently, cancellationToken);
```

## Удаление папок

Следующий код пытается асинхронно удалить папку.

Он вызывает метод [DeleteFolderAsync](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/deletefolderasync/) объекта EWSClient. Метод принимает три параметра:

- `folderUri` — строка, представляющая URI папки для удаления
- `deletePermanently` — указывает, следует ли удалять папку навсегда или переместить ее в папку "Удаленные элементы"
- `cancellationToken` — необязательный параметр, который можно использовать для отмены асинхронной операции.

Метод возвращает объект Task, который завершается по завершении асинхронной операции. Ключевое слово "await" используется для ожидания завершения объекта Task перед продолжением.

```cs
const bool deletePermanently = true;
await ewsClient.DeleteFolderAsync(folderUri, deletePermanently, cancellationToken);
```

## Обновление элементов

Пример кода ниже пытается асинхронно обновить элемент. Он выполняет следующие шаги:

1. Создает объект [EwsUpdateItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsupdateitem/) с использованием метода [Create](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsupdateitem/create/#create_2), передавая объект элемента. EwsUpdateItem представляет параметры операции обновления. Метод [SetCancellationToken](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/setcancellationtoken/) вызывается на объекте [EwsUpdateItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsupdateitem/), передавая параметр `cancellationToken`, который является необязательным параметром, который можно использовать для отмены асинхронной операции.
2. Передает объект [EwsUpdateItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsupdateitem/) в качестве параметра методу [UpdateItemAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iasyncewsclient/updateitemasync/) объекта [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/).
3. Метод [UpdateItemAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iasyncewsclient/updateitemasync/) возвращает объект Task, который завершается по завершении асинхронной операции. Ключевое слово "await" используется для ожидания завершения объекта Task перед продолжением.

```cs
await ewsClient.UpdateItemAsync(
    EwsUpdateItem.Create(mapiNote)
        .SetCancellationToken(cancellationToken));
```