---
title: "Trabalhando com Arquivo In-Place"
url: /pt/java/trabalhando-com-arquivo-in-place/
weight: 150
type: docs
---


## **Arquivos In-Place no Office 365**
Arquivos In-Place no Office 365 fornecem aos usuários espaço adicional de armazenamento. Depois que as caixas de correio de arquivo são ativadas, os usuários podem acessar e armazenar mensagens em sua Caixa de Correio de Arquivo usando o Microsoft Outlook e o Outlook na Web. Quando a caixa de correio com arquivamento In-Place ativado é aberta com o Outlook, a caixa de correio de arquivo é exibida como uma caixa de correio separada.
## **Mover Itens para o Arquivo In-Place**
A API Aspose.Email pode ser usada para mover itens para a caixa de correio de arquivo dos usuários usando o [IEWSClient.archiveItem](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#archiveItem\(java.lang.String,%20java.lang.String\)) método. O método [IEWSClient.archiveItem](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#archiveItem\(java.lang.String,%20java.lang.String\)) fornece quatro sobrecargas que estão listadas abaixo.

- `archiveItem(String sourceFolderUri, Appointment appointment)`
- `archiveItem(String sourceFolderUri, ExchangeTask task)`
- `archiveItem(String sourceFolderUri, MapiMessageItemBase item)`
- `archiveItem(String sourceFolderUri, String uniqueId)`

O exemplo de código dado abaixo demonstra o uso do [`IEWSClient.archiveItem`](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#archiveItem\(java.lang.String,%20java.lang.String\)) método para mover um e-mail para a Caixa de Correio de Arquivo usando o UniqueUri.

~~~Java
NetworkCredential credentials = new NetworkCredential(username, password, domain);
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);

ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    System.out.println("Subject:" + msgInfo.getSubject());
    client.archiveItem(client.getMailboxInfo().getInboxUri(), msgInfo.getUniqueUri());
}
client.dispose();
~~~