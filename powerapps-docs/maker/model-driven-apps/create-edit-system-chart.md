---
title: Crear o editar un gráfico del sistema de una aplicación controlada por modelos en PowerApps | MicrosoftDocs
description: Aprenda a crear o editar un gráfico
ms.custom: ''
ms.date: 05/23/2018
ms.reviewer: ''
ms.service: crm-online
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
---
# <a name="create-a-model-driven-app-system-chart"></a>Crear o editar un gráfico del sistema de una aplicación controlada por modelos

En este tema aprenderá a crear un gráfico del sistema. Los gráficos del sistema son gráficos propiedad de la organización, que los pone a disposición de cualquier persona con acceso para leer los datos que ejecutan la aplicación. Los gráficos del sistema no se pueden asignar ni compartir con usuarios específicos de la aplicación.  
  
1. En el sitio de [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) seleccione **Controlado por modelos** (parte inferior izquierda del panel de navegación).  

     ![Modo de diseño controlado por modelos](media/model-driven-switch.png)

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

## <a name="next-steps"></a>Pasos siguientes  
[Crear o editar paneles](create-edit-dashboards.md)
