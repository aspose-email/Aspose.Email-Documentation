---
title: "Модуль синхронизации Google для Umbraco"
url: /ru/net/umbraco-google-sync-module/
weight: 20
type: docs
---

## **Введение**
Aspose .NET Gmail Sync для Umbraco — это модуль с открытым исходным кодом от [Aspose](http://www.aspose.com/), который связывает ваших пользователей/участников Umbraco с контактами Google или Gmail без необходимости установки какого-либо другого ПО. Он использует мощные функции [Aspose.Email для .NET](http://www.aspose.com/.net/email-component.aspx), чтобы вы могли легко синхронизировать свои контакты Gmail и пользователей/участников Umbraco.
### **Особенности модуля**
Эта начальная версия модуля обогащена следующими функциями, чтобы сделать процесс синхронизации эффективным, простым и удобным в использовании.

- Учётные данные сервера Google/Gmail зашифрованы и сохранены в базе данных, так что вам не нужно вводить их каждый раз при использовании модуля.
- Синхронизация всех или выбранных контактов Gmail с Umbraco и наоборот.
- Возможность выбрать один или несколько типов пользователей/участников Umbraco при выполнении синхронизации Gmail с Umbraco.
- Проверка существования каждого контакта/пользователя в целевой системе перед миграцией, чтобы убедиться, что синхронизация не создает дублирующих записей.
- Контакты, перенесенные в Gmail, помещаются в группу Другие контакты, чтобы вы могли проверить и переместить только нужные контакты в Мои контакты.
- Краткое резюме процесса синхронизации показывается по завершении.

![todo:image_alt_text](http://www.aspose.com/blogs/wp-content/uploads/2014/11/Aspose-.NET-Gmail-Sync-for-Umbraco.png)

![todo:image_alt_text](http://www.aspose.com/blogs/wp-content/uploads/2014/11/Gmail-to-Umbraco-Sync.png)

![todo:image_alt_text](http://www.aspose.com/blogs/wp-content/uploads/2014/11/Umbraco-to-Gmail-Sync.png)
## **Системные требования и поддерживаемые платформы**
### **Системные требования**
Чтобы настроить модуль Aspose .NET Exchange/Google Sync для Umbraco, необходимо, чтобы были выполнены следующие требования:

- Umbraco 6.0 +

Пожалуйста, не стесняйтесь обращаться к нам, если вы хотите установить этот модуль на более старую версию Umbraco.
### **Поддерживаемые платформы**
Модуль поддерживается на всех версиях

- Umbraco, работающем на ASP.NET 4.0
## **Скачивание**
Вы можете скачать Aspose .NET Google Sync для Umbraco из одного из следующих мест

- [CodePlex](https://asposeumbraco.codeplex.com/releases)
- [Github](https://github.com/asposemarketplace/Aspose_for_Umbraco/releases)
- [Sourceforge](https://sourceforge.net/projects/asposeumbraco/files/)
- [Bitbucket](https://bitbucket.org/asposemarketplace/aspose-for-umbraco/downloads)
- [Umbraco](https://our.umbraco.org/projects/website-utilities/sync-umbraco-users-and-members-with-google-contacts-using-aspose-net-gmail-sync-for-umbraco)
## **Установка**
После загрузки, пожалуйста, выполните следующие шаги, чтобы установить модуль на вашем сайте Umbraco:

1. Войдите в раздел **Разработчик** Umbraco, например <http://www.myblog.com/umbraco/>
1. В дереве раскройте папку **Пакеты**.
1. Отсюда есть два способа установить пакет: выберите **Установить локальный пакет** или просмотрите **Репозиторий пакетов Umbraco.**
1. Если вы устанавливаете **локальный пакет**, не распаковывайте пакет, а загрузите zip в Umbraco.
1. Следуйте инструкциям на экране.
## **Использование**
После установки модуля Aspose .NET Gmail Sync для Umbraco очень просто начать использовать его на вашем сайте. Пожалуйста, следуйте этим простым шагам, чтобы начать

1. Убедитесь, что вы вошли в раздел **Разработчик** Umbraco, например <http://www.myblog.com/umbraco/>
1. Нажмите **Настройки** в списке секций в нижнем левом углу экрана.
1. Раскройте узел **Шаблоны** и выберите шаблон, к которому хотите добавить функцию синхронизации Gmail, например Textpage.
1. Выберите позицию в выбранном шаблоне, куда хотите добавить кнопку экспорта. Обычно вы хотите добавить ее в верхнем правом углу страницы или внизу страницы.
1. Нажмите **Вставить макрос** на верхней панели.
1. В разделе **Выберите макрос** выберите недавно установленный макрос Aspose .NET Gmail Sync для Umbraco и нажмите **ОК**.

Пожалуйста, посмотрите скриншот ниже для деталей.

![todo:image_alt_text](http://www.aspose.com/blogs/wp-content/uploads/2014/11/How-to-use-Aspose-.NET-Gmail-Sync-for-Umbraco.png)

Вы успешно установили и добавили модуль Aspose .NET Gmail Sync для Umbraco на вашу страницу. Вам будут предложены три простых варианта, чтобы начать

- Синхронизация Gmail с Umbraco
- Синхронизация Umbraco с Gmail
- Настройки сервера Gmail

Вас попросят ввести данные сервера Gmail при нажатии на любой из вариантов в первый раз. Простая форма требует все необходимые данные для подключения к вашему аккаунту Gmail, а затем эти данные будут зашифрованы и сохранены в базе данных для дальнейшего использования.

![todo:image_alt_text](http://www.aspose.com/blogs/wp-content/uploads/2014/11/Gmail-server-details.png)

**Примечание:** Вы можете получить идентификатор клиента и секрет клиента вашей учетной записи Google, используя шаги, описанные в [Функциях утилиты Gmail](/email/net/gmail-utility-features)

Как только процесс синхронизации завершится, будет показано краткое резюме количества перенесенных записей и список записей, которые уже существовали и не были импортированы.
## **Видеодемонстрация**
Пожалуйста, посмотрите [видео](https://www.youtube.com/watch?v=A3RoXFpge9M) ниже, чтобы увидеть модуль в действии.
## **Поддержка, расширение и вклад**
### **Поддержка**
С первых дней существования Aspose мы знали, что просто предоставление нашим клиентам хороших продуктов будет недостаточно. Мы также должны предоставить хорошее обслуживание. Мы сами разработчики и понимаем, как это расстраивает, когда техническая проблема или особенность программного обеспечения мешает вам делать то, что вам нужно. Мы здесь, чтобы решать проблемы, а не создавать их.

Вот почему мы предлагаем бесплатную поддержку. Каждый, кто использует наш продукт, независимо от того, купил ли он его или использует оценочную версию, заслуживает нашего полного внимания и уважения.

Вы можете зарегистрировать любые проблемы или предложения, связанные с модулем Aspose .NET Exchange/Google Sync для Umbraco, с помощью любой из следующих платформ

- [CodePlex](https://asposeumbraco.codeplex.com/workitem/list/basic)
- [Github](https://github.com/asposemarketplace/Aspose_for_Umbraco/issues)
- [Sourceforge](https://sourceforge.net/p/asposeumbraco/tickets/?source=navbar)
- [Bitbucket](https://bitbucket.org/asposemarketplace/aspose-for-umbraco/issues?status=new&status=open)
- [Microsoft Developer Network - Вопросы и ответы](https://code.msdn.microsoft.com/Sync-Umbraco-Users-and-dc8086fa/view/Discussions#content)
### **Расширение и вклад**
Aspose .NET Exchange Sync для Umbraco и Aspose .NET Gmail Sync для Umbraco являются открытым исходным кодом, и их исходный код доступен на основных социальных сайтах разработки, перечисленных ниже. Разработчики поощряются к загрузке исходного кода и расширению функциональности в соответствии с собственными требованиями.
#### **Исходный код**
Вы можете получить последний исходный код из одного из следующих мест

- [CodePlex](https://asposeumbraco.codeplex.com/SourceControl/latest)
- [Github](https://github.com/asposemarketplace/Aspose_for_Umbraco)
- [Sourceforge](https://sourceforge.net/p/asposeumbraco/code/ci/master/tree/)
- [Bitbucket](https://bitbucket.org/asposemarketplace/aspose-for-umbraco/src)
#### **Как настроить исходный код**
Вам необходимо установить следующее, чтобы открыть и расширить исходный код

- Visual Studio 2010 или выше

Пожалуйста, следуйте этим простым шагам, чтобы начать

1. Загрузите/склонируйте исходный код.
1. Откройте Visual Studio 2010 и выберите **Файл** > **Открыть проект**
1. Перейдите к последнему загруженному исходному коду и откройте **Aspose.GmailSync.sln**