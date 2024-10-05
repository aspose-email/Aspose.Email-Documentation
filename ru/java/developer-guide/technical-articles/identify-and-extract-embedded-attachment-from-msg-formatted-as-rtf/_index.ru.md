---
title: "Определение и извлечение встроенного вложения из MSG, отформатированного как RTF"
url: /ru/java/identify-and-extract-embedded-attachment-from-msg-formatted-as-rtf/
weight: 20
type: docs
---

{{% alert color="primary" %}} 

Электронные письма с телом в формате RTF могут содержать встроенные вложения, которые либо встраиваются как целый объект, либо представлены как иконка. Чтобы различать эти два типа вложений, необходимо сначала изучить определенные свойства вложения. После выполнения определенных критериев, основанных на свойствах вложения, вложение может быть сохранено путем извлечения его из ObjectData.

{{% /alert %}} 

В этой статье определяется и извлекается встроенное вложение из файла MSG, отформатированного как RTF.

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