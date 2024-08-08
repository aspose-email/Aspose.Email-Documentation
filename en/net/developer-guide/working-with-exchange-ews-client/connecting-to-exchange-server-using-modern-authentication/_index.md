---
title: Connecting to Exchange Server using Modern Authentication
type: docs
weight: 5
url: /net/connecting-to-exchange-server-using-modern-authentication/
---

Modern Authentication is now enabled by default for all new Microsoft 365/Azure tenants because this protocol is more secure than the deprecated Basic Authentication.
Modern Authentication is based on Active Directory Authentication Library and OAuth 2.0. It uses time-limited tokens, and applications don’t store user credentials.

## **Prerequisite settings**

To use Modern Authentication, make sure that it is enabled. However, for tenants created before August 1, 2017, modern authentication is turned off by default.
In the [Microsoft 365 admin center](https://admin.microsoft.com/), go **Settings > Org Settings > Modern Authentication**. In the **Modern authentication flyout** that appears, you can identify the protocols that no longer require Basic authentication.
For new Microsoft365 tenants in Azure, Basic Authentication is disabled by default for all applications. Therefore, the text will be displayed in this section.

> Your organization has security defaults enabled, which means modern authentication to Exchange Online is required, and basic authentication connections are blocked.
> You must turn off security defaults in the Azure portal before you can change any settings here.


You can enable Basic Auth support for tenant from the [Azure](https://aad.portal.azure.com/) portal, go **Azure Active Directory > Properties > Manage Security defaults > Enable Security defaults > No**.
For more information, see the [Microsoft Documentation Article](https://docs.microsoft.com/en-us/exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online).

## **App registration with Azure Active Directory**

It is necessary to perform app registration with Azure Active Directory.
There are two types of permissions that can be used to access mailboxes with your app. Choose a specific type of permission, depending on the app you are creating:

- Apps that use **Delegated permissions** have a signed-in user present. In other words, when you connect to the service, a dialog window appears for a username and a password. App can never have more privileges than a signed-in user.
- Apps that use **Application permissions** run without a signed-in user present. For instance, these are apps that run as background services or daemons. Only an administrator can consent to application permissions.

In addition, refer to the [Microsoft Documentation Article](https://docs.microsoft.com/en-us/exchange/client-developer/exchange-web-services/how-to-authenticate-an-ews-application-by-using-oauth) for more information.

The registration procedure depends on the type of permission selected. To register your app, refer to the [Microsoft Documentation Article](https://docs.microsoft.com/en-us/exchange/client-developer/exchange-web-services/how-to-authenticate-an-ews-application-by-using-oauth#register-your-application).

## **Use modern authentication with EwsClient**

After registering the application, we can focus on writing the code, which will consist of the following parts:

 - Get the authorization token.
 - Use the token to authenticate.

### Getting the authorization token

To get the token we’ll use [Microsoft Authentication Library (MSAL) for .NET](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet).

The following are the steps to get authorization token.

 - Add the [Microsoft.Identity.Client nuget package](https://www.nuget.org/packages/Microsoft.Identity.Client) that contains the binaries of the MSAL.NET.
 - Create an AccessParameters class to store credentials.
 - Create a method accepting access parameters and using MSAL.NET to get an access token.

The following code samples will depend on the type of auth chosen.

**Get a token with delegated auth**

```csharp
public class AccessParameters
{
    public string TenantId { get; set; }
    public string ClientId { get; set; }
    public string RedirectUri { get; set; } = "http://localhost";
    public string[] Scopes { get; set; } = { "https://outlook.office365.com/EWS.AccessAsUser.All" };
}

public static async Task<string> GetAccessToken(AccessParameters accessParameters)
{
    var pca = PublicClientApplicationBuilder
                            .Create(accessParameters.ClientId)
                            .WithTenantId(accessParameters.TenantId)
                            .WithRedirectUri(ccessParameters.RedirectUri)
                            .Build();

    var result = await pca.AcquireTokenInteractive(accessParameters.Scopes)
        .WithUseEmbeddedWebView(false)
        .ExecuteAsync();

    return result.AccessToken;
}

```
**Get a token with app auth**

```csharp
public class AccessParameters
{
    public string TenantId { get; set; }
    public string ClientId { get; set; }
    public string ClientSecret { get; set; }
    public string[] Scopes { get; set; } = { "https://outlook.office365.com/.default" };
}

public static async Task<string> GetAccessToken(AccessParameters accessParameters)
{
    var cca = ConfidentialClientApplicationBuilder
        .Create(accessParameters.ClientId)
        .WithClientSecret(accessParameters.ClientSecret)
        .WithTenantId(accessParameters.TenantId)
        .Build();

    var result = await cca.AcquireTokenForClient(accessParameters.Scopes).ExecuteAsync();

    return result.AccessToken;
}

```

### Using the token to authenticate

After that, when we have successfully obtained a token, let’s initialize the [EwsClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/).

**Using the token with delegated auth**

```csharp
NetworkCredential credentials = new OAuthNetworkCredential(accessToken);

using var client = EWSClient.GetEWSClient("https://outlook.office365.com/EWS/Exchange.asmx", credentials);

```

{{% alert %}}
**Try it out!**
Run the [EWSModernAuthenticationDelegated](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Sample%20Apps/EWSModernAuthenticationDelegated) simple app project, Connect to Microsoft 365 with delegated auth, and read your Inbox.
{{% /alert %}}

**Using the token with app auth**

```csharp
// Use Microsoft365 username and access token
NetworkCredential credentials = new OAuthNetworkCredential(username, accessToken);

using var client = EWSClient.GetEWSClient("https://outlook.office365.com/EWS/Exchange.asmx", credentials);

```

{{% alert %}}
**Try it out!**
Run the [EWSModernAuthenticationApp](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Sample%20Apps/EWSModernAuthenticationApp) simple app project, connect to Microsoft 365 with app auth, and read your Inbox.
{{% /alert %}}

## **Use Modern Authentication with IMAP, POP or SMTP Clients**

IMAP, POP, SMTP access via application permissions isn’t supported. In other words, delegated authentication only supported.

The App registration with Azure Active Directory procedure is defined [above](https://blog.aspose.com/email/connect-to-microsoft365-mailbox-using-modern-authentication-in-c-.net/#App-registration-with-Azure-Active-Directory).

### Use the Microsoft 365 admin center to enable or disable IMAP, POP, SMTP AUTH on specific mailboxes

 - Open the [Microsoft 365 admin center](https://admin.microsoft.com/) and go to **Users > Active users**.
 - Select the user, and in the flyout that appears, click **Mail**.
 - In the **Email apps** section, click **Manage email apps**.
 - Verify the **IMAP, POP, Authenticated SMTP** setting: unchecked = disabled, checked = enabled.
 - Click **Save changes**.

### Adding code to get an authentication token from a token server

Make sure to specify the full scopes, including Outlook resource URLs.

IMAP: https://outlook.office.com/IMAP.AccessAsUser.All
POP: https://outlook.office.com/POP.AccessAsUser.All
SMTP: https://outlook.office.com/SMTP.Send

To get the token we’ll use [Microsoft Authentication Library (MSAL) for .NET](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet).

The following are the steps to get authorization token.

- Add the [Microsoft.Identity.Client nuget package](https://www.nuget.org/packages/Microsoft.Identity.Client) that contains the binaries of the MSAL.NET.
- Create an AccessParameters class to store credentials.
- Create a method accepting access parameters and using MSAL.NET to get an access token.

```csharp
public class AccessParameters
{
    public string TenantId { get; set; }
    public string ClientId { get; set; }
    public string RedirectUri { get; set; } = "http://localhost";
    public string[] Scopes { get; set; } = { 
        "https://outlook.office.com/IMAP.AccessAsUser.All", 
        "https://outlook.office.com/SMTP.Send" };
}

public static async Task<string> GetAccessToken(AccessParameters accessParameters)
{
    var pca = PublicClientApplicationBuilder
                            .Create(accessParameters.ClientId)
                            .WithTenantId(accessParameters.TenantId)
                            .WithRedirectUri(ccessParameters.RedirectUri)
                            .Build();

    var result = await pca.AcquireTokenInteractive(accessParameters.Scopes)
        .WithUseEmbeddedWebView(false)
        .ExecuteAsync();

    return result.AccessToken;
}

```

### Using the token to authenticate

After that, when we have successfully obtained a token, let’s initialize the [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/).

```csharp
var imapClient = new ImapClient(
    "outlook.office365.com", 
    993, 
    username, 
    accessToken, 
    true);

```
Similarly, the [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) initialization will look as following.

```csharp
var smtpClient = new SmtpClient(
    "smtp.office365.com",
    587, 
    username,
    accessToken, 
    true);

```

{{% alert %}}
**Try it out!**
Run the [EWSModernAuthenticationImapSmtp](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Sample%20Apps/EWSModernAuthenticationImapSmtp) simple app project, connect to Microsoft 365 via IMAP and SMTP, and read your Inbox.
{{% /alert %}}

## **Return the Client Request ID**

 The [ReturnClientRequestId](https://reference.aspose.com/email/net/aspose.email.clients.exchange/autodiscoverservicebase/returnclientrequestid/) property was added to EWSClient for your convenience to specify whether the client request ID should be returned in the response from Exchange Web Services (EWS) calls. The client request ID is a unique identifier that you can set for each EWS request sent from your application. By setting the [ReturnClientRequestId](https://reference.aspose.com/email/net/aspose.email.clients.exchange/autodiscoverservicebase/returnclientrequestid/) property to *true*, you indicate that you want the client request ID to be included in the response from the EWS server. This can be useful for tracking and correlating requests and responses in scenarios where multiple requests are made and processed asynchronously.

 The following code snippet shows how the property can be utilized:

 ```cs
 using (IEWSClient client = TestUtil.CreateEWSClient(user))
{
    // Client will create random id and pass it to the server.
	// The server should include this id in request-id header of all responses.
    client.ReturnClientRequestId = true;
    
	client.LogFileName = "ews.log";
    client.GetMailboxInfo();
}
 ```