---
title: "Exclusão de Mensagens do Servidor POP3"
url: /pt/python-net/deleting-messages-from-pop3-server/
weight: 20
type: docs
---

Aspose.Email.Mail é um componente robusto que permite realizar operações personalizadas após certas ações. Aspose.Email.Mail dispara muitos eventos sobre os quais os usuários podem realizar operações. Este recurso proporciona aos usuários mais controle sobre seu aplicativo. Por exemplo, os usuários podem realizar as ações desejadas quando:

- Todos os emails em massa foram enviados.
- Uma mensagem está prestes a ser enviada.
- Um email foi completamente enviado.
- Quando um destinatário é rejeitado pelo servidor SMTP.

Caixas de correio POP3 residem em um servidor POP3. O email nessas caixas de correio pode ser recuperado para o seu PC pelo Aspose.Email.Pop3.Pop3Client. O namespace Pop3Client utiliza o protocolo POP3 para copiar as mensagens de email de sua caixa de correio POP3 para o seu PC. Uma vez que o email tenha sido recuperado, você não precisa estar conectado à internet enquanto ele está sendo lido, pois você pode ler o email recuperado em seu PC. Se você não precisar ou quiser uma cópia de algumas mensagens de email mantidas no servidor POP3, você pode excluí-las. Esta seção mostra como excluir emails usando o namespace Pop3Client.
## **Excluir um Email por Índice**
O seguinte trecho de código exclui todas as mensagens de um caixa de correio uma a uma, com base em seu índice. O índice nunca deve ser <=0 em Pop3Client.DeleteMessage.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-DeleteEmailByIndex-DeleteEmailByIndex.py" >}}
## **Excluir Todos os Emails**
Também podemos chamar Pop3Client.DeleteAllMessages() para excluir todas as mensagens. O seguinte trecho de código mostra como excluir todos os emails.

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("imap.example.com", "username", "password")

# Excluir todas as mensagens
client.delete_messages()
```

Se a conexão com o servidor POP3 for interrompida imediatamente após as operações de exclusão, você não poderá mais chamar Pop3Client.CancelDeletes() para fazer as ações que desejar.
## **Cancelar Exclusões**
Pop3Client.UndeleteMessages pode ser usado para cancelar a exclusão de mensagens de email. O seguinte trecho de código mostra como cancelar exclusões.

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("imap.example.com", "username", "password")

# Cancelar exclusões
client.undelete_messages()
```