---
title: "Извлечение заголовков электронной почты в Python"
url: /ru/java/extracting-email-headers-in-python/
weight: 50
type: docs
---

## **Aspose.Email - Извлечение заголовков писем**
Извлечение заголовков электронных писем с помощью **Aspose.Электронная почта Java для Python**, Используйте следующий код.

**Код Python**

``` python



\# Initialize and Load an existing EML file by specifying the MessageFormat

mailMessage = self.MailMessage

message = mailMessage.load(self.dataDir + "Message.eml")

print "Printing all Headers:"

\# Print out all the headers

i=0

while (i < message.getHeaders().getCount()):

    print message.getHeaders().get(i)

    i += 1

```
## **Загрузить рабочий код**
Download **Извлечение заголовков электронной почты (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)
