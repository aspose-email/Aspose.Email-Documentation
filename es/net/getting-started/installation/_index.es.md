---
title: "Instalación"
url: /es/net/installation/
weight: 70
type: docs
---


## **Instalando Aspose.Email para .NET a través de NuGet**
NuGet es la forma más fácil de descargar e instalar las APIs de Aspose para .NET. Abre Microsoft Visual Studio y el administrador de paquetes de NuGet. Busca "aspose" para encontrar la API de Aspose deseada. Haz clic en "Instalar"; la API seleccionada será descargada y referenciada en tu proyecto.

![todo:image_alt_text](installation_1.png)
## **Instalar o Actualizar Aspose.Email usando la Consola del Administrador de Paquetes**
Puedes seguir los pasos a continuación para referenciar la API de Aspose.Email usando la consola del administrador de paquetes:

1. Abre tu solución/proyecto en Visual Studio.
1. Selecciona Herramientas -> Administrador de Paquetes de Biblioteca -> Consola del Administrador de Paquetes del menú para abrir la consola del administrador de paquetes.

![todo:image_alt_text](installation_2.png)

Escribe el comando “**Install-Package Aspose.Email -Version x.x.0**” y presiona enter para instalar la última versión completa en tu aplicación. Alternativamente, puedes agregar el sufijo "**-prerelease**" al comando para especificar que también se debe instalar la última versión que incluye correcciones rápidas.

![todo:image_alt_text](installation_3.png)

