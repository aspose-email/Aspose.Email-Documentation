---
title: "Criar Novo Email em PHP"
url: /pt/java/criar-novo-email-em-php/
weight: 20
type: docs
---

## **Aspose.Email - Criar Novo Email**
Para criar um novo Email usando **Aspose.Email Java para PHP**, simplesmente invoque o módulo **CreateNewEmail**. Aqui você pode ver um exemplo de código.

**Código PHP**

``` php

 # Crie uma nova instância da classe MailMessage

$message = new MailMessage();

\# Defina o assunto da mensagem

$message->setSubject("Nova mensagem criada pelo Aspose.Email para Java");

$mail_address = new MailAddress();

\# Defina o corpo em Html

$message->setHtmlBody("<b>Esta linha está em negrito.</b> <br/> <br/>" .

"<font color=blue>Esta linha está em azul</font>");

\# Defina as informações do remetente

$message->setFrom(new MailAddress("from@domain.com", "Nome do Remetente", false));

\# Adicione os destinatários TO

$message->getTo()->add(new MailAddress("to1@domain.com", "Destinatário 1", false));

$message->getTo()->add(new MailAddress("to2@domain.com", "Destinatário 2", false));

\# Adicione os destinatários CC

$message->getCC()->add(new MailAddress("cc1@domain.com", "Destinatário 3", false));

$message->getCC()->add(new MailAddress("cc2@domain.com", "Destinatário 4", false));

\# Salve a mensagem nos formatos EML e MSG

$mail_message_save_type = new MailMessageSaveType();

$message->save($dataDir . "Message.eml", $mail_message_save_type->getEmlFormat());

$message->save($dataDir . "Message.msg", $mail_message_save_type->getOutlookMessageFormat());

\# Exiba o status

print "Mensagens de email criadas com sucesso.".PHP_EOL;


```
## **Baixar Código em Execução**
Baixe **Criar Novo Email (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingEmail/CreateNewEmail.php)
- [CodePlex](https://asposeemailjavaphp.codeplex.com/SourceControl/latest#src/aspose/email/ProgrammingEmail/CreateNewEmail.php)