---
title: "Suporte para o Comando IMAP IDLE e Extensões"
url: /pt/java/support-for-imap-idle-command-and-extensions/
weight: 110
type: docs
---

## **Suporte para o Comando IMAP Idle**

A API Aspose.Email [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) fornece a capacidade de abrir uma conexão com o servidor e aguardar a chegada de uma mensagem de email. Isso evita a necessidade de verificar o servidor repetidamente por qualquer email recebido. O seguinte trecho de código mostra como suportar o Comando IMAP Idle.

~~~Java
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-Java
// Conectar e fazer login no IMAP
ImapClient client = new ImapClient("imap.domain.com", "username", "password");

client.startMonitoring(new ImapMonitoringEventHandler() {
    public void invoke(Object sender, ImapMonitoringEventArgs e) {
        System.out.println(e.getNewMessages().length);
        System.out.println(e.getDeletedMessages().length);
    }
});
client.stopMonitoring("Inbox");
~~~

## **Suporte para Extensões IMAP**

A API Aspose.Email oferece suporte para extensões IMAP. As seguintes extensões IMAP são suportadas pela API no momento. Essas extensões IMAP não são suportadas por todos os servidores.

~~~Java
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-Java
final ImapClient client = new ImapClient("imap.gmail.com", 993, "username", "password");
try {
    // Definir SecurityOptions
    client.setSecurityOptions(SecurityOptions.Auto);
    System.out.println(client.getIdSupported());

    ImapIdentificationInfo serverIdentificationInfo1 = client.introduceClient();
    ImapIdentificationInfo serverIdentificationInfo2 = client.introduceClient(ImapIdentificationInfo.getDefaultValue());

    // Exibir propriedades do ImapIdentificationInfo
    System.out.println(serverIdentificationInfo1.toString() + serverIdentificationInfo2.toString());
    System.out.println(serverIdentificationInfo1.getName());
    System.out.println(serverIdentificationInfo1.getVendor());
    System.out.println(serverIdentificationInfo1.getSupportUrl());
    System.out.println(serverIdentificationInfo1.getVersion());
} finally {
    if (client != null)
        client.dispose();
}
~~~

### **Comando de Lista Estendida IMAP4**

O seguinte trecho de código mostra como usar o comando de lista estendida IMAP4.

~~~Java
// Para exemplos completos e arquivos de dados, por favor vá para https://github.com/aspose-email/Aspose.Email-for-Java
final ImapClient client = new ImapClient("imap.gmail.com", 993, "username", "password");
try {
    ImapFolderInfoCollection folderInfoCol = client.listFolders("*");
    System.out.println("Lista Estendida Suportada: " + client.getExtendedListSupported());
    for (ImapFolderInfo folderInfo : (Iterable<ImapFolderInfo>) folderInfoCol) {
        if (folderInfo.getName().equals("[Gmail]/Todos os e-mails"))
            System.out.println("Tem Filhos: " + folderInfo.hasChildren());
        if (folderInfo.getName().equals("[Gmail]/Lixeira"))
            System.out.println("A Lixeira tem filhos? " + folderInfo.hasChildren());
        if (folderInfo.getName().equals("[Gmail]/Rascunhos"))
            System.out.println("Rascunhos tem filhos? " + folderInfo.hasChildren());
        if (folderInfo.getName().equals("[Gmail]/Importante"))
            System.out.println("Importante tem Filhos? " + folderInfo.hasChildren());
        if (folderInfo.getName().equals("[Gmail]/E-mails Enviados"))
            System.out.println("E-mails Enviados tem Filhos? " + folderInfo.hasChildren());
        if (folderInfo.getName().equals("[Gmail]/Spam"))
            System.out.println("Spam tem Filhos? " + folderInfo.hasChildren());
        if (folderInfo.getName().equals("[Gmail]/Destacados"))
            System.out.println("Destacados têm Filhos? " + folderInfo.hasChildren());
    }
} finally {
    if (client != null)
        client.dispose();
}
~~~