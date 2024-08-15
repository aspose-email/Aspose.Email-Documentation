---
title: "Первое приложение с использованием Aspose.Email.Outlook"
url: /ru/net/first-application-with-aspose-email-outlook/
weight: 280
type: docs
---


В этом разделе показано, как использовать [Aspose.Email.Mapi](http://www.aspose.com/api/net/email/aspose.email.mapi/). Мы создаем небольшое приложение, которое загружает файл сообщений Outlook (TestMessage.msg) и отображает тему сообщения, адреса от и до адреса, а также основное содержимое формы Windows. Выполните следующие действия, чтобы создать свое первое приложение с помощью Aspose.Email.Outlook.

1. В Visual Studio на **File** меню, выберите **New**, затем **Project**.
1. Выберите создание приложения для Windows на языке C# или VB.NET.
1. Импортируйте DLL Aspose.Email в приложение, щелкнув правой кнопкой мыши **Reference** в обозревателе решений. Это будет приложение на базе Windows, которое будет отображать только информацию, содержащуюся в файле сообщения.
1. Создайте экземпляр [MapiMessage](http://www.aspose.com/api/net/email/aspose.email.mapi/MapiMessage) класс, указав путь к файлу сообщения.
1. Используйте общедоступные свойства для отображения объекта, от, до и тела на элементах управления Windows.

Реализация вышеуказанных шагов продемонстрирована ниже в следующем фрагменте кода. Используйте следующий код, лежащий в основе **Загрузить файл Msg** кнопку или в событии forms onLoad.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AsposeEmailOutlookSampleApp-AsposeEmailOutlook.cs" >}}
