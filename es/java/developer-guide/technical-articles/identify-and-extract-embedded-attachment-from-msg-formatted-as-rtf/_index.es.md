---
title: "Identificar y extraer adjuntos incrustados de MSG formateados como RTF"
url: /es/java/identificar-y-extraer-adjuntos-incrustados-de-msg-formateados-como-rtf/
weight: 20
type: docs
---

{{% alert color="primary" %}} 

Los mensajes de correo electrónico con un cuerpo formateado en RTF pueden contener adjuntos en línea que están incrustados como un objeto completo o como un ícono. Para diferenciar entre estos dos tipos de adjuntos, se deben investigar primero ciertas propiedades del adjunto. Después de cumplir con ciertos criterios basados en las propiedades del adjunto, el adjunto puede ser guardado extrayéndolo de su ObjectData.

{{% /alert %}} 

Este artículo identifica y extrae adjuntos incrustados de un archivo MSG formateado como RTF.

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