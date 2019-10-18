---
title: ¿Qué son los componentes de código? | MicrosoftDocs
description: Use el marco de componentes de PowerApps para crear componentes de código con el fin de proporcionar experiencias de usuario mejoradas para que los usuarios puedan ver y trabajar con datos en formularios, vistas y paneles.
manager: kvivek
ms.date: 09/05/2019
ms.service: powerapps
ms.topic: article
ms.assetid: 135481cd-4583-4e49-8f58-02f32a9b054a
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: 08a2043dfb92634837c367e664306d9c100632d6
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346978"
---
# <a name="what-are-code-components"></a>Qué son los componentes de código

Los componentes de código son un tipo de componentes de la solución, lo que significa que se pueden incluir en un archivo de solución e instalar en entornos diferentes. Más información: [empaquetar y distribuir extensiones mediante soluciones](https://docs.microsoft.com/dynamics365/customer-engagement/developer/package-distribute-extensions-use-solutions).

Para agregar componentes de código, puede incluirlos en una solución y, a continuación, importarlos en Common Data Service. Una vez que los componentes están en Common Data Service, los administradores del sistema y los personalizadores del sistema pueden configurar los campos, subcuadrículas, vistas y subcuadrículas del panel que se usarán en lugar de los componentes predeterminados. También puede agregar estos componentes de código en las aplicaciones de canvas. 

Los componentes de código constan de tres elementos:

1. [Manifiesto](#manifest)
2. [Biblioteca de implementación de componentes](#component-implementation-library)
3. [Resources](#resources)

## <a name="manifest"></a>Manifiesto

El manifiesto es el archivo de metadatos que define un componente. Se trata de un documento XML que describe:

- Nombre del componente.
- El tipo de datos que se pueden configurar, ya sea un campo o un conjunto de datos.
- Propiedades que se pueden configurar en la aplicación cuando se agrega el componente.
- Una lista de archivos de recursos que necesita el componente. 
- El nombre de la función TypeScript en la biblioteca de implementación de componentes que devuelve un objeto que aplica la interfaz de componentes necesaria.

Cuando un usuario configura un componente de código, los datos del archivo de manifiesto filtran los componentes disponibles para que solo estén disponibles para la configuración los componentes válidos para el contexto. Las propiedades definidas en el archivo de manifiesto para un componente se representan como campos de configuración para que el usuario que configura el componente pueda especificar los valores. Estos valores de propiedad están disponibles para el componente en tiempo de ejecución. Más información: [Referencia del esquema del manifiesto](manifest-schema-reference/index.md)

## <a name="component-implementation-library"></a>Biblioteca de implementación de componentes

La implementación de la biblioteca de componentes es uno de los pasos clave para desarrollar componentes de código mediante el marco de componentes de PowerApps. Los desarrolladores pueden implementar una biblioteca de componentes mediante TypeScript. Cada componente de código debe tener una biblioteca que incluya la definición de una función, que devuelve un objeto que implementa los métodos descritos en la interfaz del componente de código. 

El objeto implementa los métodos siguientes:

- [init](reference/control/init.md) (obligatorio)
- [updateView](reference/control/updateview.md) (obligatorio)
- [getOutputs](reference/control/getoutputs.md) (opcional)
- [destruir](reference/control/destroy.md) (obligatorio)

Estos métodos controlan el ciclo de vida del componente de código.

### <a name="page-load"></a>Carga de página

Cuando se carga la página, la aplicación requiere que un objeto funcione. Con los datos del archivo de manifiesto, el código obtiene el objeto mediante una llamada a:

```js
var obj =  new <"namespace on manifest">.<"constructor on manifest">();
```

Si los valores de espacio de nombres y constructor del manifiesto son `SampleNameSpace` y `LinearInputComponent` respectivamente, el código para crear una instancia del objeto sería el siguiente:

```js
var controlObj = new SampleNameSpace.LinearInputComponent();
```

Cuando la página está lista, inicializa el componente llamando al método [init](reference/control/init.md) con un conjunto de parámetros.

```js
controlObj.init(context,notifyOutputChanged,state,container);
```

|Parámetro|Descripción|
|---|---|
|contexto| Contiene toda la información sobre cómo se configura el componente y todos los parámetros que se pueden usar en el componente junto con las [API del marco de componentes de PowerApps](reference/index.md). Por ejemplo, el `context.parameters.<"property name from manifest">` se puede utilizar para tener acceso a la propiedad de entrada.|
|notifyOutputChanged |Alerta el marco de trabajo cada vez que el componente de código tiene nuevas salidas listas para ser recuperadas de forma asincrónica.|
|State|Contiene datos de componentes de la carga de página anterior en la sesión actual si el componente lo ha almacenado explícitamente anteriormente mediante el método [setControlState](reference/mode/setcontrolstate.md) .|
|contenedor|Un elemento HTML div en el que los desarrolladores y los responsables de aplicaciones pueden anexar los elementos HTML para la interfaz de usuario que define el componente.|

### <a name="user-changes-data"></a>El usuario cambia los datos

Cuando se carga la página, el componente muestra los datos hasta que el usuario interactúa con el componente para cambiar los datos. Cuando esto sucede, debe llamar al método que se pasa como parámetro *notifyOutputChanged* en el método [init](reference/control/init.md) . Cuando se usa este método, la plataforma responde después llamando al método [getOutputs](reference/control/getoutputs.md) . El método [getOutputs](reference/control/getoutputs.md) devuelve valores que tienen los cambios realizados por el usuario. Para un componente de campo, normalmente sería el nuevo valor del componente.

### <a name="app-changes-data"></a>Datos de la aplicación cambia

Si la plataforma cambia los datos, llama al método [updateView](reference/control/updateview.md) del componente y pasa el nuevo objeto de contexto como un parámetro. Este método debe implementarse para actualizar los valores que se muestran en el componente.

### <a name="page-close"></a>Cerrar página

Siempre que un usuario se queda fuera de la página, el componente de código pierde el ámbito y se borra toda la memoria asignada en esa página para los objetos. Sin embargo, algunos métodos, basados en el mecanismo de implementación del explorador, pueden permanecer y consumir memoria. Normalmente, se trata de controladores de eventos. Si el usuario desea almacenar esta información, debe implementar el método [setControlState](reference/mode/setcontrolstate.md) para que la información se proporcione la próxima vez dentro de la misma sesión.

Los desarrolladores deben implementar el método [Destroy](reference/control/destroy.md) , al que se llama cuando se cierra la página, para quitar el código de limpieza, como los controladores de eventos.

## <a name="resources"></a>Recursos

Cada componente de código debe tener un archivo de recursos para construir su visualización. Puede definir un archivo de recursos en el manifiesto. El nodo de recursos del archivo de manifiesto hace referencia a los recursos que el componente requiere para implementar su visualización. Más información: [Resources (elemento](manifest-schema-reference/resources.md) )

### <a name="related-topics"></a>Temas relacionados

[Crear y compilar un componente de código](create-custom-controls-using-pcf.md)
