---
title: "Trabajar con contactos de Gmail"
url: /es/net/working-with-gmail-contacts/
weight: 30
type: docs
---


Aspose.Email permite trabajar con contactos de Gmail. Utilizando el [IGmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/) interfaz, los usuarios pueden recuperar contactos de una cuenta de Gmail, crear nuevos contactos y actualizar y eliminar los contactos existentes. Gmail permite a los desarrolladores realizar todo esto mediante su API pública para desarrolladores. La siguiente información de usuario es necesaria para trabajar con los contactos de Gmail:
Nombre de usuario, dirección de correo electrónico, contraseña, identificador de cliente y token de actualización del secreto del cliente.
En este artículo se muestra cómo:

- [Acceder a los contactos de Gmail](/email/net/working-with-gmail-contacts/).
- [Crear nuevos contactos de Gmail](/email/net/working-with-gmail-contacts/).
- [Actualizar los contactos existentes](/email/net/working-with-gmail-contacts/).
- [Eliminar un contacto](/email/net/working-with-gmail-contacts/).
- [Guardar contacto](/email/net/working-with-gmail-contacts/).
 
## **Acceder a los contactos de Gmail**

El siguiente es un ejemplo de aplicación que se puede utilizar para acceder a los detalles de los contactos de todos los grupos.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-AccessGmailContacts-AccessGmailContacts.cs" >}}

## **Creación de un contacto**

El siguiente fragmento de código muestra cómo crear un contacto.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-CreateGmailContact-CreateGmailContact.cs" >}}

## **Actualización del contacto**

Una vez que se recupera un contacto, sus atributos se pueden actualizar y el contacto se puede volver a guardar en la cuenta de Gmail. En el siguiente fragmento de código, se muestra cómo recuperar contactos de una cuenta de Gmail y, a continuación, modificar una de ellas para guardarla de nuevo.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-UpdateGmailContact-UpdateGmailContact.cs" >}}

## **Eliminar contacto**

Para eliminar un contacto de Gmail, el cliente de Gmail [DeleteContact](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/deletecontact/#igmailclientdeletecontact-method) el método se usa como se muestra en el siguiente fragmento de ejemplo.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-DeleteGmailContact-DeleteGmailContact.cs" >}}

## **Guardar contacto**

Aspose.Email permite guardar contactos en varios formatos de salida, como MSG y VCF. El [Save](https://reference.aspose.com/email/net/aspose.email.personalinfo/contact/save/) el método proporciona la capacidad de lograr esto. El siguiente fragmento de código muestra cómo guardar un contacto.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-SavingContact-SavingContact.cs" >}}
