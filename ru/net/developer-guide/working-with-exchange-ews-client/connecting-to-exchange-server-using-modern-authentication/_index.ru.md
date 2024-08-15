---
title: "Подключение к серверу Exchange с использованием современной аутентификации"
url: /ru/net/connecting-to-exchange-server-using-modern-authentication/
weight: 5
type: docs
---

Современная аутентификация теперь включена по умолчанию для всех новых клиентов Microsoft 365/Azure, поскольку этот протокол более безопасен, чем устаревшая базовая аутентификация.
Современная аутентификация основана на библиотеке аутентификации Active Directory и OAuth 2.0. Она использует токены, ограниченные по времени, а приложения не хранят учетные данные пользователей.

## **Предварительные настройки**

Чтобы использовать современную аутентификацию, убедитесь, что она включена. Однако для арендаторов, созданных до 1 августа 2017 года, современная аутентификация по умолчанию отключена.
В [Центр администрирования Microsoft 365](https://admin.microsoft.com/), иди **Настройки > Организационные настройки > Современная аутентификация**. В **Современное всплывающее окно аутентификации** на экране появляется возможность определить протоколы, для которых больше не требуется обычная аутентификация.
Для новых клиентов Microsoft365 в Azure базовая аутентификация по умолчанию отключена для всех приложений. Поэтому текст будет отображаться в этом разделе.

> В вашей организации включены настройки безопасности по умолчанию, что означает, что требуется современная аутентификация в Exchange Online, а подключения к базовой аутентификации заблокированы. Вы должны отключить настройки безопасности по умолчанию на портале Azure, прежде чем изменять какие-либо настройки здесь.


Вы можете включить поддержку Basic Auth для арендатора из [Azure](https://aad.portal.azure.com/) портал, вперед **Azure Active Directory > Свойства > Управление настройками безопасности по умолчанию > Включить настройки безопасности по умолчанию > Нет**.
Для получения дополнительной информации см. [Статья в документации Microsoft](https://docs.microsoft.com/en-us/exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online).

## **Регистрация приложения в Azure Active Directory**

Необходимо выполнить регистрацию приложения в Azure Active Directory.
Существует два типа разрешений, которые можно использовать для доступа к почтовым ящикам с помощью приложения. Выберите определенный тип разрешения в зависимости от создаваемого приложения:

- Приложения, использующие **Делегированные разрешения** пригласите зарегистрированного пользователя. Другими словами, когда вы подключаетесь к сервису, появляется диалоговое окно с именем пользователя и паролем. Приложение никогда не может иметь больше привилегий, чем авторизованный пользователь.
- Приложения, использующие **Разрешения для приложений** запускается без присутствия зарегистрированного пользователя. Например, это приложения, которые работают в фоновом режиме или в качестве демонов. Только администратор может дать согласие на получение разрешений для приложений.

Кроме того, см. [Статья в документации Microsoft](https://docs.microsoft.com/en-us/exchange/client-developer/exchange-web-services/how-to-authenticate-an-ews-application-by-using-oauth) для получения дополнительной информации.

Процедура регистрации зависит от типа выбранного разрешения. Чтобы зарегистрировать приложение, обратитесь к [Статья в документации Microsoft](https://docs.microsoft.com/en-us/exchange/client-developer/exchange-web-services/how-to-authenticate-an-ews-application-by-using-oauth#register-your-application).

## **Используйте современную аутентификацию с EWSClient**

После регистрации приложения мы можем сосредоточиться на написании кода, который будет состоять из следующих частей:

 - Получите токен авторизации.
 - Используйте токен для аутентификации.

### Получение токена авторизации

Чтобы получить токен, мы будем использовать [Библиотека аутентификации Microsoft (MSAL) для .NET](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet).

Ниже приведены шаги для получения токена авторизации.

 - Добавьте [Пакет microsoft.Identity.Client nuget](https://www.nuget.org/packages/Microsoft.Identity.Client) который содержит двоичные файлы MSAL.NET.
 - Создайте класс AccessParameters для хранения учетных данных.
 - Создайте метод, принимающий параметры доступа и использующий MSAL.NET для получения токена доступа.

Следующие примеры кода будут зависеть от выбранного типа аутентификации.

**Получите токен с делегированной аутентификацией**

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
**Получите токен с помощью аутентификации приложения**

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

### Использование токена для аутентификации

После этого, когда мы успешно получим токен, давайте инициализируем [EwsClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/).

**Использование токена с делегированной аутентификацией**

```csharp
NetworkCredential credentials = new OAuthNetworkCredential(accessToken);

using var client = EWSClient.GetEWSClient("https://outlook.office365.com/EWS/Exchange.asmx", credentials);

```

{{% alert %}}
**Попробуйте!**
Запустите [EWSModernAuthenticationDelegated](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Sample%20Apps/EWSModernAuthenticationDelegated) простой проект приложения, подключитесь к Microsoft 365 с делегированной аутентификацией и прочтите свой почтовый ящик.
{{% /alert %}}

**Использование токена с аутентификацией приложения**

```csharp
// Use Microsoft365 username and access token
NetworkCredential credentials = new OAuthNetworkCredential(username, accessToken);

using var client = EWSClient.GetEWSClient("https://outlook.office365.com/EWS/Exchange.asmx", credentials);

```

{{% alert %}}
**Попробуйте!**
Запустите [EWSModernAuthenticationApp](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Sample%20Apps/EWSModernAuthenticationApp) простой проект приложения, подключитесь к Microsoft 365 с помощью аутентификации приложения и прочтите свой почтовый ящик.
{{% /alert %}}

## **Используйте современную аутентификацию с клиентами IMAP, POP или SMTP**

Доступ по протоколам IMAP, POP, SMTP через разрешения приложений не поддерживается. Другими словами, поддерживается только делегированная аутентификация.

Определена процедура регистрации приложения в Azure Active Directory [above](https://blog.aspose.com/email/connect-to-microsoft365-mailbox-using-modern-authentication-in-c-.net/#App-registration-with-Azure-Active-Directory).

### Используйте Центр администрирования Microsoft 365, чтобы включить или отключить IMAP, POP, SMTP AUTH в определенных почтовых ящиках

 - Откройте [Центр администрирования Microsoft 365](https://admin.microsoft.com/) и перейдите к **Пользователи > Активные пользователи**.
 - Выберите пользователя и в появившемся всплывающем окне нажмите **Mail**.
 - В **Приложения для электронной почты** раздел, нажмите **Управление почтовыми приложениями**.
 - Проверьте **IMAP, POP, аутентифицированный SMTP** настройка: не отмечена = выключена, отмечена = включена.
 - Click **Сохранить изменения**.

### Добавление кода для получения токена аутентификации с сервера токенов

Обязательно укажите полные области, включая URL-адреса ресурсов Outlook.

IMAP: https://outlook.office.com/IMAP.AccessAsUser.All
ПОП-МУЗЫКА: https://outlook.office.com/POP.AccessAsUser.All
SMTP: https://outlook.office.com/SMTP.Send

Чтобы получить токен, мы будем использовать [Библиотека аутентификации Microsoft (MSAL) для .NET](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet).

Ниже приведены шаги для получения токена авторизации.

- Добавьте [Пакет microsoft.Identity.Client nuget](https://www.nuget.org/packages/Microsoft.Identity.Client) который содержит двоичные файлы MSAL.NET.
- Создайте класс AccessParameters для хранения учетных данных.
- Создайте метод, принимающий параметры доступа и использующий MSAL.NET для получения токена доступа.

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

### Использование токена для аутентификации

После этого, когда мы успешно получим токен, давайте инициализируем [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/).

```csharp
var imapClient = new ImapClient(
    "outlook.office365.com",
    993,
    username,
    accessToken,
    true);

```
Аналогичным образом, [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) инициализация будет выглядеть следующим образом.

```csharp
var smtpClient = new SmtpClient(
    "smtp.office365.com",
    587,
    username,
    accessToken,
    true);

```

{{% alert %}}
**Попробуйте!**
Запустите [EWSModernAuthenticationImapSmtp](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Sample%20Apps/EWSModernAuthenticationImapSmtp) простой проект приложения, подключитесь к Microsoft 365 через IMAP и SMTP и прочтите свой почтовый ящик.
{{% /alert %}}

## **Верните идентификатор запроса клиента**

 The [ReturnClientRequestId](https://reference.aspose.com/email/net/aspose.email.clients.exchange/autodiscoverservicebase/returnclientrequestid/) Для вашего удобства в EWSClient было добавлено свойство, позволяющее указать, следует ли возвращать идентификатор запроса клиента в ответе на вызовы Exchange Web Services (EWS). Идентификатор запроса клиента — это уникальный идентификатор, который можно задать для каждого запроса EWS, отправляемого из приложения. Настроив [ReturnClientRequestId](https://reference.aspose.com/email/net/aspose.email.clients.exchange/autodiscoverservicebase/returnclientrequestid/) недвижимость для *true*, вы указываете, что хотите включить идентификатор запроса клиента в ответ сервера EWS. Это может быть полезно для отслеживания и сопоставления запросов и ответов в сценариях, где несколько запросов подаются и обрабатываются асинхронно.

 В следующем фрагменте кода показано, как можно использовать это свойство:

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
