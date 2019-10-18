---
title: Agregar componentes de código a un campo o entidad | Microsoft Docs
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
ms.openlocfilehash: 63ecdde21328219b70af04b9b65edbb3073f3025
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72347047"
---
# <a name="add-code-components-to-a-field-or-entity-in-model-driven-apps"></a>Agregar componentes de código a un campo o una entidad en aplicaciones controladas por modelos

Los componentes de código permiten transformar los campos que tradicionalmente contienen texto en visualizaciones. Del mismo modo, puede utilizar componentes de código para transformar conjuntos de elementos, como una vista, para que se muestren en una representación más visual, en lugar de una lista de registros. los componentes de código pueden aparecer como visualizaciones en formularios, paneles, vistas y cuadrículas de página principal. 


   > [!div class="mx-imgBorder"] 
   > ![](../../maker/model-driven-apps/media/slider-control.PNG "Control deslizante del") control deslizante personalizado para un campo

## <a name="add-a-code-component-to-a-field"></a>Agregar un componente de código a un campo

Si sigue los pasos de este procedimiento, cambiará el campo de cuadro de texto y la etiqueta predeterminada del campo **importe del presupuesto** al componente de código del control deslizante de la entidad oportunidad. Puede utilizar pasos similares para reemplazar un campo existente por un componente de código o configurar un componente de código para un campo personalizado.

1. Abra el Explorador de soluciones.

2. Expanda **entidades**, expanda la entidad que desee, como la entidad **oportunidad** , seleccione **formularios**y, a continuación, abra un formulario como el formulario **principal** .

3. En el editor de formularios, haga doble clic en el campo en el que desea agregar un componente de código, como el campo **importe del presupuesto** del formulario principal de la oportunidad. También puede crear un campo personalizado.

4. En la página **propiedades de campo** , seleccione la pestaña **controles** y, a continuación, seleccione **Agregar control**.

5. En la página Agregar control, seleccione el componente que desee, como el componente de **control deslizante lineal** , y, a continuación, seleccione **Agregar**.

   > [!div class="mx-imgBorder"] 
   > ![Agregar control deslizante lineal](../../maker/model-driven-apps/media/add-slider.PNG "Agregar control deslizante lineal")

6. Elija el cliente en el que desea que aparezca el componente.

   - **Web**. Para que el componente de código esté disponible desde cualquier explorador Web, seleccione la opción Web que se encuentra junto al componente. Tenga en cuenta que el establecimiento de la opción web incluye la representación del componente en exploradores Web en PC, Mac y dispositivos móviles.

   - **Teléfono**. Para que el componente de código esté disponible en teléfonos que ejecutan Dynamics 365 para teléfonos, seleccione la opción teléfono junto al componente.

   - **Tableta**. Para que el componente de código esté disponible en los dispositivos de Tablet PC que ejecutan Dynamics 365 para tabletas, seleccione la opción de Tablet PC junto al componente.

   > [!div class="mx-imgBorder"] 
   > ![Elegir las aplicaciones cliente para ver el control personalizado](../../maker/model-driven-apps/media/choose-client.png "elegir las aplicaciones cliente para ver el control personalizado") 

7. Seleccione el icono de lápiz junto a **min**, **Max**y **Step**, establezca la opción de propiedad y, a continuación, seleccione **Aceptar**.  
   
   > [!div class="mx-imgBorder"] 
   > ![Agregar propiedades de control personalizadas](../../maker/model-driven-apps/media/ccf-add-properties.png "Agregar propiedades de controles personalizados")

   - **Mín**. Establezca el valor mínimo aceptado. Puede enlazar un valor estático que especifique o enlace el valor a un campo existente. En este ejemplo, el **enlace a un valor estático** es **Currency** y el valor mínimo que se puede especificar es *cero*.  
  
       - **Enlazar a un valor estático**. Seleccione el tipo de datos, como un número entero (todo. ninguno), moneda, punto flotante (FP) o decimal. A continuación, escriba un número que represente el valor mínimo aceptado para el campo.  
  
       - **Enlazar a valores en un campo**. Seleccione un campo de la lista que se usará como el valor mínimo aceptado.  
  
   - **Máx**. Establezca el valor máximo permitido para el campo. Al igual que el valor mínimo, puede enlazar un valor estático que especifique o enlazar el valor a un campo existente como se describió anteriormente. En este ejemplo, el **enlace a un valor estático** es **Currency** y el valor máximo que se puede especificar es **1 mil millones**.  
  
   - **Paso**. Representa la unidad que se va a aumentar o reducir al agregar o restar del valor actual. Por ejemplo, para la cantidad de presupuesto puede seleccionar 100 dólar increments\decrements.  
  
   - **Ocultar control predeterminado**. Al seleccionar esta opción, se oculta el componente para que no se muestre el componente o los datos en ninguno de los clientes que no admiten el componente de código.   
  
8. Seleccione **Aceptar**para cerrar la página Propiedades del campo.  
  
9. Para activar la personalización, en el formulario de la entidad, seleccione **Guardar**y, a continuación, seleccione **publicar**.  
  
10. Seleccione **Guardar y cerrar** para cerrar el editor de formularios.  
  
## <a name="add-code-component-to-an-entity"></a>Agregar componente de código a una entidad

Para agregar un componente de código como componente de conjunto de datos o componente de tabla simple a una cuadrícula o vista, siga estos pasos:

  - Vaya a **configuración > personalizaciones** y haga clic en **personalizar el sistema**.
  - Haga clic en la flecha situada junto a la pestaña **entidades** , seleccione la entidad a la que desea agregar el componente de código. 
  - Haga clic en la pestaña **controles** y haga clic en **Agregar un control**.
  - En la página Agregar control, seleccione el componente que desee, como componente de tabla simple y, a continuación, seleccione **Agregar**.
  - Elija el cliente en el que desea que aparezca el componente.


## <a name="see-the-code-component-in-action"></a>Ver el componente de código en acción  

 Abra un registro que incluya el campo con el componente de código, como el formulario de la oportunidad del ejemplo anterior, y vea cómo se cambia el campo. El campo se representa ahora como un componente de control deslizante en lugar del campo de texto.  

> [!div class="mx-imgBorder"] 
> ![Control deslizante representado en]el(../../maker/model-driven-apps/media/slider-control.PNG "control deslizante del formulario representado en el formulario")  

### <a name="see-also"></a>Vea también

[Implementación de componentes en TypeScript](implementing-controls-using-typescript.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](overview.md)