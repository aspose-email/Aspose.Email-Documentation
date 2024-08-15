---
title: "Uso del control Aspose Outlook para arrastrar y soltar mensajes de Outlook en Windows Forms"
url: /es/net/using-aspose-outlook-control-to-drag-and-drop-outlook-messages-to-windows-forms/
weight: 45
type: docs
---


Aspose.Email admite la función de arrastrar y soltar de Microsoft Outlook. Permite a los desarrolladores crear fácilmente elementos de interfaz de usuario que respondan a los eventos de arrastrar y soltar de Outlook. En el ejemplo siguiente se muestra cómo crear un panel en el que los usuarios puedan arrastrar un mensaje de Outlook y soltarlo, así como el programa para guardar los mensajes en archivos MSG. En el siguiente fragmento de código se muestra cómo configurar un control Aspose Outlook que pueda recibir los mensajes de Microsoft Outlook descartados.

- Cree una aplicación de formulario de Windows.
- Agregue una referencia al ensamblaje Aspose.Email.
- Navegue hasta Aspose.Email.dll y haga clic **OK**.

El elemento de interfaz de usuario creado en este ejemplo es un panel. Para crear un panel:

- Haga clic con el botón derecho en su proyecto en el panel de soluciones y seleccione **Add** y luego **Artículo nuevo** del menú.
- Crea una clase llamada MyPanel:
- Deje que MyPanel sea una subclase de System.Windows.Form.Panel y agregue una propiedad Aspose.Email.Windows.Forms.FileDropTargetManager a MyPanel:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-MyPanel-FileDropTargetManager.cs" >}}

- Anule los métodos onHandleCreated y onHandleDestroyed para registrar MyPanel mediante Aspose.Email.Windows.Forms.FileDropTargetManager:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-MyPanel-OnHandleCreatedOnHandleDestroyed.cs" >}}

- Construye el proyecto.

MyPanel está listo para usarse. Este panel permite arrastrar y soltar eventos desde Outlook.

- Abre el panel de tu caja de herramientas y arrastra MyPanel a tu formulario de Windows:

|![todo:image_alt_text](using-aspose-outlook-control-to-drag-and-drop-outlook-messages-to-windows-forms_1.png)|
|: - |

- Agregue un controlador de eventos al evento DragDrop de MyPanel. (No olvides establecer la propiedad allowDrop} en true desde el panel de propiedades y cambiar la propiedad BackColor de MyPanel por tu favorita).

|![todo:image_alt_text](using-aspose-outlook-control-to-drag-and-drop-outlook-messages-to-windows-forms_2.png)|
|: - |

- Agregue la siguiente línea en el método initializeComponent () del formulario principal:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-DragDropOutlookMessages.Designer-AllowDrop.cs" >}}

- Implemente el controlador de eventos DragDrop para guardar los mensajes arrastrados desde Outlook a archivos MSG.
- Convierte DragEventArgs en Aspose.Email.Windows.Forms.FileDragEventArgs, que contiene una propiedad de array Files que representa el objetivo de arrastre del usuario.

Si un usuario arrastra varios mensajes de Outlook y los coloca en MyPanel, Files.Count es el número de mensajes y Files i se repite para cada mensaje.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-DragDropOutlookMessages-DisplayFilesCount.cs" >}}

- Ejecute el proyecto y pruébelo.

Ahora puedes arrastrar mensajes desde Outlook y soltarlos en tu aplicación. La aplicación le pide que guarde esos mensajes en archivos MSG.
