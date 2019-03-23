---
title: Función Concurrent| Microsoft Docs
description: Información de referencia, incluida sintaxis, de la función Concurrent de PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 06/26/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e9c63d1814b72cae0c675be6b33773799cfb3b8f
ms.sourcegitcommit: 5b2b70c3fc7bcba5647d505a79276bbaad31c610
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2019
ms.locfileid: "58357101"
---
# <a name="concurrent-function-in-powerapps"></a>Función Concurrent de PowerApps
Evalúa varias fórmulas simultáneamente entre sí.

## <a name="description"></a>Descripción
La función **Concurrent** evalúa varias fórmulas al mismo tiempo. Normalmente, se evalúan varias fórmulas encadenándolas junto con el [ **;** ](operators.md) operador, que evalúa cada secuencialmente en orden. Cuando la aplicación realiza operaciones de forma simultánea, los usuarios esperan menos para el mismo resultado.

En la propiedad [**OnStart**](../controls/control-screen.md) de la aplicación, use **Concurrent** para mejorar el rendimiento cuando la aplicación carga los datos. Si las llamadas de datos no se inician hasta que terminan las llamadas anteriores, la aplicación debe esperar la suma de todos los tiempos de solicitud. Si las llamadas de datos se inician al mismo tiempo, la aplicación solo debe esperar el tiempo de solicitud más largo. Los exploradores web suelen mejorar el rendimiento al realizar las operaciones de datos de forma simultánea.

No se puede predecir el orden en que las fórmulas de la función **Concurrent** inician y terminan la evaluación. Las fórmulas de la función **Concurrent** no deben contener dependencias en otras fórmulas de la misma función **Concurrent** y, si se intenta, PowerApps muestra un error. Desde dentro, es posible tomar dependencias en fórmulas de fuera de la función **Concurrent** con seguridad, puesto que se completan antes de que se inicie la función **Concurrent**. Fórmulas después la **simultáneas** función con seguridad puede tomar dependencias en las fórmulas en: deberá completar antes de la **simultáneas** función finaliza y se mueve a la siguiente fórmula en una cadena (si se Utilice la **;** operador). Esté atento a las dependencias de orden sutiles si está llamando a funciones o métodos de servicio con efectos secundarios.

Puede encadenar las fórmulas junto con el **;** operador dentro de un argumento a **simultáneas**. Por ejemplo, **Concurrent( Set( a, 1 ); Set( b, a+1 ), Set( x, 2 ); Set( y, x+2 ) )** evalúa **Set( a, 1 ); Set( b, a+1 )** simultáneamente con **Set( x, 2 ); Set( y, x+2 )**. En este caso, las dependencias dentro de las fórmulas están bien: **a** se establece antes de **b** y **x** se establece antes de **y**.

Según el dispositivo o explorador en el que se ejecute la aplicación, es posible que solo un puñado de fórmulas se evalúen realmente de forma simultánea. **Concurrent** usa las capacidades disponibles y no finaliza hasta que se han evaluado todas las fórmulas.

Si habilita **Administración de errores a nivel de fórmula** (en Configuración avanzada), se devuelve el primer error detectado en el orden de los argumentos de **Concurrent**; en caso contrario, se devuelve *blank*. Si todas las fórmulas son correctas, se devuelve *true*. Si se produce un error en una fórmula, se detiene el resto de la fórmula, pero las demás fórmulas se siguen evaluando.

Solo puede usar **Concurrent** en [fórmulas de comportamiento](../working-with-formulas-in-depth.md).

## <a name="syntax"></a>Sintaxis
**Concurrent**( *Formula1*, *Formula2* [, ...] )

* *Formula(s)*: requerido. Fórmulas que se van a evaluar de forma simultánea. Se deben proporcionar al menos dos fórmulas.

## <a name="examples"></a>Ejemplos

#### <a name="loading-data-faster"></a>Carga de datos más rápida

1. Creación de una aplicación y agregar cuatro orígenes de datos de Common Data Service, SQL Server o SharePoint. 

    En este ejemplo se usan cuatro tablas de la [base de datos de ejemplo Adventure Works en SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-portal). Después de crear la base de datos, conéctese a ella desde PowerApps con el nombre de servidor completo (por ejemplo, srvname.database.windows.net):

    ![Conexión a la base de datos Adventure Works en Azure](media/function-concurrent/connect-database.png)

2. Agregue un control **[Botón](../controls/control-button.md)** y establezca su propiedad **OnSelect** en esta fórmula:

    ```powerapps-dot
    ClearCollect( Product, '[SalesLT].[Product]' );
    ClearCollect( Customer, '[SalesLT].[Customer]' );
    ClearCollect( SalesOrderDetail, '[SalesLT].[SalesOrderDetail]' ); 
    ClearCollect( SalesOrderHeader, '[SalesLT].[SalesOrderHeader]' )
    ```

