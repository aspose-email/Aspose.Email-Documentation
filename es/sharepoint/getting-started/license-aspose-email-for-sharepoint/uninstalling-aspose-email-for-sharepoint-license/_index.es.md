---
title: "Desinstalación de la Licencia de Aspose.Email para SharePoint"
url: /es/sharepoint/uninstalling-aspose-email-for-sharepoint-license/
weight: 30
type: docs
---

Para desinstalar la licencia de Aspose.Email para SharePoint, utiliza la consola del servidor o el Shell de Administración de SharePoint 2010:

1. Retracta la solución de licencia de la granja:

``` java

  stsadm.exe -o retractsolution -name Aspose.Email.SharePoint2010.License.wsp -immediate

```

1. Ejecuta trabajos de temporizador administrativos para completar la retractación inmediatamente:

``` java

 stsadm.exe -o execadmsvcjobs

```

1. Espera a que la retractación se complete. Usa la Administración Central para verificar si la retractación completó:
   1. En **Administración Central**, selecciona **Operaciones** y luego **Administración de Soluciones**.
1. Elimina la solución de la tienda de soluciones de SharePoint:

``` java

 stsadm.exe -o deletesolution -name Aspose.Email.SharePoint2010.License.wsp

```