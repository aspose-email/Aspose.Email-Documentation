---
title: "Модуль синхронизации DNN Exchange"
url: /ru/net/dnn-exchange-sync-module/
weight: 10
type: docs
---


## **Introduction**
Синхронизация обмена DNN — это модуль с открытым исходным кодом от [Aspose](http://www.aspose.com/) который связывает ваших пользователей DNN с контактами Microsoft Exchange Server без использования какого-либо другого программного обеспечения. Он использует мощные функции [Электронная почта Aspose.NET](http://www.aspose.com/.net/email-component.aspx) чтобы вы могли легко синхронизировать контакты Exchange и пользователей DNN. Контактные данные сервера Exchange и профиль пользователя DNN тщательно сопоставлены, поэтому вся информация, связанная с пользователем DNN или контактом Exchange, правильно переносится из одной системы в другую.
### **Характеристики модуля**
Эта начальная версия модуля обогащена следующими интересными функциями, которые делают процесс синхронизации простым и удобным в использовании.

- Учетные данные сервера Exchange зашифрованы и сохраняются в базе данных, поэтому их не нужно вводить каждый раз при использовании этого модуля.
- Синхронизируйте все или выбранные контакты Exchange с DNN и наоборот.
- Возможность выбора одной или нескольких ролей DNN при синхронизации Exchange с DNN.
- Перед переносом проверяется наличие каждого контакта/пользователя в целевой системе, чтобы убедиться, что синхронизация не создает дубликатов записей.
- По завершении отображается краткое описание процесса синхронизации.

|![todo:image_alt_text](http://www.aspose.com/blogs/wp-content/uploads/2014/07/DNN-Exchange-Sync-home.png)|
|: - |
|![todo:image_alt_text](http://www.aspose.com/blogs/wp-content/uploads/2014/07/Exchange-to-DNN-Sync.png)|
|![todo:image_alt_text](http://www.aspose.com/blogs/wp-content/uploads/2014/07/DNN-to-Exchange-Sync.png)|
## **Системные требования и поддерживаемые платформы**
### **Системные требования**
Чтобы настроить модуль Aspose.NET Exchange/Gmail Sync для DNN, вам необходимо выполнить следующие требования:

- ДНН 7.0 +

Пожалуйста, свяжитесь с нами по адресу, если вы хотите установить этот модуль на более старые версии DNN.
### **Поддерживаемые платформы**
Модуль синхронизации Aspose.NET Exchange/Gmail для DNN в настоящее время поддерживает

- ДНН 7.0 +

Пожалуйста, свяжитесь с нами, если вы хотите установить этот модуль на другие версии DNN.
## **Downloading**
Вы можете загрузить Aspose.NET Exchange Sync для DNN в одном из следующих мест

- [CodePlex ](https://asposednn.codeplex.com/releases)
- [Магазин DNN ](http://store.dnnsoftware.com/home/product-details/dnn-exchange-sync-2-way-link-between-dnn-and-microsoft-exchange-server)
- [Github ](https://github.com/asposemarketplace/Aspose_for_DNN/releases)
- [Sourceforge ](https://sourceforge.net/projects/asposednn/files/)
- [Bitbucket ](https://bitbucket.org/asposemarketplace/aspose-for-dnn/downloads)
## **Installing**
После загрузки выполните следующие действия, чтобы установить модуль на свой веб-сайт DNN:

1. Войдите на свой сайт в качестве хоста или другой учетной записи уровня Supersuser.
1. Перейдите к **Host** меню и выберите **Extensions**.
1. Нажмите на **Мастер установки расширений**.
1. В соответствии с указаниями найдите загруженный ZIP-файл, выберите его и нажмите **Open**.
1. Click **Next**, примите лицензию и продолжите установку.
1. По завершении нажмите **Return**.

Пожалуйста, проверьте [видео по установке этого модуля](http://www.dnnsoftware.com/community/learn/video-library/view-video/video/542/view/details/how-to-install-a-module-in-dotnetnuke-7) от DNN для получения более подробной информации.

**Note:** Если при загрузке модуля вы получаете сообщение об ошибке, это связано с ограничением maxRequestLength в файле web.config вашей установки DNN. Откройте web.config и обновите значение MaxRequestLength до 20 МБ, установив **maxRequestLength=”20480″** и попробуйте загрузить модуль снова.
## **Using**
После установки модуля Синхронизация обмена DNN начать использовать его на своем веб-сайте очень просто. Для начала выполните следующие простые шаги

1. Убедитесь, что вы вошли в DNN как учетную запись уровня хоста или администратора.
1. Перейдите на страницу, где вы хотите добавить модуль синхронизации DNN Exchange.
1. Select **Modules** за которым следует **Добавить новый модуль** из верхней ленты.

![todo:image_alt_text](http://www.aspose.com/blogs/wp-content/uploads/2014/07/DNN-Exchange-Sync-add-module-to-page.png)

1. Из списка выберите, **Aspose** **Синхронизация обмена DNN** и перетащите его в нужное место на странице.

Вы успешно добавили модуль синхронизации DNN Exchange на свою страницу. Для начала вам будут предложены 3 простых варианта

- Синхронизация с обменом на DNN
- Синхронизация DNN с Exchange
- Настройки биржи

При первом выборе любой опции вас попросят ввести данные Microsoft Exchange Server. В простой форме указываются все необходимые данные для подключения к учетной записи Exchange, а затем эти данные будут зашифрованы и сохранены в базе данных для последующего использования.

![todo:image_alt_text](http://www.aspose.com/blogs/wp-content/uploads/2014/07/DNN-Exchange-Sync-Exchange-Server-Details.png)


После завершения процесса синхронизации отображается краткая сводка по количеству перенесенных записей и список уже существующих и не импортированных записей.
## **Демонстрационное видео**
Пожалуйста, проверьте [видео](https://www.youtube.com/watch?v=LqEiYz287GA) ниже, чтобы увидеть модуль в действии.
## **Поддерживайте, расширяйте и вносите свой вклад**
### **Support**
С самых первых дней существования Aspose мы знали, что просто предлагать нашим клиентам хорошие продукты будет недостаточно. Нам также необходимо было предоставлять хороший сервис. Мы сами являемся разработчиками и понимаем, как неприятно, когда технические проблемы или неполадки в программном обеспечении мешают вам делать то, что вам нужно. Мы здесь для того, чтобы решать проблемы, а не создавать их.

Вот почему мы предлагаем бесплатную поддержку. Любой, кто использует наш продукт, независимо от того, купил ли он его или использует оценку, заслуживает нашего полного внимания и уважения.

Вы можете регистрировать любые проблемы или предложения, связанные с модулем Aspose.NET Exchange/Gmail Sync for DNN, используя любую из следующих платформ

- [CodePlex ](https://asposednn.codeplex.com/workitem/list/basic)
- [Github ](https://github.com/asposemarketplace/Aspose_for_DNN/issues)
- [Sourceforge ](https://sourceforge.net/p/asposednn/tickets/)
- [Bitbucket ](https://bitbucket.org/asposemarketplace/aspose-for-dnn/issues?status=new&status=open)
- [Магазин DNN ](http://store.dnnsoftware.com/help-center/help-desk/ticket-entry/packageid/33341)
- [Сеть разработчиков Майкрософт — вопросы и ответы ](https://code.msdn.microsoft.com/DNN-Exchange-Sync-2-Way-fab0339b/view/Discussions#content)
### **Расширяйте и вносите**
Aspose.NET Exchange Sync для DNN и Aspose.NET Gmail Sync для DNN имеют открытый исходный код, и их исходный код доступен на основных сайтах социального программирования, перечисленных ниже. Разработчикам рекомендуется загрузить исходный код и расширить функциональность в соответствии со своими требованиями.
#### **Исходный код**
Вы можете получить последний исходный код в одном из следующих мест

- [CodePlex ](https://asposednn.codeplex.com/SourceControl/latest)
- [Github ](https://github.com/asposemarketplace/Aspose_for_DNN)
- [Sourceforge ](https://sourceforge.net/p/asposednn/code/ci/master/tree/)
- [Bitbucket ](https://bitbucket.org/asposemarketplace/aspose-for-dnn/src)
#### **Как настроить исходный код**
Чтобы открыть и расширить исходный код, вам необходимо установить следующее

- Visual Studio 2010 или более поздняя версия
- [Шаблон для разработки DNN] (https://downloads.aspose.com/total/net

Для начала выполните следующие простые шаги

1. Скачайте или клонируйте исходный код.
1. Откройте Visual Studio 2010 и выберите **File** > **Открытый проект**
1. Перейдите к последнему исходному коду, который вы скачали и открыли **Aspose.DNN.ExchangeSync.csproj**
