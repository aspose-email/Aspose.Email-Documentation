---
title: "Registro de Actividad de ImapClient"
url: /es/net/imapclient-activity-logging/
weight: 90
type: docs
---

El registro de actividad se utiliza para depuración, así como para recopilar y analizar información de funcionamiento sobre el cliente IMAP.

## **Habilitar el Registro de Actividad usando el Archivo appsettings.json**

> **_NOTA:_** Esta opción es preferida para aplicaciones .NET Core.

El registro en [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) se puede habilitar con los siguientes pasos y ejemplos de código:

1. Agrega un archivo de configuración appsettings.json a un proyecto C#, si no se ha agregado antes.
2. Asegúrate de que el archivo del proyecto contenga las siguientes líneas en la sección ItemGroup.

   ```xml
      <Content Include="appsettings.json">
          <CopyToOutputDirectory>Always</CopyToOutputDirectory>
      </Content>
   ```

3. Luego, agrega el siguiente contenido al archivo appsettings.json.

   ```json
      {
        "ImapDiagnosticLog": "imap.log",
        "ImapDiagnosticLog_UseDate": true
      }
   ```

Las dos propiedades mencionadas anteriormente son:

- **ImapDiagnosticLog** - especifica la ruta relativa o absoluta al archivo de registro.

- **ImapDiagnosticLog_UseDate** - especifica si se debe agregar una representación en cadena de la fecha actual al nombre del archivo de registro.

## **Habilitar el Registro de Actividad en el Código del Programa**

También puedes habilitar el registro de inmediato en el código.

> **_NOTA:_** incluso si ya has habilitado el registro usando archivos de configuración, esta opción se aplicará.

El registro en [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) se puede habilitar con los siguientes pasos y ejemplos de código:

1. Crea un [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/).
2. Establece la ruta al archivo de registro usando la propiedad [LogFileName](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/logfilename/).
3. Establece la propiedad [UseDateInLogFileName](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usedateinlogfilename/) si es necesario.

```cs
   using (var client = new ImapClient("your imap server", 993, "your username", "your password"))
{
    // Establecer el modo de seguridad
    client.SecurityOptions = SecurityOptions.Auto;

    // Establecer la ruta al archivo de registro usando la propiedad LogFileName.
    client.LogFileName = @"C:\Aspose.Email.IMAP.log";

    // Establecer la propiedad UseDateInLogFileName si es necesario.
    client.UseDateInLogFileName = false;
}
```

## **Habilitar el Registro de Actividad usando el Archivo App.config**

La actividad de [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) se puede registrar modificando las configSections en el archivo de configuración. A continuación se presentan los pasos para realizar el registro de diagnósticos:

1. Agrega un **sectionGroup** llamado "applicationSettings".
1. Agrega una **section** llamada "Aspose.Email.Properties.Settings".
1. Incluye la configuración ImapDiagonosticLog donde se define el nombre del archivo en **applicationSettings/Aspose.Email.Properties.Settings**.

Aquí hay un ejemplo de una aplicación de formularios que utiliza [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) para procesar correo. Esta actividad completa se registra modificando el archivo App.config.

- Crea una aplicación basada en formularios con un solo botón. Agrega el siguiente código de ejemplo para el clic del botón:

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-ImapClientActivityLogging-ImapClientActivityLogging.cs" >}}

- Agrega una referencia a Aspose.Email.

|![todo:image_alt_text](imapclient-activity-logging_1.png)| |
| :- | :- |

- Ahora agrega el archivo App.Config y modifícalo para que el contenido del archivo sea el siguiente:

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-ImapClientActivityLogging-ImapClientActivityLogging.xml" >}}

Para C# .NET usa la siguiente opción

|![todo:image_alt_text](imapclient-activity-logging_2.png)| |
| :- | :- |
Para VB .NET usa la siguiente opción

|![todo:image_alt_text](imapclient-activity-logging_2.png)| |![todo:image_alt_text](imapclient-activity-logging_4.png)| |
| :- | :- | :- | :- |

|![todo:image_alt_text](imapclient-activity-logging_5.png)| |
| :- | :- |

- Ejecuta el código y luego observa la carpeta Log. Se generará el siguiente archivo.

|![todo:image_alt_text](imapclient-activity-logging_6.png)| |
| :- | :- |