---
title: "Baixar e Configurar Aspose.Email em PHP"
url: /pt/java/download-and-configure-aspose-email-in-php/
weight: 10
type: docs
---

## **Baixar Bibliotecas Necessárias**
Baixe as bibliotecas necessárias mencionadas abaixo. Estas são necessárias para executar exemplos de Aspose.Email Java para PHP.

- **Aspose:** [Aspose.Email para Java Component](https://downloads.aspose.com/total)
- [PHP/Java Bridge](http://citylan.dl.sourceforge.net/project/php-java-bridge/Binary%20package/php-java-bridge_6.2.1/php-java-bridge_6.2.1_documentation.zip)
## **Baixar Exemplos de Sites de Codificação Social**
As seguintes versões de exemplos em execução estão disponíveis para download nos sites de codificação social mencionados abaixo:

-----
### **GitHub**
- **Aspose.Email Java para Exemplos PHP**
  - [Aspose.Email Java para PHP](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_Java_for_PHP)
### **CodePlex**
- **Aspose.Email Java para Exemplos PHP**
  - [Aspose.Email Java para PHP](https://archive.codeplex.com/?p=asposeemailjavaphp)
## **Como configurar o código-fonte na Plataforma Linux**
Siga estes passos simples para abrir e estender o código-fonte enquanto usa:
## **1. Instalar o Servidor Tomcat**
Para instalar o servidor tomcat, execute o seguinte comando no console linux. Isso instalará com sucesso o servidor tomcat.

``` actionscript3

 sudo apt-get install tomcat8

```
## **2. Baixar e Configurar PHP/JavaBridge**
Para baixar os binaries do PHP/JavaBridge, execute o seguinte comando no console linux.

``` actionscript3

  wget http://citylan.dl.sourceforge.net/project/php-java-bridge/Binary%20package/php-java-bridge_6.2.1/php-java-bridge_6.2.1_documentation.zip 

```


Descompacte os binaries do PHP/JavaBridge executando o seguinte comando no console linux.

``` actionscript3

  unzip -d php-java-bridge_6.2.1_documentation.zip 

```


Isso irá extrair o arquivo **JavaBridge.war**. Copie-o para a pasta **webapps** do tomcat8 executando o seguinte comando no console Linux.

``` actionscript3

  sudo cp JavaBridge.war /var/lib/tomcat8/webapps/JavaBridge.war 

```


Ao copiar, o tomcat8 criará automaticamente uma nova pasta "**JavaBridge**" em **webapps**. Depois que a pasta for criada, certifique-se de que seu tomcat8 está em execução e verifique <http://localhost:8080/JavaBridge> no navegador, deve abrir uma página padrão do JavaBridge.

Se alguma mensagem de erro aparecer, instale **FastCGI** executando o seguinte comando no console Linux.

``` actionscript3

  sudo apt-get install php55-cgi 

```

Depois de instalar o php5.5 cgi, reinicie o servidor tomcat8 e verifique <http://localhost:8080/JavaBridge> novamente no navegador.

Se o erro **JAVA_HOME** for exibido, abra o arquivo /etc/default/tomcat8 e descomente a linha que define o JAVA_HOME. Verifique <http://localhost:8080/JavaBridge> no navegador novamente, deve abrir a página de Exemplos PHP/JavaBridge.
## **3. Configurar Exemplos Aspose.Email Java para PHP**
Clone os exemplos PHP executando os seguintes comandos dentro da pasta webapps/JavaBridge.

``` actionscript3

 $ git init&nbsp;

$ git clone [https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_Java_for_PHP] 

```


## **Como configurar o código-fonte na Plataforma Windows**
Siga os passos simples abaixo para configurar o PHP/Java Bridge na Plataforma Windows

1. Instale o PHP5 e configure como de costume
2. Instale o JRE 6 (Java Runtime Environment) se você ainda não o tiver. Você pode verificar isso em C:\Program Files etc. Você pode baixá-lo aqui. Estou usando o JRE 6, pois é compatível com o PHP Java Bridge (PJB).

3. Instale o Apache Tomcat 8.0. Você pode baixá-lo aqui.

4. Baixe [JavaBridge.war](https://sourceforge.net/projects/php-java-bridge/files/Binary%20package/php-java-bridge_6.2.1/JavaBridgeTemplate621.war/download). Copie este arquivo para o diretório webapps do tomcat.
(ex: `C:\Program Files\Apache Software Foundation\Tomcat 8.0\webapps` )

5. Reinicie o serviço apache tomcat.

6. Vá para <http://localhost:8080/JavaBridge/test.php> para verificar se o php funciona. Você pode encontrar outros exemplos lá.

7. Copie seu arquivo jar [Aspose.Email Java](https://downloads.aspose.com/total) para `C:\Program Files\Apache Software Foundation\Tomcat 8.0\webapps\JavaBridge\WEB-INF\lib`.

8. Clone os exemplos [Aspose.Email Java para PHP](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose.Email-for-Java_for_PHP) dentro da pasta `C:\Program Files\Apache Software Foundation\Tomcat 8.0\webapps\`.

9. Copie a pasta `C:\Program Files\Apache Software Foundation\Tomcat 8.0\webapps\JavaBridge\java` para sua pasta de exemplos Aspose.Email Java para PHP.

10. Reinicie o serviço apache tomcat e comece a usar os exemplos.