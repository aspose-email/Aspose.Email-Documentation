---
title: "Прочитайте файл Outlook PST и получите информацию о папках и подпапках"
url: /ru/cpp/read-outlook-pst-file-and-get-folders-and-subfolders-information/
weight: 30
type: docs
---

## **Прочитайте файл Outlook PST и получите информацию о папках и подпапках**
Aspose.Email для C++ предоставляет API для чтения файлов Microsoft Outlook PST. PST-файл можно загрузить с диска или в потоковом режиме в экземпляр класса PersonalStorage и получить информацию о его содержимом, например о папках, подпапках и сообщениях. API также предоставляет возможность включать папки поиска при поиске сообщений из папок PST.
### **Загрузка файла PST**
Файл Outlook PST можно загрузить в экземпляре класса PersonalStorage. В следующем фрагменте кода показано, как загрузить файл PST.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-PST-LoadingPSTFile-LoadingPSTFile.cpp" >}}
### **Отображение информации о папках**
После загрузки файла PST в класс PersonalStorage вы можете получить информацию о отображаемом имени файла, корневой папке, подпапках и количестве сообщений. В следующем фрагменте кода показано, как отобразить имя файла PST, папки и количество сообщений в папках.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-PST-DisplayInformationOfPSTFile-DisplayInformationOfPSTFile.cpp" >}}
### **Получение информации о родительской папке из MessageInfo**
В следующем фрагменте кода показано, как получить информацию о родительской папке из MessageInfo.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-RetreiveParentFolderInformationFromMessageInfo-RetreiveParentFolderInformationFromMessageInfo.cpp" >}}
