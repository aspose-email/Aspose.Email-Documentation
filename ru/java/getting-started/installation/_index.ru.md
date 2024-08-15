---
title: "Installation"
url: /ru/java/installation/
weight: 50
type: docs
---

## **Установка Aspose.Email для Java из репозитория Maven**
Aspose размещает все API Java на [Представьте себе артефактуру](https://releases.aspose.com/). Вы можете легко использовать [Aspose.Электронная почта для Java](https://releases.aspose.com/java/repo/com/aspose/aspose-email/) API прямо в ваших проектах Maven с простыми конфигурациями.
### **Укажите конфигурацию репозитория Maven**
Во-первых, вам нужно указать конфигурацию/местоположение репозитория Aspose Maven в вашем Maven pom.xml следующим образом:

``` java

 <repositories>

    <repository>

        <id>AsposeJavaAPI</id>

        <name>Aspose Java API</name>

        <url>https://releases.aspose.com/java/repo/</url>

    </repository>

</repositories>

```
### **Определение зависимости Aspose.Email от API Java**
Затем определите зависимость Aspose.Email для Java API в файле pom.xml следующим образом:

``` java

 <dependencies>

    <dependency>

        <groupId>com.aspose</groupId>

        <artifactId>aspose-email</artifactId>

        <version>19.12</version>

        <classifier>jdk16</classifier>

 </dependency>

</dependencies>

```

После выполнения вышеуказанных шагов зависимость Aspose.Email для Java наконец будет определена в вашем проекте Maven.
