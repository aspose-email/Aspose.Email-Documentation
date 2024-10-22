---
title: Trabajando con las Propiedades de Protección por Contraseña de PST
type: docs
weight: 110
url: /cpp/working-with-pst-password-protection-properties/
---

## **Trabajando con las Propiedades de Protección por Contraseña de PST**

Microsoft Outlook permite a los usuarios proteger con contraseña los archivos PST para restringir el acceso a ellos. Aspose.Email puede detectar la protección por contraseña en un archivo PST. Este artículo muestra cómo:

-   Eliminar/Reiniciar la propiedad de contraseña del PST
-   Configurar/Cambiar la contraseña del PST

### **Eliminando/Reiniciando la Propiedad PR_PST_PASSWORD**

La eliminación de la propiedad PR_PST_PASSWORD no se puede lograr de la misma manera que se eliminan otras propiedades de un almacén de mensajes. En su lugar, debemos establecer su valor en cero (0) para que se elimine. La propiedad "Store" de la clase PST permite acceder a las propiedades de almacenamiento de PST en lugar de las MessageStoreProperties de PST en este caso. El siguiente fragmento de código te muestra cómo eliminar/reiniciar la propiedad PR_PST_PASSWORD.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-EmailCPP-Outlook-RemovingPaswordProperty-RemovingPaswordProperty.cpp" >}}

### **Configurando la Contraseña en Archivos PST**

El siguiente fragmento de código te muestra cómo configurar la contraseña en archivos PST.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-EmailCPP-Outlook-SetPasswordOnPST-SetPasswordOnPST.cpp" >}}

