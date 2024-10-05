---
title: Список серверных расширений с использованием Pop3Client
type: docs
weight: 30
url: /java/listing-server-extensions-using-pop3client/
---


Aspose.Email [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) позволяет получить расширения сервера, которые поддерживает сервер, такие как IDLE, UNSELECT, QUOTA и т. д. Это помогает определить доступность расширения перед использованием клиента для данной конкретной функции. Метод [getCapabilities()](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#getCapabilities--) возвращает поддерживаемые типы расширений в виде массива строк.

## **Получение серверных расширений**

Следующий пример кода демонстрирует получение серверных расширений с использованием Pop3Client для сервера Gmail.

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