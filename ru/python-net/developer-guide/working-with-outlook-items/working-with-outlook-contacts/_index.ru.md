---
title: "Работа с контактами Outlook"
url: /ru/python-net/working-with-outlook-contacts/
weight: 90
type: docs
---


## **Создание, сохранение и чтение контактов**
Как и MAPIMessage, Aspose.Email позволяет создавать контакты Outlook. Класс MapiContact предоставляет все свойства, связанные с контактами, необходимые для создания контакта Outlook. В этой статье показано, как создать, сохранить и прочитать контакт Outlook с помощью класса MapiContact.
### **Создание и сохранение контакта Outlook**
Чтобы создать контакт и сохранить его на диске, выполните следующие действия:

1. Создайте новый объект класса MapiContact.
1. Введите контактную информацию об объекте.
1. Добавьте данные фотографии (если есть).
1. Сохраните контакт в формате MSG или vCard.

В следующем фрагменте кода показано, как создать и сохранить контакт Outlook.

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

# Add a photo
with open(data_dir + "Desert.jpg", "rb") as file:
    buffer = file.read()
    contact.photo = ae.mapi.MapiContactPhoto(buffer, ae.mapi.MapiContactPhotoImageFormat.Jpeg)

# Save the Contact in MSG format
contact.save(data_dir + "MapiContact_out.msg", ae.mapi.ContactSaveFormat.MSG)

# Save the Contact in VCF format
contact.save(data_dir + "MapiContact_out.vcf", ae.mapi.ContactSaveFormat.V_CARD)
```

### **Сохранить контакт в формате VCF версии 3**

Чтобы сохранить контакт в формате VCF версии 3, используйте *version* собственность [VCardSaveOptions](https://reference.aspose.com/email/python-net/aspose.email.personalinfo.vcard/vcardsaveoptions/#vcardsaveoptions-class) класс. Создайте новый экземпляр класса vCardSaveOptions, задайте для свойства версии объекта vCardSaveOptions значение vCardVersion.v30. Это устанавливает версию vCard на 3.0., вызовите *save* метод объекта MapiContact, передающий имя файла «contact.vcf» и объект vCardSaveOptions в качестве параметров. При этом контакт сохраняется в виде файла vCard с указанным именем файла и параметрами. В следующем фрагменте кода показано, как сохранить контакт в формате VCF версии 3:

```python
import aspose.email as ae

contact = ae.mapi.MapiContact()
contact.name_info = ae.mapi.MapiContactNamePropertySet("Bertha", "A.", "Buell")
options = ae.personalinfo.vcard.VCardSaveOptions()
options.version = ae.personalinfo.vcard.VCardVersion.V30
contact.save("contact.vcf", options)
```

### **Чтение контакта MAPI**
Класс MapiContact можно использовать для загрузки контактов в формате Outlook MSG и vCard. В следующем фрагменте кода показано, как загрузить контакты Outlook, сохраненные в формате MSG и VCF, в MapiContact.
#### **Загрузка контакта из MSG**
В следующем фрагменте кода показано, как загрузить контакт из MSG.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-LoadingContactFromMSG-LoadingContactFromMSG.py" >}}
#### **Загрузка контакта из vCard**
В следующем фрагменте кода показано, как загрузить контакт из vCard.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-LoadingContactFromVCF-LoadingContactFromVCF.py" >}}
#### **Загрузка контакта из vCard с указанной кодировкой**
В следующем фрагменте кода показано, как загрузить контакт из vcard с указанной кодировкой.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-LoadingContactFromVCardWithSpecifiedEncoding-LoadingContactFromVCardWithSpecifiedEncoding.py" >}}

#### **Сохранение контактных элементов vCard в указанной кодировке**

При сохранении файла vCard можно указать используемую кодировку символов, обеспечивающую совместимость с символами, отличными от ASCII. Задайте *preferred_text_encoding* свойство объекта vCardSaveOptions, равное «utf-8». В следующем фрагменте кода показано, как реализовать эту функцию в вашем проекте:

```python
import aspose.email as ae

contact = ae.mapi.MapiContact()
contact.name_info = ae.mapi.MapiContactNamePropertySet("Bertha", "A.", "Buell")
options = ae.personalinfo.vcard.VCardSaveOptions()
options.preferred_text_encoding = "utf-8"
contact.save("contact.vcf", options)
```

#### **Сохранение файлов vCard с расширенными полями**

При сохранении файла vCard вы также можете указать параметры, включая использование расширенных полей, представляющих собой дополнительные свойства или атрибуты, которые можно добавить в vCard помимо стандартного набора полей, определенного спецификацией vCard. *use_extensions* собственность [VCardSaveOptions](https://reference.aspose.com/email/python-net/aspose.email.personalinfo.vcard/vcardsaveoptions/#vcardsaveoptions-class) класс позволяет вам это сделать. В следующем фрагменте кода показано, как сохранить файл vCard с расширенными полями:

```python
import aspose.email as ae

contact = ae.mapi.MapiContact()
contact.name_info = ae.mapi.MapiContactNamePropertySet("Bertha", "A.", "Buell")
options = ae.personalinfo.vcard.VCardSaveOptions()
options.use_extensions = True
contact.save("contact.vcf", options)
```
#### **Чтение нескольких контактов в формате vCard**

Чтобы получить список всех контактов с vCard, вам понадобятся следующие методы:

```
# Checks whether VCard source stream contains multiple contacts.
aspose.email.personalinfo.vcard.VCardContact.is_multi_contacts(stream)

# Loads list of all contacts from VCard file.
aspose.email.personalinfo.vcard.VCardContact.load_as_multiple(file_path, encoding)

# Loads list of all contacts from VCard stream.
aspose.email.personalinfo.vcard.VCardContact.load_as_multiple(stream, encoding)
```
Приведенный ниже фрагмент кода продемонстрирует процесс чтения нескольких контактов из файла vCard:

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

## **Отображение контактной информации в MHTML**
Контакт Outlook можно преобразовать в MHTML с помощью API Aspose.Email. В этом примере показано, как vCard загружается в MapiContact, а затем конвертируется в MHTML с помощью MailMessage API.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-RenderingContactInformationToMhtml-RenderingContactInformationToMhtml.py" >}}
