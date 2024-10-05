---
title: "Работа с контактами Outlook с использованием библиотеки разбора электронной почты C++"
description: "Библиотека разбора электронной почты C++ позволяет вам создавать, сохранять и читать контакты Outlook, а также импортировать контакты из форматов файлов MSG и VCard."
url: /ru/cpp/working-with-outlook-contacts/
weight: 90
type: docs
linktitle: "Работа с контактами Outlook"
---

## **Создание, сохранение и чтение контактов**
Как и MapiMessage, Aspose.Email позволяет вам создавать контакты Outlook. Класс MapiContact предоставляет все свойства, связанные с контактами, необходимые для создания контакта Outlook. Эта статья показывает, как создать, сохранить и прочитать контакт Outlook с использованием класса MapiContact.

### **Создание и сохранение контакта Outlook**
Чтобы создать контакт и сохранить его на диск:

1. Создайте новый объект класса MapiContact.
1. Введите информацию о свойстве контакта.
1. Добавьте данные фотографии (если есть).
1. Сохраните контакт в формате MSG или VCard.

Следующий фрагмент кода показывает, как создать и сохранить контакт Outlook с помощью библиотеки или API разбора электронной почты C++.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateAndSaveOutlookContact-CreateAndSaveOutlookContact.cpp" >}}

### **Чтение MapiContact**
Класс MapiContact может быть использован для загрузки контактов как в формате MSG, так и в формате VCard. Следующий фрагмент кода показывает, как загрузить контакты Outlook, сохраненные в формате MSG и VCF, в MapiContact.

#### **Загрузка контакта из MSG**
Следующий фрагмент кода показывает, как загрузить контакт из MSG.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-LoadingContactFromMSG-LoadingContactFromMSG.cpp" >}}

#### **Загрузка контакта из VCard**
Следующий фрагмент кода показывает, как загрузить контакт из VCard.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-LoadingContactFromVCard-LoadingContactFromVCard.cpp" >}}