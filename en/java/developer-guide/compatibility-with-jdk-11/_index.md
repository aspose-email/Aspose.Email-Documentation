---
title: Compatibility with JDK 11
ArticleTitle: Compatibility with JDK 11
type: docs
weight: 210
url: /java/compatibility-with-jdk-11/
---


Aspose.Email EWSClient API is fully compatible and it can be used with JDK 11. For working with JDK 11, we need to add JAXB dependencies. All other Aspose.Email API shall work normally without any additional dependencies.

{{% alert color="primary" %}} 

The JAXB APIs are considered to be Java EE APIs, and therefore are no longer contained on the default class path in Java SE 9. In Java 11 they are completely removed from the JDK.

{{% /alert %}} 


The following Maven JAXB dependencies shall be added to the project:

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
