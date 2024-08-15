---
title: "Поддержка команд и расширений IMAP IDLE"
url: /ru/net/support-for-imap-idle-command-and-extensions/
weight: 110
type: docs
---


## **Поддержка команды IMAP Idle**

API Aspose.Email [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) предоставляет возможность открыть соединение с сервером и дождаться получения сообщения электронной почты. Это позволяет избежать повторного опроса сервера на предмет получения входящей электронной почты. В следующем фрагменте кода показано, как поддерживать команду IMAP Idle.

```csharp
var client = = new ImapClient("imap.domain.com", "username", "password");

//anySuccess is a flag to prevent infinite Client.ResumeMonitoring calls
var anySuccess = false;
await client.StartMonitoringAsync(OnNewMessagesCallback, OnErrorCallback);

void OnErrorCallback(object eventSender, ImapMonitoringErrorEventArgs errorEventArguments)
{
    //The exception can be handled here
    Logger.Debug.Write(
        $"An error occured while folder monitoring: {errorEventArguments.FolderName}",
        errorEventArguments.Error);
    //IMAP folder monitoring is stopped on any error. Here is an example
    //of resuming after that.
    if (!anySuccess) return;
    anySuccess = false;
    //Make sure you use ResumeMonitoring instead of StartMonitoring here
    //to prevent missing any emails between the error handling and resuming.
    client.ResumeMonitoring(OnNewMessagesCallback, OnErrorCallback,
        errorEventArguments.MonitoringState);
}

void OnNewMessagesCallback(object sender, ImapMonitoringEventArgs successEventArgs)
{
    anySuccess = true;
    //Use successEventArgs.NewMessages to handle new messages
    //Use successEventArgs.DeletedMessages to handle deleted messages
}
```

## **Поддержка расширений IMAP**

API Aspose.Email обеспечивает поддержку расширений IMAP. В настоящее время API поддерживает следующие расширения IMAP. Эти расширения IMAP поддерживаются не всеми серверами.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
using (ImapClient client = new ImapClient("imap.gmail.com", 993, "username", "password"))
{
    // Set SecurityOptions
    client.SecurityOptions = SecurityOptions.Auto;
    Console.WriteLine(client.IdSupported.ToString());

    ImapIdentificationInfo serverIdentificationInfo1 = client.IntroduceClient();
    ImapIdentificationInfo serverIdentificationInfo2 = client.IntroduceClient(ImapIdentificationInfo.DefaultValue);

    // Display ImapIdentificationInfo properties
    Console.WriteLine(serverIdentificationInfo1.ToString(), serverIdentificationInfo2);
    Console.WriteLine(serverIdentificationInfo1.Name);
    Console.WriteLine(serverIdentificationInfo1.Vendor);
    Console.WriteLine(serverIdentificationInfo1.SupportUrl);
    Console.WriteLine(serverIdentificationInfo1.Version);
}
```

### **Команда расширенного списка IMAP4**

В следующем фрагменте кода показано, как использовать команду IMAP4 extended list.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
using (ImapClient client = new ImapClient("imap.gmail.com", 993, "username", "password"))
{
    ImapFolderInfoCollection folderInfoCol = client.ListFolders("*");
    Console.WriteLine("Extended List Supported: " + client.ExtendedListSupported);
    foreach (ImapFolderInfo folderInfo in folderInfoCol)
    {
        switch (folderInfo.Name)
        {
            case "[Gmail]/All Mail":
                Console.WriteLine("Has Children: " + folderInfo.HasChildren);
                break;
            case "[Gmail]/Bin":
                Console.WriteLine("Bin has children? " + folderInfo.HasChildren);
                break;
            case "[Gmail]/Drafts":
                Console.WriteLine("Drafts has children? " + folderInfo.HasChildren);
                break;
            case "[Gmail]/Important":
                Console.WriteLine("Important has Children? " + folderInfo.HasChildren);
                break;
            case "[Gmail]/Sent Mail":
                Console.WriteLine("Sent Mail has Children? " + folderInfo.HasChildren);
                break;
            case "[Gmail]/Spam":
                Console.WriteLine("Spam has Children? " + folderInfo.HasChildren);
                break;
            case "[Gmail]/Starred":
                Console.WriteLine("Starred has Children? " + folderInfo.HasChildren);
                break;
        }
    }
}
```
