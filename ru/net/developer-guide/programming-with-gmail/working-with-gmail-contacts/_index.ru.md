---
title: "Работа с контактами Gmail"
url: /ru/net/working-with-gmail-contacts/
weight: 30
type: docs
---


Aspose.Email поддерживает работу с контактами Gmail. Используя интерфейс [IGmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/), пользователи могут извлекать контакты из учетной записи Gmail, создавать новые контакты, а также обновлять и удалять существующие контакты. Gmail позволяет разработчикам выполнять все это с помощью своего публичного API для разработчиков. Для работы с контактами Gmail необходима следующая информация о пользователе: 
Имя пользователя, адрес электронной почты, пароль, ID клиента, секрет клиента, токен обновления.
В этой статье показано, как:

- [Получить доступ к контактам Gmail](/email/net/working-with-gmail-contacts/).
- [Создать новые контакты Gmail](/email/net/working-with-gmail-contacts/).
- [Обновить существующие контакты](/email/net/working-with-gmail-contacts/).
- [Удалить контакт](/email/net/working-with-gmail-contacts/).
- [Сохранить контакт](/email/net/working-with-gmail-contacts/).
  
## **Доступ к контактам Gmail**

Следующее является примером приложения, которое может быть использовано для доступа к деталям контактов во всех группах.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-AccessGmailContacts-AccessGmailContacts.cs" >}}

## **Создание контакта**

Следующий фрагмент кода показывает, как создать контакт.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-CreateGmailContact-CreateGmailContact.cs" >}}

## **Обновление контакта**

После того, как контакт будет извлечен, его атрибуты могут быть обновлены, и контакт может быть сохранен обратно в учетную запись Gmail. Следующий фрагмент кода показывает, как извлекать контакты из учетной записи Gmail и затем модифицировать один из них, после чего он сохраняется обратно.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-UpdateGmailContact-UpdateGmailContact.cs" >}}

## **Удаление контакта**

Для удаления контакта Gmail используется метод клиента Gmail [DeleteContact](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/deletecontact/#igmailclientdeletecontact-method), как показано в следующем образце кода.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-DeleteGmailContact-DeleteGmailContact.cs" >}}

## **Сохранение контакта**

Aspose.Email позволяет сохранять контакты в различные форматы вывода, такие как MSG и VCF. Метод [Save](https://reference.aspose.com/email/net/aspose.email.personalinfo/contact/save/) предоставляет возможность достичь этого. Следующий фрагмент кода показывает, как сохранить контакт.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-SavingContact-SavingContact.cs" >}}