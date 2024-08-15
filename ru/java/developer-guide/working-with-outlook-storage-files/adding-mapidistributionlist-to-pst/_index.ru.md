---
title: "Добавление списка рассылки MapiDistributionList в PST"
url: /ru/java/adding-mapidistributionlist-to-pst/
weight: 120
type: docs
---

[Создайте новый PST, добавьте подпапки и сообщения](/email/java/create-new-pst-add-sub-folders-and-messages/) показал, как создать файл PST и добавить в него подпапку. С помощью Aspose.Email вы можете добавить [MapiDistributionList](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlist/) в подпапку «Контакты» созданного или загруженного файла PST.

{{% alert color="primary" %}}

Чтобы установить EntryID для [MapiDistributionListMember](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlistmember/), строку Base64String необходимо преобразовать, используя [Кодек Apache Commons](https://commons.apache.org/proper/commons-codec/download_codec.cgi).

{{% /alert %}}

## **Загрузить список рассылки Mapi из файла**

Приведенный ниже код загружает список рассылки MAPI из файла.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiDistributionListToPST-LoadMapiDistributionList.java" >}}

## **Создайте новый MapiDistributionList и добавьте его в подпапку «Контакты»**

Ниже приведены шаги по добавлению [MapiDistributionList](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlist/) в PST:

1. Создайте новый PST.
1. Добавьте папку «Контакты» в PST.
1. Создайте образцы контактов.
1. Создайте список рассылки на основе созданных контактов.
1. Добавьте список рассылки в PST.

В приведенном ниже фрагменте кода показано, как создать [MapiDistributionList](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlist/) а затем добавьте его в папку «Контакты» вновь созданного файла PST.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiDistributionListToPST-AddMapiDistributionListToPST.java" >}}

## **Создайте одноразовый список рассылки**

Для этого списка рассылки не требуются отдельные контакты.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiDistributionListToPST-CreateAOneOffDistributionList.java" >}}
