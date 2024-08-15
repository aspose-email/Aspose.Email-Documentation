---
title: "Trabajando con las propiedades de protección con contraseña de PST"
url: /es/cpp/working-with-pst-password-protection-properties/
weight: 110
type: docs
---

## **Trabajando con las propiedades de protección con contraseña de PST**
Microsoft Outlook permite a los usuarios proteger con contraseña los archivos PST para restringir el acceso a ellos. Aspose.Email puede detectar la protección con contraseña en un archivo PST. Este artículo muestra cómo:

- Eliminar/restablecer la propiedad de contraseña del PST
- Configuración/cambio de contraseña PST
### **Eliminar/restablecer la propiedad PR_PST_PASSWORD**
No se puede eliminar la propiedad PR_PST_PASSWORD porque se eliminan otras propiedades de un almacén de mensajes. En su lugar, necesitamos establecer su valor en cero (0) para eliminarla. La propiedad «Store» de la clase PST permite acceder a las propiedades de la tienda de PST en lugar de a MessageStoreProperties de PST en este caso. El siguiente fragmento de código muestra cómo eliminar o restablecer la propiedad PR_PST_PASSWORD.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-EmailCPP-Outlook-RemovingPaswordProperty-RemovingPaswordProperty.cpp" >}}
### **Configuración de la contraseña en los archivos PST**
El siguiente fragmento de código muestra cómo configurar la contraseña en los archivos PST.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-EmailCPP-Outlook-SetPasswordOnPST-SetPasswordOnPST.cpp" >}}
