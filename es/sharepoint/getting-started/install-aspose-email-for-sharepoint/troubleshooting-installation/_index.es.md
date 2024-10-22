---
title: "Solución de problemas de instalación"
url: /es/sharepoint/troubleshooting-installation/
weight: 40
type: docs
---


## **Error: Algunos o todos los referencias de identidad no se pudieron traducir**
Si ves errores como “Algunos o todos los referencias de identidad no se pudieron traducir”, puedes ejecutar el siguiente comando para resolverlos.

**[DOS]**

``` cs



stsadm.exe -o updatefarmcredentials -userlogin <DOMINIO\usuario> -password <contraseña>



```

{{% alert color="primary" %}} 

Si aparece el mensaje de error "Algunos o todos los referencias de identidad", también es posible que necesites reiniciar los servicios de IIS usando “iisreset” o reiniciar el sistema operativo. 

![todo:image_alt_text](troubleshooting-installation_1.png)

{{% /alert %}}