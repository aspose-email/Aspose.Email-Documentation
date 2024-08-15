---
title: "Compatibilidad con JDK 11"
url: /es/java/compatibility-with-jdk-11/
weight: 210
type: docs
---


La API Aspose.Email EWSClient es totalmente compatible y se puede usar con JDK 11. Para trabajar con el JDK 11, necesitamos agregar dependencias de JAXB. Todas las demás API de Aspose.Email funcionarán normalmente sin dependencias adicionales.

{{% alert color="primary" %}}

Las API de JAXB se consideran API de Java EE y, por lo tanto, ya no figuran en la ruta de clases predeterminada de Java SE 9. En Java 11, se eliminan por completo del JDK.

{{% /alert %}}


Se añadirán al proyecto las siguientes dependencias JAXB de Maven:

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
