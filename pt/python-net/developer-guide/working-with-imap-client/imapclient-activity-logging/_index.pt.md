---
title: "Registro de Atividade do ImapClient em Python"
url: /pt/python-net/imapclient-activity-logging/
weight: 40
type: docs
---


## **Ativar Registro de Atividade**

O registro de atividade envolve a gravação de conexões com o servidor, detalhes de transmissão de mensagens enviadas e recebidas, mensagens de erro durante o processamento de emails e qualquer outra ação realizada pelo cliente ou servidor. Para rastrear a atividade do cliente IMAP e interações com o servidor, use o seguinte exemplo de código que utiliza a propriedade 'log_file_name' da classe [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) para registrar as informações no arquivo de log especificado:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

# Defina o caminho para o arquivo de log usando a propriedade LogFileName.
client.log_file_name = "C:\\Aspose.Email.IMAP.log"
# Defina a propriedade UseDateInLogFileName se necessário.
client.use_date_in_log_file_name = False
```