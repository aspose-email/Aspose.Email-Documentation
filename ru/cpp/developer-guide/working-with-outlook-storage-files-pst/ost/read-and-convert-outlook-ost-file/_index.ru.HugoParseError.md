---
title: Чтение и конвертация файлов Outlook OST
type: docs
weight: 20
url: /cpp/read-and-convert-outlook-ost-file/
---

## **Чтение и конвертация файлов Outlook OST**
Aspose.Email для C++ предоставляет API для чтения файлов Microsoft Outlook OST. Вы можете загрузить файл OST с диска или потока в экземпляр класса Aspose.Email.Outlook.Pst.PersonalStorage и получить информацию о его содержимом, например, папки, подпапки и сообщения. Microsoft Outlook создает файл PST для хранения электронных писем, когда используются почтовые серверы POP3 или IMAP для загрузки сообщений. Он создает файл OST, когда сервером электронной почты является Microsoft Exchange. OST поддерживает большие размеры файлов, чем PST.

### **Чтение файлов OST**
Процесс чтения файла OST с помощью Aspose.Email абсолютно такой же, как и для чтения файла PST. Один и тот же код может читать как PST, так и OST файлы: просто предоставьте правильное имя файла в метод PersonalStorage.FromFile(). Следующий кодовый фрагмент показывает, как читать файлы OST.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-PST-ReadingOSTFiles-ReadingOSTFiles.cpp" >}}

### **Конвертация OST в PST**
Aspose.Email позволяет конвертировать файл OST в PST всего с одной строки кода. Аналогично, файл OST может быть создан из файла PST, используя ту же строку кода с перечислением FileFormat. В настоящее время API поддерживает конвертацию форматов OST в PST, за исключением OST 2013/2016. Следующий кодовый фрагмент показывает, как конвертировать OST в PST.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-PST-ConvertingOSTToPST-ConvertingOSTToPST.cpp" >}}