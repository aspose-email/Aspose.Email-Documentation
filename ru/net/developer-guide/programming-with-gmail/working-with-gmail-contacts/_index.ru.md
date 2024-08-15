---
title: "Работа с контактами Gmail"
url: /ru/net/working-with-gmail-contacts/
weight: 30
type: docs
---


Aspose.Email поддерживает работу с контактами Gmail. Использование [IGmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/) интерфейс, пользователи могут извлекать контакты из учетной записи Gmail, создавать новые контакты, обновлять и удалять существующие контакты. Gmail позволяет разработчикам выполнять все это с помощью общедоступного API для разработчиков. Для работы с контактами Gmail необходима следующая пользовательская информация:
Имя пользователя, адрес электронной почты, пароль, идентификатор клиента, токен обновления секретного ключа клиента.
В этой статье показано, как:

- [Доступ к контактам Gmail](/email/net/working-with-gmail-contacts/).
- [Создайте новые контакты Gmail](/email/net/working-with-gmail-contacts/).
- [Обновить существующие контакты](/email/net/working-with-gmail-contacts/).
- [Удалить контакт](/email/net/working-with-gmail-contacts/).
- [Сохранить контакт](/email/net/working-with-gmail-contacts/).
 
## **Доступ к контактам Gmail**

Ниже приведен пример приложения, которое можно использовать для доступа к подробной информации о контактах во всех группах.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-AccessGmailContacts-AccessGmailContacts.cs" >}}

## **Создание контакта**

В следующем фрагменте кода показано, как создать контакт.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-CreateGmailContact-CreateGmailContact.cs" >}}

## **Обновление контакта**

После получения контакта его атрибуты можно обновить и сохранить контакт обратно в учетную запись Gmail. В следующем фрагменте кода показано, как извлечь контакты из учетной записи Gmail, а затем изменить один из них, который затем будет сохранен обратно.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-UpdateGmailContact-UpdateGmailContact.cs" >}}

## **Удаление контакта**

Чтобы удалить контакт Gmail, клиент Gmail [DeleteContact](https://reference.aspose.com/email/net/aspose.email.clients.google/igmailclient/deletecontact/#igmailclientdeletecontact-method) метод используется, как показано в следующем примере фрагмента.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-DeleteGmailContact-DeleteGmailContact.cs" >}}

## **Сохранение контакта**

Aspose.Email позволяет сохранять контакты в различных выходных форматах, таких как MSG и VCF. [Save](https://reference.aspose.com/email/net/aspose.email.personalinfo/contact/save/) метод обеспечивает возможность достижения этой цели. В следующем фрагменте кода показано, как сохранить контакт.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Gmail-SavingContact-SavingContact.cs" >}}
