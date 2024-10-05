---
title: Установка
type: docs
weight: 50
url: /java/installation/
---

## **Установка Aspose.Email для Java из репозитория Maven**
Aspose размещает все Java API в [Aspose Artifactory](https://releases.aspose.com/). Вы можете легко использовать [Aspose.Email для Java](https://releases.aspose.com/java/repo/com/aspose/aspose-email/) API непосредственно в ваших проектах Maven с простыми конфигурациями.
### **Укажите конфигурацию репозитория Maven**
Сначала вам нужно указать конфигурацию/расположение репозитория Aspose Maven в вашем файле pom.xml следующим образом:

``` java

 <repositories>

    <repository>

        <id>AsposeJavaAPI</id>

        <name>Aspose Java API</name>

        <url>https://releases.aspose.com/java/repo/</url>

    </repository>

</repositories>

```
### **Определите зависимость Aspose.Email для Java API**
Затем определите зависимость Aspose.Email для Java API в вашем pom.xml следующим образом:

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

После выполнения вышеуказанных шагов зависимость Aspose.Email для Java будет окончательно определена в вашем проекте Maven.