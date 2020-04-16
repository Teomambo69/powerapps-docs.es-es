---
title: Especificar propiedades para aplicaciones controladas por modelos de Interfaz unificada en Power Apps | MicrosoftDocs
description: Aprenda a configurar el control de cuadrícula para la aplicación
keywords: ''
ms.date: 06/03/2019
ms.service: powerapps
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 3ecea4a7-0d18-4ccd-9609-3a62179e9e1b
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: 0
topic-status: Drafting
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 25e6125476ae3e5ceac47b0ef6b45f67ccfc1d3f
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "3125857"
---
# <a name="specify-properties-for-model-driven-unified-interface-apps"></a>Especificar propiedades para aplicaciones controladas por modelos de Interfaz unificada

El marco de interfaz unificada usa principios de diseño dinámicos para ofrecer una experiencia de visualización e interacción óptima para cualquier tamaño de pantalla u orientación. Con las aplicaciones basadas en modelos que usan el marco de interfaz unificada, el control de cuadrícula (vista) es dinámico. Como el tamaño del contenedor disminuye , por ejemplo, en los teléfonos y los puntos de visión más pequeños, la cuadrícula se transforma en una lista. 

El control de cuadrícula de solo lectura especifica cómo debe ajustar una cuadrícula al tamaño de pantalla diferente. Como creador de aplicaciones, si trabaja con una aplicación de interfaz unificada, puede configurar el control de cuadrícula de solo lectura y sus propiedades paras cuadrículas y listas personalizadas.
- Propiedad **Formulario de tarjeta**: utilizar un formulario de tarjeta para listas en lugar de la plantilla de lista predeterminada. Los formularios de tarjeta proporcionan más información para mostrar los elementos que la plantilla de lista predeterminada.
- Propiedad de **Comportamiento de redistribución**: use este parámetro para especificar si redistribuir una cuadrícula en una lista o no.

## <a name="allow-grid-to-reflow-into-list"></a>Permitir redistribuir cuadrícula en la lista

Cuando se agrega el control de cuadrícula de solo lectura a la lista de controles le permite configurar las características siguientes: 
- Permite redistribuir una cuadrícula en una lista en pantallas más pequeñas como móviles.
- Especifique el modo de representación como solo cuadrícula o solo lista.  

1. Abra el [explorador de soluciones](advanced-navigation.md#solution-explorer).
2. En el panel de navegación **Entidades**, seleccione la entidad correspondiente (como **Cuenta** o **Contacto**) y, después, en la ficha **Controles**, seleccione **Agregar control**.

    ![Abrir Agregar control](media/UnifiedInterface_ReadOnlyGrid_AddControl.png "Abrir Agregar control")

3. Seleccione **Cuadrícula de solo lectura** de la lista de controles y elija **Agregar**.

    El control se agrega a la lista de controles disponibles.
   
    ![Seleccionar un control](media/UnifiedInterface_ReadOnlyGrid_SelectControl.png "Seleccionar un control")
    
4. Seleccione los dispositivos (**Web**, **teléfono**, o **Tableta**) para el que desea realizar la cuadrícula de solo lectura.

    ![Seleccionar el tipo de dispositivo](media/UnifiedInterface_ReadOnlyGrid_SelectDevice.png "Seleccionar dispositivos")

5. Configure la propiedad **Formulario de tarjeta**.

    Puede usar la propiedad de formulario de tarjeta para mostrar los artículos de lista en lugar de la plantilla de lista predeterminada. Los formularios de tarjeta proporcionan más información para los elementos de lista que la plantilla de lista predeterminada.    

    a. Elija el icono de lápiz junto a **Formulario de tarjeta**.

    ![Editar formulario de tarjeta](media/UnifiedInterface_ReadOnlyGrid_CardForm.png "Editar formulario de tarjeta")

    b.  Seleccione el tipo de **Entidad** y **Formulario de tarjeta**.

    ![Propiedades de formulario de tarjeta](media/UnifiedInterface_ReadOnlyGrid_CardFormProperties.png "Propiedades de formulario de tarjeta")

    c. Elija **Aceptar**.
6. Configurar la propiedad **Comportamiento de redistribución**. 
    
    a. Elija el icono de lápiz junto a **Comportamiento de redistribución**.

    ![Editar comportamiento de redistribución](media/UnifiedInterface_ReadOnlyGrid_EditReflow.png "Editar comportamiento de redistribución")

    b. Seleccione el tipo de flujo de cuadrícula del desplegable **Enlazar a opciones estáticas**. 

    |Tipo de flujo|Descripción|
    |--------------|--------------------|
    |**Redistribución**|Permite a la cuadrícula mostrarse en modo lista en función de cuando no haya espacio suficiente de visualización.|
    |**Solo cuadrícula**|Restringe la redistribución de la cuadrícula en una lista incluso cuando no haya espacio suficiente de visualización.|
    |**Solo lista**|Muestra solo como una lista, incluso si hay espacio suficiente para mostrar como cuadrícula.|
    
     ![Propiedades de comportamiento de redistribución](media/UnifiedInterface_ReadOnlyGrid_ReflowProperties.png "Propiedades de comportamiento de redistribución")

    c. Elija **Aceptar**.


7.  Guarde y publique los cambios. 


## <a name="conditional-image"></a>Imagen condicional
Puede mostrar un iconos personalizado en lugar de un valor en una lista y establecer la lógica utilizada para seleccionarlos basada en los valores de la columna mediante JavaScript. Para obtener más información acerca de las imágenes condicionales, vea [Mostrar iconos personalizados en lugar de valores en vistas de lista](../common-data-service/display-custom-icons-instead.md).

## <a name="next-steps"></a>Pasos siguientes
[Crear o editar vistas](create-edit-views.md)
