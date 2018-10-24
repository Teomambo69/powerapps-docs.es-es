---
title: Establecimiento de las propiedades de una lista o un gráfico de aplicaciones controladas por modelos incluidos en un panel de PowerApps | Microsoft Docs
description: Información sobre cómo establecer las propiedades de un gráfico o una lista incluidos en un panel
ms.custom: ''
ms.date: 06/06/2018
ms.reviewer: ''
ms.service: crm-online
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
ms.openlocfilehash: c88fef0412060516ef448c89f5ddfdc9cad00e20
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39710594"
---
# <a name="set-properties-for-a-model-driven-app-chart-or-list-included-in-a-dashboard"></a>Establecimiento de las propiedades de una lista o un gráfico de aplicaciones controladas por modelos incluidos en un panel

Para editar un componente de lista o gráfico en el Diseñador de paneles, seleccione el gráfico o la lista que desee y, a continuación, elija Editar componente en la barra de herramientas del Diseñador de paneles.   

  ![Componente de edición de gráficos del Diseñador de paneles](media/dashboard-chart-select.png)

Se abrirá el cuadro de diálogo **Establecer propiedades**.

  ![Cuadro de diálogo Establecer propiedades en gráficos](media/set-properties-chart.png)  
 
Puede establecer las siguientes propiedades de gráfico en el cuadro de diálogo **Establecer propiedades**:  
  
- **Nombre**. Nombre único del gráfico. El sistema sugiere un valor, pero puede cambiarlo.  
  
- **Etiqueta**. La etiqueta que aparece en la parte superior del gráfico.  
  
- **Mostrar etiqueta en el panel**. Active o desactive esta casilla de verificación para mostrar u ocultar la etiqueta de gráfico.  
  
- **Entidad**. Seleccione la entidad (tipo de registro) en la que se basará el gráfico. Esta configuración determina los valores disponibles para las propiedades Vista predeterminada y Gráfico predeterminado.  
  
- **Vista predeterminada**. Seleccione la vista utilizada para recuperar los datos del gráfico.  
  
- **Gráfico predeterminado**. Seleccione el gráfico predeterminado que se desea mostrar cuando se abra el panel por primera vez. Los valores disponibles dependen del valor establecido para la propiedad Entidad. Esta propiedad funciona junto con la propiedad Mostrar selección de gráfico. Un usuario puede cambiar el tipo de gráfico si la opción **Mostrar selección de gráfico** está activada, pero el gráfico se revertirá al predeterminado la próxima vez que se abra el panel.  
  
- **Solo mostrar gráfico**. Active esta casilla de verificación si desea mostrar solo el gráfico. Desactívela si desea mostrar el gráfico y sus datos asociados.  
  
- **Mostrar selección de gráfico**. Active esta casilla para permitir que los usuarios puedan cambiar el tipo de gráfico (columna, barras, gráficos circulares, etc.) cuando usen el panel. Si el usuario cambia el tipo de gráfico, la configuración no se guarda. El tipo de gráfico se revierte a la configuración de gráfico predeterminado cuando se cierra el panel.  
  
Puede establecer las siguientes propiedades de lista en el cuadro de diálogo **Establecer propiedades**:  
  
- **Nombre**. Nombre único de la lista. El sistema sugiere un valor, pero puede cambiarlo.  
  
- **Etiqueta**. La etiqueta que aparece en la parte superior de la lista.  
  
- **Mostrar etiqueta en el panel**. Active o desactive esta casilla de verificación para mostrar u ocultar la etiqueta de lista.  
  
- **Entidad**. Seleccione la entidad (tipo de registro) en la que se basará la lista. Esta configuración determina los valores disponibles para la propiedad Vista predeterminada.  
  
- **Vista predeterminada**. Seleccione la vista utilizada para recuperar los datos de la lista. Un usuario puede cambiar la vista, pero la lista se revertirá a la predeterminada la próxima vez que se abra el panel.  
  
- **Mostrar cuadro de búsqueda**. Active esta casilla de verificación si desea mostrar un cuadro de búsqueda en la parte superior de la lista. Si se incluye el cuadro de búsqueda, los usuarios pueden buscar registros en la lista en un entorno de ejecución.  
  
- **Mostrar índice**. Active esta casilla de verificación si desea mostrar los filtros A a Z en la parte inferior de la lista. Cuando se muestran los filtros A a Z, los usuarios pueden seleccionar una letra para saltar a los registros que comienzan con esa letra.  
  
- **Selector de vista**. Elija uno de los siguientes valores:  
  
    - **Desactivado**. No se muestra el selector de vistas. Los usuarios no pueden cambiar las vistas en un entorno de ejecución.  
  
    - **Mostrar todas las vistas.** Proporcione una lista completa de las vistas asociadas al valor establecido en la propiedad Entidad.  
  
    - **Mostrar las vistas seleccionadas**. Seleccione esta opción para limitar la lista de vistas disponibles en un entorno de ejecución. Para seleccionar las vistas específicas que se mostrarán, mantenga presionada la tecla Ctrl y pulse o seleccione cada vista que desee incluir.  
 
## <a name="next-steps"></a>Pasos siguientes  
 [Crear o personalizar paneles](create-edit-dashboards.md)
