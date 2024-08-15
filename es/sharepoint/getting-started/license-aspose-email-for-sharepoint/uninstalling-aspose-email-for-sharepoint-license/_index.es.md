---
title: "Desinstalar la licencia de Aspose.Email para SharePoint"
url: /es/sharepoint/uninstalling-aspose-email-for-sharepoint-license/
weight: 30
type: docs
---

Para desinstalar la licencia de Aspose.Email for SharePoint, utilice la consola del servidor o el Shell de administración de SharePoint 2010:

1. Retirar la solución de licencias de la granja:

``` java

  stsadm.exe -o retractsolution -name Aspose.Email.SharePoint2010.License.wsp -immediate

```

1. Ejecute tareas de temporizador administrativo para completar la retractación de inmediato:

``` java

 stsadm.exe -o execadmsvcjobs

```

1. Espera a que se complete la retractación. Utilice la Administración Central para comprobar si la retractación se ha completado:
   1. Under **Administración central**, selecciona **Operations** y luego **Administración de soluciones**.
1. Elimine la solución del almacén de soluciones de SharePoint:

``` java

 stsadm.exe -o deletesolution -name Aspose.Email.SharePoint2010.License.wsp

```
