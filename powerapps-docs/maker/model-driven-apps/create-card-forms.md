---
title: Crear un formulario de tarjeta con Power Apps | MicrosoftDocs
description: Aprenda a crear y usar los formularios de tarjeta en Power Apps
keywords: ''
ms.date: 03/05/2019
ms.service: powerapps
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
author: Mattp123
ms.assetid: be93b9d7-f1c2-4ee7-8d7c-0f5c34dfa5f7
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
topic-status: Drafting
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 2e39935c3373974bd968c93ee0fce2743f39360d
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "2884977"
---
# <a name="create-a-card-form"></a>Crear un formulario de tarjeta
Los formularios de tarjeta se utilizan en vistas para aplicaciones de la interfaz unificada. Los formularios de tarjeta están diseñados para mostrar información en un formato compacto adecuado para dispositivos móviles. Por ejemplo, el formulario de tarjeta predeterminado para la vista Mis cuentas activas define la información mostrada para cada registro de cuenta. 

> [!div class="mx-imgBorder"] 
> ![](media/account-cardform-for-myactiveaccounts-view.png "Account card form for my active accounts view")

Aunque los formularios de tarjeta se pueden crear y editar igual que otros tipos de formularios, los formularios de tarjeta se agregan a aplicaciones de forma diferente. En lugar de agregar un formulario como componente de aplicación, los formularios de tarjeta personalizados se agregan a vistas mediante el control **Cuadrícula de solo lectura**. 

## <a name="create-a-card-form"></a>Crear un formulario de tarjeta
1. Para crear un formulario de tarjeta, inicie sesión en [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc). 
2. Expanda **Datos**, seleccione **Entidades**, seleccione la entidad que desee y, a continuación, seleccione la pestaña **Formularios**.
3. En la barra de herramientas, seleccione **Agregar formulario** y luego seleccione **Formulario de tarjeta**. Como alternativa, puede abrir un **Tipo de formulario** existente que sea un formulario de **Tarjeta** para editarlo.
4. Agregue los campos que desee. Se recomienda limitar el número de campos para que el formulario se muestre correctamente en pantallas pequeñas. 
5. Seleccione **Guardar** y, a continuación, **Publicar**. 

## <a name="add-a-card-form-to-a-view"></a>Agregar un formulario de tarjeta a una vista 
1. Inicie sesión en [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).
2. Expanda **Datos**, seleccione la entidad que desee y, a continuación, seleccione la pestaña **Vistas**.
3. Seleccione la vista que desee y, en la barra de herramientas del diseñador de vistas, seleccione **Cambiar a clásica**.
4. Seleccione **Controles personalizados** del panel **Tareas comunes**.
5. Seleccione **Agregar control** de la lista de controles, seleccione **Cuadrícula de solo lectura** y, a continuación, seleccione **Agregar**.

   > [!NOTE]
   > Hay dos controles de cuadrícula de solo lectura. El control de cuadrícula de solo lectura predeterminado que se llama **Cuadrícula de solo lectura (predeterminada)** no admite formularios de tarjeta personalizados. 

6. En la página de propiedades **Cuadrícula de solo lectura** configure las propiedades siguientes y, a continuación seleccione **Aceptar**. 
   - **Formulario de tarjeta**. Seleccione el icono de lápiz ![Editar propiedades de control](media/ccf-pencil-icon.png) y luego seleccione el formulario de tarjeta que desea mostrar en la vista. De forma predeterminada, entidad principal asociada a la vista ya está seleccionada, pero puede cambiarla. 
   - **Comportamiento de redistribución**. Si desea cambiar si el formulario de tarjeta se muestra al cambiar de tamaño, seleccione el icono de lápiz ![Editar propiedades de control](media/ccf-pencil-icon.png). Más información: [Permitir que la cuadrícula se redistribuya en la lista](specify-properties-for-unified-interface-apps.md#allow-grid-to-reflow-into-list)  
   - Seleccione los tipos de clientes: **Web**, **Teléfono**, o **Tableta**, donde desea que se muestre el control de **Cuadrícula de solo lectura**.

     ![Cuadrícula de solo lectura para formulario de tarjeta](media/read-only-grid-for-cardform.png)

7. Seleccione **Aceptar** para cerrar la página de propiedades de **Controles personalizados**. 
8. En la barra de herramientas del diseñador de vistas clásica, seleccione **Guardar y cerrar**. 

## <a name="see-also"></a>Vea también
[Usar controles personalizados para visualizaciones de datos de aplicaciones controladas por modelos](use-custom-controls-data-visualizations.md)



