---
title: 'Control Icono de Power BI: referencia | Microsoft Docs'
description: Información sobre el control Icono de Power BI, con propiedades y ejemplos
documentationcenter: na
author: fikaradz
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 07/07/2016
ms.author: fikaradz
ms.openlocfilehash: e7bc2e7e0aafa4d933c47bcf47300dc243c38523
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "31827152"
---
# <a name="power-bi-tile-control-in-powerapps"></a>Control Icono de Power BI en PowerApps
Control que muestra un icono de [Power BI ](https://powerbi.microsoft.com) dentro de una aplicación.

## <a name="description"></a>Descripción
Para sacar provecho de las funciones de informes y análisis de datos existentes, muestre sus **[iconos de Power BI](https://docs.microsoft.com/power-bi/service-dashboard-tiles)** dentro de las aplicaciones.  Para seleccionar el icono que desea mostrar, establezca las propiedades **Área de trabajo**, **Panel** e **Icono**  en la pestaña **Datos** del panel de opciones.

## <a name="sharing-and-security"></a>Recursos compartidos y seguridad
Una vez compartida, la aplicación de PowerApps será accesible a todos los usuarios que tengan permisos para acceder a la aplicación.  Sin embargo, para que el contenido de Power BI sea visible para esos usuarios, es necesario [compartir](https://docs.microsoft.com/power-bi/service-how-to-collaborate-distribute-dashboards-reports) el panel de dónde procede el icono con los usuarios en Power BI.  Esto garantiza que se respetarán los permisos de uso compartido de Power BI cuando se acceda al contenido de Power BI en una aplicación.

## <a name="key-properties"></a>Propiedades principales
**Área de trabajo**: área de trabajo de Power BI de dónde procede el mosaico.

**Panel**: panel de Power BI de dónde procede el mosaico.

**Icono**: nombre del icono de Power BI que desea mostrar.

## <a name="additional-properties"></a>Propiedades adicionales
**[BorderColor](properties-color-border.md)**: el color de un borde del control.

**[BorderStyle](properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)**: el grosor de un borde del control.

**[DisplayMode](properties-core.md)**: indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[Height](properties-size-location.md)**: la distancia entre los bordes superior e inferior de un control.

**[OnSelect](properties-core.md)**: indica cómo responde la aplicación cuando el usuario toca o hace clic en un control. El comportamiento predeterminado es llevar al usuario al informe de Power BI asociado al icono.

**[Visible](properties-core.md)**: indica si un control aparece o está oculto.

**[Width](properties-size-location.md)**: la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)**: la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)**: la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="example"></a>Ejemplo
1. Agregue un control **Icono de Power BI** desde la pestaña **Insertar**, menú **Controles**.  
2. En la pestaña **Datos** del panel de opciones, elija "Mi área de trabajo" como valor de la opción **Área de trabajo**.  Elija un panel en la lista de paneles y un icono en la lista de iconos.
   
    El control representa el icono de Power BI.
   
    ¿No sabe cómo [agregar y configurar un control](../add-configure-controls.md)?
   
   ¿No tiene Power BI? [Regístrese](https://docs.microsoft.com/power-bi/service-self-service-signup-for-power-bi).


## <a name="accessibility-guidelines"></a>Directrices de accesibilidad
El **icono de Power BI** es simplemente un contenedor de contenido de Power BI. Aprenda a crear contenido accesible con estas [sugerencias de accesibilidad de Power BI](https://docs.microsoft.com/power-bi/desktop-accessibility).

### <a name="screen-reader-support"></a>Soporte técnico para el lector de pantalla
* Considere la posibilidad de agregar un encabezado mediante un control **[Etiqueta](control-text-box.md)** si el contenido de Power BI no tiene un icono. El encabezado puede colocarse inmediatamente delante del **icono de Power BI**.
