---
title: Validación y publicación de una aplicación basada en modelos mediante el diseñador de aplicaciones | MicrosoftDocs
description: Aprenda cómo validar y publicar una aplicación basada en modelos
keywords: ''
ms.date: 06/08/2018
ms.service: powerapps
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
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8195103992e14094816b0bbedfd17d6a799072a0
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "2884358"
---
# <a name="validate-and-publish-a-model-driven-app-using-the-app-designer"></a>Validar y publicar una aplicación controlada por modelos usando el diseñador de aplicaciones

Validar una aplicación para comprobar dependencias de activos que se requieren para que funcione la aplicación, pero que aún no se han agregado a la aplicación. Después de una validación correcta, publique la aplicación. 
  
Por ejemplo, ha agregado un Panel del rendimiento del servicio al cliente a la aplicación, que usa gráficos como Combinación de casos (por prioridad) o Tendencia de resolución de caso (por día) que no ha agregado. Cuando se valida esta aplicación, recibirá una lista de todos los activos necesarios que faltan.  
  
Cuando se valida la aplicación, el lienzo del diseñador de la aplicación le muestra los detalles acerca de los activos que faltan.  
  
1.  En el diseñador de la aplicaciones, seleccione **Validar**.  
  
     Una barra de notificación aparece y muestra si la aplicación tiene algún error o advertencias. La barra de notificación muestra advertencias en casos donde, por ejemplo, una entidad no tiene ningún formulario ni vista, o la aplicación no tiene ningún componente. Un error podría producirse si un mapa del sitio no está configurado para la aplicación. Puede publicar una aplicación sin abordar las advertencias, pero debe solucionar los errores para poder publicarla.  
  
     ![Barra de notificación que muestra advertencias en la aplicación](media/app-designer-warning-notification.png "Barra de notificación que muestra advertencias en la aplicación")  
  
     El diseñador de la aplicación también muestra un símbolo de advertencia con el número de dependencias en cada ventana de anomalía o activo donde falta un activo necesario.  
  
     ![Advertencia de componente que falta en la ventana del diseñador de la aplicación](media/warning--button-on-app-designer-tile.png "Advertencia de componente que falta en la ventana del diseñador de la aplicación")  
  
2.  Para agregar los activos necesarios, seleccione la pestaña **Necesario** en el lado derecho del lienzo. La pestaña **Necesario** está visible cuando falta al menos un activo necesario en la aplicación.  
  
     La pestaña muestra una lista de componentes requeridos.  
  
     ![Pestaña Requerido que muestra una lista de componentes que faltan en la aplicación](media/app-designer-required-components-tab.png "Pestaña Requerido que muestra una lista de componentes que faltan en la aplicación")  
  
3.  Seleccione los activos que desea agregar y luego seleccione **Agregar dependencias**. Cuando se agrega un activo requerido, el recuento en la ventana a la que se ha agregado el activo disminuye.  
  
    > [!NOTE]
    >  Si hay un activo necesario común entre los distintos componentes de la aplicación, por ejemplo, se requiere un formulario para un panel y una entidad, y agrega ese activo solo una vez desde el árbol de dependencia del panel, el recuento de dependencias disminuirá solo en la ventana del panel, pero no en la ventana de la entidad. Sin embargo, la dependencia se resolverá para ambas.  
    >   
    >  Seleccione el botón **Obtener las últimas dependencias** ![Botón Obtener las últimas dependencias en el diseñador de aplicaciones](media/app-designer-get-latest-dependencies.png "Botón Obtener las últimas dependencias en el diseñador de la aplicación")o seleccione de nuevo **Validar** para obtener el último conjunto de dependencias. Verá solo estos botones después de guardar la aplicación.  
  
     Seleccione **Ocultar dependencias** si no desea agregar componentes necesarios recomendados. Las advertencias sin resolver aparecerán otra vez cuando abre la aplicación, en el diseñador de la aplicación y selecciona **Validar** u **Obtener las últimas dependencias** ![Botón Obtener las últimas dependencias en el diseñador de aplicaciones](media/app-designer-get-latest-dependencies.png "Botón Obtener las últimas dependencias en el diseñador de la aplicación").  
  
    > [!NOTE]
    >  Si ahora oculta dependencias y desea exportar esta aplicación más adelante, volverán a aparecer todas estas dependencias.  
  
## <a name="publish-an-app-using-the-app-designer"></a>Publicar una aplicación usando el diseñador de aplicaciones

Publique una aplicación para que esté disponible para los usuarios.  
  
 Tras agregar componentes, validar y guardar la aplicación, en la barra de comandos, seleccione **Publicar**. También puede publicar la aplicación desde la ventana de la aplicación en la página [Mis aplicaciones](advanced-navigation.md#apps). En la vista **Aplicaciones que se están editando**, en la esquina inferior derecha de la ventana de la aplicación que desee publicar, seleccione el botón **Más opciones** (**...**) y después seleccione **Publicar**.  
  
 El estado de la aplicación cambia a Publicado. Puede verlo en la esquina superior derecha del diseñador de aplicaciones. La aplicación cambia de la vista **Aplicaciones que se están editando** a la vista **Aplicaciones publicadas**, y la fecha publicada se muestra en la ventana de la aplicación.  
  
> [!NOTE]
> - Si su aplicación tiene un error de validación, se mostrará el error en una barra de notificación. No podrá publicar la aplicación hasta que se resuelva el error.  
> - No puede publicar una aplicación hasta que la guarde.  

## <a name="next-steps"></a>Pasos siguientes  
[Compartir una aplicación controlada por modelos con Power Apps](https://docs.microsoft.com/powerapps/maker/model-driven-apps/share-model-driven-app) <br/>
 [Ejecutar una aplicación controlada por modelos en un dispositivo móvil](https://docs.microsoft.com/powerapps/user/run-app-client-model-driven)   
 
