---
title: "Uso de operaciones asincrónicas en EWSClient"
url: /es/net/using-asynchronous-operations-in-ewsclient/
weight: 42
type: docs
---

A diferencia de los métodos sincrónicos, los métodos asíncronos no bloquean y permiten realizar varias solicitudes simultáneamente. Los métodos asincrónicos se nombran con el sufijo asíncrono.

> **_NOTE:_** Los métodos asíncronos están disponibles en las versiones orientadas a .NET Core, .NET Framework 4.5 y versiones posteriores.

## Implementación de IAsyncTokenProvider para obtener tokens de OAuth de forma asíncrona

El siguiente ejemplo de código define un `SomeAsyncTokenProvider` clase, que implementa la [IAsyncTokenProvider](https://reference.aspose.com/email/net/aspose.email.clients/iasynctokenprovider/) interfaz.
La clase implementa [GetAccessTokenAsync](https://reference.aspose.com/email/net/aspose.email.clients/iasynctokenprovider/getaccesstokenasync/) método asincrónico que devuelve una tarea de tipo OAuthToken. Este método obtiene un valor válido [OAuthToken](https://reference.aspose.com/email/net/aspose.email.clients/oauthtoken/) asynchronously.

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

## Creación de la instancia de IAsyncEWSClientInstance

El siguiente ejemplo de código obtiene un cliente de Exchange Web Services (EWS) de forma asincrónica mediante la autenticación OAuth. El código lleva a cabo los siguientes pasos:

1. Crea un nuevo [CancellationToken](https://reference.aspose.com/tasks/net/aspose.tasks/loadoptions/cancellationtoken/) objeto que se puede usar para cancelar operaciones asincrónicas.
2. Instantiates `SomeAsyncTokenProvider` clase que implementa el [IAsyncTokenProvider](https://reference.aspose.com/email/net/aspose.email.clients/iasynctokenprovider/) interfaz. Esta clase se usa como parámetro para construir una nueva [OAuthNetworkCredential](https://reference.aspose.com/email/net/aspose.email.clients/oauthnetworkcredential/oauthnetworkcredential/) object.
3. Establece el URI del buzón en el punto final de los servicios web de Exchange.
4. Llama al [GetEwsClientAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/getewsclientasync/) método del [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) clase con el `mailboxUri` and `OAuthNetworkCredential` objeto como parámetros. Este método devuelve un objeto Task, por lo que espera el resultado antes de continuar. El `cancellationToken` el objeto se pasa como parámetro opcional al [GetEwsClientAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/getewsclientasync/) method.

```cs
//The cancellationToken can be used
var cancellationToken = new CancellationToken();

//Create IAsyncEwsClientInstance
IAsyncTokenProvider tokenProvider = new SomeAsyncTokenProvider(/*some parameters*/);
const string mailboxUri = "https://outlook.office365.com/ews/exchange.asmx";
var ewsClient = await EWSClient.GetEwsClientAsync(mailboxUri, new OAuthNetworkCredential(tokenProvider),
    cancellationToken: cancellationToken);
```

## Enviar un mensaje

El ejemplo de código siguiente intenta enviar un mensaje de correo electrónico de forma asincrónica. El código lleva a cabo los siguientes pasos:

1. Crea un nuevo [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) objeto con los parámetros del mensaje.
2. Llama al [SendAsync](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice.sendgrid/sendgridclient/sendasync/) método del [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) objeto, pasando el MailMessage como parámetro. El método está en espera porque devuelve un objeto Task. El `cancellationToken` el objeto se pasa como parámetro opcional al [SendAsync](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice.sendgrid/sendgridclient/sendasync/) method.

```cs
MailMessage message = new MailMessage("from@aspose.com", "to@aspose.com", "Some subject", "Some body");
await ewsClient.SendAsync(message, cancellationToken: cancellationToken);
```

## Obtención de un mensaje con archivos adjuntos

Para recuperar un mensaje de correo electrónico de forma asincrónica, utilice el siguiente ejemplo de código con los pasos que se describen a continuación:

1. Llame al [FetchItemAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iasyncewsclient/fetchitemasync/) método de un EWSClient. El método toma dos parámetros:

   - `messageUri` es una cadena que representa el URI del mensaje que se va a buscar
   - `cancellationToken` es un parámetro opcional que se puede usar para cancelar la operación asincrónica. El método devuelve un objeto de tarea que se resuelve en [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) objeto cuando se complete la operación asincrónica. La palabra clave «await» se usa para esperar a que finalice el objeto de la tarea antes de continuar.

2. Asignar a `fetched` variable el resultado de la tarea completada, que es una [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) objeto que contiene los datos del mensaje obtenido.

   ```cs
      var fetched = await ewsClient.FetchItemAsync(messageUri, cancellationToken: cancellationToken);
   ```

## Agregar mensajes

El ejemplo de código siguiente intenta anexar mensajes de correo electrónico de forma asincrónica. El código lleva a cabo los siguientes pasos:

1. Llama al [AppendMessagesAsync](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/appendmessagesasync/) método de un [EWSclient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) objeto. El método requiere un [EwsAppendMessage](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/) objeto que contiene parámetros: los mensajes que se van a añadir, el URI de la carpeta de destino y el token de cancelación.
2. Crea el [EwsAppendMessage](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/) objeto que usa el [Create](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/create/) método y lo configura con las siguientes llamadas a métodos:

   - [AddMessage](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/addmessage/) añade un mensaje a la operación de anexión.
   - [SetFolder](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/setfolder/) establece el URI de la carpeta de destino para la operación de anexión.
   - [SetCancellationToken](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/setcancellationtoken/) establece el token de cancelación que se puede usar para cancelar la operación asincrónica.

3. The [AppendMessagesAsync](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/appendmessagesasync/) el método devuelve un objeto Task que se resuelve en un IEnumerable<string> objeto cuando se complete la operación asincrónica. La palabra clave «await» se usa para esperar a que finalice el objeto de la tarea antes de continuar.
4. The `uris` a la variable se le asigna el resultado de la tarea completada, que es un IEnumerable<string> objeto que contiene los URI de los mensajes adjuntos.

```cs
IEnumerable<string> uris = await ewsClient.AppendMessagesAsync(
    EwsAppendMessage.Create()
        .AddMessage(message)
        .AddMessage(fetched)
        .SetFolder(folderUri)
        .SetCancellationToken(cancellationToken));
```

## Copiar elementos

En el ejemplo de código que aparece a continuación se muestra cómo copiar elementos y se llevan a cabo los pasos siguientes:

1. Llama al [CopyItemAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iasyncewsclient/copyitemasync/) método de un [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) objeto. El método toma tres parámetros:

   - `messageUri` es una cadena que representa el URI del mensaje que se va a copiar
   - `destinationFolderUri` es una cadena que representa el URI de la carpeta de destino
   - `cancellationToken` es un parámetro opcional que se puede usar para cancelar la operación asincrónica.

   El método devuelve un objeto Task que se resuelve en una cadena cuando se completa la operación asincrónica. La palabra clave «await» se usa para esperar a que finalice el objeto Task antes de continuar.

2. `newItemUri` a la variable se le asigna el resultado de la tarea completada, que es una cadena que contiene el URI de la copia recién creada del mensaje.

```cs
string newItemUri = await ewsClient.CopyItemAsync(messageUri, destinationFolderUri, cancellationToken);
```

## Eliminar elementos

El siguiente código intenta eliminar un mensaje de correo electrónico de forma asincrónica.

Llama al [DeleteItemAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iasyncewsclient/deleteitemasync/) método de un objeto EWSClient. El método toma tres parámetros:

- `newItemUri` es una cadena que representa el URI del elemento que se va a eliminar
- `DeletionOptions.DeletePermanently` especifica que el elemento se debe eliminar de forma permanente
- `cancellationToken` es un parámetro opcional que se puede usar para cancelar la operación asincrónica.

El método devuelve un objeto Task que finaliza cuando finaliza la operación asincrónica. La palabra clave «await» se usa para esperar a que se complete el objeto de tarea antes de continuar.

```cs
await ewsClient.DeleteItemAsync(newItemUri, DeletionOptions.DeletePermanently, cancellationToken);
```

## Eliminar carpetas

El siguiente código intenta eliminar una carpeta de forma asincrónica.

Llama al [DeleteFolderAsync](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/deletefolderasync/) método de un objeto EWSClient. El método toma tres parámetros:

- `folderUri` es una cadena que representa el URI de la carpeta que se va a eliminar
- `deletePermanently` especifica si se debe eliminar la carpeta de forma permanente o moverla a la carpeta «Elementos eliminados»
- `cancellationToken` es un parámetro opcional que se puede usar para cancelar la operación asincrónica.

El método devuelve un objeto Task que finaliza cuando finaliza la operación asincrónica. La palabra clave «await» se usa para esperar a que se complete el objeto de tarea antes de continuar.

```cs
const bool deletePermanently = true;
await ewsClient.DeleteFolderAsync(folderUri, deletePermanently, cancellationToken);
```

## Actualización de elementos

El ejemplo de código siguiente intenta actualizar un artículo de forma asincrónica. Realiza los siguientes pasos:

1. Crea un [EwsUpdateItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsupdateitem/) objeto que usa el [Create](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsupdateitem/create/#create_2) método, pasando un objeto de elemento. El ewsUpdateItem representa los parámetros de una operación de actualización. El [SetCancellationToken](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/setcancellationtoken/) el método se invoca en el [EwsUpdateItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsupdateitem/) objeto, pasando por el `cancellationToken` parámetro, que es un parámetro opcional que se puede usar para cancelar la operación asincrónica.
2. Pasa el [EwsUpdateItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsupdateitem/) objeto como parámetro del [UpdateItemAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iasyncewsclient/updateitemasync/) método de un [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/).
3. The [UpdateItemAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iasyncewsclient/updateitemasync/) el método devuelve un objeto Task que finaliza cuando finaliza la operación asincrónica. La palabra clave «await» se usa para esperar a que se complete el objeto de tarea antes de continuar.

```cs
await ewsClient.UpdateItemAsync(
    EwsUpdateItem.Create(mapiNote)
        .SetCancellationToken(cancellationToken));
```
