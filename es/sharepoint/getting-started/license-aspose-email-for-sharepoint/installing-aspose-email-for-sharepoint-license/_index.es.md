---
title: "Instalación de la Licencia de Aspose.Email para SharePoint"
url: /es/sharepoint/installing-aspose-email-for-sharepoint-license/
weight: 10
type: docs
---


{{% alert color="primary" %}} 

Una vez que estés satisfecho con tu evaluación, puedes [comprar una licencia](http://www.aspose.com/purchase/default.aspx). Antes de comprar, asegúrate de entender y aceptar los términos de la licencia.

La licencia te será enviada por correo electrónico una vez que se haya pagado el pedido. La licencia es un archivo ZIP que contiene un paquete de solución de SharePoint regular.

El archivo ZIP contiene:

- **Aspose.Email.SharePoint.License.wsp**: Archivo de paquete de solución de SharePoint. La licencia de Aspose.Email para SharePoint se empaqueta como una solución de SharePoint para facilitar la implementación/retracción a través de la granja de servidores.
- **readme.txt**: Instrucciones de instalación de la licencia. La licencia se instala desde la consola del servidor a través del archivo stsadm.exe. Los pasos necesarios para instalar la licencia se indican a continuación.

{{% /alert %}} 
## **Instalación de la Licencia desde la solución WSP**
En las instrucciones a continuación, se omiten las rutas por claridad. Es posible que debas agregar la ruta real a stsadm.exe y/o al archivo de solución al ejecutarlos.

Para instalar la licencia de Aspose.Email:

1. Ejecuta la Consola de Administración de SharePoint 2010.
1. Ejecuta stsadm para agregar la solución a la solución de SharePoint: 

``` java

 stsadm.exe \-o addsolution \-filename Aspose.Email.SharePoint.License.wsp

```

1. Despliega la solución en todos los servidores de la granja: 

``` java

  stsadm.exe \-o deploysolution \-name Aspose.Email.SharePoint.License.wsp \-immediate --force

```

1. Ejecuta trabajos de temporizador administrativos para completar la implementación de inmediato: 

``` java

 stsadm.exe \-o execadmsvcjobs

```

Si el servicio de administración de Windows SharePoint Services no ha sido iniciado cuando despliegas la licencia, se mostrará un error. Stsadm.exe depende de este servicio y del Servicio de Temporizador de Windows SharePoint para replicar datos de solución a través de la granja. Si estos servicios no están en ejecución en tu granja de servidores, es posible que debas desplegar la licencia en cada servidor. 

![todo:image_alt_text](installing-aspose-email-for-sharepoint-license_1.png)
## **Instalación de la Licencia desde el archivo LIC**
Para instalar la licencia desde el archivo Lic, necesitas colocar el archivo de licencia en la carpeta Aspose.Network.SharePoint.License de la siguiente manera:

`InstalledDrive\Program Files\Common Files\Microsoft Shared\Web Server Extensions\14\Template\Features\Aspose.Network.SharePoint.License`

Los siguientes nombres de licencia son reconocidos por la API de Aspose.Email para SharePoint:

1. Aspose.Network Product Family.lic
1. Aspose.Email.SharePoint.lic
1. Aspose.Email Product Family.lic
1. Aspose.Total for SharePoint.lic
1. Aspose.Total Product Family.lic
