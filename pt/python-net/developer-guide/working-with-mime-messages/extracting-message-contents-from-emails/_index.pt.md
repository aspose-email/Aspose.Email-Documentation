---
title: "Extraindo Conteúdos de Mensagens de Emails"
url: /pt/python-net/extracting-message-contents-from-emails/
weight: 20
type: docs
---


## **Exibindo Informações de Email na Tela**
O MailMessage representa uma mensagem de email e permite que os desenvolvedores acessem as propriedades da mensagem de email. As informações do cabeçalho (discutidas em Extraindo Cabeçalhos de Email) podem ser extraídas e manipuladas de diferentes maneiras. Este artigo explica como exibir informações selecionadas do cabeçalho de email e o corpo do email na tela. Para Exibir Informações de Email na Tela, siga estes passos:

- Crie uma instância da classe MailMessage.
- Carregue uma mensagem de email na instância MailMessage.
- Exiba o conteúdo do email na tela.

O seguinte trecho de código mostra como exibir informações de email na tela.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-DisplayEmailInformation-DisplayEmailInformation.py" >}}
## **Extraindo Cabeçalhos de Email**
O cabeçalho do email representa um conjunto padrão de campos de cabeçalho definidos pela Internet e pelo RFC incluídos nas mensagens de email da Internet. Um cabeçalho de email pode ser especificado usando a classe MailMessage. Tipos comuns de cabeçalho são definidos na classe HeaderType. É uma classe selada que funciona como uma enumeração normal. Para extrair cabeçalhos de um email, siga estes passos:

1. Crie uma instância da classe MailMessage.
1. Carregue uma mensagem de email na instância da classe MailMessage.
1. Após uma mensagem de email ter sido carregada, obteremos seu conteúdo bruto.

A própria classe MailMessage contém propriedades como De, Para, Cc, Assunto e assim por diante. Essas propriedades podem ser extraídas dos cabeçalhos.

1. Exiba o conteúdo bruto.

O seguinte trecho de código mostra como extrair cabeçalhos de email.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-ExtractingEmailHeaders-ExtractingEmailHeaders.py" >}}
## **Obter Valores de Cabeçalho Decodificados**
O seguinte trecho de código mostra como obter valores de cabeçalho decodificados.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-GetDecodedHeaderValues-GetDecodedHeaderValues.py" >}}