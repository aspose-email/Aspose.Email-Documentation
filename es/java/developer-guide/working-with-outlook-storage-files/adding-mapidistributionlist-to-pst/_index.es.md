---
title: "Agregar MapiDistributionList a PST"
url: /es/java/adding-mapidistributionlist-to-pst/
weight: 120
type: docs
---

[Crear un nuevo PST, agregar subcarpetas y mensajes](/email/java/create-new-pst-add-sub-folders-and-messages/) mostró cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email puedes agregar un [MapiDistributionList](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlist/) a la subcarpeta Contactos de un archivo PST que haya creado o cargado.

{{% alert color="primary" %}}

Para establecer el EntryID para un [MapiDistributionListMember](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlistmember/), la cadena Base64 debe convertirse usando [Códec Apache Commons](https://commons.apache.org/proper/commons-codec/download_codec.cgi).

{{% /alert %}}

## **Cargar MapiDistributionList desde un archivo**

El código siguiente carga una lista de distribución MAPI desde un archivo.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiDistributionListToPST-LoadMapiDistributionList.java" >}}

## **Cree una nueva MAPIDistributionList y agréguela a la subcarpeta Contactos**

A continuación se muestran los pasos para agregar un [MapiDistributionList](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlist/) a un PST:

1. Crea un nuevo PST.
1. Agregue la carpeta Contactos a PST.
1. Crea contactos de muestra.
1. Cree una lista de distribución sobre la base de los contactos creados.
1. Agregue la lista de distribución a PST.

El siguiente fragmento de código muestra cómo crear un [MapiDistributionList](https://reference.aspose.com/email/java/com.aspose.email/mapidistributionlist/) y, a continuación, agréguelo a la carpeta Contactos de un archivo PST recién creado.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiDistributionListToPST-AddMapiDistributionListToPST.java" >}}

## **Crear una lista de distribución única**

Para esta lista de distribución, no se requieren contactos separados.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiDistributionListToPST-CreateAOneOffDistributionList.java" >}}
