---
title: "Registro de Atividades do ImapClient"
url: /pt/net/imapclient-activity-logging/
weight: 90
type: docs
---

O registro de atividades é usado para depuração, bem como para coletar e analisar informações de funcionamento sobre o cliente IMAP.

## **Ativar o Registro de Atividades usando o arquivo appsettings.json**

> **_NOTA:_** Esta opção é preferida para aplicativos .NET Core.

O registro no [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) pode ser ativado com os seguintes passos e exemplos de código:

1. Adicione um arquivo de configuração appsettings.json a um projeto C#, se ainda não tiver sido adicionado.
2. Certifique-se de que o arquivo do projeto contenha as seguintes linhas na seção ItemGroup.

   ```xml
      <Content Include="appsettings.json">
          <CopyToOutputDirectory>Always</CopyToOutputDirectory>
      </Content>
   ```

3. Em seguida, adicione o seguinte conteúdo ao arquivo appsettings.json.

   ```json
      {
        "ImapDiagnosticLog": "imap.log",
        "ImapDiagnosticLog_UseDate": true
      }
   ```

As duas propriedades mencionadas acima são:

- **ImapDiagnosticLog** - especifica o caminho relativo ou absoluto para o arquivo de log.

- **ImapDiagnosticLog_UseDate** - especifica se deve adicionar uma representação em string da data atual ao nome do arquivo de log.

## **Ativar o Registro de Atividades no Código do Programa**

Você também pode ativar o registro imediatamente no código.

> **_NOTA:_** mesmo que você já tenha ativado o registro usando arquivos de configuração, esta opção será aplicada.

O registro no [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) pode ser ativado com os seguintes passos e exemplos de código:

1. Crie um [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/).
2. Defina o caminho para o arquivo de log usando a propriedade [LogFileName](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/logfilename/).
3. Defina a propriedade [UseDateInLogFileName](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usedateinlogfilename/) se necessário.

```cs
   using (var client = new ImapClient("seu servidor imap", 993, "seu nome de usuário", "sua senha"))
{
    // Defina o modo de segurança
    client.SecurityOptions = SecurityOptions.Auto;

    // Defina o caminho para o arquivo de log usando a propriedade LogFileName.
    client.LogFileName = @"C:\Aspose.Email.IMAP.log";

    // Defina a propriedade UseDateInLogFileName se necessário.
    client.UseDateInLogFileName = false;
}
```

## **Ativar o Registro de Atividades usando o arquivo App.config**

A atividade do [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) pode ser registrada modificando as configSections no arquivo de configuração. A seguir estão os passos para realizar o registro de diagnósticos:

1. Adicione um **sectionGroup** chamado "applicationSettings".
1. Adicione uma **section** chamada "Aspose.Email.Properties.Settings".
1. Inclua a configuração ImapDiagonosticLog onde o nome do arquivo é definido em **applicationSettings/Aspose.Email.Properties.Settings**.

Aqui está um exemplo de aplicação de formulário que usa [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) para processar e-mails. Esta atividade inteira é registrada modificando o arquivo App.config.

- Crie uma aplicação baseada em formulário com um único botão. Adicione o seguinte código de exemplo para o clique do botão:

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-ImapClientActivityLogging-ImapClientActivityLogging.cs" >}}

- Adicione uma referência ao Aspose.Email.

|![todo:image_alt_text](imapclient-activity-logging_1.png)| |
| :- | :- |

- Agora adicione o arquivo App.Config e modifique-o para que o conteúdo do arquivo seja o seguinte:

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-ImapClientActivityLogging-ImapClientActivityLogging.xml" >}}

Para C# .NET, use a seguinte opção

|![todo:image_alt_text](imapclient-activity-logging_2.png)| |
| :- | :- |
Para VB .NET, use a seguinte opção

|![todo:image_alt_text](imapclient-activity-logging_2.png)| |![todo:image_alt_text](imapclient-activity-logging_4.png)| |
| :- | :- | :- | :- |

|![todo:image_alt_text](imapclient-activity-logging_5.png)| |
| :- | :- |

- Execute o código e, em seguida, observe a pasta Log. O seguinte arquivo será gerado.

|![todo:image_alt_text](imapclient-activity-logging_6.png)| |
| :- | :- |