---
title: "Analisando Arquivos de Mensagens do Microsoft Outlook"
url: /pt/java/analisando-arquivos-de-mensagens-do-microsoft-outlook/
weight: 80
type: docs
---


Com o Aspose.Email, você pode analisar mensagens do Microsoft Outlook em apenas algumas linhas de código. Este artigo mostra como. O Aspose.Email possui classes para realizar muitas tarefas de programação com mensagens do Outlook. O exemplo de código abaixo mostra como:

1. Carregar uma mensagem de email.
1. Obter o assunto do email.
1. Obter o nome do remetente.
1. Obter o corpo completo da mensagem.
1. Descobrir se há anexos.
1. Obter os nomes dos arquivos de quaisquer anexos e salvá-los.

O seguinte trecho de código mostra como analisar arquivos de mensagens do Microsoft Outlook.



~~~Java
// O caminho para o diretório de Arquivos e Carregar arquivo de mensagem de email do Microsoft Outlook
String dataDir = "data/";
MapiMessage msg = MapiMessage.fromFile(dataDir + "message3.msg");

// Obter o assunto da mensagem de email, remetente, corpo e contagem de Anexos
System.out.println("Assunto:" + msg.getSubject());
System.out.println("De:" + msg.getSenderName());
System.out.println("Corpo:" + msg.getBody());
System.out.println("Contagem de Anexos:" + msg.getAttachments().size());

// Iterar pelos anexos
for (MapiAttachment attachment : msg.getAttachments()) {
    // Acessar o nome do arquivo do anexo e Salvar anexo
    System.out.println("Anexo:" + attachment.getFileName());
    attachment.save(dataDir + attachment.getLongFileName());
}
~~~