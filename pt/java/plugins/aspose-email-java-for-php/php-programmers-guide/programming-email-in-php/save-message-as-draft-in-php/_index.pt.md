---
title: "Salvar Mensagem como Rascunho em PHP"
url: /pt/java/salvar-mensagem-como-rascunho-em-php/
weight: 60
type: docs
---

## **Aspose.Email - Salvar Mensagem como Rascunho**
Para salvar uma mensagem como rascunho usando **Aspose.Email Java para PHP**, simplesmente invoque o módulo **SaveMessageAsDraft**. Aqui você pode ver um código de exemplo.

**Código PHP**

``` php

 # Crie uma nova instância da classe MailMessage

$message = new MailMessage();

\# Defina o assunto da mensagem

$message->setSubject("Nova mensagem criada por Aspose.Email para Java");

$mail_address = new MailAddress();

\# Defina o corpo Html

$message->setHtmlBody("<b>Esta linha está em negrito.</b> <br/> <br/>" .

"<font color=blue>Esta linha está em azul</font>");

\# Defina as informações do remetente

$message->setFrom(new MailAddress("from@domain.com", "Nome do Remetente", false));

\# Adicione os destinatários TO

$message->getTo()->add(new MailAddress("to1@domain.com", "Destinatário 1", false));

$message->getTo()->add(new MailAddress("to2@domain.com", "Destinatário 2", false));

\# Crie uma instância de MapiMessage e carregue a instância MailMessage nela

$mapiMessage=new MapiMessage();

$mapi_msg = $mapiMessage->fromMailMessage($message);

\# Defina os MapiMessageFlags como UNSENT e FROMME

$mapi_message_flags = new MapiMessageFlags();

\# Salve o MapiMessage no disco

$mapi_msg->save($dataDir . "Novo-Rascunho.msg");

\# Exiba o Status

print "Rascunho salvo com sucesso.".PHP_EOL;

```
## **Baixar Código em Execução**
Baixe **Salvar Mensagem como Rascunho (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingEmail/SaveMessageAsDraft.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingEmail/SaveMessageAsDraft.php)