---
title: "Совместимость с JDK 11"
url: /ru/java/compatibility-with-jdk-11/
weight: 210
type: docs
---


API Aspose.Email Ewsclient полностью совместим и может использоваться с JDK 11. Для работы с JDK 11 нам необходимо добавить зависимости JAXB. Все остальные API Aspose.Email должны работать нормально без дополнительных зависимостей.

{{% alert color="primary" %}}

API-интерфейсы JAXB считаются API Java EE и поэтому больше не содержатся в пути к классам по умолчанию в Java SE 9. В Java 11 они полностью удалены из JDK.

{{% /alert %}}


В проект должны быть добавлены следующие зависимости Maven JAXB:

~~~Java

 <dependency>

    <groupId>javax.xml.bind</groupId>

    <artifactId>jaxb-api</artifactId>

    <version>2.3.1</version>

</dependency>

<dependency>

    <groupId>com.sun.xml.bind</groupId>

    <artifactId>jaxb-impl</artifactId>

    <version>2.3.1</version>

</dependency>

<dependency>

    <groupId>com.sun.xml.bind</groupId>

    <artifactId>jaxb-core</artifactId>

    <version>2.3.0.1</version>

</dependency>

<dependency>

    <groupId>com.sun.xml.messaging.saaj</groupId>

    <artifactId>saaj-impl</artifactId>

    <version>1.5.0</version>

</dependency>

~~~
