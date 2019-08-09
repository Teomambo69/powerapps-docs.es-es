---
title: Qué son componentes personalizados | MicrosoftDocs
description: 'Use el marco de componentes de PowerApps para crear componentes personalizados para proporcionar una mejor experiencia de usuario para que los usuarios vean y trabajen con datos en formularios, vistas, y paneles.'
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.topic: article
ms.assetid: 135481cd-4583-4e49-8f58-02f32a9b054a
ms.author: nabuthuk
---

# <a name="what-are-custom-components"></a>Qué son componentes personalizados

[!INCLUDE[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Los componentes personalizados son un tipo de componente de la solución, lo que significa que se pueden incluir en una solución e instalar en diferentes entornos. Más información: [Empaquetar y distribuir extensiones utilizando soluciones](https://docs.microsoft.com/dynamics365/customer-engagement/developer/package-distribute-extensions-use-solutions).

Puede agregar los componentes personalizados incluyéndolos en una solución y después importándolos en el sistema. Una vez que están en el sistema, administradores y personalizadores del sistema pueden configurar campos de formulario, subcuadrículas, vistas y subcuadrículas del panel para usarlos en lugar del componente predeterminado.

Los componentes personalizados están compuestos de tres componentes:

1. Manifiesto
2. Biblioteca de implementación del componente
3. Recursos

## <a name="manifest"></a>Manifiesto

El manifiesto es el archivo de metadatos que define un componente. Es un documento XML que describe:

- El espacio de nombres y el nombre del componente.
- El tipo de datos que se puede configurar, un campo o un conjunto de datos.
- Las propiedades que se pueden configurar en la aplicación cuando se agrega el componente.
- Una lista de archivos de recursos que el componente necesita. 
- El nombre de una función TypeScript en la biblioteca de implementación del componente que devolverá un objeto que aplica la interfaz del componente necesario.

Cuando alguien configura un componente en la aplicación, los datos del manifiesto filtran el componente disponible para que sólo el componente válido para el contexto esté disponible para configuración. Las propiedades definidas en el manifiesto para un componente se generan como campos de configuración para que la persona que configura el componente pueda especificar valores. Estos valores de propiedad están disponibles entonces para la función de componente en tiempo de ejecución. Más información: [Referencia del archivo de manifiesto](manifest-schema-reference/index.md)

## <a name="component-implementation-library"></a>Biblioteca de implementación del componente

[!INCLUDE [component-implementation-library](control-implementation-library.md)]

### <a name="page-load"></a>Carga de página

Cuando se carga la página, la aplicación requiere un objeto con el que trabajar. Al usar los datos del manifiesto, el código obtiene el objeto mediante llamada

```js
var obj =  new ["namespace on manifest"].["constructor on manifest"]();
```

Si los valores de espacio de nombres y constructor del manifiesto son `MyNameSpace` y `LinearInputControl` respectivamente, el código para crear instancias del objeto sería éste:

```js
var controlObj = new MyNameSpace.LinearInputControl();
```

Cuando la página está lista, inicializa el componente llamando a la función [init](reference/control/init.md) con un conjunto de parámetros.

```js
controlObj.init(context,notifyOutputChanged,state,container);
```

|Parámetro|Descripción|
|---|---|
|contexto| Contiene toda la información sobre cómo se configura el componente y todos los parámetros que se pueden usar en el componente junto con las [API de marco](reference/index.md). Por ejemplo, `context.parameters.["property name from manifest"]` se puede usar para tener acceso a la propiedad de entrada.|
|notifyOutputChanged |Función que alerta al marco de trabajo que el componente tiene las nuevas salidas listas para recuperarse de forma asincrónica.|
|estado|Contiene datos del componente de la carga de página anterior en la sesión actual si el control explícitamente lo almacenó antes usando `setControlState API`.|
|contenedor|Un elemento de div HTML al que anexará los elementos HTML para la interfaz de usuario que define el componente. Para mostrar el valor en la interfaz de usuario, debe obtener los datos de `context.parameters.controlValue object`.|

### <a name="user-changes-data"></a>El usuario cambia los datos

Después de que se cargue la página, el componente muestra los datos hasta que el usuario interactúa con el componente para cambiar los datos. Cuando esto ocurre, puede administrarlo del modo que prefiera, pero debe llamar a la función pasada como parámetro **notifyOutputChanged** en la función [init](reference/control/init.md). Cuando use esta función, la plataforma responderá llamando al método [getOutputs](reference/control/getoutputs.md) que debe implementar. Los métodos [getOutputs](reference/control/getoutputs.md) devolverán cualquier valor que represente los cambios que un usuario ha realizado. Para un componente de campo, esto sería normalmente el nuevo valor para el componente.

### <a name="app-changes-data"></a>La aplicación cambia los datos

Si los datos los cambia la plataforma, llamará al método [updateView](reference/control/updateview.md) del objeto de componente y pasará un nuevo objeto de contexto como parámetro. Debe implementar este método y usarlo para actualizar el valor mostrado en el componente.

### <a name="page-close"></a>Cierre de página

Cuando el usuario navega fuera de la página el componente perderá ámbito y generalmente se borrará toda la memoria asignada en esa página para los objetos del componente. Sin embargo, algunos elementos basados en el mecanismo de implementación del explorador pueden mantenerse y consumir memoria. Normalmente, estos son controladores de eventos. Si el usuario desea almacenar la información, debe implementar el método `setControlState` para que la información se dé la siguiente vez en la misma sesión.
Debe definir un método [destroy](reference/control/destroy.md) en el objeto. Este se llamará cuando se cierre la página y debe usarlo para quitar código de limpieza, por ejemplo, cualquier controladores de evento.

## <a name="resources"></a>Recursos

Cada componente personalizado debe tener un archivo de recurso para generar su visualización. Puede definir un archivo de recursos en el manifiesto. El nodo de recurso en el archivo de manifiesto hace referencia a los recursos que el componente requiere para implementar su visualización. Más información: [Recursos](manifest-schema-reference/resources.md)

### <a name="related-topics"></a>Temas relacionados

[Creación de componentes personalizados](create-custom-controls-using-pcf.md)
