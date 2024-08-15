---
title: "Генерация повторов на основе шаблона повторения"
url: /ru/net/generate-occurrences-from-a-recurrence-pattern/
weight: 180
type: docs
---


С помощью Aspose.Email можно создавать повторения, используя шаблон повторения. В этой статье объясняется, как и как [сгенерировать следующее событие](#calculate-the-next-occurrence-or-n-next-occurrences) and [получите удобные описания товаров](#get-user-friendly-text-for-a-recurrence). Случаи из шаблона повторения календаря MAPI можно генерировать с помощью Aspose.Email. В следующем фрагменте кода показано, как генерировать повторения на основе шаблонов повторения.


## **Вычислите следующее или n следующих вхождений**
Чтобы получить «следующее» вхождение, используйте метод generateOccurrences с параметром nNextOccurrences=1. В следующем фрагменте кода показано, как создать 20 повторов, используя nNextOccurrences = 20. Вывод приведенного ниже кода выглядит следующим образом:

![todo:image_alt_text](generate-occurrences-from-a-recurrence-pattern_1.png)



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-CalculateTheNextOccurrence-CalculateTheNextOccurrence.cs" >}}
## **Получите удобный текст для повторения**
Удобный для пользователя текст правила можно получить с помощью свойства friendlyText, как показано ниже. Вывод кода будет выглядеть следующим образом: «Повторяйте каждый месяц 1-го и 1-го числа конца месяца, максимум 2 раза». В следующем фрагменте кода показано, как создать удобный для пользователя текст для повторения.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-GetUserFriendlyTextForARecurrence-GetUserFriendlyTextForARecurrence.cs" >}}
