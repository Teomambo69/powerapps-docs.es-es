---
title: Definir las reglas de habilitación de la cinta de opciones (aplicaciones basadas en modelos) | Microsoft Docs
description: Obtenga información sobre cómo definir las reglas específicas a supervisar cuando se habilitan los elementos de la cinta de opciones al configurar los elementos de la cinta de opciones.
keywords: ''
ms.date: 10/31/2018
ms.service:
  - powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: 201f5db9-be65-7c3b-8202-822d78338bd6
author: JimDaly
ms.author: jdaly
manager: shilpas
ms.reviewer: null
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="define-ribbon-enable-rules"></a>Definir las reglas de habilitación de la cinta de opciones

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/customize-dev/define-ribbon-enable-rules -->

Al configurar los elementos de la cinta de opciones se pueden definir las reglas para supervisar cuando se habilitan los elementos de la cinta de opciones. El elemento `<EnableRule>` se usa de la siguiente manera:  

-   Use el elemento `/RuleDefinitions/EnableRules/EnableRule` para definir las reglas que controlan cuándo debe habilitarse el elemento de la cinta de opciones.  

-   Use el elemento `/CommandDefinitions/CommandDefinition/EnableRules/EnableRule` para asociar reglas de habilitación específicas a una definición de comando.  

## <a name="what-does-enabled-mean"></a>¿Qué significa estar habilitado?  
 En la barra de comandos, los comandos deshabilitados están ocultos. En la cinta de opciones, los comandos deshabilitados están visibles pero no responden a eventos.  

## <a name="control-when-ribbon-elements-are-enabled"></a>Controlar cuando los elementos de la cinta de opciones están habilitados  
 Las reglas de habilitación se proporcionan para que puedan reutilizarse. Al definirlas con definiciones de reglas, se puede usar la misma regla de habilitación para muchas definiciones de comando. Cuando más de una regla de habilitación está definida para una definición de comando, todas las reglas de habilitación deben evaluarse como true para que el elemento de la cinta de opciones esté habilitado.  

 Todas las reglas de habilitación proporcionan un atributo opcional para especificar si el valor predeterminado de la regla es true o false, y un atributo `InvertResult` opcional para permitir que se devuelva un resultado negativo cuando el elemento que se está probando devuelve true.  

 El elemento `/RuleDefinitions/EnableRules/EnableRule` admite los siguientes tipos de reglas:  

### <a name="command-client-type-rule"></a>Regla de tipo de cliente de comando
 Usa el elemento `<CommandClientTypeRule>`. [!INCLUDE[ribbon_element_CommandClientTypeRule](../../includes/ribbon-element-commandclienttyperule.md)]  

 Los valores `Type` corresponden a lo siguiente:  


