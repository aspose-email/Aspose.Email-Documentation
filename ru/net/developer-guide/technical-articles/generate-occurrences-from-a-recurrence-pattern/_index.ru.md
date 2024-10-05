---
title: "Генерация событий на основе шаблона повторения"
url: /ru/net/generate-occurrences-from-a-recurrence-pattern/
weight: 180
type: docs
---


С помощью Aspose.Email можно генерировать события, используя шаблон повторения. Эта статья объясняет, как это сделать, как [сгенерировать следующее событие](#calculate-the-next-occurrence-or-n-next-occurrences) и [получить удобные для пользователя описания элементов](#get-user-friendly-text-for-a-recurrence). События на основе шаблона повторения календаря MAPI могут быть созданы с использованием Aspose.Email. Следующий фрагмент кода показывает, как генерировать события из шаблонов повторения.


## **Расчет следующего события или n следующих событий**
Чтобы получить "следующее" событие, используйте метод GenerateOccurrences с параметром nNextOccurrences=1. Следующий фрагмент кода показывает, как сгенерировать 20 событий, используя nNextOccurrences = 20. Вывод кода ниже выглядит следующим образом:

![todo:image_alt_text](generate-occurrences-from-a-recurrence-pattern_1.png)



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-CalculateTheNextOccurrence-CalculateTheNextOccurrence.cs" >}}
## **Получение удобного для пользователя текста для повторения**
Удобный для пользователя текст для правила можно получить с помощью свойства FriendlyText, как показано ниже. Вывод кода будет следующим: "Повторять каждый месяц 1-го и 1-го числа с конца дня(ей) месяца максимально 2 раза.". Следующий фрагмент кода показывает, как получить удобный для пользователя текст для повторения.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-GetUserFriendlyTextForARecurrence-GetUserFriendlyTextForARecurrence.cs" >}}