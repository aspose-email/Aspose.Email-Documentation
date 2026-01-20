---
title: Microsoft Graph Authentication with MSAL (Aspose.Email)
ArticleTitle: Microsoft Graph Authentication with MSAL
type: docs
weight: 20
url: /net/microsoft-graph-authentication-with-msal/
---


## **Introduction to Graph Authentication**

[Microsoft Graph](https://learn.microsoft.com/en-us/graph/overview) is a unified REST API for accessing data across Microsoft 365 services such as Outlook, OneDrive, and Teams. Aspose.Email for .NET provides a built-in [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/) interface that simplifies interaction with Microsoft Graph by offering a high-level, strongly-typed API.

Using [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/), you can authenticate via MSAL, then perform common operations such as:

- Managing mail folders (list, create, update, copy, delete)

- Working with messages and attachments (read, send, move, and manipulate content)

- Accessing and managing calendar events, contacts, categories, rules, tasks, and OneNote notebooks

The following examples demonstrate how to create and configure a [GraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/graphclient/) instance with an access token, followed by typical usage scenarios.



## **Authenticate Microsoft Graph with MSAL.NET**

To work with Microsoft Graph using Aspose.Email for .NET, you must first authenticate your application. It can be done by implementing the [ITokenProvider](https://reference.aspose.com/email/net/aspose.email.clients/itokenprovider/) interface, which supplies access tokens to the [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/).

This section guides you through setting up MSAL.NET to obtain tokens and initializing the [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/) to send authenticated requests to Microsoft Graph services.

[Microsoft Authentication Library (MSAL)](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet) 

### **Step 1: Define the AccessParameters Class**

Create a simple class to store your Microsoft 365 credentials and related configuration.

```csharp
public class AccessParameters
{
    public string TenantId { get; init; }
    public string ClientId { get; init; }
    public string ClientSecret { get; init; }
    public string UserId { get; init; }
    public Uri Authority => new ($"https://login.microsoftonline.com/{TenantId}");
    public string ApiUrl => "https://graph.microsoft.com/.default";
}
```

### **Step 2: Install the MSAL.NET Package**

Add the [Microsoft.Identity.Client](https://www.nuget.org/packages/Microsoft.Identity.Client) NuGet package to your project. It contains the Microsoft Authentication Library (MSAL) used to acquire access tokens.

```bash
dotnet add package Microsoft.Identity.Client
```

### **Step 3: Implement the ITokenProvider Interface**

Create a `GraphTokenProvider` class that implements the [ITokenProvider](https://reference.aspose.com/email/net/aspose.email.clients/itokenprovider/) interface. This class will use the MSAL.NET library to acquire an access token.

```csharp
using Microsoft.Identity.Client;
using Microsoft.Identity.Web;
using Aspose.Email.Clients;

public class GraphTokenProvider : ITokenProvider
{
    private readonly IConfidentialClientApplication _app;
    private readonly string[] _scopes;
    private string? _token;

    public GraphTokenProvider(AccessParameters accessParams)
    {
        _app = ConfidentialClientApplicationBuilder.Create(accessParams.ClientId)
            .WithClientSecret(accessParams.ClientSecret)
            .WithAuthority(accessParams.Authority)
            .Build();

        _app.AddInMemoryTokenCache();

        _scopes = new[] { accessParams.ApiUrl };
    }

    public void Dispose()
    {
        throw new NotImplementedException();
    }

    public OAuthToken GetAccessToken()
    {
        return GetAccessToken(false);
    }

    public OAuthToken GetAccessToken(bool ignoreExistingToken)
    {
        if (!ignoreExistingToken && _token != null)
        {
            return new OAuthToken(_token);
        }

        _token = GetAccessTokenAsync().GetAwaiter().GetResult();
        return new OAuthToken(_token);
    }

    private async Task<string?> GetAccessTokenAsync()
    {
        AuthenticationResult? result;

        try
        {
            result = await _app.AcquireTokenForClient(_scopes)
                .ExecuteAsync();

            Console.WriteLine("Token acquired");
        }
        catch (MsalServiceException ex) when (ex.Message.Contains("AADSTS70011"))
        {
            Console.WriteLine("Scope provided is not supported");
            result = null;
        }

        if (result == null) return null;
        _token = result.AccessToken;
        return result.AccessToken;
    }
```

### **Step 4: Create an ITokenProvider Instance**

Once your `GraphTokenProvider` class is ready, you can instantiate it using your app credentials.

```csharp
var accessParams = new AccessParameters()
{
    TenantId = "Your Tenant ID",
    ClientId = "Your Client ID",
    ClientSecret = "Your Client Secret",
    UserId = "User's Object ID"
};

var tokenProvider = new GraphTokenProvider(accessParams);
```

### **Step 5: Initialize the IGraphClient**

Use the token provider to create an authenticated [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/) instance. Set the resource type and ID to begin interacting with Microsoft Graph.

```csharp
using var client = GraphClient.GetClient(tokenProvider, accessParams.TenantId);

client.Resource = ResourceType.Users;
client.ResourceId = accessParams.UserId;
```

Your IGraphClient is now authenticated and ready to send requests to Microsoft Graph on behalf of your application.

## **Connect to GCC High Endpoint in Microsoft Graph**

Aspose.Email [GraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/) supports connecting to Microsoft Graph GCC High endpoint by setting the [EndPoint](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/endpoint/) property manually. Set the property to `https://graph.microsoft.us` before making requests.

The following code sample demonstrates how to configure the [GraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/) to connect to the GCC High endpoint for listing folders and retrieving messages.

```cs
client.EndPoint = "https://graph.microsoft.us";

var folders = client.ListFolders();
string folderId = folders.Find(x => x.DisplayName == "Inbox").ItemId;
var msgs = client.ListMessages(folderId);
```

## **Asynchronous Authentication to Microsoft Graph**

Use the `Aspose.Email.Clients.Graph.IGraphClientAsync` interface to perform asynchronous operations with [GraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/graphclient/). The `GraphClient.GetClientAsync(ITokenProvider, string)` and `GraphClient.GetClientAsync(IMultipleServicesTokenProvider, string)` methods allow you to initialize asynchronous Graph clients. The following code sample demonstrates how to configure an authenticated Microsoft Graph client with Azure AD application credentials so it can operate on a specific user's mailbox: 



```cs
var accessParameters = Settings.User1;

var provider = new AzureConfidentialTokenProvider(
    accessParameters.TenantId,
    accessParameters.ClientId,
    accessParameters.ClientSecret);

var client = GraphClient.GetClientAsync(provider, accessParameters.TenantId);

client.Resource = Aspose.Email.Clients.Graph.ResourceType.Users;
client.ResourceId = accessParameters.Username;
client.EndPoint = "https://graph.microsoft.com";
```