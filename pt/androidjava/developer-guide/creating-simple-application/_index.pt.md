---
title: "Criando Aplicação Simples"
url: /pt/androidjava/criando-aplicacao-simples/
weight: 10
type: docs
---

## **Como usar Aspose.Email para Android via Java**
Este tópico irá guiá-lo através dos passos necessários para configurar o Aspose.Email para Android via Java no IDE Android Studio, assumindo que você já tem a versão mais recente do Android Studio instalada em sua máquina e que também adquiriu a versão mais recente do pacote Aspose.Email para Android via Java.

{{% alert color="primary" %}} 

Se você ainda não instalou o Android Studio, primeiro deve adquirir o instalador do Android Studio e instalá-lo em sua máquina. Você pode baixar a versão mais recente do Android Studio [ aqui ](https://developer.android.com/studio/index.html#win-bundle), enquanto os detalhes sobre como instalar o IDE estão disponíveis [ aqui](https://developer.android.com/studio/install.html).

{{% /alert %}} {{% alert color="primary" %}} 

O pacote Aspose.Email para Android via Java pode ser baixado [ aqui](https://downloads.aspose.com/email/androidjava). Por favor, note que cada pacote de lançamento do Aspose.Email para Android via Java consiste principalmente de 2 arquivos, conforme detalhado abaixo.

- aspose-email-x.x.x.jar é o arquivo da biblioteca principal que contém todos os namespaces da API Aspose.Email para Android via Java.
- aspose-email-x.x.x-libs.apk é o APK que contém o jar bcprov-jdk15-146.jar de terceiros utilizado para as funcionalidades de criptografia e descriptografia oferecidas pela API Aspose.Email para Android via Java.

{{% /alert %}} 
## **Começando com Aspose.Email para Android via Java no Android Studio**
Uma vez que o IDE Android Studio carrega, clique em File > New > New Project, conforme mostrado abaixo.

![todo:image_alt_text](run_examples_1.png)

Você também pode criar um novo projeto a partir da tela de boas-vindas do Android Studio, conforme mostrado abaixo.

![todo:image_alt_text](run_examples_2.png)

Em seguida, você será solicitado a especificar o nome da aplicação, domínio e local para armazenar os arquivos do projeto. Você pode escolher alterar os valores padrão conforme sua preferência ou deixá-los como estão e clicar em Next.

![todo:image_alt_text](run_examples_3.png)

No próximo passo, você deve especificar o dispositivo Android em que deseja hospedar/executar sua aplicação. Uma vez selecionado, clique no botão Next.

![todo:image_alt_text](run_examples_4.png)

Agora você precisa selecionar a Activity de uma lista pré-definida de templates. Para manter a demonstração simples, selecionamos o template Empty Activity, conforme mostrado abaixo.

![todo:image_alt_text](run_examples_5.png)

Clique no botão Finish na caixa de diálogo Customize the Activity, pois manteremos todas as configurações padrão como estão.

![todo:image_alt_text](run_examples_6.png)

Assim que você clicar no botão Finish no passo anterior, o IDE começará a construir o projeto, conforme mostrado abaixo. Deixe-o terminar ou clique no botão Cancel.

![todo:image_alt_text](run_examples_7.png)

Agora o projeto foi carregado no IDE, no entanto, você pode desejar mudar a visualização para Project para que possa visualizar a hierarquia completa dos arquivos do projeto. Para mudar a visualização, verifique a captura a seguir.

![todo:image_alt_text](run_examples_8.png)

Após mudar a visualização para Project, encontre e carregue o arquivo build.gradle no editor e cole o seguinte snippet, conforme mostrado abaixo.

~~~Java

 dexOptions{

    javaMaxHeapSize "4g"

}

~~~

![todo:image_alt_text](run_examples_9.png)

Em seguida, vamos adicionar o Aspose.Email para Android via Java Jar ao projeto. Existem 2 passos importantes, conforme detalhado abaixo.

- Copie manualmente o Aspose.Email para Android via Java Jar para a pasta \app\libs.
- Adicione o Aspose.Email para Android via Java Jar como Biblioteca ao módulo, conforme mostrado abaixo.

![todo:image_alt_text](run_examples_10.png)

Você será solicitado a selecionar o módulo ao qual deseja adicionar o Aspose.Email para Java.Android Jar como biblioteca. Por favor, escolha adequadamente e clique em OK.

![todo:image_alt_text](run_examples_11.png)

Você também precisa adicionar o arquivo APK ao projeto. Você deve copiar o APK para a pasta \app\src\main\assets. Se você não tiver a pasta assets dentro da pasta main, pode criar uma clicando com o botão direito do mouse no nó main na visualização do Projeto. Selecione New > Folder > Asset Folder.

![todo:image_alt_text](run_examples_12.png)

Uma vez que o APK tenha sido adicionado ao projeto, ele precisa ser carregado pelo projeto. Existem 2 maneiras de carregar o APK, conforme segue.

- Carregue o APK em uma classe de aplicação personalizada usando o snippet fornecido abaixo e registre a classe de aplicação personalizada no AndroidManifest.xml.

~~~Java

 LibsLoadHelper.loadLibs(this);

~~~

- Carregue o APK no método OnCreate da MainActivity.

~~~Java

 LibsLoadHelper.loadLibs(getApplicationContext());

~~~

Agora estamos prontos para escrever o código. Para manter a demonstração fácil de entender, adicionamos um widget Button ao layout e vamos tratar seu evento de clique da seguinte forma.

~~~Java

private class TestEmail extends AsyncTask<Void, String, Boolean> 

{

    @Override

    protected Boolean doInBackground(Void... params) 

    {

        Boolean result = false;

        try 

        {

            //Crie uma instância de PersonalStorage

            com.aspose.email.PersonalStorage pst = com.aspose.email.PersonalStorage.create("newSample_out.pst", 0);

            //Crie uma pasta na raiz do PST

            pst.getRootFolder().addSubFolder("myInbox");

            //Adicione uma mensagem à pasta recém-criada

            pst.getRootFolder().getSubFolder("myInbox").addMessage(com.aspose.email.MapiMessage.fromFile("message.msg"));

        } 

        catch (Exception e) 

        {

            e.printStackTrace();

        }

        return result;

    }

}

~~~

Quando você executar a aplicação usando o botão play na interface do IDE (ou usando SHIFT + F10), o emulador carregará a aplicação, conforme mostrado abaixo.

![todo:image_alt_text](run_examples_13.png)

Clicando no botão no emulador, o código será executado.