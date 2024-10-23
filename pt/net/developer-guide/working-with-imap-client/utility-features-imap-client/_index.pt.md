---
title: "Recursos de Utilidade - Cliente IMAP"
url: /pt/net/utility-features-imap-client/
weight: 100
type: docs
---

## **Validar Credenciais do Servidor de Email**

A API Aspose.Email permite a validação das credenciais do servidor de email sem enviar um email. O método [ValidateCredentials](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/validatecredentials) é responsável por verificar a autenticidade e validade das credenciais de email fornecidas, que normalmente são usadas para autenticar ao se conectar ao servidor.

Ele verifica se as credenciais de email fornecidas, como nome de usuário e senha, são válidas e se é possível para o cliente estabelecer uma conexão bem-sucedida com o servidor. Essa verificação de credenciais ajuda a garantir que o cliente possa acessar com segurança a conta de email e realizar várias operações, como receber emails.

```cs
using (ImapClient client = new ImapClient(server.ImapUrl, server.ImapPort, "username", "password", SecurityOptions.Auto))
{
    client.Timeout = 4000;
   
    if (client.ValidateCredentials())
    {
        //to do something
    }
}
```

Para uma operação assíncrona, também existe uma versão do método [ValidateCredentialsAsync](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/validatecredentialsasync).