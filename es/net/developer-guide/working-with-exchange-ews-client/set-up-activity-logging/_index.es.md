---
title: "Configurar el registro de actividades"
url: /es/net/set-up-activity-logging/
weight: 41
type: docs
---

El registro se usa para depurar, así como para recopilar y analizar información de trabajo sobre la aplicación. Los archivos de registro contienen información del sistema sobre el funcionamiento de la aplicación cliente.

## **Habilitar el registro de actividades mediante el archivo appsettings.json**

> **_NOTE:_** Esta opción es la preferida para las aplicaciones.NET Core.

Los siguientes son los pasos para habilitar el inicio de sesión [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/).

- Agregue un archivo de configuración appsettings.json a un proyecto de C#, si no se ha agregado antes. Asegúrese de que el archivo del proyecto contenga las siguientes líneas en la sección ItemGroup:

  ```xml
  <Content Include="appsettings.json">
      <CopyToOutputDirectory>Always</CopyToOutputDirectory>
  </Content>
  ```

- A continuación, añada el siguiente contenido al archivo appsettings.json.

  ```json
  {
    "EWSDiagnosticLog": "ews.log",
    "EWSDiagnosticLog_UseDate": true
  }
  ```

Hay dos propiedades:

- `EWSDiagnosticLog` - Especifica la ruta relativa o absoluta al archivo de registro.
- `EWSDiagnosticLog_UseDate` - especifica si se debe añadir una representación en cadena de la fecha actual al nombre del archivo de registro.

## **Habilitar el registro de actividades en el código del programa**

También puede activar el registro de forma inmediata en el código.

> **_NOTE:_** aunque ya haya habilitado el registro mediante archivos de configuración, se aplicará esta opción.

Los siguientes son los pasos para habilitar el inicio de sesión en EWSClient.

- Crea un [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/).
- Establezca la ruta al archivo de registro mediante el [LogFileName](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeclientbase/logfilename/) property.
- Configure el [UseDateInLogFileName](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeclientbase/usedateinlogfilename/) propiedad si es necesario.

```csharp
using (var client = EWSClient.GetEWSClient("https://outlook.office365.com/EWS/Exchange.asmx", credentials))
{
  client.LogFileName = @"Aspose.Email.EWS.log";
  client.UseDateInLogFileName = false;
}
```

## **Habilitar el registro de actividades mediante el archivo App.config**

Esta opción es adecuada para aplicaciones en las que `app.config` es la forma preferida de mantener la configuración de la aplicación.

Los siguientes son los pasos para habilitar el inicio de sesión [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/).

- Agregue un archivo de configuración de la aplicación a un proyecto de C#, si no se ha agregado antes.
- Agregue el siguiente contenido al archivo de configuración.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" >
      <section name="Aspose.Email.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" requirePermission="false" />
    </sectionGroup>
  </configSections>
    <applicationSettings>
        <Aspose.Email.Properties.Settings>
            <setting name="EWSDiagnosticLog" serializeAs="String">
                <value>..\..\..\Log\Aspose.Email.EWS.log</value>
            </setting>
            <setting name="EWSDiagnosticLog_UseDate" serializeAs="String">
                <value>False</value>
            </setting>
        </Aspose.Email.Properties.Settings>
    </applicationSettings>
</configuration>
```

Hay dos secciones de configuración:

- `EWSDiagnosticLog` - Especifica la ruta relativa o absoluta al archivo de registro.
- `EWSDiagnosticLog_UseDate` - especifica si se debe añadir una representación en cadena de la fecha actual al nombre del archivo de registro.
