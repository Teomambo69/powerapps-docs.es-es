---
title: Agregar componentes de código a un campo o una entidad | Microsoft Docs
description: Proceso para importar componentes de código
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.openlocfilehash: 6f801328a4fc6b400cecd9ae7d8d233d8f3241a7
ms.sourcegitcommit: 551af7e0273862b28d9b2387671a4eeaf719eb37
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2020
ms.locfileid: "3116873"
---
# <a name="add-code-components-to-a-field-or-entity-in-model-driven-apps"></a>Agregar componentes de código a un campo o entidad en aplicaciones basadas en modelo

Los componentes de código permiten transformar en visualizaciones campos que normalmente contienen texto. De forma similar, puede usar los componentes de código para transformar conjuntos de datos, como una vista, de forma que se muestren con una presentación más visual, en lugar de como una lista de registros. Los componentes de código pueden aparecer como visualizaciones en formularios, paneles, vistas y cuadrículas de la página principal. 


   > [!div class="mx-imgBorder"] 
   > ![Control deslizante personalizado](../../maker/model-driven-apps/media/slider-control.PNG "Control deslizante para un campo")

## <a name="add-a-code-component-to-a-field"></a>Agregar un componente de código a un campo

Siga los pasos para cambiar la etiqueta predeterminada y el campo de cuadro de texto del campo **Importe del presupuesto** por un componente de código deslizante en la entidad Oportunidad. Puede seguir los mismos pasos para sustituir un campo existente por un componente de código o configurar un componente de código para un campo personalizado.

1. Navegue a **Configuración** > **Personalizaciones** > **Personalizar el sistema**.

2. Expanda **Entidades**, expanda la entidad que desee, como la entidad **Oportunidad**, seleccione **Formularios** y, a continuación, abra un formulario como el formulario **Principal** .

3. En el editor de formularios, haga doble clic en el campo en el que desee agregar un componente de código, como el campo **Importe del presupuesto** en el formulario principal de oportunidad. También puede crear un campo personalizado.

4. En la página **Propiedades de campo**, seleccione la pestaña **Controles** y, a continuación, seleccione **Agregar control**.

5. En la página Agregar control, seleccione el componente que desee, como el componente **Control deslizante lineal** y, a continuación, seleccione **Agregar**.

   > [!div class="mx-imgBorder"] 
   > ![Agregar control deslizante lineal](../../maker/model-driven-apps/media/add-slider.PNG "Agregar control deslizante lineal")

6. Elija el cliente en el que desee que aparezca el componente.

   - **Web**. Para que el componente de código esté disponible desde cualquier explorador web, seleccione la opción Web situada junto al componente. Tenga en cuenta que, al establecer la opción Web, el componente aparece en exploradores web de PC, Mac y dispositivos móviles.

   - **Teléfono**. Para que el componente de código esté disponible en teléfonos en los que se ejecute Dynamics 365 para teléfonos, seleccione la opción Teléfono situada junto al componente.

   - **Tableta**. Para que el componente de código esté disponible en tabletas en las que se ejecute Dynamics 365 para tabletas, seleccione la opción Tableta situada junto al componente.

   > [!div class="mx-imgBorder"] 
   > ![Elija las aplicaciones del cliente para ver el control personalizado](../../maker/model-driven-apps/media/choose-client.png "Elija las aplicaciones del cliente para ver el control personalizado") 

7. Seleccione el icono de lápiz junto a **Mín**, **Máx.**, y **Paso**, establezca la opción de la propiedad y, a continuación seleccione **Aceptar**.  
   
   > [!div class="mx-imgBorder"] 
   > ![Agregar propiedades del control personalizado](../../maker/model-driven-apps/media/ccf-add-properties.png "Agregar propiedades del control personalizado")

   - **Mín.** Establezca el valor mínimo aceptado. Puede enlazar el valor estático que especifique o enlazar el valor a un campo existente. En este ejemplo, **Enlazar a un valor estático** es **Divisa** y el valor mínimo que se puede introducir es *cero*.  
  
       - **Enlazar a un valor estático**. Seleccione el tipo de datos, por ejemplo, un número entero (Whole.None), divisa, coma flotante (FP) o decimales. A continuación, escriba un número que represente el valor mínimo aceptado para el campo.  
  
       - **Enlazar a un valor de un campo**. Seleccione un campo en la lista que se usará como el valor mínimo aceptado.  
  
   - **Máx.** Establezca el valor máximo aceptado del campo. Al igual que ocurre con el valor mínimo, puede enlazar el valor estático que especifique o enlazar el valor a un campo existente, como se ha descrito más arriba. En este ejemplo, **Enlazar a un valor estático** es **Divisa** y el valor máximo que se puede introducir es **1000 millones**.  
  
   - **Paso**. Representa la unidad que debe aumentar o disminuir al sumar o restar del valor actual. Por ejemplo, para el importe del presupuesto, puede seleccionar incrementos/disminuciones de 100 dólares.  
  
   - **Ocultar control predeterminado**. Se oculta el componente, por lo que ni el componente ni los datos se muestran en ninguno de los clientes que no admitan el componente de código.   
  
8. Seleccione **Aceptar** para cerrar la página Propiedades de campo.  
  
9. Para activar la personalización, en el formulario de entidad, seleccione **Guardar** y, a continuación, seleccione **Publicar**.  
  
10. Seleccione **Guardar y cerrar** para cerrar el editor de formularios.  
  
## <a name="add-code-component-to-an-entity"></a>Agregar componente de código a una entidad

Para agregar un componente de código como el componente de conjunto de datos o un componente de tabla sencilla a una cuadrícula o a una vista, siga los pasos indicados a continuación:

  - Navegue hasta **Configuración > Personalizaciones** y haga clic en **Personalización del sistema**.
  - Haga clic en la flecha junto a la pestaña **Entidades** y seleccione la entidad a la que desea agregar el componente de código. 
  - Haga clic en la pestaña **Controles** y haga clic en **Agregar un control**.
  - En la página Agregar control, seleccione el componente que desee, como el componente Tabla sencilla y, a continuación, seleccione **Agregar**.
  - Elija el cliente en el que desee que aparezca el componente.


## <a name="see-the-code-component-in-action"></a>Ver el componente de código en acción  

 Abra un registro que incluya el campo con el componente de código, como el formulario de oportunidad del ejemplo anterior, y observe cómo ha cambiado el campo. El campo se muestra ahora como un componente de control deslizante en lugar de como un campo de texto.  

> [!div class="mx-imgBorder"] 
> ![Control deslizante mostrado en formulario](../../maker/model-driven-apps/media/slider-control.PNG "Control deslizante mostrado en formulario")  

### <a name="see-also"></a>Vea también

[Implementación de componentes en TypeScript](implementing-controls-using-typescript.md)<br/>
[Referencia de la API de Power Apps component framework](reference/index.md)<br/>
[Información general sobre Power Apps component framework](overview.md)