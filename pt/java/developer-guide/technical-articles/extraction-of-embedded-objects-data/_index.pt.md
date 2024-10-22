---
title: "Extração de dados de Objetos Incorporados"
url: /pt/java/extracao-de-dados-de-objetos-incorporados/
weight: 220
type: docs
---


Às vezes, os dados OLE incorporados são representados como anexos "oleData.mso" pelo [MapiAttachment](https://apireference.aspose.com/email/java/com.aspose.email/MapiAttachment) e precisam ser extraídos manualmente. Esses arquivos oleData.mso estão no formato Microsoft Computer Document File (MCDF) e o suporte para tais arquivos está além da ocupação do Aspose.Email. No entanto, o Aspose.Email pode ser usado em combinação com outras bibliotecas de código aberto, como OpenMCDF, para ler o conteúdo desses arquivos para salvá-los em disco. O Aspose.Email fornece a classe [InlineAttachmentExtractor](https://apireference.aspose.com/email/java/com.aspose.email/InlineAttachmentExtractor) para enumerar pacotes MSO a partir dos dados binários de oledata.mso, que podem então ser usados para a extração de conteúdos por bibliotecas de leitura de Arquivos Compostos.

Se o tipo de corpo da mensagem for HTML (não RTF) e houver objetos OLE em uma mensagem, a propriedade MapiPropertyTag.PR_ATTACH_DATA_OBJ está ausente. Nesse caso, as informações sobre os objetos OLE estão contidas em oldedata.mso.
## **Extração de Objetos Incorporados**
Este artigo mostra como extrair o conteúdo de tal arquivo usando Aspose.Email:



~~~Java
// O caminho para o diretório de arquivos
String dataDir = "/data";

MapiMessage msg = MapiMessage.fromFile(dataDir + "double.msg");
for (MapiAttachment mapiAttachment : msg.getAttachments()) {
    if ("oledata.mso".equals(mapiAttachment.getLongFileName())) {
        IGenericDictionary<String, byte[]> oledata = InlineAttachmentExtractor.enumerateMsoPackage(new ByteArrayInputStream(mapiAttachment.getBinaryData()));

        for (String oleItem : oledata.getKeys()) {
            // Usar dados binários
            processBynaryData(oledata.get_Item(oleItem));
        }
    }
}
~~~