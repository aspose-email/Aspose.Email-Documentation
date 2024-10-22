---
title: "Atualizar e Salvar um Email em PHP"
url: /pt/java/update-and-save-an-email-in-php/
weight: 70
type: docs
---

## **Aspose.Email - Atualizar e Salvar um Email**
Para Atualizar e Salvar um Email usando **Aspose.Email Java for PHP**, basta invocar o módulo **UpdateEmail**. Aqui você pode ver um código de exemplo.

**Código PHP**

``` php

 # Inicializar e Carregar um arquivo MSG existente especificando o MessageFormat

$mailMessage=new MailMessage();

$email = $mailMessage->load($dataDir . "Message.msg");

\# Inicializar uma variável String para obter o Assunto do Email

$subject = $email->getSubject();

\# Definir o Assunto do Email

$email->setSubject('Este texto é adicionado ao assunto existente');

\# Inicializar uma variável String para obter o Corpo HTML do Email

$body = $email->getHtmlBody();

\# Adicionar mais informações à variável Corpo

$body = $body . "<br> Este texto é adicionado ao corpo existente".PHP_EOL;

\# Definir o Corpo do Email

$email->setHtmlBody($body);

\# Inicializar o objeto MailAddressCollection

$contacts = new MailAddressCollection();

\# Recuperar a lista TO do Email

$contacts = $email->getTo();

\# Adicionar outro endereço de email à coleção

$contacts->add("to1@domain.com");

\# Definir a coleção como a lista TO do Email

$email->setTo($contacts);

\# Inicializar MailAddressCollection

$contacts = new MailAddressCollection();

\# Recuperar a lista CC do Email

$contacts = $email->getCC();

\# Adicionar outro endereço de email à coleção

$contacts->add("cc2@domain.com");

\# Definir a coleção como a lista CC do Email

$email->setCC($contacts);

\# Salvar a mensagem de Email no disco especificando o MessageFormat

$mailMessageSaveType=new MailMessageSaveType();

$email->save($dataDir . "UpdateMessage.msg", $mailMessageSaveType->getOutlookMessageFormat());

\# Exibir Status

print "Mensagem de email atualizada com sucesso.".PHP_EOL;

```
## **Baixar Código em Execução**
Baixe **Atualizar e Salvar um Email (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingEmail/UpdateEmail.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingEmail/UpdateEmail.php)