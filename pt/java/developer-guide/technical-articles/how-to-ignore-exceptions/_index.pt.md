---
title: "Como Ignorar Exceções"
url: /pt/java/how-to-ignore-exceptions/
weight: 290
type: docs
---


## **Suporte para Ignorar Exceções**
A classe [ExceptionManager](https://apireference.aspose.com/email/java/com.aspose.email/ExceptionManager) fornece a capacidade de ignorar exceções:

### **Exemplos de código:**

Defina um callback para lidar com exceções:
~~~java
ExceptionManager.setIgnoreExceptionsHandler(new IgnoreExceptionsCallback() {
    //caminho da exceção: {Módulo}\{Método}\{Ação}\{GUID}
    //exemplo: MailMessage\Load\DecodeTnefAttachment\64149867-679e-4645-9af0-d46566cae598
    public boolean invoke(AsposeException ex, String path) {
        //Ignorar todas as exceções em MailMessage.Load
        return path.equals("MailMessage\\Load");
    }
});
~~~

Ou use uma **alternativa**:
~~~java
//Ignorar todas as exceções
ExceptionManager.setIgnoreAll(true);
~~~

Além disso, você pode definir um callback para o **log de exceções ignoradas**:
~~~java
ExceptionManager.setIgnoreExceptionsLogHandler(new IgnoreExceptionsLogCallback() {
    public void invoke(String message) {
        System.out.println("=== EXCEÇÃO IGNORADA === " + message);
    }
});
~~~

O usuário será notificado de que a exceção pode ser ignorada por uma mensagem de erro. Por exemplo:
~~~
Mensagem de exceção:

AsposeArgumentException: as propriedades não devem estar vazias.
Se você deseja ignorar uma exceção e deseja prosseguir, pode usar:
ExceptionManager.getIgnoreList().add("MailMessage\\Load\\DecodeTnefAttachment\\64149867-679e-4645-9af0-d46566cae598")
Anexo TNEF inválido será interpretado como anexo regular.
~~~