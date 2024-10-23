---
title: "Identificar e Extrair Anexo Incorporado de MSG Formatado como RTF"
url: /pt/java/identificar-e-extrair-anexo-incorporado-de-msg-formatado-como-rtf/
weight: 20
type: docs
---

{{% alert color="primary" %}} 

Mensagens de email com um corpo formatado em RTF podem conter anexos inline que estão incorporados como um objeto inteiro ou como um ícone. Para diferenciar entre esses dois tipos de anexos, certas propriedades do anexo precisam ser investigadas primeiro. Depois de atender a certos critérios com base nas propriedades do anexo, o anexo pode ser salvo extraindo-o de seu ObjectData.

{{% /alert %}} 

Este artigo identifica e extrai anexos incorporados de um arquivo MSG formatado como RTF.

**Java**

``` java

   static void ExtractInlineAttachments()

  {

        MapiMessage message = MapiMessage.fromFile("Test.msg");

    MapiAttachmentCollection attachments = message.getAttachments();

    for (Object untypedAttachment : attachments)

    {

          MapiAttachment attachment = (MapiAttachment) untypedAttachment;

          if(IsAttachmentInline(attachment))

          {

                try

                {

                      SaveAttachment(attachment, UUID.randomUUID().toString());

                }

                catch (IOException | FileNotFoundException e)

                {

                      // TODO Auto-generated catch block

                          e.printStackTrace();

                    }

              }

        }

  }

  static boolean IsAttachmentInline(MapiAttachment attachment)

  {

        MapiObjectProperty objectData = attachment.getObjectData();

        if (objectData == null)

              return false;

        for (Object prop : attachment.getObjectData().getProperties().getValues())

        {

              MapiProperty property = (MapiProperty)prop;

              if ("\u0003ObjInfo".equals(property.getName()))

              {

                    byte[] data = property.getData();

                    int odtPersist1 = data[1] << 8 | data[0];

                    return (odtPersist1 & 0x40) == 0;

              }

        }

        return false;

  }

  static void SaveAttachment(MapiAttachment attachment, String fileName) throws IOException, FileNotFoundException

  {

        for (Object prop : attachment.getObjectData().getProperties().getValues())

        {

              MapiProperty property = (MapiProperty)prop;

              if ("Package".equals(property.getName()))

          {

                FileOutputStream fs;

                try

                {

                      fs = new FileOutputStream(fileName);

                      fs.write(property.getData(), 0, property.getData().length);

                }

                catch (java.io.IOException e)

                {

                      // TODO Auto-generated catch block

                          e.printStackTrace();

                    }

              }

        }

  }

```