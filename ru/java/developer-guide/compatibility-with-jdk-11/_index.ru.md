---
title: "Совместимость с JDK 11"
url: /ru/java/compatibility-with-jdk-11/
weight: 210
type: docs
---


Aspose.Email EWSClient API полностью совместим и может использоваться с JDK 11. Для работы с JDK 11 необходимо добавить зависимости JAXB. Все остальные API Aspose.Email будут работать нормально без каких-либо дополнительных зависимостей.

{{% alert color="primary" %}} 

API JAXB считаются API Java EE, и, следовательно, больше не содержатся в стандартном классовом пути в Java SE 9. В Java 11 они полностью удалены из JDK.

{{% /alert %}} 


Следующие зависимости Maven JAXB должны быть добавлены в проект:

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