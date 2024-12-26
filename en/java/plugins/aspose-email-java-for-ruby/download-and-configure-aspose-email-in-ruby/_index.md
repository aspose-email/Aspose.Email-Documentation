---
title: Download and Configure Aspose.Email in Ruby
ArticleTitle: Download and Configure Aspose.Email in Ruby
type: docs
weight: 10
url: /java/download-and-configure-aspose-email-in-ruby/
---


## **Download Required Libraries**
Download required libraries mentioned below. These are the required for executing Aspose.Email Java for Ruby examples.

- [Aspose.Email for Java Component](https://downloads.aspose.com/total)
## **Download Examples from Social Coding Sites**
Following releases of running examples are available to download on below mentioned social coding sites:

**GitHub**

- [Aspose.Email Java for Ruby](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_Java_for_Ruby)
## **Installing**
It is very simple and easy to install Aspose.Email Java for Ruby gem, please follow these simple steps:

1. Run following command. 

``` java

 $ gem install aspose-emailjava

```

1. Download required Aspose.Email for Java Component from following link.
   <https://downloads.aspose.com/total>
1. Create "jars" folder at root of the Aspose.Email Java for Ruby gem and copy downloaded component into it.
## **Using**
Include the required files for working with the **createnewemail** example.

``` java

 require File.dirname(File.dirname(File.dirname(__FILE__))) + '/lib/aspose-emailjava'

include Asposeemailjava

include Asposeemailjava::CreateNewEmail

initialize_aspose_email

```

Let's understand the above code.

1. The first line makes sure that the aspose email is loaded and available.
1. Include the files that are required to access the aspose email.
1. Initialize the libraries. The aspose JAVA classes are loaded from the path provided in the aspose.yml file
