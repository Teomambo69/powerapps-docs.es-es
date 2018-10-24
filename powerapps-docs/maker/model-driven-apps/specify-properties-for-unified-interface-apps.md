---
title: Definición de propiedades para aplicaciones de interfaz unificada basadas en modelos en PowerApps | Microsoft Docs
description: Obtenga información sobre cómo configurar el control de cuadrícula de la aplicación.
keywords: ''
ms.date: 06/06/2018
ms.service: crm-online
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
ms.openlocfilehash: 007ac566e317ee99bd85ab0675e5a53839800bb4
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39699694"
---
# <a name="specify-properties-for-model-driven-unified-interface-apps"></a>Definición de propiedades para aplicaciones de interfaz unificada basadas en modelos

El marco de interfaz unificada usa principios de diseño dinámico para ofrecer una experiencia de visualización e interacción óptima para cualquier tamaño u orientación de pantalla. Con las aplicaciones basadas en modelos que utilizan el marco de interfaz unificada, el control de cuadrícula (vista) es dinámico. A medida que el tamaño del contenedor se reduce, como, por ejemplo, en teléfonos y ventanillas más pequeñas, la cuadrícula se transforma en una lista. 

El control de cuadrícula de solo lectura especifica cómo se debe redistribuir una cuadrícula para distintos tamaños de pantalla. Como responsable de una aplicación, si está trabajando con una aplicación de interfaz unificada, puede configurar el control de cuadrícula de solo lectura y sus propiedades para las listas y cuadrículas personalizadas.
- Propiedad **Formulario de tarjeta**: use un formulario de tarjeta para las listas en lugar de una plantilla de lista predeterminada. Los formularios de tarjeta proporcionan más elementos de lista que la plantilla de lista predeterminada.
- Propiedad **Comportamiento de redistribución**: use este parámetro para especificar que una cuadrícula se redistribuya en una lista o no.

## <a name="allow-grid-to-reflow-into-list"></a>Permitir que una cuadrícula se redistribuya en una lista

Agregar el control de cuadrícula de solo lectura a la lista de controles permite configurar las siguientes características: 
- Permita que una cuadrícula se redistribuya en una lista en pantallas pequeñas como la de un móvil.
- Especifique el modo de representación como solo cuadrícula o solo lista.  

1. Abra el [Explorador de soluciones](advanced-navigation.md#solution-explorer).
2. En el panel de navegación, expanda **Entidades**, seleccione la entidad correspondiente (como **Cuenta** o **Contacto**) y, después, en la pestaña **Controles**, seleccione **Agregar control**.

    ![Abrir Agregar control](media/UnifiedInterface_ReadOnlyGrid_AddControl.png "Abrir Agregar control")

3. Seleccione **Cuadrícula de solo lectura** en la lista de controles y, después, elija **Agregar**.

    El control se agrega a la lista de controles disponibles.
   
    ![Seleccionar un control](media/UnifiedInterface_ReadOnlyGrid_SelectControl.png "Seleccionar un control")
    
4. Seleccione los dispositivos (**web**, **teléfono** o **tableta**) en los que desea habilitar la cuadrícula de solo lectura.

    ![Seleccione el tipo de dispositivo](media/UnifiedInterface_ReadOnlyGrid_SelectDevice.png "Seleccionar dispositivos")

5. Configurar la propiedad **Formulario de tarjeta**.

    Puede usar la propiedad Formulario de tarjeta para mostrar los elementos de lista en lugar de la plantilla de lista predeterminada. Los formularios de tarjeta proporcionan más elementos de lista que la plantilla de lista predeterminada.    

    a. Elija el icono de lápiz junto a **Formulario de tarjeta**.

    ![Editar formulario de tarjeta](media/UnifiedInterface_ReadOnlyGrid_CardForm.png "Editar formulario de tarjeta")

    b.  Seleccione los tipos **Entidad** y **Formulario de tarjeta**.

    ![Propiedades del formulario de tarjeta](media/UnifiedInterface_ReadOnlyGrid_CardFormProperties.png "Propiedades del formulario de tarjeta")

    c. Seleccione **Aceptar**.
6. Configure la propiedad **Comportamiento de redistribución**. 
    
    a. Elija el icono de lápiz junto a **Comportamiento de redistribución**.

    ![Modificar el comportamiento de redistribución](media/UnifiedInterface_ReadOnlyGrid_EditReflow.png "Comportamiento de redistribución")

    b. Seleccione el tipo de flujo de la cuadrícula en el menú desplegable **Enlazar a opciones estáticas**.
    |Tipo de flujo|Descripción|
    |--------------|--------------------|
    |**Redistribución**|Permite a la cuadrícula realizar representaciones en modo de lista en función de si hay o no suficiente espacio para mostrar.|
    |**Solo cuadrícula**|Restringe la cuadrícula para que se redistribuya en la lista incluso aunque no haya suficiente espacio para mostrar.|
    |**Solo lista**|Se muestra solo como una lista incluso cuando no hay suficiente espacio para mostrar como cuadrícula.|
    
     ![Propiedades del comportamiento de redistribución](media/UnifiedInterface_ReadOnlyGrid_ReflowProperties.png "Propiedades del comportamiento de redistribución")

    c. Seleccione **Aceptar**.


7.  Guarde y publique los cambios. 


## <a name="conditional-image"></a>Imagen condicional
Puede mostrar un icono personalizado en lugar de un valor en una lista y establecer la lógica utilizada para seleccionarlo en función de los valores de una columna mediante el uso de JavaScript. Para más información sobre las imágenes condicionales, vea [Mostrar iconos personalizados en lugar de valores en las vistas de lista](../common-data-service/display-custom-icons-instead.md).

## <a name="next-steps"></a>Pasos siguientes
[Crear o editar una vista](create-edit-views.md)