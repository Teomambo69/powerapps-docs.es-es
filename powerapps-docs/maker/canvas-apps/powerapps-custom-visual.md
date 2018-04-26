---
title: Objeto visual personalizado de PowerApps para Power BI | Microsoft Docs
description: Procedimiento y limitaciones para insertar una aplicación en la que se usa el mismo origen de datos y se puede filtrar al igual que otros elementos de informe en Power BI
documentationcenter: na
author: mgblythe
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: canvas
ms.date: 03/15/2018
ms.author: mblythe
ms.openlocfilehash: da3d21e3f4488f552568a95d856af175f9a042eb
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="powerapps-custom-visual-for-power-bi"></a>Objeto visual personalizado de PowerApps para Power BI

Power BI habilita la información sobre los datos y mejora la toma de decisiones, mientras que PowerApps permite a todos los usuarios compilar y usar aplicaciones que se conectan a datos empresariales. Con el objeto visual personalizado de PowerApps, se pueden pasar datos en contexto a una aplicación de PowerApps, que se actualiza en tiempo real mientras se realizan cambios en el informe. Ahora, los usuarios de la aplicación pueden derivar información empresarial y realizar acciones desde el interior de sus informes y paneles de Power BI.

## <a name="using-the-powerapps-custom-visual"></a>Uso del objeto visual personalizado de PowerApps

Veamos los pasos necesarios para usar el objeto visual personalizado de PowerApps en el informe de Power BI.

1. Obtenga el objeto visual personalizado desde [AppSource](https://appsource.microsoft.com/product/power-bi-visuals/WA104381378?tab=Overview) o impórtelo directamente en el servicio de Power BI.

    ![Objeto visual personalizado en Marketplace](./media/powerapps-custom-visual/powerapps-store.png) 

1. Agregue el objeto visual de PowerApps al informe y establezca los campos de datos asociados con él.

    ![Seleccionar los datos de informe](./media/powerapps-custom-visual/add-visual-set-data.png)

1. Puede elegir una aplicación existente o crear una. Si decide crear una aplicación, puede elegir en qué entorno crearla.

    ![Aplicación nueva o existente](./media/powerapps-custom-visual/create-new-or-choose-app.png)

    Si elige usar una aplicación existente, el objeto visual le pedirá que abra la aplicación en PowerApps. Después, el objeto visual configura los componentes necesarios de la aplicación para que Power BI pueda enviar datos a PowerApps.

    Si crea una aplicación, PowerApps crea una aplicación sencilla con los componentes necesarios ya configurados.

    ![Nueva aplicación](./media/powerapps-custom-visual/new-app.png)

1. Ahora en PowerApps Studio, se pueden usar los campos de datos que se establecieron en el paso 2. El objeto `PowerBIIntegration` actúa como cualquier otro origen de datos o colección de solo lectura de PowerApps. Se puede usar el objeto para rellenar un control, o para combinar y filtrar otros orígenes de datos.

    ![Fórmula personalizada](./media/powerapps-custom-visual/custom-formula.png)

    Esta fórmula combina datos de Power BI con el origen de datos de cliente: `LookUp(Customer,Customer_x0020_Name=First(PowerBIIntegration.Data).Customer_Name)`

 El informe de Power BI y la instancia de PowerApps Studio que se inició comparten una conexión de datos dinámica. Mientras los dos estén abiertos, se pueden filtrar o cambiar los datos del informe para ver los datos actualizados reflejados al instante en la aplicación en PowerApps Studio.

1. Después de haber completado la compilación o los cambios en la aplicación, guárdela y publíquela en PowerApps para verla en el informe de Power BI.

1. Una vez esté satisfecho con los cambios, asegúrese de compartir la aplicación de PowerApps con los usuarios del informe y, después, guarde el informe.

1. Y con eso, ha creado un informe en el que los usuarios pueden realizar acciones como obtener información de los datos.

    ![Informe de trabajo](./media/powerapps-custom-visual/working-report.gif)

    Si necesita realizar cambios en una aplicación, abra el informe en modo de edición, pulse o haga clic en **Más opciones** (**. . .**) en el objeto visual de PowerApps y seleccione **Editar**.

    ![Editar la aplicación](./media/powerapps-custom-visual/edit-app.png)

## <a name="limitations-of-the-powerapps-custom-visual"></a>Limitaciones del objeto visual personalizado de PowerApps

El objeto visual personalizado de PowerApps está disponible en versión preliminar y presenta las limitaciones siguientes:

- No se pueden crear o modificar aplicaciones cuando se usa el objeto visual personalizado de PowerApps en Power BI Desktop, Internet Explorer o Mozilla Firefox. Se recomienda publicar primero el informe en el servicio Power BI. Después, use Microsoft Edge o Google Chrome para crear aplicaciones y realizar cambios en las aplicaciones.
- Si se cambian los campos de datos asociados con el objeto visual, tendrá que modificar la aplicación desde dentro del servicio Power BI haciendo clic en el botón de puntos suspensivos (...) y seleccionando después **Editar**. En caso contrario, los cambios no se propagarán a PowerApps y la aplicación se comportará de forma inesperada.
- El objeto visual personalizado de PowerApps no puede desencadenar una actualización del informe o el origen de datos de Power BI. Si se escriben datos desde la aplicación en el mismo origen de datos que el informe, los cambios no se reflejarán inmediatamente. Los cambios se reflejan en la siguiente actualización programada.
- El objeto visual personalizado de PowerApps no puede filtrar los datos o devolver ningún dato al informe.
- Tendrá que compartir la aplicación de PowerApps de forma independiente al informe. Obtenga información sobre cómo [compartir aplicaciones en PowerApps](share-app.md).
- La aplicación móvil para Power BI no es compatible con el objeto visual personalizado de PowerApps.

## <a name="next-steps"></a>Pasos siguientes

* Realice un sencillo [tutorial paso a paso](embed-powerapps-powerbi.md).
* Consulte nuestro [vídeo](https://aka.ms/powerappscustomvisualvideo).