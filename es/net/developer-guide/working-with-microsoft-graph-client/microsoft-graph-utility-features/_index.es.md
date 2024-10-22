---
title: "Características de Utilidad de Microsoft Graph"
url: /es/net/microsoft-graph-utility-features/
weight: 10
type: docs
---


## **Creando un Proyecto en el Centro de Administración de Azure Active Directory**

Se debe crear un Proyecto en el centro de administración de Azure Active Directory para un usuario que tenga cuenta de MS Office.

### **Pasos para Crear un Proyecto en el Centro de Administración de Azure Active Directory**

A continuación se presenta un tutorial paso a paso para crear un proyecto en el centro de administración de Azure Active Directory.

#### 1. Ve a Azure Active Directory e inicia sesión con tus credenciales de MS Office.

**Azure Active Directory** Enlace - <https://aad.portal.azure.com/>

#### 2. Crea una Aplicación de Azure AD en tu inquilino.

En el panel izquierdo, haz clic en la etiqueta **Azure Active Directory**. Esto abrirá el panel para Azure Active Directory. En esa pantalla deberías ver una etiqueta **Registros de aplicaciones**. Este es el punto de partida para registrar una Aplicación de Azure AD. Este panel te permitirá crear una nueva aplicación para Azure AD.

Haz clic en el botón **Nueva registro** para crear una nueva aplicación.

![todo:image_alt_text](microsoft-graph-utility-features_1.png)

#### 3. Ahora verás el panel de registro de la nueva aplicación.

- **Nombre** Este será el nombre de tu aplicación.
- **Tipos de cuentas soportadas** Esta sección restringirá el acceso.

Haz clic en el botón **Registrar**.

![todo:image_alt_text](microsoft-graph-utility-features_2.png)

#### 4. Deberías ver el panel de aplicaciones recién registradas.

- **ID de aplicación (cliente)** El id de tu aplicación.
- **ID de directorio (inquilino)** El id del inquilino de Azure AD.

![todo:image_alt_text](microsoft-graph-utility-features_6.png)

#### 5. Permitir permisos para Microsoft Graph API.

Haz clic en la etiqueta **Permisos de API**.

Azure ya te ha otorgado permisos delegados **User.Read** para tu aplicación. Este permiso nos permitirá leer la información del usuario para un usuario conectado. Estos son permisos de la API de Microsoft Graph, también los podemos llamar **Alcances**.

La lista completa de alcances para la API de Microsoft Graph - <https://learn.microsoft.com/en-us/graph/permissions-reference>.

Haz clic en el botón **+ Agregar un permiso** y selecciona **Microsoft Graph**.

Haz clic en **Permisos delegados**. Ahora verás una lista de permisos disponibles para la API de Microsoft Graph.

Selecciona los permisos requeridos, haz clic en el botón **Agregar permisos**.

Haz clic en el botón **Conceder consentimiento de administrador**.

![todo:image_alt_text](microsoft-graph-utility-features_3.png)

#### 6. Permitir flujos de cliente público.

Especifica si la aplicación es un cliente público. Apropiado para aplicaciones que utilizan flujos de concesión de tokens que no utilizan un URI de redirección.

![todo:image_alt_text](microsoft-graph-utility-features_4.png)

#### 7. Crear una clave para la aplicación

![todo:image_alt_text](microsoft-graph-utility-features_5.png)