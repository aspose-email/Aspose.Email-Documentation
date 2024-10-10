---
title: "Первое приложение с Aspose.Email.Outlook"
url: /ru/net/first-application-with-aspose-email-outlook/
weight: 280
type: docs
---


Этот раздел демонстрирует, как использовать [Aspose.Email.Mapi](http://www.aspose.com/api/net/email/aspose.email.mapi/). Мы создаем небольшое приложение, которое загружает файл сообщения Outlook (TestMessage.msg) и отображает тему, адреса отправителя и получателя, а также содержимое тела на форме Windows. Следуйте этим шагам, чтобы создать свое первое приложение с использованием Aspose.Email.Outlook.

1. В Visual Studio в меню **Файл** выберите **Создать**, затем **Проект**.
1. Выберите создание приложения для Windows на C# или VB.NET.
1. Импортируйте DLL Aspose.Email в приложение, щелкнув правой кнопкой мыши по **Ссылке** в Обозревателе решений. Это будет приложение на базе Windows, которое будет отображать только информацию, содержащуюся в файле сообщения.
1. Создайте экземпляр класса [MapiMessage](http://www.aspose.com/api/net/email/aspose.email.mapi/MapiMessage), указав путь к файлу сообщения.
1. Используйте общие свойства для отображения темы, отправителя, получателя и тела на элементах управления Windows.

Реализация вышеуказанных шагов показана ниже в следующем фрагменте кода. Используйте следующий код за кнопкой **Загрузить Msg файл** или в событии OnLoad форм.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AsposeEmailOutlookSampleApp-AsposeEmailOutlook.cs" >}}