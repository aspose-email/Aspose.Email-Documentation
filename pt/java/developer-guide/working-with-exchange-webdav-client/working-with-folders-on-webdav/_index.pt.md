---
title: "Trabalhando com Pastas no WebDav"
url: /pt/java/trabalhando-com-pastas-no-webdav/
weight: 130
type: docs
---


## **Listando todas as Pastas do Servidor**
A API Aspose.Email fornece a capacidade de se conectar ao Exchange Server e listar todas as pastas e sub-pastas. Você também pode recuperar todas as sub-pastas de cada pasta de forma recursiva. Este artigo mostra como recuperar todas as sub-pastas do servidor Exchange e recuperar pastas com paginação.
### **Usando WebDav**
O seguinte trecho de código mostra como listar pastas do Exchange Server.


~~~Java
public static void run() {
    try {
        ExchangeClient client = new ExchangeClient("http://ex07sp1/exchange/Administrator", "user", "pwd", "domain");
        System.out.println("Baixando todas as mensagens da Caixa de Entrada....");

        ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();
        System.out.println("URI da Caixa de Correio: " + mailboxInfo.getMailboxUri());
        String rootUri = client.getMailboxInfo().getRootUri();
        // Listar todas as pastas do servidor Exchange
        ExchangeFolderInfoCollection folderInfoCollection = client.listSubFolders(rootUri);
        for (ExchangeFolderInfo folderInfo : folderInfoCollection) {
            // Chamar o método recursivo para ler mensagens e obter sub-pastas
            listSubFolders(client, folderInfo);
        }

        System.out.println("Todas as mensagens baixadas.");
    } catch (Exception ex) {
        System.err.println(ex);
    }
}

private static void listSubFolders(ExchangeClient client, ExchangeFolderInfo folderInfo) {
    System.out.println(folderInfo.getDisplayName());
    try {
        // Se esta pasta tem sub-pastas, chamar este método recursivamente para obter mensagens
        ExchangeFolderInfoCollection folderInfoCollection = client.ListSubFolders(folderInfo.Uri);
        for (ExchangeFolderInfo subfolderInfo : folderInfoCollection) {
            listSubFolders(client, subfolderInfo);
        }
    } catch (Exception ex) {
        System.err.println(ex);
    }
}
~~~