---
title: "Adicionando MapiDistributionList ao PST"
url: /pt/java/adding-mapidistributionlist-to-pst/
weight: 120
type: docs
---

[Criar Novo PST, Adicionar Subpastas e Mensagens](/email/java/create-new-pst-add-sub-folders-and-messages/) mostrou como criar um arquivo PST e adicionar uma subpasta a ele. Com Aspose.Email você pode adicionar uma [MapiDistributionList](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlist/) à subpasta Contatos de um arquivo PST que você criou ou carregou.

{{% alert color="primary" %}} 

Para definir o EntryId para um [MapiDistributionListMember](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlistmember/), o base64String precisa ser convertido usando o [Apache Commons Codec](https://commons.apache.org/proper/commons-codec/download_codec.cgi).

{{% /alert %}} 

## **Carregar MapiDistributionList de arquivo**

O código abaixo carrega uma lista de distribuição MAPI de um arquivo.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiDistributionListToPST-LoadMapiDistributionList.java" >}}

## **Criar uma Nova MapiDistributionList e Adicioná-la à Subpasta Contatos**

Abaixo estão os passos para adicionar uma [MapiDistributionList](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlist/) ao PST:

1. Criar um novo PST.
1. Adicionar a pasta Contatos ao PST.
1. Criar contatos de exemplo.
1. Criar uma lista de distribuição com base nos contatos criados.
1. Adicionar a lista de distribuição ao PST.

O trecho de código abaixo mostra como criar uma [MapiDistributionList](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlist/) e depois adicioná-la à pasta Contatos de um arquivo PST recém-criado.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiDistributionListToPST-AddMapiDistributionListToPST.java" >}}

## **Criar uma Lista de Distribuição Pontual**

Para esta lista de distribuição, não são necessários contatos separados.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiDistributionListToPST-CreateAOneOffDistributionList.java" >}}