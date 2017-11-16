---
title: "Uso de una aplicación de ejemplo | Microsoft Docs"
description: "Instrucciones detalladas para usar una aplicación de ejemplo en powerapps.com."
services: 
suite: powerapps
documentationcenter: na
author: linhtranms
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/25/2016
ms.author: litran
ms.openlocfilehash: 7794f1ee28898016d3e8d4ac855f6ae1cf2090c7
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="use-a-sample-app"></a>Usar una aplicación de ejemplo
En [powerapps.com](http://web.powerapps.com), utilice una aplicación de ejemplo para explorar posibilidades de diseño y descubrir conceptos que puede aplicar al desarrollar sus propias aplicaciones. Cada aplicación de ejemplo usa datos ficticios para presentar un escenario real.

![](./media/open-and-run-a-sample-app/portal-home.png)

En **Cost Estimator**, por ejemplo, puede crear una cita para estimar el costo de la instalación de un producto para suelos en una sala de un tamaño determinado. Capture detalles como la dirección y los metros cuadrados, y calcule el precio en función de los descuentos y los tipos impositivos. Filtre una lista de citas para que se muestren solo aquellas para las que se han creado las estimaciones, o aquellas para las que no se han creado, o todas las citas.

## <a name="open-the-app"></a>Abrir la aplicación
1. Inicie sesión en [powerapps.com](https://web.powerapps.com) y, a continuación, haga clic o pulse en **Cost Estimator** en la lista de aplicaciones de ejemplo.
   
    ![](./media/open-and-run-a-sample-app/app-tile.png)
2. Pulse o haga clic en **Abrir para teléfono** para mostrar la aplicación como aparecería en un teléfono y, a continuación, haga clic o pulse **Permitir** para dar el consentimiento para usar la cámara del dispositivo.
   
    La aplicación contiene datos de ejemplo para crear citas y estimar el costo de la instalación de un producto específico para suelos en una sala de un tamaño determinado.
   
    ![](./media/open-and-run-a-sample-app/cost_estimator_home.png)

## <a name="make-and-view-an-appointment"></a>Concertar y ver una cita
1. Haga clic o pulse **+** para concertar una cita para una estimación.
   
    ![](./media/open-and-run-a-sample-app/cost_estimator_add.png)
2. Proporcione los detalles y, a continuación, haga clic o pulse en **Guardar trabajo**.
   
    ![](./media/open-and-run-a-sample-app/cost_estimator_new.png)
   
    La cita que ha creado aparecerá en la lista de citas.
   
    ![](./media/open-and-run-a-sample-app/new_job_added.png)
3. Haga clic o pulse en una cita, como la que creó, para ver sus detalles, incluido un mapa de la ubicación.
   
    ![](./media/open-and-run-a-sample-app/job_details.png)
   
    **Nota**: Puede eliminar una cita haciendo clic o pulsando en el icono de la papelera en la esquina superior derecha.
   
    ![](./media/open-and-run-a-sample-app/job_delete.png)

## <a name="create-an-estimate"></a>Crear una estimación
1. En la página de detalles de una cita, haga clic o pulse en **Comenzar estimación**.
   
    ![](./media/open-and-run-a-sample-app/begin_estimate.png)
2. Proporcione la información necesaria acerca de la sala, como el **nombre**, la **longitud** y el **ancho** y, a continuación, haga clic o pulse en **Select flooring style** (Seleccionar estilo de suelo).
   
    ![](./media/open-and-run-a-sample-app/dimensions.png)
   
    Aparece una lista de categorías de productos para el suelo.
   
    ![](./media/open-and-run-a-sample-app/select_flooring_type.png)
3. Haga clic o pulse en **Carpet** (Alfombra) y, a continuación, haga clic o pulse en **Caserta Sky Grey**.
   
    ![](./media/open-and-run-a-sample-app/carpet.png)
4. Si va a utilizar la aplicación en un dispositivo que tiene una cámara, haga clic o pulse en **Agregar fotos**.
   
    ![](./media/open-and-run-a-sample-app/add_photos.png)
5. Realice una o varias fotos y, a continuación, haga clic o pulse en **Listo**.
   
    ![](./media/open-and-run-a-sample-app/take_photos.png)

## <a name="finish-and-submit-an-estimate"></a>Finalizar y enviar una estimación
1. Haga clic o pulse en **Review Estimate** (Revisar estimación).
   
    ![](./media/open-and-run-a-sample-app/review_estimate.png)
2. (opcional) Especifique un **ajuste de precios** y un tipo **impositivo**.
3. Agregue una firma y, a continuación, haga clic o pulse en **Submit estimate** (Enviar estimación).
   
    ![](./media/open-and-run-a-sample-app/submit_estimate.png)
   
    Si lo permite la configuración del explorador, se abrirá el cliente de correo predeterminado con un mensaje que contiene la información de estimación.
   
    ![](./media/open-and-run-a-sample-app/email.png)
   
    En PowerApps, la pantalla indicará que se ha enviado una estimación.
   
    ![](./media/open-and-run-a-sample-app/done.png)
4. Haga clic o pulse en **Listo** para volver a la lista de citas.
   
    La cita para la estimación que acaba de completar aparece en verde, lo cual indica que está cerrada.
   
    ![](./media/open-and-run-a-sample-app/estimate_done.png)
5. (opcional) Haga clic o pulse en el icono de filtro de la esquina superior izquierda y, a continuación, filtre la lista por estado (abierta o cerrada) o muestre todas las citas.

