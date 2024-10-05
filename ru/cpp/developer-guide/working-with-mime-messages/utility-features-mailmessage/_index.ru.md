---
title: "Утилитарные функции - MailMessage"
description: "Вы можете читать электронные сообщения с вложениями TNEF, используемыми Microsoft Outlook и Exchange Server, а также изменять содержимое вложения с помощью API библиотеки C++ Email Parser."
url: /ru/cpp/utility-features-mailmessage/
weight: 40
type: docs
---

## **MailMessages с вложениями TNEF**
Формат транспортной нейтральной инкапсуляции (TNEF) является проприетарным форматом вложений электронной почты, используемым Microsoft Outlook и Microsoft Exchange Server. API Aspose.Email позволяет вам читать электронные сообщения, которые имеют вложения TNEF, и изменять содержимое вложения. Электронное сообщение можно сохранить как обычное электронное сообщение или в том же формате, сохраняя вложения TNEF. Эта статья демонстрирует различные примеры кода для работы с сообщениями, содержащими вложения TNEF. Эта статья также показывает, как создавать TNEF EML файлы из Outlook MSG файлов.

### **Чтение сообщения с сохранением вложений TNEF**
Следующий фрагмент кода показывает, как читать сообщение, сохраняя вложения TNEF.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-ReadMessageByPreservingTNEFAttachments-ReadMessageByPreservingTNEFAttachments.cpp" >}}

## **Проверка отклоненных сообщений**
Очень часто сообщение, отправленное получателю, может быть отклонено по любой причине, такой как недействительный адрес получателя. API Aspose.Email имеет возможность обрабатывать такие сообщения, чтобы проверить, является ли это отклоненным электронным письмом или обычным электронным сообщением. Метод CheckBounced класса MailMessage возвращает действительный результат, если электронное сообщение является отклоненным. Эта статья демонстрирует использование класса BounceResult, который предоставляет возможность проверки, является ли сообщение отклоненным электронным письмом. Она также предоставляет подробную информацию о получателях, принятых мерах и причине уведомления. Следующий фрагмент кода показывает, как обрабатывать отклоненные сообщения.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-CheckBouncedMessage-CheckBouncedMessage.cpp" >}}