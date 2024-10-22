---
title: "Cómo Ejecutar los Ejemplos"
url: /es/net/how-to-run-the-examples/
weight: 90
type: docs
---


## **Requisitos de Software**
Asegúrate de cumplir con los siguientes requisitos antes de descargar y ejecutar los ejemplos.

1. Visual Studio 2010 o superior
1. NuGet Package Manager instalado en Visual Studio. Asegúrate de que la última versión de la API de NuGet esté instalada en Visual Studio. Para más detalles sobre cómo instalar el administrador de paquetes NuGet, consulta <https://docs.microsoft.com/en-us/nuget/install-nuget-client-tools>
1. Ve a Herramientas->Opciones->Administrador de paquetes NuGet->Fuentes de paquetes y asegúrate de que la opción **nuget.org** esté marcada
1. El proyecto de ejemplo utiliza la característica de Restauración Automática de Paquetes de NuGet, por lo tanto, debes tener una conexión a Internet activa.
## **Descargar de GitHub**
Todos los ejemplos de Aspose.Font para .NET se alojan en [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET).

- Puedes clonar el repositorio usando tu cliente de GitHub favorito o descargar el archivo ZIP desde [aquí](https://docs.microsoft.com/en-us/nuget/install-nuget-client-tools).
- Extrae el contenido del archivo ZIP en cualquier carpeta de tu computadora. Todos los ejemplos están ubicados en la carpeta **Examples**.
- Los proyectos se crean en Visual Studio 2013, pero los archivos de solución son compatibles con Visual Studio 2010 SP1 y superior.
- Abre el archivo de solución en Visual Studio y compila el proyecto.
- En la primera ejecución, las dependencias se descargarán automáticamente a través de NuGet.
- La carpeta **Data** en la carpeta raíz de **Examples** contiene archivos de entrada. Es obligatorio que descargues la carpeta **Data** junto con el proyecto de ejemplos.
- Abre RunExamples.cs, todos los ejemplos se llaman desde aquí.
- Descomenta los ejemplos que deseas ejecutar dentro del proyecto.

No dudes en contactarnos a través de nuestros foros si tienes algún problema al configurar o ejecutar los ejemplos.
## **Contribuir**
Si te gustaría agregar o mejorar un ejemplo, te animamos a contribuir al proyecto. Todos los ejemplos y proyectos de exhibición en este repositorio son de código abierto y se pueden usar libremente en tus propias aplicaciones.

Para contribuir, puedes bifurcar el repositorio, editar el código fuente y crear una solicitud de extracción. Revisaremos los cambios e iremos incluidos en el repositorio si se consideran útiles.