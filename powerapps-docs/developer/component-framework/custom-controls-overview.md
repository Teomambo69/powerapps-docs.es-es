---
title: Qué son los componentes de código | MicrosoftDocs
description: Use Power Apps component framework para crear componentes de código para proporcionar una mejor experiencia para que los usuarios vean y trabajen con datos en formularios, vistas, y paneles.
manager: kvivek
ms.date: 09/05/2019
ms.service: powerapps
ms.topic: article
ms.assetid: 135481cd-4583-4e49-8f58-02f32a9b054a
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: 6b563136dba6cc2144e66654860c1f760adbea60
ms.sourcegitcommit: 27cb5ad024d43f208ef6acfbea456a05df3edf8e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/25/2020
ms.locfileid: "3082817"
---
# <a name="what-are-code-components"></a>Qué son los componentes de código

Los componentes de código son un tipo de componente de la solución, lo que significa que se pueden incluir en un archivo de solución e instalar en diferentes entornos. Más información: [Empaquetar y distribuir extensiones utilizando soluciones](https://docs.microsoft.com/dynamics365/customer-engagement/developer/package-distribute-extensions-use-solutions).

> [!div class="mx-imgBorder"] 
> ![Componentes de código](media/code-components.gif "Componentes de código")

Puede agregar los componentes de código incluyéndolos en una solución y después importándolos en Common Data Service. Una vez que los componentes están en Common Data Service, los administradores y personalizadores del sistema pueden configurar campos de formulario, subcuadrículas, vistas y subcuadrículas del panel para usarlos en lugar del componente predeterminado. Puede agregar estos componentes de código a **aplicaciones basadas en modelo y de lienzo**. 

Los componentes de código constan de tres elementos:

- [Manifiesto](#manifest)
- [Implementación del componente](#component-implementation)
- [Recursos](#resources)

> [!NOTE]
> La definición e implementación de componentes de código utilizando Power Apps component framework es el mismo tanto para aplicaciones basadas en modelo como para las de lienzo. La única diferencia entre ambos es la parte de configuración. 

## <a name="manifest"></a>Manifiesto

El manifiesto es el archivo de metadatos que define un componente. Es un documento XML que describe:

- Nombre del componente.
- El tipo de datos que se puede configurar, un campo o un conjunto de datos.
- Las propiedades que se pueden configurar en la aplicación cuando se agrega el componente.
- Una lista de archivos de recursos que el componente necesita. 
- El nombre de la función TypeScript en la biblioteca de implementación del componente que devuelve un objeto que aplica la interfaz del componente necesario.

Cuando un usuario configura un componente de código, los datos del archivo de manifiesto filtran los componentes disponibles para que sólo los componentes válidos para el contexto estén disponibles para configuración. Las propiedades definidas en el archivo de manifiesto para un componente se generan como campos de configuración para que el usuario que configura el componente pueda especificar los valores. Estos valores de propiedad están disponibles entonces para el componente en tiempo de ejecución. Más información: [Referencia de esquema de manifiesto](manifest-schema-reference/index.md)

## <a name="component-implementation"></a>Implementación del componente

Implementar el componente es uno de los pasos clave cuando está desarrollando componentes de código con Power Apps component framework. Los desarrolladores pueden implementar un componente con TypeScript. Cada componente de código debe tener un archivo `index.ts` que incluya la definición de una función que devuelva un objeto que implemente los métodos descritos en la interfaz de componentes de código. Este archivo se genera automáticamente a través de herramientas CLI con métodos de stub principales.

El objeto implementa los siguientes métodos:

- [init](reference/control/init.md) (requerido)
- [updateView](reference/control/updateview.md) (requerido)
- [getOutputs](reference/control/getoutputs.md) (opcional)
- [destroy](reference/control/destroy.md) (requerido)

Estos métodos controlan el ciclo de vida del componente de código.

### <a name="page-load"></a>Carga de página

Cuando se carga la página, la aplicación requiere un objeto para trabajar. Al usar los datos del archivo de manifiesto, el código obtiene el objeto llamando:

```js
var obj =  new <"namespace on manifest">.<"constructor on manifest">();
```

Si los valores de espacio de nombres y constructor del manifiesto son `SampleNameSpace` y `LinearInputComponent` respectivamente, el código para crear instancias del objeto sería éste:

```js
var controlObj = new SampleNameSpace.LinearInputComponent();
```

Cuando la página está lista, inicializa el componente llamando al método [init](reference/control/init.md) con un conjunto de parámetros.

```js
controlObj.init(context,notifyOutputChanged,state,container);
```

|Parámetro|Descripción|
|---|---|
|contexto| Contiene toda la información sobre cómo se configura el componente y todos los parámetros que se pueden usar en el componente junto con las [API de Power Apps component framework](reference/index.md). Por ejemplo, `context.parameters.<"property name from manifest">` se puede usar para tener acceso a la propiedad de entrada.|
|notifyOutputChanged |Alerta al marco de trabajo cuando el componente de código tiene las nuevas salidas listas para recuperarse de forma asincrónica.|
|estado|Contiene datos del componente de la carga de página anterior en la sesión actual si el componente explícitamente lo almacenó antes usando el método [setControlState](reference/mode/setcontrolstate.md).|
|contenedor|Un elemento de div HTML al que los desarrolladores y creadores de aplicaciones pueden anexar los elementos HTML para la interfaz de usuario que define el componente.|

### <a name="user-changes-data"></a>El usuario cambia los datos

Cuando se carga la página, el componente muestra los datos hasta que el usuario interactúa con el componente para cambiar los datos. En este caso, debe llamar al método pasado en como parámetro *notifyOutputChanged* del método [init](reference/control/init.md). Cuando se usa este método, la plataforma responde llamando al método [getOutputs](reference/control/getoutputs.md). El método [getOutputs](reference/control/getoutputs.md) devuelve los valores que tienen los cambios realizados por el usuario. Para un componente de campo, esto sería normalmente el nuevo valor para el componente.

### <a name="app-changes-data"></a>La aplicación cambia los datos

Si la plataforma cambia los datos, llamará al método [updateView](reference/control/updateview.md) del componente y pasará el nuevo objeto de contexto como parámetro. Este método se debe implementar para actualizar los valores mostrados en el componente.

### <a name="page-close"></a>Cierre de página

Cada vez que un usuario sale de la página, el componente de código pierde el ámbito y se borra toda la memoria asignada en esa página para los objetos del componente. Sin embargo, algunos métodos basados en el mecanismo de implementación del explorador pueden mantenerse y consumir memoria. Normalmente, estos son controladores de eventos. Si el usuario desea almacenar esta información, debe implementar el método [setControlState](reference/mode/setcontrolstate.md) para que la información se dé la siguiente vez en la misma sesión.

Los programadores debe implementar el método [destroy](reference/control/destroy.md), al que se llama cuando se cierra la página, para eliminar cualquier código de limpieza como controladores de eventos.

## <a name="resources"></a>Recursos

Cada componente de código debe tener un archivo de recurso para generar su visualización. Puede definir un archivo de recursos en el manifiesto. El nodo de recurso en el archivo de manifiesto hace referencia a los recursos que el componente requiere para implementar su visualización. Más información: [elemento de recursos](manifest-schema-reference/resources.md)

### <a name="related-topics"></a>Temas relacionados

[Crear y generar un componente de código](create-custom-controls-using-pcf.md)
