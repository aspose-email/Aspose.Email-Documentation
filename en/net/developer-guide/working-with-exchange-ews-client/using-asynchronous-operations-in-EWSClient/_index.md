---
title: Using Asynchronous Operations in EWSClient
type: docs
weight: 42
url: /net/using-asynchronous-operations-in-ewsclient/
---

Unlike the synchronous methods, the asynchronous methods are non-blocking and allow to perform multiple requests simultaneously. Asynchronous methods are named with the Async postfix.

> **_NOTE:_** Async methods are available in versions targeting .NET Core, .NET Framework 4.5, and later.

## Implementing IAsyncTokenProvider to get OAuth Tokens Asynchronously

The following code sample defines a `SomeAsyncTokenProvider` class, which implements the [IAsyncTokenProvider](https://reference.aspose.com/email/net/aspose.email.clients/iasynctokenprovider/) interface.
The class implements [GetAccessTokenAsync](https://reference.aspose.com/email/net/aspose.email.clients/iasynctokenprovider/getaccesstokenasync/) asynchronous method that returns a Task of type OAuthToken. This method fetches a valid [OAuthToken](https://reference.aspose.com/email/net/aspose.email.clients/oauthtoken/) asynchronously.

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

## Creating the IAsyncEwsClientInstance

The next code example obtains an Exchange Web Services (EWS) client asynchronously using OAuth authentication. The code performs the following steps:

1. Creates a new [CancellationToken](https://reference.aspose.com/tasks/net/aspose.tasks/loadoptions/cancellationtoken/) object that can be used to cancel asynchronous operations.
2. Instantiates `SomeAsyncTokenProvider` class that implements the [IAsyncTokenProvider](https://reference.aspose.com/email/net/aspose.email.clients/iasynctokenprovider/) interface. This class is used as a parameter for constructing a new [OAuthNetworkCredential](https://reference.aspose.com/email/net/aspose.email.clients/oauthnetworkcredential/oauthnetworkcredential/) object.
3. Sets the mailbox URI to the Exchange Web Services endpoint.
4. Calls the [GetEwsClientAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/getewsclientasync/) method of the [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) class with the `mailboxUri` and `OAuthNetworkCredential` object as parameters. This method returns a Task object, so it awaits the result before continuing. The `cancellationToken` object is passed as an optional parameter to the [GetEwsClientAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/getewsclientasync/) method.

```cs
//The cancellationToken can be used
var cancellationToken = new CancellationToken();

//Create IAsyncEwsClientInstance
IAsyncTokenProvider tokenProvider = new SomeAsyncTokenProvider(/*some parameters*/);
const string mailboxUri = "https://outlook.office365.com/ews/exchange.asmx";
var ewsClient = await EWSClient.GetEwsClientAsync(mailboxUri, new OAuthNetworkCredential(tokenProvider),
    cancellationToken: cancellationToken);
```

## Sending a Message

The code example below is attempting to send an email message asynchronously. The code performs the following steps:

1. Creates a new [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) object with the message parameters.
2. Calls the [SendAsync](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice.sendgrid/sendgridclient/sendasync/) method of the [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) object, passing the MailMessage as a parameter. Method is awaited since it returns a Task object. The `cancellationToken` object is passed as an optional parameter to the [SendAsync](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice.sendgrid/sendgridclient/sendasync/) method.

```cs
MailMessage message = new MailMessage("from@aspose.com", "to@aspose.com", "Some subject", "Some body");
await ewsClient.SendAsync(message, cancellationToken: cancellationToken);
```

## Fetching a Message with Attachments

To fetch an email message asynchronously, use the following code example with the steps described below:

1. Call the [FetchItemAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iasyncewsclient/fetchitemasync/) method of an EWSclient. The method takes two parameters:

   - `messageUri` is a string representing the URI of the message to fetch
   - `cancellationToken` is an optional parameter that can be used to cancel the asynchronous operation. The method returns a Task object that resolves to a [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) object when the asynchronous operation is complete. The "await" keyword is used to wait for the Task object to complete before proceeding.

2. Assign to the `fetched` variable the result of the completed Task, which is a [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) object containing the fetched message data.

   ```cs
      var fetched = await ewsClient.FetchItemAsync(messageUri, cancellationToken: cancellationToken);
   ```

## Appending Messages

The code example below is attempting to append email messages asynchronously. The code performs the following steps:

1. Calls the [AppendMessagesAsync](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/appendmessagesasync/) method of an [EWSclient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) object. The method takes an [EwsAppendMessage](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/) object that contains paremeters: the messages to append, the target folder URI, and the cancellation token.
2. Creates the [EwsAppendMessage](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/) object using the [Create](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/create/) method and configures it with the following method calls:

   - [AddMessage](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/addmessage/) adds a message to the append operation.
   - [SetFolder](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/setfolder/) sets the target folder URI for the append operation.
   - [SetCancellationToken](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/setcancellationtoken/) sets the cancellation token that can be used to cancel the asynchronous operation.

3. The [AppendMessagesAsync]((https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/appendmessagesasync/)) method returns a Task object that resolves to an IEnumerable<string> object when the asynchronous operation is complete. The "await" keyword is used to wait for the Task object to complete before proceeding.
4. The `uris` variable is assigned the result of the completed Task, which is an IEnumerable<string> object containing the URIs of the appended messages.

```cs
IEnumerable<string> uris = await ewsClient.AppendMessagesAsync(
    EwsAppendMessage.Create()
        .AddMessage(message)
        .AddMessage(fetched)
        .SetFolder(folderUri)
        .SetCancellationToken(cancellationToken));
```

## Copying Items

The code sample below shows how to copy items and performs the following steps:

1. Calls the [CopyItemAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iasyncewsclient/copyitemasync/) method of an [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) object. The method takes three parameters: 

   - `messageUri` is a string representing the URI of the message to copy 
   - `destinationFolderUri` is a string representing the URI of the destination folder
   - `cancellationToken` is an optional parameter that can be used to cancel the asynchronous operation. 

   The method returns a Task object that resolves to a string when the asynchronous operation is complete. The "await" keyword is used to wait for the Task object to complete before proceeding.

2. `newItemUri` variable is assigned the result of the completed Task, which is a string containing the URI of the newly created copy of the message.

```cs
string newItemUri = await ewsClient.CopyItemAsync(messageUri, destinationFolderUri, cancellationToken);
```

## Deleting Items

The following code is attempting to delete an email message asynchronously.

It calls the [DeleteItemAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iasyncewsclient/deleteitemasync/) method of an EWSClient object. The method takes three parameters:

- `newItemUri` is a string representing the URI of the item to delete
- `DeletionOptions.DeletePermanently` specifies that the item should be deleted permanently
- `cancellationToken` is an optional parameter that can be used to cancel the asynchronous operation. 

The method returns a Task object that completes when the asynchronous operation is complete. The "await" keyword is used to wait for the Task object to complete before proceeding.

```cs
await ewsClient.DeleteItemAsync(newItemUri, DeletionOptions.DeletePermanently, cancellationToken);
```

## Deleting Folders

The following code is attempting to delete a folder asynchronously.

It calls the [DeleteFolderAsync](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/deletefolderasync/) method of an EWSClient object. The method takes three parameters:

- `folderUri` is a string representing the URI of the folder to delete
- `deletePermanently` specifies whether to delete the folder permanently or move it to the "Deleted Items" folder
- `cancellationToken` is an optional parameter that can be used to cancel the asynchronous operation. 

The method returns a Task object that completes when the asynchronous operation is complete. The "await" keyword is used to wait for the Task object to complete before proceeding.

```cs
const bool deletePermanently = true;
await ewsClient.DeleteFolderAsync(folderUri, deletePermanently, cancellationToken);
```

## Updating Items

The code example below is attempting to update an item asynchronously. It performs the following steps:

1. Creates an [EwsUpdateItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsupdateitem/) object using the [Create](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsupdateitem/create/#create_2) method, passing in an item object. The EwsUpdateItem represents an update operation parameters. The [SetCancellationToken](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/setcancellationtoken/) method is called on the [EwsUpdateItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsupdateitem/) object, passing in the `cancellationToken` parameter, which is an optional parameter that can be used to cancel the asynchronous operation.
2. Passes the [EwsUpdateItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsupdateitem/) object as a parameter to the [UpdateItemAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iasyncewsclient/updateitemasync/) method of an [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/).
3. The [UpdateItemAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iasyncewsclient/updateitemasync/) method returns a Task object that completes when the asynchronous operation is complete. The "await" keyword is used to wait for the Task object to complete before proceeding.

```cs
await ewsClient.UpdateItemAsync(
    EwsUpdateItem.Create(mapiNote)
        .SetCancellationToken(cancellationToken));
```
