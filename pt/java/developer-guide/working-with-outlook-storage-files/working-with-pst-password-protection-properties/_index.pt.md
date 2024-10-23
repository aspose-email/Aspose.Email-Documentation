---
title: "Trabalhando com Propriedades de Proteção por Senha de PST"
url: /pt/java/trabalhando-com-propriedades-de-protecao-por-senha-de-pst/
weight: 100
type: docs
---

{{% alert color="primary" %}} 

O Microsoft Outlook permite que os usuários protejam arquivos PST com senha para restringir o acesso a eles. Aspose.Email pode detectar a proteção por senha em um arquivo PST. Este artigo mostra como verificar um PST para uma senha e também como verificar se a senha aplicada a ele está correta.

{{% /alert %}} 

## **Verificar a Proteção por Senha**

O valor [MapiPropertyTag.PR_PST_PASSWORD](https://reference.aspose.com/email/java/com.aspose.email/mapipropertytag/#PR-PST-PASSWORD) da classe [MapiPropertyTag](https://reference.aspose.com/email/java/com.aspose.email/mapipropertytag/) é usado para verificar se um arquivo está protegido por senha.

O hash CRC-32 da string da senha é armazenado na propriedade PidTagPstPassword (tag = 0x67ff0003) na [MessageStore](https://reference.aspose.com/email/java/com.aspose.email/messagestore/). Se essa propriedade existir e for diferente de zero, então o PST está protegido por senha.

O seguinte trecho de código mostra como verificar se um arquivo PST está protegido por senha e se a string fornecida é uma senha válida para esse PST.

O trecho de código abaixo mostra duas funções, a primeira verifica se o PST está protegido por senha e a segunda mostra como verificar se uma senha fornecida está correta ou não.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-PSTPasswordProtectionProperties-CheckForPasswordProtection.java" >}}

## **Remover/Redefinir a Propriedade PR_PST_PASSWORD**

A remoção da propriedade [PR_PST_PASSWORD](https://reference.aspose.com/email/java/com.aspose.email/mapipropertytag/#PR-PST-PASSWORD) não pode ser realizada como outras propriedades são removidas de um repositório de mensagens. Em vez disso, precisamos definir seu valor como zero (0) para que ela seja removida. A propriedade "Store" da classe PST permite acesso às propriedades de armazenamento do PST em vez das MessageStoreProperties do PST neste caso.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-PSTPasswordProtectionProperties-RemovePSTPasswordProperty.java" >}}

## **Definir/Mudar a Senha do PST**

O seguinte trecho de código mostra como definir uma senha em arquivos PST.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-PSTPasswordProtectionProperties-SetPSTPassword.java" >}}

## **Verificação de Senha para Arquivos PST Protegidos por Senha**

Aspose.Email permite que os desenvolvedores verifiquem se o arquivo PST está protegido por senha e se a senha fornecida está correta ou não. Para isso, a API fornece a propriedade [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#isPasswordProtected--) e o método [PersonalStorage.Store.IsPasswordValid()](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#isPasswordValid-java.lang.String-). A propriedade [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#isPasswordProtected--) retorna **true** se o arquivo PST estiver protegido por senha e **false** se não estiver. O método [PersonalStorage.Store.IsPasswordValid()](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#isPasswordValid-java.lang.String-) que recebe a senha como string como parâmetro e retorna **true** se a senha estiver correta e **false** se estiver incorreta.

O seguinte trecho de código demonstra o uso da propriedade [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#isPasswordProtected--) e do método [PersonalStorage.Store.IsPasswordValid()](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#isPasswordValid-java.lang.String-).

### **Código de Exemplo**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-PSTPasswordValidation-1.java" >}}

### **Saída do Console**

O armazenamento está protegido por senha - Verdadeiro  
A senha é válida - Verdadeiro