Si no estás familiarizado con el [Aspose EULA](http://www.aspose.com/corporate/purchase/end-user-license-agreement.aspx), entonces es una buena idea leer la licencia referenciada en la URL.

Ahora deberías encontrar que Aspose.Email ha sido añadido y referenciado exitosamente en tu aplicación.

![todo:image_alt_text](installation_4.png)

En la consola del administrador de paquetes, también puedes usar el comando “**Update-Package Aspose.Email.NET**” y presionar enter para buscar actualizaciones en el paquete Aspose.Email e instalarlas si están presentes. También puedes agregar el sufijo "-prerelease" para actualizar la última versión.
## **Referenciando el Componente**
Para usar cualquier componente en tu aplicación, añade una referencia a él. Los pasos que siguen describen qué hacer cuando usas Visual Studio .NET.

1. En el Explorador de Soluciones, expande el nodo del proyecto al que deseas agregar una referencia.
1. Haz clic derecho en el nodo **Referencias** del proyecto y selecciona **Agregar Referencia** del menú.
1. En el cuadro de diálogo Agregar Referencia, selecciona la pestaña **.NET** (generalmente está seleccionada por defecto).
1. Si has utilizado un instalador MSI para instalar Aspose.Email, verás Aspose.Email en el panel superior. Selecciónalo y luego haz clic en el botón **Seleccionar**.
1. Si solo has descargado y descomprimido el DLL, haz clic en el botón **Examinar** y localiza el archivo Aspose.Email.dll. Has referenciado Aspose.Email y debería aparecer en el panel **SelectedComponents** del cuadro de diálogo.
1. Haz clic en **Aceptar**. Una referencia de Aspose.Email aparece bajo el nodo **Referencias** del proyecto.
## **Desinstalando Aspose.Email para .NET**
Si has utilizado un instalador MSI para desplegar Aspose.Email, sigue estos pasos para eliminar completamente el componente y las demostraciones y documentación asociadas:

1. Desde el menú **Inicio**, selecciona **Configuración** seguido de **Panel de Control**.
1. Haz clic en **Agregar/Quitar Programas**.
1. Selecciona **Aspose.Email**.
1. Haz clic en el botón **Cambiar/Quitar** para quitar Aspose.Email.
## **Dirigiendo a una Versión Específica de .NET Framework**
Aunque Aspose.Email referencia .NET Framework 1.1, es posible usarlo en una máquina con solo la versión 1.0 instalada. Pero necesitas agregar una entrada al archivo de configuración de la aplicación para redirigir las referencias porque de lo contrario el componente intentará cargar ensamblados de .NET Framework 1.1. Cada ensamblado que compone .NET Framework debe ser redirigido para usar la versión 1.0 de .NET Framework. El archivo de configuración es un archivo XML que puede ser cambiado según sea necesario. Los desarrolladores pueden usarlo para cambiar configuraciones sin recompilar aplicaciones. El nombre y la ubicación del archivo de configuración de la aplicación dependen del host de la aplicación, que puede ser uno de los siguientes:

- Aplicación alojada en un ejecutable: El archivo de configuración para una aplicación alojada por el host ejecutable está en el mismo directorio que la aplicación. El nombre del archivo de configuración es el nombre de la aplicación con una extensión .config. Por ejemplo, una aplicación llamada myApp.exe puede estar asociada con un archivo de configuración llamado myApp.exe.config.
- Aplicación alojada en ASP.NET: Los archivos de configuración de ASP.NET se llaman Web.config y también se colocan en el directorio de la aplicación. Ingresa el siguiente XML en el archivo de configuración de la aplicación:

**XML**

``` cs

 <configuration>

  <startup>

    <requiredRuntime version="v1.0.3705"  />

  </startup>

  <runtime>

    <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">

      <dependentAssembly>

        <assemblyIdentity name="Regcode" publicKeyToken="b03f5f7f11d50a3a" culture=""/>

        <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>

      </dependentAssembly>

      <dependentAssembly>

        <assemblyIdentity name="System.EnterpriseServices" publicKeyToken="b03f5f7f11d50a3a" culture=""/>

        <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>

      </dependentAssembly>

      <dependentAssembly>

        <assemblyIdentity name="System.Security" publicKeyToken="b03f5f7f11d50a3a" culture=""/>

        <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>

      </dependentAssembly>

      <dependentAssembly>

        <assemblyIdentity name="CustomMarshalers" publicKeyToken="b03f5f7f11d50a3a" culture=""/>

        <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>

      </dependentAssembly>

      <dependentAssembly>

        <assemblyIdentity name="Accessibility" publicKeyToken="b03f5f7f11d50a3a" culture=""/>

        <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>

      </dependentAssembly>

      <dependentAssembly>

        <assemblyIdentity name="System.Configuration.Install" publicKeyToken="b03f5f7f11d50a3a" culture=""/>

        <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>

      </dependentAssembly>

      <dependentAssembly>

        <assemblyIdentity name="System.DirectoryServices" publicKeyToken="b03f5f7f11d50a3a" culture=""/>

        <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>

      </dependentAssembly>

      <dependentAssembly>

        <assemblyIdentity name="System.Drawing.Design" publicKeyToken="b03f5f7f11d50a3a" culture=""/>

        <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>

      </dependentAssembly>

      <dependentAssembly>

        <assemblyIdentity name="System.ServiceProcess" publicKeyToken="b03f5f7f11d50a3a" culture=""/>

        <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>

      </dependentAssembly>

      <dependentAssembly>

        <assemblyIdentity name="System.Web" publicKeyToken="b03f5f7f11d50a3a" culture=""/>

        <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>

      </dependentAssembly>

      <dependentAssembly>

        <assemblyIdentity name="System.Web.RegularExpressions" publicKeyToken="b03f5f7f11d50a3a" culture=""/>

        <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>

      </dependentAssembly>

      <dependentAssembly>

        <assemblyIdentity name="System.Web.Services" publicKeyToken="b03f5f7f11d50a3a" culture=""/>

        <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>

      </dependentAssembly>

      <dependentAssembly>

        <assemblyIdentity name="System.Windows.Forms" publicKeyToken="b77a5c561934e089" culture=""/>

        <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>

      </dependentAssembly>

      <dependentAssembly>

        <assemblyIdentity name="System.Xml" publicKeyToken="b77a5c561934e089" culture=""/>

        <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>

      </dependentAssembly>

      <dependentAssembly>

        <assemblyIdentity name="System.Data" publicKeyToken="b77a5c561934e089" culture=""/>

        <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>

      </dependentAssembly>

      <dependentAssembly>

        <assemblyIdentity name="System.Design" publicKeyToken="b03f5f7f11d50a3a" culture=""/>

        <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>

      </dependentAssembly>

      <dependentAssembly>

        <assemblyIdentity name="System.Drawing" publicKeyToken="b03f5f7f11d50a3a" culture=""/>

        <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>

      </dependentAssembly>

      <dependentAssembly>

        <assemblyIdentity name="System" publicKeyToken="b77a5c561934e089" culture=""/>

        <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>

      </dependentAssembly>

      <dependentAssembly>

        <assemblyIdentity name="System.Messaging" publicKeyToken="b03f5f7f11d50a3a" culture=""/>

        <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>

      </dependentAssembly>

      <dependentAssembly>

        <assemblyIdentity name="IEExecRemote" publicKeyToken="b03f5f7f11d50a3a" culture=""/>

        <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>

      </dependentAssembly>

      <dependentAssembly>

        <assemblyIdentity name="IEHost" publicKeyToken="b03f5f7f11d50a3a" culture=""/>

        <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>

      </dependentAssembly>

      <dependentAssembly>

        <assemblyIdentity name="IIEHost" publicKeyToken="b03f5f7f11d50a3a" culture=""/>

        <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>

      </dependentAssembly>

      <dependentAssembly>

        <assemblyIdentity name="ISymWrapper" publicKeyToken="b03f5f7f11d50a3a" culture=""/>

        <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>

      </dependentAssembly>

      <dependentAssembly>

        <assemblyIdentity name="mscorcfg" publicKeyToken="b03f5f7f11d50a3a" culture=""/>

        <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>

      </dependentAssembly>

      <dependentAssembly>

        <assemblyIdentity name="System.Management" publicKeyToken="b03f5f7f11d50a3a" culture=""/>

        <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>

      </dependentAssembly>

      <dependentAssembly>

        <assemblyIdentity name="System.Runtime.Remoting" publicKeyToken="b77a5c561934e089" culture=""/>

        <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>

      </dependentAssembly>

      <dependentAssembly>

        <assemblyIdentity name="System.Runtime.Serialization.Formatters.Soap" publicKeyToken="b03f5f7f11d50a3a" culture=""/>

        <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>

      </dependentAssembly>

      <dependentAssembly>

        <assemblyIdentity name="System.Web.Mobile" publicKeyToken="b03f5f7f11d50a3a" culture=""/>

        <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>

      </dependentAssembly>

      <dependentAssembly>

        <assemblyIdentity name="Microsoft.Vsa.Vb.CodeDOMProcessor" publicKeyToken="b03f5f7f11d50a3a" culture=""/>

        <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="7.0.3300.0"/>

      </dependentAssembly>

      <dependentAssembly>

        <assemblyIdentity name="Microsoft_VsaVb" publicKeyToken="b03f5f7f11d50a3a" culture=""/>

        <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="7.0.3300.0"/>

      </dependentAssembly>

      <dependentAssembly>

        <assemblyIdentity name="Microsoft.Vsa" publicKeyToken="b03f5f7f11d50a3a" culture=""/>

        <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="7.0.3300.0"/>

      </dependentAssembly>

      <dependentAssembly>

        <assemblyIdentity name="Microsoft.VisualBasic.Vsa" publicKeyToken="b03f5f7f11d50a3a" culture=""/>

        <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="7.0.3300.0"/>

      </dependentAssembly>

      <dependentAssembly>

        <assemblyIdentity name="cscompmgd" publicKeyToken="b03f5f7f11d50a3a" culture=""/>

        <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="7.0.3300.0"/>

      </dependentAssembly>

      <dependentAssembly>

        <assemblyIdentity name="Microsoft.JScript" publicKeyToken="b03f5f7f11d50a3a" culture=""/>

        <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="7.0.3300.0"/>

      </dependentAssembly>

      <dependentAssembly>

        <assemblyIdentity name="Microsoft.VisualBasic" publicKeyToken="b03f5f7f11d50a3a" culture=""/>

        <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="7.0.3300.0"/>

      </dependentAssembly>

      <dependentAssembly>

        <assemblyIdentity name="Microsoft.VisualC" publicKeyToken="b03f5f7f11d50a3a" culture=""/>

        <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="7.0.3300.0"/>

      </dependentAssembly>

    </assemblyBinding>

  </runtime>

</configuration>

``` 

Para más información consulta el [artículo de MSDN](http://msdn.microsoft.com/library/default.asp?url/library/en-us/cpguide/html/cpcontargetingnetframeworkversion.asp)