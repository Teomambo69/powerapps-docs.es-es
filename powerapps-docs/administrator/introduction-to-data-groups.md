---
title: Grupos de datos | Microsoft Docs
description: Tutorial de cómo usar grupos de datos en PowerApps.
author: manasmams
manager: kvivek
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: manasma
search.audienceType:
- admin
search.app:
- D365CE
- PowerApps
- Powerplatform
ms.openlocfilehash: e2424207cdc70f2f8135fa6ef5559cec2fc637d9
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42834007"
---
# <a name="data-groups"></a>Grupos de datos
Los grupos de datos son una manera sencilla de clasificar servicios dentro de una [directiva de prevención de pérdida de datos (DLP)](prevent-data-loss.md). Los dos grupos de datos disponibles son el grupo **Business data only** (Solo datos empresariales) y el grupo **No business data allowed** (No se permiten datos empresariales). Las organizaciones pueden determinar libremente qué servicios se colocan en un grupo de datos determinado. Una buena manera de clasificar servicios es colocarlos en grupos, según el impacto sobre la organización. De forma predeterminada, todos los servicios se colocan en el grupo de datos **No business data allowed** (No se permiten datos empresariales). Se administran los servicios en un grupo de datos cuando se crean o modifican las propiedades de una directiva DLP desde el centro de administración.

## <a name="how-data-is-shared-between-data-groups"></a>Cómo se comparten datos entre grupos de datos
No se pueden compartir datos entre servicios ubicados en diferentes grupos. Por ejemplo, si coloca SharePoint y Salesforce en el grupo **Business data only** (Solo datos empresariales) y coloca Facebook y Twitter en el grupo **No business data allowed** (No se permiten datos empresariales), no se puede crear una aplicación de PowerApps que mueva datos entre SharePoint y Facebook. Aunque no se pueden compartir datos entre servicios de diferentes grupos, puede compartirlos entre los servicios de un grupo concreto. Por lo tanto, volviendo al ejemplo anterior, puesto que SharePoint y Salesforce se colocaron en el mismo grupo de datos, las aplicaciones de PowerApps creadas por los usuarios finales pueden compartir datos entre SharePoint y Salesforce. El punto clave es que los servicios de un grupo específico pueden compartir datos, mientras que los de grupos diferentes no pueden hacerlo.

Además, se debe designar un grupo de datos como *predeterminado*. Inicialmente, el grupo **No business data allowed** (No se permiten datos empresariales) es el *predeterminado* y contiene todos los servicios. Un administrador puede cambiar el grupo de datos predeterminado a **Business data only** (Solo datos empresariales). 

> [!NOTE]
> Todos los servicios nuevos que se agreguen a PowerApps se colocarán en el grupo designado como *predeterminado*. Por este motivo, se recomienda que mantenga **No business data allowed** (No se permiten datos empresariales) como grupo predeterminado y agregue manualmente servicios al grupo **Business data only** (Solo datos empresariales) una vez que su organización haya evaluado el impacto de permitir que se compartan datos empresariales con el nuevo servicio.

## <a name="add-services-to-a-data-group"></a>Agregar servicios a un grupo de datos
En este tutorial, se agrega SharePoint y Salesforce al grupo de datos **Business data only** (Solo datos empresariales) de una directiva de prevención de pérdida de datos (DLP).

1. Seleccione el vínculo **+ Agregar** situado en el cuadro de grupo **Business data only** (Solo datos empresariales) de una directiva DLP:    
   ![Imagen de Agregar](./media/introduction-to-data-groups/add-to-data-group-1.png)  
2. Seleccione SharePoint y Salesforce, y después **Agregar servicios** para agregar ambos al grupo Business data only (Solo datos empresariales):    
   ![Imagen de Agregar servicios](./media/introduction-to-data-groups/add-to-data-group-2.png)  
3. Seleccione **Guardar directiva** en el menú en la parte superior:  
   ![Guardar directiva](./media/introduction-to-data-groups/add-to-data-group-4.png)
4. Observe que ahora SharePoint y Salesforce están en grupo Business data only (Solo datos empresariales):  
   ![grupo de datos empresariales actualizado](./media/introduction-to-data-groups/add-to-data-group-3.png)   

En este tutorial, ha agregado SharePoint y Salesforce al grupo de datos **Business data only** (Solo datos empresariales) de una directiva DLP. Si una de las personas que forma parte del entorno de la directiva DLP crea una aplicación que comparte datos entre SharePoint o Salesforce y cualquier servicio del grupo de datos **No business data allowed** (No se permiten datos empresariales), no se permitirá la ejecución de la aplicación.

## <a name="remove-services-from-a-data-group"></a>Quitar servicios de un grupo de datos
Puesto que todos los servicios deben estar en uno de los grupos de datos disponibles, para quitar un servicio de uno concreto, basta con agregar el servicio a otro y guardar la directiva.  

## <a name="change-the-default-data-group"></a>Cambiar el grupo de datos predeterminado
En este tutorial, se cambiará el grupo de datos predeterminado de **No business data allowed** (No se permiten datos empresariales) al grupo de datos **Business data only** (Solo datos empresariales).  

> [!IMPORTANT]
> Todos los servicios nuevos que se agreguen a PowerApps se colocarán en el grupo designado como *predeterminado*. Por este motivo, se recomienda que mantenga **No business data allowed** (No se permiten datos empresariales) como grupo predeterminado y agregue manualmente servicios al grupo **Business data only** (Solo datos empresariales).

1. Seleccione el botón **...** situado en la esquina superior derecha del grupo de datos que desee designar como predeterminado:    
   ![cambiar de grupo predeterminado](./media/introduction-to-data-groups/default-data-group-0.png)  
2. Seleccione **Establecer como grupo predefinido**:  
   ![cambiar de grupo predeterminado](./media/introduction-to-data-groups/default-data-group-1.png)   
3. Seleccione **Guardar directiva** en el menú en la parte superior:  
   ![cambiar de grupo predeterminado](./media/introduction-to-data-groups/add-to-data-group-4.png)
4. Observe que el grupo de datos ahora está designado como predeterminado:  
   ![cambiar de grupo predeterminado](./media/introduction-to-data-groups/default-data-group-2.png)   

## <a name="next-steps"></a>Pasos siguientes
* [Aprender más sobre las directivas de prevención de pérdida de datos (DLP)](prevent-data-loss.md)
* [Aprender más acerca de los entornos](environments-overview.md)
* [Aprender más acerca de Microsoft PowerApps](../maker/canvas-apps/getting-started.md)
