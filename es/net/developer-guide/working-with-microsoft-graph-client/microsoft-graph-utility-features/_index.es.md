---
title: "Características de Microsoft Graph Utility"
url: /es/net/microsoft-graph-utility-features/
weight: 10
type: docs
---


## **Creación de un proyecto en el Centro de administración de Azure Active Directory**

Se va a crear un proyecto en el centro de administración de Azure Active Directory para un usuario que tenga una cuenta de MS Office.

### **Pasos para crear un proyecto en el Centro de administración de Azure Active Directory**

A continuación se muestra un tutorial paso a paso para crear un proyecto en el centro de administración de Azure Active Directory.

#### 1. Vaya a Azure Active Directory e inicie sesión con sus credenciales de MS Office.

**Azure Active Directory** Enlace - <https://aad.portal.azure.com/>

#### 2. Cree una aplicación Azure AD en su inquilino.

En el panel lateral izquierdo, haga clic en la etiqueta **Azure Active Directory**. Esto abrirá la hoja para Azure Active Directory. En esa pantalla deberías ver una etiqueta **Registros de aplicaciones**. Este es el punto de partida para registrar una aplicación Azure AD. Esta hoja le permitirá crear una nueva aplicación para Azure AD.

Haga clic en el botón **Nuevo registro** para crear una nueva aplicación.

![todo:image_alt_text](microsoft-graph-utility-features_1.png)

#### 3. Ahora verá la nueva hoja de registro de aplicaciones.

- **Name** Este será el nombre de su solicitud.
- **Tipos de cuentas compatibles** Esta sección restringirá el acceso.

Click **Register** button.

![todo:image_alt_text](microsoft-graph-utility-features_2.png)

#### 4. Debería ver la hoja de aplicaciones recién registradas.

- **ID de aplicación (cliente)** El identificador de su solicitud.
- **ID de directorio (inquilino)** El identificador de inquilino de Azure AD.

![todo:image_alt_text](microsoft-graph-utility-features_6.png)

#### 5. Permitir permisos para la API de Microsoft Graph.

Haga clic en el **Permisos de API** label.

Azure ya le ha dado **User.Read** permisos delegados para su aplicación. Este permiso nos permitirá leer la información de usuario de un usuario que haya iniciado sesión. Estos son los permisos de la API de Microsoft Graph, también podemos llamarlos **Scopes**.

La lista completa de ámbitos de la API de Microsoft Graph - <https://learn.microsoft.com/en-us/graph/permissions-reference>.

Haga clic en **+ Añadir un permiso** botón y selección **Microsoft Graph**.

Haga clic en **Permisos delegados**. Ahora puede ver una lista de los permisos disponibles para la API de Microsoft Graph.

Seleccione los permisos necesarios y haga clic **Añadir permisos** button.

Click **Otorgar el consentimiento del administrador** button.

![todo:image_alt_text](microsoft-graph-utility-features_3.png)

#### 6. Permita los flujos de clientes públicos.

Especifica si la aplicación es un cliente público. Apropiado para aplicaciones que utilizan flujos de concesión de tokens que no utilizan un URI de redireccionamiento.

![todo:image_alt_text](microsoft-graph-utility-features_4.png)

#### 7. Crea una clave para la aplicación

![todo:image_alt_text](microsoft-graph-utility-features_5.png)
