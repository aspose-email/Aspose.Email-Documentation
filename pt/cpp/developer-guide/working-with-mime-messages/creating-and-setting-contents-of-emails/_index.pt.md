---
title: "Criando e Definindo o Conteúdo de Emails em C++ e Enviando Email Usando SmtpClient"
description: "Para criar e definir o conteúdo de email em C++, use a classe MailMessage que pode criar e salvar a mensagem de email em diferentes formatos como EML, MSG e MHTML."
url: /pt/cpp/creating-and-setting-contents-of-emails/
weight: 10
type: docs
linktitle: "Criando e definindo o conteúdo de Emails"
keywords: "c++ enviar email"
---

## **Criar Nova Mensagem de Email**
A classe MailMessage representa uma mensagem de email e permite que os desenvolvedores criem novas mensagens de email. Propriedades básicas do email, como De, Para, Assunto e corpo, podem ser facilmente anexadas à mensagem de email recém-criada. Da mesma forma, podemos salvar a mensagem de email em diferentes formatos, como EML, MSG e MHTML.

<a name="csharp-create-new-email-msg" id="csharp-create-new-email-msg"><strong>Passos: Criar Nova Mensagem de Email em C#</strong></a>

- Crie uma instância da classe MailMessage.
- Defina as propriedades da mensagem de email.
- Salve a mensagem de email em diferentes formatos.
- Crie uma instância da classe SmtpClient e envie o email usando o método Send.

O seguinte trecho de código C++ mostra como criar um novo email com diferentes propriedades.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-CreateNewMailMessage-CreateNewMailMessage.cpp" >}}

## **Mudando endereços de email para um nome amigável**
Os exemplos de programação abaixo demonstram como mudar endereços de email para nomes amigáveis em uma mensagem de email. Um nome amigável é um nome que é mais amigável para o ser humano do que o endereço de email, por exemplo, John Smith em vez de js346@domain.com. Ao enviar um email, podemos associar um nome amigável a um endereço de email no construtor da classe MailMessage.

Para mudar endereços de email para nomes amigáveis em uma mensagem de email, siga estes passos:

- Crie uma instância da classe MailMessage e especifique endereços de email nos campos **Para** e **De**, juntamente com nomes amigáveis.
- Especifique os endereços de email Cc e Bcc juntamente com nomes amigáveis, chamando o construtor da classe MailMessage na instância de MailMessage.
- Crie uma instância da classe SmtpClient e envie o email usando o método Send.

O seguinte trecho de código mostra como exibir Nomes para endereços de email.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-ChangeEmailAddress-ChangeEmailAddress.cpp" >}}

## **Definir Corpo do Email**
A classe MailMessage representa uma mensagem de email. Instâncias da classe MailMessage são usadas para construir mensagens de email que são transmitidas a um servidor SMTP para entrega usando a classe SmtpClient. Um corpo de email pode ser especificado usando a classe MailMessage. Um email pode ter múltiplos corpos. Existem dois tipos de corpos de email na classe MailMessage:

- Corpo HTML
- Corpo de Texto

Além de HtmlBody e TextBody, Aspose.Email tem mais duas propriedades somente de leitura relacionadas ao corpo do email:

- IsBodyText: informa ao usuário se o corpo é texto.
- IsBodyHtml: informa ao usuário se o corpo é HTML ou texto simples.

Este artigo mostra como definir texto de corpo em texto simples ou HTML, definir texto alternativo e codificar o corpo do email.

### **Definindo Corpo HTML**
[HtmlBody](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message) é usado para especificar o conteúdo HTML de um corpo de mensagem. HtmlBody deve estar entre as tags <html> </html>. O seguinte trecho de código mostra como definir corpo HTML.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-SetHTMLBody-SetHTMLBody.cpp" >}}

### **Definindo Texto Alternativo**
Use a classe AlternateView para especificar cópias de uma mensagem de email em formato diferente. Por exemplo, se você enviar uma mensagem em HTML, também pode querer fornecer uma versão em texto simples, caso alguns dos destinatários usem leitores de email que não conseguem exibir conteúdo HTML. Esta classe tem duas propriedades, LinkedResources e BaseUri, que são usadas para resolver URLs dentro do conteúdo do email.

- LinkedResources é uma coleção de objetos LinkedResources. Quando renderizado, URLs dentro do conteúdo do email são primeiro coincididos com os URLs no Link de Conteúdo de cada objeto LinkedResources na coleção LinkedResources e resolvidos.
- BaseUri é usado pelo leitor de email para resolver URLs relativas dentro do corpo e também para resolver URLs relativas de Link de Conteúdo, na coleção LinkedResources.

O seguinte trecho de código C++ mostra como definir texto alternativo.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-SetAlternateText-SetAlternateText.cpp" >}}