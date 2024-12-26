---
title: Adding MapiDistributionList to PST
ArticleTitle: Adding MapiDistributionList to PST
type: docs
weight: 120
url: /java/adding-mapidistributionlist-to-pst/
---

[Create New PST, Add Sub-folders and Messages](/email/java/create-new-pst-add-sub-folders-and-messages/) showed how to create a PST file and add a subfolder to it. With Aspose.Email you can add a [MapiDistributionList](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlist/) to the Contacts subfolder of a PST file that you have created or loaded.

{{% alert color="primary" %}} 

In order to set the EntryId for a [MapiDistributionListMember](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlistmember/), the base64String needs to be converted using [Apache Commons Codec](https://commons.apache.org/proper/commons-codec/download_codec.cgi).

{{% /alert %}} 

## **Load MapidistributionList from file**

The code below loads a MAPI distribution list from a file.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiDistributionListToPST-LoadMapiDistributionList.java" >}}

## **Create a New MapiDistributionList and Add it to the Contacts Subfolder**

Below are the steps to add a [MapiDistributionList](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlist/) to a PST:

1. Create a new PST.
1. Add the Contacts folder to PST.
1. Create sample contacts.
1. Create a distribution list on the base of the created contacts.
1. Add the distribution list to PST.

The code snippet below shows how to create a [MapiDistributionList](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlist/) and then add it to the Contacts folder of a newly created PST file.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiDistributionListToPST-AddMapiDistributionListToPST.java" >}}

## **Create a One-off Distribution List**

For this distribution list, no separate contacts are required.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiDistributionListToPST-CreateAOneOffDistributionList.java" >}}
