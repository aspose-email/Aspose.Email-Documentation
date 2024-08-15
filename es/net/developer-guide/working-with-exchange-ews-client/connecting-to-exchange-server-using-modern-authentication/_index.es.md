---
title: "Conexión a Exchange Server mediante autenticación moderna"
url: /es/net/connecting-to-exchange-server-using-modern-authentication/
weight: 5
type: docs
---

La autenticación moderna ahora está habilitada de forma predeterminada para todos los nuevos inquilinos de Microsoft 365/Azure porque este protocolo es más seguro que la autenticación básica obsoleta.
La autenticación moderna se basa en la biblioteca de autenticación de Active Directory y en OAuth 2.0. Utiliza tokens de tiempo limitado y las aplicaciones no almacenan las credenciales de usuario.

## **Ajustes de requisitos previos**

Para usar la autenticación moderna, asegúrese de que esté habilitada. Sin embargo, para los arrendatarios creados antes del 1 de agosto de 2017, la autenticación moderna está desactivada de forma predeterminada.
En el [Centro de administración de Microsoft 365](https://admin.microsoft.com/), vaya **Configuración > Configuración de la organización > Autenticación moderna**. En el **Flecha desplegable de autenticación moderna** cuando aparezca, puede identificar los protocolos que ya no requieren autenticación básica.
Para los nuevos usuarios de Microsoft 365 en Azure, la autenticación básica está deshabilitada de forma predeterminada en todas las aplicaciones. Por lo tanto, el texto se mostrará en esta sección.

> Su organización tiene habilitados los valores predeterminados de seguridad, lo que significa que se requiere una autenticación moderna en Exchange Online y que las conexiones de autenticación básica están bloqueadas. Debe desactivar los valores predeterminados de seguridad en el portal de Azure antes de poder cambiar cualquier configuración aquí.


Puede habilitar la compatibilidad con la autenticación básica para el inquilino desde [Azure](https://aad.portal.azure.com/) portal, vaya **Azure Active Directory > Propiedades > Administrar los valores predeterminados de seguridad > Habilitar los valores predeterminados de seguridad > No**.
Para obtener más información, consulte el [Artículo de documentación de Microsoft](https://docs.microsoft.com/en-us/exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online).

## **Registro de aplicaciones con Azure Active Directory**

Es necesario realizar el registro de la aplicación con Azure Active Directory.
Hay dos tipos de permisos que se pueden usar para acceder a los buzones con la aplicación. Elige un tipo de permiso específico, según la aplicación que estés creando:

- Aplicaciones que usan **Permisos delegados** tener presente un usuario que haya iniciado sesión. En otras palabras, cuando se conecta al servicio, aparece una ventana de diálogo con un nombre de usuario y una contraseña. La aplicación nunca puede tener más privilegios que los de un usuario que ha iniciado sesión.
- Aplicaciones que usan **Permisos de aplicación** se ejecuta sin la presencia de un usuario que haya iniciado sesión. Por ejemplo, se trata de aplicaciones que se ejecutan como servicios o demonios en segundo plano. Solo un administrador puede dar su consentimiento a los permisos de la aplicación.

Además, consulte la [Artículo de documentación de Microsoft](https://docs.microsoft.com/en-us/exchange/client-developer/exchange-web-services/how-to-authenticate-an-ews-application-by-using-oauth) para obtener más información.

El procedimiento de registro depende del tipo de permiso seleccionado. Para registrar su aplicación, consulte la [Artículo de documentación de Microsoft](https://docs.microsoft.com/en-us/exchange/client-developer/exchange-web-services/how-to-authenticate-an-ews-application-by-using-oauth#register-your-application).

## **Utilice la autenticación moderna con EWSClient**

Tras registrar la aplicación, podemos centrarnos en escribir el código, que constará de las siguientes partes:

 - Obtenga el token de autorización.
 - Usa el token para autenticarte.

### Obtener el token de autorización

Para obtener el token usaremos [Biblioteca de autenticación de Microsoft (MSAL) para.NET](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet).

Los siguientes son los pasos para obtener el token de autorización.

 - Añada el [Paquete nuget Microsoft.Identity.Client](https://www.nuget.org/packages/Microsoft.Identity.Client) que contiene los archivos binarios de MSAL.NET.
 - Cree una clase AccessParameters para almacenar las credenciales.
 - Cree un método que acepte los parámetros de acceso y utilice MSAL.NET para obtener un token de acceso.

Los siguientes ejemplos de código dependerán del tipo de autenticación elegido.

**Obtenga un token con autenticación delegada**

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
**Obtenga un token con la autenticación de la aplicación**

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

### Uso del token para autenticarse

Después de eso, cuando hayamos obtenido con éxito un token, inicialicemos el [EwsClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/).

**Uso del token con autenticación delegada**

```csharp
NetworkCredential credentials = new OAuthNetworkCredential(accessToken);

using var client = EWSClient.GetEWSClient("https://outlook.office365.com/EWS/Exchange.asmx", credentials);

```

{{% alert %}}
**¡Pruébalo!**
Ejecute el [EWSModernAuthenticationDelegated](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Sample%20Apps/EWSModernAuthenticationDelegated) proyecto de aplicación simple, conéctese a Microsoft 365 con autenticación delegada y lea su bandeja de entrada.
{{% /alert %}}

**Uso del token con la autenticación de la aplicación**

```csharp
// Use Microsoft365 username and access token
NetworkCredential credentials = new OAuthNetworkCredential(username, accessToken);

using var client = EWSClient.GetEWSClient("https://outlook.office365.com/EWS/Exchange.asmx", credentials);

```

{{% alert %}}
**¡Pruébalo!**
Ejecute el [EWSModernAuthenticationApp](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Sample%20Apps/EWSModernAuthenticationApp) proyecto de aplicación simple, conéctese a Microsoft 365 con la autenticación de aplicaciones y lea su bandeja de entrada.
{{% /alert %}}

## **Utilice la autenticación moderna con clientes IMAP, POP o SMTP**

No se admite el acceso IMAP, POP ni SMTP mediante permisos de aplicaciones. En otras palabras, solo se admite la autenticación delegada.

El procedimiento de registro de la aplicación con Azure Active Directory está definido [above](https://blog.aspose.com/email/connect-to-microsoft365-mailbox-using-modern-authentication-in-c-.net/#App-registration-with-Azure-Active-Directory).

### Use el centro de administración de Microsoft 365 para habilitar o deshabilitar IMAP, POP y SMTP AUTH en buzones específicos

 - Abra el [Centro de administración de Microsoft 365](https://admin.microsoft.com/) y vaya a **Usuarios > Usuarios activos**.
 - Seleccione el usuario y, en el menú desplegable que aparece, haga clic en **Mail**.
 - En el **Aplicaciones de correo electrónico** sección, haga clic **Administrar aplicaciones de correo electrónico**.
 - Verifique el **IMAP, POP, SMTP autenticado** configuración: desmarcada = deshabilitada, marcada = habilitada.
 - Click **Guardar cambios**.

### Agregar código para obtener un token de autenticación de un servidor de tokens

Asegúrese de especificar los ámbitos completos, incluidas las URL de los recursos de Outlook.

IMAP: https://outlook.office.com/IMAP.AccessAsUser.All
POP: https://outlook.office.com/POP.AccessAsUser.All
SMTP: https://outlook.office.com/SMTP.Send

Para obtener el token usaremos [Biblioteca de autenticación de Microsoft (MSAL) para.NET](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet).

Los siguientes son los pasos para obtener el token de autorización.

- Añada el [Paquete nuget Microsoft.Identity.Client](https://www.nuget.org/packages/Microsoft.Identity.Client) que contiene los archivos binarios de MSAL.NET.
- Cree una clase AccessParameters para almacenar las credenciales.
- Cree un método que acepte los parámetros de acceso y utilice MSAL.NET para obtener un token de acceso.

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

### Uso del token para autenticarse

Después de eso, cuando hayamos obtenido con éxito un token, inicialicemos el [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/).

```csharp
var imapClient = new ImapClient(
    "outlook.office365.com",
    993,
    username,
    accessToken,
    true);

```
Del mismo modo, el [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) la inicialización tendrá el siguiente aspecto.

```csharp
var smtpClient = new SmtpClient(
    "smtp.office365.com",
    587,
    username,
    accessToken,
    true);

```

{{% alert %}}
**¡Pruébalo!**
Ejecute el [EWSModernAuthenticationImapSmtp](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Sample%20Apps/EWSModernAuthenticationImapSmtp) proyecto de aplicación simple, conéctese a Microsoft 365 a través de IMAP y SMTP y lea su bandeja de entrada.
{{% /alert %}}

## **Devolver el ID de solicitud del cliente**

 The [ReturnClientRequestId](https://reference.aspose.com/email/net/aspose.email.clients.exchange/autodiscoverservicebase/returnclientrequestid/) La propiedad se agregó a EWSClient para que pueda especificar si el ID de solicitud del cliente debe devolverse en la respuesta de las llamadas de Exchange Web Services (EWS). El identificador de solicitud del cliente es un identificador único que puede establecer para cada solicitud de EWS enviada desde su aplicación. Al configurar el [ReturnClientRequestId](https://reference.aspose.com/email/net/aspose.email.clients.exchange/autodiscoverservicebase/returnclientrequestid/) propiedad a *true*, indica que desea que el identificador de solicitud del cliente se incluya en la respuesta del servidor EWS. Esto puede resultar útil para rastrear y correlacionar las solicitudes y respuestas en situaciones en las que se realizan y procesan varias solicitudes de forma asincrónica.

 El siguiente fragmento de código muestra cómo se puede utilizar la propiedad:

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
