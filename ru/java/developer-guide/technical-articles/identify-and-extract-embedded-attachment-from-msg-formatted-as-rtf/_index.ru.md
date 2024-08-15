---
title: "Определите и извлеките встроенное вложение из MSG в формате RTF"
url: /ru/java/identify-and-extract-embedded-attachment-from-msg-formatted-as-rtf/
weight: 20
type: docs
---

{{% alert color="primary" %}}

Сообщения электронной почты с текстом в формате RTF могут содержать встроенные вложения, встроенные в виде целого объекта или значка. Чтобы отличить эти два типа вложений, сначала необходимо изучить некоторые свойства вложения. После выполнения определенных критериев, основанных на свойствах вложения, вложение можно сохранить, извлекая его из ObjectData.

{{% /alert %}}

Эта статья идентифицирует и извлекает встроенное вложение из файла MSG в формате RTF.

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
