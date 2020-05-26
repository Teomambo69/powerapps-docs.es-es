---
title: Ordenar registros en una vista de aplicación controlada por modelos en Power Apps | MicrosoftDocs
ms.custom: ''
ms.date: 04/17/2020
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 25f5aa52-56dc-4be5-884e-9346616f665f
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: a89a2c4953f5a78a58ff6717f15a803a7cf58527
ms.sourcegitcommit: 3c6c5594b73abd5ff438d50f3b579d56cef7241c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2020
ms.locfileid: "3285672"
---
# <a name="sort-records-in-a-model-driven-app-view"></a>Ordenar registros en una vista de aplicación controlada por modelos


Al crear o editar una vista puede configurar el criterio de ordenación ascendente o descendente.

Para cambiar el orden de clasificación en el diseñador de vistas, vea [Crear una vista pública en Power Apps](create-edit-views-app-designer.md#create-a-public-view-in-power-apps).

## <a name="change-the-sort-order-using-solution-explorer"></a>Cambiar el orden de clasificación utilizando el explorador de soluciones

1.  Abra el [explorador de soluciones](advanced-navigation.md#solution-explorer), expanda **Entidades**, seleccione la entidad que desee, seleccione **Vistas** y después abra la vista que quiera.

2.  En el diseñador de vistas, seleccione **Configurar orden**.  

    > [!div class="mx-imgBorder"] 
    > ![Configurar la ordenación](media/configure-sorting.png "Configurar la ordenación")
  
3.  En el cuadro de diálogo **Configurar orden**, en la lista **Ordenar por**, seleccione la columna que desea ordenar y, a continuación, seleccione **Orden ascendente** u **Orden descendente**.  
  
4.  Seleccione **Aceptar** para cerrar el cuadro de diálogo **Configurar orden**. 

    > [!IMPORTANT]
    > Las cuadrículas en las aplicaciones Interfaz unificada toman la lista de columnas mostradas del FetchXML subyacente de la vista. Si el FetchXML que se devuelve desde Common Data Service no tiene una columna, entonces esa columna no se muestra. Esto contrasta con la aplicación web clásica, donde si una columna no está presente en FetchXML pero está en LayoutXML, dicha columna se agrega automáticamente a la lista de columnas mostradas. Las aplicaciones de Interfaz unificada usan OData directamente con FetchXML para recuperar datos del servidor.

## <a name="next-steps"></a>Pasos siguientes
[Crear o editar una vista](create-edit-views.md)
[Usar FetchXML para consultar datos](../../developer/common-data-service/use-fetchxml-construct-query.md)
