---
title: Administración de propiedades de aplicaciones basadas en modelos en el diseñador de aplicaciones de PowerApps | MicrosoftDocs
description: Aprenda a administrar las propiedades de la aplicación.
keywords: ''
ms.date: 06/27/2018
ms.service: crm-online
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: e773e60f-0211-4c4b-a1af-663be4997629
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: 14
topic-status: Drafting
ms.openlocfilehash: 62129690a0f5969b6f0f749e110eca001f2c0c8b
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39701390"
---
# <a name="manage-model-driven-app-properties-in-the-app-designer"></a>Administración de propiedades de aplicaciones basadas en modelos en el diseñador de aplicaciones

Las propiedades de aplicaciones definen detalles importantes sobre la aplicación, como su título o dirección URL. Las propiedades de las aplicaciones se definen al crear una aplicación. Si quiere cambiar las propiedades más adelante, puede hacerlo en el diseñador de aplicaciones.  
  
1.  En el diseñador de aplicaciones, en el lado derecho, seleccione la pestaña **Propiedades**.  
  
    ![Panel de propiedades del diseñador de aplicaciones](media/app-designer-properties-tab.png "App designer Properties pane")  
  
2.  Cambie la información, según sea necesario:  

    |Propiedad|Descripción|  
    |--------------|-----------------|
    |**Nombre**|Escriba un nombre único y descriptivo para la aplicación.|  
    |**Description**|Escriba una descripción corta del tipo de aplicación.|  
    |**Icono**|De forma predeterminada, se activa la casilla **Use Default App** (Usar aplicación predeterminada). Para seleccionar un recurso web diferente como icono de la aplicación, desactive la casilla y, luego, seleccione un icono de la lista desplegable. Este icono se muestra en el icono de vista previa de la aplicación.|
    |**Nombre único**| No se puede cambiar el nombre único. Con el nombre único, puede consultar tablas de consulta para obtener datos de la base de datos.| 
    |**Cliente**|Define el tipo de cliente que se usará para la aplicación.<br/>-  **Web:** es el cliente clásico del explorador web de Dynamics 365 Customer Engagement.<br/>-  **Interfaz unificada:** es el nuevo cliente del explorador web que tiene una interfaz similar en dispositivos móviles y PC.|
    |**Sufijo de la URL de aplicación**| Aquí se muestra de forma predeterminada la dirección URL que eligió al crear la aplicación. Puede cambiar la dirección URL de la aplicación en el cuadro de diálogo **Administrar aplicación**. Tenga en cuenta que, en este momento, no se puede exportar ni importar el sufijo de dirección URL de la aplicación mediante una solución.|
    |**Elija una página de bienvenida para la aplicación**|Esta opción le permite seleccionar entre los recursos web disponibles en su entorno. Las páginas de bienvenida que cree pueden contener información útil para los usuarios como vínculos a vídeos, instrucciones de actualización o información de primeros pasos. Para más información sobre cómo crear un recurso web, como un archivo HTML que pueda usar como página de bienvenida, consulte [Crear o editar recursos web para extender la aplicación web](create-edit-web-resources.md).|
    |**Habilitar Mobile Offline**|Esta opción permite que la aplicación esté disponible sin conexión en dispositivos móviles para los perfiles que se seleccionan mediante la lista desplegable **Perfiles de Mobile Offline**.|
  
3.  Guarde la aplicación.  
  
## <a name="next-steps"></a>Pasos siguientes  
 [Creación o edición de una aplicación](create-edit-app.md)
