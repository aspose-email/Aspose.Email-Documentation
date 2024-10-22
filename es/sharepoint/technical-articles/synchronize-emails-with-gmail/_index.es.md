---
title: "Sincronizar Correos Electrónicos con Gmail"
url: /es/sharepoint/synchronize-emails-with-gmail/
weight: 10
type: docs
---


{{% alert color="primary" %}} 

Aspose.Email para SharePoint soporta tanto los protocolos POP3 como IMAP al sincronizar correos electrónicos. Gmail también permite acceso gratuito a POP e IMAP para clientes de correo electrónico como Outlook Express, Microsoft Office Outlook, Thunderbird o cualquier API como Aspose.Network. 

Este artículo muestra cómo utilizar la función de sincronización de correos electrónicos de Aspose.Email para SharePoint para sincronizar correos electrónicos con Gmail.

{{% /alert %}} 
## **Sincronizando Correos Electrónicos**
El componente de conversión de correos electrónicos de Aspose.Email para SharePoint es una herramienta fácil de usar para sincronizar correos electrónicos con la lista personalizada de correos electrónicos de SharePoint. Con soporte para protocolos populares y servidores de correo electrónico, como POP3, IMAP y Microsoft Exchange Server, Aspose.Email puede conectarse con una variedad de servidores de correo electrónico y sincronizar correos electrónicos. 

Este artículo explica cómo [configurar Gmail](/email/sharepoint/synchronize-emails-with-gmail/) para que los correos electrónicos puedan ser descargados, [configurar SharePoint](/email/sharepoint/synchronize-emails-with-gmail/) para sincronizar correos electrónicos y cómo [ejecutar la sincronización manualmente](/email/sharepoint/synchronize-emails-with-gmail/).
### **Configurar Gmail**
Para obtener correos electrónicos de Gmail utilizando un cliente de correo electrónico, se debe habilitar POP o IMAP desde la página de configuración de Gmail. Por defecto, está deshabilitado.

Para habilitar POP3 e IMAP:

1. Inicie sesión en su cuenta de Gmail y haga clic en **Configuración** en la esquina superior derecha.
1. Haga clic en **Reenvío y POP/IMAP** para cambiar la configuración de POP e IMAP.
1. Habilite POP y elija la opción adecuada "Habilitar POP": 
   1. **Habilitar POP para todo el correo** para descargar todos los correos electrónicos (nuevos y antiguos).
   1. **Habilitar POP para el correo que llegue de ahora en adelante** para descargar solo correos electrónicos nuevos.
1. Habilite IMAP. Para IMAP, solo hay dos opciones: 
   1. **Habilitar** para descargar todos los mensajes de su buzón.
   1. **Deshabilitar** apaga el servicio. No seleccione esta opción. 

      **La pestaña Reenvío y POP/IMAP en Gmail** 

![todo:image_alt_text](synchronize-emails-with-gmail_1.png)

### **Configurar Aspose.Email para SharePoint**
1. En SharePoint, haga clic en **Configuraciones de Sincronización** en la cinta de **Herramientas Aspose** para abrir la ventana de configuración.
1. Especifique la configuración POP3 de Gmail para sincronizar con Gmail utilizando el protocolo POP3. Ingrese la siguiente información en esta pantalla: 
   1. Habilitar Sincronización: marcar
   1. Protocolo: POP3
   1. Servidor de correo: pop.gmail.com
   1. Puerto: 995
   1. SSL: marcar
   1. Dejar en el Servidor: marcar
   1. Nombre de usuario: username@gmail.com (especificar la dirección de correo electrónico completa)
   1. Contraseña: especificar la contraseña de Gmail
   1. Programar: elegir “Minutalmente” y “Cada 5 minutos” o lo que le convenga 
      **El cuadro de diálogo de Configuraciones de Sincronización.** 

![todo:image_alt_text](synchronize-emails-with-gmail_2.png)

1. Verifique la conexión haciendo clic en **Haga clic para probar los parámetros de conexión**. Si hay algo mal con las credenciales o la dirección del host, se mostrará un mensaje de error.
1. Haga clic en **Guardar** para guardar la configuración. Aspose.Email para SharePoint intenta conectarse a Gmail cada 5 minutos (o cualquier otro tiempo especificado). Descarga los mensajes y actualiza la lista de correos electrónicos.

Todos los adjuntos, imágenes incrustadas y el formato del cuerpo se conservan al descargar los mensajes y crear correos electrónicos en la lista personalizada de correos electrónicos de SharePoint. 
### **Sincronizando Correos Electrónicos Manualmente**
Para iniciar la sincronización manualmente: 

1. Haga clic en **Sincronizar ahora** en la cinta de **Herramientas Aspose**. Se muestra el cuadro de diálogo Sincronizar Ahora. La pantalla Sincronizar Ahora muestra un resumen de la configuración de la cuenta de correo electrónico y el estado de la última sincronización. 

   **El cuadro de diálogo Sincronizar Ahora.** 

![todo:image_alt_text](synchronize-emails-with-gmail_3.png)

1. Haga clic en **Sincronizar Ahora**. 

   **Correos electrónicos listados en una lista de SharePoint después de la sincronización exitosa** 

![todo:image_alt_text](synchronize-emails-with-gmail_4.png)

1. Haga clic en cualquier correo electrónico de la lista para abrirlo en SharePoint.

   **Un correo electrónico mostrado en SharePoint.** 

![todo:image_alt_text](synchronize-emails-with-gmail_5.png)
## **Referencias**
- [Instalando Aspose.Email para SharePoint](/email/sharepoint/install-aspose-email-for-sharepoint/)
- [Sincronizar Correos Electrónicos con el Servidor de Correo](/email/sharepoint/email-synchronization/)
- [Acerca del Componente de Sincronización de Correo Electrónico para SharePoint](/email/sharepoint/about-email-synchronization/)