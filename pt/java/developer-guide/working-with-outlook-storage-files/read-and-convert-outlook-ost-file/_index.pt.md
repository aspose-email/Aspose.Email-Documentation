---
title: "Ler e Converter Arquivo OST do Outlook"
url: /pt/java/read-and-convert-outlook-ost-file/
weight: 20
type: docs
---

Aspose.Email fornece uma API para leitura de arquivos OST do Microsoft Outlook. Você pode carregar um arquivo OST do disco ou fluxo para uma instância da classe [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) e obter informações sobre seu conteúdo, por exemplo, pastas, subpastas e mensagens. O Microsoft Outlook cria um arquivo PST para armazenar e-mails quando servidores de email POP3 ou IMAP são usados para baixar mensagens. Ele cria um arquivo OST quando o Microsoft Exchange é o servidor de email. OST suporta tamanhos de arquivos maiores do que arquivos PST.

## **Lendo Arquivos OST**

O processo para ler um arquivo OST com Aspose.Email é exatamente o mesmo que para ler um arquivo PST. O mesmo código pode ler arquivos PST e OST: basta fornecer o nome do arquivo correto para o método [PersonalStorage.fromFile()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#fromFile-java.lang.String-). O seguinte snippet de código mostra como ler arquivos OST.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-LoadAndConvertOSTFile-ReadAnOSTFile.java" >}}

## **Convertendo OST para PST**

{{% alert %}}
**Experimente!**

Converta e-mails e arquivos de mensagens online com o grátis [**Aplicativo de Conversão Aspose.Email**](https://products.aspose.app/email/pt/Conversion).
{{% /alert %}}
Aspose.Email torna possível converter um arquivo OST para PST com uma única linha de código. Da mesma forma, o arquivo OST pode ser criado a partir de um arquivo PST usando a mesma linha de código com o enumerador [FileFormat](https://reference.aspose.com/email/java/com.aspose.email/fileformat/). No momento, a API suporta a conversão de formatos OST para PST, exceto OST 2013/2016. O seguinte snippet de código mostra como converter OST para PST.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-LoadAndConvertOSTFile-ConvertOSTToPST.java" >}}

Para realizar outras operações com arquivos OST, consulte as seguintes páginas:

- [Leia o arquivo PST do Outlook e obtenha informações sobre pastas e subpastas](/email/java/read-outlook-pst-file-and-get-folders-and-subfolders-information/)
- [Obtenha informações sobre mensagens de um arquivo PST do Outlook](/email/java/working-with-messages-in-a-pst-file/#get-messages-information-from-an-outlook-pst-file)
- [Extraia mensagens do arquivo PST do Outlook e salve no disco ou fluxo no formato MSG](/email/java/working-with-messages-in-a-pst-file/#extracting-messages-form-pst-files)
- [Acesse informações de contato do arquivo PST do Outlook e salve no disco no formato MSG](/email/java/working-with-contacts-in-pst-file/#save-contacts-information-from-pst-file-in-msg-format)

## **Convertendo PST para OST**

A conversão de PST para OST não é suportada pelo Aspose.Email porque o OST é sempre criado pelo Outlook ao adicionar uma conta e sincronizar com o servidor de email. A diferença entre arquivos PST e OST é que o PST está disponível apenas localmente. O conteúdo do OST também está disponível no servidor de e-mail. Portanto, não há necessidade de converter PST para OST para uso local. Mas você pode importar PST em uma conta existente usando o assistente de Importação/Exportação no Outlook.