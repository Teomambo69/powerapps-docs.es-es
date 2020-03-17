---
title: Visual de Power apps para Power BI | Microsoft Docs
description: Procedimiento y limitaciones para insertar una aplicación de lienzo en la que se usa el mismo origen de datos y se puede filtrar al igual que otros elementos de informe en Power BI
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/11/2020
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b3678c01210d5cb0398ce12e2111dba516404cfe
ms.sourcegitcommit: d500f44e77747a3244b6691ad9b3528e131dbfa5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2020
ms.locfileid: "79133588"
ms.PowerAppsDecimalTransform: true
---
# <a name="power-apps-visual-for-power-bi"></a>Visual de Power apps para Power BI

Power BI permite obtener información sobre los datos y mejorar la toma de decisiones, mientras que Power apps permite a todos los usuarios compilar y usar aplicaciones que se conectan a datos empresariales. Con el visual de Power Apps, puede pasar datos contextuales a una aplicación de lienzo, que se actualiza en tiempo real a medida que se realizan cambios en el informe. Ahora, los usuarios de la aplicación pueden derivar información empresarial y realizar acciones desde el interior de sus informes y paneles de Power BI.

## <a name="using-the-power-apps-visual"></a>Usar el visual de Power apps

Echemos un vistazo a los pasos necesarios para usar el visual de Power Apps en el informe de Power BI.

1. El visual de Power apps está disponible de forma predeterminada en el servicio Power BI. Si usa Power BI Desktop y no lo ve, debe actualizar a la versión más reciente de Power BI Desktop.

2. Agregue el objeto visual de Power apps a su informe y establezca los campos de datos asociados a él.

    ![Seleccionar los datos de informe](./media/powerapps-custom-visual/add-visual-set-data.png)

    Puede elegir una aplicación existente o crear una, pero el informe se deben publicar en el servicio Power BI y abrir en Microsoft Edge o Google Chrome.

3.  Si decide crear una aplicación, puede elegir en qué entorno crearla.

    ![Aplicación nueva o existente](./media/powerapps-custom-visual/create-new-or-choose-app.png)

    Si decide usar una aplicación existente, el visual le pedirá que abra la aplicación en Power apps. A continuación, el objeto visual configura los componentes necesarios en la aplicación para que Power BI pueda enviar datos a Power apps.

    Si crea una nueva aplicación, Power apps crea una aplicación sencilla con los componentes necesarios ya configurados.

    > [!NOTE]
    > Debe crear una nueva aplicación desde el visual de Power Apps en Power BI informe para que la función de `PowerBIIntegration.Refresh()` esté disponible en la aplicación.

    ![Nueva aplicación](./media/powerapps-custom-visual/new-app.png)

4. Ahora, en Power apps Studio, puede usar los campos de datos que estableció en el paso 2. El objeto `PowerBIIntegration` actúa como cualquier otra colección o origen de datos de solo lectura de Power apps. Se puede usar el objeto para rellenar un control, o para combinar y filtrar otros orígenes de datos.

    ![Fórmula personalizada](./media/powerapps-custom-visual/custom-formula.png)

    Esta fórmula combina datos de Power BI con el origen de datos de cliente: `LookUp(Customer;Customer_x0020_Name=First(PowerBIIntegration.Data).Customer_Name)`

   El informe de Power BI y la instancia de Power apps Studio que se inició comparten una conexión de datos activa. Mientras ambos están abiertos, puede filtrar o cambiar los datos del informe para ver los datos actualizados reflejados inmediatamente en la aplicación en Power apps Studio.

5. Una vez que haya completado la compilación o la realización de cambios en la aplicación, guarde y publique la aplicación en Power apps para ver la aplicación en el Power BI informe.

6. Una vez que esté satisfecho con los cambios, asegúrese de compartir la aplicación Power apps con los usuarios del informe y, a continuación, guarde el informe.

