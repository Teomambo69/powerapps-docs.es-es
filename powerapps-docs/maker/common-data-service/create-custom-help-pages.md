---
title: Cree páginas de ayuda personalizadas | MicrosoftDocs
description: Cree páginas de ayuda personalizadas en UCI
ms.custom: ''
ms.date: 09/13/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: ''
caps.latest.revision: ''
author: matthewbolanos
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0ba852565acee10fc4c853eb185f552df6399fc9
ms.sourcegitcommit: d98dd90a7dda11f434a13a7f8976459856d6142b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/29/2020
ms.locfileid: "3093924"
---
# <a name="create-guided-help-for-your-unified-interface-app"></a>Crear ayuda guiada para la aplicación de la Interfaz unificada

[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Use paneles de ayuda personalizados y tareas guiadas de dar a su aplicación de la Interfaz unificada una experiencia de ayuda personalizada en el producto que esté adaptada a su organización. Use paneles de ayuda personalizados para proporcionar asistencia y orientación específicas de la entidad, formulario, e idioma que incluyan texto enriquecido, vínculos de contenido, imágenes, y vínculos de vídeos. 

> [!IMPORTANT]
> Los paneles de ayuda personalizados reemplazan la característica de aprendizaje guiado de la ruta de aprendizaje anterior usada en aplicaciones del cliente web heredadas.

## <a name="custom-help-panes-and-learning-path"></a>Paneles de ayuda personalizados y ruta de aprendizaje
La nueva implementación de ayuda guiada de paneles de ayuda personalizados se diferencia de la característica de ayuda guiada de la ruta de aprendizaje anterior. Ambas características permiten crear la ayuda personalizada para su aplicación. Sin embargo, los paneles de ayuda personalizados están optimizados para los escenarios de ayuda guiada más comunes.   

Los paneles de ayuda personalizados proporcionan las características clave siguientes que no están disponibles con ruta de aprendizaje: 
- Texto enriquecido de forma libre, incluidas viñetas y numeración.
- Marcas de formación y globos de ayuda vinculados visiblemente.
- Más opciones de orígenes de vídeo, incluidos orígenes privados.
- Almacenamiento de contenido de ayuda en Common Data Service como parte de la solución. 

Los paneles de ayuda personalizados no proporcionan las características clave siguientes que están disponibles con ruta de aprendizaje: 
- Globos de ayuda secuenciales.
- Páginas de ayuda por rol.
- Páginas de ayuda para factor de forma por dispositivo, como smartphones. 

## <a name="prerequisites"></a>Requisitos previos 
Para crear paneles personalizados de ayuda, necesita el siguiente: 
- Versión 9.1.0.10300 o posterior.
- Permisos globales para crear, leer, escribir, eliminar, anexar, y anexar a en el privilegio **Página de ayuda**. De forma predeterminada, los roles de seguridad Administrador del sistema y Personalizador del sistema tienen este privilegio.  
- [El entorno debe tener paneles personalizados de Ayuda habilitados.](#enable-custom-help-panes-for-your-environment)

## <a name="enable-custom-help-panes-for-your-environment"></a>Habilitar paneles de Ayuda personalizados para el entorno
1. Abra una aplicación basada en modelo y en la barra de comandos seleccione **Configuración** ![Configuración](../model-driven-apps/media/powerapps-gear.png) > **Configuración avanzada**.
2. Vaya a **Configuración** > **Sistema** > **Administración**.  
3. En la página **Administración**, seleccione **Configuración del sistema**.
4. En la pestaña **General** , en **Establecer la URL de la Ayuda personalizada**, seleccione **Sí** para **Habilitar tareas guiadas y paneles de ayuda personalizados** y después seleccione **Aceptar**.

    > [!div class="mx-imgBorder"] 
    > ![Habilitar paneles de ayuda personalizados](media/enable-custom-help-panes.png "Habilitar paneles de ayuda personalizados")

> [!IMPORTANT]
> Puede habilitar paneles de ayuda personalizados o ayuda personalizable pero no ambos al mismo tiempo. Confirme que **Usar la Ayuda personalizada para entidades personalizables** y **Anexar los parámetros a la URL** están establecidos en **No**.  
 
## <a name="context-sensitive-custom-help"></a>Ayuda personalizada contextual
Cada panel de ayuda es único para estos contextos: 
- Aplicación 
- Entidad
- Formulario 
- Language   

## <a name="help-pane-navigation"></a>Navegación por el panel de ayuda
De forma predeterminada, un panel de ayuda se mantiene abierto en el contenido de ayuda con el que lo abrió la primera vez incluso cuando navega a otro formulario. Esto permite que el contenido de ayuda se mantenga intacto mientras lleva a los usuarios a diferentes partes de la aplicación. 

### <a name="to-author-help-pane-content"></a>Para crear contenido del panel de ayuda
1.  Para ver el panel de ayuda, abra una aplicación basada en modelo y, a continuación, en la barra de comandos seleccione **Ayuda**. 

    ![Ayuda](media/help-command.png)   
2.  En el panel de Ayuda, seleccione los puntos suspensivos verticales y, a continuación seleccione **Editar**. 

    ![Editar ayuda](media/help-edit-command.png)
    
    El panel de ayuda ahora está en modo de edición y cursor se coloca en el título del panel de ayuda.
3.  Desde el panel de edición puede realizar las siguientes tareas: 
    - Escriba texto escribiendo directamente en el área del panel de ayuda. 
    - Dé formato al texto mediante los comandos de texto enriquecido, como negrita, cursiva, tachado y cree listas. 
    - Seleccione la pestaña **Insertar** para agregar secciones, vídeo, imágenes, vínculos, marcas de formación y ayuda de globo. 
<!-- confirm the image is safe for use
    > [!div class="mx-imgBorder"] 
    > ![Custom help pane edit](media/custom-help-pane-edit.png)  -->
4.  Seleccione **Guardar** para guardar los cambios.  

### <a name="free-form-text"></a>Texto de forma libre
El texto se puede colocar en cualquier lugar dentro del panel de ayuda. Escriba texto de forma libre antes, dentro o después de secciones. El texto admite formatos de fuente de negrita, cursiva, subrayado y tachado. También puede usar cortar, copiar y pegar así como deshacer multinivel. 

### <a name="bullets-and-numbered-lists"></a>Viñetas y listas numeradas
La selección del icono de viñeta o número activa y desactiva la línea actual para convertirla en viñetas o numerarla. Si ha seleccionado varias líneas en una lista, cada línea se convierte en viñetas o se numera. Tabulación y aplicación de sangría a subnúmeros en una línea de la lista.  

### <a name="sections"></a>Secciones
Una sección es un cuadro de texto contraíble.  Puede colocar vínculos o texto de forma libre en ella. Use una sección para agrupar elementos similares. Una sección puede estar abierta o contraída de forma predeterminada. 

### <a name="video-and-static-images"></a>Imágenes de vídeo y estáticas
Puede insertar vídeos e imágenes estáticas en el panel de ayuda. Los vídeos y las imágenes son vínculos al contenido en Internet. Los paneles de ayuda personalizados no almacenan archivos de vídeo y de imagen en el panel de ayuda. Cuando se abre el panel de la ayuda, los paneles personalizados de la ayuda llevan el contenido del vínculo para mostrarlo. Puede usar un vínculo a un vídeo de Microsoft Stream si desea hacer referencia al contenido corporativo privado. 

> [!TIP]
> Recuerde copiar la dirección URL del vínculo para el vídeo o la imagen que desee para poder pegarlo en el panel de ayuda. 

Los paneles personalizados de ayuda admiten los orígenes de vídeo siguientes:
- Microsoft Stream (uso para contenido privado) 
- YouTube
- Facebook
- Vimeo


### <a name="links"></a>Vínculos
Los vínculos pueden ser a páginas web y abrirse en la misma ventana (la predeterminada) o abrirse en una ventana independiente. La capacidad de vincularlos a una página de ayuda existente aún no está habilitada.   

### <a name="balloons-and-coach-marks"></a>Globos y marcas de formación
Los globos y marcas de formación se pueden usar para apuntar elementos específicos de la interfaz de usuario. Un globo puede tener texto. Una marca de formación resalta simplemente un elemento con un puntero de formación. Una forma de mostrar varios elementos de la interfaz de usuario secuencialmente es obtener simplemente vínculos en una lista que el usuario puede seleccionar. Por ejemplo:

1. Vincule al primer elemento de la interfaz de usuario con instrucciones o comentarios.
2. Vincule al segundo elemento de la interfaz de usuario con instrucciones o comentarios.
3. Vincule al tercer elemento de la interfaz de usuario con instrucciones o comentarios.

Un usuario puede seleccionar un elemento en orden o volver a uno específico y resaltarlo.

## <a name="solutions-and-custom-help-pane-content"></a>Soluciones y contenido del panel de ayuda personalizado
Todo el contenido de ayuda se almacena en un componente de la página de ayuda en Common Data Service como parte de la solución. Cuando mueva la solución desde un entorno a otro, por ejemplo, de prueba a producción, puede definir que los registros de la ayuda se exporten para incluirlos en la solución. Esto le permite mantener su contenido de ayuda en sincronización con características de la solución mientras se mueve a diferentes entornos. Como parte de la solución, los paneles personalizados de ayuda admiten todas las características de administración del ciclo de vida de la aplicación (ALM) de la solución estándar.

### <a name="moving-content-via-solutions"></a>Mover contenido mediante soluciones
De forma predeterminada, todas las nuevas páginas de ayuda aparecen en la solución predeterminada. Si desea mover su contenido a otro entorno, primero agregue sus páginas de ayuda existentes a una solución no administrada antes de exportarlas. Para agregar una página de ayuda a una solución no administrada, siga estos pasos:

1. Vaya a una solución no administrada.
2. Seleccione **Cambiar a clásico** en los puntos suspensivos de la barra de comandos.
3. Seleccionar **Agregar existente**.
4. Seleccione **Página de ayuda**.
5. Seleccione las páginas de ayuda que desea agregar y, después, seleccione **Aceptar**.

> [!NOTE]
> Actualmente, no puede agregar paneles existentes de la ayuda a una solución no administrada en el explorador de soluciones moderno. 


## <a name="help-page-documentation-automation"></a>Automatización de la documentación de la página de ayuda
Es posible que desee realizar una copia de seguridad o almacenar su contenido en un sistema de control de código de origen. Puede que también desee usar herramientas de automatización de la documentación, como herramientas de traducción o comprobadores, en contenido del panel de ayuda. Los datos del panel de la ayuda personalizado se almacenan directamente en Common Data Service y se pueden exportar e importar con este fin.  

Los paneles personalizados de ayuda admiten un formato XML personalizado. Este formato se documenta a continuación. Más información: [Definición XML de ayuda personalizado](#custom-help-xml-definition)  

Cuando se exportada, cada página de ayuda se exporta como un archivo separado.   

## <a name="frequently-asked-questions"></a>Preguntas más frecuentes
En esta sección se explican preguntas frecuentes sobre las páginas de ayuda personalizadas. 

### <a name="are-custom-help-pages-the-same-as-customizable-help"></a>¿Son las páginas de ayuda personalizadas igual que la ayuda personalizable?

Los paneles personalizados de ayuda y tareas guiadas son una opción en la sección **Establecer la URL de ayuda personalizada** de la configuración del sistema. Los paneles personalizados de ayuda y las tareas guiadas habilitan un panel personalizable de Ayuda que aparece junto al formulario del usuario.  Las otras opciones en esta sección de ayuda personalizada de configuraciones comprenden las características personalizables de ayuda. Permiten reemplazar la ayuda de aplicaciones predeterminadas y dirigen a los usuarios de la organización a otra dirección URL para la ayuda. Alternativamente, usted puede reemplazar la ayuda para una entidad muy personalizada que puede describir mejor el flujo de trabajo.

Para obtener más información sobre Ayuda personalizable, consulte [Habilitar y usar ayuda personalizable](../model-driven-apps/use-customizable-help.md).


### <a name="how-do-i-migrate-my-data-from-learning-path-to-custom-help-pages"></a>¿Cómo migro mis datos desde ruta de aprendizaje hasta páginas de ayuda personalizadas? 
Ruta de aprendizaje tiene dos tipos de Ayuda: paneles de ayuda y globos de ayuda secuenciales. Las ubicaciones de globo de ayuda secuenciales están muy integradas con la interfaz de usuario del cliente web heredada y no son transferibles a los nuevos paneles personalizados de ayuda.  

Según cuánto texto tenga en la ayuda guiada puede ser más fácil copiar simplemente la información directamente desde la interfaz de usuario de ruta de aprendizaje a la nueva interfaz de usuario del panel de ayuda personalizado. Sin embargo, también puede exportar el contenido de ayuda de la ruta de aprendizaje.  La forma más fácil de hacerlo es exportar el contenido mediante la característica **Ruta de aprendizaje** > **Biblioteca de contenido** > **Localizar** > **Exportar**. Seleccione los registros que desea y luego expórtelos. Esto crea un archivo XLIFF para cada panel de ayuda y tarea guiada.  A continuación, use a un editor de XLIFF disponible públicamente o un convertidor de XLIFF a HTML para recuperar su contenido. 

## <a name="custom-help-xml-definition"></a>Definición de XML de ayuda personalizada
Esta sección describe la definición de XML de la ayuda personalizada. 

### <a name="pphml"></a>PPHML

```
<pphml>
    <h1>FAQ</h1>
    <collapsible title="What is PPHML?">
        <p>PPHML is a domain specific language for help content. It is used to create help content that includes elements such as images, videos, balloons, coach marks, etc.</p>
    </collapsible>
    <collapsible title="What does PPHML stand for?">
        <p>PPHML stands for Power Platform Help Markup Language</p>
    </collapsible>
</pphml>
```

#### <a name="definition-and-usage"></a>Definición y uso

El elemento `<pphml>` indica al explorador de la ayuda que esto es un documento PPHML.

El elemento `<pphml>` representa la raíz de un documento PPHML.

El elemento `<pphml>` es el contenedor para todos los demás elementos PPHML.

### <a name="title"></a>Título
Muestra un título en una página de ayuda.

```
<h1>This will be displayed at the top of the help page</h1>
```

#### <a name="definition-and-usage"></a>Definición y uso
El elemento **`<h1>`** define el título de una página de ayuda.

`<h1>` Debe ser el primer elemento en `<pphml>`.

### <a name="image"></a>Imagen
Muestra una imagen en una página de ayuda.

```
<img src="smiley.gif" alt="Smiley face" title="Smiley face"/>
```

#### <a name="definition-and-usage"></a>Definición y uso
El elemento **`<img>`** inserta una imagen en una página de ayuda.

#### <a name="attributes"></a>Atributos
- `src`: Especifica la dirección URL de una imagen. Se requiere este atributo.

- `title`: Especifica un título para mostrar junto con la imagen, normalmente como información sobre herramientas al mantener el puntero.

- `alt`: Especifica un texto alternativo para una imagen. Este texto se usa en los lectores de pantalla.

### <a name="video"></a>Vídeo
Muestra un vídeo en una página de ayuda.

```
<video src="https://www.youtube.com/watch?v=WSWmn7WM3i4" />
```

#### <a name="definition-and-usage"></a>Definición y uso

El elemento **`<video>`** inserta un vídeo, como un tutorial o una película de aprendizaje, en una página de ayuda.

##### <a name="supported-sources"></a>Orígenes compatibles

- Microsoft Stream
- YouTube
- Facebook
- Vimeo

#### <a name="attributes"></a>Atributos
- `src`: Especifica la dirección URL del vídeo. Se requiere este atributo.

- `allowFullScreen`: Especifica si el usuario puede cambiar el vídeo a pantalla completa. Los valores posibles son “true “o “false”. Este atributo no es compatible con todos los orígenes de vídeo.

- `autoplay`: Especifica que el vídeo comenzará a reproducirse tan pronto como la página de ayuda se cargue. Los valores posibles son “true “o “false”. Este atributo no es compatible con todos los orígenes de vídeo.

- `startTime`: Especifica, en segundos, desde qué punto comienza a reproducirse el vídeo.

### <a name="paragraph"></a>Párrafo
Muestra un párrafo en una página de ayuda.

```
<p>This is some text in a paragraph.</p>
```

#### <a name="definition-and-usage"></a>Definición y uso
El elemento **`<p>`** define un párrafo.

El texto dentro de un párrafo se puede adornar de las siguientes formas:
- Negrita, con el elemento `<strong>`
- Cursiva, con el elemento `<em>`
- Tachado, con el elemento `<del>`
- Subrayado, con el elemento `<u>`

Estas decoraciones se pueden combinar. Por ejemplo, cree un fragmento de texto que sea negrita y subrayado.

### <a name="bulleted-list"></a>Lista de viñetas
Muestra una lista de viñetas en una página de ayuda.

```
<ul>
    <li>Coffee</li>
    <li>Tea</li>
    <li>Milk</li>
</ul>
```

#### <a name="definition-and-usage"></a>Definición y uso
El elemento **`<ul>`** define una lista con viñetas.

Use el elemento `<ul>` junto con el elemento `<li>` para crear listas con viñetas.

### <a name="numbered-list"></a>Lista numerada
Muestra una lista numerada en una página de ayuda.

```
<ol>
    <li>First step</li>
    <li>Second step</li>
    <li>Third step</li>
</ol>
```

#### <a name="definition-and-usage"></a>Definición y uso
El elemento **`<ol>`** define una lista ordenada (numerada).
Use la etiqueta `<ol>` junto con el elemento `<li>` para crear listas numeradas.

### <a name="collapsible"></a>Plegable
Muestra una sección contraíble en una página de ayuda.

```
<collapsible title="This is a Section">
    <p>This is a paragraph inside a section</p>
    <img src=smiley.gif" title="This is an image inside a section" />
</collapsible>
```

#### <a name="definition-and-usage"></a>Definición y uso
El elemento **`<collapsible>`** define una sección de contenido que el usuario puede ver u ocultar a petición.

#### <a name="attributes"></a>Atributos
- `collapsed`: Especifica si la sección se contrae o expande inicialmente. Los valores posibles son “true“ (contraída) o “false” (expandida).

### <a name="link"></a>Vínculo
Muestra un vínculo en una página de ayuda.

Vincular a una página web que se abre en una nueva ventana del explorador:

```
<a href="https://www.microsoft.com" target="_blank">Microsoft Home Page</a>
```

Vincular a otra página de la ayuda:

```
<a href="./LearnMore">Learn More</a>
```

#### <a name="definition-and-usage"></a>Definición y uso
La etiqueta `<a>` define un vínculo, que permite al usuario navegar de una página de ayuda a un sitio web, o a otra página de ayuda.

#### <a name="attributes"></a>Atributos

- `href`: Especifica la dirección URL del sitio web o la página de ayuda a los que navegar. Se requiere este atributo.
- `target`: Especifica dónde abrir la dirección URL vinculada.
   - Si no está presente o `_self`, se da por hecho que el vínculo es otra página de ayuda y se abre en el explorador de ayuda.
   - Si `_blank`, el vínculo se abre en una nueva ventana del explorador.
   - Si `_top`, el vínculo se abre en la ventana actual del explorador.
   - Si el valor es el nombre de un `iframe`, el vínculo se abre en ese iframe.

### <a name="coach-mark"></a>Marca de formación
Muestra una marca de formación en una página de ayuda.

```
<coachmark target="#my-html-button">Click to highlight the HTML element with id [my-html-button]</coachmark>
```

#### <a name="definition-and-usage"></a>Definición y uso
Una marca de formación es un elemento interactivo que se puede usar para atraer la atención del usuario a un punto específico en la interfaz de usuario de la aplicación que hospeda el explorador de ayuda.

#### <a name="attributes"></a>Atributos

- `target`: [Selector de CSS](https://www.w3schools.com/cssref/css_selectors.asp) que especifica el elemento HTML sobre el que se mostrará la marca de formación. Se requiere este atributo.

### <a name="balloon"></a>Globo
Muestra un globo en una página de ayuda.

```
<balloon target="#my-html-button" title="This button submits the form" details="Please click this button to continue and submit the form">Click to show a balloon over the HTML element with id [my-html-button]</balloon>
```

#### <a name="definition-and-usage"></a>Definición y uso
Un globo es un elemento interactivo que se puede usar para ayudar al usuario a realizar una acción en la interfaz de usuario de la aplicación que hospeda el explorador de ayuda.

#### <a name="attributes"></a>Atributos
- `target`: Selector de CSS que especifica el elemento HTML sobre el que se mostrará el vínculo de globo. Se requiere este atributo.
- `title`: Especifica el título del globo.
- `details`: Especifica el contenido para mostrar en Globo de conexión.


