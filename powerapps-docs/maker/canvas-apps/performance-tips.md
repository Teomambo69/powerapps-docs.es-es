---
title: Optimización del rendimiento de las aplicaciones de lienzo | Microsoft Docs
description: Siga los procedimientos recomendados que aparecen este tema para mejorar el rendimiento de las aplicaciones de lienzo que se crean en PowerApps.
author: yingchin
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 06/17/2019
ms.author: yingchin
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c0926c2c38adac6b3377de9a87eef4dd7d7a7cf7
ms.sourcegitcommit: 9c4d95eeace85a3e91a00ef14fefe7cce0af69ec
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2019
ms.locfileid: "67349805"
---
# <a name="optimize-canvas-app-performance-in-powerapps"></a>Optimización del rendimiento de las aplicaciones de lienzo en PowerApps
Microsoft se esfuerza por mejorar el rendimiento de todas las aplicaciones que se ejecutan en la plataforma de PowerApps, pero puede seguir los procedimientos recomendados que aparecen en este tema para mejorar el rendimiento de las aplicaciones que se crean.

Cuando un usuario abre una aplicación, esta pasa a través de estas fases de ejecución antes de mostrar cualquier interfaz de usuario: 
1. **Autenticación del usuario**: se le pide al usuario, si esa persona nunca antes abrió la aplicación, que inicie sesión con las credenciales de cualquier conexión que la aplicación necesite. Si el mismo usuario vuelve a abrir la aplicación, se le podría pedir nuevamente que lo haga, en función de las directivas de seguridad de la organización. 
2. **Obtención de los metadatos**: se recuperan metadatos, como la versión de la plataforma de PowerApps en la que se ejecuta la aplicación y los orígenes desde donde se deben recuperar los datos. 
3. **Inicialización de la aplicación**: se realiza cualquier tarea especificada en la propiedad **OnStart**. 
4. **Presentación de pantallas**: se presenta la primera pantalla con controles que la aplicación ha rellenado con datos. Si el usuario abre otras pantallas, la aplicación las presenta mediante el mismo proceso.  

## <a name="limit-data-connections"></a>Límite de conexiones de datos 
**No se conecte a más de 30 orígenes de datos desde la misma aplicación**. Las aplicaciones piden a los usuarios nuevos que inicien sesión en cada conector, por tanto, cada conector adicional aumenta la cantidad de tiempo que la aplicación necesita para iniciarse. Cuando se ejecuta una aplicación, cada conector requiere recursos de CPU, memoria y ancho de banda de red cuando la aplicación solicita datos a ese origen. 

