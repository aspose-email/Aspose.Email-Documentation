---
title: "Устранение неполадок при установке"
url: /ru/sharepoint/troubleshooting-installation/
weight: 40
type: docs
---


## **Ошибка: Некоторые или все ссылки на учетные записи не могут быть переведены**
Если вы видите ошибки, такие как «Некоторые или все ссылки на учетные записи не могут быть переведены», вы можете выполнить следующую команду для их устранения.

**[DOS]**

``` cs



stsadm.exe -o updatefarmcredentials -userlogin <DOMAIN\username> -password <password>



```

{{% alert color="primary" %}} 

Если появляется сообщение об ошибке "Некоторые или все ссылки на учетные записи", возможно, вам также нужно будет перезагрузить службы IIS, используя “iisreset”, или перезагрузить операционную систему.

![todo:image_alt_text](troubleshooting-installation_1.png)

{{% /alert %}}