---
title: "Programação de Verificação de Email"
url: /pt/net/programming-email-verification/
weight: 140
type: docs
---


## **Usando Aspose.Email.Verifications**

Aspose.Email.Verifications oferece suporte total para validar endereços de email. Com a ajuda da classe Aspose.Email.Verifications.EmailValidator, diferentes tipos de validação podem ser realizados, incluindo verificação de sintaxe do email, verificação de domínio do email e verificação de contas de usuário com servidores de email. A enumeração ValidationPolicy é usada para definir o nível da política de validação:

- SyntaxOnly valida a sintaxe do endereço de email.
- SyntaxAndDomain valida a sintaxe do endereço de email, em seguida, o domínio.
- MailServer valida o endereço tentando se conectar ao servidor de email.
  
## **Aplicação de Exemplo**

Aspose.Email.Verifications é um componente poderoso e útil para verificar a validade de endereços de email, nomes de domínio de email e muito mais. Este artigo mostra como criar uma aplicação usando Aspose.Email.Verifications. A aplicação de demonstração verifica a validade de um endereço de email.

Para criar uma aplicação que usa Aspose.Email.Verifications para verificar endereços de email:

- Abra o Visual Studio.
- No menu **Arquivo**, clique em **Novo** e depois em **Projeto**. Para simplicidade, este será um programa de console. Escolha o projeto C# ou VB.NET, como preferir.

|**Criando um novo projeto**|
| :- |
|![todo:image_alt_text](programming-email-verification_1.png)|

- Adicione uma referência à aplicação de console.

|**Adicionando uma referência ao Aspose.Email**|
| :- |
|![todo:image_alt_text](programming-email-verification_2.png)|

- Navegue até o Aspose.Email.dll no diretório Bin sob o diretório de instalação do Aspose.Email.

O seguinte trecho de código mostra como validar um endereço de email. Quando o código é executado, uma mensagem anuncia se o endereço de email é válido ou não.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Email-EmailValidations-EmailValidations.cs" >}}

- Compile e execute.

|**Executando a aplicação.**|| 
| :- | :- |
|![todo:image_alt_text](programming-email-verification_3.png)| |

## **Funcionalidade Básica de Validação**

Use Aspose.Email.Verifications para verificar a validade de endereços de email. Para esse fim, Aspose.Email.Verifications possui a classe EmailValidator.

### **Validando Emails**

A funcionalidade de validação do Aspose.Email pode ser usada para validar endereços de email, nomes de domínio e servidores de email. O seguinte trecho de código mostra como usar o EmailValidator para validar um endereço de email.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Email-ValidatingEmails-ValidatingEmails.cs" >}}

### **Validando Domínio**

Aspose.Email.Verifications pode verificar a validade de um nome de domínio.

### **Validando Servidor de Email**

Aspose.Email.Verifications pode verificar a validade de um servidor de email.