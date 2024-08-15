---
title: "Работа с контактами Outlook"
url: /ru/java/working-with-outlook-contacts/
weight: 80
type: docs
---

## **Создать контакт Outlook**

Aspose.Email для Java поддерживает создание контактов Outlook (vCards) с помощью [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) class. [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) содержит множество методов, некоторые из которых приведены ниже.

- [MapiContactElectronicAddressPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontactelectronicaddresspropertyset/#MapiContactElectronicAddressPropertySet--) содержит набор [MapiContactElectronicAddress](https://reference.aspose.com/email/java/com.aspose.email/mapicontactelectronicaddress/).
- [MapiContactEventPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontacteventpropertyset/#MapiContactEventPropertySet--)
- [MapiContactNamePropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontactnamepropertyset/#MapiContactNamePropertySet--)
- [MapiContactPersonalInfoPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontactpersonalinfopropertyset/#MapiContactPersonalInfoPropertySet--)
- [MapiContactPhysicalAddressPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontactphysicaladdresspropertyset/#MapiContactPhysicalAddressPropertySet--) содержит набор [MapiContactPhysicalAddress](https://reference.aspose.com/email/java/com.aspose.email/mapicontactphysicaladdress/#MapiContactPhysicalAddress--).
- [MapiContactProfessionalPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontactprofessionalpropertyset/#MapiContactProfessionalPropertySet--)
- [MapiContactTelephonePropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontacttelephonepropertyset/#MapiContactTelephonePropertySet--)
 
### **Структура контактов в Aspose.Email для Java**

Ниже представлена иерархия, реализованная для контактов в Aspose.Email для Java. Каждому свойству указано соответствующее имя класса. Для получения дополнительной информации приведены гиперссылки на онлайн-документацию.

1. [Contact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) (MapiContact)
   1. [Электронные адреса](https://reference.aspose.com/email/java/com.aspose.email/mapicontactelectronicaddresspropertyset/#MapiContactElectronicAddressPropertySet--) (MapiContactElectronicAddressPropertySet)
      1. [Email1](https://reference.aspose.com/email/java/com.aspose.email/mapicontactelectronicaddress/) (MapiContactElectronicAddress)
         1. Тип адреса
         1. Отображаемое имя
         1. Адрес электронной почты
         1. Номер факса
      1. Email2
      1. Email3
      1. Домашний факс
      1. Основной факс
      1. Деловой факс
   1. [Events](https://reference.aspose.com/email/java/com.aspose.email/mapicontacteventpropertyset/#MapiContactEventPropertySet--) (`MapiContactEventPropertySet`). Ниже приведен пример настройки событий.
      1. Birthday
      1. Годовщина свадьбы
   1. [Информация об имени](https://reference.aspose.com/email/java/com.aspose.email/mapicontactnamepropertyset/#MapiContactNamePropertySet--) (`MapiContactNamePropertySet`)
      1. Отображаемое имя
      1. Префикс отображаемого имени
      1. Файл в разделе
      1. Файл под идентификатором
      1. Generation
      1. Заданное имя
      1. Initials
      1. Отчество
      1. Ник
      1. Surname
   1. [Персональная информация](https://reference.aspose.com/email/java/com.aspose.email/mapicontactpersonalinfopropertyset/#MapiContactPersonalInfoPropertySet--) (MapiContactPersonalInfoPropertySet)
      1. Account
      1. Домашняя страница компании
      1. Имя компьютерной сети
      1. Идентификатор клиента
      1. Бесплатное размещение бизнеса
      1. FTP-сайт
      1. Gender
      1. Правительственный идентификационный номер
      1. Hobbies
      1. HTML
      1. Адрес для обмена мгновенными сообщениями
      1. Language
      1. Location
      1. Notes
      1. Идентификационный номер организации
      1. Персональная домашняя страница
      1. Рекомендовано по имени
      1. Имя супруга
   1. [Физический адрес](https://reference.aspose.com/email/java/com.aspose.email/mapicontactphysicaladdresspropertyset/#MapiContactPhysicalAddressPropertySet--) (MapiContactPhysicalAddressPropertySet)
      1. [Домашний адрес](https://reference.aspose.com/email/java/com.aspose.email/mapicontactphysicaladdress/#MapiContactPhysicalAddress--) (MapiContactPhysicalAddress)
         1. Address
         1. City
         1. Country
         1. Код страны
         1. Почтовый индекс
         1. Почтовый ящик
         1. Штат или провинция
      1. Другой адрес
      1. Рабочий адрес
   2. [Профессиональная информация](https://reference.aspose.com/email/java/com.aspose.email/mapicontactprofessionalpropertyset/#MapiContactProfessionalPropertySet--)
      1. Assistant
      2. Название компании
      3. Название отъезда
      4. Имя руководителя
      5. Местонахождение офиса
      6. Profession
      7. Title
   3. [Telephones](https://reference.aspose.com/email/java/com.aspose.email/mapicontacttelephonepropertyset/#MapiContactTelephonePropertySet--) (MapiContactTelephonePropertySet)
      1. Номер телефона помощника
      2. Номер телефона Business2
      3. Рабочий телефонный номер
      4. Номер телефона для обратного вызова
      5. Номер телефона автомобиля
      6. Основной телефонный номер компании
      7. Номер телефона Home2
      8. Домашний телефонный номер
      9. Номер ISDN
      10. Номер мобильного телефона
      11. Другой телефонный номер
      12. Номер телефона пейджера
      13. Основной телефонный номер
      14. Номер радиотелефона
      15. Номер телекса
      16. Номер телефона TTY/TDD

Следующий код использует Aspose.Email для создания контакта Outlook и заполняет его именем, профессиональными свойствами, физическим адресом и адресом электронной почты. Он также показывает добавление [MapiContactEventPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontacteventpropertyset/#MapiContactEventPropertySet--) к контакту.

|![todo:image_alt_text](https://i.imgur.com/D4jXgXo.png)|
|: - |
|**Рис.: Контакт Microsoft Outlook, закодированный с помощью Aspose.Email**|
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateOutlookContact-CreateOutlookContact.java" >}}

### **Добавление информации о контактном событии в MapiContact**

Microsoft Outlook позволяет пользователям добавлять в контакт информацию о событии. Мероприятие приурочено к дню рождения и годовщине свадьбы. Aspose.Email предоставляет [MapiContactEventPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontacteventpropertyset/) класс для добавления этой информации в контакт. Это подробно описано в следующем примере.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateOutlookContact-AddingContactEventInformationToAMapiContact.java" >}}

## **Создание, сохранение и чтение контактов Outlook**

Aspose.Email позволяет разработчикам создавать контакты Microsoft Outlook, а также сообщения электронной почты. [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) класс предоставляет все свойства контакта, необходимые для создания контакта Outlook. В этой статье показано, как создать, сохранить и прочитать контакт Outlook с помощью [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) class.

### **Создание и сохранение контакта MapiContact**

Для создания и сохранения контакта на диске можно использовать следующие шаги:

1. Создайте новый объект из [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) class.
1. Введите информацию, связанную с различными свойствами контакта.
1. Добавьте данные фотографии к контакту, если таковые имеются.
1. Сохраните контакт в формате MSG или vCard.
 

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateSaveAndReadOutlookContact-CreatingAndSavingAMapiContact.java" >}}

### **Сохранить контакт в формате VCF версии 3**

Чтобы сохранить контакт в формате VCF версии 3, используйте [VCardVersion](https://reference.aspose.com/email/java/com.aspose.email/vcardversion/) перечислимый для установки [VCardSaveOptions.Version](https://reference.aspose.com/email/java/com.aspose.email/vcardsaveoptions/#getVersion--) имущество. Следующий пример кода демонстрирует использование [VCardVersion](https://reference.aspose.com/email/java/com.aspose.email/vcardversion/) перечислим для сохранения контактного формата VCF версии 3.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateV30Contact-1.java" >}}

### **Прочтите контакт MAPIcontact**

The [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) класс можно использовать для загрузки как файлов Microsoft Outlook MSG, так и контактов формата vCard. В следующих примерах кода показано, как загрузить контакты Outlook, сохраненные в форматах MSG и VCF, в [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/).

#### **Загрузить контакт из MSG**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateSaveAndReadOutlookContact-LoadingAContactFromMSG.java" >}}

#### **Загрузите контакт из vCard**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateSaveAndReadOutlookContact-LoadingAContactFromVCard.java" >}}

#### **Загрузить контакт vCard с указанной кодировкой**

Поддерживаемый метод: [Mapicontact.from vCard (строка, кодировка)](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/#fromVCard-java.lang.String-java.nio.charset.Charset-)

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateSaveAndReadOutlookContact-LoadingVCardContactWithSpecifiedEncoding.java" >}}

## **Отображение контактной информации в MHTML**

Контакт Outlook можно преобразовать в MHTML с помощью API Aspose.Email. В этом примере показано, как vCard загружается в [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) а затем преобразован в MHTML с помощью [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) API.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-RenderingContactInformationToMhtml-RenderingContactInformationToMhtml.java" >}}
