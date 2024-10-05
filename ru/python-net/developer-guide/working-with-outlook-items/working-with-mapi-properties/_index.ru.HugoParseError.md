---
title: Работа с свойствами MAPI
type: docs
weight: 60
url: /python-net/working-with-mapi-properties/
---


## **Доступ и установка свойств MAPI Outlook**

Класс MapiProperty представляет свойство MAPI, которое содержит:

- Имя: строка, представляющая имя свойства.
- Тег: длинное число, представляющее тег свойства.
- Данные: массив байтов, представляющий данные свойства.

### **Получение свойства MAPI с использованием тега свойства MAPI**

Для получения свойств MAPI:

1. Создайте экземпляр MapiMessage, загружая его из файлов или потока.
1. Получите MapiProperty из MapiMessage.Properties по ключам MapiPropertyTag.
1. Получите данные MapiProperty с помощью метода GetX.

Следующий фрагмент кода демонстрирует, как получить свойство MAPI с использованием тега свойства MAPI.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-GetMapiProperty-GetMapiProperty.py" >}}

### **Установка свойств MAPI**

Следующий фрагмент кода демонстрирует, как установить свойства MAPI.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-SetMapiProperties-SetMapiProperties.py" >}}



где определение метода convertDateTime выглядит следующим образом:



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-ConvertDateTime-ConvertDateTime.py" >}}

## **Чтение именованных свойств MAPI из файлов MSG Outlook**

Aspose.Email предоставляет набор API для работы с файлами MSG, включая извлечение именованных свойств MAPI.

### **Чтение именованных свойств MAPI из файла MSG**

Для чтения именованных свойств MAPI мы можем использовать свойство **named_properties** класса [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/#mapimessage-class). Следующий образец кода демонстрирует, как загрузить сообщение, извлечь все именованные свойства MAPI, итерировать по каждому свойству, чтобы проверить его значение:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("my.msg")

# Получить все именованные свойства MAPI
properties = msg.named_properties.values
# Прочитать все свойства в цикле foreach
for prop in properties:
    #  Прочитать конкретное свойство
    if prop.descriptor.canonical_name == "PidLidSideEffects":
        print(f"{prop.descriptor.canonical_name} = {prop}")
    if prop.descriptor.canonical_name == "PidLidInternetAccountName":
        print(f"{prop.descriptor.canonical_name} = {prop}")
```

## **Чтение именованного свойства MAPI из вложения**

Aspose.Email позволяет извлекать все именованные свойства MAPI вложения. Следующий образец кода демонстрирует, как читать именованные свойства MAPI из вложений:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("my.msg")

# Получить все именованные свойства MAPI
attach_properties = msg.attachments[0].named_properties.values
# Прочитать все свойства в цикле foreach
for prop in attach_properties:
    #  Прочитать конкретное свойство
    if prop.descriptor.name == "AttachmentOriginalUrl":
        print(f"{prop.descriptor.name} = {prop.get_string()}")
    if prop.descriptor.name == "AttachmentWasSavedToCloud":
        print(f"{prop.descriptor.name} = {prop.get_boolean()}")
```

## **Удаление свойств из MSG и вложений**

Этот образец кода демонстрирует создание сообщения Outlook MSG с содержимым тела и прикрепленным файлом сообщения. Он также демонстрирует, как удалить свойство вложения из созданного сообщения.

```python
import aspose.email as ae

# создаем MSG
msg = ae.mapi.MapiMessage("from@doamin.com", "to@domain.com", "subject", "body");
msg.set_body_content("<html><body><h1>This is the body content</h1></body></html>", ae.mapi.BodyContentType.HTML)

# загружаем сообщение и добавляем его в созданный MSG как вложение
attachment = ae.mapi.MapiMessage.load("attach.msg")
msg.attachments.add("Outlook2 Test subject.msg", attachment)

# количество свойств вложения перед удалением
print(f"Before removal = {msg.attachments[0].properties.count}")

# Удалить любое свойство вложения
msg.attachments[0].remove_property(923467779)

# количество свойств вложения после удаления
print(f"Before removal = {msg.attachments[0].properties.count}")
```