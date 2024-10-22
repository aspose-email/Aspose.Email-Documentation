---
title: "Recursos de Utilidade - MailMessage"
url: /pt/java/utility-features-mailmessage/
weight: 50
type: docs
---

## **Criptografando e Descriptografando Mensagens**

Aspose.Email fornece a capacidade de criptografar e descriptografar mensagens de Email. Este tópico mostra como uma mensagem existente ou nova pode ser carregada e criptografada usando [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). Os métodos [encrypt()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#encrypt-byte---java.lang.String-) e [decrypt()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#decrypt--) retornam o objeto **MailMessage** para os efeitos aplicados e precisam ser considerados ao criptografar/descriptografar mensagens. Criptografar e descriptografar mensagens envolve os seguintes passos:

1. Criar uma nova mensagem ou carregar uma existente
2. Criptografar a mensagem usando o arquivo de certificado
3. Enviar a mensagem ou salvá-la
4. Descriptografar a mensagem conforme necessário

O seguinte trecho de código mostra como criptografar e descriptografar mensagens.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-EncryptAndDecryptMessage-EncryptAndDecryptMessage.java" >}}

### **Verificando uma Mensagem para Criptografia**

A classe Aspose.Email [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#encrypt-byte---java.lang.String-) permite verificar se uma mensagem está criptografada ou não. A propriedade [isEncrypted](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#isEncrypted--) do **MailMessage** permite essa verificação, como mostrado no seguinte exemplo de código.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-CheckMessageForEncryption-CheckMessageForEncryption.java" >}}

## **Criptografia de Mensagens com X509Certificate**

Aspose.Email fornece a API para trabalhar com Mensagens Criptografadas com X509Certificate:

A classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) possui os seguintes métodos para trabalhar com criptografia de mensagens:

- public MailMessage [attachSignature(X509Certificate2 certificate, boolean detached)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#attachSignature-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-boolean-) - Cria uma mensagem assinada.
- public MailMessage [attachSignature(X509Certificate2 certificate)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#attachSignature-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-) - Cria uma mensagem assinada.
- public X509Certificate2[] [checkSignatureCert()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#checkSignatureCert--) - Verifica a assinatura da MailMessage existente.
- public MailMessage [decrypt(X509Certificate2 certificate)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#decrypt-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-)
- public MailMessage [encrypt(X509Certificate2 certificate)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#encrypt-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-)
- public MailMessage [encrypt(X509Certificate2[] certificates)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#encrypt-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2---)

## **Configurar Opções de Locale para Aspose.Email**

Você pode usar a classe [LocaleOptions](https://reference.aspose.com/email/java/com.aspose.email/localeoptions/) em caso de locale padrão não reconhecido e definir o locale mais apropriado para a biblioteca Aspose Email. Ela oferece os seguintes métodos para realizar a tarefa:

- [getLocale()](https://reference.aspose.com/email/java/com.aspose.email/localeoptions/#getLocale--) - Retorna o Locale padrão para Aspose.Email.
- [setLocale(Locale locale)](https://reference.aspose.com/email/java/com.aspose.email/localeoptions/#setLocale-java.util.Locale-) e [setLocale(String localeName)](https://reference.aspose.com/email/java/com.aspose.email/localeoptions/#setLocale-java.lang.String-) - Define o locale padrão relacionado para Aspose.Email.
- [clear()](https://reference.aspose.com/email/java/com.aspose.email/localeoptions/#clear--) - Limpa o locale padrão para Aspose.Email. O locale padrão para Java será utilizado.

O seguinte exemplo de código demonstra como carregar uma mensagem de email de um arquivo usando as configurações de locale especificadas:

```java
final Locale locale = new Locale("en", "DE");
Locale.setDefault(locale);

// definir Locale para a biblioteca Aspose Email
LocaleOptions.setLocale("en-US");
// ou
//LocaleOptions.setLocale(new Locale("en", "US"));

MailMessage.load("document.msg");
```
Este código garante que a aplicação e a biblioteca Aspose.Email usem os locales especificados para lidar com a linguagem, país e convenções culturais.

## **MailMessages Contendo anexos TNEF**

O Formato de Encapsulamento Neutro de Transporte (TNEF) é um formato de anexo de email proprietário usado pelo Microsoft Outlook e pelo Microsoft Exchange Server. A API Aspose.Email permite que você leia mensagens de email que têm anexos TNEF e modifique seus conteúdos. O email pode ser salvo como um email normal ou no mesmo formato, preservando os anexos TNEF. Este artigo mostra diferentes exemplos de código para trabalhar com mensagens contendo anexos TNEF.

### **Lendo uma Mensagem Preservando Anexos TNEF**

O seguinte trecho de código mostra como ler uma mensagem preservando os anexos TNEF.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ReadMessageByPreservingTNEFAttachments-ReadMessageByPreservingTNEFAttachments.java" >}}

### **Atualizando Recursos em um Anexo TNEF e Preservando o Formato TNEF**

O seguinte trecho de código mostra como atualizar recursos em um anexo TNEF e preservar o formato TNEF.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-UpdateTNEFAttachments-UpdateTNEFAttachments.java" >}}

### **Adicionando Novos Anexos à Mensagem Principal Contendo TNEF**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-TNEFAttachment-AddNewAttachmentToMessageContainingTNEF.java" >}}

### **Criando TNEF EML a partir de MSG**

Os MSGs do Outlook às vezes contêm informações como tabelas e estilos de texto que podem ser perturbados se forem convertidos para EML. Criar mensagens TNEF a partir de tais arquivos MSG nos permite reter a formatação e até enviar tais mensagens através dos clientes de email mantendo a formatação.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-TNEFAttachment-CreatingTNEFEMLFromMSG.java" >}}

Para criar o TNEF, o seguinte código de exemplo pode ser usado.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-TNEFAttachment-CreateTNEF.java" >}}

### **Detectar se uma Mensagem é TNEF**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-TNEFAttachment-DetectIfAMessageIsTNEF.java" >}}

## **Processando Mensagens Devolvidas**

É muito comum que uma mensagem enviada a um destinatário possa ser devolvida por qualquer motivo, como um endereço de destinatário inválido. A API Aspose.Email tem a capacidade de processar tal mensagem para verificar se é um email devolvido ou uma mensagem de email normal. O método [CheckBounced](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#checkBounced--) da classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) retorna um resultado válido se a mensagem de email for um email devolvido.

Este artigo mostra o uso da classe [BounceResult](https://reference.aspose.com/email/java/com.aspose.email/bounceresult/) que fornece a capacidade de verificar se uma mensagem é um email devolvido. Ela ainda fornece informações detalhadas sobre os destinatários, a ação tomada e a razão da notificação.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ProcessBouncedMessages-.java" >}}

## **Ignorar exceções**

A biblioteca oferece uma classe [ExceptionManager](https://reference.aspose.com/email/java/com.aspose.email/exceptionmanager/) para implementar a capacidade de ignorar exceções na funcionalidade da sua aplicação. O trecho de código abaixo demonstra como definir um callback para tratar exceções:

```java
 ExceptionManager.setIgnoreExceptionsHandler( new IgnoreExceptionsCallback() {

   //caminho da exceção: {Módulo}\{Método}\{Ação}\{GUID}

   //exemplo: MailMessage\Load\DecodeTnefAttachment\64149867-679e-4645-9af0-d46566cae598

   public boolean invoke(AsposeException ex, String path) {

       //Ignorar todas as exceções em MailMessage.Load

       return path.equals("MailMessage\\Load");

   }

});
```
Ou use uma **alternativa**:

```java
 ExceptionManager.setIgnoreAll(true);
```
Além disso, você pode definir um callback para o **log de exceções ignoradas**:

```java
ExceptionManager.setIgnoreExceptionsLogHandler( new IgnoreExceptionsLogCallback() {

   public void invoke(String message) {

        System.out.println("=== EXCEÇÃO IGNORADA === " + message);

   }

});
```
O usuário será notificado de que a exceção pode ser ignorada por uma mensagem de erro. Por exemplo:

Exceção na mensagem:

```java
AsposeArgumentException: properties should not be empty.
```

Se você deseja ignorar uma exceção e prosseguir, pode usar:
```java
ExceptionManager.getIgnoreList().add("MailMessage\\Load\\DecodeTnefAttachment\\64149867-679e-4645-9af0-d46566cae598")

Anexo TNEF inválido será interpretado como anexo regular.
```

## **Analisador de Spam Bayesiano**

Aspose.Email fornece a capacidade de filtragem de e-mails usando o analisador de spam Bayesiano. Ele fornece a classe [SpamAnalyzer](https://reference.aspose.com/email/java/com.aspose.email/spamanalyzer/) para esse propósito. Este artigo mostra como treinar o filtro para distinguir entre spam e emails regulares com base no banco de palavras.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-BayesianSpamAnalyzer-.java" >}}

## **Obtendo Preamble e Epilogue de Mensagens EML**

No formato MIME, o *preamble* é o texto que aparece após os cabeçalhos e antes da primeira fronteira multipart. O *epilogue* é o texto que aparece após a última fronteira e antes do final da mensagem. Este texto geralmente não é visível para os usuários em leitores de email, mas algumas implementações MIME podem usá-lo para inserir notas para destinatários que leem a mensagem usando programas que não estão em conformidade com MIME.

O seguinte trecho de código mostra como obter o preamble e o epilogue de uma mensagem EML, o que pode ser alcançado com os métodos correspondentes da classe [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/):

- [setPreamble(String value)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setPreamble-java.lang.String-) - Obtém ou define um texto preamble.
- [setEpilogue(String value)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setEpilogue-java.lang.String-) - Obtém ou define um texto epilogue.

```java
// Obtém ou define um texto preamble.
public String getPreamble, setPreamble

// Obtém ou define um texto epilogue.
public String getEpilogue, setEpilogue
```