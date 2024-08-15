---
title: "Registro de actividad de SMTPClient"
url: /es/net/smtpclient-activity-logging/
weight: 26
type: docs
---

El registro de actividades se usa para depurar, así como para recopilar y analizar información de trabajo sobre el cliente SMTP.

## **Habilitar el registro de actividades mediante el archivo appsettings.json**

> **_NOTE:_** Esta opción es la preferida para las aplicaciones.NET Core.

Iniciar sesión [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) se puede habilitar con los siguientes pasos y ejemplos de código:

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
        "SmtpDiagnosticLog": "smtp.log",
        "SmtpDiagnosticLog_UseDate": true
      }
   ```

Las dos propiedades mencionadas anteriormente son:

- **SmtpDiagnosticLog** - especifica la ruta relativa o absoluta al archivo de registro.

- **SmtpDiagnosticLog_UseDate** - especifica si se debe añadir una representación en cadena de la fecha actual al nombre del archivo de registro.

## **Habilitar el registro de actividades en el código del programa**

También puede activar el registro de forma inmediata en el código.

> **_NOTE:_** aunque ya haya habilitado el registro mediante archivos de configuración, se aplicará esta opción.

Iniciar sesión [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) se puede habilitar con los siguientes pasos y ejemplos de código:

1. Crea un [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/).
2. Establezca la ruta al archivo de registro mediante el [LogFileName](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/logfilename/) property.
3. Configure el [UseDateInLogFileName](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usedateinlogfilename/) propiedad si es necesario.

```cs
   using (var client = new SmtpClient("your smtp server"))
   {
       // Set username, password, port, and security options
       client.Username = "your username";
       client.Password = "your password";
       client.Port = 465;
       client.SecurityOptions = SecurityOptions.SSLImplicit;
  
       // Establezca la ruta al archivo de registro mediante el LogFileName property.
       client.LogFileName = @"C:\Aspose.Email.Smtp.log";
      
       // Configure el UseDateInLogFileName propiedad si es necesario.
       client.UseDateInLogFileName = false;
  
       var eml = new MailMessage("from address", "to address", "this is a test subject", "this is a test body");
  
       client.Send(eml);
   }
```

## **Habilitar el registro de actividades mediante el archivo App.config**

La actividad del cliente SMTP se puede registrar modificando las ConfigSections del archivo de configuración. El registro de diagnósticos se puede realizar con los siguientes pasos:

1. Agregue un grupo de secciones llamado «ApplicationSettings».
2. Agregue una sección llamada «Aspose.Email.Properties.Settings».
3. Incluya la configuración con el nombre SMTPDiagonosticLog donde se define el nombre del archivo en ApplicationSettings/Aspose.Email.Properties.Settings

Aquí hay un ejemplo de aplicación basada en formularios que utiliza [SmtpClient](https://apireference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient) para enviar un correo electrónico. Toda esta actividad se registra modificando el archivo App.config. Cree una aplicación de formulario con un solo botón. Agregue el siguiente código para hacer clic en el botón:

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-SMTPClientActivityLogging-SMTPClientActivityLogging.cs" >}}

4. Agregar referencia a Aspose.Email.

|![todo:image_alt_text](utility-features-smtp-client_1.png)|
|: - |

5. Agregue el archivo App.Config y modifíquelo de manera que el contenido del archivo sea el siguiente

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-App-SMTPClientActivityLogging.config" >}}

- Para C# .NET, utilice la siguiente opción

|![todo:image_alt_text](utility-features-smtp-client_2.png)|
|: - |

- Para VB.NET, utilice la siguiente opción

|![todo:image_alt_text](utility-features-smtp-client_2.png)| |![todo:image_alt_text](utility-features-smtp-client_4.png)|
|: - |: - |: - |

|![todo:image_alt_text](utility-features-smtp-client_5.png)|
|: - |

6. Ejecute el código y, a continuación, observe la carpeta de depuración. Se generará el siguiente archivo.

|![todo:image_alt_text](utility-features-smtp-client_6.png)|
|: - |
