---
title: "Criando e Salvando Notas do Outlook em Python"
url: /pt/java/creating-and-saving-outlook-notes-in-python/
weight: 20
type: docs
---

## **Aspose.Email - Criando e Salvando Notas do Outlook**
Para Criar e Salvar Notas do Outlook usando **Aspose.Email Java para Python**, use o código a seguir.

**Código em Python**

```python



note = self.MapiNote()

note.setSubject("Nota de cor azul")

note.setBody("Esta é uma nota de cor azul")

noteColor = self.NoteColor

note.setColor(noteColor.Blue)

note.setHeight(500)

note.setWidth(500)

noteSaveFormat = self.NoteSaveFormat

note.save(self.dataDir + "MapiNote.msg", noteSaveFormat.Msg)

print "Nota do Outlook criada com sucesso."

```
## **Baixar Código em Execução**
Baixe **Criando e Salvando Notas do Outlook (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)