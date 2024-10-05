---
title: Извлечение содержимого сообщений из электронных писем
type: docs
weight: 30
url: /java/extracting-message-contents-from-emails/
---

## **Отображение информации об электронной почте на экране**

Класс [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getDate()) представляет сообщение электронной почты и позволяет разработчикам получать доступ к свойствам сообщения. Заголовочная информация (обсуждаемая в [Извлечение заголовков электронной почты](#extracting-email-headers)) может быть извлечена и обработана различными способами. Эта статья объясняет, как отобразить выбранную информацию из заголовков электронной почты и тело письма на экране.

1. Создайте экземпляр **MailMessage**.
2. Загрузите сообщение электронной почты в экземпляр **MailMessage**.
3. Отобразите содержимое электронной почты на экране.

Ниже приведен код, демонстрирующий, как загрузить сообщение электронной почты и отобразить его содержимое - от, до, тема и тело письма - на экране.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-DisplayEmailInformation-DisplayEmailInformation.java" >}}

### **Получение времени даты сообщения**

Класс [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) может быть использован для получения даты сообщения в формате UTC или местной часовой зоны. Эта информация может быть обобщена следующим образом:

1. [MailMessage.getDate()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getDate--) - возвращает дату в UTC
1. [MailMessage.getLocalDate()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getLocalDate--) - возвращает дату в местной часовой зоне
2. [MailMessage.isLocalDate](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#isLocalDate--) Возвращает **true**, если **MailMessage.getDate()** находится в местной часовой зоне

## **Извлечение заголовков электронной почты**

Заголовок электронной почты представляет собой набор полей заголовка, определенных стандартом Internet и RFC, включенных в сообщения электронной почты. Заголовок электронной почты можно указать с использованием класса [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). Общие типы заголовков определены в классе [HeaderType](https://reference.aspose.com/email/java/com.aspose.email/headertype/). Это закрытый класс, работающий как обычная перечисляемая функция.

Чтобы извлечь заголовки из электронного письма, выполните следующие действия:

1. Создайте экземпляр класса **MailMessage**.
2. Загрузите сообщение электронной почты в экземпляр класса **MailMessage**.
3. После загрузки сообщения электронной почты мы получим его необработанное содержимое. Сам класс **MailMessage** содержит такие свойства, как From, To, Cc, Subject и так далее. Эти свойства можно извлечь из заголовков.
4. Отобразите необработанное содержимое.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-EmailHeaders-ExtractingEmailHeaders.java" >}}

## **Получение закодированных значений заголовков**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-EmailHeaders-GetDecodedHeaderValueFromHeaderCollection.java" >}}

## **Получение и изменение заголовка привязки ресурсов**

К ресурсам, привязанным к сообщению электронной почты, можно получить доступ и обрабатывать их программно. Метод [getContentDisposition()](https://reference.aspose.com/email/java/com.aspose.email/linkedresource/#getContentDisposition--) класса [LinkedResource](https://reference.aspose.com/email/java/com.aspose.email/linkedresource/) получает заголовок Content-Disposition. Пример кода ниже демонстрирует, как получить доступ и изменить имя файла связанного ресурса:

```java
MailMessage eml = MailMessage.load(fileName);
eml.getLinkedResources().get_Item(0).getContentDisposition().setFileName("changed.png");
```
## **Получение HTML-тела как простого текста**

Класс [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) предоставляет возможность извлечь HTML-тело сообщения как простой текст. Класс **MailMessage** предоставляет метод [GetHtmlBodyText](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getHtmlBodyText-boolean-), который возвращает HTML-тело в виде простого текста. Метод **GetHtmlBodyText** принимает булевый параметр, который указывает, должно ли тело содержать URL или нет. Передача параметра как true означает, что HTML-тело должно содержать URL.

Следующий фрагмент кода демонстрирует использование метода **GetHtmlBodyText** для извлечения HTML-тела электронной почты как простого текста.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-GetHTMLBodyAsPlainText-1.java" >}}