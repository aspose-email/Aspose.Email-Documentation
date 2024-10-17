---
title: "Agregar MapiCalendar a PST en PHP"
url: /es/java/adding-mapicalendar-to-pst-in-php/
weight: 20
type: docs
---

## **Aspose.Email - Agregar MapiCalendar a PST**
Para agregar MapiCalendar a PST usando **Aspose.Email Java para PHP**, simplemente invoca el módulo **AddMapiCalendarToPST**. Aquí puedes ver un código de ejemplo.

**Código PHP**

``` php

 # Crear la cita

$appointment =new MapiCalendar(

"LAKE ARGYLE WA 6743",

"Cita",

"Esta es una reunión muy importante :)",

new Date(2012, 10, 2),

new Date(2012, 10, 2, 14, 0, 0));

\# Crear la reunión

$attendees = new MapiRecipientCollection();

$mapiRecipientType=new MapiRecipientType();

$attendees->add("ReneeAJones@armyspy.com", "Renee A. Jones", $mapiRecipientType->MAPI_TO);

$attendees->add("SzllsyLiza@dayrep.com", "Szollosy Liza", $mapiRecipientType->MAPI_TO);

$meeting = new MapiCalendar(

"Sala de reuniones 3 en la sede de la oficina",

"Reunión",

"Por favor confirma tu disponibilidad.",

new Date(2012, 10, 2, 13, 0, 0),

new Date(2012, 10, 2, 14, 0, 0),

"CharlieKhan@dayrep.com",

$attendees

);

$personalStorage=new PersonalStorage();

$fileFormatVersion=new FileFormatVersion();

$standardIpmFolder=new StandardIpmFolder();

$pst = $personalStorage->create($dataDir . "MapiCalendarToPST1.pst", $fileFormatVersion->Unicode);

$calendar_folder = $pst->createPredefinedFolder("Calendario", $standardIpmFolder->Appointments);

print "MapiCalendar agregado exitosamente.".PHP_EOL;

```
## **Descargar Código en Ejecución**
Descarga **Agregar MapiCalendar a PST (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddMapiCalendarToPST.php)
- [CodePlex](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose.Email-for-Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddMapiCalendarToPST.php)