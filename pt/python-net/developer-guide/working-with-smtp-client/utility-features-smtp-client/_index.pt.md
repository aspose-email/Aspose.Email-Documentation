---
title: "Recursos de Utilidade - Cliente SMTP"
url: /pt/python-net/utility-features-smtp-client/
weight: 30
type: docs
---


## **Listando Servidores de Extensão usando o Cliente Smtp**
O Pop3Client da Aspose.Email permite que você recupere as extensões do servidor que um servidor suporta, como IDLE, UNSELECT, QUOTA, etc. Isso ajuda a identificar a disponibilidade de uma extensão antes de usar o cliente para essa funcionalidade específica. O método GetCapabilities() retorna os tipos de extensão suportados na forma de um array de strings.
### **Recuperando Extensões do Servidor**
O seguinte trecho de código mostra como recuperar extensões do servidor.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-RetrieveSMTPServerExtensions-RetrieveSMTPServerExtensions.py" >}}

## **Validar Credenciais do Servidor de Email Sem Enviar Email**

O método 'validate_credentials()' da classe [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) é usado para verificar a validade das credenciais fornecidas, estabelecendo uma conexão com o servidor SMTP. Se as credenciais forem válidas e a conexão for bem-sucedida, outras ações poderão ser realizadas. O seguinte exemplo de código pode ser usado para verificar as credenciais fornecidas para autenticação com o servidor SMTP sem enviar um email:

```py
import aspose.email as ae

client = ae.clients.smtp.SmtpClient("Url", port, "username", "password", ae.clients.SecurityOptions.AUTO)
client.timeout = 4000

if client.validate_credentials():
  # to do something
```