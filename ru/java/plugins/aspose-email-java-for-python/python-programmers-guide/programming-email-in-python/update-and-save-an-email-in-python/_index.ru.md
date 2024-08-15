---
title: "Обновите и сохраните электронное письмо в Python"
url: /ru/java/update-and-save-an-email-in-python/
weight: 80
type: docs
---

## **Aspose.Email - Обновите и сохраните электронное письмо**
Чтобы обновить и сохранить электронное письмо, используя **Aspose.Электронная почта Java для Python**, Используйте следующий код.

**Код Python**

``` python



\# Initialize and Load an existing MSG file by specifying the MessageFormat

mailMessage = self.MailMessage

email = mailMessage.load(self.dataDir + "Message.msg")

\# Initialize a String variable to get the Email Subject

subject = email.getSubject()

\# Append some more information to Subject

subject = subject + " This text is added to the existing subject"

\# Set the Email Subject

email.setSubject('This text is added to the existing subject')

\# Initialize a String variable to get the Email's HTML Body

body = email.getHtmlBody()

\# Apppend some more information to the Body variable

body = body + "<br> This text is added to the existing body"

\# Set the Email Body

email.setHtmlBody(body)

\# Initialize MailAddressCollection object

contacts = self.MailAddressCollection()

\# Retrieve Email's TO list

contacts = email.getTo()

\# Add another email address to collection

contacts.add("to1@domain.com")

\# Set the collection as Email's TO list

email.setTo(contacts)

\# Initialize MailAddressCollection

contacts = self.MailAddressCollection()

\# Retrieve Email's CC list

contacts = email.getCC()

\# Add another email address to collection

contacts.add("cc2@domain.com")

\# Set the collection as Email's CC list

email.setCC(contacts)

\# Save the Email message to disk by specifying the MessageFormat

mailMessageSaveType = self.MailMessageSaveType

email.save(self.dataDir + "UpdateMessage.msg", mailMessageSaveType.getOutlookMessageFormat())

\# Display Status

print "Updated email message Successfully."

```
## **Загрузить рабочий код**
Download **Обновить и сохранить электронное письмо (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)
