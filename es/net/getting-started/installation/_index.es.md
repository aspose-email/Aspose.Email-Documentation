---
title: "Installation"
url: /es/net/installation/
weight: 70
type: docs
---


## **Instalación de Aspose.Email para.NET a través de NuGet**
NuGet es la forma más sencilla de descargar e instalar las API de Aspose para.NET. Abra el administrador de paquetes Microsoft Visual Studio y NuGet. Busca «aspose» para encontrar la API de Aspose deseada. Haga clic en «Instalar», la API seleccionada se descargará y se consultará en su proyecto.

![todo:image_alt_text](installation_1.png)
## **Instale o actualice Aspose.Email mediante la consola del administrador de paquetes**
Puedes seguir los pasos que se indican a continuación para hacer referencia a la API Aspose.Email mediante la consola del administrador de paquetes:

1. Abra su solución/proyecto en Visual Studio.
1. Seleccione Herramientas -> Administrador de paquetes de biblioteca -> Consola de administrador de paquetes en el menú para abrir la consola del administrador de paquetes.

![todo:image_alt_text](installation_2.png)

Escriba el comando»**Paquete de instalación Aspose.Email -Versión x.x.0**» y pulse enter para instalar la última versión completa en su aplicación. Si lo prefiere, puede añadir el»**-prerelease**«sufijo del comando para especificar que también se debe instalar la última versión, incluidas las correcciones urgentes.

![todo:image_alt_text](installation_3.png)

Si no está familiarizado con el [EULA de Aspose](http://www.aspose.com/corporate/purchase/end-user-license-agreement.aspx) entonces es una buena idea leer la licencia a la que se hace referencia en la URL. 

Ahora deberías comprobar que Aspose.Email se ha agregado correctamente y se ha hecho referencia a él en tu solicitud.

![todo:image_alt_text](installation_4.png)

En la consola del administrador de paquetes, también puede usar el comando»**Paquete de actualización Aspose.Email.net**» y pulse enter para comprobar si hay actualizaciones en el paquete Aspose.Email e instálelas si las hubiera. También puedes añadir el sufijo «-prerelease» para actualizar la última versión.
## **Hacer referencia al componente**
Para usar cualquier componente de la aplicación, añada una referencia a él. En los pasos siguientes se describe qué hacer al usar Visual Studio .NET.

1. En el Explorador de soluciones, expanda el nodo del proyecto al que desea agregar una referencia.
1. Haga clic derecho en **References** nodo para el proyecto y seleccione **Agregar referencia** del menú.
1. En el cuadro de diálogo Agregar referencia, seleccione **.NET** pestaña (normalmente está seleccionada de forma predeterminada).
1. Si ha utilizado el instalador MSI para instalar Aspose.Email, verá Aspose.Email en el panel superior. Selecciónelo y, a continuación, haga clic en **Select** button.
1. Si solo ha descargado y desempaquetado la DLL, haga clic en **Browse** botón y localice el archivo Aspose.Email.dll. Ha hecho referencia a Aspose.Email y debería aparecer en **SelectedComponents** panel del cuadro de diálogo.
1. Click **OK**. Aparece una referencia a Aspose.Email debajo del **References** nodo del proyecto.
## **Desinstalar Aspose.Email para.NET**
Si ha utilizado el instalador MSI para implementar Aspose.Email, siga estos pasos para eliminar por completo el componente y las demostraciones y la documentación asociadas:

1. Desde el **Start** menú, seleccionar **Settings** seguido de **Panel de control**.
1. Click **Agregar o quitar programas**.
1. Select **Aspose.Email**.
1. Haga clic en el **Change/Remove** botón para eliminar Aspose.Email.
## **Dirigido a una versión específica de.NET Framework**
Aunque Aspose.Email hace referencia a .NET Framework 1.1, es posible usarlo en una máquina que solo tenga instalada la versión 1.0. Sin embargo, es necesario añadir una entrada al archivo de configuración de la aplicación para redirigir las referencias, ya que, de lo contrario, el componente intentará cargar los ensamblajes desde .NET Framework 1.1. Todos los ensamblados que componen .NET Framework se deben redirigir para que usen la versión 1.0 de .NET Framework. El archivo de configuración es un archivo XML que se puede cambiar según sea necesario. Los desarrolladores pueden usarlo para cambiar la configuración sin tener que volver a compilar las aplicaciones. El nombre y la ubicación del archivo de configuración de la aplicación dependen del host de la aplicación, que puede ser uno de los siguientes:

- Aplicación alojada en un ejecutable: el archivo de configuración de una aplicación alojada por el host ejecutable se encuentra en el mismo directorio que la aplicación. El nombre del archivo de configuración es el nombre de la aplicación con la extensión.config. Por ejemplo, una aplicación denominada myApp.exe se puede asociar a un archivo de configuración denominado MyApp.exe.config.
- Aplicación alojada en ASP.NET: los archivos de configuración de ASP.NET se denominan Web.config y también se encuentran en el directorio de la aplicación. Introduzca el siguiente XML en el archivo de configuración de la aplicación:

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

Para obtener más información, consulte [Artículo de MSDN](http://msdn.microsoft.com/library/default.asp?url/library/en-us/cpguide/html/cpcontargetingnetframeworkversion.asp)
