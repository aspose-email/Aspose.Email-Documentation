---
title: "Registro de Atividades do SmtpClient"
url: /pt/python-net/smtpclient-activity-logging/
weight: 30
type: docs
---


## **Ativar Registro de Atividades no Código do Programa**

Aspose.Email possibilita registrar ou documentar sistematicamente atividades, eventos ou transações ao longo de um período de tempo. Também conhecido como registro de atividades, isso pode ser alcançado com as seguintes propriedades da classe [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class):

- A propriedade 'log_file_name' obtém ou define o nome do arquivo de log.
- A propriedade 'use_date_in_log_file_name' obtém ou define o valor que indica se a data deve ser usada no nome do arquivo de log.

O exemplo de código abaixo demonstra como ativar o registro de atividades no código do programa:

```py
import aspose.email as ae

# Defina o nome de usuário, senha, porta e opções de segurança
client = ae.clients.smtp.SmtpClient
client.host = "<HOST>"
client.username = "<USERNAME>"
client.password = "<PASSWORD>"
client.port = 587
client.security_options = ae.clients.SecurityOptions.SSL_EXPLICIT

# Defina o caminho para o arquivo de log usando a propriedade LogFileName
client.log_file_name = "C:\Aspose.Email.Smtp.log"

# Defina a propriedade UseDateInLogFileName se necessário.
client.use_date_in_log_file_name = False

eml = ae.MailMessage("endereço de remetente", "endereço de destinatário", "este é um assunto de teste", "este é um corpo de teste")
client.send(eml)
```