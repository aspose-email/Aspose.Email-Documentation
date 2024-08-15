---
title: "Список серверных расширений с помощью Pop3Client"
url: /ru/java/listing-server-extensions-using-pop3client/
weight: 30
type: docs
---


Aspose.Email [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) позволяет получить серверные расширения, поддерживаемые сервером, такие как IDLE, UNSELECT, QUOTA и т. д. Это помогает определить доступность расширения перед использованием клиента для выполнения этой конкретной функции. [getCapabilities()](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#getCapabilities--) метод возвращает поддерживаемые типы расширений в виде строкового массива.

## **Получение серверных расширений**

Следующий пример кода демонстрирует получение серверных расширений с помощью Pop3Client для сервера Gmail.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Connect and log in to POP3
Pop3Client client = new Pop3Client("pop.gmail.com", "username", "password");
client.setSecurityOptions(SecurityOptions.Auto);
client.setPort(995);
String[] getCaps = client.getCapabilities();
for (String item : getCaps) {
    System.out.println(item);
}
~~~
