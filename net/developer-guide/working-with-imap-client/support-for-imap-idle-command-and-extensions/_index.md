---
title: Support for IMAP IDLE Command And Extensions
type: docs
weight: 110
url: /net/support-for-imap-idle-command-and-extensions/
---


## **Support for IMAP Idle Command**
Aspose.Email API's [ImapClient](https://apireference.aspose.com/net/email/aspose.email.clients.imap/imapclient) provides the capability to open a connection to the server and wait for the arrival of an email message. This allows avoiding polling the server again and again for any incoming email. The following code snippet shows you how to Support for IMAP Idle Command.

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
## **Support for IMAP Extensions**
Aspose.Email API provides support for IMAP extensions. The following IMAP extensions are supported by the API at present. These IMAP extensions are not supported by all servers.

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
### **IMAP4 Extended List Command**
The following code snippet shows you how to use IMAP4 extended list command.

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
