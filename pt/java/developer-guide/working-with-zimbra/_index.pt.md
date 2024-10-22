---
title: "Trabalhando com Zimbra"
url: /pt/java/trabalhando-com-zimbra/
weight: 110
type: docs
---

## **Sobre o Zimbra**
Zimbra é uma suíte de email, calendário e colaboração construída para a nuvem. O Zimbra inclui email completo, contatos, calendário, compartilhamento de arquivos, tarefas e mensagens/videoconferência, todos acessados a partir do Cliente Web Zimbra de qualquer dispositivo.
## **Ler todas as mensagens do armazenamento TGZ do Zimbra**
Aspose.Email fornece a classe [TgzReader](https://apireference.aspose.com/email/java/com.aspose.email/TgzReader) para ler arquivos de armazenamento TGZ do Zimbra. O seguinte código de exemplo demonstra o uso da classe [TgzReader](https://apireference.aspose.com/email/java/com.aspose.email/TgzReader) para ler todas as mensagens do arquivo.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ReadAllMessagesFromZimbraTgzStorage-1.java" >}}
## **Salvar mensagens e estrutura de diretório**
Você também pode salvar todas as mensagens com a estrutura de diretórios do arquivo de armazenamento TGZ do Zimbra. Para isso, a classe [TgzReader](https://apireference.aspose.com/email/java/com.aspose.email/TgzReader) fornece um método [ExportTo](https://apireference.aspose.com/email/java/com.aspose.email/TgzReader#exportTo\(java.lang.String\)) que recebe o caminho de saída como parâmetro.

O seguinte trecho de código demonstra o uso do método [TgzReader.ExportTo](https://apireference.aspose.com/email/java/com.aspose.email/TgzReader#exportTo\(java.lang.String\)) para salvar todas as mensagens do arquivo de armazenamento TGZ do Zimbra.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-SaveMessagesFromZimbraTgzStorage-1.java" >}}

## **Exportar itens de calendário e contatos de arquivos de backup do Zimbra**

Aspose.Email torna possível exportar o calendário e os contatos do Zimbra para os formatos iCalendar e VCard. O código de exemplo abaixo mostra como implementar esse recurso em nosso projeto:

```java
try (TgzReader reader = new TgzReader("test2.tgz")) {
    //os arquivos de contatos podem ser encontrados nas subpastas Contatos e Contatos por Email
    //os arquivos de calendário podem ser encontrados na subpasta Calendário
    reader.exportTo("out");
}
```