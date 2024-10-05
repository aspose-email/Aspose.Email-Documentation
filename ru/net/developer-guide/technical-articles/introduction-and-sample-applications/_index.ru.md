---
title: "Введение и пример приложений"
url: /ru/net/introduction-and-sample-applications/
weight: 260
type: docs
---


## **Сценарии использования Aspose.Email.Mail**
Эта статья предлагает ряд возможных применений Aspose.Email для .NET, с особым вниманием к возможностям программирования электронной почты компонента.
### **Программное обеспечение для рассылки новостей**
API [Aspose.Email.Mail](https://apireference.aspose.com/email/net/aspose.email) может быть использован для создания надежного приложения для рассылки новостей. С помощью поддержки Aspose.Email для добавления встроенных объектов (таких как картинки, звуки и т. д.) можно создавать насыщенные HTML-рассылки с изображениями (и другими встроенными объектами). Используя функцию массовой рассылки API Aspose.Email.Mail, также можно отправлять огромные массовые электронные письма в ограниченные сроки. Aspose.Email.Mail также предоставляет функцию слияния почты на основе шаблонов, которая может быть использована для создания шаблона рассылки новостей. Шаблон рассылки может быть использован для выполнения слияния почты для отправки массовых новостей. Существует множество других возможных задач, которые Aspose.Email.Mail может выполнять в приложении для email-маркетинга.
### **Другие маркетинговые инструменты**
Подобно приложениям для рассылки новостей, можно создать много других типов программного обеспечения, используя Aspose.Email.Mail. Используйте его для создания email-маркетинга, массовых рассылок и e-кампаний, и многое другое.
### **Бизнес-приложения**
Aspose.Email.Mail может использоваться практически во всех видах бизнес-приложений для выполнения служебных задач:

- Уведомления по электронной почте: Отправка уведомлений по электронной почте для информирования пользователей о событиях.
- Запросы на встречи: Отправка бизнес-запросов на встречи с использованием поддержки iCalendar в Aspose.Email.Mail.
- Запланированные отчеты по электронной почте: Отчеты являются неотъемлемой частью большинства бизнес-приложений. Многие бизнес-отчеты генерируются на интервалах. Используйте Aspose.Email.Mail для отправки запланированных отчетов.
### **Email-клиенты**
Aspose.Email.Mail также может быть использован в email-клиентах для отправки обычных писем. Он поддерживает вложения, встроенные объекты, события iCalendar, слияние почты, отправку массовых писем и так далее, поэтому Aspose.Email.Mail является лучшим выбором для создания приложений email-клиента для Windows или веба.
## **Пример приложения Aspose.Email.Mail**
Чтобы продемонстрировать, как использовать Aspose.Email.Mail, мы создадим приложение под названием 'Моя первая почта', которое демонстрирует, как создать электронное сообщение с помощью класса [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) и затем отправить его с использованием класса SmtpClient.
### **Mail: Шаги создания приложения**
Пожалуйста, следуйте приведенным ниже шагам для создания приложения 'Моя первая почта' с использованием Aspose.Email.

1. Откройте Visual Studio.
1. В меню **Файл** выберите **Создать**, затем **Проект**. (Выберите создание приложения Windows на C# или VB.NET).
1. Если у вас есть лицензия, примените ее для использования полной версии Aspose.Email.
1. Импортируйте сборку Aspose.Email DLL в приложение, щелкнув правой кнопкой мыши на **Ссылки** в обозревателе решений.
1. Разработайте ваше Windows-приложение: создайте интерфейс, который принимает три поля: **От**, **Кому** и **Сообщение**.
1. Дважды щелкните кнопку **Отправить** в дизайнере и напишите свой код в редакторе.
1. Создайте экземпляр класса MailMessage и используйте его свойства для создания электронного сообщения. (Экземпляры класса MailMessage используются для построения электронных сообщений, которые передаются на SMTP-сервер для доставки с использованием класса SmtpClient).
1. Создайте экземпляр класса SmtpClient и используйте его свойства для отправки электронного сообщения.
1. Протестируйте ваше Windows-приложение, нажав F5.
1. Введите адреса в поля **От** и **Кому**.
1. Введите сообщение в поле **Текст сообщения**.
1. Щелкните **Отправить**.

Приведенные выше шаги описаны ниже дважды щелкнув кнопку **Отправить** в дизайнере и добавив код ниже:



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AsposeEmailMailSampleApp-AsposeEmailMail.cs" >}}



При подключении к серверу с поддержкой SSL необходимо установить следующие свойства объекта SMTPClient:



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AsposeEmailMailSampleApp-SSLEnabledSMTP.cs" >}}
### **Заключение**
[Aspose.Email.Mail](https://apireference.aspose.com/email/net/aspose.email) является очень мощным компонентом, с помощью которого разработчики могут выполнять почти все задачи, связанные с электронной почтой, такие как отправка многопоточных массовых отправок, использование слияния почты, добавление вложений, встраивание изображений и звуков в электронные сообщения, добавление событий iCalendar в электронные письма, получение электронных писем и многое другое.
## **Aspose.Email.Pop3**
[Aspose.Email.Pop3](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client) реализует Протокол почтового отделения версии 3 (POP3) на платформе .NET. Он позволяет разработчикам .NET добавлять функции запросов и получения электронной почты в свои приложения .NET, не углубляясь в детали протокола и сложности программирования электронной почты и сети. Aspose.Email.Pop3 поддерживает все команды, определенные в стандартном протоколе POP3, и предоставляет удобные интерфейсы вместе с компактной и интуитивно понятной объектной моделью. Это значительно сокращает обычную кривую обучения для разработчиков .NET.
### **Pop3: Основные функции**
В рамках Aspose.Email, Aspose.Email.Pop3 был разработан специально для .NET и написан на управляемом C# коде. Он позволяет вам:

- Подключаться и входить на POP3 серверы.
- Поддерживать APOP.
- Запрашивать сообщения.
- Получать сообщения.
- Полностью поддерживать стиль асинхронного программирования.
- Поддерживать SSL.
### **Сценарии использования Aspose.Email.Pop3**
Aspose.Email.Pop3 может быть использован разработчиками в самых разных сценариях. Здесь мы делимся парой.
### **Автоматизация бизнес-электронной почты**
Aspose.Email.Pop3 можно использовать для запроса почтовых ящиков электронной почты и получения сообщений электронной почты. Он хорошо работает с компонентом отправки электронной почты Aspose.Email.Mail. Aspose.Email полностью поддерживает автоматизацию электронной почты. Отправьте сообщения по электронной почте с помощью Aspose.Email.Mail и получите сообщения с помощью Aspose.Email.Pop3. Загруженные сообщения электронной почты затем могут быть обработаны Aspose.Email.Mime.
### **Email-клиенты**
Aspose.Email.Pop3 можно использовать в приложениях email-клиентов для получения электронной почты.
### **Pop3: Пример приложения**
Здесь мы продемонстрируем, как использовать [Aspose.Email.Pop3](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client). Этот класс имеет много функций, но мы сосредоточимся на том, как подключиться к POP3 серверу и получить сообщения. Пример показывает, как создать приложение в Visual Studio, а также примеры кода, которые заставляют приложение работать. Следуйте приведенным ниже шагам, чтобы создать пример приложения с использованием Aspose.Email.Pop3.

1. Откройте Visual Studio.
1. В меню **Файл** выберите **Создать**, затем **Проект**.
1. Выберите Windows-приложение на C# или VB.NET.
1. Импортируйте Aspose.Email.dll в приложение, щелкнув правой кнопкой мыши на **Ссылки** в обозревателе решений.
1. Теперь разработайте Windows-приложение, как показано ниже.
1. Создайте экземпляр Pop3Client.
1. Установите имя хоста POP3, логин и пароль в этом экземпляре.
1. Вызовите функции Connect() и Login() класса Pop3Client.
1. Создайте экземпляр MailMessage и получите первое сообщение в своей учетной записи, вызвав функцию FetchMessage(). Это извлекает первое сообщение из вашего почтового ящика в экземпляр MailMessage.
1. Используйте свойства From, Subject и HtmlBody экземпляра MailMessage, чтобы увидеть отправителя, тему и содержание сообщения.

Приведенные выше шаги представлены в примерах кода ниже. Используйте следующий код под любой кнопкой или в событии OnLoad формы.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AsposeEmailPop3SampleApp-AsposeEmailPop3.cs" >}}



Для серверов с поддержкой SSL необходимо изменить следующие свойства объекта Pop3Client:



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AsposeEmailPop3SampleApp-SSLEnabledServer.cs" >}}
## **Aspose.Email.Imap**
[Aspose.Email.Imap](https://apireference.aspose.com/email/net/aspose.email.clients.imap) реализует Протокол доступа к интернет-сообщениям (IMAP) на платформах .NET. Aspose.Email.Imap позволяет разработчикам .NET быстро добавлять возможности IMAP в свои приложения .NET, не вникая в детали протокола. Компонент поддерживает извлечение и загрузку сообщений, проверку статуса новых/прочитанных/непрочитанных сообщений и так далее.
### **Imap: Основные функции**
Aspose.Email.Imap позволяет вам:

- Извлекать сообщения электронной почты.
- Загружать сообщения электронной почты.
- Перечислять сообщения электронной почты в разных папках.
- Проверять статус сообщений электронной почты.
- Работать с MailMessage.
- Работать с поддержкой SSL.
### **Использование Aspose.Email.Imap**
Aspose.Email.Imap реализует Протокол доступа к интернет-сообщениям на платформах .NET. С его помощью разработчики могут легко запрашивать и управлять электронными письмами на IMAP сервере, а также создавать, удалять или переименовывать папки электронной почты. Используя Aspose.Email.Imap, разработчики могут воспользоваться преимуществами протокола IMAP с удобными API. Они могут получать доступ к электронной почте с любого ПК, так как письма остаются сохраненными на сервере. Используя Aspose.Email.Imap, разработчики могут создавать веб- или настольные приложения, которые получают и обрабатывают электронные письма с IMAP серверов. Aspose реализовал протокол IMAP в соответствии с интернет-аутентификацией и стандартами RFC. Поэтому Aspose.Email.Imap является безопасной и полнофункциональной реализацией IMAP протокола с понятной объектной моделью и интерфейсами.
### **Imap: Пример приложения**
В этой статье объясняется, как использовать [Aspose.Email.Imap](https://apireference.aspose.com/email/net/aspose.email.clients.imap). Мы создаем небольшое приложение, которое получает количество сообщений электронной почты в вашем IMAP-аккаунте. Следуйте приведенным ниже шагам, чтобы создать образец приложения с использованием Aspose.Email.Imap.

1. Откройте Visual Studio.
1. В меню **Файл** выберите **Создать**, затем **Проект**.
1. Выберите Windows-приложение на C# или VB.NET.
1. Импортируйте Aspose.Email.dll в это приложение, щелкнув правой кнопкой мыши на **Ссылки** в обозревателе решений.
1. Создайте экземпляр ImapClient, передав имя IMAP сервера, логин и пароль.
1. Вызовите функцию Connect() экземпляра ImapClient, чтобы подключиться к серверу.
1. Вызовите функцию SelectFolder() экземпляра ImapClient, чтобы выбрать папку, в которой вы хотите подсчитать количество сообщений.
1. Теперь вызовите свойство CurrentFolder.TotalMessageCount экземпляра ImapClient, чтобы получить количество сообщений электронной почты.
### **Imap: Примеры кода**
Примеры кода ниже идут за кнопкой или в событии OnLoad на форме. Они показывают, как реализовать указанные выше шаги с использованием Aspose.Email.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AsposeEmailIMAPSampleApp-AsposeEmailIMAP.cs" >}}



Для почтовых серверов с поддержкой SSL установите следующие свойства объекта ImapClient:



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AsposeEmailIMAPSampleApp-SSLEnabledServer.cs" >}}
## **Aspose.Email.Exchange**
[Aspose.Email.Exchange](https://apireference.aspose.com/email/net/aspose.email.clients.exchange/index) позволяет разработчикам управлять электронной почтой на сервере Microsoft Exchange. Используя этот компонент, вы можете подключаться, перечислять сообщения и загружать электронные письма из почтового ящика exchange-сервера, не углубляясь в детали протоколов. Компонент поддерживает перечисление сообщений, отправку электронной почты, загрузку сообщений и сохранение в формате eml или msg на вашем локальном диске и т. д.
### **Exchange: Основные функции**
Aspose.Email.Exchange позволяет вам:

- Подключаться к серверам Microsoft Exchange.
- Перечислять сообщения электронной почты в почтовых ящиках Exchange.
- Перечислять сообщения электронной почты из разных папок, например, Входящие, Отправленные, Удаленные или Черновики.
- Удалять сообщения в любой папке на серверах Exchange.
### **Использование Aspose.Email.Exchange**
С помощью Aspose.Email.Exchange разработчики могут получать доступ к почтовым ящикам Exchange Server из своих приложений .NET. Он предоставляет простой в использовании API для управления электронной почтой на серверах Exchange. Разработчики могут создавать консольные, настольные или веб-приложения, которые управляют электронной почтой в почтовых ящиках Exchange.
## **Пример приложения Aspose.Email.Exchange**
Эта статья демонстрирует, как использовать [Aspose.Email.Exchange](https://apireference.aspose.com/email/net/aspose.email.clients.exchange/index). Мы создаем простое настольное приложение, которое подключается к почтовому ящику Exchange Server, получает список сообщений в папке Входящие и отображает их на окне формы.
### **Exchange: Шаги создания образца приложения**
1. Откройте Microsoft Visual Studio.
1. Создайте новый проект. (Выберите язык на ваш выбор: C# или VB.NET)
1. Добавьте ссылку на Aspose.Email.dll в ваш проект, щелкнув правой кнопкой мыши на проекте и выбрав **Добавить ссылку** из меню.
1. Разработайте Windows-форму, как показано ниже:

Чтобы успешно запустить приложение, вам нужны правильные учетные данные для доступа к серверу Exchange. Здесь мы получаем информацию об учетных данных - URI сервера Exchange, имя пользователя, пароль и домен - из формы Windows. Это очень простой пример, поэтому свойства сообщений - тема, от и к - просто отображаются в списке.
### **Exchange: Примеры кода**
Добавьте следующий код в обработчик события нажатия кнопки **Список сообщений**.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AsposeEmailExchangeSampleApp-AsposeEmailExchange.cs" >}}
### **Exchange: Вывод**
Этот скриншот показывает сообщения, извлеченные из сервера Exchange. Метод ListMessages() возвращает основную информацию, такую как тема, от, к и ID сообщения. Чтобы получить полное сообщение, вызовите метод ExchangeClient.SaveMessage(). (Использование метода ExchangeClient.SaveMessage() описано в статье [Сохранение сообщений из почтового ящика Exchange в формате EML и MSG](/email/net/working-with-exchange-mailbox-and-messages/#saving-messages).)

|![todo:image_alt_text](introduction-and-sample-applications_1.png)|
| :- |
## **Aspose.Email.Mime**
Расширения многоцелевая Интернет-почты (MIME) - это интернет-стандарт, который расширяет формат электронной почты для поддержки текста в кодировках, отличных от US-ASCII, не текстовых вложений, многочастных тел сообщений и информации заголовков в кодировках, отличных от ASCII. Aspose.Email.Mime реализует протокол MIMI на платформах .NET. Он действует как переводчик, так как может читать электронную почту из файла (.eml и т. д.) или из памяти (строка). Затем он разбирает файл или строку электронной почты на значимые части. Если вы хотите просмотреть файл электронной почты, не вникая в детали протокола MIME, например, чтобы извлечь вложение из электронной почты, используйте Aspose.Email.Mime.
### **Основные функции**
Aspose.Email.Mime прекрасно работает с Aspose.Email.Pop3 и Aspose.Email.Mail.

- [Aspose.Email.Pop3](https://apireference.aspose.com/email/net/aspose.email.clients.pop3/pop3client) извлекает сообщения электронной почты из указанного почтового ящика.
- [Aspose.Email.Mail](https://apireference.aspose.com/email/net/aspose.email) отправляет сообщения электронной почты в указанный почтовый ящик.
- [Aspose.Email.Mime](https://apireference.aspose.com/email/net/aspose.email.mime) является связующим звеном между двумя предыдущими компонентами и разбирает сообщения электронной почты.