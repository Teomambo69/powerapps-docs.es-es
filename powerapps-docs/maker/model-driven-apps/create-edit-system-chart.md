---
title: Crear o editar un gráfico del sistema de una aplicación controlada por modelos en Power Apps | MicrosoftDocs
description: Aprenda a crear o editar un gráfico
ms.custom: ''
ms.date: 03/30/2020
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
ms.assetid: e02d58f7-6b1c-4a51-b801-a4d9f24729c5
caps.latest.revision: 29
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 426bfaf0ab53e1d896f7e0b098e089c8596ad907
ms.sourcegitcommit: 3c6c5594b73abd5ff438d50f3b579d56cef7241c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2020
ms.locfileid: "3285628"
---
# <a name="create-a-model-driven-app-system-chart"></a>Crear o editar un gráfico del sistema de una aplicación controlada por modelos

En este tema aprenderá a crear un gráfico del sistema. Los gráficos del sistema son gráficos propiedad de la organización, que los pone a disposición de cualquier persona con acceso para leer los datos que ejecutan la aplicación. Los gráficos del sistema no se pueden asignar ni compartir con usuarios específicos de la aplicación.  
  
1. Inicie sesión en [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).  

2. Expanda **Datos**, seleccione **Entidades**, seleccione la entidad que desee y, a continuación, seleccione la pestaña **Gráficos**.  
  
3.  En la barra de herramientas, seleccione **Agregar gráfico**.  
  
4.  Especifique el tipo de gráfico y cómo se mostrarán los datos en el gráfico.  
  
    -   Introduzca el nombre del gráfico, como *Número de empleados por cuenta*.  
  
    -   En las listas desplegables de **Seleccionar campo**: 
        - En la lista desplegable del eje **Serie** de **Seleccionar campo**, seleccione un campo como **Número de empleados**.  
        - En la lista desplegable del eje **Categoría** de **Seleccionar campo**, seleccione un campo como **Nombre de cuenta**.
  
    -   Agregue una descripción para identificar la finalidad del gráfico, como *Este gráfico de columnas muestra el número de empleados por nombre de cuenta*. 

    > [!div class="mx-imgBorder"] 
    > ![Gráfico de ejemplo](media/sample-chart.png)
  
5.  Seleccione **Guardar y cerrar**.  

## <a name="known-issues"></a>Problemas conocidos  
En el diseñador de gráficos, no se admite agregar una orden en algunos campos calculados y produce un error.  Los campos calculados que producen esto están usando otros campos calculados, un campo de entidad relacionado, o un campo local en la entidad.

## <a name="next-steps"></a>Pasos siguientes  
[Crear o editar paneles](create-edit-dashboards.md)
