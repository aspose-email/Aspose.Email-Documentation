---
title: "Recursos de Utilidade - Cliente SMTP"
url: /pt/net/utility-features-smtp-client/
weight: 30
type: docs
---

# Recursos de Utilidade - Cliente SMTP

## **Listando Servidores de Extensão usando o Cliente SMTP**

Aspose.Email [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) permite recuperar as extensões que um servidor suporta, como IDLE, UNSELECT, QUOTA, etc. Isso ajuda a identificar a disponibilidade de uma extensão antes de usar o cliente para essa funcionalidade específica. O método [GetCapabilities()](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/getcapabilities/#getcapabilities) retorna os tipos de extensões suportados na forma de um array de strings.

### **Recuperando Extensões de Servidor**

O seguinte trecho de código mostra como recuperar extensões de servidor.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-RetreiveServerExtensions-RetreiveSMTPServerExtensions.cs" >}}

## **Trabalhando com Mensagens Assinadas**

A API Aspose.Email fornece a capacidade de criar mensagens assinadas usando certificados. O método [AttachSignature](https://reference.aspose.com/email/net/aspose.email/mailmessage/attachsignature/#attachsignature/) da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) pode ser usado para assinar uma mensagem para salvá-la ou até mesmo enviá-la usando o [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/).

### **Assinar uma Mensagem**

O seguinte trecho de código mostra como assinar uma mensagem.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-SignAMessage-SignAMessage.cs" >}}

### **Usando a Opção de Certificado Destacado**

Clientes de email baseados na web podem não conseguir exibir o conteúdo do corpo de uma mensagem assinada. Isso pode ser resolvido destacando o certificado antes de enviá-lo para clientes de email baseados na web. A flag destacada no método sobrecarregado de [AttachSignature](https://reference.aspose.com/email/net/aspose.email/mailmessage/attachsignature/#attachsignature/) pode ser usada para alcançar isso. Se definido como **true**, o certificado é destacado do email e vice-versa. Para ver o corpo da Mensagem Assinada em clientes baseados na web, você precisa criar um [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) com assinatura destacada. O seguinte trecho de código mostra como usar a opção de certificado destacado.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-UsingDetachedCertificate-UsingDetachedCertificate.cs" >}}

## **Validar Credenciais do Servidor de Email sem Enviar Email**

A API Aspose.Email fornece a capacidade de validar credenciais do servidor de email sem enviar um email. Isso pode ser alcançado com o método [ValidateCredentials](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/validatecredentials/) que é responsável por verificar a autenticidade e a correção das credenciais de email fornecidas, que normalmente são usadas para autenticação ao conectar-se ao servidor.

Ele verifica se as credenciais de email fornecidas, como nome de usuário e senha, são válidas e se o cliente pode estabelecer uma conexão bem-sucedida com o servidor. Essa verificação de credenciais ajuda a garantir que o cliente possa acessar a conta de email de forma segura e realizar várias operações, como enviar email.

```cs
using (SmtpClient client = new SmtpClient(server.SmtpUrl, server.SmtpPort, "username", "password", SecurityOptions.Auto))
{
    client.Timeout = 4000;
   
    if (client.ValidateCredentials())
    {
        //para fazer algo
    }
}
```

Também existe uma versão do método [ValidateCredentialsAsync](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/validatecredentialsasync/) para realizar uma operação assíncrona.