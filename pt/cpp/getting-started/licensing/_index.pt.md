---
title: "Licenciamento"
description: "Avaliar a API do Email C++ Library e aplicar licença usando arquivo ou objeto de fluxo."
url: /pt/cpp/licensing/
weight: 60
type: docs
---

## **Limitações da Versão de Avaliação**
Uma versão de avaliação gratuita do Aspose.Email para C++ pode ser baixada na seção de downloads do site da Aspose em: https://releases.aspose.com/email/cpp/

## **Aplicar Licença usando Objeto de Arquivo ou Fluxo**
A licença pode ser carregada de um arquivo ou objeto de fluxo. Aspose.Email para C++ tentará encontrar a licença nos seguintes locais:

1. Caminho explícito.
2. A pasta que contém Aspose.Cells.dll.
3. A pasta que contém o assembly que chamou Aspose.Cells.dll.
4. A pasta que contém o assembly de entrada (seu .exe).
5. Um recurso incorporado no assembly que chamou Aspose.Cells.dll.

A maneira mais fácil de definir uma licença é colocar o arquivo de licença na mesma pasta que o arquivo Aspose.Email.dll e especificar apenas o nome do arquivo, sem um caminho, como mostrado no exemplo abaixo.
### **Carregando uma Licença de um Arquivo**
A maneira mais fácil de aplicar uma licença é colocar o arquivo de licença na mesma pasta que o arquivo Aspose.Email.dll e especificar apenas o nome do arquivo sem um caminho.

{{% alert color="primary" %}} 

Quando você chamar o método SetLicense, o nome da licença que você passar deve ser o do arquivo de licença. Por exemplo, se você mudar o nome do arquivo de licença para "Aspose.Email.lic", passe esse nome de arquivo para o método Emails->SetLicense(…).

{{% /alert %}} 

**C++**

``` cs

 intrusive_ptr<License> license = new License();

license->SetLicense(new String("Aspose.Email.lic"));

```
### **Carregando uma Licença de um Objeto de Fluxo**
O seguinte exemplo mostra como carregar uma licença de um fluxo.

**C++**

``` cs

 intrusive_ptr<License>license = new License();

intrusive_ptr<FileStream> myStream = new FileStream(new String("Aspose.Email.lic"), FileMode_Open);

license->SetLicense(myStream);

```