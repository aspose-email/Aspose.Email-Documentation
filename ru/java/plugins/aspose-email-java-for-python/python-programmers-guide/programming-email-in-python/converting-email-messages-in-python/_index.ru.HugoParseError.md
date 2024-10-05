---  
title: Конвертация электронных сообщений в Python  
type: docs  
weight: 10  
url: /java/converting-email-messages-in-python/  
---  
  
## **Aspose.Email - Конвертация электронных сообщений**  
Чтобы конвертировать электронные сообщения с использованием **Aspose.Email Java for Python**, используйте следующий код.  
  
**Python Код**  
  
``` python  
  
 # Инициализация и загрузка существующего EML файла, указав формат сообщения  
  
mailMessage = self.MailMessage  
  
eml = mailMessage.load(self.dataDir + "Message.eml")  
  
\# Сохранить электронное сообщение на диск в формате Unicode  
  
saveOptions= self.SaveOptions  
  
eml.save(self.dataDir + "AnEmail.msg", saveOptions.getDefaultMsgUnicode())  
  
\# Показать статус  
  
print "Электронное сообщение успешно конвертировано в msg."  
  
```  
## **Скачать исполняемый код**  
Скачать **Конвертацию электронных сообщений (Aspose.Email)** с любого из нижеупомянутых сайтов социального программирования:  
  
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)  
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)  