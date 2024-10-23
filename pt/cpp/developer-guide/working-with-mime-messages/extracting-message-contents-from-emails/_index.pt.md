---
title: "Extraindo Conteúdos de Mensagens de E-mails em C++"
description: "Usando a Biblioteca de Análise de E-mails em C++, você pode acessar propriedades de mensagens de e-mail, informações de cabeçalho e manipulá-las de diferentes maneiras programaticamente."
url: /pt/cpp/extracting-message-contents-from-emails/
weight: 20
type: docs
linktitle: "Extraindo Conteúdos de Mensagens de E-mails"
---

## **Exibindo Informações de E-mail na Tela**
O [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message) representa uma mensagem de e-mail e permite que os desenvolvedores acessem as propriedades da mensagem de e-mail. As informações de cabeçalho (discutidas em Extraindo Cabeçalhos de E-mail) podem ser extraídas e manipuladas de diferentes maneiras. Este artigo explica como exibir informações de cabeçalho de e-mail selecionadas e o corpo do e-mail na tela. Para Exibir Informações de E-mail na tela, siga estes passos:

- Crie uma instância da classe [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message).
- Carregue uma mensagem de e-mail na instância [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message).
- Exiba o conteúdo do e-mail na tela.

O seguinte trecho de código C++ mostra como exibir informações de e-mail na tela.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-EmailCPP-Email-DisplayEmailInformation-DisplayEmailInformation.cpp" >}}

## **Extraindo Cabeçalhos de E-mail**
O cabeçalho do e-mail representa um conjunto padrão de campos de cabeçalho definidos pela Internet e pelos RFC incluídos em mensagens de e-mail na Internet. Um cabeçalho de e-mail pode ser especificado usando a classe [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message). Tipos de cabeçalho comuns são definidos na classe HeaderType. É uma classe selada que funciona como uma enumeração normal. Para extrair cabeçalhos de um e-mail, siga estes passos:

1. Crie uma instância da classe [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message).
1. Carregue uma mensagem de e-mail na instância da classe [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message).
1. Após uma mensagem de e-mail ser carregada, obteremos seu conteúdo bruto.

A classe [`MailMessage`](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message) contém propriedades como De, Para, Cc, Assunto e assim por diante. Essas propriedades podem ser extraídas dos cabeçalhos.

1. Exiba o conteúdo bruto.

O seguinte trecho de código C++ mostra como extrair cabeçalhos de e-mail.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-EmailCPP-Email-ExtractingEmailHeaders-ExtractingEmailHeaders.cpp" >}}

## **Obter Valores de Cabeçalho Decodificados**
O seguinte trecho de código mostra como obter valores de cabeçalho decodificados.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-EmailCPP-Email-GetDecodedHeaderValues-GetDecodedHeaderValue.cpp" >}}