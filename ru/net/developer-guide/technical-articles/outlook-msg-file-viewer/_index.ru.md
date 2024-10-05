---
title: "Просмотрщик файлов MSG Outlook"
url: /ru/net/outlook-msg-file-viewer/
weight: 50
type: docs
---


Эта статья посвящена разбору и просмотру файлов MSG Microsoft Outlook. Если вам нужно управлять файлами MSG в вашем проекте или приложении, вам нужен API для разбора формата Outlook MSG. Или, если у вас нет Microsoft Outlook, установленного на вашей системе, вы можете создать собственный просмотрщик для получения содержимого файла MSG.

Примеры кода в этой статье показывают, как разобрать файл MSG Outlook в приложении C# с использованием библиотеки Aspose.Email. Aspose.Email — это .NET библиотека, доступная в виде DLL. Используйте эту библиотеку для просмотра файлов MSG в Windows, вебе, консольных или любых других приложениях на основе .NET. Пробную версию Aspose.Email можно [легко скачать](http://www.aspose.com/downloads/email/net). Исходный код для проекта ниже включен в образцы, предоставленные с установщиком.
## **Демо просмотрщика MSG Outlook**
Мы создали простое демо-приложение, которое можно использовать для разбора и просмотра файлов MSG. Пользовательский интерфейс можно увидеть ниже:

![todo:image_alt_text](outlook-msg-file-viewer_1.png)



Левая панель показывает диски и папки на системе, как это делает проводник Windows. Вы можете просматривать папки, чтобы отобразить или отфильтровать файлы MSG. Только файлы MSG появляются в верхнем списке контроллера отображения в соответствующей папке в древовидном представлении. Как видно из скриншота выше, поля Тема, От, Кому и Копия отображаются в верхнем списке. Если вы щелкните на любом MSG в списке, соответствующее сообщение откроется, и детали можно будет увидеть в интерфейсе ниже контроллера списка. Мы использовали метки для отображения информации о теме, кому, копии и от.

В нижней панели мы использовали вкладки для показа других деталей сообщения, таких как текстовое тело, RTF тело, заголовок сообщения, вложения и свойства MAPI. Если вы щелкните на вкладку **Вложения**, она показывает список вложений в файле MSG (если они есть). Вы также можете сохранить вложения на свою систему, выбрав вложение и щелкнув кнопку **Сохранить**. Откроется диалоговое окно сохранения файла. Перейдите в нужную папку и сохраните файл там. Следующий скриншот показывает вид вкладки **Вложения**.

![todo:image_alt_text](outlook-msg-file-viewer_2.png)
## **Парсинг и просмотр содержимого файла MSG программным образом**
В этом разделе мы представим код, который мы использовали в демо, чтобы показать содержимое файла MSG.
### **Загрузка файла MSG**
Библиотека Aspose.Email предоставляет класс [MapiMessage](https://apireference.aspose.com/email/net/aspose.email.mapi/mapimessage) для загрузки и разбора файлов MSG. Вы можете загрузить файл MSG с помощью одной строки кода, вызвав статический метод FromFile() и передав путь к файлу MSG. Следующий фрагмент кода показывает, как загрузить файл MSG.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-LoadingMSGFile-LoadingMSGFile.cs" >}}
### **Получение информации От, Кому, Копия и Тема из файла MSG**
Класс [MapiMessage](https://apireference.aspose.com/email/net/aspose.email.mapi/mapimessage) предоставляет свойства и коллекции для получения информации о теме, от, к кому и копии. Следующий пример кода показывает, как получить эти свойства. Следующий фрагмент кода показывает, как получить От, Кому, Копия и Тема из файла MSG.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-GetMessageProperties-GetMessageProperties.cs" >}}
### **Получение текстовых и RTF тел**
Мы можем получить текстовые и RTF тела сообщения, используя свойства класса [MapiMessage](https://apireference.aspose.com/email/net/aspose.email.mapi/mapimessage). Следующий фрагмент кода показывает, как получить текстовые и RTF тела.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-GetTheTextAndRTFBodies-GetTheTextAndRTFBodies.cs" >}}
### **Получение вложений из файла MSG и сохранение на диск**
Класс [MapiMessage](https://apireference.aspose.com/email/net/aspose.email.mapi/mapimessage) предоставляет коллекцию [Attachments](https://apireference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/properties/attachments) для получения всех вложений в файле сообщения (MSG). Свойство MapiMessage.Attachments возвращает объект типа MapiAttachmentCollection. Вы можете использовать цикл for-each, чтобы перебрать коллекцию вложений и перечислить вложения. Класс Attachment содержит метод Save() для сохранения отдельного вложения на диск. Следующий фрагмент кода показывает, как получить список вложений и сохранить их.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-GetAttachmentsFromMSGFile-GetAttachmentsFromMSGFile.cs" >}}
### **Получение свойств MAPI файла MSG**
Вы можете получить свойства MAPI из файла MSG, используя коллекцию свойств класса [MapiMessage](https://apireference.aspose.com/email/net/aspose.email.mapi/mapimessage). Пример кода ниже показывает, как получить все свойства MAPI в файле сообщения.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-GetMAPIProperties-GetMAPIProperties.cs" >}}