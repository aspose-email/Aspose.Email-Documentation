---
title: "Instalación"
url: /es/java/installation/
weight: 50
type: docs
---

## **Instalación de Aspose.Email para Java desde el Repositorio de Maven**
Aspose aloja todas las API de Java en [Aspose Artifactory](https://releases.aspose.com/). Puedes utilizar fácilmente la API de [Aspose.Email para Java](https://releases.aspose.com/java/repo/com/aspose/aspose-email/) directamente en tus proyectos Maven con configuraciones simples.
### **Especificar la Configuración del Repositorio de Maven**
Primero, necesitas especificar la configuración/ubicación del Repositorio Maven de Aspose en tu archivo pom.xml de la siguiente manera:

``` java

 <repositories>

    <repository>

        <id>AsposeJavaAPI</id>

        <name>API de Aspose Java</name>

        <url>https://releases.aspose.com/java/repo/</url>

    </repository>

</repositories>

```
### **Definir la Dependencia de la API de Aspose.Email para Java**
Luego define la dependencia de la API de Aspose.Email para Java en tu pom.xml de la siguiente manera:

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

Después de realizar los pasos anteriores, la dependencia de Aspose.Email para Java estará finalmente definida en tu proyecto Maven.