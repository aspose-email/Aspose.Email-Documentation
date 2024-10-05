---
title: Удаление лицензии Aspose.Email для SharePoint
type: docs
weight: 30
url: /sharepoint/uninstalling-aspose-email-for-sharepoint-license/
---

Чтобы удалить лицензию Aspose.Email для SharePoint, используйте консоль сервера или оболочку управления SharePoint 2010:

1. Отозвать лицензионное решение из фермы: 

``` java

  stsadm.exe -o retractsolution -name Aspose.Email.SharePoint2010.License.wsp -immediate

```

1. Выполните административные задания по таймеру, чтобы немедленно завершить отзыв: 

``` java

 stsadm.exe -o execadmsvcjobs

```

1. Дождитесь завершения отзыва. Используйте Центр администрирования для проверки завершения отзыва: 
   1. В разделе **Центр администрирования** выберите **Операции**, а затем **Управление решениями**.
1. Удалите решение из хранилища решений SharePoint: 

``` java

 stsadm.exe -o deletesolution -name Aspose.Email.SharePoint2010.License.wsp

```