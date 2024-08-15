---
title: "Средство просмотра файлов MSG Outlook"
url: /ru/net/outlook-msg-file-viewer/
weight: 50
type: docs
---


Эта статья посвящена разбору и просмотру MSG-файлов Microsoft Outlook. Если вам нужно манипулировать файлами MSG в вашем проекте или приложении, вам понадобится API для анализа формата Outlook MSG. Или, если в вашей системе не установлен Microsoft Outlook, вы можете создать собственную программу просмотра содержимого файлов MSG.

Примеры кода в этой статье показывают, как анализировать MSG-файл Outlook в приложении C# с помощью библиотеки Aspose.Email. Aspose.Email — это библиотека.NET, доступная в виде DLL. Используйте эту библиотеку для просмотра файлов MSG в Windows, Интернете, консоли или любом приложении на основе .NET. Пробная версия Aspose.Email может быть [легко загружается](http://www.aspose.com/downloads/email/net). Исходный код проекта, приведенный ниже, включен в примеры, поставляемые вместе с инсталлятором.
## **Демонстрационная версия программы просмотра сообщений Outlook**
Мы создали простое демонстрационное приложение, которое можно использовать для анализа и просмотра файлов MSG. Пользовательский интерфейс можно увидеть ниже:

![todo:image_alt_text](outlook-msg-file-viewer_1.png)



На левой панели отображаются диски и папки в системе, как это делает Windows Explorer. Вы можете просматривать папки, чтобы показать или отфильтровать файлы MSG. Только файлы MSG отображаются в верхнем элементе управления списком в соответствующей папке в древовидном представлении. Как видно из скриншота выше, поля Subject, From, To и Cc отображаются в верхнем списке. Если вы нажмете на любое сообщение в списке, откроется соответствующее сообщение, а подробности можно увидеть в пользовательском интерфейсе под элементом управления отображением списка. Мы использовали метки для отображения информации о теме, в которую, в каком направлении и откуда.

На нижней панели мы использовали элементы управления вкладками для отображения других сведений о сообщении, таких как текст, тело RTF, заголовок сообщения, вложения и свойства MAPI. Если вы нажмете кнопку **Attachments** вкладка, она показывает список вложений в файле MSG (если есть). Вы также можете сохранить вложения в систему, выбрав вложение и нажав кнопку **Save** кнопка. Она открывает диалоговое окно «Сохранить файл». Перейдите в нужную папку и сохраните там файл. На следующем скриншоте показано **Attachments** вид вкладок.

![todo:image_alt_text](outlook-msg-file-viewer_2.png)
## **Программный анализ и просмотр содержимого файлов MSG**
В этом разделе мы представим код, который мы использовали в демонстрационной версии для отображения содержимого файла MSG.
### **Загрузка файла MSG**
Библиотека Aspose.Email предоставляет [MapiMessage](https://apireference.aspose.com/email/net/aspose.email.mapi/mapimessage) класс для загрузки и разбора файлов MSG. Файл MSG можно загрузить с помощью одной строки кода, вызвав статический метод fromFile () и передав путь к файлу MSG. В следующем фрагменте кода показано, как загрузить файл MSG.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-LoadingMSGFile-LoadingMSGFile.cs" >}}
### **Получение исходных, исходных, координационных данных и темы из файла MSG**
The [MapiMessage](https://apireference.aspose.com/email/net/aspose.email.mapi/mapimessage) класс предоставляет свойства и коллекции для получения информации о теме, от, до и cc. Ниже приведен пример кода для получения этих свойств. В следующем фрагменте кода показано, как получить данные «Откуда», «Кому», «Cc» и «Тема» из файла MSG.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-GetMessageProperties-GetMessageProperties.cs" >}}
### **Получение текста и тел RTF**
Мы можем получить текст и текст сообщения в формате RTF, используя свойства [MapiMessage](https://apireference.aspose.com/email/net/aspose.email.mapi/mapimessage) класс. В следующем фрагменте кода показано, как получить текст и тела RTF.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-GetTheTextAndRTFBodies-GetTheTextAndRTFBodies.cs" >}}
### **Получение вложений из файла MSG и сохранение на диск**
The [MapiMessage](https://apireference.aspose.com/email/net/aspose.email.mapi/mapimessage) класс предоставляет [Attachments](https://apireference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/properties/attachments) коллекция для получения всех вложений в файле сообщения (MSG). Свойство MapiMessage.attachments возвращает объект типа MapiAttachmentCollection. Для просмотра коллекции вложений и составления списка вложений можно использовать цикл for-each. Класс Attachment содержит метод Save () для сохранения отдельного вложения на диск. В следующем фрагменте кода показано, как получить список вложений и сохранить их.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-GetAttachmentsFromMSGFile-GetAttachmentsFromMSGFile.cs" >}}
### **Получение свойств MAPI файла MSG**
Свойства MAPI можно получить из файла MSG, используя [MapiMessage](https://apireference.aspose.com/email/net/aspose.email.mapi/mapimessage) коллекция свойств класса. В приведенном ниже примере кода показано, как получить все свойства MAPI в файле сообщения.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-GetMAPIProperties-GetMAPIProperties.cs" >}}
