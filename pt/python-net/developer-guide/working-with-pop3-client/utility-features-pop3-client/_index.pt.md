---
title: "Recursos de Utilidade - Cliente POP3"
url: /pt/python-net/utility-features-pop3-client/
weight: 30
type: docs
---

## **Validar Credenciais do Servidor de Email**

Aspose.Email fornece o método 'validate_credentials()' da classe [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/#pop3client-class) para verificar as credenciais (nome de usuário e senha) fornecidas pelo usuário para acessar um servidor de email POP3. Este método garante que as credenciais de login do usuário sejam precisas e válidas, permitindo que ele autentique com sucesso e acesse sua conta de email usando o protocolo POP3. Se as credenciais fornecidas estiverem incorretas, o método pode retornar um erro ou lançar uma exceção, indicando que o processo de login falhou.

O trecho de código abaixo demonstra o método de verificação fornecido pela API:

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("host", 995, "username", "password", ae.clients.SecurityOptions.AUTO)
client.timeout = 40000
if client.validate_credentials():
# to do something
```