Para medir rápidamente el rendimiento de la aplicación, active Herramientas de desarrollo en [Microsoft Edge](https://docs.microsoft.com/microsoft-edge/devtools-guide/network) o [Google Chrome](https://developers.google.com/web/tools/chrome-devtools/network-performance/) mientras se ejecuta la aplicación. La aplicación es más probable que tarden más de 15 segundos para devolver los datos si solicita con frecuencia datos de más de 30 orígenes de datos, como Common Data Service, Azure SQL, SharePoint y Excel en OneDrive.  

## <a name="limit-the-number-of-controls"></a>Límite del número de controles 
**No agregue más de 500 controles a la misma aplicación**. PowerApps genera DOM HTML para presentar cada control. Cuantos más controles agregue, más tiempo de generación necesita PowerApps. 

En algunos casos, es posible llegar al mismo resultado y hacer que la aplicación se inicie más rápido si usa una galería en lugar de controles individuales. Además, puede que quiera disminuir el número de tipos de control en la misma pantalla. Algunos controles (como el visor de PDF, la tabla de datos y el cuadro combinado) incorporan scripts de ejecución de gran tamaño y tardan más en presentarse. 

## <a name="optimize-the-onstart-function"></a>Optimización de la función OnStart
Use la función [**ClearCollect**](functions/function-clear-collect-clearcollect.md) para almacenar en caché local los datos si no cambian durante la sesión del usuario. Además, use la función [**Concurrent**](functions/function-concurrent.md) para cargar orígenes de datos de manera simultánea.

Como se muestra en [este tema de referencia](functions/function-concurrent.md), puede usar la función **Concurrent** para disminuir a la mitad el tiempo que una aplicación necesita para cargar los datos.

Sin la función **Concurrent**, esta fórmula carga cada una por una cada una de estas cuatro tablas:

    ClearCollect( Product, '[SalesLT].[Product]' );
    ClearCollect( Customer, '[SalesLT].[Customer]' );
    ClearCollect( SalesOrderDetail, '[SalesLT].[SalesOrderDetail]' );
    ClearCollect( SalesOrderHeader, '[SalesLT].[SalesOrderHeader]' )

Puede confirmar este comportamiento en las Herramientas de desarrollo del explorador:

![ClearCollect en serie](./media/performance-tips/perfconcurrent1.png)
    
Puede incluir la misma fórmula en la función **Concurrent** para disminuir el tiempo total que necesita la operación:

    Concurrent( 
        ClearCollect( Product, '[SalesLT].[Product]' ),
        ClearCollect( Customer, '[SalesLT].[Customer]' ),
        ClearCollect( SalesOrderDetail, '[SalesLT].[SalesOrderDetail]' ),
        ClearCollect( SalesOrderHeader, '[SalesLT].[SalesOrderHeader]' ))
        
Con este cambio, la aplicación captura las tablas en paralelo: 

![ClearCollect paralelo](./media/performance-tips/perfconcurrent2.png)  

## <a name="cache-lookup-data"></a>Almacenamiento en caché de datos de búsqueda
Use la función **Set** para almacenar en caché local datos provenientes de tablas de búsqueda con el fin de evitar tener que recuperar repetidamente los datos desde el origen. Esta técnica permite optimizar el rendimiento si es probable que los datos no cambien durante una sesión. Como en este ejemplo, los datos se recuperan desde el origen una sola vez y, después, se hace referencia a ellos de manera local hasta que el usuario cierra la aplicación. 

    Set(CustomerOrder, Lookup(Order, id = “123-45-6789”));
    Set(CustomerName, CustomerOrder.Name);
    Set(CustomerAddress, CustomerOrder.Address);
    Set(CustomerEmail, CustomerOrder.Email);
    Set(CustomerPhone, CustomerOrder.Phone);

La información de contacto con cambia con frecuencia, así como tampoco lo hacen los valores predeterminados ni la información del usuario. Por tanto, puede usar habitualmente esta técnica también con las funciones **Defaults** y **User**. 

## <a name="avoid-controls-dependency-between-screens"></a>Evitar la dependencia de controles entre pantallas
Para mejorar el rendimiento, las pantallas de una aplicación se cargan en memoria solo según sean necesarios. Esta optimización puede verse limitada si, por ejemplo, 1 de la pantalla se carga y una de sus fórmulas utiliza una propiedad de un control de pantalla de 2. Ahora, pantalla 2 debe cargarse para satisfacer la dependencia antes de que se puede mostrar la pantalla 1. Imagine pantalla 2 tiene una dependencia en la pantalla 3, que no tiene otra dependencia de pantalla de 4 y así sucesivamente. Esta cadena de dependencia puede hacer que se puede cargar varias pantallas.

Por esta razón, evite las fórmulas dependencias entre pantallas. En algunos casos puede usar una variable global o una colección para compartir información entre pantallas.

Hay una excepción. En el ejemplo anterior, imagine que es la única manera de mostrar la pantalla 1 navegando desde la pantalla de 2. A continuación, pantalla 2 habría ya se ha cargado en memoria cuando estaba pantalla 1 que se cargue. No es necesario ningún trabajo adicional para satisfacer la dependencia para la pantalla 2 y, por tanto, no hay ningún impacto en el rendimiento.

## <a name="use-delegation"></a>Uso de la delegación
Siempre que sea posible, use las funciones que delegan el procesamiento de datos al origen de datos en lugar de recuperar los datos en el dispositivo local para el procesamiento. Si una aplicación debe procesar localmente los datos, la operación requiere mucha más potencia de procesamiento, memoria y ancho de banda de red, especialmente si el conjunto de datos es grande.

Tal como se muestra en [esta lista](delegation-list.md), distintos orígenes de datos admiten la delegación desde distintas funciones:

![Uso de la delegación](./media/performance-tips/perfdelegation1.png)

Por ejemplo, las listas de SharePoint admiten la delegación desde la función [**Filter**](functions/function-filter-lookup.md), pero no desde la función [**Search**](functions/function-filter-lookup.md). Por tanto, debería usar **Filter** en lugar de **Search** para buscar elementos en una galería si la lista de SharePoint contiene más de 500 elementos. Para más sugerencias, consulte la entrada de blog [Working with large SharePoint lists in PowerApps](https://powerapps.microsoft.com/blog/powerapps-now-supports-working-with-more-than-256-items-in-sharepoint-lists/) (Trabajo con listas grandes de SharePoint en PowerApps). 

## <a name="use-delayed-load"></a>Uso de la carga retrasada
Active la [característica experimental](working-with-experimental.md) para carga retrasada si la aplicación tiene más de 10 pantallas, ninguna regla y muchos controles que se encuentran en varias pantallas y que están directamente enlazados al origen de datos. Si compila este tipo de aplicación y no habilita esta característica, el rendimiento de la aplicación podría verse afectado porque los controles que están en todas las pantallas se deben rellenar incluso en las pantallas que no están abiertas. Además, es necesario actualizar todas las pantallas de la aplicación cada vez que cambia el origen de datos, como ocurre cuando el usuario agrega un registro.

## <a name="working-with-large-data-sets"></a>Trabajo con conjuntos de datos grandes
Use los orígenes de datos y las fórmulas que se pueden delegar para que las aplicaciones sigan funcionando correctamente mientras los usuarios pueden acceder a toda la información que necesitan y evite llegar al límite de 2000 filas de datos para las consultas que no se pueden delegar. En el caso de las columnas con registros de datos en las que los usuarios pueden buscar, filtrar u ordenar los datos, esos índices de columna están diseñados tal como lo describen estos documentos para [SQL Server](https://docs.microsoft.com/sql/relational-databases/sql-server-index-design-guide?view=sql-server-2017) y [SharePoint](https://support.office.com/article/Add-an-index-to-a-SharePoint-column-f3f00554-b7dc-44d1-a2ed-d477eac463b0).  

## <a name="republish-apps-regularly"></a>Volver a publicar aplicaciones de manera habitual
Consulte la entrada de blog [Republish your apps](https://powerapps.microsoft.com/blog/republish-your-apps-to-get-performance-improvements-and-additional-features/) (Volver a publicar las aplicaciones) para obtener mejoras en el rendimiento y características adicionales desde la plataforma de PowerApps.

## <a name="avoid-repeating-the-same-formula-in-multiple-places"></a>Evitar repetir la misma fórmula en varios lugares
Si varias propiedades ejecutan la misma fórmula (especialmente si es compleja), considere la posibilidad de una vez establecidos y, a continuación, hacer referencia a la salida de la primera propiedad en las posteriores. Por ejemplo, no establezca la **DisplayMode** propiedad de los controles A, B, C, D y E en la misma fórmula compleja. En su lugar, establezca la **DisplayMode** propiedad en la fórmula compleja, establezca la B **DisplayMode** el resultado de la propiedad **DisplayMode** propiedad, y así sucesivamente para C, D y E.

## <a name="enable-delayoutput-on-all-text-input-controls"></a>Habilitar DelayOutput en todos los controles de entrada de texto
Si tiene varias fórmulas o las reglas que hacen referencia al valor de un **entrada de texto** , establezca el **DelayedOutput** propiedad de ese control en true. El **texto** se actualizará la propiedad de ese control solo después de que han dejado de pulsaciones de teclas escritas en una sucesión rápida. Las reglas o fórmulas no se ejecutan tantas veces y mejorará el rendimiento de la aplicación.

## <a name="avoid-using-formupdates-in-rules-and-formulas"></a>Evite el uso de Form.Updates en reglas y fórmulas
Si hace referencia a un valor de entrada del usuario en una regla o una fórmula mediante el uso de un **Form.Updates** variable, se recorre en iteración todas las tarjetas del formulario datos y crea un registro cada vez. Para que la aplicación más eficaz, hacen referencia al valor directamente desde la tarjeta de datos o el valor del control.

## <a name="next-steps"></a>Pasos siguientes
Revise el [estándares de codificación](https://aka.ms/powerappscanvasguidelines) para maximizar el rendimiento de la aplicación y mantener aplicaciones más fáciles de mantener.
