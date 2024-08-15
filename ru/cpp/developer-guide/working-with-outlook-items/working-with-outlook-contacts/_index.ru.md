---
title: "Работа с контактами Outlook с помощью библиотеки парсера электронной почты C++"
description: "Библиотека C++ Email Parser позволяет создавать, сохранять и читать контакты Outlook и импортировать контакты из форматов файлов MSG и vCard."
url: /ru/cpp/working-with-outlook-contacts/
weight: 90
type: docs
linktitle: "Работа с контактами Outlook"
---

## **Создание, сохранение и чтение контактов**
Как и MAPIMessage, Aspose.Email позволяет создавать контакты Outlook. Класс MapiContact предоставляет все свойства, связанные с контактами, необходимые для создания контакта Outlook. В этой статье показано, как создать, сохранить и прочитать контакт Outlook с помощью класса MapiContact.

### **Создание и сохранение контакта Outlook**
Чтобы создать контакт и сохранить его на диске, выполните следующие действия:

1. Создайте новый объект класса MapiContact.
1. Введите контактную информацию об объекте.
1. Добавьте данные фотографии (если есть).
1. Сохраните контакт в формате MSG или vCard.

В следующем фрагменте кода показано, как создать и сохранить контакт Outlook с помощью библиотеки или API C++ Email Parser.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateAndSaveOutlookContact-CreateAndSaveOutlookContact.cpp" >}}

### **Чтение контакта MAPI**
Класс MapiContact можно использовать для загрузки контактов в формате Outlook MSG и vCard. В следующем фрагменте кода показано, как загрузить контакты Outlook, сохраненные в формате MSG и VCF, в MapiContact.

#### **Загрузка контакта из MSG**
В следующем фрагменте кода показано, как загрузить контакт из MSG.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-LoadingContactFromMSG-LoadingContactFromMSG.cpp" >}}

#### **Загрузка контакта из vCard**
В следующем фрагменте кода показано, как загрузить контакт из vCard.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-LoadingContactFromVCard-LoadingContactFromVCard.cpp" >}}
