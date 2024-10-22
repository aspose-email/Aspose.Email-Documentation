---
title: "Extração de dados de objetos incorporados"
url: /pt/net/extraction-of-embedded-objects-data/
weight: 220
type: docs
---


Às vezes, os dados OLE incorporados são representados como um anexo "oleData.mso" pelo [MapiAttachment](https://apireference.aspose.com/net/email/aspose.email.mapi/mapiattachment) e precisam ser extraídos manualmente. Esses arquivos oleData.mso são no formato Microsoft Computer Document File (MCDF) e o suporte para tais arquivos está além da ocupação do Aspose.Email. No entanto, o Aspose.Email pode ser usado em combinação com outras bibliotecas de código aberto, como o OpenMCDF, para ler o conteúdo desses arquivos para salvá-los em disco. O Aspose.Email fornece a classe [InlineAttachmentExtractor](https://apireference.aspose.com/net/email/aspose.email.mapi/inlineattachmentextractor) para enumerar pacotes MSO dos dados binários de oledata.mso, que podem então ser usados para extração de conteúdos por bibliotecas de leitura de arquivos compostos.

Se o tipo do corpo da mensagem for HTML (não RTF), e houver objetos OLE em uma mensagem, a propriedade MapiPropertyTag.PR_ATTACH_DATA_OBJ está ausente. Nesse caso, as informações sobre objetos OLE estão contidas em oldedata.mso.
## **Extração de Objetos Incorporados**
Este artigo mostra como extrair o conteúdo de tal arquivo usando Aspose.Email e [OpenMCDF](http://sourceforge.net/projects/openmcdf/). Isso pode ser feito da seguinte maneira:

- Enumerar pacotes MSO dos dados binários do anexo oledata.mso
- Para cada dado OLE, ler o CompoundFile
- Ler o fluxo com CONTEÚDOS
- Salvar o conteúdo em FileStream



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-ExtractEmbeddedObjectdata-ExtractEmbeddedObjectdata.cs" >}}