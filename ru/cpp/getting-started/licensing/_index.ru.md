---
title: "Licensing"
description: "Оцените API библиотеки Email C++ и примените лицензию, используя файл или потоковый объект."
url: /ru/cpp/licensing/
weight: 60
type: docs
---

## **Ограничения пробной версии**
Бесплатную ознакомительную версию Aspose.Email для C++ можно загрузить в разделе загрузок на веб-сайте Aspose по адресу: https://releases.aspose.com/email/cpp/

## **Применить лицензию с помощью объекта File или Stream**
Лицензию можно загрузить из файла или потокового объекта. Aspose.Eamil для C++ попытается найти лицензию в следующих местах:

1. Явный путь.
1. Папка, содержащая Aspose.Cells.dll.
1. Папка, содержащая сборку под названием Aspose.Cells.dll.
1. Папка, содержащая сборку записей (ваш EXE-файл).
1. Встроенный в сборку ресурс под названием Aspose.Cells.dll.

Самый простой способ установить лицензию — поместить файл лицензии в ту же папку, что и файл Aspose.Email.dll, и указать имя файла без пути, как показано в примере ниже.
### **Загрузка лицензии из файла**
Самый простой способ применить лицензию — поместить файл лицензии в ту же папку, что и файл Aspose.Email.dll, и указать только имя файла без пути.

{{% alert color="primary" %}}

При вызове метода setLicense передаваемое имя лицензии должно совпадать с именем файла лицензии. Например, если вы измените имя файла лицензии на «aSpose.email.lic», передайте это имя методу emails->setLicense (...).

{{% /alert %}}

**C++**

``` cs

 intrusive_ptr<License> license = new License();

license->SetLicense(new String("Aspose.Email.lic"));

```
### **Загрузка лицензии из объекта Stream**
В следующем примере показано, как загрузить лицензию из потока.

**C++**

``` cs

 intrusive_ptr<License>license = new License();

intrusive_ptr<FileStream> myStream = new FileStream(new String("Aspose.Email.lic"), FileMode_Open);

license->SetLicense(myStream);

```
