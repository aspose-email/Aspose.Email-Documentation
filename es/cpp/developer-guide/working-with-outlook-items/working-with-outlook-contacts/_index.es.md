---
title: "Trabajar con contactos de Outlook mediante la biblioteca de analizadores de correo electrónico de C++"
description: "La biblioteca de analizadores de correo electrónico de C++ le permite crear, guardar y leer contactos de Outlook e importar contactos desde formatos de archivo MSG y vCard."
url: /es/cpp/working-with-outlook-contacts/
weight: 90
type: docs
linktitle: "Trabajar con contactos de Outlook"
---

## **Crear, guardar y leer contactos**
Al igual que MapiMessage, Aspose.Email te permite crear contactos de Outlook. La clase MapiContact proporciona todas las propiedades relacionadas con los contactos necesarias para crear un contacto de Outlook. En este artículo se muestra cómo crear, guardar y leer un contacto de Outlook mediante la clase MapiContact.

### **Crear y guardar contactos de Outlook**
Para crear un contacto y guardarlo en un disco:

1. Cree una instancia de un objeto nuevo de la clase MapiContact.
1. Introduzca la información de contacto de la propiedad.
1. Agregue datos fotográficos (si los hay).
1. Guarda el contacto en formato MSG o vCard.

El siguiente fragmento de código muestra cómo crear y guardar contactos de Outlook con la biblioteca o API del analizador de correo electrónico de C++.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateAndSaveOutlookContact-CreateAndSaveOutlookContact.cpp" >}}

### **Lectura de un MapiContact**
La clase MapiContact se puede usar para cargar contactos en formato MSG y vCard de Outlook. El siguiente fragmento de código muestra cómo cargar los contactos de Outlook guardados como MSG y VCF en un MapiContact.

#### **Cargar un contacto desde MSG**
El siguiente fragmento de código muestra cómo cargar un contacto desde MSG.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-LoadingContactFromMSG-LoadingContactFromMSG.cpp" >}}

#### **Cargar un contacto desde vCard**
El siguiente fragmento de código muestra cómo cargar un contacto desde vCard.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-LoadingContactFromVCard-LoadingContactFromVCard.cpp" >}}
