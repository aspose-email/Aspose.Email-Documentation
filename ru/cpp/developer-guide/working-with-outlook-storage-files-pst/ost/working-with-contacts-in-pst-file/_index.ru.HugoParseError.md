---
title: Работа с контактами в PST файле
type: docs
weight: 60
url: /cpp/working-with-contacts-in-pst-file/
---

## **Добавление контакта в PST**
С помощью Aspose.Email вы можете добавить MapiContact в подкаталог Contacts файла PST, который вы создали или загрузили. Ниже приведены шаги для добавления MapiContact в PST:

1. Создайте объект MapiContact.
1. Установите свойства MapiContact, используя различные конструкторы и методы.
1. Создайте PST, используя метод PersonalStorage.Create().
1. Создайте предопределенную папку (Contacts) в корне файла PST, получив доступ к корневой папке и затем вызвав метод AddMapiMessageItem().

Следующий фрагмент кода показывает, как создать MapiContact и затем добавить его в папку контактов только что созданного файла PST.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateNewMapiContactAndAddToContactsSubfolder-CreateNewMapiContactAndAddToContactsSubfolder.cpp" >}}
## **Сохранение информации о контактах из файла PST в формате MSG**
В этой статье объясняется, как получить доступ к информации о контактах из файла PST Outlook и сохранить контакт на диск в формате MSG. Классы PersonalStorage и MapiContact используются для получения и отображения информации о контакте. Шаги для получения информации о контакте следующие:

1. Загрузите файл PST в классе PersonalStorage.
1. Просмотрите папку Contacts.
1. Получите содержимое папки Contacts, чтобы получить коллекцию сообщений.
1. Пройдите через коллекцию сообщений.
1. Вызовите метод PersonalStorage.ExtractContactInfo(), чтобы получить информацию о контакте в классе MapiContact. Используйте свойства класса MapiContact для доступа к информации о контакте.
1. Вызовите метод PersonalStorage.ExtractMessage(), чтобы получить информацию о контакте в классе MapiMessage.
1. Вызовите метод MapiMessage.Save(), чтобы сохранить контакт на диск в формате MSG.

Следующий фрагмент кода показывает, как извлечь всю информацию о контакте из файла PST и сохранить на диск в формате MSG.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AccessContactInformation-AccessContactInformation.cpp" >}}
## **Сохранение информации о контактах из файла PST в формате VCF**
В этой статье показано, как получить доступ к информации о контактах из файла PST Microsoft Outlook и сохранить контакт на диск в формате vCard (VCF). Используйте классы PersonalStorage и MapiContact для получения информации о контактах из файла PST. Чтобы получить информацию о контакте:

1. Загрузите файл PST в классе PersonalStorage.
1. Просмотрите папку Contacts.
1. Получите содержимое папки Contacts, чтобы получить коллекцию сообщений.
1. Пройдите через коллекцию сообщений.
1. Вызовите метод PersonalStorage.ExtractMessage(), чтобы получить информацию о контакте в классе MapiContact.
1. Используйте различные свойства класса MapiContact для доступа к информации о контакте.

Программа ниже загружает файл PST с диска и сохраняет все контакты в формате vCard (VCF). Файлы VCF можно затем использовать в любой другой программе, которая может загрузить стандартный файл контактов vCard. Если вы откроете любой файл VCF в Microsoft Outlook, он будет выглядеть, как на скриншоте ниже.

|![todo:image_alt_text](working-with-contacts-in-pst-file_1.png)|
| :- |
Следующий фрагмент кода показывает, как экспортировать контакты из Outlook PST в формат vCard (VCF).



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SaveContactInformation-SaveContactInformation.cpp" >}}
## **Работа с распределительными списками**
Можно создать распределительный список, используя API Aspose.Email, который представляет собой коллекцию нескольких контактов. Распределительный список может быть сохранен на диск в формате Outlook MSG и может быть просмотрен/изменен, открыв его в MS Outlook.
### **Создание и сохранение распределительного списка**
Следующий фрагмент кода показывает, как создать и сохранить распределительный список.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateDistributionListInPST-CreateDistributionListInPST.cpp" >}}
### **Чтение распределительного списка из PST**
Следующий фрагмент кода показывает, как прочитать распределительный список из PST.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadingDistributionListFromPST-ReadingDistributionListFromPST.cpp" >}}