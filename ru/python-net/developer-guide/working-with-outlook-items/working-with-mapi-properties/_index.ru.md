---
title: "Работа со свойствами MAPI"
url: /ru/python-net/working-with-mapi-properties/
weight: 60
type: docs
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

В следующем фрагменте кода показано, как получить свойство MAPI с помощью тега свойства MAPI.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-GetMapiProperty-GetMapiProperty.py" >}}

### **Настройка свойств MAPI**

В следующем фрагменте кода показано, как настроить свойства MAPI.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-SetMapiProperties-SetMapiProperties.py" >}}



где определение метода convertDateTime выглядит следующим образом:



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-ConvertDateTime-ConvertDateTime.py" >}}

## **Чтение именованных свойств MAPI из MSG-файлов Outlook**

Aspose.Email предоставляет набор API для работы с файлами MSG, включая извлечение именованных свойств MAPI.

### **Чтение именованных свойств MAPI из файла MSG**

Чтобы прочитать именованные свойства MAPI, мы можем использовать **named_properties** собственность [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/#mapimessage-class) класс. В следующем примере кода показано, как загрузить сообщение, получить все именованные свойства MAPI, выполнить итерацию по каждому свойству для проверки его значения:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("my.msg")

# Get all named MAPI properties
properties = msg.named_properties.values
# Read all properties in foreach loop
for prop in properties:
    #  Read any specific property
    if prop.descriptor.canonical_name == "PidLidSideEffects":
        print(f"{prop.descriptor.canonical_name} = {prop}")
    if prop.descriptor.canonical_name == "PidLidInternetAccountName":
        print(f"{prop.descriptor.canonical_name} = {prop}")
```

## **Чтение именованного свойства MAPI из вложения**

Aspose.Email позволяет получить все именованные свойства MAPI вложения. В следующем примере кода показано, как читать именованные свойства MAPI из вложений:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("my.msg")

# Get all named MAPI properties
attach_properties = msg.attachments[0].named_properties.values
# Read all properties in foreach loop
for prop in attach_properties:
    #  Read any specific property
    if prop.descriptor.name == "AttachmentOriginalUrl":
        print(f"{prop.descriptor.name} = {prop.get_string()}")
    if prop.descriptor.name == "AttachmentWasSavedToCloud":
        print(f"{prop.descriptor.name} = {prop.get_boolean()}")
```

## **Удалить свойства из файлов MSG и вложений**

В этом примере кода показано создание сообщения Outlook MSG с основным содержимым и вложенным файлом сообщения. В нем также показано, как удалить свойство вложения из созданного сообщения.

```python
import aspose.email as ae

# create an MSG
msg = ae.mapi.MapiMessage("from@doamin.com", "to@domain.com", "subject", "body");
msg.set_body_content("<html><body><h1>This is the body content</h1></body></html>", ae.mapi.BodyContentType.HTML)

# load message and add it to created MSG as attachment
attachment = ae.mapi.MapiMessage.load(attach.msg")
msg.attachments.add("Outlook2 Test subject.msg", attachment)

# count of attachment properties before removal
print(f"Before removal = {msg.attachments[0].properties.count}")

# Delete anyone attachment property
msg.attachments[0].remove_property(923467779)

# count of attachment properties after removal
print(f"Before removal = {msg.attachments[0].properties.count}")
```