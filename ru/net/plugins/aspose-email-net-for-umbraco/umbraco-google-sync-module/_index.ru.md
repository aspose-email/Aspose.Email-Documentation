---
title: "Модуль синхронизации Umbraco Google"
url: /ru/net/umbraco-google-sync-module/
weight: 20
type: docs
---


## **Introduction**
Aspose.NET Gmail Sync для Umbraco — это модуль с открытым исходным кодом от [Aspose](http://www.aspose.com/) который связывает ваших пользователей/участников Umbraco с контактами Google или Gmail без использования какого-либо другого программного обеспечения. Он использует мощные функции [Электронная почта Aspose.NET](http://www.aspose.com/.net/email-component.aspx) чтобы вы могли легко синхронизировать контакты Gmail и пользователей/участников Umbraco.
### **Характеристики модуля**
Эта начальная версия модуля обогащена следующими функциями, которые делают процесс синхронизации эффективным, простым и удобным в использовании.

- Учетные данные сервера Google/Gmail зашифрованы и сохраняются в базе данных, поэтому вам не нужно вводить их каждый раз при использовании модуля.
- Синхронизируйте все или выбранные контакты Gmail с Umbraco и наоборот.
- Возможность выбрать один или несколько типов пользователя/участника Umbraco при синхронизации Gmail с Umbraco.
- Перед переносом проверяется наличие каждого контакта/пользователя в целевой системе, чтобы убедиться, что синхронизация не создает дубликатов записей.
- Контакты, перенесенные в Gmail, помещаются в группу «Другие контакты», чтобы вы могли проверить и перенести в «Мои контакты» только нужные контакты.
- По завершении отображается краткое описание процесса синхронизации.

![todo:image_alt_text](http://www.aspose.com/blogs/wp-content/uploads/2014/11/Aspose-.NET-Gmail-Sync-for-Umbraco.png)

![todo:image_alt_text](http://www.aspose.com/blogs/wp-content/uploads/2014/11/Gmail-to-Umbraco-Sync.png)

![todo:image_alt_text](http://www.aspose.com/blogs/wp-content/uploads/2014/11/Umbraco-to-Gmail-Sync.png)
## **Системные требования и поддерживаемые платформы**
### **Системные требования**
Чтобы настроить модуль Aspose.NET Exchange/Google Sync для Umbraco, вам необходимо выполнить следующие требования:

- Умбрако 6.0 +

Пожалуйста, свяжитесь с нами, если вы хотите установить этот модуль на более старую версию Umbraco.
### **Поддерживаемые платформы**
Модуль поддерживается во всех версиях

- Umbraco работает на ASP.NET 4.0
## **Downloading**
Вы можете скачать Aspose.NET Google Sync для Umbraco из одного из следующих мест

- [CodePlex ](https://asposeumbraco.codeplex.com/releases)
- [Github ](https://github.com/asposemarketplace/Aspose_for_Umbraco/releases)
- [Sourceforge ](https://sourceforge.net/projects/asposeumbraco/files/)
- [Bitbucket ](https://bitbucket.org/asposemarketplace/aspose-for-umbraco/downloads)
- [Umbraco ](https://our.umbraco.org/projects/website-utilities/sync-umbraco-users-and-members-with-google-contacts-using-aspose-net-gmail-sync-for-umbraco)
## **Installing**
После загрузки выполните следующие действия, чтобы установить модуль на свой веб-сайт Umbraco:

1. Войдите в систему Umbraco **Developer** раздел, например <http://www.myblog.com/umbraco/>
1. Из дерева разверните **Packages** folder.
1. Отсюда есть два способа установки пакета: выберите **Установить локальный пакет** или просмотрите **Репозиторий пакетов Umbraco.**
1. Если вы устанавливаете **местный пакет**, не разархивируйте пакет, а загрузите zip-архив в Umbraco.
1. Следуйте инструкциям на экране.
## **Using**
После того, как вы установили модуль Aspose.NET Gmail Sync for Umbraco, начать использовать его на своем веб-сайте очень просто. Для начала выполните следующие простые шаги

1. Убедитесь, что вы вошли в Umbraco **Developer** раздел, например <http://www.myblog.com/umbraco/>
1. Click **Settings** в списке разделов в левом нижнем углу экрана.
1. Расширьте **Templates** выберите шаблон, в который вы хотите добавить функцию синхронизации Gmail, например Textpage.
1. Выберите позицию в выбранном шаблоне, куда вы хотите добавить кнопку экспорта. Обычно вы можете добавить ее в верхнюю правую часть страницы или в нижнюю часть страницы.
1. Click **Вставить макрос** на верхней ленте.
1. From **Выберите макрос**выберите недавно установленный макрос Aspose.NET Gmail Sync for Umbraco и нажмите **OK**.

Подробности смотрите на скриншоте ниже.

![todo:image_alt_text](http://www.aspose.com/blogs/wp-content/uploads/2014/11/How-to-use-Aspose-.NET-Gmail-Sync-for-Umbraco.png)

Вы успешно установили и добавили модуль Aspose.NET Gmail Sync для Umbraco на свою страницу. Для начала вам будут предложены три простых варианта

- Синхронизация с Gmail и Umbraco
- Синхронизация Умбрако с Gmail
- Настройки сервера Gmail

При первом нажатии на любую опцию вам будет предложено ввести данные сервера Gmail. Простая форма содержит все необходимые данные для подключения к вашей учетной записи Gmail, а затем эти данные будут зашифрованы и сохранены в базе данных для последующего использования.

![todo:image_alt_text](http://www.aspose.com/blogs/wp-content/uploads/2014/11/Gmail-server-details.png)

**Note:** Вы можете получить идентификатор клиента и секрет клиента своей учетной записи Google, выполнив действия, описанные на [Функции утилиты Gmail](/email/net/gmail-utility-features)

После завершения процесса синхронизации отображается краткая сводка по количеству перенесенных записей и список уже существующих и не импортированных записей.
## **Демонстрационное видео**
Пожалуйста, проверьте [видео](https://www.youtube.com/watch?v=A3RoXFpge9M) ниже, чтобы увидеть модуль в действии.
## **Поддерживайте, расширяйте и вносите свой вклад**
### **Support**
С самых первых дней существования Aspose мы знали, что просто предлагать нашим клиентам хорошие продукты будет недостаточно. Нам также необходимо было предоставлять хороший сервис. Мы сами являемся разработчиками и понимаем, как неприятно, когда технические проблемы или неполадки в программном обеспечении мешают вам делать то, что вам нужно. Мы здесь для того, чтобы решать проблемы, а не создавать их.

Вот почему мы предлагаем бесплатную поддержку. Любой, кто использует наш продукт, независимо от того, купил ли он его или использует оценку, заслуживает нашего полного внимания и уважения.

Вы можете регистрировать любые проблемы или предложения, связанные с модулем Aspose.NET Exchange/Google Sync для Umbraco, используя любую из следующих платформ

- [CodePlex ](https://asposeumbraco.codeplex.com/workitem/list/basic)
- [Github ](https://github.com/asposemarketplace/Aspose_for_Umbraco/issues)
- [Sourceforge ](https://sourceforge.net/p/asposeumbraco/tickets/?source=navbar)
- [Bitbucket ](https://bitbucket.org/asposemarketplace/aspose-for-umbraco/issues?status=new&status=open)
- [Сеть разработчиков Майкрософт — вопросы и ответы ](https://code.msdn.microsoft.com/Sync-Umbraco-Users-and-dc8086fa/view/Discussions#content)
### **Расширяйте и вносите**
Aspose.NET Exchange Sync для Umbraco и Aspose.NET Gmail Sync для Umbraco имеют открытый исходный код, и их исходный код доступен на основных сайтах социального программирования, перечисленных ниже. Разработчикам рекомендуется загрузить исходный код и расширить функциональность в соответствии со своими требованиями.
#### **Исходный код**
Вы можете получить последний исходный код в одном из следующих мест

- [CodePlex ](https://asposeumbraco.codeplex.com/SourceControl/latest)
- [Github ](https://github.com/asposemarketplace/Aspose_for_Umbraco)
- [Sourceforge ](https://sourceforge.net/p/asposeumbraco/code/ci/master/tree/)
- [Bitbucket ](https://bitbucket.org/asposemarketplace/aspose-for-umbraco/src)
#### **Как настроить исходный код**
Чтобы открыть и расширить исходный код, вам необходимо установить следующее

- Visual Studio 2010 или более поздняя версия

Для начала выполните следующие простые шаги

1. Скачайте или клонируйте исходный код.
1. Откройте Visual Studio 2010 и выберите **File** > **Открытый проект**
1. Перейдите к последнему исходному коду, который вы скачали и открыли **Aspose.GmailSync.sln**
