---
title: Работа с архивом на месте
type: docs
weight: 150
url: /java/working-with-in-place-archive/
---


## **Архивы на месте в Office 365**
Архивы на месте в Office 365 предоставляют пользователям дополнительное пространство для хранения. После активации архивных почтовых ящиков пользователи могут получать доступ и сохранять сообщения в своем архивном почтовом ящике, используя Microsoft Outlook и Outlook в Интернете. Когда почтовый ящик с включенной архивизацией на месте открывается в Outlook, архивный почтовый ящик отображается как отдельный почтовый ящик.
## **Перемещение элементов в архив на месте**
API Aspose.Email можно использовать для перемещения элементов в архивный почтовый ящик пользователей с помощью метода [IEWSClient.archiveItem](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#archiveItem\(java.lang.String,%20java.lang.String\)). Метод [IEWSClient.archiveItem](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#archiveItem\(java.lang.String,%20java.lang.String\)) предлагает четыре перегрузки, которые перечислены ниже.

- `archiveItem(String sourceFolderUri, Appointment appointment)`
- `archiveItem(String sourceFolderUri, ExchangeTask task)`
- `archiveItem(String sourceFolderUri, MapiMessageItemBase item)`
- `archiveItem(String sourceFolderUri, String uniqueId)`

Пример кода, приведенный ниже, демонстрирует использование метода [`IEWSClient.archiveItem`](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#archiveItem\(java.lang.String,%20java.lang.String\)) для перемещения электронного письма в архивный почтовый ящик с использованием UniqueUri.



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