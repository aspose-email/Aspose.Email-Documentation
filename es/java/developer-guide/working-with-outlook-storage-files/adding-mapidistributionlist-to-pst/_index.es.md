---
title: "Agregar MapiDistributionList a PST"
url: /es/java/adding-mapidistributionlist-to-pst/
weight: 120
type: docs
---

[Crear nuevo PST, agregar subcarpetas y mensajes](/email/java/create-new-pst-add-sub-folders-and-messages/) mostró cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email puedes agregar una [MapiDistributionList](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlist/) a la subcarpeta de Contactos de un archivo PST que has creado o cargado.

{{% alert color="primary" %}} 

Para establecer el EntryId para un [MapiDistributionListMember](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlistmember/), el base64String debe ser convertido usando [Apache Commons Codec](https://commons.apache.org/proper/commons-codec/download_codec.cgi).

{{% /alert %}} 

## **Cargar MapiDistributionList desde un archivo**

El código a continuación carga una lista de distribución MAPI desde un archivo.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiDistributionListToPST-LoadMapiDistributionList.java" >}}

## **Crear una nueva MapiDistributionList y agregarla a la subcarpeta de Contactos**

A continuación se presentan los pasos para agregar una [MapiDistributionList](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlist/) a un PST:

1. Crear un nuevo PST.
1. Agregar la carpeta de Contactos al PST.
1. Crear contactos de ejemplo.
1. Crear una lista de distribución sobre la base de los contactos creados.
1. Agregar la lista de distribución al PST.

El fragmento de código a continuación muestra cómo crear una [MapiDistributionList](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlist/) y luego agregarla a la carpeta de Contactos de un archivo PST recién creado.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiDistributionListToPST-AddMapiDistributionListToPST.java" >}}

## **Crear una lista de distribución única**

Para esta lista de distribución, no se requieren contactos separados.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiDistributionListToPST-CreateAOneOffDistributionList.java" >}}