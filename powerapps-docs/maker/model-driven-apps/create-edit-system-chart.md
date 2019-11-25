---
title: Crear o editar un gráfico del sistema de una aplicación controlada por modelos en PowerApps | MicrosoftDocs
description: Aprenda a crear o editar un gráfico
ms.custom: ''
ms.date: 05/23/2018
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
ms.openlocfilehash: c1286c0d234a93bb3316d1afa0aac809b5455142
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2759092"
---
# <a name="create-a-model-driven-app-system-chart"></a>Crear o editar un gráfico del sistema de una aplicación controlada por modelos

En este tema aprenderá a crear un gráfico del sistema. Los gráficos del sistema son gráficos propiedad de la organización, que los pone a disposición de cualquier persona con acceso para leer los datos que ejecutan la aplicación. Los gráficos del sistema no se pueden asignar ni compartir con usuarios específicos de la aplicación.  
  
1. Inicie sesión en [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).  

    > [!IMPORTANT]
    > “Si el modo de diseño **Controlado por modelos** no está disponible, puede que tenga que [Crear un entorno](https://docs.microsoft.com/powerapps/administrator/create-environment).     
  
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
