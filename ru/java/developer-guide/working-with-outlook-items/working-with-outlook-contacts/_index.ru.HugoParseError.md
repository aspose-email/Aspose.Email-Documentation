---
title: Работа с контактами Outlook
type: docs
weight: 80
url: /java/working-with-outlook-contacts/
---

## **Создание контакта Outlook**

Aspose.Email для Java поддерживает создание контактов Outlook (VCards) с использованием класса [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/). [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) содержит множество методов, некоторые из которых приведены ниже.

- [MapiContactElectronicAddressPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontactelectronicaddresspropertyset/#MapiContactElectronicAddressPropertySet--) содержит набор [MapiContactElectronicAddress](https://reference.aspose.com/email/java/com.aspose.email/mapicontactelectronicaddress/).
- [MapiContactEventPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontacteventpropertyset/#MapiContactEventPropertySet--)
- [MapiContactNamePropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontactnamepropertyset/#MapiContactNamePropertySet--)
- [MapiContactPersonalInfoPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontactpersonalinfopropertyset/#MapiContactPersonalInfoPropertySet--)
- [MapiContactPhysicalAddressPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontactphysicaladdresspropertyset/#MapiContactPhysicalAddressPropertySet--) содержит набор [MapiContactPhysicalAddress](https://reference.aspose.com/email/java/com.aspose.email/mapicontactphysicaladdress/#MapiContactPhysicalAddress--).
- [MapiContactProfessionalPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontactprofessionalpropertyset/#MapiContactProfessionalPropertySet--)
- [MapiContactTelephonePropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontacttelephonepropertyset/#MapiContactTelephonePropertySet--)

### **Структура контакта в Aspose.Email для Java**

Ниже представлена иерархия, реализованная для контактов в Aspose.Email для Java. Соответствующее имя класса указано напротив каждого свойства. Гиперссылки предоставлены для онлайн-документации для дальнейшего изучения.

1. [Contact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) (MapiContact)
   1. [Электронные адреса](https://reference.aspose.com/email/java/com.aspose.email/mapicontactelectronicaddresspropertyset/#MapiContactElectronicAddressPropertySet--) (MapiContactElectronicAddressPropertySet)
      1. [Email1](https://reference.aspose.com/email/java/com.aspose.email/mapicontactelectronicaddress/) (MapiContactElectronicAddress)
         1. Тип адреса
         1. Имя для отображения
         1. Электронный адрес
         1. Номер факса
      1. Email2
      1. Email3
      1. Домашний факс
      1. Основной факс
      1. Факс для бизнеса
   1. [События](https://reference.aspose.com/email/java/com.aspose.email/mapicontacteventpropertyset/#MapiContactEventPropertySet--) (`MapiContactEventPropertySet`). Ниже приведен пример того, как установить события.
      1. День рождения
      1. Юбилей свадьбы
   1. [Информация о имени](https://reference.aspose.com/email/java/com.aspose.email/mapicontactnamepropertyset/#MapiContactNamePropertySet--) (`MapiContactNamePropertySet`)
      1. Имя для отображения
      1. Префикс имени для отображения
      1. Файл под
      1. ID файла
      1. Поколение
      1. Имя
      1. Инициал(ы)
      1. Отчество
      1. Псевдоним
      1. Фамилия
   1. [Личная информация](https://reference.aspose.com/email/java/com.aspose.email/mapicontactpersonalinfopropertyset/#MapiContactPersonalInfoPropertySet--) (MapiContactPersonalInfoPropertySet)
      1. Учетная запись
      1. Веб-страница бизнеса
      1. Имя компьютерной сети
      1. ID клиента
      1. Свободное местоположение бизнеса
      1. FTP сайт
      1. Пол
      1. Номер удостоверения личности
      1. Хобби
      1. HTML
      1. Адрес мгновенных сообщений
      1. Язык
      1. Местоположение
      1. Заметки
      1. Номер организационного удостоверения
      1. Личная веб-страница
      1. Рекомендованное имя
      1. Имя супруга
   1. [Физический адрес](https://reference.aspose.com/email/java/com.aspose.email/mapicontactphysicaladdresspropertyset/#MapiContactPhysicalAddressPropertySet--) (MapiContactPhysicalAddressPropertySet)
      1. [Домашний адрес](https://reference.aspose.com/email/java/com.aspose.email/mapicontactphysicaladdress/#MapiContactPhysicalAddress--) (MapiContactPhysicalAddress)
         1. Адрес
         1. Город
         1. Страна
         1. Код страны
         1. Почтовый индекс
         1. Почтовый ящик
         1. Штат или провинция
      1. Другой адрес
      1. Рабочий адрес
   2. [Профессиональная информация](https://reference.aspose.com/email/java/com.aspose.email/mapicontactprofessionalpropertyset/#MapiContactProfessionalPropertySet--)
      1. Ассистент
      2. Название компании
      3. Название отдела
      4. Имя менеджера
      5. Местоположение офиса
      6. Профессия
      7. Должность
   3. [Телефоны](https://reference.aspose.com/email/java/com.aspose.email/mapicontacttelephonepropertyset/#MapiContactTelephonePropertySet--) (MapiContactTelephonePropertySet)
      1. Номер телефона ассистента
      2. Номер телефона для бизнеса2
      3. Номер телефона для бизнеса
      4. Номер телефона для обратного вызова
      5. Номер телефона автомобиля
      6. Основной номер телефона компании
      7. Номер телефона для дома2
      8. Номер телефона для дома
      9. Номер ISDN
      10. Номер мобильного телефона
      11. Другой номер телефона
      12. Номер пейджера
      13. Основной номер телефона
      14. Номер радиотелефона
      15. Номер телекса
      16. Номер телефона TTY/TDD

Следующий код использует Aspose.Email для создания контакта Outlook и заполняет его именем, профессиональными свойствами, физическим адресом и электронной почтой. Также показано как добавить [MapiContactEventPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontacteventpropertyset/#MapiContactEventPropertySet--) к контакту.

|![todo:image_alt_text](https://i.imgur.com/D4jXgXo.png)|
| :- |
|**Рисунок: Контакт Microsoft Outlook, закодированный с помощью Aspose.Email**|
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateOutlookContact-CreateOutlookContact.java" >}}

### **Добавление информации о событиях контакта в MapiContact**

Microsoft Outlook позволяет пользователям добавлять информацию о событиях к контакту. Событие содержит день рождения и юбилей свадьбы. Aspose.Email предоставляет класс [MapiContactEventPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontacteventpropertyset/) для добавления этой информации к контакту. Это подробно описано в следующем примере.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateOutlookContact-AddingContactEventInformationToAMapiContact.java" >}}

## **Создание, сохранение и чтение контактов Outlook**

Aspose.Email позволяет разработчикам создавать контакты Microsoft Outlook, а также электронные сообщения. Класс [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) предоставляет все свойства контакта, необходимые для создания контакта Outlook. В этой статье показано, как создать, сохранить и прочитать контакт Outlook с помощью класса [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/).

### **Создайте и сохраните MapiContact**

Следующие шаги можно использовать для создания и сохранения контакта на диске:

1. Создайте новый объект класса [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/).
1. Введите информацию, связанную с различными свойствами контакта.
1. Добавьте фотоданные к контакту, если есть.
1. Сохраните контакт в формате MSG или VCard.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateSaveAndReadOutlookContact-CreatingAndSavingAMapiContact.java" >}}

### **Сохранение контакта в формате VCF версии 3**

Чтобы сохранить контакт в формате VCF версии 3, используйте перечисление [VCardVersion](https://reference.aspose.com/email/java/com.aspose.email/vcardversion/) для установки свойства [VCardSaveOptions.Version](https://reference.aspose.com/email/java/com.aspose.email/vcardsaveoptions/#getVersion--). Следующий пример кода демонстрирует использование перечисления [VCardVersion](https://reference.aspose.com/email/java/com.aspose.email/vcardversion/) для сохранения контакта в формате VCF версии 3.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateV30Contact-1.java" >}}

### **Чтение MapiContact**

Класс [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) может использоваться для загрузки как файлов MSG Microsoft Outlook, так и контактов формата VCard. Следующие примеры кода показывают, как загрузить контакты Outlook, сохраненные в формате MSG и VCF, в [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/).

#### **Загрузка контакта из MSG**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateSaveAndReadOutlookContact-LoadingAContactFromMSG.java" >}}

#### **Загрузка контакта из VCard**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateSaveAndReadOutlookContact-LoadingAContactFromVCard.java" >}}

#### **Загрузка VCard контакта с заданной кодировкой**

Поддерживаемый метод: [MapiContact.fromVCard(String, Encoding)](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/#fromVCard-java.lang.String-java.nio.charset.Charset-)

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateSaveAndReadOutlookContact-LoadingVCardContactWithSpecifiedEncoding.java" >}}

## **Отображение информации о контакте в MHTML**

Контакт Outlook можно преобразовать в MHTML с помощью API Aspose.Email. Этот пример показывает, как VCard загружается в [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) и затем преобразуется в MHTML с помощью API [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-RenderingContactInformationToMhtml-RenderingContactInformationToMhtml.java" >}}