---
title: "Configurar Registro de Actividades"
url: /es/net/configurar-registro-de-actividades/
weight: 41
type: docs
---

El registro se utiliza para la depuración, así como para recopilar y analizar información de trabajo sobre la aplicación. Los archivos de registro contienen información del sistema sobre la operación de la aplicación cliente.

## **Habilitar el Registro de Actividades usando el Archivo appsettings.json**

> **_NOTA:_** Esta opción es preferida para aplicaciones .NET Core.

Los siguientes son los pasos para habilitar el registro en [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/).

- Agregue un archivo de configuración appsettings.json a un proyecto de C#, si no se ha agregado antes. Asegúrese de que el archivo del proyecto contenga las siguientes líneas en la sección ItemGroup:

  ```xml
  <Content Include="appsettings.json">
      <CopyToOutputDirectory>Always</CopyToOutputDirectory>
  </Content>
  ```

- Luego, agregue el siguiente contenido al archivo appsettings.json.

  ```json
  {
    "EWSDiagnosticLog": "ews.log",
    "EWSDiagnosticLog_UseDate": true
  }
  ```

Hay dos propiedades:

- `EWSDiagnosticLog` - Especifica la ruta relativa o absoluta al archivo de registro.
- `EWSDiagnosticLog_UseDate` - especifica si se debe agregar una representación en cadena de la fecha actual al nombre del archivo de registro.

## **Habilitar el Registro de Actividades en el Código del Programa**

También puede habilitar el registro inmediatamente en el código.

> **_NOTA:_** incluso si ya ha habilitado el registro mediante archivos de configuración, esta opción se aplicará.

Los siguientes son los pasos para habilitar el registro en EWSClient.

- Cree un [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/).
- Establezca la ruta al archivo de registro usando la propiedad [LogFileName](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeclientbase/logfilename/).
- Establezca la propiedad [UseDateInLogFileName](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeclientbase/usedateinlogfilename/) si es necesario.

```csharp
using (var client = EWSClient.GetEWSClient("https://outlook.office365.com/EWS/Exchange.asmx", credentials))
{
  client.LogFileName = @"Aspose.Email.EWS.log";
  client.UseDateInLogFileName = false;
}
```

## **Habilitar el Registro de Actividades usando el Archivo App.config**

Esta opción es adecuada para aplicaciones donde `app.config` es la forma preferida de mantener la configuración de la aplicación.

Los siguientes son los pasos para habilitar el registro en [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/).

- Agregue un archivo de configuración de aplicación a un proyecto de C#, si no se ha agregado antes.
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
- `EWSDiagnosticLog_UseDate` - especifica si se debe agregar una representación en cadena de la fecha actual al nombre del archivo de registro.