---
title: "Generar Ocurrencias a partir de un Patrón de Recurrencia"
url: /es/net/generate-occurrences-from-a-recurrence-pattern/
weight: 180
type: docs
---


Con Aspose.Email, es posible generar ocurrencias utilizando un patrón de recurrencia. Este artículo explica cómo, cómo [generar la siguiente ocurrencia](#calculate-the-next-occurrence-or-n-next-occurrences) y [obtener descripciones de ítems amigables para el usuario](#get-user-friendly-text-for-a-recurrence). Las ocurrencias de un patrón de recurrencia de calendario MAPI se pueden generar usando Aspose.Email. El siguiente fragmento de código te muestra cómo generar ocurrencias a partir de patrones de recurrencia.


## **Calcular la Siguiente Ocurrencia o n Siguientes Ocurrencias**
Para obtener la "siguiente" ocurrencia, utiliza el método GenerateOccurrences con el parámetro nNextOccurrences=1. El siguiente fragmento de código te muestra cómo generar 20 ocurrencias usando nNextOccurrences = 20. La salida del código a continuación es la siguiente:

![todo:image_alt_text](generate-occurrences-from-a-recurrence-pattern_1.png)



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-CalculateTheNextOccurrence-CalculateTheNextOccurrence.cs" >}}
## **Obtener Texto Amigable para el Usuario para una Recurrencia**
El texto amigable para el usuario de una regla se puede obtener usando la propiedad FriendlyText como se muestra a continuación. La salida del código será: "Recurre cada mes el 1 y el 1 de los días finales del mes, para un máximo de 2 ocurrencias.". El siguiente fragmento de código te muestra cómo obtener texto amigable para el usuario para una recurrencia.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-GetUserFriendlyTextForARecurrence-GetUserFriendlyTextForARecurrence.cs" >}}