---
title: "Programação de Verificação de Email"
url: /pt/java/programming-email-verification/
weight: 125
type: docs
---


## **Usando EmailValidator**
[EmailValidator](https://apireference.aspose.com/email/java/com.aspose.email/EmailValidator) fornece suporte total para validar endereços de email. Com a ajuda da classe [EmailValidator](https://apireference.aspose.com/email/java/com.aspose.email/EmailValidator), diferentes tipos de validação podem ser realizados, incluindo verificação de sintaxe de email, verificação de domínio de email e verificação de contas de usuário com servidores de email. A enumeração [ValidationPolicy](https://apireference.aspose.com/email/java/com.aspose.email/ValidationPolicy) é usada para definir o nível da política de validação:

- SyntaxOnly valida a sintaxe do endereço de email.
- SyntaxAndDomain valida a sintaxe do endereço de email e, em seguida, valida o domínio.
## **Funcionalidade Básica de Validação**
Use [EmailValidator](https://apireference.aspose.com/email/java/com.aspose.email/EmailValidator) para verificar a validade dos endereços de email.
### **Validando Emails**
A funcionalidade de validação da Aspose.Email pode ser usada para validar endereços de email, nomes de domínio e servidores de email. O seguinte trecho de código mostra como usar [EmailValidator](https://apireference.aspose.com/email/java/com.aspose.email/EmailValidator) para validar um endereço de email.


~~~Java
EmailValidator ev = new EmailValidator();
ValidationResult[] result = new ValidationResult[] { null };
ev.validate("user@domain.com", result);
if (result[0].getReturnCode() == ValidationResponseCode.ValidationSuccess)
{
    System.out.println("o endereço de email é válido.");
}
else
{
    System.out.println("o endereço de email é inválido, por " + result[0].getMessage());
}
~~~
## **Validar Mensagens de Email**

Essa funcionalidade permite que os usuários validem arquivos de mensagens, garantindo a aderência a formatos e estruturas especificados. Ela suporta validação para arquivos/fluxos nos seguintes formatos:

- **Formatos MIME:** eml, emlx, mht
- **Formatos MAPI:** msg, oft

Aspose.Email fornece as seguintes ferramentas para realizar a tarefa:

- O método [MessageValidator.validate](https://reference.aspose.com/email/java/com.aspose.email/messagevalidator/#validate-java.lang.String-) - valida mensagens usando este método, fornecendo um caminho de arquivo ou fluxo como entrada.
- A classe [MessageValidationResult](https://reference.aspose.com/email/java/com.aspose.email/messagevalidationresult/) - encapsula os resultados do processo de validação de mensagens. Fornece informações sobre o sucesso da validação, tipo de formato e quaisquer erros encontrados.
- O Enum [MessageValidationErrorType](https://reference.aspose.com/email/java/com.aspose.email/messagevalidationerrortype/) - enumera diferentes tipos de erros de validação.

O exemplo de código abaixo demonstra como usar essas ferramentas para validação de mensagens:

```java
MessageValidationResult result = MessageValidator.validate(fileName);

// Verifique se a validação foi bem-sucedida
if (!result.isSuccess()) {
    System.out.println("A validação falhou.");

    // Verifique o tipo de formato
    if (result.getFormatType() == FileFormatType.Mht) {
        System.out.println("O tipo de formato é Mht.");
    }

    // Verifique e exiba os erros
    System.out.println("Número de erros: " + result.getErrors().size());

    for (MessageValidationError error : result.getErrors()) {
        System.out.println("Tipo de Erro: " + error.getErrorType());
        System.out.println("Descrição: " + error.getDescription());
    }
} else {
    System.out.println("Validação bem-sucedida.");
}
```