---
title: "Настройка заголовков писем в Ruby"
url: /ru/java/customizing-email-headers-in-ruby/
weight: 30
type: docs
---

## **Aspose.Email - Настройка заголовков писем**
Для настройки заголовков электронной почты с помощью **Aspose.Электронная почта Java для Ruby**, просто вызовите **CustomizeEmailHeaders** модуль. Здесь вы можете увидеть пример кода.

**Код Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'



\# Create a new instance of MailMessage class

message = Rjb::import('com.aspose.email.MailMessage').new

\# Set subject of the message

message.setSubject("New message created by Aspose.Email for Java")

\# Set Html body

message.setHtmlBody("<b>This line is in bold.</b> <br/> <br/>" +

        "<font color=blue>This line is in blue color</font>")

\# Set sender information

message.setFrom(Rjb::import('com.aspose.email.MailAddress').new("from@domain.com", "Sender Name", false))

\# Add TO recipients

message.getTo().add(Rjb::import('com.aspose.email.MailAddress').new("to@domain.com", "Recipient 1", false))

\# Message subject

message.setSubject("Customizing Email Headers")

\# Specify Date

calendar = Rjb::import('java.util.Calendar').getInstance(Rjb::import('java.util.TimeZone').getTimeZone("GMT"))

date = calendar.getTime()

message.setDate(date)

\# Specify XMailer

message.setXMailer("Aspose.Email")

\# Specify Secret Header

message.getHeaders().add("secret-header", "mystery")

\# Save message to disc

message.save(data_dir + "MsgHeaders.msg", Rjb::import('com.aspose.email.MessageFormat').getMsg())

\# Display Status

puts "Customized message headers Successfully."

```
## **Загрузить рабочий код**
Download **Настройка заголовков электронной почты (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/customizeemailheaders.rb)
