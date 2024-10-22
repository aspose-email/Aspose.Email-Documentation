---
title: "Ler e Converter Arquivo OST do Outlook"
url: /pt/net/read-and-convert-outlook-ost-file/
weight: 20
type: docs
---

Aspose.Email para .NET fornece uma API para ler arquivos OST do Microsoft Outlook. Você pode carregar um arquivo OST de um disco ou de um fluxo em uma instância da classe [Aspose.Email.Outlook.Pst.PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) e obter informações sobre seu conteúdo, por exemplo, pastas, subpastas e mensagens. O Microsoft Outlook cria um arquivo PST para armazenar e-mails quando servidores de e-mail POP3 ou IMAP são usados para baixar mensagens. Ele cria um arquivo OST quando o Microsoft Exchange é o servidor de e-mail. OST suporta tamanhos de arquivo maiores do que arquivos PST.

## **Lendo Arquivos OST**

O processo para ler um arquivo OST com Aspose.Email é exatamente o mesmo que para ler um arquivo PST. O mesmo código pode ler arquivos PST e OST: basta fornecer o nome do arquivo correto ao método [PersonalStorage.FromFile()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/fromfile/#fromfile/). O seguinte snippet de código mostra como ler arquivos OST.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-PST-ReadingOSTFiles-ReadingOSTFiles.cs" >}}

## **Convertendo OST para PST**

{{% alert %}}
**Experimente!**

Converta e-mails e arquivos de mensagem online com o gratuito [**Aplicativo de Conversão Aspose.Email**](https://products.aspose.app/email/pt/Conversion).
{{% /alert %}}
Aspose.Email torna possível converter um arquivo OST para PST com uma única linha de código. De forma semelhante, o arquivo OST pode ser criado a partir de um arquivo PST usando a mesma linha de código com o enumerador [FileFormat](https://reference.aspose.com/email/net/aspose.email.storage.pst/fileformat/). No momento, a API suporta a conversão de formatos OST para PST, exceto 2013/2016/2019/2021 e versões futuras. O seguinte snippet de código mostra como converter OST para PST.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-PST-ConvertingOSTToPST-ConvertingOSTToPST.cs" >}}

Para realizar outras operações com arquivos OST, consulte as seguintes páginas:

- [Ler Arquivo PST do Outlook e Obter Informações sobre Pastas e Subpastas](https://docs.aspose.com/email/pt/net/read-outlook-pst-file-and-get-folders-and-subfolders-information/)
- [Obter Informações de Mensagens de um Arquivo PST do Outlook](https://docs.aspose.com/email/pt/net/working-with-messages-in-a-pst-file/#get-messages-information-from-an-outlook-pst-file)
- [Extrair Mensagens de um Arquivo PST do Outlook e Salvar em Disco ou Fluxo no Formato MSG](https://docs.aspose.com/email/pt/net/working-with-messages-in-a-pst-file/#extracting-messages-form-pst-files)
- [Acessar Informações de Contato de um Arquivo PST do Outlook e Salvar em Disco no Formato MSG](https://docs.aspose.com/email/pt/net/working-with-contacts-in-pst-file/#save-contacts-information-from-pst-file-in-msg-format)

## **Convertendo PST para OST**

A conversão de PST para OST não é suportada pelo Aspose.Email porque o OST é sempre criado pelo Outlook ao adicionar uma conta e sincronizar com o servidor de e-mail. A diferença entre arquivos PST e OST é que o PST está disponível apenas localmente. O conteúdo do OST também está disponível no servidor de e-mail. Portanto, não há necessidade de converter PST para OST para uso local. Mas você pode importar PST em uma conta existente usando o assistente de Importação/Exportação no Outlook.