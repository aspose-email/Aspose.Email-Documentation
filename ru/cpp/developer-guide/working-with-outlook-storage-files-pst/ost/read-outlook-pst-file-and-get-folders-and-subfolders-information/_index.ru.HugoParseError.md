---
title: Чтение файла PST Outlook и получение информации о папках и подпапках
type: docs
weight: 30
url: /cpp/read-outlook-pst-file-and-get-folders-and-subfolders-information/
---

## **Чтение файла PST Outlook и получение информации о папках и подпапках**
Aspose.Email для C++ предоставляет API для чтения файлов PST Microsoft Outlook. Вы можете загрузить файл PST с диска или потока в экземпляр класса PersonalStorage и получить информацию о его содержимом, например, папках, подпапках и сообщениях. API также предоставляет возможность включать папки поиска при обходе сообщений из папок PST.
### **Загрузка файла PST**
Файл PST Outlook можно загрузить в экземпляр класса PersonalStorage. Следующий фрагмент кода показывает, как загрузить файл PST.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-PST-LoadingPSTFile-LoadingPSTFile.cpp" >}}
### **Отображение информации о папках**
После загрузки файла PST в класс PersonalStorage вы можете получить информацию о его отображаемом имени, корневой папке, подпапках и количестве сообщений. Следующий фрагмент кода показывает, как отобразить имя файла PST, папки и количество сообщений в папках.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-PST-DisplayInformationOfPSTFile-DisplayInformationOfPSTFile.cpp" >}}
### **Получение информации о родительской папке из MessageInfo**
Следующий фрагмент кода показывает, как получить информацию о родительской папке из MessageInfo.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-RetreiveParentFolderInformationFromMessageInfo-RetreiveParentFolderInformationFromMessageInfo.cpp" >}}