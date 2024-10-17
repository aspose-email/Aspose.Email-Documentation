---
title: "Uso de operaciones asíncronas en EWSClient"
url: /es/net/uso-de-operaciones-asíncronas-en-ewsclient/
weight: 42
type: docs
---

A diferencia de los métodos síncronos, los métodos asíncronos son no bloqueantes y permiten realizar múltiples solicitudes simultáneamente. Los métodos asíncronos se nombran con el sufijo Async.

> **_NOTA:_** Los métodos Async están disponibles en versiones que apunten a .NET Core, .NET Framework 4.5 y posteriores.

## Implementando IAsyncTokenProvider para obtener tokens OAuth de forma asíncrona

El siguiente ejemplo de código define una clase `SomeAsyncTokenProvider`, que implementa la interfaz [IAsyncTokenProvider](https://reference.aspose.com/email/net/aspose.email.clients/iasynctokenprovider/). La clase implementa el método asíncrono [GetAccessTokenAsync](https://reference.aspose.com/email/net/aspose.email.clients/iasynctokenprovider/getaccesstokenasync/) que devuelve un Task de tipo OAuthToken. Este método obtiene un [OAuthToken](https://reference.aspose.com/email/net/aspose.email.clients/oauthtoken/) válido de forma asíncrona.

```cs
private class SomeAsyncTokenProvider : IAsyncTokenProvider
{
    public SomeAsyncTokenProvider( /*algunos parámetros*/)
    {
        ...
    }

    public async Task<OAuthToken> GetAccessTokenAsync(bool ignoreExistingToken = false,
        CancellationToken cancellationToken = default)
    {
        //Algún código asíncrono para obtener un OAuthToken válido
        ...
    }

    public void Dispose()
    {
        ...
    }
}
```

## Creando la instancia IAsyncEwsClientInstance

El siguiente ejemplo de código obtiene un cliente de Exchange Web Services (EWS) de forma asíncrona utilizando autenticación OAuth. El código realiza los siguientes pasos:

1. Crea un nuevo objeto [CancellationToken](https://reference.aspose.com/tasks/net/aspose.tasks/loadoptions/cancellationtoken/) que puede usarse para cancelar operaciones asíncronas.
2. Instancia la clase `SomeAsyncTokenProvider` que implementa la interfaz [IAsyncTokenProvider](https://reference.aspose.com/email/net/aspose.email.clients/iasynctokenprovider/). Esta clase se utiliza como un parámetro para construir un nuevo objeto [OAuthNetworkCredential](https://reference.aspose.com/email/net/aspose.email.clients/oauthnetworkcredential/oauthnetworkcredential/).
3. Establece la URI del buzón en el extremo de Exchange Web Services.
4. Llama al método [GetEwsClientAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/getewsclientasync/) de la clase [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) con la `mailboxUri` y el objeto `OAuthNetworkCredential` como parámetros. Este método devuelve un objeto Task, por lo que espera el resultado antes de continuar. El objeto `cancellationToken` se pasa como un parámetro opcional al método [GetEwsClientAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/getewsclientasync/).

```cs
//El cancellationToken puede ser usado
var cancellationToken = new CancellationToken();

//Crear IAsyncEwsClientInstance
IAsyncTokenProvider tokenProvider = new SomeAsyncTokenProvider(/*algunos parámetros*/);
const string mailboxUri = "https://outlook.office365.com/ews/exchange.asmx";
var ewsClient = await EWSClient.GetEwsClientAsync(mailboxUri, new OAuthNetworkCredential(tokenProvider),
    cancellationToken: cancellationToken);
```

## Enviando un mensaje

El siguiente ejemplo de código intenta enviar un mensaje de correo electrónico de forma asíncrona. El código realiza los siguientes pasos:

1. Crea un nuevo objeto [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) con los parámetros del mensaje.
2. Llama al método [SendAsync](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice.sendgrid/sendgridclient/sendasync/) del objeto [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/), pasando el MailMessage como parámetro. El método se espera ya que devuelve un objeto Task. El objeto `cancellationToken` se pasa como un parámetro opcional al método [SendAsync](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice.sendgrid/sendgridclient/sendasync/).

```cs
MailMessage message = new MailMessage("from@aspose.com", "to@aspose.com", "Algun asunto", "Algun cuerpo");
await ewsClient.SendAsync(message, cancellationToken: cancellationToken);
```

## Recuperando un mensaje con archivos adjuntos

Para recuperar un mensaje de correo electrónico de manera asíncrona, utiliza el siguiente ejemplo de código con los pasos descritos a continuación:

1. Llama al método [FetchItemAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iasyncewsclient/fetchitemasync/) de un EWSclient. El método toma dos parámetros:

   - `messageUri` es una cadena que representa la URI del mensaje a recuperar
   - `cancellationToken` es un parámetro opcional que se puede utilizar para cancelar la operación asíncrona. El método devuelve un objeto Task que se resuelve en un objeto [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) cuando la operación asíncrona se completa. La palabra clave "await" se utiliza para esperar que el objeto Task complete antes de proceder.

2. Asigna a la variable `fetched` el resultado de la tarea completada, que es un objeto [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) que contiene los datos del mensaje recuperado.

   ```cs
      var fetched = await ewsClient.FetchItemAsync(messageUri, cancellationToken: cancellationToken);
   ```

## Agregando mensajes

El siguiente ejemplo de código intenta agregar mensajes de correo electrónico de forma asíncrona. El código realiza los siguientes pasos:

1. Llama al método [AppendMessagesAsync](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/appendmessagesasync/) del objeto [EWSclient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/). El método toma un objeto [EwsAppendMessage](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/) que contiene parámetros: los mensajes a agregar, la URI de la carpeta de destino y el token de cancelación.
2. Crea el objeto [EwsAppendMessage](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/) utilizando el método [Create](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/create/) y lo configura con las siguientes llamadas de método:

   - [AddMessage](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/addmessage/) agrega un mensaje a la operación de agregar.
   - [SetFolder](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/setfolder/) establece la URI de la carpeta de destino para la operación de agregar.
   - [SetCancellationToken](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/setcancellationtoken/) establece el token de cancelación que se puede utilizar para cancelar la operación asíncrona.

3. El método [AppendMessagesAsync](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/appendmessagesasync/) devuelve un objeto Task que se resuelve en un objeto IEnumerable<string> cuando la operación asíncrona se completa. La palabra clave "await" se usa para esperar que el objeto Task complete antes de continuar.
4. La variable `uris` se asigna al resultado de la tarea completada, que es un objeto IEnumerable<string> que contiene las URIs de los mensajes agregados.

```cs
IEnumerable<string> uris = await ewsClient.AppendMessagesAsync(
    EwsAppendMessage.Create()
        .AddMessage(message)
        .AddMessage(fetched)
        .SetFolder(folderUri)
        .SetCancellationToken(cancellationToken));
```

## Copiando elementos

El siguiente ejemplo de código muestra cómo copiar elementos y realiza los siguientes pasos:

1. Llama al método [CopyItemAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iasyncewsclient/copyitemasync/) del objeto [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/). El método toma tres parámetros: 

   - `messageUri` es una cadena que representa la URI del mensaje a copiar 
   - `destinationFolderUri` es una cadena que representa la URI de la carpeta de destino
   - `cancellationToken` es un parámetro opcional que se puede utilizar para cancelar la operación asíncrona. 

   El método devuelve un objeto Task que se resuelve en una cadena cuando la operación asíncrona se completa. La palabra clave "await" se usa para esperar que el objeto Task complete antes de continuar.

2. La variable `newItemUri` se asigna al resultado de la tarea completada, que es una cadena que contiene la URI de la copia recién creada del mensaje.

```cs
string newItemUri = await ewsClient.CopyItemAsync(messageUri, destinationFolderUri, cancellationToken);
```

## Eliminando elementos

El siguiente código intenta eliminar un mensaje de correo electrónico de forma asíncrona.

Llama al método [DeleteItemAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iasyncewsclient/deleteitemasync/) del objeto EWSClient. El método toma tres parámetros:

- `newItemUri` es una cadena que representa la URI del elemento a eliminar
- `DeletionOptions.DeletePermanently` especifica que el elemento debe eliminarse permanentemente
- `cancellationToken` es un parámetro opcional que se puede utilizar para cancelar la operación asíncrona. 

El método devuelve un objeto Task que se completa cuando la operación asíncrona se completa. La palabra clave "await" se usa para esperar que el objeto Task complete antes de continuar.

```cs
await ewsClient.DeleteItemAsync(newItemUri, DeletionOptions.DeletePermanently, cancellationToken);
```

## Eliminando carpetas

El siguiente código intenta eliminar una carpeta de forma asíncrona.

Llama al método [DeleteFolderAsync](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/deletefolderasync/) del objeto EWSClient. El método toma tres parámetros:

- `folderUri` es una cadena que representa la URI de la carpeta a eliminar
- `deletePermanently` especifica si se debe eliminar la carpeta permanentemente o moverla a la carpeta "Elementos Eliminados"
- `cancellationToken` es un parámetro opcional que se puede utilizar para cancelar la operación asíncrona. 

El método devuelve un objeto Task que se completa cuando la operación asíncrona se completa. La palabra clave "await" se usa para esperar que el objeto Task complete antes de continuar.

```cs
const bool deletePermanently = true;
await ewsClient.DeleteFolderAsync(folderUri, deletePermanently, cancellationToken);
```

## Actualizando elementos

El siguiente ejemplo de código intenta actualizar un elemento de forma asíncrona. Realiza los siguientes pasos:

1. Crea un objeto [EwsUpdateItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsupdateitem/) utilizando el método [Create](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsupdateitem/create/#create_2), pasando un objeto de elemento. El EwsUpdateItem representa los parámetros de la operación de actualización. Se llama al método [SetCancellationToken](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsappendmessage/setcancellationtoken/) en el objeto [EwsUpdateItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsupdateitem/), pasando el parámetro `cancellationToken`, que es un parámetro opcional que se puede usar para cancelar la operación asíncrona.
2. Pasa el objeto [EwsUpdateItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsupdateitem/) como un parámetro al método [UpdateItemAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iasyncewsclient/updateitemasync/) de un [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/).
3. El método [UpdateItemAsync](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iasyncewsclient/updateitemasync/) devuelve un objeto Task que se completa cuando la operación asíncrona se completa. La palabra clave "await" se usa para esperar que el objeto Task complete antes de continuar.

```cs
await ewsClient.UpdateItemAsync(
    EwsUpdateItem.Create(mapiNote)
        .SetCancellationToken(cancellationToken));
```