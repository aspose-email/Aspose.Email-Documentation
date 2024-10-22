---
title: "Adicionando MapiCalendar ao PST em PHP"
url: /pt/java/adicionando-mapicalendar-ao-pst-em-php/
weight: 20
type: docs
---

## **Aspose.Email - Adicionando MapiCalendar ao PST**  
Para adicionar MapiCalendar ao PST usando **Aspose.Email Java para PHP**, simplesmente invoque o módulo **AddMapiCalendarToPST**. Aqui você pode ver um exemplo de código.  

**Código PHP**  

``` php  

 # Criar o compromisso  

$appointment =new MapiCalendar(  

"LAKE ARGYLE WA 6743",  

"Compromisso",  

"Esta é uma reunião muito importante :)",  

new Date(2012, 10, 2),  

new Date(2012, 10, 2, 14, 0, 0));  

\# Criar a reunião  

$attendees = new MapiRecipientCollection();  

$mapiRecipientType=new MapiRecipientType();  

$attendees->add("ReneeAJones@armyspy.com", "Renee A. Jones", $mapiRecipientType->MAPI_TO);  

$attendees->add("SzllsyLiza@dayrep.com", "Szollosy Liza", $mapiRecipientType->MAPI_TO);  

$meeting = new MapiCalendar(  

"Sala de Reuniões 3 na Sede",  

"Reunião",  

"Por favor, confirme sua disponibilidade.",  

new Date(2012, 10, 2, 13, 0, 0),  

new Date(2012, 10, 2, 14, 0, 0),  

"CharlieKhan@dayrep.com",  

$attendees  

);  

$personalStorage=new PersonalStorage();  

$fileFormatVersion=new FileFormatVersion();  

$standardIpmFolder=new StandardIpmFolder();  

$pst = $personalStorage->create($dataDir . "MapiCalendarToPST1.pst", $fileFormatVersion->Unicode);  

$calendar_folder = $pst->createPredefinedFolder("Calendário", $standardIpmFolder->Appointments);  

print "MapiCalendar adicionado com sucesso.".PHP_EOL;  

```  
## **Baixar Código em Execução**  
Baixe **Adicionando MapiCalendar ao PST (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:  

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddMapiCalendarToPST.php)  
- [CodePlex](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose.Email-for-Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddMapiCalendarToPST.php)  