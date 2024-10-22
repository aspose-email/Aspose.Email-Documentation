---
title: "Soporte para el comando IMAP IDLE y extensiones"
url: /es/net/support-for-imap-idle-command-and-extensions/
weight: 110
type: docs
---

## **Soporte para el comando IMAP Idle**

La API Aspose.Email [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) proporciona la capacidad de abrir una conexión con el servidor y esperar la llegada de un mensaje de correo electrónico. Esto permite evitar el sondeo al servidor una y otra vez para cualquier correo entrante. El siguiente fragmento de código muestra cómo dar soporte al comando IMAP Idle.

```csharp
var client = new ImapClient("imap.domain.com", "username", "password");

//anySuccess es una bandera para prevenir llamadas infinitas a Client.ResumeMonitoring
var anySuccess = false;
await client.StartMonitoringAsync(OnNewMessagesCallback, OnErrorCallback);

void OnErrorCallback(object eventSender, ImapMonitoringErrorEventArgs errorEventArguments)
{
    //La excepción puede ser manejada aquí
    Logger.Debug.Write(
        $"Ocurrió un error durante la monitorización de la carpeta: {errorEventArguments.FolderName}",
        errorEventArguments.Error);
    //La monitorización de la carpeta IMAP se detiene ante cualquier error. Aquí hay un ejemplo
    //de reanudar después de eso.
    if (!anySuccess) return;
    anySuccess = false;
    //Asegúrate de usar ResumeMonitoring en lugar de StartMonitoring aquí
    //para prevenir la pérdida de cualquier correo entre el manejo del error y la reanudación.
    client.ResumeMonitoring(OnNewMessagesCallback, OnErrorCallback,
        errorEventArguments.MonitoringState);
}

void OnNewMessagesCallback(object sender, ImapMonitoringEventArgs successEventArgs)
{
    anySuccess = true;
    //Usa successEventArgs.NewMessages para manejar nuevos mensajes
    //Usa successEventArgs.DeletedMessages para manejar mensajes eliminados
}
```

## **Soporte para extensiones IMAP**

La API Aspose.Email proporciona soporte para extensiones IMAP. Las siguientes extensiones IMAP son soportadas por la API en la actualidad. Estas extensiones IMAP no son soportadas por todos los servidores.

```csharp
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-.NET
using (ImapClient client = new ImapClient("imap.gmail.com", 993, "username", "password"))
{
    // Establecer opciones de seguridad
    client.SecurityOptions = SecurityOptions.Auto;
    Console.WriteLine(client.IdSupported.ToString());

    ImapIdentificationInfo serverIdentificationInfo1 = client.IntroduceClient();
    ImapIdentificationInfo serverIdentificationInfo2 = client.IntroduceClient(ImapIdentificationInfo.DefaultValue);

    // Mostrar propiedades de ImapIdentificationInfo
    Console.WriteLine(serverIdentificationInfo1.ToString(), serverIdentificationInfo2);
    Console.WriteLine(serverIdentificationInfo1.Name);
    Console.WriteLine(serverIdentificationInfo1.Vendor);
    Console.WriteLine(serverIdentificationInfo1.SupportUrl);
    Console.WriteLine(serverIdentificationInfo1.Version);
}
```

### **Comando de lista extendida IMAP4**

El siguiente fragmento de código muestra cómo usar el comando de lista extendida IMAP4.

```csharp
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-.NET
using (ImapClient client = new ImapClient("imap.gmail.com", 993, "username", "password"))
{
    ImapFolderInfoCollection folderInfoCol = client.ListFolders("*");
    Console.WriteLine("Lista extendida soportada: " + client.ExtendedListSupported);
    foreach (ImapFolderInfo folderInfo in folderInfoCol)
    {
        switch (folderInfo.Name)
        {
            case "[Gmail]/Todo el correo":
                Console.WriteLine("¿Tiene hijos?: " + folderInfo.HasChildren);
                break;
            case "[Gmail]/Papelera":
                Console.WriteLine("¿La papelera tiene hijos? " + folderInfo.HasChildren);
                break;
            case "[Gmail]/Borradores":
                Console.WriteLine("¿Los borradores tienen hijos? " + folderInfo.HasChildren);
                break;
            case "[Gmail]/Importante":
                Console.WriteLine("¿Importante tiene hijos? " + folderInfo.HasChildren);
                break;
            case "[Gmail]/Correo enviado":
                Console.WriteLine("¿El correo enviado tiene hijos? " + folderInfo.HasChildren);
                break;
            case "[Gmail]/Spam":
                Console.WriteLine("¿Spam tiene hijos? " + folderInfo.HasChildren);
                break;
            case "[Gmail]/Destacados":
                Console.WriteLine("¿Destacados tienen hijos? " + folderInfo.HasChildren);
                break;
        }
    }
}
```