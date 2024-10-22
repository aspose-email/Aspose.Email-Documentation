---
title: "Extraindo Conteúdo de Mensagens de Emails"
url: /pt/java/extracting-message-contents-from-emails/
weight: 30
type: docs
---

## **Exibindo Informações de Email na Tela**

O [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getDate()) representa uma mensagem de email e permite que os desenvolvedores acessem as propriedades da mensagem de email. As informações do cabeçalho (discutidas em [Extraindo Cabeçalhos de Email](#extracting-email-headers)) podem ser extraídas e manipuladas de diferentes maneiras. Este artigo explica como exibir informações do cabeçalho de email selecionadas e o corpo do email na tela.

1. Crie uma instância do **MailMessage**.
2. Carregue uma mensagem de email na instância do **MailMessage**.
3. Exiba o conteúdo do email na tela.

O código abaixo demonstra como carregar uma mensagem de email e exibir seu conteúdo - de, para, assunto e corpo do email - na tela.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-DisplayEmailInformation-DisplayEmailInformation.java" >}}

### **Obtendo Data e Hora da Mensagem**

A classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) pode ser usada para recuperar a data da mensagem em UTC ou no fuso horário local. Essa informação pode ser resumida da seguinte forma:

1. [MailMessage.getDate()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getDate--) - retorna a data em UTC
1. [MailMessage.getLocalDate()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getLocalDate--) - retorna a data no fuso horário local
2. [MailMessage.isLocalDate](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#isLocalDate--) Retorna **true** se **MailMessage.getDate()** estiver no fuso horário local

## **Extraindo Cabeçalhos de Email**

O cabeçalho de email representa um conjunto padrão de campos de cabeçalho definidos pelo Internet e RFC incluídos nas mensagens de email da Internet. Um cabeçalho de email pode ser especificado usando a classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). Tipos de cabeçalho comuns são definidos na classe [HeaderType](https://reference.aspose.com/email/java/com.aspose.email/headertype/). É uma classe selada que funciona como uma enumeração normal.

Para extrair cabeçalhos de um email, siga estas etapas:

1. Crie uma instância da classe **MailMessage**.
2. Carregue uma mensagem de email na instância da classe **MailMessage**.
3. Após uma mensagem de email ter sido carregada, obteremos seu conteúdo bruto. A própria classe **MailMessage** contém propriedades como De, Para, Cc, Assunto e assim por diante. Essas propriedades podem ser extraídas dos cabeçalhos.
4. Exiba o conteúdo bruto.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-EmailHeaders-ExtractingEmailHeaders.java" >}}

## **Obter Valores de Cabeçalho Decodificados**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-EmailHeaders-GetDecodedHeaderValueFromHeaderCollection.java" >}}

## **Obter e Modificar o Cabeçalho de Disposição de Recurso Vinculado**

O recurso vinculado pode ser acessado e manipulado programaticamente no objeto da mensagem de email. O método [getContentDisposition()](https://reference.aspose.com/email/java/com.aspose.email/linkedresource/#getContentDisposition--) da classe [LinkedResource](https://reference.aspose.com/email/java/com.aspose.email/linkedresource/) obtém o cabeçalho Content-Disposition. O exemplo de código abaixo demonstra como acessar e modificar o nome do arquivo do recurso vinculado:

```java
MailMessage eml = MailMessage.load(fileName);
eml.getLinkedResources().get_Item(0).getContentDisposition().setFileName("changed.png");
```
## **Obter o corpo HTML como texto puro**

A classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) oferece o recurso de extrair o corpo HTML da mensagem como texto puro. A classe **MailMessage** fornece um método [GetHtmlBodyText](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getHtmlBodyText-boolean-) que retorna o corpo HTML como texto puro. O método **GetHtmlBodyText** aceita um parâmetro booleano que indica se o corpo deve conter URLs ou não. Passar o parâmetro como verdadeiro indica que o corpo HTML deve conter URLs.

O seguinte trecho de código demonstra o uso do método **GetHtmlBodyText** para extrair o corpo HTML do email como texto puro.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-GetHTMLBodyAsPlainText-1.java" >}}