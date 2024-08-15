---
title: "Работа с локальным архивом"
url: /ru/java/working-with-in-place-archive/
weight: 150
type: docs
---


## **Местные архивы в Office 365**
Местовые архивы в Office 365 предоставляют пользователям дополнительное пространство для хранения. После включения архивных почтовых ящиков пользователи могут получать доступ к сообщениям и хранить их в своем архивном почтовом ящике с помощью Microsoft Outlook и Outlook в Интернете. Если почтовый ящик с включенной архивацией на месте открывается в Outlook, архивный почтовый ящик отображается как отдельный почтовый ящик.
## **Переместить элементы в локальный архив**
Aspose.Email API можно использовать для перемещения элементов в архивный почтовый ящик пользователей с помощью [IEWSClient.archiveItem](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#archiveItem\(java.lang.String,%20java.lang.String\)) method. [IEWSClient.archiveItem](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#archiveItem\(java.lang.String,%20java.lang.String\)) Метод обеспечивает четыре перегрузки, которые перечислены ниже.

- `archiveItem(String sourceFolderUri, Appointment appointment)`
- `archiveItem(String sourceFolderUri, ExchangeTask task)`
- `archiveItem(String sourceFolderUri, MapiMessageItemBase item)`
- `archiveItem(String sourceFolderUri, String uniqueId)`

Приведенный ниже пример кода демонстрирует использование [`IEWSClient.archiveItem`](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#archiveItem\(java.lang.String,%20java.lang.String\)) метод перемещения электронной почты в архивный почтовый ящик с помощью uniqueURI.



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
