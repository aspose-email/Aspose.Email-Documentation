---
title: "Удаление лицензии Aspose.Email для SharePoint"
url: /ru/sharepoint/uninstalling-aspose-email-for-sharepoint-license/
weight: 30
type: docs
---

Чтобы удалить лицензию Aspose.Email для SharePoint, используйте консоль сервера или командную консоль SharePoint 2010:

1. Извлеките лицензионное решение из фермы:

``` java

  stsadm.exe -o retractsolution -name Aspose.Email.SharePoint2010.License.wsp -immediate

```

1. Выполните административные задания таймера, чтобы немедленно завершить ретракцию:

``` java

 stsadm.exe -o execadmsvcjobs

```

1. Дождитесь завершения ретракции. Используйте Центр администрирования, чтобы проверить, завершено ли опровержение:
   1. Under **Центральное управление**, выберите **Operations** а затем **Управление решениями**.
1. Удалите решение из хранилища решений SharePoint:

``` java

 stsadm.exe -o deletesolution -name Aspose.Email.SharePoint2010.License.wsp

```
