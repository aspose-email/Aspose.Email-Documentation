---
title: "Excluindo Mensagens do Servidor POP3"
url: /pt/net/deleting-messages-from-pop3-server/
weight: 20
type: docs
---


Aspose.Email é um componente robusto que permite realizar operações personalizadas após certas ações. Aspose.Email suporta muitos eventos sobre os quais os usuários podem realizar operações. Esse recurso fornece aos usuários mais controle sobre seu aplicativo. Por exemplo, os usuários podem realizar as ações desejadas quando:

- Todos os e-mails em massa foram enviados.
- Uma mensagem está prestes a ser enviada.
- Um e-mail é completamente enviado.
- Quando um destinatário é rejeitado pelo servidor SMTP.

As caixas de correio POP3 residem em um servidor POP3. Os e-mails nessas caixas de correio podem ser recuperados para o seu PC pelo [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/). A classe [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) utiliza o protocolo POP3 para copiar as mensagens de e-mail da sua caixa de correio POP3 para o seu PC. Uma vez que o e-mail foi recuperado, você não precisa estar conectado à internet enquanto ele está sendo lido, pois você pode ler o e-mail recuperado no seu PC. Se você não precisa ou não quer que uma cópia de algumas mensagens de e-mail seja mantida no servidor POP3, você pode excluí-las. Esta seção mostra como excluir e-mails usando a classe [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/).

## **Excluir um E-mail por Índice**

O seguinte trecho de código exclui todas as mensagens de e-mail de uma caixa de correio uma por uma, com base em seu índice. O índice nunca deve ser <=0 em [Pop3Client.DeleteMessage](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/deletemessage/#deletemessage/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-DeleteEmailByIndex-DeleteEmailByIndex.cs" >}}

## **Excluir Todos os E-mails**

Também podemos chamar [Pop3Client.DeleteMessages](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/deletemessage/#deletemessage/) para excluir todas as mensagens. O seguinte trecho de código mostra como excluir todos os e-mails.

```cs
// Excluir todas as mensagens
client.DeleteMessages();
```

Se a conexão com o servidor POP3 for interrompida imediatamente após as operações de exclusão, você não poderá mais chamar Cancel Deletes para fazer o que deseja.

## **Cancelar Exclusões**

[Pop3Client.UndeleteMessages](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/undeletemessages/#undeletemessages/) pode ser usado para cancelar a exclusão de mensagens de e-mail. O seguinte trecho de código mostra como cancelar exclusões.

```cs
// Cancelar exclusões
client.UndeleteMessages();
```