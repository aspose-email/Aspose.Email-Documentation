---
title: "Soporte para el comando IMAP IDLE y extensiones"
url: /es/java/support-for-imap-idle-command-and-extensions/
weight: 110
type: docs
---


## **Soporte para el comando IMAP Idle**

La API de Aspose.Email [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) proporciona la capacidad de abrir una conexión con el servidor y esperar la llegada de un mensaje de correo electrónico. Esto permite evitar la consulta al servidor una y otra vez por cualquier correo electrónico entrante. El siguiente fragmento de código muestra cómo soportar el comando IMAP Idle.

~~~Java
// Para ejemplos completos y archivos de datos, por favor ve a https://github.com/aspose-email/Aspose.Email-for-Java
// Conectar e iniciar sesión en IMAP
ImapClient client = new ImapClient("imap.dominio.com", "nombredeusuario", "contraseña");

client.startMonitoring(new ImapMonitoringEventHandler() {
    public void invoke(Object sender, ImapMonitoringEventArgs e) {
        System.out.println(e.getNewMessages().length);
        System.out.println(e.getDeletedMessages().length);
    }
});
client.stopMonitoring("Bandeja de entrada");
~~~

## **Soporte para extensiones IMAP**

La API de Aspose.Email proporciona soporte para extensiones IMAP. Las siguientes extensiones IMAP son compatibles con la API en la actualidad. Estas extensiones IMAP no son compatibles con todos los servidores.

~~~Java
// Para ejemplos completos y archivos de datos, por favor ve a https://github.com/aspose-email/Aspose.Email-for-Java
final ImapClient client = new ImapClient("imap.gmail.com", 993, "nombredeusuario", "contraseña");
try {
    // Establecer opciones de seguridad
    client.setSecurityOptions(SecurityOptions.Auto);
    System.out.println(client.getIdSupported());

    ImapIdentificationInfo serverIdentificationInfo1 = client.introduceClient();
    ImapIdentificationInfo serverIdentificationInfo2 = client.introduceClient(ImapIdentificationInfo.getDefaultValue());

    // Mostrar propiedades de ImapIdentificationInfo
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

### **Comando IMAP4 Extended List**

El siguiente fragmento de código muestra cómo usar el comando IMAP4 extended list.

~~~Java
// Para ejemplos completos y archivos de datos, por favor ve a https://github.com/aspose-email/Aspose.Email-for-Java
final ImapClient client = new ImapClient("imap.gmail.com", 993, "nombredeusuario", "contraseña");
try {
    ImapFolderInfoCollection folderInfoCol = client.listFolders("*");
    System.out.println("Lista extendida soportada: " + client.getExtendedListSupported());
    for (ImapFolderInfo folderInfo : (Iterable<ImapFolderInfo>) folderInfoCol) {
        if (folderInfo.getName().equals("[Gmail]/Todo el correo"))
            System.out.println("Tiene hijos: " + folderInfo.hasChildren());
        if (folderInfo.getName().equals("[Gmail]/Papelera"))
            System.out.println("¿La papelera tiene hijos? " + folderInfo.hasChildren());
        if (folderInfo.getName().equals("[Gmail]/Borradores"))
            System.out.println("¿Los borradores tienen hijos? " + folderInfo.hasChildren());
        if (folderInfo.getName().equals("[Gmail]/Importante"))
            System.out.println("¿Importante tiene hijos? " + folderInfo.hasChildren());
        if (folderInfo.getName().equals("[Gmail]/Correo enviado"))
            System.out.println("¿El correo enviado tiene hijos? " + folderInfo.hasChildren());
        if (folderInfo.getName().equals("[Gmail]/Spam"))
            System.out.println("¿El spam tiene hijos? " + folderInfo.hasChildren());
        if (folderInfo.getName().equals("[Gmail]/Destacados"))
            System.out.println("¿Los destacados tienen hijos? " + folderInfo.hasChildren());
    }
} finally {
    if (client != null)
        client.dispose();
}
~~~