---
title: "Registro de actividad de IMAPClient"
url: /es/net/imapclient-activity-logging/
weight: 90
type: docs
---

El registro de actividades se usa para depurar, así como para recopilar y analizar información de trabajo sobre el cliente IMAP.

## **Habilitar el registro de actividades mediante el archivo appsettings.json**

> **_NOTE:_** Esta opción es la preferida para las aplicaciones.NET Core.

Iniciar sesión [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) se puede habilitar con los siguientes pasos y ejemplos de código:

1. Agregue un archivo de configuración appsettings.json a un proyecto de C#, si no se ha agregado antes.
2. Asegúrese de que el archivo del proyecto contenga las siguientes líneas en la sección ItemGroup.

   ```xml
      <Content Include="appsettings.json">
          <CopyToOutputDirectory>Always</CopyToOutputDirectory>
      </Content>
   ```

3. A continuación, añada el siguiente contenido al archivo appsettings.json.

   ```json
      {
        "ImapDiagnosticLog": "imap.log",
        "ImapDiagnosticLog_UseDate": true
      }
   ```

Las dos propiedades mencionadas anteriormente son:

- **ImapDiagnosticLog** - especifica la ruta relativa o absoluta al archivo de registro.

- **ImapDiagnosticLog_UseDate** - especifica si se debe añadir una representación en cadena de la fecha actual al nombre del archivo de registro.

## **Habilitar el registro de actividades en el código del programa**

También puede activar el registro de forma inmediata en el código.

> **_NOTE:_** aunque ya haya habilitado el registro mediante archivos de configuración, se aplicará esta opción.

Iniciar sesión [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) se puede habilitar con los siguientes pasos y ejemplos de código:

1. Crea un [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/).
2. Establezca la ruta al archivo de registro mediante el [LogFileName](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/logfilename/) property.
3. Configure el [UseDateInLogFileName](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usedateinlogfilename/) propiedad si es necesario.

```cs
   using (var client = new ImapClient("your imap server", 993, "your username", "your password"))
{
    // Set security mode
    client.SecurityOptions = SecurityOptions.Auto;

    // Establezca la ruta al archivo de registro mediante el LogFileName property.
    client.LogFileName = @"C:\Aspose.Email.IMAP.log";

    // Configure el UseDateInLogFileName propiedad si es necesario.
    client.UseDateInLogFileName = false;
}
```

## **Habilitar el registro de actividades mediante el archivo App.config**

[ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) la actividad se puede registrar modificando las ConfigSections en el archivo de configuración. Los siguientes son los pasos para realizar el registro de diagnósticos:

1. Añadir un **sectionGroup** llamado «ApplicationSettings».
1. Añadir un **section** llamado «Aspose.Email.Properties.Settings».
1. Incluya la configuración IMAPDiagonosticLog donde el nombre del archivo está definido en el **applicationSettings/Aspose.Email.Properties.Settings**.

Aquí hay un ejemplo de aplicación de formulario que utiliza [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) para procesar el correo. Toda esta actividad se registra modificando el archivo App.config.

- Cree una aplicación basada en formularios con un solo botón. Agregue el siguiente código de ejemplo para hacer clic en un botón:

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-ImapClientActivityLogging-ImapClientActivityLogging.cs" >}}

- Agregue una referencia a Aspose.Email.

|![todo:image_alt_text](imapclient-activity-logging_1.png)| |
|: - |: - |

- Ahora añada el archivo App.Config y modifíquelo para que el contenido del archivo sea el siguiente:

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-ImapClientActivityLogging-ImapClientActivityLogging.xml" >}}

Para C# .NET, utilice la siguiente opción

|![todo:image_alt_text](imapclient-activity-logging_2.png)| |
|: - |: - |
Para VB.NET, utilice la siguiente opción

|![todo:image_alt_text](imapclient-activity-logging_2.png)| |![todo:image_alt_text](imapclient-activity-logging_4.png)| |
|: - |: - |: - |: - |

|![todo:image_alt_text](imapclient-activity-logging_5.png)| |
|: - |: - |

- Ejecute el código y, a continuación, observe la carpeta de registro. Se generará el siguiente archivo.

|![todo:image_alt_text](imapclient-activity-logging_6.png)| |
|: - |: - |
