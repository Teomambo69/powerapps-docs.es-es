---
title: 'Control Icono de Power BI: referencia | Microsoft Docs'
description: Información sobre el control Icono de Power BI, con propiedades y ejemplos
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 07/07/2016
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 959f8eaee539febbb7c00441453da9bab23a1812
ms.sourcegitcommit: 263a12aefa72a3d73e07b2660bf1e89eba532a16
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2020
ms.locfileid: "81441774"
---
# <a name="power-bi-tile-control-in-power-apps"></a>Power BI el control de icono en Power apps

Control que muestra un icono de [Power BI ](https://powerbi.microsoft.com) dentro de una aplicación.

¿No tiene Power BI? [Regístrese](https://docs.microsoft.com/power-bi/service-self-service-signup-for-power-bi).

## <a name="description"></a>Descripción

Para sacar provecho de las funciones de informes y análisis de datos existentes, muestre sus **[iconos de Power BI](https://docs.microsoft.com/power-bi/service-dashboard-tiles)** dentro de las aplicaciones. Especifique el icono que quiere mostrar mediante el establecimiento de sus propiedades **Workspace**, **Dashboard** y **Tile** en la pestaña **Datos** del panel de opciones.

## <a name="sharing-and-security"></a>Recursos compartidos y seguridad

Cuando se comparte una aplicación que incluye contenido de Power BI, no solo se debe compartir la propia aplicación, sino también el [panel](https://docs.microsoft.com/power-bi/service-how-to-collaborate-distribute-dashboards-reports) de donde procede el icono. De lo contrario, no aparecerá el contenido de Power BI ni siquiera para los usuarios que abran la aplicación. Las aplicaciones que incluyen contenido de Power BI respetan los permisos de ese contenido.

## <a name="performance"></a>Rendimiento

No se recomienda tener más de tres iconos de Power BI cargados al mismo tiempo dentro de una aplicación. Puede controlar la carga y descarga de iconos si establece la propiedad **LoadPowerBIContent**.

## <a name="pass-a-parameter"></a>Pasar un parámetro

Al pasar un solo parámetro de la aplicación, puede filtrar los resultados que aparecen en un icono de Power BI. Sin embargo, solo se admiten valores de cadena y el operador Equals, y es posible que el filtro no funcione si el nombre de tabla o el nombre de columna contiene espacios.

Para pasar un valor de filtro único, modifique el valor de la propiedad **TileURL** , que sigue esta sintaxis:

```
"https://app.powerbi.com/embed?dashboardId=<DashboardID>&tileId=<TileID>&config=<SomeHash>"
```

En ese valor, anexe esta sintaxis:

```
&$filter=<TableName>/<ColumnName> eq '<Value>'
```

El parámetro filtrará un valor en el conjunto de DataSet del informe en el que se origina el icono. Sin embargo, la característica de filtrado tiene las siguientes limitaciones:

- Solo se puede aplicar un filtro.
- Solo se admite el operador `eq`.
- El tipo de campo debe ser una cadena.

Puede usar campos calculados en el informe Power BI para convertir otros tipos de valor en una cadena o combinar varios campos en uno.

## <a name="key-properties"></a>Propiedades principales

**Área de trabajo**: área de trabajo de Power BI de dónde procede el mosaico.

**Panel**: panel de Power BI de dónde procede el mosaico.

**Tile**: nombre del icono de Power BI que quiere mostrar.

**LoadPowerBIContent**: cuando se establece en true, el contenido de Power BI se carga y se muestra. Cuando se establece en false, el contenido de Power BI se descarga, lo que libera memoria y optimiza el rendimiento.

## <a name="additional-properties"></a>Propiedades adicionales

**[BorderColor](properties-color-border.md)** : el color de un borde del control.

**[BorderStyle](properties-color-border.md)** : si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)** : el grosor de un borde del control.

**[DisplayMode](properties-core.md)** : indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[Height](properties-size-location.md)** : la distancia entre los bordes superior e inferior de un control.

**[OnSelect](properties-core.md)** : indica cómo responde la aplicación cuando el usuario toca o hace clic en un control. De forma predeterminada, se abre el informe de Power BI asociado al icono.

**TileUrl**: dirección URL por medio de la cual se solicita un icono desde el servicio Power BI. Puede pasar un parámetro único en el icono de Power BI si anexa el parámetro a la dirección URL (por ejemplo:… & "&$filter=Town/Province eq '" & ListBox1.Selected.Abbr & "'"). Solo puede usar el operador equals en el parámetro.

**[Visible](properties-core.md)** : indica si un control aparece o está oculto.

**[Width](properties-size-location.md)** : la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)** : la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)** : la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="example"></a>Ejemplo

1. En la pestaña **Insertar**, abra el menú **Controles** y luego agregue un control **Icono de Power BI**.

    ¿No sabe cómo [agregar y configurar un control](../add-configure-controls.md)?

2. En la pestaña **Datos** del panel de opciones, pulse o haga clic en **My Workspace** como valor de **Workspace**.

3. Seleccione un panel en la lista de paneles y luego seleccione un icono en la lista de iconos.

    El control representa el icono de Power BI.

## <a name="accessibility-guidelines"></a>Directrices de accesibilidad

El **icono de Power BI** es simplemente un contenedor de contenido de Power BI. Aprenda a crear contenido accesible con estas [sugerencias de accesibilidad de Power BI](https://docs.microsoft.com/power-bi/desktop-accessibility).

Si el contenido de Power BI no tiene un icono, considere la posibilidad de agregar un encabezado mediante un control **[Etiqueta](control-text-box.md)** para admitir lectores de pantalla. Puede colocar la etiqueta inmediatamente delante del icono de Power BI.
