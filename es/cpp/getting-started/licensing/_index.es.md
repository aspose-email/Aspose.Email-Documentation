---
title: "Licensing"
description: "Evalúe la API de la biblioteca C++ de correo electrónico y aplique la licencia mediante un archivo o un objeto de transmisión."
url: /es/cpp/licensing/
weight: 60
type: docs
---

## **Limitaciones de la versión de evaluación**
Se puede descargar una versión de evaluación gratuita de Aspose.Email para C++ desde la sección de descargas del sitio web de Aspose en: https://releases.aspose.com/email/cpp/

## **Aplicar la licencia mediante un archivo o un objeto de transmisión**
La licencia se puede cargar desde un archivo o un objeto de transmisión. Aspose.Eamil para C++ intentará encontrar la licencia en las siguientes ubicaciones:

1. Ruta explícita.
1. La carpeta que contiene Aspose.Cells.dll.
1. La carpeta que contiene el ensamblado que llamó a Aspose.Cells.dll.
1. La carpeta que contiene el ensamblado de la entrada (su.exe).
1. Un recurso integrado en el ensamblado que se llama Aspose.Cells.dll.

La forma más sencilla de configurar una licencia es colocar el archivo de licencia en la misma carpeta que el archivo Aspose.Email.dll y especificar el nombre del archivo, sin una ruta, como se muestra en el ejemplo siguiente.
### **Carga de una licencia desde un archivo**
La forma más sencilla de aplicar una licencia es colocar el archivo de licencia en la misma carpeta que el archivo Aspose.Email.dll y especificar solo el nombre del archivo sin una ruta.

{{% alert color="primary" %}}

Al llamar al método setLicense, el nombre de la licencia que transfiera debe ser el del archivo de licencia. Por ejemplo, si cambias el nombre del archivo de licencia a «Aspose.Email.lic», pasa ese nombre de archivo al método Emails->setLicense (...).

{{% /alert %}}

**C++**

``` cs

 intrusive_ptr<License> license = new License();

license->SetLicense(new String("Aspose.Email.lic"));

```
### **Carga de una licencia desde un objeto de transmisión**
El siguiente ejemplo muestra cómo cargar una licencia desde una transmisión.

**C++**

``` cs

 intrusive_ptr<License>license = new License();

intrusive_ptr<FileStream> myStream = new FileStream(new String("Aspose.Email.lic"), FileMode_Open);

license->SetLicense(myStream);

```
