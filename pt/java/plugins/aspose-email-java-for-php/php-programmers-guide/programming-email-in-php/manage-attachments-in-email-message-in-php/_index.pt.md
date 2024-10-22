---
title: "Gerenciar Anexos em Mensagens de Email em PHP"
url: /pt/java/manage-attachments-in-email-message-in-php/
weight: 50
type: docs
---

## **Aspose.Email - Gerenciar Anexos em Mensagens de Email**
Para adicionar anexos a uma nova mensagem de email usando **Aspose.Email Java para PHP**, chame o método **add_attachments** do módulo **ManageAttachments**. Aqui você pode ver um exemplo de código.

**Código PHP**

``` php

 public static function add_attachments($dataDir=null){

\# Criar uma nova instância da classe MailMessage

$message =new MailMessage();

\# Definir assunto da mensagem

$message->setSubject("Nova mensagem criada pelo Aspose.Email para Java");

$mail_address = new MailAddress();

\# Definir corpo Html

$message->setHtmlBody("<b>Esta linha está em negrito.</b> <br/> <br/>" .

"<font color=blue>Esta linha está em azul</font>");

\# Definir informações do remetente

$message->setFrom(new MailAddress("from@domain.com", "Nome do Remetente", false));

\# Adicionar destinatários

$message->getTo()->add(new MailAddress("to1@domain.com", "Destinatário 1", false));

\# Adicionando anexo

\# Carregar um anexo

$attachment = new Attachment($dataDir . "1.txt");

\# Adicionar anexo na instância da classe MailMessage

$message->addAttachment($attachment);

\# Salvar mensagem no disco

$messageFormat=new MessageFormat();

$message->save($dataDir . "Add-Attachment.msg", $messageFormat->getMsg());

\# Exibir Status

print "Anexo adicionado com sucesso.".PHP_EOL;

}

```
## **Baixar Código em Execução**
Baixe **Gerenciar Anexos em Mensagens de Email (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingEmail/ManageAttachments.php)
- [CodePlex](https://asposeemailjavaphp.codeplex.com/SourceControl/latest#src/aspose/email/ProgrammingEmail/ManageAttachments.php)