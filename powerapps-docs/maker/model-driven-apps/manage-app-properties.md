---
title: Administrar propiedades de aplicaciones basadas en modelos en el diseñador de aplicaciones de PowerApps | MicrosoftDocs
description: Obtenga información sobre cómo administrar las propiedades de la aplicación
keywords: ''
ms.date: 02/05/2019
ms.service: powerapps
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
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: a4f28dd878ca2e862a99982564066eefacfb7892
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2701903"
---
# <a name="manage-model-driven-app-properties-in-the-app-designer"></a>Administrar las propiedades de aplicaciones controladas por modelos en el diseñador de aplicaciones

Las propiedades de la aplicación definen detalles importantes acerca la aplicación, como su título o dirección URL. Defina propiedades de la aplicación al crear una aplicación. Si desea cambiar esas propiedades más adelante, puede hacerlo en el diseñador de la aplicación.  
  
1.  En el diseñador de aplicaciones, en el lado derecho, seleccione la pestaña **Propiedades**.  

    > [!div class="mx-imgBorder"] 
    > ![Panel Propiedades del diseñador de la aplicación](media/app-designer-properties-tab.png "Panel Propiedades del diseñador de la aplicación")  
  
2.  Cambie la información si lo desea:  

    |Propiedad|Descripción|  
    |--------------|-----------------|
    |**Nombre**|Escriba un nombre único y significativo para la aplicación.|  
    |**Descripción**|Escriba una breve descripción de qué es la aplicación.|  
    |**Icono**|De forma predeterminada, la casilla **Usar aplicación predeterminada** está activada. Para seleccionar otro recurso web como icono para la aplicación, desactive la casilla y seleccione un icono de la lista desplegable. Este icono se muestra en la ventana de vista previa de la aplicación.|
    |**Nombre único**| No puede cambiar el nombre único. Con el nombre único, puede consultar tablas para obtener datos de la base de datos.|
    |**App URL Suffix<sup>1</sup>**| La dirección URL que elija mientras crea la aplicación se muestra aquí de forma predeterminada. Puede cambiar la dirección URL de la aplicación en el cuadro de diálogo **Administrar aplicación**. Tenga en cuenta que en este momento no se puede exportar o importar el sufijo de la dirección URL de la aplicación mediante una solución.|
    |**Elija una página de bienvenida para la aplicación**|Esta opción permite elegir entre los recursos web disponibles en su entorno. Las páginas de bienvenida que cree pueden contener información útil para los usuarios, como vínculos a los vídeos, instrucciones de actualización o información de introducción. Para obtener más información acerca de cómo crear un recurso web, por ejemplo, un archivo HTML que pueda usar como página de bienvenida, consulte [Crear y editar recursos web para extender la aplicación web](create-edit-web-resources.md).|
    |**Habilitar Mobile Offline**|Esta opción permite que la aplicación esté disponible sin conexión en móviles a los perfiles que se seleccionan con la lista desplegable **Perfiles de Mobile Offline**.|

    <sup>1</sup>Las propiedades **Client** y **App URL Suffix** ya no están disponibles cuando se crea una nueva aplicación.
3.  Guardar la aplicación.  
  
## <a name="next-steps"></a>Pasos siguientes  
 [Creación o edición de aplicaciones](create-edit-app.md)
