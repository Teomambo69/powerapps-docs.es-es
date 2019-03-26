---
title: Definir las reglas de habilitación de la cinta de opciones (aplicaciones basadas en modelos) | Microsoft Docs
description: Obtenga información sobre cómo definir las reglas específicas a supervisar cuando se habilitan los elementos de la cinta de opciones al configurar los elementos de la cinta de opciones.
keywords: ''
ms.date: 02/08/2019
ms.service:
  - powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: 201f5db9-be65-7c3b-8202-822d78338bd6
author: JesseParsons
ms.author: jeparson
manager: annbe
ms.reviewer: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="define-ribbon-enable-rules"></a>Definir las reglas de habilitación de la cinta de opciones

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
| `Modern`  |                                       La barra de comandos se muestra mediante [!INCLUDE[pn_moca_full](../../includes/pn-moca-full.md)].                                       |
| `Refresh` |                                                      La barra de comandos se muestra mediante la interfaz de usuario actualizada.                                                      |
| `Legacy`  | La cinta de opciones se muestra en los formularios de entidades que no se actualizaron o en una vista de lista en [!INCLUDE[pn_crm_for_outlook_full](../../includes/pn-crm-for-outlook-full.md)]. |

### <a name="crm-client-type-rule"></a>Regla de tipo de cliente CRM
Usa el elemento `<CrmClientTypeRule>` para permitir la definición de reglas en función del tipo de cliente utilizado. Las opciones de tipo son las siguientes:  

-   `Web`  

-   `Outlook`  

### <a name="crm-offline-access-state-rule"></a>Regla de estado de acceso sin conexión de CRM
 Usa el elemento `<CrmOfflineAccessStateRule>`. Use este criterio para habilitar un elemento de la cinta de opciones en función de si [!INCLUDE[pn_crm_outlook_offline_access](../../includes/pn-crm-outlook-offline-access.md)] está actualmente sin conexión.  

### <a name="crm-outlook-client-type-rule"></a>Regla de tipo de cliente Outlook de CRM
 Usa el elemento `<CrmOutlookClientTypeRule>`. Use esta regla si desea mostrar solo un botón para un tipo específico de [!INCLUDE[pn_crm_for_outlook_full](../../includes/pn-crm-for-outlook-full.md)]. Las opciones de tipo son las siguientes:  

-   `CrmForOutlook`  

-   `CrmForOutlookOfflineAccess`  

### <a name="custom-rule"></a>Regla personalizada
 Usa el elemento `<CustomRule>`. Use este tipo de regla para llamar a una función en una biblioteca de JavaScript que devuelva una promesa (interfaz unificada) o un valor booleano (interfaz unificada y cliente web).

```JavaScript
function EnableRule()
{
    const value = Xrm.Page.getAttribute("field1").getValue();
    return value === "Active";
}
```

> [!NOTE]
>  Las reglas personalizadas que no devuelven un valor rápidamente pueden afectar al rendimiento de la cinta de opciones. Si tiene que realizar lógica que puede tardar algún tiempo en completarse (por ejemplo, una solicitud de red), use la siguiente estrategia para crear su regla personalizada asincrónica.

 La reglas de la interfaz unificada admiten que se devuelva una promesa más que un valor booleano para la evaluación de reglas asincrónica. Si la promesa no se resuelve en 10 segundos, la regla se resolverá con un valor false.
 > [!NOTE]
>  Las reglas basadas en promesas solo funcionarán en la interfaz unificada, por lo que no se pueden usar si se sigue utilizando el típico cliente web.
 ```JavaScript
function EnableRule()
{
    const request = new XMLHttpRequest();
    request.open('GET', '/bar/foo');

    return new Promise((resolve, reject) =>
    {
        request.onload = function (e)
        {
            if (request.readyState === 4)
            {
                if (request.status === 200)
                {
                    resolve(request.responseText === "true");
                }
                else
                {
                    reject(request.statusText);
                }
            }
        };
        request.onerror = function (e)
        {
            reject(request.statusText);
        };

        request.send(null);
    });
}
```


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
 Usa el elemento `<OutlookItemTrackingRule>`. Use el atributo `TrackedInCrm` de este elemento para determinar si se realiza el seguimiento del registro en PowerApps.  

### <a name="outlook-version-rule"></a>Regla de la versión de Outlook
 Usa el elemento `<OutlookVersionRule>`. Use esto para habilitar un elemento de la cinta de opciones de una versión determinada de [!INCLUDE[pn_MS_Outlook_Full](../../includes/pn-ms-outlook-full.md)], de la siguiente manera:  

-   `2003`  

-   `2007`  

-   `2010`  

### <a name="page-rule"></a>Regla de página
 Usa el elemento `<PageRule>`. Este tipo de regla compruebe la dirección URL de la página que se muestra. Devuelve true si coincide con `Address`.  

### <a name="record-privilege-rule"></a>Regla de privilegios de registro
 Usa el elemento `<RecordPrivilegeRule>`. Use esta regla para determinar si el usuario actual tiene privilegios en un registro específico. Estos privilegios difieren del privilegio de la entidad porque pueden incluir los privilegios obtenidos por otro usuario que comparte el registro con el usuario actual.  

### <a name="selection-count-rule"></a>Regla de recuento de selección
 Usa el elemento `<SelectionCountRule>`. Use este tipo de regla con una cinta de opciones para que aparezca una lista para habilitar un botón cuando se seleccionan los números de registros máximos y mínimos específicos en la cuadrícula. Por ejemplo, si el botón combina los registros, debe asegurarse de que al menos dos registros están seleccionados antes de habilitar el control de la cinta de opciones.  

### <a name="value-rule"></a>Regla de valor
Usa el elemento `<ValueRule>`. Use esta regla para comprobar el valor de un campo específico en el registro que se muestra en el formulario. Debe especificar `Field` y `Value` para comprobar.

### <a name="see-also"></a>Vea también  
 [Personalización de comandos y la cinta de opciones](customize-commands-ribbon.md)   
 [Definir comandos de la cinta de opciones](define-ribbon-commands.md)   
 [Definir reglas de visualización de la cinta de opciones](define-ribbon-display-rules.md)
