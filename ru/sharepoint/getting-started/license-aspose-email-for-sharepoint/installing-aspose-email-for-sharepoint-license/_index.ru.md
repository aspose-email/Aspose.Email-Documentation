---
title: "Установка лицензии Aspose.Email для SharePoint"
url: /ru/sharepoint/installing-aspose-email-for-sharepoint-license/
weight: 10
type: docs
---


{{% alert color="primary" %}}

Как только вы будете довольны своей оценкой, вы можете [купить лицензию](http://www.aspose.com/purchase/default.aspx). Перед покупкой убедитесь, что вы понимаете и согласны с условиями лицензии.

Лицензия будет отправлена вам по электронной почте после оплаты заказа. Лицензия представляет собой ZIP-архив, содержащий обычный пакет решений SharePoint.

ZIP-архив содержит:

- **Aspose.Email.SharePoint.License.wsp**: файл пакета решений SharePoint. Лицензия Aspose.Email для SharePoint поставляется в виде решения SharePoint, облегчающего развертывание/повторное развертывание в ферме серверов.
- **readme.txt**: Инструкции по установке лицензии. Лицензия устанавливается из консоли сервера через файл stsadm.exe. Шаги, необходимые для установки лицензии, приведены ниже.

{{% /alert %}}
## **Установка лицензии из решения WSP**
В приведенных ниже инструкциях пути пропущены для ясности. Возможно, вам потребуется добавить фактический путь к stsadm.exe и/или файлу решения при их выполнении.

Чтобы установить лицензию Aspose.Email, выполните следующие действия:

1. Запустите командную консоль SharePoint 2010.
1. Запустите stsadm, чтобы добавить решение к решению SharePoint:

``` java

 stsadm.exe \-o addsolution \-filename Aspose.Email.SharePoint.License.wsp

```

1. Разверните решение на всех серверах фермы:

``` java

  stsadm.exe \-o deploysolution \-name Aspose.Email.SharePoint.License.wsp \-immediate --force

```

1. Выполните административные задания таймера, чтобы немедленно завершить развертывание:

``` java

 stsadm.exe \-o execadmsvcjobs

```

Если служба администрирования Windows SharePoint Services не была запущена при развертывании лицензии, отображается сообщение об ошибке. Программа Stsadm.exe использует эту службу и службу Windows SharePoint Timer Service для репликации данных решений по ферме. Если эти службы не запущены в вашей ферме серверов, возможно, потребуется развернуть лицензию на каждом сервере.

![todo:image_alt_text](installing-aspose-email-for-sharepoint-license_1.png)
## **Установка лицензии из файла LIC**
Чтобы установить лицензию из файла Lic, вам необходимо поместить файл лицензии в папку Aspose.Network.Sharepoint.license следующим образом:

`InstalledDrive\Program Files\Common Files\Microsoft Shared\Web Server Extensions\14\Template\Features\Aspose.Network.SharePoint.License`

Следующие названия лицензий распознаются Aspose.Email для Sharepoint API:

1. Семейство сетевых продуктов Aspose.lic
1. Aspose.Email.SharePoint.lic
1. Семейство продуктов Aspose.Email.lic
1. Общая сумма для SharePoint.lic
1. Семейство продуктов Aspose.Total.lic