|   Value   |                                                                               Presentación                                                                               |
|-----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Modern`  |                                       La barra de comandos se muestra mediante Microsoft Dynamics 365 for tablets.                                       |
| `Refresh` |                                                      La barra de comandos se muestra mediante la interfaz de usuario actualizada.                                                      |
| `Legacy`  | La cinta de opciones se muestra en los formularios de entidades que no se actualizaron o en una vista de lista en Dynamics 365 for Outlook. |

### <a name="crm-client-type-rule"></a>Regla de tipo de cliente CRM
Usa el elemento `<CrmClientTypeRule>` para permitir la definición de reglas en función del tipo de cliente utilizado. Las opciones de tipo son las siguientes:  

-   `Web`  

-   `Outlook`  

### <a name="crm-offline-access-state-rule"></a>Regla de estado de acceso sin conexión de CRM
 Usa el elemento `<CrmOfflineAccessStateRule>`. Use este los criterios para habilitar un elemento de la cinta de opciones en función de si Dynamics 365 for Microsoft Office Outlook con acceso sin conexión está funcionando actualmente sin conexión.  

### <a name="crm-outlook-client-type-rule"></a>Regla de tipo de cliente Outlook de CRM
 Usa el elemento `<CrmOutlookClientTypeRule>`. Use esta regla si desea mostrar solo un botón para un tipo específico de Dynamics 365 for Outlook. Las opciones de tipo son las siguientes:  

-   `CrmForOutlook`  

-   `CrmForOutlookOfflineAccess`  

### <a name="custom-rule"></a>Regla personalizada
 Usa el elemento `<CustomRule>`. Use este tipo de regla para llamar a una función de una biblioteca de JavaScript que devuelve un valor booleano.  

> [!NOTE]
>  Las reglas personalizadas que no devuelven un valor rápidamente pueden afectar al rendimiento de la cinta de opciones. Si tiene que realizar la lógica que puede tardar algún tiempo en completarse, use la siguiente estrategia para crear su regla personalizada asincrónica:  
>   
> 1.  Defina una regla que compruebe si tiene un objeto personalizado. Puede comprobar si tiene un objeto como `Window.ContosoCustomObject.RuleIsTrue` que acaba de adjuntar a la ventana.  
> 2.  Si existe el objeto, debe devolverlo  
> 3.  Si no existe el objeto, defina el objeto y establezca el valor como false.  
> 4.  Antes de devolver un valor, use [settimeout](https://msdn.microsoft.com/library/ms536753\(VS.85\).aspx) <!-- TODO not sure about this link--> para ejecutar una función de devolución de llamada asincrónica para volver a establecer el objeto. Después devuelva false.  
> 5.  Después de que la función de devolución de llamada haya realizado las operaciones necesarias para determinar el resultado correcto, establece el valor del objeto y usa el método `refreshRibbon` para actualizar la cinta de opciones.  
> 6.  Cuando se actualiza la cinta de opciones, esta detecta el objeto así como el conjunto exacto de valores y se evalúa la regla.  

### <a name="entity-rule"></a>Regla de entidad
 Usa el elemento `<EntityRule>`. Las reglas de la entidad permiten la evaluación de la entidad actual. Esto resulta útil al definir acciones personalizadas que se aplican a la plantilla de la entidad en lugar de a las entidades específicas. Por ejemplo, es posible que desee agregar un elemento de la cinta de opciones en todas las entidades excepto en algunas entidades específicas. Es más fácil definir la acción personalizada de la plantilla de la entidad que se aplica a todas las entidades y después usar una regla de la entidad para filtrar aquellas que se deben excluir.  

 La regla de entidad también incluye un atributo Context opcional para especificar si se muestra la entidad en el formulario o en una lista (HomePageGrid). El atributo opcional `AppliesTo` se puede establecer en `PrimaryEntity` o en `SelectedEntity` para distinguir si se muestra la entidad en una subcuadrícula.  

### <a name="form-state-rule"></a>Regla de estado del formulario
 Usa el elemento `<FormStateRule>`. Use la regla `FormState` para determinar el tipo actual de formulario que se muestra en un registro. Las opciones de estado son las siguientes:  

-   `Create`  

-   `Existing`  

-   `ReadOnly`  

-   `Disabled`  

-   `BulkEdit`  

### <a name="or-rule"></a>Regla O
 Usa el elemento `<OrRule>`. `OrRule` permite reemplazar el valor de comparación predeterminado AND para varios tipos de reglas de habilitación. Use el elemento `OrRule` para definir varias combinaciones posibles válidas para comprobar.

### <a name="outlook-item-tracking-rule"></a>Regla de seguimiento de elementos de Outlook
 Usa el elemento `<OutlookItemTrackingRule>`. Use el atributo `TrackedInCrm` de este elemento para determinar si se realiza el seguimiento del registro en Common Data Service para aplicaciones.  

### <a name="outlook-version-rule"></a>Regla de la versión de Outlook
 Usa el elemento `<OutlookVersionRule>`. Use esto para habilitar un elemento de la cinta de opciones de una versión determinada de Office Outlook, de la siguiente manera:  

-   `2003`  

-   `2007`  

-   `2010`  

### <a name="page-rule"></a>Regla de página
 Usa el elemento `<PageRule>`. Este tipo de regla compruebe la dirección URL de la página que se muestra. Devuelve true si coincide con `Address`.  

### <a name="record-privilege-rule"></a>Regla de privilegios de registro
 Usa el elemento `<RecordPrivilegeRule>`. Use esta regla para determinar si el usuario actual tiene privilegios en un registro específico. Estos privilegios difieren del privilegio de la entidad porque pueden incluir los privilegios obtenidos por otro usuario que comparte el registro con el usuario actual.  

### <a name="selection-count-rule"></a>Regla de recuento de selección
 Usa el elemento `<SelectionCountRule>`. Use este tipo de regla con una cinta de opciones para que aparezca una lista para habilitar un botón cuando se seleccionan los números de registros máximos y mínimos específicos en la cuadrícula. Por ejemplo, si el botón combina los registros, debe asegurarse de que al menos dos registros están seleccionados antes de habilitar el control de la cinta de opciones.  

### <a name="sku-rule"></a>Regla de SKU
 Usa el elemento `<SkuRule>`. Use este tipo de regla para habilitar un elemento de la cinta de opciones para una versión de SKU determinada de Dynamics 365, de la siguiente manera:  

-   `OnPremise`  

-   `Online`  

-   `Spla`  

### <a name="value-rule"></a>Regla de valor
Usa el elemento `<ValueRule>`. Use esta regla para comprobar el valor de un campo específico en el registro que se muestra en el formulario. Debe especificar `Field` y `Value` para comprobar.  

### <a name="see-also"></a>Vea también  
 [Personalización de comandos y la cinta de opciones](customize-commands-ribbon.md)   
 [Definir comandos de la cinta de opciones](define-ribbon-commands.md)   
 [Definir reglas de visualización de la cinta de opciones](define-ribbon-display-rules.md)
