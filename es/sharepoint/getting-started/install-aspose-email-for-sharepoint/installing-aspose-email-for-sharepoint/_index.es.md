---
title: "Instalación de Aspose.Email para SharePoint"
url: /es/sharepoint/installing-aspose-email-for-sharepoint/
weight: 20
type: docs
---


{{% alert color="primary" %}}

Aspose.Email para SharePoint se puede descargar como [Aspose.Email.SharePoint2010.zip](https://downloads.aspose.com/) archive.

{{% /alert %}}
## **Installation**
### **Archivar contenido**
El archivo Aspose.Email for SharePoint contiene carpetas:

1. **Conversión de correo electrónico**: Convierta formatos de archivos de correo electrónico y extraiga archivos adjuntos de archivos EML y MSG en una biblioteca de documentos.
1. **Sincronización de correo**: Sincronización del correo electrónico entre la lista personalizada de correos electrónicos de SharePoint y el servidor de correo.
1. **Sincronización de bibliotecas de documentos**: Sincronización de archivos entre la biblioteca de documentos y el servidor FTP.

Cada carpeta contiene el acuerdo de licencia y los archivos de instalación:

1. **archivo wsp**: archivo de solución de SharePoint. Aspose.Email para SharePoint se presenta como una solución de SharePoint para facilitar la implementación o la retirada en todo el conjunto de servidores.
1. **Aspose_LicenseAgreement.rtf**: Acuerdo de licencia de usuario final
1. **Setup.exe**: Programa de configuración
1. **Setup.exe.config**: Archivo de configuración de configuración.

El programa de instalación comprueba las siguientes condiciones antes de llevar a cabo la instalación:

1. SharePoint Foundation 2010 está instalado.
1. El usuario tiene permiso para instalar soluciones de SharePoint.
1. Se inicia el servicio de administración de SharePoint Foundation 2010.
1. Se inicia el servicio de temporizador de SharePoint Foundation 2010.

{{% alert color="primary" %}}

El servicio de administración de WSS y el servicio de temporizador son necesarios porque algunas acciones de configuración dependen de un trabajo de temporizador para propagarse a todos los servidores del conjunto de servidores.

{{% /alert %}}
### **Instalación de Aspose.Email**
Para instalar Aspose.Email para SharePoint:

1. Descomprima el SIP de Aspose.Email para SharePoint en la unidad local del servidor SharePoint 2010.
1. Ejecute Setup.exe y siga las instrucciones de la pantalla. El programa de instalación realiza las siguientes acciones:
   1. Comprueba los requisitos previos de instalación. La instalación no continuará si se produce un error en alguna de las comprobaciones.

![todo:image_alt_text](installing-aspose-email-for-sharepoint_1.png)




1. Muestra el contrato de licencia de usuario final. El usuario debe aceptar el acuerdo para continuar

![todo:image_alt_text](installing-aspose-email-for-sharepoint_2.png)




1. Instala e implementa la función en la granja de servidores

![todo:image_alt_text](installing-aspose-email-for-sharepoint_3.png)
