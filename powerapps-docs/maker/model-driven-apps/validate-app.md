---
title: Validación y publicación de una aplicación basada en modelos mediante el diseñador de aplicaciones | Microsoft Docs
description: Aprenda a validar y publicar una aplicación basada en modelos.
keywords: ''
ms.date: 06/08/2018
ms.service: crm-online
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 5a9ec120-9ddc-4d92-b48c-0fee8c57d3c3
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: 10
topic-status: Drafting
ms.openlocfilehash: e3802ef423e7012974c24311c36b78cd56f8ed06
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39701821"
---
# <a name="validate-and-publish-a-model-driven-app-using-the-app-designer"></a>Validación y publicación de una aplicación basada en modelos mediante el diseñador de aplicaciones

Valide una aplicación para buscar dependencias de recursos que son necesarias para que funcione la aplicación, pero que aún no se han agregado a ella. Después de una validación correcta, publicará la aplicación. 
  
Por ejemplo, ha agregado un Panel de rendimiento de servicio al cliente a la aplicación, que usa gráficos como Combinación de casos (por prioridad) o Tendencia de resolución de casos (por día) que aún no ha agregado. Cuando se valide esta aplicación, obtendrá una lista de todos los recursos necesarios que faltan.  
  
Al validar la aplicación, el lienzo del diseñador de aplicaciones muestra los detalles acerca de los recursos que faltan.  
  
1.  En el diseñador de aplicaciones, seleccione **Validar**.  
  
     Aparece una barra de notificación que muestra si la aplicación tiene errores o advertencias. En la barra de notificación se muestran advertencias en casos donde, por ejemplo, una entidad no tenga ningún formulario o vista, o la aplicación no contenga ningún componente. Si no hay un mapa del sitio configurado para la aplicación, puede aparecer un error. Puede publicar una aplicación sin solucionar las advertencias, pero es necesario corregir los errores antes de publicarla.  
  
     ![Barra de notificación que muestra las advertencias de la aplicación](media/app-designer-warning-notification.png "Notification bar showing warnings in the app")  
  
     El diseñador de aplicaciones también muestra un símbolo de advertencia con el número de dependencias en cada icono de artefacto o recurso al que le falta un recurso necesario.  
  
     ![Advertencia de falta de componente en el icono del diseñador de aplicaciones](media/warning--button-on-app-designer-tile.png "Missing component warning on the app designer tile")  
  
2.  Para agregar los recursos necesarios, seleccione la pestaña **Requerido** en el lado derecho del lienzo. La pestaña **Requerido** está visible cuando al menos un recurso requerido falta en la aplicación.  
  
     La pestaña muestra una lista de los componentes necesarios.  
  
     ![Pestaña Requerido que muestra una lista de componentes que faltan en la aplicación](media/app-designer-required-components-tab.png "Required tab showing a list of missing components in the app")  
  
3.  Seleccione los recursos que quiere agregar y, a continuación, seleccione **Agregar dependencias**. Cuando se agrega un recurso necesario, disminuye el número en el icono al que se ha agregado el recurso.  
  
    > [!NOTE]
    >  Si un recurso común se requiere en varios componentes de aplicación, por ejemplo, se requiere un formulario para un panel y una entidad y agrega ese recurso solo una vez desde el árbol de dependencias del panel, el número de dependencias disminuye solo en el icono de panel, pero no en el icono de entidad. Sin embargo, la dependencia se resolverá para ambos.  
    >   
    >  Seleccione **Get Latest Dependencies** (Obtener últimas dependencias) ![botón Get Latest Dependencies (Obtener últimas dependencias) en el diseñador de aplicaciones](media/app-designer-get-latest-dependencies.png "Get Latest Dependencies button in the app designer") o seleccione de nuevo **Validar** para obtener el último conjunto de dependencias. Solo verá estos botones después de guardar la aplicación.  
  
     Seleccione **Ocultar dependencias** si no quiere agregar los componentes necesarios sugeridos. Cualquier advertencia sin resolver volverá a aparecer cuando abra la aplicación en el diseñador de aplicaciones y seleccione **Validar** o **Get Latest Dependencies** (Obtener las últimas dependencias) ![botón Get Latest Dependencies (Obtener las últimas dependencias) del diseñador de aplicaciones ](media/app-designer-get-latest-dependencies.png "Get Latest Dependencies button in the app designer").  
  
    > [!NOTE]
    >  Si oculta las dependencias ahora y quiere exportar esta aplicación más adelante, todas estas dependencias aparecerán de nuevo.  
  
## <a name="publish-an-app-using-the-app-designer"></a>Publicación de una aplicación mediante el diseñador de aplicaciones

Publique una aplicación para que esté disponible para los usuarios.  
  
 Cuando haya agregado componentes, y haya validado y guardado la aplicación, seleccione **Publicar** en la barra de comandos. También puede publicar la aplicación desde el icono de la aplicación en la página [Mis aplicaciones](advanced-navigation.md#my-apps). En la vista **Aplicaciones que se están editando**, en la esquina inferior derecha del icono de la aplicación que quiere publicar, seleccione el botón **Más opciones** (**...**) y, luego, seleccione **Publicar**.  
  
 El estado de la aplicación cambia a Publicado. Puede verlo en la esquina superior derecha del diseñador de aplicaciones. La aplicación se mueve desde la vista **Aplicaciones que se están editando** hasta la vista **Aplicaciones publicadas**, y la fecha de publicación se muestra en el icono de la aplicación.  
  
> [!NOTE]
> - Si la aplicación tiene un error de validación, verá el error en una barra de notificación. No podrá publicar la aplicación hasta que se resuelva el error.  
> - No se puede publicar una aplicación hasta que se guarde.  

## <a name="next-steps"></a>Pasos siguientes  
[Compartir una aplicación controlada por modelos con PowerApps](https://docs.microsoft.com/powerapps/maker/model-driven-apps/share-model-driven-app) <br/>
 [Ejecución de una aplicación controlada por modelos en un dispositivo móvil](https://docs.microsoft.com/powerapps/user/run-app-client-model-driven)   
 
