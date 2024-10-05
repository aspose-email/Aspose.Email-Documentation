---
title: Извлечение заголовков электронной почты в Python
type: docs
weight: 50
url: /java/extracting-email-headers-in-python/
---

## **Aspose.Email - Извлечение заголовков электронной почты**
Чтобы извлечь заголовки электронной почты, используя **Aspose.Email Java для Python**, используйте следующий код.

**Python код**

``` python



\# Инициализировать и загрузить существующий EML файл, указав формат сообщения

mailMessage = self.MailMessage

message = mailMessage.load(self.dataDir + "Message.eml")

print "Печать всех заголовков:"

\# Вывести все заголовки

i=0

while (i < message.getHeaders().getCount()):

    print message.getHeaders().get(i)

    i += 1

```
## **Скачать работающий код**
Скачать **Извлечение заголовков электронной почты (Aspose.Email)** с любого из нижеупомянутых сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)