---
title: "Извлечение содержимого сообщений из электронных писем"
url: /ru/java/extracting-message-contents-from-emails/
weight: 30
type: docs
---

## **Отображение информации об электронной почте на экране**

The [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getDate()) представляет собой сообщение электронной почты и предоставляет разработчикам доступ к свойствам сообщения электронной почты. Информация в заголовке (обсуждается в [Извлечение заголовков электронной почты](#extracting-email-headers)) можно извлекать и манипулировать им по-разному. В этой статье объясняется, как отображать выбранную информацию в заголовке электронного письма и текст письма на экране.

1. Создайте экземпляр **MailMessage**.
2. Загрузите сообщение электронной почты в **MailMessage** instance.
3. Отобразите содержимое электронной почты на экране.

В приведенном ниже коде показано, как загрузить сообщение электронной почты и отобразить его содержимое (от, до, тему и текст письма) на экране.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-DisplayEmailInformation-DisplayEmailInformation.java" >}}

### **Получение даты и времени сообщения**

The [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) класс можно использовать для получения даты сообщения в формате UTC или местного часового пояса. Эту информацию можно резюмировать следующим образом:

1. [MailMessage.getDate()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getDate--) - дата возврата в формате UTC
1. [MailMessage.getLocalDate()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getLocalDate--) - возвращает дату в местном часовом поясе
2. [MailMessage.isLocalDate](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#isLocalDate--) Returns **true**, если **MailMessage.getDate()** находится в местном часовом поясе

## **Извлечение заголовков электронной почты**

Заголовок электронного письма представляет собой стандартный набор полей заголовков, определенных в Интернете и RFC, включенных в сообщения электронной почты Интернета. Заголовок электронного письма можно указать с помощью [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) класс. Общие типы заголовков определены в поле [HeaderType](https://reference.aspose.com/email/java/com.aspose.email/headertype/) класс. Это закрытый класс, работающий как обычное перечисление.

Чтобы извлечь заголовки из электронного письма, выполните следующие действия:

1. Создайте экземпляр **MailMessage** class.
2. Загрузите сообщение электронной почты в экземпляре **MailMessage** class.
3. После загрузки сообщения электронной почты мы получим его необработанное содержимое. **MailMessage** Сам класс содержит такие свойства, как From, To, Cc, Subject и т. д. Эти свойства можно извлечь из заголовков.
4. Отобразите необработанный контент.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-EmailHeaders-ExtractingEmailHeaders.java" >}}

## **Получите декодированные значения заголовков**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-EmailHeaders-GetDecodedHeaderValueFromHeaderCollection.java" >}}

## **Получите и измените заголовок размещения связанных ресурсов**

Связанный ресурс можно получить доступ к связанному ресурсу и управлять им программно в объекте сообщения электронной почты. [getContentDisposition()](https://reference.aspose.com/email/java/com.aspose.email/linkedresource/#getContentDisposition--) метод [LinkedResource](https://reference.aspose.com/email/java/com.aspose.email/linkedresource/) класс получает заголовок Content-Disposition. В приведенном ниже примере кода показано, как получить доступ к файлу связанного ресурса и изменить его:

```java
MailMessage eml = MailMessage.load(fileName);
eml.getLinkedResources().get_Item(0).getContentDisposition().setFileName("changed.png");
```
## **Получить текст HTML в виде обычного текста**

The [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) класс предоставляет возможность извлечения HTML-тела сообщения в виде обычного текста. **MailMessage** класс предоставляет [GetHtmlBodyText](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getHtmlBodyText-boolean-) метод, который возвращает тело HTML в виде обычного текста. **GetHtmlBodyText** метод принимает логический параметр, указывающий, должно ли тело содержать URL-адреса или нет. Передача параметру значения true означает, что тело HTML должно содержать URL-адреса.

Следующий фрагмент кода демонстрирует использование **GetHtmlBodyText** метод извлечения HTML-тела электронного письма в виде обычного текста.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-GetHTMLBodyAsPlainText-1.java" >}}
