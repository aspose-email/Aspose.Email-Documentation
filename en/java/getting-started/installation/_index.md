---
title: Installation
ArticleTitle: Installation
type: docs
weight: 50
url: /java/installation/
---

## **Installing Aspose.Email for Java from Maven Repository**
Aspose hosts all Java APIs on [Aspose Artifactory](https://releases.aspose.com/). You can easily use [Aspose.Email for Java](https://releases.aspose.com/java/repo/com/aspose/aspose-email/) API directly in your Maven Projects with simple configurations.
### **Specify Maven Repository Configuration**
First, you need to specify the Aspose Maven Repository configuration/location in your Maven pom.xml as follows:

``` java

 <repositories>

    <repository>

        <id>AsposeJavaAPI</id>

        <name>Aspose Java API</name>

        <url>https://releases.aspose.com/java/repo/</url>

    </repository>

</repositories>

```
### **Define Aspose.Email for Java API Dependency**
Then define Aspose.Email for Java API dependency in your pom.xml as follows:

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

After performing the above steps, Aspose.Email for Java dependency will finally be defined in your Maven Project.
