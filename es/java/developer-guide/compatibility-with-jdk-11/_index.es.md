---
title: "Compatibilidad con JDK 11"
url: /es/java/compatibility-with-jdk-11/
weight: 210
type: docs
---


La API Aspose.Email EWSClient es completamente compatible y se puede usar con JDK 11. Para trabajar con JDK 11, necesitamos agregar las dependencias de JAXB. Todas las demás API de Aspose.Email funcionarán normalmente sin ninguna dependencia adicional.

{{% alert color="primary" %}} 

Las API de JAXB se consideran API de Java EE, y por lo tanto ya no están contenidas en la ruta de clase por defecto en Java SE 9. En Java 11 se eliminan por completo del JDK.

{{% /alert %}} 


Las siguientes dependencias de Maven JAXB deben ser agregadas al proyecto:

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