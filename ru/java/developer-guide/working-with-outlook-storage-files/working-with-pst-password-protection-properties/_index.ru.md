---
title: "Работа со свойствами защиты паролем PST"
url: /ru/java/working-with-pst-password-protection-properties/
weight: 100
type: docs
---

{{% alert color="primary" %}}

Microsoft Outlook позволяет пользователям защищать PST-файлы паролем для ограничения доступа к ним. Aspose.Email может обнаруживать защиту паролем в PST-файле. В этой статье показано, как проверить пароль в PST, а также как проверить правильность примененного к нему пароля.

{{% /alert %}}

## **Проверьте защиту паролем**

The [MapiPropertyTag.PR_PST_PASSWORD](https://reference.aspose.com/email/java/com.aspose.email/mapipropertytag/#PR-PST-PASSWORD) значение от [MapiPropertyTag](https://reference.aspose.com/email/java/com.aspose.email/mapipropertytag/) класс используется для проверки того, защищен ли файл паролем.

Хеш строки пароля CRC-32 хранится в свойстве pidTagPstPassword (тег = 0x67ff0003) в [MessageStore](https://reference.aspose.com/email/java/com.aspose.email/messagestore/). Если это свойство существует и не равно нулю, то PST защищен паролем.

В следующем фрагменте кода показано, как проверить, защищен ли PST-файл паролем и является ли данная строка действительным паролем для этого PST.

В приведенном ниже фрагменте кода показаны две функции: первая проверяет, защищен ли PST паролем, а вторая показывает, как проверить правильность предоставленного пароля.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-PSTPasswordProtectionProperties-CheckForPasswordProtection.java" >}}

## **Удалить/сбросить свойство PR_PST_PASSWORD**

Удаление [PR_PST_PASSWORD](https://reference.aspose.com/email/java/com.aspose.email/mapipropertytag/#PR-PST-PASSWORD) невозможно получить свойство, так как другие свойства удаляются из хранилища сообщений. Вместо этого нам нужно присвоить этому значению ноль (0), чтобы удалить его. Свойство «Store» класса PST в данном случае предоставляет доступ к свойствам хранилища PST вместо MessageStoreProperties из PST.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-PSTPasswordProtectionProperties-RemovePSTPasswordProperty.java" >}}

## **Установить/изменить пароль PST**

В следующем фрагменте кода показано, как установить пароль для файлов PST.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-PSTPasswordProtectionProperties-SetPSTPassword.java" >}}

## **Проверка пароля для PST-файлов, защищенных паролем**

Aspose.Email позволяет разработчикам проверить, защищен ли файл PST паролем, и проверить, является ли данный пароль правильным или нет. Для этого API предоставляет [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#isPasswordProtected--) имущество и [PersonalStorage.Store.IsPasswordValid()](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#isPasswordValid-java.lang.String-) метод. [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#isPasswordProtected--) возврат недвижимости **true** если файл PST защищен паролем и **false** если это не так. [PersonalStorage.Store.IsPasswordValid()](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#isPasswordValid-java.lang.String-) метод, который принимает строковый пароль в качестве параметра и возвращает **true** если пароль правильный и ложный, он неверен.

Следующий фрагмент кода демонстрирует использование [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#isPasswordProtected--) имущество и [PersonalStorage.Store.IsPasswordValid()](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#isPasswordValid-java.lang.String-) method.

### **Образец кода**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-PSTPasswordValidation-1.java" >}}

### **Выход на консоль**

Хранилище защищено паролем - True
Пароль действителен — верно
