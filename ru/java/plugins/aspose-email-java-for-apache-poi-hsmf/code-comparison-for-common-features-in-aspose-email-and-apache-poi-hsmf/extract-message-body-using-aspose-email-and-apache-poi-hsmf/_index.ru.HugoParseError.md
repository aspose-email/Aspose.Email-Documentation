---  
title: Извлечение тела сообщения с помощью Aspose.Email и Apache POI HSMF  
type: docs  
weight: 20  
url: /java/extract-message-body-using-aspose-email-and-apache-poi-hsmf/  
---  
  
## **Aspose.Email - Извлечение тела сообщения**  
MailMessage представляет собой электронное сообщение и позволяет разработчикам получать доступ к свойствам сообщений электронной почты. Заголовочная информация (обсуждаемая в [Извлечение заголовков электронной почты](http://www.aspose.com/docs/display/emailjava/Extracting+Email+Headers)) может быть извлечена и обработана разными способами.  
  
**Java**  
  
```java  
 MailMessage msg = MailMessage.load(dataDir + "message.msg");  
System.out.println("Body:"+ msg.getBody());  
System.out.println("Text Body:"+ msg.getTextBody());  
System.out.println("Text Body HTML:"+ msg.getHtmlBody());  
```  
## **Apache POI HSMF - Извлечение тела сообщения**  
MAPIMessage может получить доступ к телу сообщения электронной почты.  
  
**Java**  
  
```java  
 MAPIMessage msg = new MAPIMessage(dataDir + "message.msg");  
System.out.println("Text Body:"+ msg.getTextBody());  
```  
## **Скачивание рабочего кода**  
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)  
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)  
## **Скачивание примера кода**  
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/featurescomparison/extractor/)  
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/featurescomparison/extractor)  
  
{{% alert color="primary" %}}  
  
Для получения более подробной информации посетите [Отображение информации об электронной почте на экране](/email/java/display-information-in-custom-order-in-mhtml-files/).  
  
{{% /alert %}}  