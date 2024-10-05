---
title: Добавление MapiDistributionList в PST
type: docs
weight: 120
url: /java/adding-mapidistributionlist-to-pst/
---

[Создание нового PST, добавление подпапок и сообщений](/email/java/create-new-pst-add-sub-folders-and-messages/) показало, как создать файл PST и добавить в него подпапку. С помощью Aspose.Email вы можете добавить [MapiDistributionList](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlist/) в подпапку Контакты файла PST, который вы создали или загрузили.

{{% alert color="primary" %}} 

Для установки EntryId для [MapiDistributionListMember](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlistmember/) строку base64String необходимо конвертировать с использованием [Apache Commons Codec](https://commons.apache.org/proper/commons-codec/download_codec.cgi).

{{% /alert %}} 

## **Загрузка MapiDistributionList из файла**

Код ниже загружает MAPI-список рассылки из файла.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiDistributionListToPST-LoadMapiDistributionList.java" >}}

## **Создание нового MapiDistributionList и добавление его в подпапку Контакты**

Ниже приведены шаги для добавления [MapiDistributionList](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlist/) в PST:

1. Создайте новый PST.
1. Добавьте папку Контакты в PST.
1. Создайте примеры контактов.
1. Создайте список рассылки на основе созданных контактов.
1. Добавьте список рассылки в PST.

Код ниже показывает, как создать [MapiDistributionList](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlist/) и затем добавить его в папку Контакты вновь созданного файла PST.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiDistributionListToPST-AddMapiDistributionListToPST.java" >}}

## **Создание разового списка рассылки**

Для этого списка рассылки отдельные контакты не требуются.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiDistributionListToPST-CreateAOneOffDistributionList.java" >}}