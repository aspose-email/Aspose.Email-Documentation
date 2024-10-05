---
title: "Список расширений сервера IMAP"
url: /ru/java/listing-imap-server-extensions/
weight: 80
type: docs
---


Aspose.Email [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) позволяет вам получить расширения сервера, которые поддерживает сервер, такие как IDLE, UNSELECT, QUOTA и т.д. Это помогает определить доступность расширения перед использованием клиента для этой конкретной функции. Метод [getCapabilities()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#getCapabilities--) возвращает поддерживаемые типы расширений в виде массива строк. Следующий фрагмент кода показывает, как получить расширения.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Connect and log in to IMAP
ImapClient client = new ImapClient("imap.gmail.com", "username", "password");
String[] getCapabilities = client.getCapabilities();
for (String getCap : getCapabilities) {
    System.out.println(getCap);
}
~~~