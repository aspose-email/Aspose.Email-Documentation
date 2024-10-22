---
title: "Instalación de Aspose.Email para SharePoint"
url: /es/sharepoint/installing-aspose-email-for-sharepoint/
weight: 20
type: docs
---


{{% alert color="primary" %}} 

Aspose.Email para SharePoint se puede descargar como un archivo [Aspose.Email.SharePoint2010.zip](https://downloads.aspose.com/). 

{{% /alert %}} 
## **Instalación**
### **Contenido del Archivo**
El archivo de Aspose.Email para SharePoint contiene carpetas:

1. **Conversión de Correos Electrónicos**: Convertir formatos de archivos de correo electrónico y extracción de adjuntos de archivos EML y MSG en una biblioteca de documentos.
1. **Sincronización de Correos Electrónicos**: Sincronización de correos electrónicos entre la lista personalizada de correos electrónicos de SharePoint y el servidor de correo.
1. **Sincronización de Biblioteca de Documentos**: Sincronización de archivos entre la biblioteca de documentos y el servidor FTP.

Cada carpeta contiene un acuerdo de licencia y archivos de instalación:

1. **archivo wsp**: Archivo de solución de SharePoint. Aspose.Email para SharePoint se empaqueta como una solución de SharePoint para facilitar la implementación/retracción en toda la granja de servidores.
1. **Aspose_LicenseAgreement.rtf**: Acuerdo de licencia de usuario final
1. **Setup.exe**: Programa de instalación
1. **Setup.exe.config**: Archivo de configuración de instalación.

El programa de instalación verifica las siguientes condiciones antes de llevar a cabo la instalación:

1. SharePoint Foundation 2010 está instalado.
1. El usuario tiene permiso para instalar soluciones de SharePoint.
1. El servicio de administración de SharePoint Foundation 2010 está iniciado.
1. El servicio Timer de SharePoint Foundation 2010 está iniciado.

{{% alert color="primary" %}} 

Se necesitan los servicios de administración de WSS y Timer porque algunas acciones de instalación dependen de un trabajo de temporizador para propagarse a todos los servidores en la granja de servidores.

{{% /alert %}} 
### **Instalando Aspose.Email**
Para instalar Aspose.Email para SharePoint:

1. Desempaquete el SIP de Aspose.Email para SharePoint en la unidad local en el servidor SharePoint 2010.
1. Ejecute Setup.exe y siga las instrucciones en pantalla. El programa de instalación realiza las siguientes acciones: 
   1. Verifica los requisitos previos de instalación. La instalación no continuará si alguna verificación falla. 

![todo:image_alt_text](installing-aspose-email-for-sharepoint_1.png)




1. Muestra el acuerdo de licencia de usuario final. El usuario debe aceptar el acuerdo para continuar 

![todo:image_alt_text](installing-aspose-email-for-sharepoint_2.png)




1. Instala y despliega la característica en la granja de servidores 

![todo:image_alt_text](installing-aspose-email-for-sharepoint_3.png)