---
title: "Работа с контактами Outlook"
url: /ru/net/working-with-outlook-contacts/
weight: 90
type: docs
---


## **Создание, сохранение и чтение контактов**

Как и MapiMessage, Aspose.Email позволяет создавать контакты Outlook. Класс [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) предоставляет все необходимые свойства, связанные с контактами, для создания контакта Outlook. В данной статье показано, как создать, сохранить и прочитать контакт Outlook с помощью класса [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/).

### **Создание и сохранение контакта Outlook**

Чтобы создать контакт и сохранить его на диск:

1. Создайте новый объект класса [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/).
1. Введите информацию о свойствах контакта.
1. Добавьте данные о фотографии (если есть).
1. Сохраните контакт в формате MSG или VCard.

Следующий код показывает, как создать и сохранить контакт Outlook.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreateAndSaveOutlookContact-CreateAndSaveOutlookContact.cs" >}}

### **Сохранение списка рассылки Mapi в один мульти-контактный файл VCF**

Пример кода ниже демонстрирует, как сохранить список рассылки в мульти-контактный файл VCF:

```cs
// конвертировать объект `msg` в объект `MapiMessage`
var dlist = (MapiDistributionList)msg.ToMapiMessageItem();

// сохранить список рассылки
var options = new MapiDistributionListSaveOptions(ContactSaveFormat.VCard);
dlist.Save("distribution_list.vcf", options);
```


### **Сохранение контакта в формате VCF версии 3**

Чтобы сохранить контакт в формате VCF версии 3, используйте перечисление [VCardVersion](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardversion/), чтобы установить [VCardSaveOptions.Version](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/version/) свойство. Следующий пример кода демонстрирует использование [VCardVersion](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardversion/) перечисления для сохранения контакта в формате VCF версии 3:

```cs

```

### **Чтение MapiContact**

Класс [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) может использоваться для загрузки контактов как в формате MSG, так и в формате VCard. Следующий код показывает, как загрузить контакты Outlook, сохраненные как MSG и VCF, в [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/).

#### **Загрузка контакта из MSG**

Следующий код показывает, как загрузить контакты из MSG.

#### **Загрузка контакта из VCard**

Следующий код показывает, как загрузить контакты из VCard.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-LoadingContactFromVCard-LoadingContactFromVCard.cs" >}}

#### **Загрузка контакта из VCard с заданной кодировкой**

Следующий код показывает, как загрузить контакты из VCard с заданной кодировкой.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-LoadingContactFromVCardWithSpecifiedEncoding-LoadingContactFromVCardWithSpecifiedEncoding.cs" >}}

#### **Сохранение элементов VCard контактов с заданной кодировкой**

Настройте поведение сохранения при работе с VCard файлами, используя класс [VCardSaveOptions](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/#vcardsaveoptions-class). Свойство [PreferredTextEncoding](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/preferredtextencoding/) класса определяет кодировку, которая будет использоваться при сохранении элементов VCard контактов.

Следующий пример кода показывает, как реализовать это свойство в вашем проекте:

```cs
var cont = VCardContact.Load(fileName, Encoding.UTF8);
var opt = new VCardSaveOptions();
opt.PreferredTextEncoding = Encoding.UTF8;
cont.Save("my.vcard", opt);
```

#### **Сохранение VCard файлов с расширенными полями**

Свойство [UseExtensions](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/useextensions/#vcardsaveoptionsuseextensions-property) позволяет управлять тем, могут ли быть использованы расширенные поля при сохранении файлов vCard. При установке в значение true (по умолчанию) расширения разрешены, что обеспечивает совместимость с пользовательскими полями и дополнительной информацией о контактах.

### **Чтение нескольких контактов в формате VCard**

Наша библиотека позволяет получить список всех контактов из VCard. Это можно сделать с помощью следующих методов и шагов:

```cs
// Проверяет, содержит ли источник потока VCard несколько контактов.
VCardContact.IsMultiContacts(Stream stream)

// Загружает список всех контактов из файла VCard.
VCardContact.LoadAsMultiple(string filePath, Encoding encoding)

// Загружает список всех контактов из потока VCard.
VCardContact.LoadAsMultiple(Stream stream, Encoding encoding)
```
Следующий код демонстрирует, как обрабатывать VCard файлы, содержащие несколько контактов:

```cs
using (FileStream stream = new FileStream("test.vcf", FileMode.Open, FileAccess.Read))
{
    if(VCardContact.IsMultiContacts(stream))
    {
        List<VCardContact> contacts = VCardContact.LoadAsMultiple(stream, Encoding.UTF8);
    }
}
```

## **Отображение информации о контакте в MHTML**

Контакт Outlook может быть преобразован в MHTML с помощью API Aspose.Email. Этот пример показывает, как VCard загружается в [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) и затем преобразуется в MHTML с помощью API [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-RenderingContactInformationToMhtml-RenderingContactInformationToMhtml.cs" >}}