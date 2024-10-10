---
title: "Aspose.Email Java для Ruby"
url: /ru/java/aspose-email-java-for-ruby/
weight: 20
type: docs
---

## **Введение**
### **Rjb - Ruby Java Bridge**
RJB - это программа-мост, которая связывает Ruby и Java с помощью Java Native Interface. Rake + Rjb - это более мощный и полезный инструмент сборки, чем как Maven, так и Ant. Вы можете протестировать свой класс бизнес-логики Java с помощью мока Rjb. Это помогает перенести объект модели Struts в ваше приложение RoR. Но будьте осторожны с созданием Swing-приложений, Ruby (и Rjb) не учитывают обработку нативных потоков JVM.
### **Aspose.Email для Java**
Aspose.Email для Java - это библиотека классов Java, которая позволяет Java-приложениям читать и записывать файлы email-сообщений в различных форматах без Microsoft Outlook. Она предоставляет классы для чтения и обновления файлов MSG, EML, EMLX, OFT, добавления/удаления вложений и получателей, обновления темы, тела и других свойств файлов MSG.
### **Aspose.Email Java для Ruby**
Проект Aspose.Email Java для Ruby показывает, как различные задачи могут быть выполнены с использованием API Aspose.Email Java в Ruby. Этот проект нацелен на предоставление полезных примеров для разработчиков Ruby, которые хотят использовать Aspose.Email для Java в своих Ruby проектах с использованием Rjb (Ruby Java Bridge).
## **Системные требования и поддерживаемые платформы**
### **Системные требования**
**Следующие системные требования необходимы для использования Aspose.Email Java для Ruby:**

- Настроен гем Rjb
- Скачанный компонент Aspose.Email
### **Поддерживаемые платформы**
**Следующие платформы поддерживаются:**

- Ruby 2.2.x или выше и соответствующий DevKit.
- Java 1.5 или выше
## **Скачивания**
### **Скачать необходимые библиотеки**
Скачайте необходимые библиотеки, указанные ниже. Они необходимы для выполнения примеров Aspose.Email Java для Ruby.

- [Компонент Aspose.Email для Java](https://downloads.aspose.com/total)
### **Скачать примеры с сайтов социального кодирования**
Следующие выпуски работающих примеров доступны для скачивания на нижеупомянутых сайтах социального кодирования:

**GitHub**

- [Aspose.Email Java для Ruby](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_Java_for_Ruby)
## **Установка и использование**
### **Установка**
Установить гем Aspose.Email Java для Ruby очень просто, пожалуйста, следуйте этим простым шагам:

1. Выполните следующую команду. 

``` java

 $ gem install aspose-emailjava

```

1. Скачайте необходимый компонент Aspose.Email для Java по следующей ссылке.
   <https://downloads.aspose.com/total>
1. Создайте папку "jars" в корне гема Aspose.Email Java для Ruby и скопируйте в нее скачанный компонент.
### **Использование**
Включите необходимые файлы для работы с примером **createnewemail**.

``` java

 require File.dirname(File.dirname(File.dirname(__FILE__))) + '/lib/aspose-emailjava'

include Asposeemailjava

include Asposeemailjava::CreateNewEmail

initialize_aspose_email

```

Давайте разберем приведенный выше код.

1. Первая строка гарантирует, что aspose email загружен и доступен.
1. Включите файлы, необходимые для доступа к aspose email.
1. Инициализируйте библиотеки. Классы aspose JAVA загружаются из пути, указанного в файле aspose.yml
## **Поддержка, расширение и вклад**
### **Поддержка**
С первых дней существования Aspose мы знали, что просто предоставлять нашим клиентам хорошие продукты будет недостаточно. Нам также нужно было предоставить хорошее обслуживание. Мы сами разработчики и понимаем, как это раздражает, когда техническая проблема или ошибка в программном обеспечении мешает вам делать то, что вам нужно. Мы здесь, чтобы решать проблемы, а не создавать их.

Вот почему мы предлагаем бесплатную поддержку. Каждый, кто использует наш продукт, независимо от того, купил ли он его или использует оценочную версию, заслуживает нашего полного внимания и уважения.

Вы можете сообщить о любых проблемах или предложениях, связанных с Aspose.Email Java для Ruby, используя любую из следующих платформ:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/issues)
### **Расширение и вклад**
Aspose.Email Java для Ruby является открытым исходным кодом, и его исходный код доступен на основных сайтах социального кодирования, перечисленных ниже. Разработчики поощряются скачивать исходный код и вносить свой вклад, предлагая или добавляя новые функции или улучшая существующие, чтобы другие также могли извлечь из этого пользу.
### **Исходный код**
Вы можете получить последний исходный код из одного из следующих мест:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_Java_for_Ruby)
## **Примеры кода**
**Этот раздел включает в себя следующие темы:**

