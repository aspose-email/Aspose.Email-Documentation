---
title: "Список серверных расширений IMAP"
url: /ru/java/listing-imap-server-extensions/
weight: 80
type: docs
---


Aspose.Email [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) позволяет получить серверные расширения, поддерживаемые сервером, такие как IDLE, UNSELECT, QUOTA и т. д. Это помогает определить доступность расширения перед использованием клиента для выполнения этой конкретной функции. [getCapabilities()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#getCapabilities--) метод возвращает поддерживаемые типы расширений в виде строкового массива. В следующем фрагменте кода показано, как извлекать расширения.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Connect and log in to IMAP
ImapClient client = new ImapClient("imap.gmail.com", "username", "password");
String[] getCapabilities = client.getCapabilities();
for (String getCap : getCapabilities) {
    System.out.println(getCap);
}
~~~
