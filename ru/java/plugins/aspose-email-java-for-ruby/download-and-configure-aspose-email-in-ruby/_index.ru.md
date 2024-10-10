---
title: "Скачивание и настройка Aspose.Email в Ruby"
url: /ru/java/download-and-configure-aspose-email-in-ruby/
weight: 10
type: docs
---


## **Скачивание необходимых библиотек**
Скачайте необходимые библиотеки, указанные ниже. Эти библиотеки необходимы для выполнения примеров Aspose.Email Java для Ruby.

- [Aspose.Email для Java Компонент](https://downloads.aspose.com/total)
## **Скачивание примеров с социальных кодинг сайтов**
Следующие релизы работающих примеров доступны для скачивания на указанных ниже социальных кодинг сайтах:

**GitHub**

- [Aspose.Email Java для Ruby](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_Java_for_Ruby)
## **Установка**
Установить gem Aspose.Email Java для Ruby очень просто, выполните следующие простые шаги:

1. Запустите следующую команду.

``` java

 $ gem install aspose-emailjava

```

1. Скачайте необходимый компонент Aspose.Email для Java по следующей ссылке.
   <https://downloads.aspose.com/total>
1. Создайте папку "jars" в корне gem Aspose.Email Java для Ruby и скопируйте загруженный компонент в неё.
## **Использование**
Включите необходимые файлы для работы с примером **createnewemail**.

``` java

 require File.dirname(File.dirname(File.dirname(__FILE__))) + '/lib/aspose-emailjava'

include Asposeemailjava

include Asposeemailjava::CreateNewEmail

initialize_aspose_email

```

Давайте разберем код выше.

1. Первая строка гарантирует, что aspose email загружен и доступен.
1. Включите файлы, необходимые для доступа к aspose email.
1. Инициализируйте библиотеки. Классы aspose JAVA загружаются из пути, указанного в файле aspose.yml.