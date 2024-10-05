---
title: "Установка лицензии Aspose.Email для SharePoint"
url: /ru/sharepoint/installing-aspose-email-for-sharepoint-license/
weight: 10
type: docs
---


{{% alert color="primary" %}} 

Как только вы будете довольны своей оценкой, вы можете [купить лицензию](http://www.aspose.com/purchase/default.aspx). Перед покупкой убедитесь, что вы понимаете и соглашаетесь с условиями лицензии.

Лицензия будет отправлена вам по электронной почте после оплаты заказа. Лицензия является ZIP-архивом, который содержит стандартный пакет решения SharePoint.

ZIP-архив содержит:

- **Aspose.Email.SharePoint.License.wsp**: файл пакета решения SharePoint. Лицензия Aspose.Email для SharePoint упакована как решение SharePoint для облегчения развертывания/отзыва по всему серверному фарму.
- **readme.txt**: инструкции по установке лицензии. Лицензия устанавливается из консоли сервера через файл stsadm.exe. Шаги, необходимые для установки лицензии, приведены ниже.

{{% /alert %}} 
## **Установка лицензии из WSP решения**
В инструкции ниже пути опущены для ясности. Возможно, вам потребуется добавить фактический путь к stsadm.exe и/или файлу решения при их выполнении.

Чтобы установить лицензию Aspose.Email:

1. Запустите оболочку управления SharePoint 2010.
1. Запустите stsadm для добавления решения в решение SharePoint: 

``` java

 stsadm.exe \-o addsolution \-filename Aspose.Email.SharePoint.License.wsp

```

1. Разверните решение на всех серверах в фарме: 

``` java

  stsadm.exe \-o deploysolution \-name Aspose.Email.SharePoint.License.wsp \-immediate --force

```

1. Выполните административные таймерные задания, чтобы завершить развертывание немедленно: 

``` java

 stsadm.exe \-o execadmsvcjobs

```

Если служба администрирования Windows SharePoint Services не была запущена, когда вы развертываете лицензию, возникает ошибка. Stsadm.exe зависит от этой службы и службы таймера Windows SharePoint для репликации данных решения по всему ферме. Если эти службы не работают на вашем серверном фарме, вам может потребоваться развернуть лицензию на каждом сервере. 

![todo:image_alt_text](installing-aspose-email-for-sharepoint-license_1.png)
## **Установка лицензии из файла LIC**
Чтобы установить лицензию из файла Lic, вам нужно поместить файл лицензии в папку Aspose.Network.SharePoint.License следующим образом:

`InstalledDrive\Program Files\Common Files\Microsoft Shared\Web Server Extensions\14\Template\Features\Aspose.Network.SharePoint.License`

Следующие имена лицензий распознаются API Aspose.Email для SharePoint:

1. Aspose.Network Product Family.lic
1. Aspose.Email.SharePoint.lic
1. Aspose.Email Product Family.lic
1. Aspose.Total для SharePoint.lic
1. Aspose.Total Product Family.lic
