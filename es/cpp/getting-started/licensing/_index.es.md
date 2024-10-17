---
title: "Licenciamiento"
description: "Evalúe la API de la biblioteca Aspose.Email para C++ y aplique la licencia usando un archivo o un objeto de flujo."
url: /es/cpp/licensing/
weight: 60
type: docs
---

## **Limitaciones de la Versión de Evaluación**
Una versión gratuita de evaluación de Aspose.Email para C++ se puede descargar desde la sección de descargas del sitio web de Aspose en: https://releases.aspose.com/email/cpp/

## **Aplicar Licencia usando Archivo u Objeto de Flujo**
La licencia se puede cargar desde un archivo o un objeto de flujo. Aspose.Email para C++ intentará encontrar la licencia en las siguientes ubicaciones:

1. Ruta explícita.
1. La carpeta que contiene Aspose.Cells.dll.
1. La carpeta que contiene el ensamblado que llamó a Aspose.Cells.dll.
1. La carpeta que contiene el ensamblado de entrada (su .exe).
1. Un recurso incrustado en el ensamblado que llamó a Aspose.Cells.dll.

La forma más fácil de establecer una licencia es colocar el archivo de licencia en la misma carpeta que el archivo Aspose.Email.dll y especificar el nombre del archivo, sin una ruta, como se muestra en el ejemplo a continuación.
### **Cargar una Licencia desde un Archivo**
La forma más sencilla de aplicar una licencia es colocar el archivo de licencia en la misma carpeta que el archivo Aspose.Email.dll y especificar solo el nombre del archivo sin una ruta.

{{% alert color="primary" %}} 

Cuando llame al método SetLicense, el nombre de la licencia que pase debe ser el del archivo de licencia. Por ejemplo, si cambia el nombre del archivo de licencia a "Aspose.Email.lic", pase ese nombre de archivo al método Emails->SetLicense(…).

{{% /alert %}} 

**C++**

``` cs

 intrusive_ptr<License> license = new License();

license->SetLicense(new String("Aspose.Email.lic"));

```
### **Cargar una Licencia desde un Objeto de Flujo**
El siguiente ejemplo muestra cómo cargar una licencia desde un flujo.

**C++**

``` cs

 intrusive_ptr<License>license = new License();

intrusive_ptr<FileStream> myStream = new FileStream(new String("Aspose.Email.lic"), FileMode_Open);

license->SetLicense(myStream);

```