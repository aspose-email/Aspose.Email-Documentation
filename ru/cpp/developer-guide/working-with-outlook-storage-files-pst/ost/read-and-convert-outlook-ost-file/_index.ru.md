---
title: "Чтение и преобразование OST-файла Outlook"
url: /ru/cpp/read-and-convert-outlook-ost-file/
weight: 20
type: docs
---

## **Чтение и преобразование OST-файла Outlook**
Aspose.Email для C++ предоставляет API для чтения OST-файлов Microsoft Outlook. OST-файл можно загрузить с диска или в потоковом режиме в экземпляр класса Aspose.Email.Outlook.Pst.PersonalStorage и получить информацию о его содержимом, например о папках, подпапках и сообщениях. Microsoft Outlook создает файл PST для хранения электронных писем, в которых для загрузки сообщений используются почтовые серверы POP3 или IMAP. Он создает OST-файл, когда Microsoft Exchange является почтовым сервером. OST поддерживает большие размеры файлов, чем файлы PST.
### **Чтение OST-файлов**
Процесс чтения OST-файла с помощью Aspose.Email точно такой же, как и при чтении файла PST. Один и тот же код может читать файлы PST и OST: просто укажите правильное имя файла методу PersonalStorage.fromFile (). В следующем фрагменте кода показано, как читать файлы OST.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-PST-ReadingOSTFiles-ReadingOSTFiles.cpp" >}}
### **Преобразование OST в PST**
Aspose.Email позволяет конвертировать OST-файл в PST с помощью одной строки кода. Точно так же файл OST можно создать из файла PST, используя ту же строку кода, что и перечислитель FileFormat. В настоящее время API поддерживает преобразование форматов OST в PST, кроме OST 2013/2016. В следующем фрагменте кода показано, как конвертировать OST в PST.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-PST-ConvertingOSTToPST-ConvertingOSTToPST.cpp" >}}