3. En [Microsoft Edge](https://docs.microsoft.com/microsoft-edge/devtools-guide/network) o [Google Chrome](https://developers.google.com/web/tools/chrome-devtools/network-performance/), active las herramientas de desarrollador para supervisar el tráfico de red mientras se ejecuta la aplicación.

1. (Opcional) Active el límite de red para exagerar los efectos de esta comparación.

4. Mientras mantiene presionada la tecla Alt, seleccione el botón y luego observe el tráfico de red.

    Las herramientas muestran cuatro solicitudes realizadas en serie similares a este ejemplo.  Se han quitado los tiempos reales, ya que van a variar mucho.  El gráfico muestra que cada llamada se inicia una vez finalizada la última:

    ![Gráfico de tiempo de cuatro solicitudes de red, que se inician una vez que finaliza la última, que abarca todo el intervalo de tiempo](media/function-concurrent/chained-network.png)

5. Guarde, cierre y vuelva a abrir la aplicación.

    PowerApps almacena los datos en caché, por lo que al volver a seleccionar el botón no se realizan necesariamente cuatro nuevas solicitudes. Cada vez que quiera probar el rendimiento, cierre y vuelva a abrir la aplicación. Si ha activado el límite de red, puede desactivarlo hasta que esté listo para otra prueba.

1. Agregue un segundo control **[Botón](../controls/control-button.md)** y establezca su propiedad **OnSelect** en esta fórmula:

    ```powerapps-dot
    Concurrent( 
        ClearCollect( Product, '[SalesLT].[Product]' ), 
        ClearCollect( Customer, '[SalesLT].[Customer]' ),
        ClearCollect( SalesOrderDetail, '[SalesLT].[SalesOrderDetail]' ),
        ClearCollect( SalesOrderHeader, '[SalesLT].[SalesOrderHeader]' )
    )
    ```

    Observe que ha agregado las mismas llamadas **ClearCollect** al primer botón, pero que esta vez están encapsuladas en una función **Concurrent** y separadas por comas.

2. Desactive la supervisión de red en el explorador.

1. Si antes estaba usando el límite de red, vuelva a activarlo.

3. Mientras mantiene presionada la tecla Alt, seleccione el segundo botón y luego observe el tráfico de red.

    Las herramientas muestran cuatro solicitudes realizadas de forma simultánea similares a este ejemplo.  Una vez más, se han quitado los tiempos reales, ya que van a variar mucho.  El gráfico muestra que todas las llamadas se inician aproximadamente al mismo tiempo y no esperan a que finalice la anterior:

    ![Gráfico de tiempo de cuatro solicitudes de red, que se inician a la vez, que abarca aproximadamente la mitad del intervalo de tiempo](media/function-concurrent/concurrent-network.png)

    Estos gráficos se basan en la misma escala. Al usar **Concurrent**, se ha reducido a la mitad la cantidad total de tiempo que estas operaciones han tardado en terminar. 

5. Guarde, cierre y vuelva a abrir la aplicación.

#### <a name="race-condition"></a>Condición de carrera

1. Agregue una conexión al servicio [Microsoft Translator](../connections/connection-microsoft-translator.md) a la aplicación.

2. Agregue un control [**Entrada de texto**](../controls/control-text-input.md) y, si tiene otro nombre, cámbielo a **TextInput1**.

3. Agregue un control **Botón** y establezca su propiedad **OnSelect** en esta fórmula:

    ```powerapps-dot
    Set( StartTime, Value( Now() ) );
    Concurrent(
        Set( FRTrans, MicrosoftTranslator.Translate( TextInput1.Text, "fr" ) ); 
            Set( FRTransTime, Value( Now() ) ),
        Set( DETrans, MicrosoftTranslator.Translate( TextInput1.Text, "de" ) ); 
            Set( DETransTime, Value( Now() ) )
    );
    Collect( Results,
        { 
            Input: TextInput1.Text,
            French: FRTrans, FrenchTime: FRTransTime - StartTime, 
            German: DETrans, GermanTime: DETransTime - StartTime, 
            FrenchFaster: FRTransTime < DETransTime
        }
    )
    ```

4. Agregue un control [**Tabla de datos**](../controls/control-data-table.md) y establezca su propiedad **Items** en **Results**.

1. En la pestaña **Propiedades** del panel derecho, seleccione **Resultados** para abrir el panel **Datos**.

1. En la lista de campos, active la casilla de cada campo para mostrarlos todos en la tabla de datos.

1. (Opcional) Arrastre el campo **Input** a la parte superior de la lista y el campo **FrenchFaster** a la parte inferior.

    ![Lista de campos de la colección de resultados](media/function-concurrent/field-list.png) 

6. En el control **Entrada de texto**, escriba o pegue una frase que quiera traducir.

7. Mientras mantiene presionada la tecla Alt, seleccione el botón varias veces para rellenar la tabla.

    Las horas se muestran en milisegundos.
  
    ![Visualización de la tabla de datos que contiene los resultados de la traducción de la cadena "Hello World" a francés y alemán. Unas veces la traducción al francés es más rápida que al alemán y otras justo lo contrario.](media/function-concurrent/race-condition.png) 

    En algunos casos, la traducción al francés es más rápida que la traducción al alemán y viceversa. Ambas se inician al mismo tiempo, pero una se devuelve antes que la otra por diversos motivos, incluidos el procesamiento de servidor y la latencia de red.

    Se produce una [condición de carrera](https://en.wikipedia.org/wiki/Race_condition) si la aplicación dependía de que una traducción terminara primero. Afortunadamente, PowerApps marca la mayoría de las dependencias de tiempo que puede detectar.
