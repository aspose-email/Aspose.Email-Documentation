---
title: "Trabalhando com Sinais de Mensagem no Servidor"
url: /pt/python-net/trabalhando-com-sinais-de-mensagem-no-servidor/
weight: 60
type: docs
---


## **Alterando os Sinais de Mensagem**
Você pode alterar os sinais de mensagem usando o método ChangeMessageFlags(). Este método aceita dois parâmetros.

1. O número de sequência da mensagem ou ID único.
1. MessageFlag.

Os seguintes sinais podem ser definidos:

- Respondido
- Deletado
- Rascunho
- Vazio
- Marcado
- Lido
- Recente
### **Definindo Sinais de Mensagem**
O seguinte trecho de código mostra como alterar os sinais de mensagem em um servidor IMAP com Aspose.Email.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-SettingMessageFlags-SettingMessageFlags.py" >}}

### **Removendo Sinais de Mensagem**

A API também oferece o método 'remove_message_flags' da classe [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) para remover sinais de sistema predefinidos, como \Seen (que corresponde à mensagem sendo lida), \Answered (mensagem foi respondida), \Flagged (mensagem é marcada como importante), \Deleted (mensagem é marcada para exclusão) e \Draft (mensagem é salva como rascunho), bem como sinais de palavras-chave personalizados definidos pelos usuários. O método aceita os seguintes parâmetros: identificador único (UID) ou número de sequência da mensagem junto com os sinais que você deseja remover. O exemplo de código abaixo demonstra como remover o sinal 'is_read' com apenas uma linha de código:

```py
# Remover o sinal da mensagem
client.remove_message_flags(1, ae.clients.imap.ImapMessageFlags.is_read)
```
### **Definindo Sinais Personalizados**
Você também pode definir sinais personalizados para uma mensagem usando o [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) da API. Seu método 'add_message_flags' proporciona a capacidade de definir sinais personalizados nas mensagens.

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

# Criar uma mensagem
message = ae.MailMessage("user@domain1.com", "user@domain2.com", "subject", "message")

# Adicionar a mensagem à caixa de correio
uid = client.append_message(ae.clients.imap.ImapFolderInfo.IN_BOX, message)

# Adicionar sinais personalizados à mensagem adicionada
client.add_message_flags(uid, ae.clients.imap.ImapMessageFlags.keyword("custom1") | ae.clients.imap.ImapMessageFlags.keyword("custom1_0"))

# Recuperar as mensagens para verificar a presença do sinal personalizado
client.select_folder(ae.clients.imap.ImapFolderInfo.IN_BOX)

messageInfos = client.ListMessages()

for inf in messageInfos:
  flags = inf.flags.split()
  if inf.contains_keyword("custom1"):
        print("Palavra-chave encontrada")
```