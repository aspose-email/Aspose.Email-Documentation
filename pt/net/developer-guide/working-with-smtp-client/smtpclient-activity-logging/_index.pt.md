---
title: "Registro de Atividade do SmtpClient"
url: /pt/net/smtpclient-activity-logging/
weight: 26
type: docs
---

O registro de atividades é utilizado para depuração, bem como para coletar e analisar informações de funcionamento sobre o cliente SMTP.

## **Ativar Registro de Atividade usando o arquivo appsettings.json**

> **_NOTA:_** Esta opção é preferida para aplicações .NET Core.

O registro em [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) pode ser ativado com os seguintes passos e exemplos de código:

1. Adicione um arquivo de configuração appsettings.json a um projeto C#, se ainda não tiver sido adicionado.
2. Certifique-se de que o arquivo do projeto contém as seguintes linhas na seção ItemGroup.

   ```xml
      <Content Include="appsettings.json">
          <CopyToOutputDirectory>Always</CopyToOutputDirectory>
      </Content>
   ```

3. Em seguida, adicione o seguinte conteúdo ao arquivo appsettings.json.

   ```json
      {
        "SmtpDiagnosticLog": "smtp.log",
        "SmtpDiagnosticLog_UseDate": true
      }
   ```

As duas propriedades mencionadas acima são:

- **SmtpDiagnosticLog** - especifica o caminho relativo ou absoluto para o arquivo de log.

- **SmtpDiagnosticLog_UseDate** - especifica se deve adicionar uma representação em string da data atual ao nome do arquivo de log.

## **Ativar Registro de Atividade no Código do Programa**

Você também pode ativar o registro imediatamente no código.

> **_NOTA:_** mesmo que você já tenha ativado o registro usando arquivos de configuração, esta opção será aplicada.

O registro em [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) pode ser ativado com os seguintes passos e exemplos de código:

1. Crie um [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/).
2. Defina o caminho para o arquivo de log usando a propriedade [LogFileName](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/logfilename/).
3. Defina a propriedade [UseDateInLogFileName](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usedateinlogfilename/) se for necessário.

```cs
   using (var client = new SmtpClient("your smtp server"))
   {
       // Defina o nome de usuário, senha, porta e opções de segurança
       client.Username = "your username";
       client.Password = "your password";
       client.Port = 465;
       client.SecurityOptions = SecurityOptions.SSLImplicit;
   
       // Defina o caminho para o arquivo de log usando a propriedade LogFileName.
       client.LogFileName = @"C:\Aspose.Email.Smtp.log";
       
       // Defina a propriedade UseDateInLogFileName se for necessário.
       client.UseDateInLogFileName = false;
   
       var eml = new MailMessage("from address", "to address", "this is a test subject", "this is a test body");
   
       client.Send(eml);
   }
```

## **Ativar Registro de Atividade usando o arquivo App.config**

A atividade do cliente SMTP pode ser registrada modificando as configSections no arquivo de configuração. O registro de diagnóstico pode ser realizado com os seguintes passos:

1. Adicione um sectionGroup chamado "applicationSettings".
2. Adicione uma seção chamada "Aspose.Email.Properties.Settings".
3. Inclua a configuração com o nome SmtpDiagonosticLog onde o nome do arquivo é definido em applicationSettings/Aspose.Email.Properties.Settings.

Aqui está um exemplo de uma aplicação baseada em formulário que usa [SmtpClient](https://apireference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient) para enviar um e-mail. Toda essa atividade é registrada modificando o arquivo App.config. Crie uma aplicação de formulário com um único botão. Adicione o seguinte código para o clique do botão:

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-SMTPClientActivityLogging-SMTPClientActivityLogging.cs" >}}

4. Adicione uma referência ao Aspose.Email.

|![todo:image_alt_text](utility-features-smtp-client_1.png)|
| :- |

5. Adicione o arquivo App.Config e modifique-o de tal forma que o conteúdo do arquivo seja o seguinte

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-App-SMTPClientActivityLogging.config" >}}

- Para C# .NET use a seguinte opção

|![todo:image_alt_text](utility-features-smtp-client_2.png)|
| :- |

- Para VB .NET use a seguinte opção

|![todo:image_alt_text](utility-features-smtp-client_2.png)| |![todo:image_alt_text](utility-features-smtp-client_4.png)|
| :- | :- | :- |

|![todo:image_alt_text](utility-features-smtp-client_5.png)|
| :- |

6. Execute o código e, em seguida, observe a pasta de depuração. O seguinte arquivo será gerado.

|![todo:image_alt_text](utility-features-smtp-client_6.png)|
| :- |