---
title: "Identifique y extraiga el archivo adjunto incrustado de un mensaje formateado como RTF"
url: /es/java/identify-and-extract-embedded-attachment-from-msg-formatted-as-rtf/
weight: 20
type: docs
---

{{% alert color="primary" %}}

Los mensajes de correo electrónico con un cuerpo con formato RTF pueden contener archivos adjuntos integrados que se incrustan como un objeto completo o como un icono. Para diferenciar entre estos dos tipos de archivos adjuntos, es necesario investigar primero ciertas propiedades del archivo adjunto. Tras cumplir ciertos criterios basados en las propiedades del adjunto, este se puede guardar extrayéndolo de sus ObjectData.

{{% /alert %}}

Este artículo identifica y extrae el archivo adjunto incrustado de un archivo MSG con formato RTF.

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
