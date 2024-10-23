---
title: "Baixar e Configurar Aspose.Email em Ruby"
url: /pt/java/download-and-configure-aspose-email-in-ruby/
weight: 10
type: docs
---


## **Baixar Bibliotecas Necessárias**
Baixe as bibliotecas necessárias mencionadas abaixo. Estas são necessárias para executar exemplos do Aspose.Email Java para Ruby.

- [Aspose.Email for Java Component](https://downloads.aspose.com/total)
## **Baixar Exemplos de Sites de Codificação Social**
As seguintes versões de exemplos em execução estão disponíveis para download nos sites de codificação social mencionados abaixo:

**GitHub**

- [Aspose.Email Java for Ruby](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_Java_for_Ruby)
## **Instalação**
É muito simples e fácil instalar a gem Aspose.Email Java para Ruby, por favor, siga estas etapas simples:

1. Execute o seguinte comando.

``` java

 $ gem install aspose-emailjava

```

1. Baixe o componente Aspose.Email for Java necessário pelo link a seguir.
   <https://downloads.aspose.com/total>
1. Crie uma pasta "jars" na raiz da gem Aspose.Email Java para Ruby e copie o componente baixado para ela.
## **Usando**
Inclua os arquivos necessários para trabalhar com o exemplo **createnewemail**.

``` java

 require File.dirname(File.dirname(File.dirname(__FILE__))) + '/lib/aspose-emailjava'

include Asposeemailjava

include Asposeemailjava::CreateNewEmail

initialize_aspose_email

```

Vamos entender o código acima.

1. A primeira linha garante que o aspose email está carregado e disponível.
1. Inclua os arquivos que são necessários para acessar o aspose email.
1. Inicialize as bibliotecas. As classes aspose JAVA são carregadas do caminho fornecido no arquivo aspose.yml.