---
title: "Configurar Registro de Atividades"
url: /pt/net/configurar-registro-de-atividades/
weight: 41
type: docs
---

O registro é usado para depuração, bem como para coletar e analisar informações de trabalho sobre a aplicação. Os arquivos de log contêm informações do sistema sobre o funcionamento da aplicação cliente.

## **Ativar Registro de Atividades usando o Arquivo appsettings.json**

> **_NOTA:_** Esta opção é preferida para aplicações .NET Core.

Os seguintes são os passos para ativar o registro em [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/).

- Adicione um arquivo de configuração appsettings.json a um projeto C#, se ainda não tiver sido adicionado. Certifique-se de que o arquivo do projeto contenha as seguintes linhas na seção ItemGroup:

  ```xml
  <Content Include="appsettings.json">
      <CopyToOutputDirectory>Always</CopyToOutputDirectory>
  </Content>
  ```

- Em seguida, adicione o seguinte conteúdo ao arquivo appsettings.json.

  ```json
  {
    "EWSDiagnosticLog": "ews.log",
    "EWSDiagnosticLog_UseDate": true
  }
  ```

Existem duas propriedades:

- `EWSDiagnosticLog` - Especifica o caminho relativo ou absoluto para o arquivo de log.
- `EWSDiagnosticLog_UseDate` - especifica se deve adicionar uma representação de string da data atual ao nome do arquivo de log.

## **Ativar Registro de Atividades no Código do Programa**

Você também pode ativar o registro imediatamente no código.

> **_NOTA:_** mesmo se você já tiver ativado o registro usando arquivos de configuração, esta opção será aplicada.

Os seguintes são os passos para ativar o registro em EWSClient.

- Crie um [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/).
- Defina o caminho para o arquivo de log usando a propriedade [LogFileName](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeclientbase/logfilename/).
- Defina a propriedade [UseDateInLogFileName](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeclientbase/usedateinlogfilename/) se necessário.

```csharp
using (var client = EWSClient.GetEWSClient("https://outlook.office365.com/EWS/Exchange.asmx", credentials))
{
  client.LogFileName = @"Aspose.Email.EWS.log";
  client.UseDateInLogFileName = false;
}
```

## **Ativar Registro de Atividades usando o Arquivo App.config**

Esta opção é adequada para aplicações onde `app.config` é a forma preferida de manter a configuração do aplicativo.

Os seguintes são os passos para ativar o registro em [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/).

- Adicione um arquivo de configuração da aplicação a um projeto C#, se ainda não tiver sido adicionado.
- Adicione o seguinte conteúdo ao arquivo de configuração.

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

Existem duas seções de configuração:

- `EWSDiagnosticLog` - Especifica o caminho relativo ou absoluto para o arquivo de log.
- `EWSDiagnosticLog_UseDate` - especifica se deve adicionar uma representação de string da data atual ao nome do arquivo de log.