---
title: "Trabajando con Contactos de Outlook usando la Biblioteca de Análisis de Correo C++"
description: "La Biblioteca de Análisis de Correo C++ te permite crear, guardar y leer contactos de Outlook e importar contactos de los formatos de archivo MSG y VCard."
url: /es/cpp/working-with-outlook-contacts/
weight: 90
type: docs
linktitle: "Trabajando con Contactos de Outlook"
---

## **Crear, Guardar y Leer Contactos**
Al igual que MapiMessage, Aspose.Email te permite crear contactos de Outlook. La clase MapiContact proporciona todas las propiedades relacionadas con el contacto necesarias para crear un contacto de Outlook. Este artículo muestra cómo crear, guardar y leer un contacto de Outlook usando la clase MapiContact.

### **Crear y Guardar un Contacto de Outlook**
Para crear un contacto y guardarlo en disco:

1. Instancia un nuevo objeto de la clase MapiContact.
2. Ingresa la información de las propiedades del contacto.
3. Agrega datos de foto (si los hay).
4. Guarda el contacto en formato MSG o VCard.

El siguiente fragmento de código te muestra cómo crear y guardar un contacto de Outlook con la Biblioteca de Análisis de Correo C++ o API.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateAndSaveOutlookContact-CreateAndSaveOutlookContact.cpp" >}}

### **Leyendo un MapiContact**
La clase MapiContact puede ser utilizada para cargar contactos de formato MSG y VCard de Outlook. El siguiente fragmento de código te muestra cómo cargar contactos de Outlook guardados como MSG y VCF en un MapiContact.

#### **Cargando un Contacto desde MSG**
El siguiente fragmento de código te muestra cómo cargar un contacto desde MSG.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-LoadingContactFromMSG-LoadingContactFromMSG.cpp" >}}

#### **Cargando un Contacto desde VCard**
El siguiente fragmento de código te muestra cómo cargar un contacto desde vCard.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-LoadingContactFromVCard-LoadingContactFromVCard.cpp" >}}