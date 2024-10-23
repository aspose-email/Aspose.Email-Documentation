---
title: "Ler e Converter Arquivo OST do Outlook"
url: /pt/python-net/read-and-convert-outlook-ost-file/
weight: 20
type: docs
---


Aspose.Email para .NET fornece uma API para ler arquivos OST do Microsoft Outlook. Você pode carregar um arquivo OST do disco ou stream para uma instância da classe Aspose.Email.Outlook.Pst.PersonalStorage e obter informações sobre seu conteúdo, por exemplo, pastas, subpastas e mensagens. O Microsoft Outlook cria um arquivo PST para armazenar e-mails quando servidores de e-mail POP3 ou IMAP são usados para baixar mensagens. Ele cria um arquivo OST quando o Microsoft Exchange é o servidor de e-mail. OST suporta tamanhos de arquivo maiores do que arquivos PST.
## **Lendo Arquivos OST**
O processo para ler um arquivo OST com o Aspose.Email é exatamente o mesmo que para ler um arquivo PST. O mesmo código pode ler arquivos PST e OST: basta fornecer o nome do arquivo correto para o método PersonalStorage.FromFile(). O seguinte trecho de código mostra como ler arquivos OST.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-ReadingOSTFiles-ReadingOSTFiles.py" >}}
## **Convertendo OST para PST**
{{% alert %}}
**Experimente!**

Converta e-mails e arquivos de mensagens online com o gratuito [**Aplicativo de Conversão Aspose.Email**](https://products.aspose.app/email/pt/Conversion).
{{% /alert %}}
Aspose.Email torna possível converter um arquivo OST para PST com uma única linha de código. Da mesma forma, um arquivo OST pode ser criado a partir de um arquivo PST usando a mesma linha de código com o enumerador FileFormat. Atualmente, a API suporta a conversão de formatos OST para PST, exceto OST 2013/2016. O seguinte trecho de código mostra como converter OST para PST.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-ConvertingOSTToPST-ConvertingOSTToPST.py" >}}

## **Converter PST para OST**

A conversão de PST para OST não é suportada pelo Aspose.Email porque o OST é sempre criado pelo Outlook ao adicionar uma conta e sincronizar com o servidor de e-mail. A diferença entre arquivos PST e OST é que o PST está disponível apenas localmente. O conteúdo do OST também está disponível no servidor de e-mail. Portanto, não há necessidade de converter PST para OST para uso local. Mas você pode importar PST em uma conta existente usando o assistente Importar/Exportar no Outlook.

Para realizar outras operações com arquivos OST, consulte as seguintes páginas:

- Ler Arquivo PST do Outlook e Obter Informações de Pastas e Subpastas
- Obter Informações de Mensagens de um Arquivo PST do Outlook
- Extrair Mensagens do Arquivo PST do Outlook e Salvar no Disco ou Stream no Formato MSG
- Acessar Informações de Contato do Arquivo PST do Outlook e Salvar no Disco no Formato MSG