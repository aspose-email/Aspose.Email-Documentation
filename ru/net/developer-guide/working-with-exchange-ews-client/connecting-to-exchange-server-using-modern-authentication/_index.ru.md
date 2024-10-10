---
title: "Подключение к Exchange Server с использованием современного способа аутентификации"
url: /ru/net/connecting-to-exchange-server-using-modern-authentication/
weight: 5
type: docs
---

Современный способ аутентификации теперь включен по умолчанию для всех новых арендаторов Microsoft 365/Azure, поскольку этот протокол более безопасен, чем устаревший базовый способ аутентификации. Современный способ аутентификации основан на библиотеке аутентификации Active Directory и OAuth 2.0. Он использует временные токены, и приложения не хранят учетные данные пользователей.

## **Предварительные настройки**

Чтобы использовать современный способ аутентификации, убедитесь, что он включен. Однако для арендаторов, созданных до 1 августа 2017 года, современный способ аутентификации по умолчанию отключен. В [центре администрирования Microsoft 365](https://admin.microsoft.com/) перейдите в раздел **Настройки > Настройки организации > Современная аутентификация**. В появившемся **всплывающем окне современного способа аутентификации** вы можете определить протоколы, которые больше не требуют базового способа аутентификации. Для новых арендаторов Microsoft 365 в Azure базовый способ аутентификации по умолчанию отключен для всех приложений. Поэтому текст будет отображаться в этом разделе.

> В вашей организации включены системные настройки безопасности, что требует использования современного способа аутентификации для Exchange Online, а подключения по базовому способу аутентификации заблокированы. Вам необходимо отключить системные настройки безопасности в портале Azure, прежде чем вы сможете изменить настройки здесь.

Вы можете включить поддержку базовой аутентификации для арендатора в портале [Azure](https://aad.portal.azure.com/), перейдя в **Azure Active Directory > Свойства > Управление системными настройками безопасности > Включить системные настройки безопасности > Нет**. Для получения дополнительной информации смотрите [статью документации Microsoft](https://docs.microsoft.com/en-us/exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online).

## **Регистрация приложения в Azure Active Directory**

Необходимо провести регистрацию приложения в Azure Active Directory. Существует два типа разрешений, которые можно использовать для доступа к почтовым ящикам с помощью вашего приложения. Выберите конкретный тип разрешения в зависимости от того, какое приложение вы создаете:

- Приложения, использующие **делегированные разрешения**, имеют авторизованного пользователя. Иными словами, когда вы подключаетесь к службе, появляется диалоговое окно для ввода имени пользователя и пароля. У приложения никогда не может быть больше привилегий, чем у авторизованного пользователя.
- Приложения, использующие **разрешения приложения**, работают без присутствия авторизованного пользователя. Например, это приложения, работающие в качестве фоновых служб или демонов. Только администратор может согласиться на разрешения приложения.

Кроме того, обратитесь к [статье документации Microsoft](https://docs.microsoft.com/en-us/exchange/client-developer/exchange-web-services/how-to-authenticate-an-ews-application-by-using-oauth) для получения дополнительной информации.

Процедура регистрации зависит от выбранного типа разрешения. Чтобы зарегистрировать ваше приложение, обратитесь к [статье документации Microsoft](https://docs.microsoft.com/en-us/exchange/client-developer/exchange-web-services/how-to-authenticate-an-ews-application-by-using-oauth#register-your-application).

## **Использование современного способа аутентификации с EwsClient**

После регистрации приложения мы можем сосредоточиться на написании кода, который будет состоять из следующих частей:

 - Получение токена авторизации.
 - Использование токена для аутентификации.

### Получение токена авторизации

Чтобы получить токен, мы будем использовать [Microsoft Authentication Library (MSAL) для .NET](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet).

Следующие шаги приведут к получению токена авторизации.

 - Добавить [пакет Microsoft.Identity.Client nuget](https://www.nuget.org/packages/Microsoft.Identity.Client), который содержит бинарные файлы MSAL.NET.
 - Создать класс AccessParameters для хранения учетных данных.
 - Создать метод, принимающий параметры доступа, и используя MSAL.NET, получить токен доступа.

Следующие примеры кода будут зависеть от выбранного типа аутентификации.

**Получение токена с делегированной аутентификацией**

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
**Получение токена с аутентификацией приложения**

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

После этого, когда мы успешно получили токен, давайте инициализируем [EwsClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/).

**Использование токена с делегированной аутентификацией**

```csharp
NetworkCredential credentials = new OAuthNetworkCredential(accessToken);

using var client = EWSClient.GetEWSClient("https://outlook.office365.com/EWS/Exchange.asmx", credentials);

```

{{% alert %}}
**Попробуйте это!**
Запустите простой проект приложения [EWSModernAuthenticationDelegated](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Sample%20Apps/EWSModernAuthenticationDelegated), подключитесь к Microsoft 365 с делегированной аутентификацией и прочитайте свою папку "Входящие".
{{% /alert %}}

**Использование токена с аутентификацией приложения**

```csharp
// Используйте имя пользователя Microsoft365 и токен доступа
NetworkCredential credentials = new OAuthNetworkCredential(username, accessToken);

using var client = EWSClient.GetEWSClient("https://outlook.office365.com/EWS/Exchange.asmx", credentials);

```

{{% alert %}}
**Попробуйте это!**
Запустите простой проект приложения [EWSModernAuthenticationApp](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Sample%20Apps/EWSModernAuthenticationApp), подключитесь к Microsoft 365 с аутентификацией приложения и прочитайте свою папку "Входящие".
{{% /alert %}}

## **Использование современного способа аутентификации с IMAP, POP или SMTP клиентами**

Доступ через IMAP, POP, SMTP с использованием разрешений приложения не поддерживается. Иными словами, поддерживается только делегированная аутентификация.

Процедура регистрации приложения в Azure Active Directory описана [выше](https://blog.aspose.com/email/connect-to-microsoft365-mailbox-using-modern-authentication-in-c-.net/#App-registration-with-Azure-Active-Directory).

### Используйте центр администрирования Microsoft 365 для включения или отключения IMAP, POP, SMTP AUTH на конкретных почтовых ящиках

 - Откройте [центр администрирования Microsoft 365](https://admin.microsoft.com/) и перейдите в раздел **Пользователи > Активные пользователи**.
 - Выберите пользователя, и в появившемся всплывающем окне нажмите **Почта**.
 - В разделе **Почтовые приложения** нажмите **Управление почтовыми приложениями**.
 - Проверьте настройку **IMAP, POP, Аутентифицированный SMTP**: не отмечено = отключено, отмечено = включено.
 - Нажмите **Сохранить изменения**.

### Добавление кода для получения токена аутентификации с сервера токенов

Убедитесь, что вы указали полные области действия, включая URL-адреса ресурсов Outlook.

IMAP: https://outlook.office.com/IMAP.AccessAsUser.All  
POP: https://outlook.office.com/POP.AccessAsUser.All  
SMTP: https://outlook.office.com/SMTP.Send  

Чтобы получить токен, мы будем использовать [Microsoft Authentication Library (MSAL) для .NET](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet).

Следующие шаги приведут к получению токена авторизации.

- Добавить [пакет Microsoft.Identity.Client nuget](https://www.nuget.org/packages/Microsoft.Identity.Client), который содержит бинарные файлы MSAL.NET.
- Создать класс AccessParameters для хранения учетных данных.
- Создать метод, принимающий параметры доступа, и используя MSAL.NET, получить токен доступа.

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

### Использование токена для аутентификации

После этого, когда мы успешно получили токен, давайте инициализируем [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/).

```csharp
var imapClient = new ImapClient(
    "outlook.office365.com", 
    993, 
    username, 
    accessToken, 
    true);

```
Аналогично, инициализация [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) будет выглядеть следующим образом.

```csharp
var smtpClient = new SmtpClient(
    "smtp.office365.com",
    587, 
    username,
    accessToken, 
    true);

```

{{% alert %}}
**Попробуйте это!**
Запустите простой проект приложения [EWSModernAuthenticationImapSmtp](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Sample%20Apps/EWSModernAuthenticationImapSmtp), подключитесь к Microsoft 365 через IMAP и SMTP и прочитайте свою папку "Входящие".
{{% /alert %}}

## **Возврат идентификатора запроса клиента**

 Свойство [ReturnClientRequestId](https://reference.aspose.com/email/net/aspose.email.clients.exchange/autodiscoverservicebase/returnclientrequestid/) было добавлено к EWSClient для вашего удобства, чтобы указать, следует ли возвращать идентификатор запроса клиента в ответах на запросы к Exchange Web Services (EWS). Идентификатор запроса клиента — это уникальный идентификатор, который вы можете установить для каждого запроса EWS, отправленного из вашего приложения. Установив свойство [ReturnClientRequestId](https://reference.aspose.com/email/net/aspose.email.clients.exchange/autodiscoverservicebase/returnclientrequestid/) в *true*, вы указываете, что хотите, чтобы идентификатор запроса клиента был включен в ответ сервера EWS. Это может быть полезно для отслеживания и коррелирования запросов и ответов в сценариях, когда выполняются и обрабатываются несколько запросов асинхронно.

 Следующий фрагмент кода показывает, как можно использовать это свойство:

 ```cs
 using (IEWSClient client = TestUtil.CreateEWSClient(user))
{
    // Клиент создаст случайный идентификатор и передаст его серверу.
	// Сервер должен включить этот идентификатор в заголовок request-id всех ответов.
    client.ReturnClientRequestId = true;
    
	client.LogFileName = "ews.log";
    client.GetMailboxInfo();
}
 ```