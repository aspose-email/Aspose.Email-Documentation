---
title: "Trabajando con Contactos de Gmail"
url: /es/net/working-with-gmail-contacts/
weight: 30
type: docs
---


Aspose.Email admite el trabajo con contactos de Gmail. Usando la interfaz [IGmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/), los usuarios pueden recuperar contactos de una cuenta de Gmail, crear nuevos contactos y actualizar o eliminar contactos existentes. Gmail permite a los desarrolladores realizar todas estas acciones mediante su API pública para desarrolladores. La siguiente información del usuario es necesaria para trabajar con los contactos de Gmail:
Nombre de usuario, dirección de correo electrónico, contraseña, ID del cliente, secreto del cliente, token de actualización.
Este artículo muestra cómo:

- [Acceder a los contactos de Gmail](/email/net/working-with-gmail-contacts/).
- [Crear nuevos contactos de Gmail](/email/net/working-with-gmail-contacts/).
- [Actualizar contactos existentes](/email/net/working-with-gmail-contacts/).
- [Eliminar un contacto](/email/net/working-with-gmail-contacts/).
- [Guardar contacto](/email/net/working-with-gmail-contacts/).
  
## **Acceso a los Contactos de Gmail**

Lo siguiente es una aplicación de muestra que se puede usar para acceder al detalle de los contactos en todos los grupos.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-AccessGmailContacts-AccessGmailContacts.cs" >}}

## **Creando un Contacto**

El siguiente fragmento de código muestra cómo crear un contacto.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-CreateGmailContact-CreateGmailContact.cs" >}}

## **Actualizando un Contacto**

Una vez que se recupera un contacto, sus atributos pueden actualizarse y el contacto puede guardarse nuevamente en la cuenta de Gmail. El siguiente fragmento de código muestra cómo recuperar contactos de una cuenta de Gmail y luego modificar uno de ellos, el cual se vuelve a guardar.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-UpdateGmailContact-UpdateGmailContact.cs" >}}

## **Eliminando un Contacto**

Para eliminar un contacto de Gmail, se utiliza el método [DeleteContact](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/deletecontact/#igmailclientdeletecontact-method) del cliente de Gmail, como se muestra en el siguiente fragmento de muestra.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-DeleteGmailContact-DeleteGmailContact.cs" >}}

## **Guardando un Contacto**

Aspose.Email permite guardar contactos en varios formatos de salida, como MSG y VCF. El método [Save](https://reference.aspose.com/email/net/aspose.email.personalinfo/contact/save/) proporciona la capacidad de lograr esto. El siguiente fragmento de código muestra cómo guardar un contacto.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-SavingContact-SavingContact.cs" >}}