- [Скачать и настроить Aspose.Email в Ruby](/email/java/download-and-configure-aspose-email-in-ruby/)
- [Руководство для программистов Ruby](/email/java/ruby-programmers-guide/)
  - [Программирование электронной почты в Ruby](/email/java/programming-email-in-ruby/)
    - [Преобразование email-сообщений в Ruby](/email/java/converting-email-messages-in-ruby/)
    - [Создание нового email в Ruby](/email/java/create-new-email-in-ruby/)
    - [Настройка заголовков email в Ruby](/email/java/customizing-email-headers-in-ruby/)
    - [Отображение информации о email на экране в Ruby](/email/java/displaying-email-information-on-screen-in-ruby/)
    - [Извлечение заголовков email в Ruby](/email/java/extracting-email-headers-in-ruby/)
    - [Управление вложениями в email-сообщении в Ruby](/email/java/manage-attachments-in-email-message-in-ruby/)
    - [Сохранение сообщения как черновика в Ruby](/email/java/save-message-as-draft-in-ruby/)
    - [Обновление и сохранение email в Ruby](/email/java/update-and-save-an-email-in-ruby/)
  - [Программирование Outlook в Ruby](/email/java/programming-outlook-in-ruby/)
    - [Работа с файлами сообщений Outlook (MSG) в Ruby](/email/java/working-with-outlook-message-msg-files-in-ruby/)
      - [Создание и сохранение контактов Outlook в Ruby](/email/java/creating-and-saving-outlook-contacts-in-ruby/)
      - [Создание и сохранение заметок Outlook в Ruby](/email/java/creating-and-saving-outlook-notes-in-ruby/)
      - [Создание и сохранение задач Outlook в Ruby](/email/java/creating-and-saving-outlook-tasks-in-ruby/)
      - [Парсинг файлов сообщений Outlook в Ruby](/email/java/parsing-outlook-message-files-in-ruby/)
      - [Работа с рассылками в Ruby](/email/java/working-with-distribution-lists-in-ruby/)
    - [Работа с файлами личного хранения Outlook (PST) в Ruby](/email/java/working-with-outlook-personal-storage-pst-files-in-ruby/)
      - [Добавление файлов в PST в Ruby](/email/java/adding-files-to-pst-in-ruby/)
      - [Добавление MapiCalendar в PST в Ruby](/email/java/adding-mapicalendar-to-pst-in-ruby/)
      - [Добавление MapiContact в PST в Ruby](/email/java/adding-mapicontact-to-pst-in-ruby/)
      - [Добавление MapiJournal в PST в Ruby](/email/java/adding-mapijournal-to-pst-in-ruby/)
      - [Добавление MapiNote в PST в Ruby](/email/java/adding-mapinote-to-pst-in-ruby/)
      - [Добавление MapiTask в PST в Ruby](/email/java/adding-mapitask-to-pst-in-ruby/)
      - [Создание нового PST в Ruby](/email/java/create-new-pst-in-ruby/)
      - [Поиск сообщений и папок в PST по некоторым критериям в Ruby](/email/java/search-messages-and-folders-in-a-pst-by-some-criteria-in-ruby/)
      - [Поиск строк в PST с игнорированием регистра в Ruby](/email/java/string-searching-in-pst-with-ignore-case-in-ruby/)
- [Поддержка, расширение и вклад в Aspose.Email в Ruby](/email/java/support-extend-and-contribute-to-aspose-email-in-ruby/)