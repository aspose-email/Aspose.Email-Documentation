---
title: "Conectarse a Exchange Server utilizando Autenticación Moderna"
url: /es/net/conectarse-a-exchange-server-utilizando-autenticacion-moderna/
weight: 5
type: docs
---

La Autenticación Moderna ahora está habilitada de forma predeterminada para todos los nuevos inquilinos de Microsoft 365/Azure porque este protocolo es más seguro que la Autenticación Básica, que está en desuso.
La Autenticación Moderna se basa en la Biblioteca de Autenticación de Active Directory y OAuth 2.0. Utiliza tokens con tiempo limitado, y las aplicaciones no almacenan las credenciales del usuario.

## **Configuraciones Previas**

Para usar la Autenticación Moderna, asegúrate de que esté habilitada. Sin embargo, para los inquilinos creados antes del 1 de agosto de 2017, la autenticación moderna está desactivada de forma predeterminada.
En el [centro de administración de Microsoft 365](https://admin.microsoft.com/), ve a **Configuraciones > Configuraciones de la organización > Autenticación moderna**. En el **desplegable de autenticación moderna** que aparece, puedes identificar los protocolos que ya no requieren autenticación básica.
Para los nuevos inquilinos de Microsoft365 en Azure, la Autenticación Básica está deshabilitada de forma predeterminada para todas las aplicaciones. Por lo tanto, el texto se mostrará en esta sección.

> Su organización tiene habilitados los valores predeterminados de seguridad, lo que significa que se requiere la autenticación moderna para Exchange Online, y las conexiones de autenticación básica están bloqueadas. Debe desactivar los valores predeterminados de seguridad en el portal de Azure antes de poder cambiar cualquier configuración aquí.

Puedes habilitar el soporte de Autenticación Básica para el inquilino desde el portal de [Azure](https://aad.portal.azure.com/), ve a **Azure Active Directory > Propiedades > Administrar valores predeterminados de seguridad > Habilitar valores predeterminados de seguridad > No**.
Para más información, consulta el [Artículo de Documentación de Microsoft](https://docs.microsoft.com/en-us/exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online).

## **Registro de Aplicaciones con Azure Active Directory**

Es necesario realizar el registro de la aplicación con Azure Active Directory.
Existen dos tipos de permisos que se pueden usar para acceder a los buzones con tu aplicación. Elige un tipo específico de permiso, dependiendo de la aplicación que estés creando:

- Las aplicaciones que usan **permisos delegados** tienen un usuario conectado presente. En otras palabras, cuando te conectas al servicio, aparece una ventana de diálogo para un nombre de usuario y una contraseña. La aplicación nunca puede tener más privilegios que el usuario conectado.
- Las aplicaciones que utilizan **permisos de aplicación** funcionan sin un usuario conectado presente. Por ejemplo, estas son aplicaciones que se ejecutan como servicios en segundo plano o demonios. Solo un administrador puede consentir permisos de aplicación.

Además, consulta el [Artículo de Documentación de Microsoft](https://docs.microsoft.com/en-us/exchange/client-developer/exchange-web-services/how-to-authenticate-an-ews-application-by-using-oauth) para más información.

El procedimiento de registro depende del tipo de permiso seleccionado. Para registrar tu aplicación, consulta el [Artículo de Documentación de Microsoft](https://docs.microsoft.com/en-us/exchange/client-developer/exchange-web-services/how-to-authenticate-an-ews-application-by-using-oauth#register-your-application).

## **Usar Autenticación Moderna con EwsClient**

Después de registrar la aplicación, podemos centrarnos en escribir el código, que constará de las siguientes partes:

 - Obtener el token de autorización.
 - Usar el token para autenticar.

### Obtener el Token de Autorización

Para obtener el token, usaremos [Microsoft Authentication Library (MSAL) para .NET](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet).

Los siguientes son los pasos para obtener el token de autorización.

 - Agrega el [paquete nuget Microsoft.Identity.Client](https://www.nuget.org/packages/Microsoft.Identity.Client) que contiene los binarios de MSAL.NET.
 - Crea una clase AccessParameters para almacenar las credenciales.
 - Crea un método que acepte parámetros de acceso y use MSAL.NET para obtener un token de acceso.

Los siguientes ejemplos de código dependerán del tipo de autenticación elegida.

**Obtener un token con autenticación delegada**

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
                            .WithRedirectUri(accessParameters.RedirectUri)
                            .Build();

    var result = await pca.AcquireTokenInteractive(accessParameters.Scopes)
        .WithUseEmbeddedWebView(false)
        .ExecuteAsync();

    return result.AccessToken;
}

```
**Obtener un token con autenticación de aplicación**

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

### Usar el Token para Autenticar

Después de eso, cuando hayamos obtenido exitosamente un token, inicialicemos el [EwsClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/).

**Usar el token con autenticación delegada**

```csharp
NetworkCredential credentials = new OAuthNetworkCredential(accessToken);

using var client = EWSClient.GetEWSClient("https://outlook.office365.com/EWS/Exchange.asmx", credentials);

```

{{% alert %}}
**¡Pruébalo!**
Ejecuta el proyecto simple [EWSModernAuthenticationDelegated](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Sample%20Apps/EWSModernAuthenticationDelegated), Conéctate a Microsoft 365 con autenticación delegada y lee tu Bandeja de entrada.
{{% /alert %}}

**Usar el token con autenticación de aplicación**

```csharp
// Usa el nombre de usuario de Microsoft365 y el token de acceso
NetworkCredential credentials = new OAuthNetworkCredential(username, accessToken);

using var client = EWSClient.GetEWSClient("https://outlook.office365.com/EWS/Exchange.asmx", credentials);

```

{{% alert %}}
**¡Pruébalo!**
Ejecuta el proyecto simple [EWSModernAuthenticationApp](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Sample%20Apps/EWSModernAuthenticationApp), conéctate a Microsoft 365 con autenticación de aplicación y lee tu Bandeja de entrada.
{{% /alert %}}

## **Usar Autenticación Moderna con Clientes IMAP, POP o SMTP**

El acceso IMAP, POP, SMTP a través de permisos de aplicación no está soportado. En otras palabras, sólo se admite la autenticación delegada.

El procedimiento de registro de aplicaciones con Azure Active Directory está definido [arriba](https://blog.aspose.com/email/connect-to-microsoft365-mailbox-using-modern-authentication-in-c-.net/#App-registration-with-Azure-Active-Directory).

### Usar el centro de administración de Microsoft 365 para habilitar o deshabilitar IMAP, POP, SMTP AUTH en buzones específicos

 - Abre el [centro de administración de Microsoft 365](https://admin.microsoft.com/) y ve a **Usuarios > Usuarios Activos**.
 - Selecciona el usuario y en el desplegable que aparece, haz clic en **Correo**.
 - En la sección **Aplicaciones de correo**, haz clic en **Administrar aplicaciones de correo**.
 - Verifica la configuración de **IMAP, POP, SMTP autenticado**: desmarcado = deshabilitado, marcado = habilitado.
 - Haz clic en **Guardar cambios**.

### Agregar código para obtener un token de autenticación de un servidor de tokens

Asegúrate de especificar los alcances completos, incluyendo las URL de recursos de Outlook.

IMAP: https://outlook.office.com/IMAP.AccessAsUser.All  
POP: https://outlook.office.com/POP.AccessAsUser.All  
SMTP: https://outlook.office.com/SMTP.Send

Para obtener el token usaremos [Microsoft Authentication Library (MSAL) para .NET](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet).

Los siguientes son los pasos para obtener el token de autorización.

- Agrega el [paquete nuget Microsoft.Identity.Client](https://www.nuget.org/packages/Microsoft.Identity.Client) que contiene los binarios de MSAL.NET.
- Crea una clase AccessParameters para almacenar las credenciales.
- Crea un método que acepte parámetros de acceso y use MSAL.NET para obtener un token de acceso.

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
                            .WithRedirectUri(accessParameters.RedirectUri)
                            .Build();

    var result = await pca.AcquireTokenInteractive(accessParameters.Scopes)
        .WithUseEmbeddedWebView(false)
        .ExecuteAsync();

    return result.AccessToken;
}

```

### Usar el Token para Autenticar

Después de eso, cuando hayamos obtenido exitosamente un token, inicialicemos el [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/).

```csharp
var imapClient = new ImapClient(
    "outlook.office365.com", 
    993, 
    username, 
    accessToken, 
    true);

```
De forma similar, la inicialización del [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) será la siguiente.

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
Ejecuta el proyecto simple [EWSModernAuthenticationImapSmtp](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Sample%20Apps/EWSModernAuthenticationImapSmtp), conéctate a Microsoft 365 a través de IMAP y SMTP, y lee tu Bandeja de entrada.
{{% /alert %}}

## **Devolver el ID de Solicitud del Cliente**

La propiedad [ReturnClientRequestId](https://reference.aspose.com/email/net/aspose.email.clients.exchange/autodiscoverservicebase/returnclientrequestid/) fue añadida a EWSClient para tu conveniencia para especificar si el ID de solicitud del cliente debe ser devuelto en la respuesta de las llamadas a Exchange Web Services (EWS). El ID de solicitud del cliente es un identificador único que puedes establecer para cada solicitud EWS enviada desde tu aplicación. Al establecer la propiedad [ReturnClientRequestId](https://reference.aspose.com/email/net/aspose.email.clients.exchange/autodiscoverservicebase/returnclientrequestid/) en *true*, indicas que quieres que el ID de solicitud del cliente se incluya en la respuesta del servidor EWS. Esto puede ser útil para rastrear y correlacionar solicitudes y respuestas en escenarios donde se realizan y procesan múltiples solicitudes de manera asíncrona.

El siguiente fragmento de código muestra cómo se puede utilizar la propiedad:

```cs
using (IEWSClient client = TestUtil.CreateEWSClient(user))
{
    // El cliente creará un ID aleatorio y lo pasará al servidor.
    // El servidor debería incluir este ID en el encabezado request-id de todas las respuestas.
    client.ReturnClientRequestId = true;
    
    client.LogFileName = "ews.log";
    client.GetMailboxInfo();
}
```