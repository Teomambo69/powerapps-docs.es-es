---
title: Agregar navegación de formulario de aplicación controlada por modelos para entidades relacionadas en Power Apps | MicrosoftDocs
description: Aprenda a agregar navegación de formulario para entidades relacionadas
ms.custom: ''
ms.date: 03/18/2020
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
author: Mattp123
ms.assetid: b4098c96-bce1-4f57-804f-8694e6254e81
caps.latest.revision: 15
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: da8842d2c83761fff2730b09b4b39f058da6e5d1
ms.sourcegitcommit: 9f2694bd14d70798310b89a4673672c1bfad989d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/26/2020
ms.locfileid: "3166990"
---
# <a name="add-model-driven-app-form-navigation-for-related-entities"></a>Agregar navegación de formulario de aplicación controlada por modelos para entidades relacionadas

En este tema, usará el panel de navegación de formulario que se usa para agregar vínculos a las entidades relacionadas. Cuando el usuario de una aplicación hace clic en uno de estos vínculos en un registro, se muestra la vista asociada para la entidad.   
  
1.  Inicie sesión en [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).  

2.  Expanda **Datos**, seleccione **Entidades**, seleccione la entidad que desee y, a continuación, seleccione la pestaña **Formularios**. 
  
3.  En la lista, abra un formulario con el tipo **Principal** para editarlo.

4.  Seleccione **Cambiar a clásico** para editar el formulario en el diseñador de formularios clásico.
  
5.  Para agregar un vínculo a una entidad relacionada, en la pestaña **Inicio**, en el grupo **Seleccionar**, elija **Navegación**.  
  
     El panel **Explorador de relaciones** se abre en la parte derecha del editor de formularios.  
  
6.  En el panel **Explorador de relaciones**, en la lista **Filtro**, seleccione una de las siguientes opciones:  
  
    - **Relaciones disponibles**. Muestra todas las entidades que pueden relacionarse con la entidad con la que está asociado el formulario.  
  
    - **Relaciones de 1:N**. Muestra las entidades que pueden relacionarse en una relación de 1:N con la entidad con la que está asociado el formulario.  
  
    - **Relaciones de N:N**. Muestra las entidades que pueden relacionarse en una relación de N:N con la entidad con la que está asociado el formulario.  
  
    > [!NOTE]
    >  Si no aparece ninguna entidad relacionada en el panel **Explorador de relaciones**, no puede crear un vínculo en este formulario con una entidad relacionada.  
  
7.  Seleccione la entidad relacionada con la que desea establecer el vínculo, arrástrela hasta el Panel de navegación y colóquela donde desee que se muestre.  
  
    > [!TIP]
    >  También puede crear una nueva relación eligiendo **Nueva 1:N** o **Nueva N:N** en el panel **Explorador de relaciones**.   
  
8. Para modificar las propiedades de este o cualquier otro vínculo a una entidad relacionada en el Panel de navegación, seleccione el vínculo y, a continuación, en la pestaña **Inicio** elija **Cambiar propiedades**.  
  
9. En el cuadro de diálogo **Propiedades de la relación**, en la pestaña **Mostrar**, escriba una nueva etiqueta para mostrar.  
  
10. En la pestaña **Nombre**, elija **Editar** para ver o modificar los detalles asociados con el registro de relación.  
  
11. Elija **Aceptar**.  
  
12. Obtenga una vista previa para comprobar cómo aparecerá el formulario principal y cómo funcionarán los eventos:  
  
    1.  En la pestaña **Inicio**, elija **Vista previa** y, a continuación, seleccione **Formulario de creación**, **Formulario de actualización** o **Formulario de sólo lectura**.  
  
    2.  Para cerrar el formulario **Vista previa**, en el menú **Archivo**, elija **Cerrar**.  
  
13. Cuando haya terminado de modificar el formulario, elija **Guardar y cerrar** para cerrarlo.  
  
14. Cuando haya completado las personalizaciones, publíquelas:  
  
    -   Para publicar las personalizaciones únicamente para el componente que está editando actualmente, en la barra de navegación o en el panel de navegación, elija la entidad en la que ha estado trabajando, y elija **Publicar**.  
  
    -   Para publicar personalizaciones de todos los componentes no publicados a la vez, en el Panel de navegación, elija **Entidades** y, en la barra de comandos, elija **Publicar todas las personalizaciones**.  
  
> [!NOTE]
> La instalación de una solución o la publicación de personalizaciones puede interferir en el funcionamiento normal del sistema. Le recomendamos que programe la importación de una solución cuando perjudique lo menos posible a los usuarios.
  
## <a name="next-steps"></a>Pasos siguientes  
 [Crear y editar relaciones entre entidades para Common Data Service](../common-data-service/create-edit-entity-relationships.md)
