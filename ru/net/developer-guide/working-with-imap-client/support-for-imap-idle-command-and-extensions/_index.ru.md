---
title: "Поддержка команды IMAP IDLE и расширений"
url: /ru/net/support-for-imap-idle-command-and-extensions/
weight: 110
type: docs
---


## **Поддержка команды IMAP IDLE**

API Aspose.Email [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) предоставляет возможность установить соединение с сервером и ожидать поступления email-сообщения. Это позволяет избежать повторных запросов к серверу для получения входящих писем. Следующий фрагмент кода показывает, как поддерживать команду IMAP IDLE.

```csharp
var client = = new ImapClient("imap.domain.com", "username", "password");

//anySuccess – это флаг, предотвращающий бесконечные вызовы Client.ResumeMonitoring
var anySuccess = false;
await client.StartMonitoringAsync(OnNewMessagesCallback, OnErrorCallback);

void OnErrorCallback(object eventSender, ImapMonitoringErrorEventArgs errorEventArguments)
{
    //Исключение можно обработать здесь
    Logger.Debug.Write(
        $"Произошла ошибка при мониторинге папки: {errorEventArguments.FolderName}",
        errorEventArguments.Error);
    //Мониторинг IMAP папки останавливается при любой ошибке. Вот пример
    //возобновления после этого.
    if (!anySuccess) return;
    anySuccess = false;
    //Убедитесь, что вы используете ResumeMonitoring вместо StartMonitoring здесь
    //чтобы избежать пропуска каких-либо писем между обработкой ошибок и возобновлением.
    client.ResumeMonitoring(OnNewMessagesCallback, OnErrorCallback,
        errorEventArguments.MonitoringState);
}

void OnNewMessagesCallback(object sender, ImapMonitoringEventArgs successEventArgs)
{
    anySuccess = true;
    //Используйте successEventArgs.NewMessages для обработки новых сообщений
    //Используйте successEventArgs.DeletedMessages для обработки удаленных сообщений
}
```

## **Поддержка расширений IMAP**

API Aspose.Email предоставляет поддержку расширений IMAP. В настоящее время API поддерживает следующие расширения IMAP. Эти расширения IMAP не поддерживаются всеми серверами.

```csharp
// Для получения полных примеров и файлов данных, пожалуйста, перейдите на https://github.com/aspose-email/Aspose.Email-for-.NET
using (ImapClient client = new ImapClient("imap.gmail.com", 993, "username", "password"))
{
    // Установить SecurityOptions
    client.SecurityOptions = SecurityOptions.Auto;
    Console.WriteLine(client.IdSupported.ToString());

    ImapIdentificationInfo serverIdentificationInfo1 = client.IntroduceClient();
    ImapIdentificationInfo serverIdentificationInfo2 = client.IntroduceClient(ImapIdentificationInfo.DefaultValue);

    // Отобразить свойства ImapIdentificationInfo
    Console.WriteLine(serverIdentificationInfo1.ToString(), serverIdentificationInfo2);
    Console.WriteLine(serverIdentificationInfo1.Name);
    Console.WriteLine(serverIdentificationInfo1.Vendor);
    Console.WriteLine(serverIdentificationInfo1.SupportUrl);
    Console.WriteLine(serverIdentificationInfo1.Version);
}
```

### **Расширенная команда IMAP4 List**

Следующий фрагмент кода показывает, как использовать расширенную команду IMAP4 List.

```csharp
// Для получения полных примеров и файлов данных, пожалуйста, перейдите на https://github.com/aspose-email/Aspose.Email-for-.NET
using (ImapClient client = new ImapClient("imap.gmail.com", 993, "username", "password"))
{
    ImapFolderInfoCollection folderInfoCol = client.ListFolders("*");
    Console.WriteLine("Расширенный список поддерживается: " + client.ExtendedListSupported);
    foreach (ImapFolderInfo folderInfo in folderInfoCol)
    {
        switch (folderInfo.Name)
        {
            case "[Gmail]/Все письма":
                Console.WriteLine("Есть дочерние? " + folderInfo.HasChildren);
                break;
            case "[Gmail]/Корзина":
                Console.WriteLine("В корзине есть дочерние? " + folderInfo.HasChildren);
                break;
            case "[Gmail]/Черновики":
                Console.WriteLine("В черновиках есть дочерние? " + folderInfo.HasChildren);
                break;
            case "[Gmail]/Важные":
                Console.WriteLine("В важных есть дочерние? " + folderInfo.HasChildren);
                break;
            case "[Gmail]/Отправленные":
                Console.WriteLine("В отправленных есть дочерние? " + folderInfo.HasChildren);
                break;
            case "[Gmail]/Спам":
                Console.WriteLine("В спаме есть дочерние? " + folderInfo.HasChildren);
                break;
            case "[Gmail]/Звёздные":
                Console.WriteLine("В звёздных есть дочерние? " + folderInfo.HasChildren);
                break;
        }
    }
}
```