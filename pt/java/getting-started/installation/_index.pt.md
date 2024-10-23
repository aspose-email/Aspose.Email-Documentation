---
title: "Instalação"
url: /pt/java/installation/
weight: 50
type: docs
---

## **Instalando Aspose.Email para Java do Repositório Maven**
Aspose hospeda todas as APIs Java no [Aspose Artifactory](https://releases.aspose.com/). Você pode usar facilmente a API [Aspose.Email para Java](https://releases.aspose.com/java/repo/com/aspose/aspose-email/) diretamente em seus Projetos Maven com configurações simples.
### **Especificar Configuração do Repositório Maven**
Primeiro, você precisa especificar a configuração/localização do Repositório Maven Aspose em seu pom.xml da seguinte maneira:

``` java

 <repositories>

    <repository>

        <id>AsposeJavaAPI</id>

        <name>Aspose Java API</name>

        <url>https://releases.aspose.com/java/repo/</url>

    </repository>

</repositories>

```
### **Definir Dependência da API Aspose.Email para Java**
Em seguida, defina a dependência da API Aspose.Email para Java em seu pom.xml da seguinte maneira:

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

Após realizar os passos acima, a dependência Aspose.Email para Java será finalmente definida em seu Projeto Maven.