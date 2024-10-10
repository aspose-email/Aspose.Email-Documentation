---
title: "Установка"
url: /ru/net/installation/
weight: 70
type: docs
---

## **Установка Aspose.Email для .NET через NuGet**
NuGet — самый простой способ загрузить и установить API Aspose для .NET. Откройте Microsoft Visual Studio и менеджер пакетов NuGet. Найдите "aspose", чтобы найти желаемый API Aspose. Нажмите "Установить", выбранный API будет загружен и подключён в вашем проекте.

![todo:image_alt_text](installation_1.png)
## **Установить или обновить Aspose.Email с помощью консоли пакетного менеджера**
Вы можете выполнить следующие шаги, чтобы сослаться на API Aspose.Email с помощью консоли пакетного менеджера:

1. Откройте ваше решение/проект в Visual Studio.
1. Выберите Быстрые средства -> Диспетчер пакетов библиотеки -> Консоль диспетчера пакетов в меню, чтобы открыть консоль диспетчера пакетов.

![todo:image_alt_text](installation_2.png)

Введите команду “**Install-Package Aspose.Email -Version x.x.0**” и нажмите Enter, чтобы установить последнюю полную версию в ваше приложение. В качестве альтернативы вы можете добавить суффикс "**-prerelease**" к команде, чтобы указать, что необходимо установить последнюю версию, включая исправления.

![todo:image_alt_text](installation_3.png)

Если вы не знакомы с [лицензией Aspose](http://www.aspose.com/corporate/purchase/end-user-license-agreement.aspx), то будет хорошей идеей прочитать лицензию, упомянутую по указанной ссылке.

Теперь вы должны увидеть, что Aspose.Email успешно добавлен и подключён в вашем приложении.

![todo:image_alt_text](installation_4.png)

В консоли пакетного менеджера вы также можете использовать команду “**Update-Package Aspose.Email.NET**” и нажать Enter, чтобы проверить наличие обновлений для пакета Aspose.Email и установить их, если они есть. Вы также можете добавить суффикс "-prerelease", чтобы обновить до последней версии.
## **Подключение компонента**
Чтобы использовать любой компонент в вашем приложении, добавьте ссылку на него. Следующие шаги описывают, что делать, когда вы используете Visual Studio .NET.

1. В Обозревателе решений разверните узел проекта, к которому вы хотите добавить ссылку.
1. Щелкните правой кнопкой мыши узел **Ссылки** для проекта и выберите **Добавить ссылку** в меню.
1. В диалоговом окне Добавить ссылку выберите вкладку **.NET** (обычно она выбрана по умолчанию).
1. Если вы использовали установщик MSI для установки Aspose.Email, вы увидите Aspose.Email в верхней панели. Выберите его, а затем нажмите кнопку **Выбрать**.
1. Если вы загрузили и распаковали только DLL-файл, нажмите кнопку **Обзор** и найдите файл Aspose.Email.dll. Вы добавили ссылку на Aspose.Email, и он должен отображаться в панели **SelectedComponents** диалогового окна.
1. Нажмите **ОК**. Ссылка на Aspose.Email появится под узлом **Ссылки** проекта.
## **Удаление Aspose.Email для .NET**
Если вы использовали установщик MSI для развертывания Aspose.Email, выполните следующие шаги, чтобы полностью удалить компонент и связанные демонстрации и документацию:

1. В меню **Пуск** выберите **Настройки**, затем **Панель управления**.
1. Нажмите **Добавить/Удалить программы**.
1. Выберите **Aspose.Email**.
1. Нажмите кнопку **Изменить/Удалить**, чтобы удалить Aspose.Email.
## **Нацеливание на конкретную версию .NET Framework**
Хотя Aspose.Email ссылается на .NET Framework 1.1, возможно использовать его на машине с установленной только версией 1.0. Но вам нужно добавить запись в файл конфигурации приложения, чтобы перенаправить ссылки, так как в противном случае компонент попытается загрузить сборки из .NET Framework 1.1. Каждая сборка, составляющая .NET Framework, должна быть перенаправлена для использования версии .NET Framework 1.0. Файл конфигурации является XML-файлом, который может быть изменён по мере необходимости. Разработчики могут использовать его для изменения настроек без повторной компиляции приложений. Имя и расположение файла конфигурации приложения зависят от хоста приложения, который может быть одним из следующих:

- Исполняемое — приложение, размещённое на хосте: Файл конфигурации для приложения, размещённого исполняемым хостом, находится в той же директории, что и приложение. Имя файла конфигурации — это имя приложения с расширением .config. Например, приложение с именем myApp.exe может быть связано с файлом конфигурации с именем myApp.exe.config.
- Приложение, размещённое на ASP.NET: Файлы конфигурации ASP.NET называются Web.config и также размещаются в каталоге приложения. Введите следующий XML в файл конфигурации приложения:

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

Дополнительную информацию см. в [статье MSDN](http://msdn.microsoft.com/library/default.asp?url/library/en-us/cpguide/html/cpcontargetingnetframeworkversion.asp)