---
title: "Работа со свойствами MAPI с помощью библиотеки Email C++"
description: "Используя API библиотеки электронной почты C++, вы можете получить доступ к свойствам Outlook MAPI и настроить их, а также прочитать именованные свойства MAPI из файла MSG."
url: /ru/cpp/working-with-mapi-properties/
weight: 60
type: docs
linktitle: "Работа со свойствами MAPI"
---

## **Доступ к свойству Outlook MAPI и его настройка**
Класс MapiProperty представляет собой свойство MAPI, которое содержит:

- Имя: строка, представляющая имя свойства.
- Тег: длинное значение, обозначающее тег свойства.
- Данные: массив байтов, представляющий данные свойства.

### **Получение свойства MAPI с помощью тега свойства MAPI**
Чтобы получить свойства MAPI, выполните следующие действия:

1. Создайте экземпляр MapiMessage, загрузив его из файлов или потока.
1. Получите свойство MAPI из приложения MapiMessage.Properties с помощью ключей MAPIpropertyTag.
1. Получите данные свойства MapiProperty с помощью метода getX.

В следующем фрагменте кода показано, как получить свойство MAPI с помощью тега свойств MAPI в библиотеке C++ Email Parser.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-GetMAPIProperty-GetMAPIProperty.cpp" >}}

### **Настройка свойств MAPI**
В следующем фрагменте кода показано, как настроить свойства MAPI.

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

## **Чтение именованных свойств MAPI из MSG-файлов Outlook**
Microsoft Outlook поддерживает добавление именованных свойств MAPI в файл MSG. Эти именованные свойства MAPI добавляются пользователем. Вы можете добавить именованное свойство, например «MyProp», в файл MSG с помощью Aspose.Email. Эта статья иллюстрирует возможности Aspose.Email по:

- Чтение свойств MAPI имени из файла Outlook MSG
- Чтение свойств из вложений
- Удалить свойства из файлов MSG и вложений

### **Чтение именованных свойств MAPI из файла MSG**
В следующем фрагменте кода показано, как читать именованные свойства MAPI из файла MSG.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadNamedMAPIProperties-ReadNamedMAPIProperties.cpp" >}}

### **Чтение именованного свойства MAPI из вложения**
Aspose.Email также позволяет просматривать свойства mapiAttachment и искать именованное свойство, аналогично приведенному выше примеру, для MapiMessage. В следующем фрагменте кода показано, как искать именованное свойство в коллекции свойств вложения.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadingNamedMAPIPropertyFromAttachment-ReadingNamedMAPIPropertyFromAttachment.cpp" >}}

### **Удалить свойства из файлов MSG и вложений**
В следующем фрагменте кода показано, как удалить свойства из файлов MSG и вложений.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-RemovePropertiesFromMSGAndAttachments-RemovePropertiesFromMSGAndAttachments.cpp" >}}
