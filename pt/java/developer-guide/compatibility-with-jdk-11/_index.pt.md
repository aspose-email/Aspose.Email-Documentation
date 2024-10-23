---
title: "Compatibilidade com JDK 11"
url: /pt/java/compatibilidade-com-jdk-11/
weight: 210
type: docs
---


A API Aspose.Email EWSClient é totalmente compatível e pode ser usada com JDK 11. Para trabalhar com JDK 11, precisamos adicionar dependências JAXB. Todas as outras APIs Aspose.Email funcionarão normalmente sem dependências adicionais.

{{% alert color="primary" %}} 

As APIs JAXB são consideradas APIs Java EE e, portanto, não estão mais contidas no caminho de classe padrão no Java SE 9. No Java 11, elas foram completamente removidas do JDK.

{{% /alert %}} 


As seguintes dependências Maven JAXB devem ser adicionadas ao projeto:

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