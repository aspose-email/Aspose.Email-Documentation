---
title: Работа с свойствами защиты паролем PST
type: docs
weight: 100
url: /java/working-with-pst-password-protection-properties/
---

{{% alert color="primary" %}} 

Microsoft Outlook позволяет пользователям защищать файлы PST паролем для ограничения доступа к ним. Aspose.Email может обнаруживать защиту паролем на файле PST. Эта статья показывает, как проверить файл PST на наличие пароля, а также как проверить, является ли введённый пароль правильным.

{{% /alert %}} 

## **Проверка на защиту паролем**

Значение [MapiPropertyTag.PR_PST_PASSWORD](https://reference.aspose.com/email/java/com.aspose.email/mapipropertytag/#PR-PST-PASSWORD) из класса [MapiPropertyTag](https://reference.aspose.com/email/java/com.aspose.email/mapipropertytag/) используется для проверки, защищён ли файл паролем.

CRC-32 хеш строки пароля хранится в свойстве PidTagPstPassword (tag = 0x67ff0003) в [MessageStore](https://reference.aspose.com/email/java/com.aspose.email/messagestore/). Если это свойство существует и его значение не ноль, то PST защищён паролем.

Следующий фрагмент кода показывает, как проверить, защищён ли файл PST паролем, и является ли данная строка допустимым паролем для этого PST.

Ниже приведённый фрагмент кода демонстрирует две функции: первая проверяет, защищён ли PST паролем, а вторая показывает, как проверить, является ли предоставленный пароль правильным или нет.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-PSTPasswordProtectionProperties-CheckForPasswordProtection.java" >}}

## **Удаление/Сброс свойства PR_PST_PASSWORD**

Удалить свойство [PR_PST_PASSWORD](https://reference.aspose.com/email/java/com.aspose.email/mapipropertytag/#PR-PST-PASSWORD) нельзя так же, как удаляются другие свойства из хранилища сообщений. Вместо этого мы должны установить его значение в ноль (0), чтобы удалить его. Свойство "Store" класса PST предоставляет доступ к свойствам хранилища PST, а не к MessageStoreProperties PST в этом случае.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-PSTPasswordProtectionProperties-RemovePSTPasswordProperty.java" >}}

## **Установка/Изменение пароля PST**

Следующий фрагмент кода показывает, как установить пароль на файлы PST.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-PSTPasswordProtectionProperties-SetPSTPassword.java" >}}

## **Проверка пароля для защищённых паролем файлов PST**

Aspose.Email позволяет разработчикам проверять, защищён ли файл PST паролем, и проверять, является ли введённый пароль правильным или нет. Для этого API предоставляет свойство [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#isPasswordProtected--) и метод [PersonalStorage.Store.IsPasswordValid()](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#isPasswordValid-java.lang.String-). Свойство [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#isPasswordProtected--) возвращает **true**, если файл PST защищён паролем, и **false**, если нет. Метод [PersonalStorage.Store.IsPasswordValid()](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#isPasswordValid-java.lang.String-) принимает строку пароля в качестве параметра и возвращает **true**, если пароль правильный, и **false**, если он неверный.

Следующий фрагмент кода демонстрирует использование свойства [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#isPasswordProtected--) и метода [PersonalStorage.Store.IsPasswordValid()](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#isPasswordValid-java.lang.String-).

### **Пример кода**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-PSTPasswordValidation-1.java" >}}

### **Консольный вывод**

Хранилище защищено паролем - True
Пароль действителен - True