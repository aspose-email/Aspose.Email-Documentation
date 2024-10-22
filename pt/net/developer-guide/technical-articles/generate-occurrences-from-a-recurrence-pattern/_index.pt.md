---
title: "Gerar Ocorrências a Partir de um Padrão de Recorrência"
url: /pt/net/generate-occurrences-from-a-recurrence-pattern/
weight: 180
type: docs
---

Com Aspose.Email, é possível gerar ocorrências usando um padrão de recorrência. Este artigo explica como, como [gerar a próxima ocorrência](#calculate-the-next-occurrence-or-n-next-occurrences) e [obter descrições de itens amigáveis ao usuário](#get-user-friendly-text-for-a-recurrence). Ocorrências de um padrão de recorrência de calendário MAPI podem ser geradas usando Aspose.Email. O seguinte trecho de código mostra como gerar ocorrências a partir de padrões de recorrência.

## **Calcular a Próxima Ocorrência ou n Próximas Ocorrências**
Para obter a próxima ocorrência, use o método GenerateOccurrences com o parâmetro nNextOccurrences=1. O seguinte trecho de código mostra como gerar 20 ocorrências usando nNextOccurrences = 20. A saída do código abaixo é a seguinte:

![todo:image_alt_text](generate-occurrences-from-a-recurrence-pattern_1.png)

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-CalculateTheNextOccurrence-CalculateTheNextOccurrence.cs" >}}
## **Obter Texto Amigável ao Usuário para uma Recorrência**
Texto amigável ao usuário para uma regra pode ser obtido usando a propriedade FriendlyText, conforme mostrado abaixo. A saída do código será: "Recorrência todo mês no 1º e 1º dia(s) do final do mês para um máximo de 2 ocorrências.". O seguinte trecho de código mostra como obter texto amigável ao usuário para uma recorrência.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-GetUserFriendlyTextForARecurrence-GetUserFriendlyTextForARecurrence.cs" >}}