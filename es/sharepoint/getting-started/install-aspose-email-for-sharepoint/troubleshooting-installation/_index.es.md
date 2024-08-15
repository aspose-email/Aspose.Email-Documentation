---
title: "Solución de problemas de instalación"
url: /es/sharepoint/troubleshooting-installation/
weight: 40
type: docs
---


## **Error: algunas o todas las referencias de identidad no se pudieron traducir**
Si ve errores como «No se han podido traducir algunas o todas las referencias de identidad», puede ejecutar el siguiente comando para resolverlos.

**[DOS]**

``` cs



stsadm.exe -o updatefarmcredentials -userlogin <DOMAIN\username> -password <password>



```

{{% alert color="primary" %}}

Si aparece el mensaje de error «Algunas o todas las referencias de identidad», es posible que también deba restablecer los servicios de IIS mediante «iisreset» o reiniciar el sistema operativo.

![todo:image_alt_text](troubleshooting-installation_1.png)

{{% /alert %}}
