---
title: "Instalación de la licencia Aspose.Email para SharePoint"
url: /es/sharepoint/installing-aspose-email-for-sharepoint-license/
weight: 10
type: docs
---


{{% alert color="primary" %}}

Una vez que esté satisfecho con su evaluación, puede [comprar una licencia](http://www.aspose.com/purchase/default.aspx). Antes de comprar, asegúrese de entender y aceptar los términos de la licencia.

La licencia se le enviará por correo electrónico una vez que se haya pagado el pedido. La licencia es un archivo ZIP que contiene un paquete de soluciones de SharePoint normal.

El archivo ZIP contiene:

- **Aspose.Email.SharePoint.License.wsp**: archivo del paquete de soluciones de SharePoint. La licencia Aspose.Email para SharePoint está empaquetada como una solución de SharePoint para facilitar la implementación o la retirada en todo el conjunto de servidores.
- **readme.txt**: Instrucciones de instalación de la licencia. La licencia se instala desde la consola del servidor mediante el archivo stsadm.exe. Los pasos necesarios para instalar la licencia se indican a continuación.

{{% /alert %}}
## **Instalación de la licencia desde la solución WSP**
En las instrucciones siguientes, las rutas se omiten para mayor claridad. Es posible que tenga que añadir la ruta real a stsadm.exe o al archivo de solución al ejecutarlos.

Para instalar la licencia Aspose.Email:

1. Ejecute el Shell de administración de SharePoint 2010.
1. Ejecute stsadm para agregar la solución a la solución de SharePoint:

``` java

 stsadm.exe \-o addsolution \-filename Aspose.Email.SharePoint.License.wsp

```

1. Implemente la solución en todos los servidores de la granja:

``` java

  stsadm.exe \-o deploysolution \-name Aspose.Email.SharePoint.License.wsp \-immediate --force

```

1. Ejecute los trabajos del temporizador administrativo para completar la implementación de inmediato:

``` java

 stsadm.exe \-o execadmsvcjobs

```

Si el servicio de administración de Windows SharePoint Services no se inició al implementar la licencia, se muestra un error. Stsadm.exe se basa en este servicio y en el servicio de temporización de Windows SharePoint para replicar los datos de la solución en toda la granja. Si estos servicios no se ejecutan en su conjunto de servidores, es posible que tenga que implementar la licencia en cada servidor.

![todo:image_alt_text](installing-aspose-email-for-sharepoint-license_1.png)
## **Instalación de la licencia desde un archivo LIC**
Para instalar la licencia desde el archivo Lic, debe colocar el archivo de licencia en la carpeta Aspose.Network.SharePoint.License de la siguiente manera:

`InstalledDrive\Program Files\Common Files\Microsoft Shared\Web Server Extensions\14\Template\Features\Aspose.Network.SharePoint.License`

Aspose.Email for Sharepoint API reconoce los siguientes nombres de licencia:

1. Familia de productos Aspose.Network. LIC
1. Aspose.Email.SharePoint.lic
1. Familia de productos Aspose.Email. LIC
1. Aspose.Total para SharePoint.lic
1. Familia de productos Aspose.Total. LIC
