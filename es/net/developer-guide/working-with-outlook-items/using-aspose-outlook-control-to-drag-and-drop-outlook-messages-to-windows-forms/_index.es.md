---
title: "Usando el Control de Aspose Outlook para Arrastrar y Soltar Mensajes de Outlook en Formularios de Windows"
url: /es/net/using-aspose-outlook-control-to-drag-and-drop-outlook-messages-to-windows-forms/
weight: 45
type: docs
---


Aspose.Email soporta la funcionalidad de arrastrar y soltar de Microsoft Outlook. Permite a los desarrolladores crear fácilmente elementos de interfaz de usuario que respondan a los eventos de arrastre y soltar de Outlook. El siguiente ejemplo muestra cómo crear un panel sobre el cual los usuarios pueden arrastrar un mensaje de Outlook y soltarlo, y el programa para guardar mensajes en archivos MSG. El siguiente fragmento de código muestra cómo configurar un control de Aspose Outlook que puede recibir mensajes de Microsoft Outlook soltados.

- Crea una aplicación de formulario de Windows.
- Agrega una referencia a la ensambladura Aspose.Email.
- Navega al Aspose.Email.dll y haz clic en **Aceptar**.

El elemento de interfaz de usuario creado en este ejemplo es un panel. Para crear un panel:

- Haz clic derecho en tu proyecto en el panel de solución y elige **Agregar** y luego **Nuevo ítem** en el menú.
- Crea una clase llamada MyPanel:
- Deja que MyPanel sea una subclase de System.Windows.Form.Panel, y agrega una propiedad Aspose.Email.Windows.Forms.FileDropTargetManager a MyPanel:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-MyPanel-FileDropTargetManager.cs" >}}

- Sobrescribe los métodos OnHandleCreated y OnHandleDestroyed para registrar MyPanel usando Aspose.Email.Windows.Forms.FileDropTargetManager:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-MyPanel-OnHandleCreatedOnHandleDestroyed.cs" >}}

- Compila el proyecto.

MyPanel está listo para usar. Este panel acepta eventos de arrastrar y soltar de Outlook.

- Abre tu panel de caja de herramientas y arrastra MyPanel a tu formulario de Windows:

|![todo:image_alt_text](using-aspose-outlook-control-to-drag-and-drop-outlook-messages-to-windows-forms_1.png)|
| :- |

- Agrega un controlador de eventos al evento DragDrop de MyPanel. (No olvides establecer la propiedad AllowDrop en true desde el panel de propiedades y cambiar la propiedad BackColor de MyPanel a tu color favorito.)

|![todo:image_alt_text](using-aspose-outlook-control-to-drag-and-drop-outlook-messages-to-windows-forms_2.png)|
| :- |

- Agrega la siguiente línea en el método InitializeComponent() del formulario principal:

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-DragDropOutlookMessages.Designer-AllowDrop.cs" >}}

- Implementa el controlador de eventos DragDrop para guardar los mensajes arrastrados desde Outlook en archivos MSG.
- Convierte DragEventArgs a Aspose.Email.Windows.Forms.FileDragEventArgs que contiene una propiedad Files, que representa la colección de destino de arrastre del usuario.

Si un usuario arrastra varios mensajes de Outlook y los suelta en MyPanel, Files.Count es el número de mensajes, y Files itera por cada mensaje.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-DragDropOutlookMessages-DisplayFilesCount.cs" >}}

- Ejecuta el proyecto y pruébalo.

Ahora puedes arrastrar mensajes de Outlook y soltarlos en tu aplicación. La aplicación te solicita que guardes esos mensajes en archivos MSG.