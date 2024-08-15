---
title: "Installation"
url: /es/java/installation/
weight: 50
type: docs
---

## **Instalación de Aspose.Email para Java desde el repositorio de Maven**
Aspose aloja todas las API de Java en [Apose Artifactory](https://releases.aspose.com/). Puedes usar fácilmente [Aspose.Email para Java](https://releases.aspose.com/java/repo/com/aspose/aspose-email/) API directamente en sus proyectos de Maven con configuraciones simples.
### **Especificar la configuración del repositorio de Maven**
En primer lugar, debe especificar la configuración/ubicación del repositorio Aspose Maven en su Maven pom.xml de la siguiente manera:

``` java

 <repositories>

    <repository>

        <id>AsposeJavaAPI</id>

        <name>Aspose Java API</name>

        <url>https://releases.aspose.com/java/repo/</url>

    </repository>

</repositories>

```
### **Definir Aspose.Email para la dependencia de la API de Java**
A continuación, defina Aspose.Email para la dependencia de la API de Java en su pom.xml de la siguiente manera:

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

Después de realizar los pasos anteriores, la dependencia de Aspose.Email para Java finalmente se definirá en su proyecto Maven.
