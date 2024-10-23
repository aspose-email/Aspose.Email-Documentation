---
title: "Como Executar os Exemplos"
url: /pt/androidjava/como-executar-os-exemplos/
weight: 70
type: docs
---

## **Baixar do GitHub**
Todos os exemplos do Aspose.Email para Java estão hospedados no [Github](https://github.com/aspose-email/Aspose.Email-for-Java). Você pode clonar o repositório usando seu cliente favorito do Github ou baixar o arquivo ZIP [aqui](https://forum.aspose.com/c/email/12).

Extraia o conteúdo do arquivo ZIP para qualquer pasta no seu computador. Todos os exemplos estão localizados na pasta **Examples**.

![todo:image_alt_text](https://i.imgur.com/WsQ2wrb.png)

O projeto utiliza o sistema de build Maven. Qualquer IDE moderna pode facilmente abrir ou importar o projeto e suas dependências. Abaixo, mostramos como usar IDEs populares para construir e executar os exemplos.

## **Como usar Aspose.Email para Android via Java**
Este tópico guiará você pelos passos necessários para configurar o Aspose.Email para Android via Java no IDE Android Studio, assumindo que você já tenha a versão mais recente do Android Studio instalada em sua máquina e também adquiriu a versão mais recente do pacote Aspose.Email para Android via Java.

{{% alert color="primary" %}} 

Se você ainda não instalou o Android Studio, primeiro precisa adquirir a instalação do Android Studio e instalá-lo em sua máquina. Você pode baixar a versão mais recente do Android Studio [aqui](https://developer.android.com/studio/index.html#win-bundle), enquanto os detalhes sobre como instalar o IDE estão disponíveis [aqui](https://developer.android.com/studio/install.html).

{{% /alert %}} {{% alert color="primary" %}} 

O pacote Aspose.Email para Android via Java pode ser baixado [aqui](https://downloads.aspose.com/email/androidjava). Por favor, note que cada pacote de lançamento do Aspose.Email para Android via Java consiste principalmente de 2 arquivos, conforme detalhado abaixo.

- aspose-email-x.x.x.jar é o arquivo principal da biblioteca que contém todos os namespaces da API Aspose.Email para Android via Java.
- aspose-email-x.x.x-libs.apk é o APK que contém o bcprov-jdk15-146.jar de terceiros, utilizado para as facilidades de criptografia e descriptografia oferecidas pela API Aspose.Email para Android via Java.

{{% /alert %}} 
## **Introdução ao Aspose.Email para Android via Java no Android Studio**
Uma vez que o IDE Android Studio é carregado, clique em Arquivo > Novo > Novo Projeto, conforme mostrado abaixo.

![todo:image_alt_text](run_examples_1.png)

Você também pode criar um novo projeto a partir da Tela de Boas-Vindas do Android Studio, conforme mostrado abaixo.

![todo:image_alt_text](run_examples_2.png)

Em seguida, você será solicitado a especificar o nome da aplicação, domínio e local para armazenar os arquivos do projeto. Você pode optar por alterar os valores padrão conforme sua escolha ou deixá-los como estão e clicar em Avançar.

![todo:image_alt_text](run_examples_3.png)

Na próxima etapa, você deve especificar o Dispositivo Android que deseja hospedar/executar sua aplicação. Uma vez selecionado, clique no botão Avançar.

![todo:image_alt_text](run_examples_4.png)

Agora você precisa selecionar a Atividade a partir de uma lista pré-definida de templates. Para manter a demonstração simples, selecionamos o template de Atividade Vazia, conforme mostrado abaixo.

![todo:image_alt_text](run_examples_5.png)

Clique no botão Concluir na caixa de diálogo Personalizar a Atividade, pois manteremos todas as configurações padrão como estão.

![todo:image_alt_text](run_examples_6.png)

Assim que você clica no botão Concluir na etapa anterior, o IDE começará a construir o projeto, conforme mostrado abaixo. Deixe-o terminar ou clique no botão Cancelar.

![todo:image_alt_text](run_examples_7.png)

Agora o projeto foi carregado no IDE, no entanto, você pode querer mudar a visualização para Projeto para que consiga ver toda a hierarquia dos arquivos do projeto. Para mudar a visualização, veja a seguinte captura de tela.

![todo:image_alt_text](run_examples_8.png)

Após mudar a visualização para Projeto, encontre e carregue o arquivo build.gradle no editor e cole o seguinte trecho, conforme mostrado abaixo.

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

Você será solicitado a selecionar o módulo ao qual deseja adicionar o Aspose.Email para Java.Android Jar como biblioteca. Por favor, escolha apropriadamente e clique em OK.

![todo:image_alt_text](run_examples_11.png)

Você também precisa adicionar o arquivo APK ao projeto. Você deve copiar o APK para a pasta \app\src\main\assets. Se você não tiver a pasta assets na pasta principal, pode criar uma clicando com o botão direito no nó principal na visualização do Projeto. Selecione Novo > Pasta > Pasta de Asset.

![todo:image_alt_text](run_examples_12.png)

Uma vez que o APK tenha sido adicionado ao projeto, ele precisa ser carregado pelo projeto. Existem 2 maneiras de carregar o APK, conforme segue.

- Carregue o APK em uma classe de aplicação personalizada usando o trecho fornecido abaixo e registre a classe de aplicação personalizada no AndroidManifest.xml.

~~~Java

 LibsLoadHelper.loadLibs(this);

~~~

- Carregue o APK no método OnCreate de MainActivity.

~~~Java

 LibsLoadHelper.loadLibs(getApplicationContext());

~~~

Agora estamos prontos para usar o código do arquivo de exemplos.

## **Contribuir**
Se você gostaria de adicionar ou melhorar um exemplo, encorajamos você a contribuir para o projeto. Todos os exemplos e projetos de demonstração neste repositório são open source e podem ser usados livremente em suas próprias aplicações.

Para contribuir, você pode bifurcar o repositório, editar o código-fonte e criar um pull request. Revisaremos as alterações e as incluiremos no repositório se forem consideradas úteis.