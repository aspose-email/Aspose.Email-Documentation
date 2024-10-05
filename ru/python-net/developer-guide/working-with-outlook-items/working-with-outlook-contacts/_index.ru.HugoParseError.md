---
title: Работа с контактами Outlook
type: docs
weight: 90
url: /python-net/working-with-outlook-contacts/
---


## **Создание, Сохранение и Чтение Контактов**
Как и MapiMessage, Aspose.Email позволяет создавать контакты Outlook. Класс MapiContact предоставляет все связанные с контактом свойства, необходимые для создания контакта Outlook. Эта статья показывает, как создать, сохранить и прочитать контакт Outlook с использованием класса MapiContact.
### **Создание и Сохранение Контакта Outlook**
Чтобы создать контакт и сохранить его на диск:

1. Создайте новый объект класса MapiContact.
1. Введите информацию о свойствах контакта.
1. Добавьте данные фотографии (если есть).
1. Сохраните контакт в формате MSG или VCard.

Следующий фрагмент кода показывает, как создать и сохранить контакт Outlook.

```py
import aspose.email as ae

data_dir = "path/to/data/directory"

contact = ae.mapi.MapiContact()
contact.name_info = ae.mapi.MapiContactNamePropertySet("Bertha", "A.", "Buell")
contact.professional_info = ae.mapi.MapiContactProfessionalPropertySet("Awthentikz", "Social work assistant")
contact.personal_info.personal_home_page = "B2BTies.com"
contact.physical_addresses.work_address.address = "Im Astenfeld 59 8580 EDELSCHROTT"
contact.electronic_addresses.email1 = ae.mapi.MapiContactElectronicAddress("Experwas", "SMTP", "BerthaABuell@armyspy.com")
contact.telephones = ae.mapi.MapiContactTelephonePropertySet("06605045265")
contact.personal_info.children = ["child1", "child2", "child3"]
contact.categories = ["category1", "category2", "category3"]
contact.mileage = "Some test mileage"
contact.billing = "Test billing information"
contact.other_fields.journal = True
contact.other_fields.private = True
contact.other_fields.reminder_topic = "Test topic"
contact.other_fields.user_field1 = "ContactUserField1"
contact.other_fields.user_field2 = "ContactUserField2"
contact.other_fields.user_field3 = "ContactUserField3"
contact.other_fields.user_field4 = "ContactUserField4"

# Добавить фотографию
with open(data_dir + "Desert.jpg", "rb") as file:
    buffer = file.read()
    contact.photo = ae.mapi.MapiContactPhoto(buffer, ae.mapi.MapiContactPhotoImageFormat.Jpeg)

# Сохранить контакт в формате MSG
contact.save(data_dir + "MapiContact_out.msg", ae.mapi.ContactSaveFormat.MSG)

# Сохранить контакт в формате VCF
contact.save(data_dir + "MapiContact_out.vcf", ae.mapi.ContactSaveFormat.V_CARD)
```

### **Сохранение Контакта в Формате VCF Версия 3**

