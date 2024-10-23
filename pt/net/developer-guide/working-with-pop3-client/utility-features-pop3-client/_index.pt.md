---
title: "Recursos de Utilidade - Cliente POP3"
url: /pt/net/utility-features-pop3-client/
weight: 10
type: docs
---

## **Validar Credenciais do Servidor de Email**

O método [ValidateCredentials](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/validatecredentials) da API Aspose.Email torna possível a validação das credenciais do servidor de email sem enviar um email. Este método é responsável por verificar a autenticidade e validade das credenciais de email fornecidas, sendo utilizado para autenticação ao conectar-se ao servidor.

Ele verifica se as credenciais de email, como nome de usuário e senha, são válidas e se é possível para o cliente estabelecer uma conexão bem-sucedida com o servidor. Essa verificação de credenciais ajuda a garantir que o cliente possa acessar com segurança a conta de email e realizar várias operações, como receber email.

```cs
using (Pop3Client client = new Pop3Client(server.Pop3Url, server.Pop3Port, "userName", "password", SecurityOptions.Auto))
{
    client.Timeout = 4000;
   
    if (client.ValidateCredentials())
    {
        //to do something
    }
}
```

Para realizar uma operação assíncrona, também há uma versão do método [ValidateCredentialsAsync](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/validatecredentialsasync/).