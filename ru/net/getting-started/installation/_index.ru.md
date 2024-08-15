---
title: "Installation"
url: /ru/net/installation/
weight: 70
type: docs
---


## **Установка Aspose.Email для .NET через NuGet**
NuGet — это самый простой способ загрузить и установить Aspose API для.NET. Откройте Microsoft Visual Studio и диспетчер пакетов NuGet. Выполните поиск по запросу «aspose», чтобы найти нужный API Aspose. Нажмите «Установить», выбранный API будет загружен и добавлен в ваш проект.

![todo:image_alt_text](installation_1.png)
## **Установите или обновите Aspose.Email с помощью консоли диспетчера пакетов**
Чтобы обратиться к API Aspose.Email с помощью консоли диспетчера пакетов, выполните следующие действия:

1. Откройте свое решение/проект в Visual Studio.
1. Выберите в меню Инструменты -> Менеджер пакетов библиотек -> Консоль диспетчера пакетов, чтобы открыть консоль диспетчера пакетов.

![todo:image_alt_text](installation_2.png)

Введите команду»**Установить пакет Aspose.Email - Версия x.x.0**» и нажмите Enter, чтобы установить последнюю полную версию в свое приложение. Кроме того, вы можете добавить кнопку»**-prerelease**«суффикс» к команде, указывающий, что также должна быть установлена последняя версия, включая исправления.

![todo:image_alt_text](installation_3.png)

Если вы не знакомы с [Примите лицензионное соглашение](http://www.aspose.com/corporate/purchase/end-user-license-agreement.aspx) тогда рекомендуется прочитать лицензию, указанную в URL-адресе. 

Теперь вы должны обнаружить, что Aspose.Email успешно добавлен и указан в вашем приложении.

![todo:image_alt_text](installation_4.png)

В консоли диспетчера пакетов вы также можете использовать команду»**Пакет обновлений Aspose.email.net**» и нажмите enter, чтобы проверить наличие обновлений в пакете Aspose.Email и установить их, если они есть. Вы также можете добавить суффикс «-prerelease», чтобы обновить последнюю версию.
## **Ссылка на компонент**
Чтобы использовать любой компонент в приложении, добавьте ссылку на него. Следующие шаги описывают, что делать при использовании Visual Studio.NET.

1. В обозревателе решений разверните узел проекта, на который вы хотите добавить ссылку.
1. Щелкните правой кнопкой мыши **References** узел для проекта и выберите **Добавить ссылку** из меню.
1. В диалоговом окне «Добавить ссылку» выберите **.NET** вкладка (обычно она выбрана по умолчанию).
1. Если вы использовали установщик MSI для установки Aspose.Email, вы увидите Aspose.Email на верхней панели. Выберите его, а затем нажмите **Select** button.
1. Если вы загрузили и распаковали только DLL, нажмите кнопку **Browse** нажмите кнопку и найдите файл Aspose.Email.dll. Вы указали ссылку на Aspose.Email, и она должна появиться в **SelectedComponents** панель диалогового окна.
1. Click **OK**. Ссылка на Aspose.Email отображается под полем **References** узел проекта.
## **Удаление Aspose.Email для.NET**
Если вы использовали установщик MSI для развертывания Aspose.Email, выполните следующие действия, чтобы полностью удалить компонент и связанные с ним демоверсии и документацию:

1. Из **Start** меню, выберите **Settings** за которым следует **Панель управления**.
1. Click **Установка и удаление программ**.
1. Select **Aspose.Email**.
1. Нажмите кнопку **Change/Remove** кнопка для удаления Aspose.Email.
## **Ориентация на определенную версию платформы.NET**
Хотя Aspose.Email ссылается на платформу.NET Framework 1.1, его можно использовать на компьютере, на котором установлена только версия 1.0. Но для перенаправления ссылок необходимо добавить запись в файл конфигурации приложения, поскольку в противном случае компонент попытается загрузить сборки из .NET Framework 1.1. Каждую сборку, входящую в состав платформы.NET Framework, необходимо перенаправить на использование платформы.NET Framework версии 1.0. Конфигурационный файл — это XML-файл, который можно изменять по мере необходимости. Разработчики могут использовать его для изменения настроек без повторной компиляции приложений. Имя и расположение файла конфигурации приложения зависят от хоста приложения. Это может быть одно из следующих мест:

- Приложение, размещенное на исполняемом файле: файл конфигурации приложения, размещенного на исполняемом хосте, находится в том же каталоге, что и приложение. Имя файла конфигурации — это имя приложения с расширением.config. Например, приложение под названием myApp.exe можно связать с файлом конфигурации под названием MyApp.exe.config.
- Приложение, размещенное на ASP.NET: файлы конфигурации ASP.NET называются Web.config и также помещаются в каталог приложения. Введите следующий XML в файл конфигурации приложения:

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

Для получения дополнительной информации см. [Статья MSDN](http://msdn.microsoft.com/library/default.asp?url/library/en-us/cpguide/html/cpcontargetingnetframeworkversion.asp)
