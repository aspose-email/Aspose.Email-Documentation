---
title: "Устранение неполадок установки"
url: /ru/sharepoint/troubleshooting-installation/
weight: 40
type: docs
---


## **Ошибка: некоторые или все идентификационные ссылки не могут быть переведены**
Если вы видите ошибки типа «Не удалось перевести некоторые или все идентификационные ссылки», для их устранения можно выполнить следующую команду.

**[DOS]**

``` cs



stsadm.exe -o updatefarmcredentials -userlogin <DOMAIN\username> -password <password>



```

{{% alert color="primary" %}}

Если появляется сообщение об ошибке «Некоторые или все идентификационные ссылки», возможно, вам также потребуется перезагрузить службы IIS с помощью «iisreset» или перезапустить операционную систему.

![todo:image_alt_text](troubleshooting-installation_1.png)

{{% /alert %}}
