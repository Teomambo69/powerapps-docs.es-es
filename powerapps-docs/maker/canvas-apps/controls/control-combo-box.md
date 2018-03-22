---
title: 'Control de cuadro combinado: referencia | Microsoft Docs'
description: Información acerca del control de cuadro combinado, incluyendo sus propiedades y ejemplos
services: ''
suite: powerapps
documentationcenter: na
author: fikaradz
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 09/13/2017
ms.author: fikaradz
ms.openlocfilehash: 4d298e24ea967cbf5cb47638d4296f6efbd758c7
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="combo-box-control-in-powerapps"></a>Control de cuadro combinado en PowerApps
Un control que permite a los usuarios seleccionar entre las opciones proporcionadas.  Admite tanto la búsqueda como la selección múltiple.

## <a name="description"></a>Descripción
Con un control de **cuadro combinado** puede buscar los elementos que va a seleccionar.  La búsqueda se realiza en el lado del servidor de la propiedad SearchField, por lo que el rendimiento no se ve afectado por orígenes de datos muy grandes.  

El modo de selección individual o múltiple se configura mediante la propiedad SelectMultiple.

Cuando se buscan elementos que se van a seleccionar, en todos los elementos puede elegir mostrar un valor de datos único, dos valores o una imagen y dos valores (Persona) mediante la modificación de la configuración de diseño en el panel Data (Datos).

## <a name="people-picker"></a>Selector de personas
Para usar **cuadro combinado** como selector de personas, elija la plantilla **Persona** desde la configuración de diseño del panel Data (Datos) y configure las propiedades de datos relacionadas que se mostrará para la persona que aparece a continuación.

## <a name="key-properties"></a>Propiedades principales
**[Items](properties-core.md)**: el origen de datos del que se puede elegir.

**DefaultItems**: los elementos seleccionados inicialmente, antes de que el usuario interactúe con el control.

**SelectedItems**: lista de los elementos seleccionados resultante de la interacción con el usuario.

**SelectMultiple**: si el usuario puede seleccionar un solo elemento o varios.

**IsSearchable**: indica si el usuario puede buscar elementos antes de realizar la selección.

## <a name="additional-properties"></a>Propiedades adicionales
**[BorderColor](properties-color-border.md)**: el color de un borde del control.

**[BorderStyle](properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)**: el grosor de un borde del control.

**[Default](properties-core.md)**: la selección inicial antes de que el usuario la cambie en modo de selección individual.

**DisplayFields**: lista de campos que se muestran en cada elemento que devuelve la búsqueda.  Lo más fácil es configurarlo mediante el panel Datos de la pestaña de la opción Propiedades.

**[DisplayMode](properties-core.md)**: indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[Height](properties-size-location.md)**: la distancia entre los bordes superior e inferior de un control.

**InputTextPlaceholder**: texto informativo que se muestra a los usuarios finales cuando no hay elementos seleccionados.

**OnChange**: cómo responde la aplicación cuando el usuario cambia una selección.

**OnNavigate**: cómo responde la aplicación cuando el usuario hace clic en un elemento.

**[OnSelect](properties-core.md)**: indica cómo responde la aplicación cuando el usuario toca o hace clic en un control.

**[Visible](properties-core.md)**: indica si un control aparece o está oculto.

**[Width](properties-size-location.md)**: la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)**: la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)**: la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="example"></a>Ejemplo
1. Agregue un control de **cuadro combinado** desde la pestaña Insertar, menú Controles.  
2. En la pestaña de opciones Propiedades, haga clic en Datos.  
3. Seleccione el origen de datos, el diseño y las propiedades relacionadas a continuación.
4. Establezca la propiedad **SelectMultiple** en la ficha Opciones avanzadas.

    Aparecerá un **cuadro combinado** funcional en la aplicación.

    ¿No sabe cómo [agregar y configurar un control](../add-configure-controls.md)?
