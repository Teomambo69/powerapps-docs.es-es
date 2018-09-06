---
title: Uso del control Formulario de entidad | Microsoft Docs
description: Cree aplicaciones más rápidamente mediante el control Formulario de la entidad para agregar completos formularios para una entidad de Common Data Service.
author: aneesmsft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 03/11/2017
ms.author: aneesa
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ee8573cb9ae4df5ac42deefad4ac67aede3a3502
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42836286"
---
# <a name="use-the-entity-form-control"></a>Usar el control Formulario de la entidad
Cree aplicaciones más rápidamente mediante el control **Formulario de entidad** para agregar formularios enriquecidos para una entidad de Common Data Service.

Para ver una introducción al control **Formulario de la entidad**, consulte esta entrada de blog: [New entity form control (experimental feature) for Common Data Service](https://powerapps.microsoft.com/blog/new-entity-form-control-experimental-feature-for-common-data-service/) (Nuevo control Formulario de la entidad (versión preliminar) para Common Data Service).

> [!IMPORTANT]
> Tenga en cuenta la naturaleza experimental del control **Formulario de la entidad**, tal como se describe en la entrada de blog, y tenga cuidado al usarlo en aplicaciones de producción, al menos por ahora.

## <a name="key-properties"></a>Propiedades principales
Estas son las propiedades fundamentales de un control **Formulario de la entidad**.

**DataSource**: especifica el origen de datos que contiene el registro o los registros que desea mostrar.   
> [!NOTE]
> Actualmente se admiten solo entidades en Common Data Service como orígenes de datos para el control **Formulario de la entidad**.  

**Patrón**: especifica el estilo del formulario que desea mostrar en el control **Formulario de la entidad**. Establezca esta propiedad mediante la enumeración **FormPattern**.

* **FormPattern.List**: muestra una lista tabular de registros.
* **FormPattern.CardList**: muestra una lista de tarjetas de registros.
* **FormPattern.Details**: muestra un formulario para ver o editar los detalles de un único registro.
* **FormPattern.None**: no se ha especificado explícitamente ningún estilo. El valor predeterminado es **List** para aplicaciones de tableta y **CardList** para las de teléfono.

**Item**: especifica el registro en el origen de datos que el control **Formulario de la entidad** debería mostrar. Esta propiedad se usa solo cuando **Patrón** está establecida en **FormPattern.Details**.

**Seleccionado**: obtiene el registro que está seleccionado actualmente.  
Ejemplo: si el control **Formulario de la entidad** muestra una lista de registros de pedido de ventas, la propiedad **Seleccionado** le proporcionará el registro que está seleccionado actualmente. También puede acceder a un campo dentro de un registro. (Por ejemplo, especifique el valor del campo **Account** del registro seleccionado como **Selected.Account**).

**CamposSeleccionables**: especifica qué campos deben aparecer como vínculos. Establezca el valor de esta propiedad con esta sintaxis:  
**{NombreDeCampo1: true, NombreDeCampo2: true}**  
Ejemplo: si desea que los campos **SalesOrderId** y **Account** aparezcan como vínculos en un formulario, establezca la propiedad **CamposSeleccionables** de ese formulario en este valor:  
**{SalesOrderId : true, Account : true}**

**CampoSeleccionado**: determina en qué campo se hizo clic o se pulsó. Esto solo se aplica a los campos especificados como **CamposSeleccionables**.  
Ejemplo: si establece la propiedad **CamposSeleccionables** en **{SalesOrderId: true, Account: true}** y el usuario hace clic o pulsa en el campo **Account**, **SelectedField.Account** está establecido en true.

**OnFieldSelect**: cómo responde una aplicación cuando el usuario hace clic o pulsa en un campo. Esto solo se aplica a los campos especificados como **CamposSeleccionables**.

**Mode**: determina el modo del formulario. Para cambiar el modo, utilice la función **ViewForm**, **EditarFormulario** o **NewForm**. Estas funciones solo se pueden usar cuando la propiedad **Patrón** está establecida en **FormPattern.Details**. Establezca el valor de la propiedad **Mode** en uno de los de la enumeración **FormMode**.

* **FormMode.View**: permite que los usuarios vean pero no que editen ni agreguen un registro.
* **FormMode.Edit**: permite que los usuarios editen un registro.
* **FormMode.New**: permite que los usuarios agreguen un registro.

**OnSuccess**: la forma en la que responde una aplicación cuando una operación de datos se ha realizado correctamente.

**OnFailure**: la forma en la que responde una aplicación cuando una operación de datos ha sido incorrecta.

**Unsaved**: determina si un registro que un usuario está editando tiene cambios no guardados.

## <a name="related-functions"></a>Funciones relacionadas
Puede usar estas funciones compartidas con el control **Formulario de la entidad** o el [control de formulario Editar](functions/function-form.md). Estas funciones se pueden usar con el control **Formulario de la entidad** solo cuando su propiedad **Patrón** está establecida en **FormPattern.Details**.

**ViewForm**: establece la propiedad **Mode** de un control **Formulario de la entidad** en **FormMode.View**.

**EditarFormulario**: establece la propiedad **Mode** de un control **Formulario de la entidad** en **FormMode.Edit**.

**NewForm**: establece la propiedad **Mode** de un control **Formulario de la entidad** en **FormMode.New**.

**SubmitForm**: guarda los cambios cuando un usuario edita un registro en un control **Formulario de la entidad**.

**ResetForm**: abandona los cambios sin guardar cuando un usuario edita un registro en un control **Formulario de la entidad**.

Después de esta introducción a las distintas propiedades y funciones, se van a mostrar en acción.

> [!NOTE]
> Si no tiene acceso a una base de datos de Common Data Service, cree una antes de empezar a seguir estos pasos.

## <a name="display-a-list-of-records"></a>Mostrar una lista de registros
Los cinco procedimientos siguientes proporcionan un ejemplo único, de principio a fin, de cómo usar controles **Formulario de la entidad**. En este procedimiento, se agrega un formulario que muestra una lista de pedidos de ventas.  

1. Cree una aplicación de tableta vacía.
   
    ![](media/entity-form-control/entityform-tutorial-01-01.png)
2. Cambie el nombre de la primera pantalla a **SalesOrderListScreen**.
   
    ![](media/entity-form-control/entityform-tutorial-01-02.png)
3. En la pestaña **Insertar**, haga clic o pulse en **Formularios** y en **Formulario de la entidad (versión preliminar)**.  
   
    Se agrega un control **Formulario de la entidad** a la pantalla.  
   
    ![](media/entity-form-control/entityform-tutorial-01-03.png)
4. Cambie el nombre del control **Formulario de la entidad** a **SalesOrderListForm** y aumente su tamaño para cubrir toda la pantalla.
5. En el panel derecho, haga clic en o pulse en el icono de la base de datos junto al texto **No se ha seleccionado un origen de datos** y haga clic o pulse en **Agregar un origen de datos**.  
   
    ![](media/entity-form-control/entityform-tutorial-01-04.png)
6. En la lista de conexiones, haga clic o pulse en la conexión para la base de datos.  
   
    ![](media/entity-form-control/entityform-tutorial-01-05.png)
7. En la lista de entidades, haga clic o pulse en **Pedido de ventas** y en **Conectar**.  
   
    Se crea un origen de datos para la entidad **Pedido de ventas** y la propiedad **DataSource** de **SalesOrderListForm** se establece en ese origen de datos.
   
    ![](media/entity-form-control/entityform-tutorial-01-06.png)  
   
    El control **Formulario de la entidad** muestra una lista de pedidos de ventas. Con el control **Formulario de la entidad**, ha mostrado rápidamente un formulario de lista sin tener que crearlo manualmente.
   
    ![](media/entity-form-control/entityform-tutorial-01-07.png)  
   
    No ha configurado la propiedad **Patrón** para el control **Formulario de la entidad**, por lo que el valor predeterminado es el patrón **List**. Por otra parte, el grupo de campos **DefaultList** de la entidad **Pedido de ventas** se usa para mostrar el formulario de lista. Además, el formulario es dinámico y reflejará automáticamente cualquier cambio en el grupo de campos.


## <a name="display-the-details-of-a-record"></a>Mostrar los detalles de un registro
Ahora se va a agregar otro control **Formulario de la entidad** para mostrar los detalles del pedido de ventas que está seleccionado en la lista que creó antes.  

1. Cambie el tamaño de **SalesOrderListForm** hasta que cubra la mitad de la pantalla y agregue un segundo control **Formulario de la entidad** para cubrir la otra mitad.  
   <br>![](media/entity-form-control/entityform-tutorial-01-09.png)
2. Cambie el nombre del segundo control **Formulario de la entidad** a **SalesOrderDetailsForm** y conéctelo al origen de datos **Pedido de ventas** que creó antes.  
   <br>![](media/entity-form-control/entityform-tutorial-01-10.png)
3. Establezca la propiedad **Patrón** de **SalesOrderDetailsForm** en **FormPattern.Details**.  
   
    **SalesOrderDetailsForm** usa el grupo de campos **DefaultDetails** de la entidad **Pedido de ventas** para mostrar el formulario. Al igual que con **SalesOrderListForm**, puede mostrar rápidamente los detalles del registro sin tener que crear manualmente un formulario.  
   
    ![](media/entity-form-control/entityform-tutorial-01-11.png)
4. Establezca la propiedad **Item** de **SalesOrderDetailsForm** en **SalesOrderListForm.Selected**.
   
    **SalesOrderDetailsForm** mostrará los detalles del registro en el que el usuario hace clic o pulsa en **SalesOrderListForm**.
   
    ![](media/entity-form-control/entityform-tutorial-01-12.png)
5. Para obtener una vista previa de la aplicación, presione F5 y haga clic o pulse en un pedido de ventas en la lista de la izquierda.  
   
    Los detalles del pedido que ha seleccionado aparecen a la derecha.  
   
    ![](media/entity-form-control/entityform-tutorial-01-13.png)  

## <a name="configure-a-field-to-navigate-to-another-screen"></a>Configurar un campo para ir a otra pantalla
A continuación, se van a agregar más pantallas a la aplicación y a configurar campos en un control **Formulario de la entidad** para ir a otra pantalla de la aplicación cuando el usuario hace clic o pulsa en un campo.  

1. Agregue una segunda pantalla a la aplicación y cámbiela de nombre a **SalesOrderDetailsScreen**.
2. Corte **SalesOrderDetailsForm**, péguelo en **SalesOrderDetailsScreen** y cambie el formulario de tamaño para que cubra la mayor parte de la pantalla, dejando espacio suficiente para un icono en la parte superior.
3. Agregue un icono Flecha atrás cerca de la esquina superior izquierda de **SalesOrderDetailsScreen**.
4. Establezca la propiedad **AlSeleccionar** del icono Flecha atrás en la función [**Atrás**](functions/function-navigate.md).  
   
    ![](media/entity-form-control/entityform-tutorial-01-14.png)
5. En **SalesOrderListScreen**, cambie el tamaño de **SalesOrderListForm** para que cubra toda la pantalla.
6. Haga clic o pulse en **SalesOrderListForm** para seleccionarlo.
7. En el panel derecho, en **Campos**, establezca **SalesOrderId** para que vaya a **SalesOrderDetailsScreen**.  
   
    ![](media/entity-form-control/entityform-tutorial-01-15.png)
   
    El control **Formulario de la entidad** muestra los valores del campo **SalesOrderId** (la primera columna de la lista) como vínculos.
   
    ![](media/entity-form-control/entityform-tutorial-01-16.png)  
8. Para obtener una vista previa de la aplicación, presione F5 y haga clic o pulse en un vínculo de la lista de pedidos de ventas.
   
    ![](media/entity-form-control/entityform-tutorial-01-17.png)  
   
    Se abre la segunda pantalla y se muestran los detalles del pedido de ventas que ha especificado.
   
    ![](media/entity-form-control/entityform-tutorial-01-18.png)  
   
    Para mostrar los detalles de otro pedido de ventas, haga clic o pulse en la flecha atrás para volver a la lista y haga clic o pulse en el vínculo del pedido cuyos detalles desea mostrar.

## <a name="navigate-with-a-context-variable"></a>Navegar con una variable de contexto
La propiedad **Item** de **SalesOrderDetailsForm** está establecida en **SalesOrderListForm.Selected** para que **SalesOrderDetailsForm** muestre detalles sobre el registro que el usuario seleccione en **SalesOrderListForm**. También puede obtener el contexto del registro seleccionado mediante la variable de contexto **NavigationContext**, que se crea automáticamente cuando se usa el panel de personalización de formularios para configurar un campo al que ir.  

1. Establezca la propiedad **Item** de **SalesOrderDetailsForm** en **NavigationContext**.
   
    ![](media/entity-form-control/entityform-tutorial-01-19.png)
2. Para obtener una vista previa de la aplicación, presione F5 y haga clic o pulse en un vínculo de la lista de pedidos de ventas.
   
    La aplicación abre **SalesOrderDetailsScreen** y muestra los detalles del pedido de ventas que ha especificado.

Ahora se va a profundizar en cómo el panel de personalización de formularios configura la navegación y el contexto.  

La propiedad **CamposSeleccionables** de **SalesOrderListForm** especifica **SalesOrderId** como campo seleccionable.

![](media/entity-form-control/entityform-tutorial-01-20.png)  

Esto se configura automáticamente cuando se utiliza el panel de personalización de formularios para hacer que el campo **SalesOrderId** vaya a **SalesOrderDetailsScreen**. Por lo tanto, los valores del campo **SalesOrderId** aparecen como vínculos.

La propiedad **OnFieldSelect** de **SalesOrderListForm** está establecida en una función [**If**](functions/function-if.md), que determina si el usuario hace clic o pulsa en el campo **Id. de pedido de ventas**: **SalesOrderListForm.SelectedField.SalesOrderId = true**.  

Si la función se evalúa como true, **SalesOrderDetailsScreen** se abre con la variable de contexto denominada **NavigationContext** que se ha usado antes.  

Además, todo esto se configura automáticamente cuando se utiliza el panel de personalización de formularios para hacer que el campo **SalesOrderId** vaya a **SalesOrderDetailsScreen**.  

Por lo tanto, cuando el usuario hace clic o pulsa en un campo Id. de pedido de ventas, la función [**If**](functions/function-if.md) se evalúa como true y se llama a la función [**Navegar**](functions/function-navigate.md) con el contexto correspondiente, lo que abre la pantalla de detalles.  

![](media/entity-form-control/entityform-tutorial-01-21.png)  

> [!NOTE]
> Cuando se usa el panel de personalización de formularios, **NavigationContext** se determina de forma inteligente y automática. Cuando el usuario hace clic o pulsa en **SalesOrderId**, **NavigationContext** se establece en **SalesOrderListForm.Selected**, como se muestra en la fórmula anterior. Si se hubiera especificado el campo **Account** para la navegación en su lugar, **NavigationContext** se habría establecido en **SalesOrderListForm.Selected.Account** para asegurarse de que se pasara el contexto correcto. Sin embargo, para consumir ese contexto, necesitaría tener un control **Formulario de la entidad** conectado a la entidad **Cuenta** en Common Data Service.

## <a name="edit-and-save-a-record"></a>Editar y guardar un registro
Por último, se va a explicar cómo editar y guardar un registro en un control **Formulario de la entidad**.  

1. En **SalesOrderDetailsScreen**, agregue un icono Editar y establezca su propiedad **AlSeleccionar** en esta fórmula:  
   **EditForm(SalesOrderDetailsForm)**
   
    ![](media/entity-form-control/entityform-tutorial-01-22.png)
2. Agregue un icono de marca de verificación junto al icono Editar y establezca la propiedad **AlSeleccionar** del icono de marca de verificación en esta fórmula:  
   **SubmitForm(SalesOrderDetailsForm)**  
   
    ![](media/entity-form-control/entityform-tutorial-01-23.png)
3. Para obtener una vista previa de la aplicación, presione F5, haga clic o pulse en un vínculo **Id. de pedido de ventas** para ver los detalles de un pedido de ventas y haga clic o pulse en el icono Editar.  
   
    La propiedad **Mode** del control **Formulario de la entidad** se establece en **FormMode.Edit** para que pueda editar el registro.
4. Actualice **Estado de pedido** a **Factura**.  
   
    ![](media/entity-form-control/entityform-tutorial-01-24.png)
5. Actualice **Vendedor** a **WRK014**.
   
    Para ayudarle a elegir un valor en **Vendedor**, el control **Formulario de la entidad** representa automáticamente una búsqueda detallada completa. Para generar y mostrar esta búsqueda, el control usa el grupo de campos **DefaultLookup** de la entidad **Trabajador** en Common Data Service. Se usa la entidad **Trabajador** porque el campo **Vendedor** es de tipo **Trabajador**.
   
    ![](media/entity-form-control/entityform-tutorial-01-25.png)
6. Haga clic o pulse en el icono de marca de verificación para guardar los cambios.

Con este paso se finaliza este artículo sobre cómo usar el control **Formulario de la entidad** en sus aplicaciones. Esperamos que la información que se trata aquí le haya resultado útil para empezar a usar el control **Formulario de la entidad**. Estamos deseando escuchar lo que piensa sobre el control **Formulario de la entidad** y nuestra iniciativa general para ayudarle a agregar rápidamente formularios completos a las aplicaciones.