7. Y con eso, ha creado un informe en el que los usuarios pueden realizar acciones como obtener información de los datos.

    ![Informe de trabajo](./media/powerapps-custom-visual/working-report.gif)

    Si necesita realizar cambios en una aplicación, abra el informe en el modo de edición, haga clic o pulse en **más opciones** ( **...** ) en el visual de Power apps y seleccione **Editar**.

    ![Editar la aplicación](./media/powerapps-custom-visual/edit-app.png)

## <a name="limitations-of-the-power-apps-visual"></a>Limitaciones del visual de Power apps

Las siguientes limitaciones se aplican al visual de Power apps:

- Si se cambian los campos de datos asociados con el objeto visual, tendrá que modificar la aplicación desde dentro del servicio Power BI haciendo clic en el botón de puntos suspensivos (...) y seleccionando después **Editar**. De lo contrario, los cambios no se propagarán a Power apps y la aplicación se comportará de maneras inesperadas.
- El visual de Power apps no puede desencadenar una actualización de Power BI informes y Power BI orígenes de datos desde Power BI Desktop. Si escribe datos de la aplicación en el mismo origen de datos que el informe, los cambios no se reflejarán inmediatamente en Power BI Desktop. Los cambios se reflejan en la siguiente actualización programada.
- El visual de Power apps no puede filtrar los datos o devolver los datos al informe.
- Tendrá que compartir la aplicación Power apps por separado del informe. Más información sobre el [uso compartido de aplicaciones en Power apps](share-app.md).
- Power BI Report Server no es compatible con el visual de Power apps.
- Al usar la función `PowerBIIntegration.Refresh()` se aplican las siguientes limitaciones:
    - Debe crear una nueva aplicación desde el visual de Power Apps en Power BI informe para que esta función esté disponible en la aplicación.
    - Debe usar un origen que admita [DirectQuery](https://docs.microsoft.com/power-bi/desktop-directquery-data-sources) y la conexión de datos se debe crear con el método directquery.
- Power Apps en Power BI Desktop proporciona datos a Power apps Studio al crear aplicaciones pero no durante la edición. Use Power BI web para obtener una vista previa de los datos mientras edita las aplicaciones.
- La aplicación móvil Power BI no admite el control de micrófono en los objetos visuales de Power apps.

> [!NOTE]
> Se recomienda publicar primero el informe en el servicio Power BI y, a continuación, crear o modificar las aplicaciones.

## <a name="browser-support"></a>Compatibilidad del explorador

En la tabla siguiente se muestra la compatibilidad del explorador para ver, crear y modificar acciones del visual de Power apps. Los exploradores y las acciones admitidos se identifican con una marca de verificación (&check;).

|Explorador.|Ver|Crear|Modificar
|-|-|-|-
|Microsoft Edge|&check;|&check;|&check;
|Internet Explorer 11|&check;
|Google Chrome|&check;|&check;|&check;
|\* Safari|&check;
|Mozilla Firefox
|Todos los demás exploradores

\* en Safari, debe habilitar el seguimiento entre sitios (**preferencias** > **privacidad**y desactivar **evitar el seguimiento entre sitios**) para ver el visual de Power apps.

## <a name="accessibility-support"></a>Compatibilidad con accesibilidad

Para navegar por el visual de Power apps con el teclado, siga estos pasos:

1. Centrar la selección en el informe de Power BI para el visual de Power apps deseado.
2. Use la tecla **Tab** del teclado hasta que se resalte el visual.
3. Use la tecla **Ctrl + flecha derecha** en el teclado para escribir el control visual.
3. Use la tecla **Tab** del teclado hasta que se seleccione el componente deseado del elemento visual.

Para obtener más información, vea: [Power BI la documentación de accesibilidad]( https://docs.microsoft.com/power-bi/desktop-accessibility)


## <a name="next-steps"></a>Pasos siguientes

* Realice un sencillo [tutorial paso a paso](https://docs.microsoft.com/power-bi/visuals/power-bi-visualization-powerapp).
* Consulte nuestro [vídeo](https://aka.ms/powerappscustomvisualvideo).
