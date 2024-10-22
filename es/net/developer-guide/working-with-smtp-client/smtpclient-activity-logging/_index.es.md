---
title: "Registro de Actividad de SmtpClient"
url: /es/net/smtpclient-activity-logging/
weight: 26
type: docs
---

El registro de actividades se utiliza para depuración, así como para recopilar y analizar información de trabajo sobre el cliente SMTP.

## **Habilitar el Registro de Actividad utilizando el Archivo appsettings.json**

> **_NOTA:_** Esta opción es preferida para aplicaciones .NET Core.

El registro en [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) se puede habilitar con los siguientes pasos y ejemplos de código:

1. Agregue un archivo de configuración appsettings.json a un proyecto C#, si no se ha agregado antes.
2. Asegúrese de que el archivo del proyecto contenga las siguientes líneas en la sección ItemGroup.

   ```xml
      <Content Include="appsettings.json">
          <CopyToOutputDirectory>Always</CopyToOutputDirectory>
      </Content>
   ```

3. Luego, agregue el siguiente contenido al archivo appsettings.json.

   ```json
      {
        "SmtpDiagnosticLog": "smtp.log",
        "SmtpDiagnosticLog_UseDate": true
      }
   ```

Las dos propiedades mencionadas anteriormente son:

- **SmtpDiagnosticLog** - especifica la ruta relativa o absoluta al archivo de registro.

- **SmtpDiagnosticLog_UseDate** - especifica si se debe agregar una representación de cadena de la fecha actual al nombre del archivo de registro.

## **Habilitar el Registro de Actividad en el Código del Programa**

También puede habilitar el registro de inmediato en el código.

> **_NOTA:_** incluso si ya ha habilitado el registro mediante archivos de configuración, esta opción se aplicará.

El registro en [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) se puede habilitar con los siguientes pasos y ejemplos de código:

1. Cree un [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/).
2. Establezca la ruta al archivo de registro utilizando la propiedad [LogFileName](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/logfilename/).
3. Establezca la propiedad [UseDateInLogFileName](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usedateinlogfilename/) si es necesario.

```cs
   using (var client = new SmtpClient("su servidor smtp"))
   {
       // Establecer nombre de usuario, contraseña, puerto y opciones de seguridad
       client.Username = "su nombre de usuario";
       client.Password = "su contraseña";
       client.Port = 465;
       client.SecurityOptions = SecurityOptions.SSLImplicit;
   
       // Establecer la ruta al archivo de registro utilizando la propiedad LogFileName.
       client.LogFileName = @"C:\Aspose.Email.Smtp.log";
       
       // Establecer la propiedad UseDateInLogFileName si es necesario.
       client.UseDateInLogFileName = false;
   
       var eml = new MailMessage("dirección de origen", "dirección de destino", "este es un asunto de prueba", "este es un cuerpo de prueba");
   
       client.Send(eml);
   }
```

## **Habilitar el Registro de Actividad utilizando el Archivo App.config**

La actividad del cliente SMTP se puede registrar modificando las secciones de configuración en el archivo de configuración. El registro de diagnóstico se puede realizar con los siguientes pasos:

1. Agregue un sectionGroup llamado "applicationSettings".
2. Agregue una sección llamada "Aspose.Email.Properties.Settings".
3. Incluya la configuración con el nombre SmtpDiagonosticLog donde se define el nombre del archivo en applicationSettings/Aspose.Email.Properties.Settings.

Aquí hay un ejemplo de una aplicación basado en formularios que utiliza [SmtpClient](https://apireference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient) para enviar un correo electrónico. Toda esta actividad se registra modificando el archivo App.config. Cree una aplicación de formulario con un solo botón. Agregue el siguiente código para el clic del botón:

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-SMTPClientActivityLogging-SMTPClientActivityLogging.cs" >}}

4. Agregue referencia a Aspose.Email.

|![todo:image_alt_text](utility-features-smtp-client_1.png)|
| :- |

5. Agregue el archivo App.Config y modifíquelo de tal manera que el contenido del archivo sea como sigue

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-App-SMTPClientActivityLogging.config" >}}

- Para C# .NET use la siguiente opción

|![todo:image_alt_text](utility-features-smtp-client_2.png)|
| :- |

- Para VB .NET use la siguiente opción

|![todo:image_alt_text](utility-features-smtp-client_2.png)| |![todo:image_alt_text](utility-features-smtp-client_4.png)|
| :- | :- | :- |

|![todo:image_alt_text](utility-features-smtp-client_5.png)|
| :- |

6. Ejecute el código y luego observe la carpeta de depuración. Se generará el siguiente archivo.

|![todo:image_alt_text](utility-features-smtp-client_6.png)|
| :- |