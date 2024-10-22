---
title: "Registro de Atividade do Pop3Client"
url: /pt/net/pop3client-activity-logging/
weight: 40
type: docs
---

O registro de atividade é utilizado para depuração, bem como para coletar e analisar informações de trabalho sobre o cliente POP3.

## **Ativar Registro de Atividade usando o Arquivo appsettings.json**

> **_NOTA:_** Esta opção é preferida para aplicações .NET Core.

O registro no [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) pode ser ativado com os seguintes passos e exemplos de código:

1. Adicione um arquivo de configuração appsettings.json a um projeto C#, caso ainda não tenha sido adicionado.
2. Certifique-se de que o arquivo do projeto contenha as seguintes linhas na seção ItemGroup.

   ```xml
      <Content Include="appsettings.json">
          <CopyToOutputDirectory>Always</CopyToOutputDirectory>
      </Content>
   ```

3. Em seguida, adicione o seguinte conteúdo ao arquivo appsettings.json.

   ```json
      {
        "Pop3DiagnosticLog": "Pop3.log",
        "Pop3DiagnosticLog_UseDate": true
      }
   ```

As duas propriedades mencionadas acima são:

- **Pop3DiagnosticLog** - especifica o caminho relativo ou absoluto para o arquivo de log.

- **Pop3DiagnosticLog_UseDate** - especifica se deve ser adicionada uma representação de string da data atual ao nome do arquivo de log.

## **Ativar Registro de Atividade no Código do Programa**

Você também pode ativar o registro imediatamente no código.

> **_NOTA:_** mesmo que você já tenha ativado o registro usando arquivos de configuração, esta opção será aplicada.

O registro no [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) pode ser ativado com os seguintes passos e exemplos de código:

1. Crie um [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/).
2. Defina o caminho para o arquivo de log usando a propriedade [LogFileName](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/logfilename/).
3. Defina a propriedade [UseDateInLogFileName](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usedateinlogfilename/) se necessário.

```cs
   using (var client = new Pop3Client("seu servidor pop3", 995, "seu usuário", "sua senha"))
{
    // Defina o modo de segurança
    client.SecurityOptions = SecurityOptions.Auto;

    // Defina o caminho para o arquivo de log usando a propriedade LogFileName.
    client.LogFileName = @"C:\Aspose.Email.Pop3.log";

    // Defina a propriedade UseDateInLogFileName se necessário.
    client.UseDateInLogFileName = false;
}
```

## **Ativar Registro de Atividade usando o Arquivo App.config**

A atividade do [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) pode ser registrada modificando as configSections no arquivo de configuração. A seguir estão os passos para realizar o registro de diagnósticos:

1. Adicione um **sectionGroup** chamado "applicationSettings".
1. Adicione uma **section** chamada "Aspose.Email.Properties.Settings".
1. Inclua a definição de configuração ImapDiagonosticLog onde o nome do arquivo é definido em **applicationSettings/Aspose.Email.Properties.Settings**.

Aqui está uma aplicação de exemplo que usa [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) para processar e-mails. Toda essa atividade é registrada modificando o arquivo App.config.

- Crie uma aplicação baseada em formulário com um único botão. Adicione o seguinte código de exemplo ao clique do botão:

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-Pop3ClientActivityLogging-Pop3ClientActivityLogging.cs" >}}

- Adicione uma referência ao Aspose.Email.
- Agora adicione o arquivo App.Config e modifique-o para que o conteúdo do arquivo seja o seguinte:

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-App-Pop3ClientActivityLogging.config" >}}

Para C# .NET use a seguinte opção

|![todo:image_alt_text](pop3client-activity-logging_1.png)|
| :- |
Para VB .NET use a seguinte opção

|![todo:image_alt_text](pop3client-activity-logging_1.png)| |![todo:image_alt_text](pop3client-activity-logging_3.png)| |
| :- | :- | :- | :- |

|![todo:image_alt_text](pop3client-activity-logging_4.png)| |
| :- | :- |

- Execute o código e, em seguida, observe a pasta Log. O seguinte arquivo será gerado.

|![todo:image_alt_text](pop3client-activity-logging_5.png)| |
| :- | :- |