---
title: "Модуль синхронизации DNN Exchange"
url: /ru/net/dnn-exchange-sync-module/
weight: 10
type: docs
---

## **Введение**
DNN Exchange Sync — это модуль с открытым исходным кодом от [Aspose](http://www.aspose.com/), который связывает ваших пользователей DNN с контактами Microsoft Exchange Server без необходимости в дополнительном ПО. Он использует мощные возможности [Aspose.Email для .NET](http://www.aspose.com/.net/email-component.aspx), позволяя вам легко синхронизировать ваши контакты Exchange и пользователей DNN. Данные о контактах из сервера Exchange и профиля пользователя DNN умно сопоставляются, чтобы вся информация, связанная с пользователем DNN или контактом Exchange, была правильно перенесена из одной системы в другую.
### **Особенности модуля**
Эта первоначальная версия модуля обогащена следующими замечательными особенностями, чтобы сделать процесс синхронизации простым и удобным в использовании.

- Учетные данные сервера Exchange шифруются и сохраняются в базе данных, так что вам не нужно вводить их каждый раз при использовании этого модуля.
- Синхронизация всех или выбранных контактов Exchange с DNN и наоборот.
- Возможность выбрать одну или несколько ролей DNN при выполнении синхронизации Exchange с DNN.
- Перед миграцией проверяется наличие каждого контакта/пользователя в целевой системе, чтобы убедиться, что синхронизация не создает дублирующих записей.
- По завершении отображается краткое содержание процесса синхронизации.

|![todo:image_alt_text](http://www.aspose.com/blogs/wp-content/uploads/2014/07/DNN-Exchange-Sync-home.png)|
| :- |
|![todo:image_alt_text](http://www.aspose.com/blogs/wp-content/uploads/2014/07/Exchange-to-DNN-Sync.png)|
|![todo:image_alt_text](http://www.aspose.com/blogs/wp-content/uploads/2014/07/DNN-to-Exchange-Sync.png)|
## **Системные требования и поддерживаемые платформы**
### **Системные требования**
Для установки модуля Aspose .NET Exchange/Gmail Sync для DNN необходимо выполнить следующие требования:

- DNN 7.0 +

Пожалуйста, свяжитесь с нами, если вы хотите установить этот модуль на более ранние версии DNN.
### **Поддерживаемые платформы**
Aspose .NET Exchange/Gmail Sync для DNN в настоящее время поддерживает

- DNN 7.0 +

Пожалуйста, свяжитесь с нами, если вы хотите установить этот модуль на других версиях DNN.
## **Загрузка**
Вы можете скачать Aspose .NET Exchange Sync для DNN из одного из следующих мест

- [CodePlex ](https://asposednn.codeplex.com/releases)
- [DNN Store ](http://store.dnnsoftware.com/home/product-details/dnn-exchange-sync-2-way-link-between-dnn-and-microsoft-exchange-server)
- [Github ](https://github.com/asposemarketplace/Aspose_for_DNN/releases)
- [Sourceforge ](https://sourceforge.net/projects/asposednn/files/)
- [Bitbucket ](https://bitbucket.org/asposemarketplace/aspose-for-dnn/downloads)
## **Установка**
После загрузки следуйте этим шагам, чтобы установить модуль на ваш сайт DNN:

1. Войдите на свой сайт как Хост или другой аккаунт уровня Суперпользователя.
1. Перейдите в меню **Хост** и выберите **Расширения**.
1. Нажмите на **Мастер установки расширений**.
1. Как указано, выберите местоположение загруженного ZIP-файла, выберите его и нажмите **Открыть**.
1. Нажмите **Далее**, примите лицензию и продолжите установку.
1. По завершении нажмите **Вернуться**.

Пожалуйста, посмотрите [это видео установки модуля](http://www.dnnsoftware.com/community/learn/video-library/view-video/video/542/view/details/how-to-install-a-module-in-dotnetnuke-7) от DNN для получения дополнительных деталей.

**Примечание:** Если вы получили ошибку при загрузке модуля, это связано с ограничением maxRequestLength в web.config вашей установки DNN. Откройте web.config и обновите maxRequestLength до 20MB, установив **maxRequestLength=”20480″**, и попробуйте загрузить модуль снова.
## **Использование**
После установки модуля DNN Exchange Sync действительно просто начать его использовать на вашем сайте. Пожалуйста, следуйте этим простым шагам, чтобы начать:

1. Убедитесь, что вы вошли в DNN как Хост или аккаунт уровня Админ.
1. Перейдите на страницу, где вы хотите добавить модуль DNN Exchange Sync.
1. Выберите **Модули**, затем **Добавить новый модуль** на верхней ленте.

![todo:image_alt_text](http://www.aspose.com/blogs/wp-content/uploads/2014/07/DNN-Exchange-Sync-add-module-to-page.png)

1. Из списка выберите **Aspose** **DNN Exchange Sync** и перетащите его в место на странице по вашему выбору.

Вы успешно добавили модуль DNN Exchange Sync на свою страницу. Вам будут предложены 3 простых варианта для начала:

- Синхронизация Exchange с DNN
- Синхронизация DNN с Exchange
- Настройки Exchange

При первом нажатии на любой из вариантов вас попросят ввести данные сервера Microsoft Exchange. Простая форма собирает все необходимые данные для подключения к вашей учетной записи Exchange, а затем эти данные будут зашифрованы и сохранены в базе данных для последующего использования.

![todo:image_alt_text](http://www.aspose.com/blogs/wp-content/uploads/2014/07/DNN-Exchange-Sync-Exchange-Server-Details.png)

После завершения процесса синхронизации будет показано краткое резюме количества мигрированных записей и список записей, которые уже существовали и не были импортированы.
## **Видеодемонстрация**
Пожалуйста, посмотрите [видео](https://www.youtube.com/watch?v=LqEiYz287GA) ниже, чтобы увидеть модуль в действии.
## **Поддержка, расширение и вклад**
### **Поддержка**
С самого начала Aspose мы знали, что просто предоставление нашим клиентам качественных продуктов будет недостаточно. Нам также нужно было предоставить хороший сервис. Мы сами разработчики и понимаем, как это frustrates, когда техническая проблема или ошибка в программном обеспечении мешает вам делать то, что нужно. Мы здесь, чтобы решать проблемы, а не создавать их.

Вот почему мы предлагаем бесплатную поддержку. Каждый, кто использует наш продукт, будь то он купил его или использует в рамках оценки, заслуживает нашего полного внимания и уважения.

Вы можете зарегистрировать любые проблемы или предложения, связанные с модулем Aspose .NET Exchange/Gmail Sync для DNN, используя любые из следующих платформ:

- [CodePlex ](https://asposednn.codeplex.com/workitem/list/basic)
- [Github ](https://github.com/asposemarketplace/Aspose_for_DNN/issues)
- [Sourceforge ](https://sourceforge.net/p/asposednn/tickets/)
- [Bitbucket ](https://bitbucket.org/asposemarketplace/aspose-for-dnn/issues?status=new&status=open)
- [DNN Store ](http://store.dnnsoftware.com/help-center/help-desk/ticket-entry/packageid/33341)
- [Microsoft Developer Network - Вопросы и ответы ](https://code.msdn.microsoft.com/DNN-Exchange-Sync-2-Way-fab0339b/view/Discussions#content)
### **Расширение и вклад**
Aspose .NET Exchange Sync для DNN и Aspose .NET Gmail Sync для DNN имеют открытый исходный код, и их исходный код доступен на основных сайтах социального программирования, перечисленных ниже. Разработчики призываются загружать исходный код и расширять функциональность в соответствии со своими требованиями.
#### **Исходный код**
Вы можете получить последний исходный код из одного из следующих мест:

- [CodePlex ](https://asposednn.codeplex.com/SourceControl/latest)
- [Github ](https://github.com/asposemarketplace/Aspose_for_DNN)
- [Sourceforge ](https://sourceforge.net/p/asposednn/code/ci/master/tree/)
- [Bitbucket ](https://bitbucket.org/asposemarketplace/aspose-for-dnn/src)
#### **Как настроить исходный код**
Вам необходимо установить следующее, чтобы открыть и расширить исходный код:

- Visual Studio 2010 или выше
- [Шаблон разработки DNN](https://downloads.aspose.com/total/net)

Пожалуйста, следуйте этим простым шагам для начала:

1. Скачайте/клонируйте исходный код.
1. Откройте Visual Studio 2010 и выберите **Файл** > **Открыть проект**.
1. Перейдите к последнему загруженному исходному коду и откройте **Aspose.DNN.ExchangeSync.csproj**.