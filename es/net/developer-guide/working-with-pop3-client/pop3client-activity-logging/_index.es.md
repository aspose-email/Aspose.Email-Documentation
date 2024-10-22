---
title: "Registro de Actividades de Pop3Client"
url: /es/net/pop3client-activity-logging/
weight: 40
type: docs
---

El registro de actividades se utiliza para depuración, así como para recopilar y analizar información de trabajo sobre el cliente POP3.

## **Habilitar el Registro de Actividades usando el Archivo appsettings.json**

> **_NOTA:_** Esta opción es preferida para aplicaciones .NET Core.

El registro en [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) se puede habilitar con los siguientes pasos y ejemplos de código:

1. Agregue un archivo de configuración appsettings.json a un proyecto de C#, si aún no se ha agregado.
2. Asegúrese de que el archivo del proyecto contenga las siguientes líneas en la sección ItemGroup.

   ```xml
      <Content Include="appsettings.json">
          <CopyToOutputDirectory>Always</CopyToOutputDirectory>
      </Content>
   ```

3. Luego, agregue el siguiente contenido al archivo appsettings.json.

   ```json
      {
        "Pop3DiagnosticLog": "Pop3.log",
        "Pop3DiagnosticLog_UseDate": true
      }
   ```

Las dos propiedades mencionadas arriba son:

- **Pop3DiagnosticLog** - especifica la ruta relativa o absoluta al archivo de registro.

- **Pop3DiagnosticLog_UseDate** - especifica si se debe agregar una representación en forma de cadena de la fecha actual al nombre del archivo de registro.

## **Habilitar el Registro de Actividades en Código de Programa**

También puede habilitar el registro inmediatamente en el código.

> **_NOTA:_** incluso si ya ha habilitado el registro utilizando archivos de configuración, esta opción se aplicará.

El registro en [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) se puede habilitar con los siguientes pasos y ejemplos de código:

1. Cree un [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/).
2. Establezca la ruta al archivo de registro utilizando la propiedad [LogFileName](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/logfilename/).
3. Establezca la propiedad [UseDateInLogFileName](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usedateinlogfilename/) si es necesario.

```cs
   using (var client = new Pop3Client("su servidor pop3", 995, "su nombre de usuario", "su contraseña"))
{
    // Establecer modo de seguridad
    client.SecurityOptions = SecurityOptions.Auto;

    // Establecer la ruta al archivo de registro utilizando la propiedad LogFileName.
    client.LogFileName = @"C:\Aspose.Email.Pop3.log";

    // Establecer la propiedad UseDateInLogFileName si es necesario.
    client.UseDateInLogFileName = false;
}
```

## **Habilitar el Registro de Actividades usando el Archivo App.config**

La actividad de [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) se puede registrar modificando las secciones configSections en el archivo de configuración. Los siguientes son los pasos para realizar el registro de diagnóstico:

1. Agregue un **sectionGroup** llamado "applicationSettings".
1. Agregue una **section** llamada "Aspose.Email.Properties.Settings".
1. Incluya la configuración ImapDiagonosticLog donde se define el nombre del archivo en **applicationSettings/Aspose.Email.Properties.Settings**.

Aquí hay un ejemplo de una aplicación de formularios que utiliza [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) para procesar correos. Esta actividad se registra modificando el archivo App.config.

- Cree una aplicación basada en formularios con un solo botón. Agregue el siguiente código de ejemplo para el clic del botón:

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-Pop3ClientActivityLogging-Pop3ClientActivityLogging.cs" >}}

- Agregue una referencia a Aspose.Email.
- Ahora agregue el archivo App.Config y modifíquelo para que el contenido del archivo sea el siguiente:

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-App-Pop3ClientActivityLogging.config" >}}

Para C# .NET use la siguiente opción

|![todo:image_alt_text](pop3client-activity-logging_1.png)|
| :- |
Para VB .NET use la siguiente opción

|![todo:image_alt_text](pop3client-activity-logging_1.png)| |![todo:image_alt_text](pop3client-activity-logging_3.png)| |
| :- | :- | :- | :- |

|![todo:image_alt_text](pop3client-activity-logging_4.png)| |
| :- | :- |

- Ejecute el código y luego observe la carpeta Log. Se generará el siguiente archivo.

|![todo:image_alt_text](pop3client-activity-logging_5.png)| |
| :- | :- |