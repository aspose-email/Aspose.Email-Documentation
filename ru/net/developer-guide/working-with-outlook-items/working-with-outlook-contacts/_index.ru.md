---
title: "Работа с контактами Outlook"
url: /ru/net/working-with-outlook-contacts/
weight: 90
type: docs
---


## **Создание, сохранение и чтение контактов**

Как и MAPIMessage, Aspose.Email позволяет создавать контакты Outlook. [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) класс предоставляет все свойства, связанные с контактами, необходимые для создания контакта Outlook. В этой статье показано, как создать, сохранить и прочитать контакт Outlook с помощью [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) class.

### **Создание и сохранение контакта Outlook**

Чтобы создать контакт и сохранить его на диске, выполните следующие действия:

1. Создайте новый объект из [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) class.
1. Введите контактную информацию об объекте.
1. Добавьте данные фотографии (если есть).
1. Сохраните контакт в формате MSG или vCard.

В следующем фрагменте кода показано, как создать и сохранить контакт Outlook.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreateAndSaveOutlookContact-CreateAndSaveOutlookContact.cs" >}}

### **Сохранить список рассылки Mapi в один многоконтактный файл VCF**

В приведенном ниже примере кода показано, как сохранить список рассылки в многоконтактный файл VCF:

```cs
// convert the `msg` object to a `MapiMessage` object
var dlist = (MapiDistributionList)msg.ToMapiMessageItem();

//save the distribution list
var options = new MapiDistributionListSaveOptions(ContactSaveFormat.VCard);
dlist.Save("distribution_list.vcf", options);
```


### **Сохранить контакт в формате VCF версии 3**

Чтобы сохранить контакт в формате VCF версии 3, используйте [VCardVersion](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardversion/) перечислимый для установки [VCardSaveOptions.Version](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/version/) имущество. Следующий пример кода демонстрирует использование [VCardVersion](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardversion/) перечислим для сохранения контактного формата VCF версии 3:

```cs

```

### **Чтение контакта MAPI**

The [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) класс можно использовать для загрузки контактов в формате Outlook MSG и vCard. В следующем фрагменте кода показано, как загрузить контакты Outlook, сохраненные в формате MSG и VCF, в [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/).

#### **Загрузка контакта из MSG**

В следующем фрагменте кода показано, как загружать контакты из MSG.

#### **Загрузка контакта из vCard**

В следующем фрагменте кода показано, как загрузить контакты из vCard.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-LoadingContactFromVCard-LoadingContactFromVCard.cs" >}}

#### **Загрузка контакта из vCard с указанной кодировкой**

В следующем фрагменте кода показано, как загрузить контакты из vCard с указанной кодировкой.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-LoadingContactFromVCardWithSpecifiedEncoding-LoadingContactFromVCardWithSpecifiedEncoding.cs" >}}

#### **Сохранение контактных элементов vCard в указанной кодировке**

Настройте режим сохранения при работе с файлами vCard с помощью [VCardSaveOptions](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/#vcardsaveoptions-class) класс. [PreferredTextEncoding](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/preferredtextencoding/) свойство класса будет указывать кодировку, которая будет использоваться при сохранении контактных элементов vCard.

В следующем примере кода показано, как реализовать это свойство в своем проекте:

```cs
var cont = VCardContact.Load(fileName, Encoding.UTF8);
var opt = new VCardSaveOptions();
opt.PreferredTextEncoding = Encoding.UTF8;
cont.Save("my.vcard", opt);
```

#### **Сохранение файлов vCard с расширенными полями**

The [UseExtensions](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/useextensions/#vcardsaveoptionsuseextensions-property) свойство позволяет вам контролировать, можно ли использовать расширенные поля при сохранении файлов vCard. Если установлено значение true (по умолчанию), расширения разрешены, что обеспечивает совместимость с настраиваемыми полями и дополнительной контактной информацией.

### **Чтение нескольких контактов в формате vCard**

Наша библиотека позволяет получить список всех контактов с vCard. Это можно сделать следующими способами и шагами:

```cs
// Checks whether VCard source stream contains multiple contacts.
VCardContact.IsMultiContacts(Stream stream)

// Loads list of all contacts from VCard file.
VCardContact.LoadAsMultiple(string filePath, Encoding encoding)

// Loads list of all contacts from VCard stream.
VCardContact.LoadAsMultiple(Stream stream, Encoding encoding)
```
В следующем фрагменте кода показано, как работать с файлами vCard, содержащими несколько контактов:

```cs
using (FileStream stream = new FileStream("test.vcf", FileMode.Open, FileAccess.Read))
{
    if(VCardContact.IsMultiContacts(stream))
    {
        List<VCardContact> contacts = VCardContact.LoadAsMultiple(stream, Encoding.UTF8);
    }
}
```

## **Отображение контактной информации в MHTML**

Контакт Outlook можно преобразовать в MHTML с помощью API Aspose.Email. В этом примере показано, как vCard загружается в [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) а затем преобразован в MHTML с помощью [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) API.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-RenderingContactInformationToMhtml-RenderingContactInformationToMhtml.cs" >}}