Чтобы сохранить контакт в формате VCF Версия 3, используйте свойство *version* класса [VCardSaveOptions](https://reference.aspose.com/email/python-net/aspose.email.personalinfo.vcard/vcardsaveoptions/#vcardsaveoptions-class). Создайте новый экземпляр класса VCardSaveOptions, установите свойство version объекта VCardSaveOptions в VCardVersion.V30. Это устанавливает версию vCard на 3.0., вызовите метод *save* объекта MapiContact, передав имя файла "contact.vcf" и объект VCardSaveOptions в качестве параметров. Это сохранит контакт как файл vCard с указанным именем файла и параметрами. Следующий фрагмент кода показывает, как сохранить контакт в формате VCF Версия 3:

```python
import aspose.email as ae

contact = ae.mapi.MapiContact()
contact.name_info = ae.mapi.MapiContactNamePropertySet("Bertha", "A.", "Buell")
options = ae.personalinfo.vcard.VCardSaveOptions()
options.version = ae.personalinfo.vcard.VCardVersion.V30
contact.save("contact.vcf", options)
```

### **Чтение MapiContact**
Класс MapiContact можно использовать для загрузки контактов в форматах Outlook MSG и VCard. Следующий фрагмент кода показывает, как загрузить контакты Outlook, сохраненные в формате MSG и VCF, в MapiContact.
#### **Загрузка Контакта из MSG**
Следующий фрагмент кода показывает, как загрузить контакт из MSG.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-LoadingContactFromMSG-LoadingContactFromMSG.py" >}}
#### **Загрузка Контакта из VCard**
Следующий фрагмент кода показывает, как загрузить контакт из vCard.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-LoadingContactFromVCF-LoadingContactFromVCF.py" >}}
#### **Загрузка Контакта из VCard с Указанным Кодированием**
Следующий фрагмент кода показывает, как загрузить контакт из vCard с указанным кодированием.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-LoadingContactFromVCardWithSpecifiedEncoding-LoadingContactFromVCardWithSpecifiedEncoding.py" >}}

#### **Сохранение Элементов Контакта VCard с Указанным Кодированием**

При сохранении файла vCard можно указать кодировку символов, которая будет использоваться для обеспечения совместимости с не-ASCII символами. Установите свойство *preferred_text_encoding* объекта VCardSaveOptions в "utf-8". Следующий фрагмент кода показывает, как внедрить эту функцию в ваш проект:

```python
import aspose.email as ae

contact = ae.mapi.MapiContact()
contact.name_info = ae.mapi.MapiContactNamePropertySet("Bertha", "A.", "Buell")
options = ae.personalinfo.vcard.VCardSaveOptions()
options.preferred_text_encoding = "utf-8"
contact.save("contact.vcf", options)
```

#### **Сохранение Файлов VCard с Расширенными Полями**

При сохранении файла vCard вы также можете указать параметры, включая использование расширенных полей, то есть дополнительных свойств или атрибутов, которые могут быть добавлены в vCard помимо стандартного набора полей, определенных спецификацией vCard. Свойство *use_extensions* класса [VCardSaveOptions](https://reference.aspose.com/email/python-net/aspose.email.personalinfo.vcard/vcardsaveoptions/#vcardsaveoptions-class) позволяет вам это сделать. Следующий фрагмент кода показывает, как сохранить файл VCard с расширенными полями:

```python
import aspose.email as ae

contact = ae.mapi.MapiContact()
contact.name_info = ae.mapi.MapiContactNamePropertySet("Bertha", "A.", "Buell")
options = ae.personalinfo.vcard.VCardSaveOptions()
options.use_extensions = True
contact.save("contact.vcf", options)
```
#### **Чтение Множественных Контактов в Формате VCard**

Вам понадобятся следующие методы, чтобы получить список всех контактов из VCard:

```
# Проверяет, содержит ли поток источника VCard несколько контактов.
aspose.email.personalinfo.vcard.VCardContact.is_multi_contacts(stream)

# Загружает список всех контактов из VCard файла.
aspose.email.personalinfo.vcard.VCardContact.load_as_multiple(file_path, encoding)

# Загружает список всех контактов из VCard потока.
aspose.email.personalinfo.vcard.VCardContact.load_as_multiple(stream, encoding)
```
Следующий фрагмент кода продемонстрирует процесс чтения нескольких контактов из файла VCard:

```python
import aspose.email as ae

contact = ae.mapi.MapiContact()
contact.name_info = ae.mapi.MapiContactNamePropertySet("Bertha", "A.", "Buell")
options = ae.personalinfo.vcard.VCardSaveOptions()
options.use_extensions = True
contact.save("contact.vcf", options)

if ae.personalinfo.vcard.VCardContact.is_multi_contacts("contact.vcf"):
    ae.personalinfo.vcard.VCardContact.load_as_multiple("contact.vcf")
```

## **Отображение Информации о Контакте в MHTML**
Контакт Outlook можно конвертировать в MHTML с использованием API Aspose.Email. Этот пример показывает, как VCard загружается в MapiContact, а затем конвертируется в MHTML с помощью API MailMessage.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-RenderingContactInformationToMhtml-RenderingContactInformationToMhtml.py" >}}