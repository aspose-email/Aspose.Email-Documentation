---
title: "Trabajando con Carpetas en WebDav"
url: /es/java/working-with-folders-on-webdav/
weight: 130
type: docs
---


## **Listando todas las Carpetas del Servidor**
La API de Aspose.Email proporciona la capacidad de conectarse al Servidor de Exchange y listar todas las carpetas y subcarpetas. También puedes recuperar todas las subcarpetas de cada carpeta de forma recursiva. Este artículo muestra cómo recuperar todas las subcarpetas del servidor de Exchange y recuperar carpetas con paginación.
### **Usando WebDav**
El siguiente fragmento de código muestra cómo listar carpetas del Servidor de Exchange.


~~~Java
public static void run() {
    try {
        ExchangeClient client = new ExchangeClient("http://ex07sp1/exchange/Administrator", "user", "pwd", "domain");
        System.out.println("Descargando todos los mensajes de la Bandeja de Entrada....");

        ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();
        System.out.println("URI del Buzón: " + mailboxInfo.getMailboxUri());
        String rootUri = client.getMailboxInfo().getRootUri();
        // Listar todas las carpetas del servidor de Exchange
        ExchangeFolderInfoCollection folderInfoCollection = client.listSubFolders(rootUri);
        for (ExchangeFolderInfo folderInfo : folderInfoCollection) {
            // Llamar al método recursivo para leer mensajes y obtener subcarpetas
            listSubFolders(client, folderInfo);
        }

        System.out.println("Todos los mensajes descargados.");
    } catch (Exception ex) {
        System.err.println(ex);
    }
}

private static void listSubFolders(ExchangeClient client, ExchangeFolderInfo folderInfo) {
    System.out.println(folderInfo.getDisplayName());
    try {
        // Si esta carpeta tiene subcarpetas, llamar a este método recursivamente para obtener mensajes
        ExchangeFolderInfoCollection folderInfoCollection = client.ListSubFolders(folderInfo.Uri);
        for (ExchangeFolderInfo subfolderInfo : folderInfoCollection) {
            listSubFolders(client, subfolderInfo);
        }
    } catch (Exception ex) {
        System.err.println(ex);
    }
}
~~~