---
title: Работа с MAPI свойствами с использованием библиотеки Email C++
linktitle: Работа с MAPI свойствами
type: docs
weight: 60
url: /cpp/working-with-mapi-properties/
description: Используя API библиотеки Email C++, вы можете получать и устанавливать свойства MAPI Outlook и читать именованные свойства MAPI из файла MSG.
---

## **Доступ и установка свойства MAPI Outlook**
Класс MapiProperty представляет собой свойство MAPI, которое содержит:

- Имя: строка, представляющая имя свойства.
- Тег: длинное целое число, представляющее тег свойства.
- Данные: массив байтов, представляющий данные свойства.

### **Получение свойства MAPI с помощью тега свойства MAPI**
Чтобы получить свойства MAPI:

1. Создайте экземпляр MapiMessage, загружая его из файлов или потока.
1. Получите MapiProperty из MapiMessage.Properties по ключам MapiPropertyTag.
1. Получите данные MapiProperty с помощью метода GetX.

Следующий фрагмент кода показывает, как получить свойство MAPI с использованием тега свойства MAPI с библиотекой C++ Email Parser.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-GetMAPIProperty-GetMAPIProperty.cpp" >}}

### **Установка свойств MAPI**
Следующий фрагмент кода показывает, как установить свойства MAPI.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SetMAPIProperties-SetMAPIProperties.cpp" >}}

где определение метода convertDateTime выглядит следующим образом:

``` java

 int64_t filetime = t.ToFileTime();

System::ArrayPtr<uint8_t> d = System::MakeArray<uint8_t>(8, 0);

d[0] = (uint8_t)(filetime & 0xFF);

d[1] = (uint8_t)((filetime & 0xFF00) >> 8);

d[2] = (uint8_t)((filetime & 0xFF0000) >> 16);

d[3] = (uint8_t)((filetime & 0xFF000000) >> 24);

d[4] = (uint8_t)((filetime & 0xFF00000000) >> 32);

d[5] = (uint8_t)((filetime & 0xFF0000000000) >> 40);

d[6] = (uint8_t)((filetime & 0xFF000000000000) >> 48);

d[7] = (uint8_t)(((uint64_t)filetime & 0xFF00000000000000) >> 56);

```

## **Чтение именованных свойств MAPI из файлов MSG Outlook**
Microsoft Outlook поддерживает добавление именованных свойств MAPI в файл MSG. Эти именованные свойства MAPI добавляются пользователем. Вы можете добавить именованное свойство, например "MyProp", в файл MSG, используя Aspose.Email. Эта статья иллюстрирует возможности Aspose.Email:

- Чтение именованных свойств MAPI из файла MSG Outlook
- Чтение свойств из вложений
- Удаление свойств из MSG и вложений

### **Чтение именованных свойств MAPI из файла MSG**
Следующий фрагмент кода показывает, как читать именованные свойства MAPI из файла MSG.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadNamedMAPIProperties-ReadNamedMAPIProperties.cpp" >}}

### **Чтение именованного свойства MAPI из вложения**
Aspose.Email также позволяет вам просматривать свойства MapiAttachment и искать именованное свойство, подобно примеру выше, для MapiMessage. Следующий фрагмент кода показывает, как искать именованное свойство через коллекцию свойств вложения.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadingNamedMAPIPropertyFromAttachment-ReadingNamedMAPIPropertyFromAttachment.cpp" >}}

### **Удаление свойств из MSG и вложений**
Следующий фрагмент кода показывает, как удалить свойства из MSG и вложений.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-RemovePropertiesFromMSGAndAttachments-RemovePropertiesFromMSGAndAttachments.cpp" >}}