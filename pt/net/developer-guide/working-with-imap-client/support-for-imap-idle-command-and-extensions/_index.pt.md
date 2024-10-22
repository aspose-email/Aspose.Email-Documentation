---
title: "Suporte para o Comando IMAP IDLE e Extensões"
url: /pt/net/support-for-imap-idle-command-and-extensions/
weight: 110
type: docs
---


## **Suporte para o Comando IMAP IDLE**

A API Aspose.Email [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) fornece a capacidade de abrir uma conexão com o servidor e aguardar a chegada de uma mensagem de e-mail. Isso permite evitar a verificação repetida do servidor por e-mails recebidos. O seguinte trecho de código mostra como suportar o comando IMAP IDLE.

```csharp
var client = new ImapClient("imap.domain.com", "username", "password");

// anySuccess é um sinalizador para evitar chamadas infinitas a Client.ResumeMonitoring
var anySuccess = false;
await client.StartMonitoringAsync(OnNewMessagesCallback, OnErrorCallback);

void OnErrorCallback(object eventSender, ImapMonitoringErrorEventArgs errorEventArguments)
{
    // A exceção pode ser tratada aqui
    Logger.Debug.Write(
        $"Ocorreu um erro durante a monitorização da pasta: {errorEventArguments.FolderName}",
        errorEventArguments.Error);
    // A monitorização da pasta IMAP é interrompida em qualquer erro. Aqui está um exemplo
    // de retomar após isso.
    if (!anySuccess) return;
    anySuccess = false;
    // Certifique-se de usar ResumeMonitoring em vez de StartMonitoring aqui
    // para evitar perder qualquer e-mail entre o tratamento de erros e a retomada.
    client.ResumeMonitoring(OnNewMessagesCallback, OnErrorCallback,
        errorEventArguments.MonitoringState);
}

void OnNewMessagesCallback(object sender, ImapMonitoringEventArgs successEventArgs)
{
    anySuccess = true;
    // Use successEventArgs.NewMessages para lidar com novas mensagens
    // Use successEventArgs.DeletedMessages para lidar com mensagens deletadas
}
```

## **Suporte para Extensões IMAP**

A API Aspose.Email fornece suporte para extensões IMAP. As seguintes extensões IMAP são atualmente suportadas pela API. Essas extensões IMAP não são suportadas por todos os servidores.

```csharp
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-.NET
using (ImapClient client = new ImapClient("imap.gmail.com", 993, "username", "password"))
{
    // Definir SecurityOptions
    client.SecurityOptions = SecurityOptions.Auto;
    Console.WriteLine(client.IdSupported.ToString());

    ImapIdentificationInfo serverIdentificationInfo1 = client.IntroduceClient();
    ImapIdentificationInfo serverIdentificationInfo2 = client.IntroduceClient(ImapIdentificationInfo.DefaultValue);

    // Exibir propriedades do ImapIdentificationInfo
    Console.WriteLine(serverIdentificationInfo1.ToString(), serverIdentificationInfo2);
    Console.WriteLine(serverIdentificationInfo1.Name);
    Console.WriteLine(serverIdentificationInfo1.Vendor);
    Console.WriteLine(serverIdentificationInfo1.SupportUrl);
    Console.WriteLine(serverIdentificationInfo1.Version);
}
```

### **Comando IMAP4 Extended List**

O seguinte trecho de código mostra como usar o comando IMAP4 extended list.

```csharp
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-.NET
using (ImapClient client = new ImapClient("imap.gmail.com", 993, "username", "password"))
{
    ImapFolderInfoCollection folderInfoCol = client.ListFolders("*");
    Console.WriteLine("Lista Estendida Suportada: " + client.ExtendedListSupported);
    foreach (ImapFolderInfo folderInfo in folderInfoCol)
    {
        switch (folderInfo.Name)
        {
            case "[Gmail]/Todos os e-mails":
                Console.WriteLine("Tem filhos: " + folderInfo.HasChildren);
                break;
            case "[Gmail]/Lixeira":
                Console.WriteLine("A Lixeira tem filhos? " + folderInfo.HasChildren);
                break;
            case "[Gmail]/Rascunhos":
                Console.WriteLine("Os Rascunhos têm filhos? " + folderInfo.HasChildren);
                break;
            case "[Gmail]/Importante":
                Console.WriteLine("Importante tem filhos? " + folderInfo.HasChildren);
                break;
            case "[Gmail]/E-mails Enviados":
                Console.WriteLine("E-mails Enviados têm filhos? " + folderInfo.HasChildren);
                break;
            case "[Gmail]/Spam":
                Console.WriteLine("Spam tem filhos? " + folderInfo.HasChildren);
                break;
            case "[Gmail]/Marcados":
                Console.WriteLine("Marcados têm filhos? " + folderInfo.HasChildren);
                break;
        }
    }
}
```