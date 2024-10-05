---
title: "Часто задаваемые вопросы"
url: /ru/java/faqs/
weight: 220
type: docs
---

**Вопрос**

Привет! для следующего кода:

~~~Java

ContentType ct = new ContentType();

ct.setMediaType("application/msword");

ct.setCharSet("ISO-2022-JP");

Attachment att = new Attachment("Test.doc", ct);

System.out.println(att.getContentType().getName());

~~~

att.getContentType().getName() возвращает имя прикрепленного документа. Это ожидаемое поведение?

**Ответ**: 
Да, это ожидаемое поведение. Если getContentType().getName() не задано явно, то значение имени файла будет взято в качестве имени.

**Вопрос:** 
Как я могу извлечь данные из вложения "oleData.mso", которое я получаю в результате чтения MapiMessage, содержащего встроенный объект OLE?

**Ответ**: 
Файлы вроде "oleData.mso" относятся к формату файлов Microsoft Compound Document (MCDF) и, к сожалению, поддержка таких файлов выходит за рамки возможностей Aspose.Email. Тем не менее, существуют некоторые библиотеки с открытым исходным кодом .NET, например OpenMCDF, которые можно использовать для чтения содержимого таких файлов и сохранения на диск.

**Вопрос:** 
Можем ли мы записывать в один и тот же PST файл в параллельных потоках, используя одни и те же объекты?

**Ответ:** 
Нет, безопасность потоков не гарантируется в таком случае. Запись сообщений должна выполняться в одном потоке. Однако продукт должен правильно работать с разными объектами из различных потоков.