---
title: Establecer propiedades para un gráfico o una lista de una aplicación controlada por modelos incluidos en un panel de PowerApps | MicrosoftDocs
description: Aprenda cómo establecer propiedades para un gráfico o una lista incluidos en un panel
ms.custom: ''
ms.date: 06/06/2018
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
ms.assetid: 50fb2ab0-5c1a-4a5e-8ebc-5603fecc4da0
caps.latest.revision: 26
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: b284b42c162c44d59fc7af22905be08748d9c766
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2711187"
---
# <a name="set-properties-for-a-model-driven-app-chart-or-list-included-in-a-dashboard"></a>Establecer propiedades para un gráfico o una lista de una aplicación controlada por modelos incluidos en un panel

Para editar un gráfico o componente de lista desde el diseñador de paneles, seleccione el gráfico o o la lista que desee y seleccione Editar componente en la barra de herramientas del diseñador de paneles.   
  > [!div class="mx-imgBorder"] 
  > ![Editar componente de gráfico en el diseñador de paneles](media/dashboard-chart-select.png)

Se abrirá el cuadro de diálogo **Establecer propiedades**.

  > [!div class="mx-imgBorder"] 
  > ![Establecer propiedades de gráfico](media/set-properties-chart.png)  
 
Puede definir las siguientes propiedades del gráfico en el cuadro de diálogo **Establecer propiedades**:  
  
- **Nombre**. Nombre único para el gráfico. El sistema sugiere un valor, pero puede cambiarlo.  
  
- **Etiqueta**. La etiqueta que aparece en la parte superior del gráfico.  
  
- **Mostrar etiqueta en el panel**. Active o desactive esta casilla para mostrar u ocultar la etiqueta del gráfico.  
  
- **Entidad**. Seleccione la entidad (tipo de registro) en la que se basará el gráfico. Este valor determina los valores disponibles para las propiedades de Vista predeterminada y Gráfico predeterminado.  
  
- **Vista predeterminada**. Seleccione la vista usada para recuperar los datos para el gráfico.  
  
- **Gráfico predeterminado**. Seleccione el gráfico predeterminado que desea mostrar al abrir el panel por primera vez. Los valores disponibles están determinados por el valor establecido para la propiedad Entidad. Esta propiedad trabaja junto con las propiedades Mostrar selección de gráfico. Un usuario pueda cambiar el tipo de gráfico si está activada la opción **Mostrar selección de gráfico**, pero el gráfico revertirá al gráfico predeterminado la próxima vez que se abra el panel.  
  
- **Solo mostrar gráfico**. Active esta casilla si desea mostrar solo el gráfico. Desactive esta casilla si desea mostrar el gráfico y sus datos asociados.  
  
- **Mostrar selección de gráfico**. Active esta casilla para permitir a los usuarios modificar el tipo de gráfico (columna, barra, circular, etc.) cuando usen el panel. Si el usuario cambia el tipo de gráfico, los valores no se guardan. El tipo de gráfico vuelve al valor de Gráfico predeterminado al cerrarse el panel.  
  
Puede definir las siguientes propiedades de lista en el cuadro de diálogo **Establecer propiedades**:  
  
- **Nombre**. Nombre único para la lista. El sistema sugiere un valor, pero puede cambiarlo.  
  
- **Etiqueta**. La etiqueta que aparece en la parte superior de la lista.  
  
- **Mostrar etiqueta en el panel**. Active o desactive esta casilla para mostrar u ocultar la etiqueta de la lista.  
  
- **Entidad**. Seleccione la entidad (tipo de registro) en la que se basará la lista. Este valor determina los valores disponibles para la propiedad de Vista predeterminada.  
  
- **Vista predeterminada**. Seleccione la vista que se usa para recuperar los datos de la lista. Un usuario puede cambiar la vista, pero la lista revertirá a la vista predeterminada la próxima vez que se abra el panel.  
  
- **Mostrar cuadro de búsqueda**. Seleccione esta casilla si desea mostrar un cuadro de búsqueda en la parte superior de la lista. Si el cuadro de búsqueda está incluido, usted u otros usuarios pueden buscar registros en la lista en tiempo de ejecución.  
  
- **Mostrar índice**. Seleccione esta casilla si desea mostrar los filtros de la A a la Z en la parte inferior de la lista. Cuando se muestran los filtros de la A a la Z, usted u otros usuarios pueden seleccionar una letra para pasar a los registros que comiencen con esa letra.  
  
- **Selector de vista**. Seleccione uno de los siguientes valores:  
  
    - **Desactivado**. No mostrar el selector de vistas. Usted u otros usuarios no podrán cambiar las vistas en tiempo de ejecución.  
  
    - **Mostrar todas las vistas**. Proporciona una lista completa de vistas asociadas con el valor establecido en la propiedad Entidad.  
  
    - **Mostrar las vistas seleccionadas**. Seleccione esta opción para limitar la lista de vistas disponibles en tiempo de ejecución. Para seleccionar vistas específicas para mostrar, mantenga presionada la tecla Ctrl y pulse o seleccione cada vista que desee incluir.  
 
## <a name="next-steps"></a>Pasos siguientes  
 [Creación o personalización de paneles](create-edit-dashboards.md)
