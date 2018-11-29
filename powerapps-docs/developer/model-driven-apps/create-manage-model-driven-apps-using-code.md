---
title: 'Crear, administrar, y publicar aplicaciones basadas en modelos con código | Microsoft Docs'
description: 'Obtenga información sobre cómo crear, administrar y publicar aplicaciones basadas en modelos usando código en PowerApps.'
keywords: ''
ms.date: 10/31/2018
ms.service:
  - powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: 4261c476-2eff-10e3-a334-d02e0cbbb9d5
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

# <a name="create-manage-and-publish-model-driven-apps-using-code"></a>Crear, administrar, y publicar aplicaciones basadas en modelos con código

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/create-manage-custom-business-apps-using-code -->

Además de crear una aplicación basada en modelos usando el diseñador de aplicaciones PowerApps, puede mediante programación crear y administrar aplicaciones basadas en modelos. 

> [!IMPORTANT]
> No tiene que escribir código para crear aplicaciones basadas en modelos si no es necesario. El diseñador de aplicaciones proporciona una experiencia mucho más sencilla e intuitiva para la creación de aplicaciones basadas en modelos sin necesidad de escribir código mediante el suministro de una estructura de información basada en ventanas y una interfaz simplificada. Consúltelo aquí: [Diseñar aplicaciones basadas en modelos mediante el diseñador de aplicaciones](../../maker/model-driven-apps/design-custom-business-apps-using-app-designer.md)  
  
La creación de una aplicación basada en modelos implica los pasos siguientes:
1. Crear una instancia [entidad AppModule](../common-data-service/reference/entities/appmodule.md) para definir la aplicación y sus propiedades.
2. Agregar o quitar componentes de la aplicación como la entidad, el mapa del sitio y otros componentes de su aplicación personalizada mediante las acciones <xref:Microsoft.Dynamics.CRM.AddAppComponents> y <xref:Microsoft.Dynamics.CRM.RemoveAppComponents>.
3. Comprobar que la aplicación tenga todos los componentes necesarios que faltan mediante la función <xref:Microsoft.Dynamics.CRM.ValidateApp>.
4. Publicar la aplicación.
5. Asociar roles de seguridad adecuados a la aplicación basada en modelos para proporcionar acceso a los usuarios.


## <a name="create-your-model-driven-app-and-define-its-properties"></a>Crear la aplicación basada en modelos y definir sus propiedades

Para poder crear una aplicación debe disponer del rol de seguridad de Administrador del sistema o de Personalizador del sistema o permisos equivalentes. Puede seleccionar uno de los siguientes tipos de aplicación para especificar al cliente que la aplicación se usará para: 
- **Web**: este es el cliente de explorador web clásico de Dynamics 365.
- **Interfaz unificada**: se ejecuta en la nueva interfaz unificada, que proporciona importantes ventajas asociadas a la accesibilidad y el diseño dinámico. Para obtener más información sobre la nueva interfaz unificada, vea la sección [Marco de trabajo de interfaz unificada para las nuevas aplicaciones](/dynamics365/get-started/whats-new/customer-engagement/new-in-version-9#unified-interface-framework-for-new-apps). 

Seleccione el tipo de aplicación especificando un valor entero para el atributo **clienttype**: 2 para **Web** y 4 para **Interfaz unificada**. Si no especifica ningún tipo de aplicación, se establece en **Web** de forma predeterminada. 

Especifique como mínimo las siguientes propiedades para crear una aplicación:
- **name**: único para la aplicación
- **uniquename**: puede ser diferente del nombre de la aplicación y solo puede tener caracteres en inglés y números. Al crear esta aplicación, el nombre se antepone automáticamente con su prefijo de editor de soluciones (por ejemplo, 'new_'). 
- **webresourceid**: identificador de los recursos web que desea establecer como el icono de imagen de la aplicación. El sistema proporciona un recurso web predeterminado (identificador: 953b9fac-1e5e-e611-80d6-00155ded156f) que puede usar como icono de la aplicación.

La siguiente solicitud de API web crea un tipo de interfaz unificada de una aplicación:

```http
POST [Organization URI]/api/data/v9.0/appmodules HTTP/1.1
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0
Accept: application/json

{
    "name": "SDKTestApp",
    "uniquename":"SDKTestApp",
    "webresourceid":"953b9fac-1e5e-e611-80d6-00155ded156f",
    "clienttype": 4
}
```

El encabezado **OData-EntityId** de respuesta contiene el URI de la aplicación creada.

```http
HTTP/1.1 204 No Content
OData-Version: 4.0
OData-EntityId: [Organization URI]/api/data/v9.0/appmodules(dd621d4a-d898-e711-80e7-00155db763be)
```  

## <a name="add-or-remove-components-from-your-model-driven-app"></a>Agregar o quitar componentes de la aplicación basada en modelos

Puede agregar o quitar componentes de una aplicación como el mapa del sitio, la entidad, el panel, los flujos de procesos empresariales, las vistas y los formularios que desea incluir en su aplicación basada en modelos. Para obtener información detallada sobre los componentes que se pueden agregar a una aplicación basada en modelos, vea [Agregar o editar componentes de la aplicación en el diseñador de aplicaciones](../../maker/model-driven-apps/add-edit-app-components.md).

Utilice la acción <xref:Microsoft.Dynamics.CRM.AddAppComponents> o el mensaje <xref:Microsoft.Crm.Sdk.Messages.AddAppComponentsRequest> para agregar componentes a la aplicación basada en modelos. La acción requiere que especifique lo siguiente:
- **AppId**: identificador de la aplicación en la que desea agregar componentes
- **Components** Una colección de componentes que se va a agregar. Debe especificar el identificador y el tipo de entidad del componente que desea agregar. Para obtener una lista de los tipos de entidad en la API web de CDS for Apps, consulte <xref:Microsoft.Dynamics.CRM.EntityTypeIndex>.

La siguiente solicitud de la API web agrega una vista (savedquery) y un formulario (systemform) a la aplicación:

```http
POST [Organization URI]/api/data/v9.0/AddAppComponents HTTP/1.1
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0
Accept: application/json

{
    "AppId":"dd621d4a-d898-e711-80e7-00155db763be",
    "Components":[
        {
            "savedqueryid":"00000000-0000-0000-00aa-000000666000",
            "@odata.type":"Microsoft.Dynamics.CRM.savedquery"
        },
        {
            "formid":"c9e7ec2d-efca-4e4c-b3e3-f63c4bba5e4b",
            "@odata.type":"Microsoft.Dynamics.CRM.systemform"
        }
    ]
}
```

Para quitar un componente de una aplicación, utilice la acción <xref:Microsoft.Dynamics.CRM.RemoveAppComponents> o el mensaje <xref:Microsoft.Crm.Sdk.Messages.RemoveAppComponentsRequest>. Esta acción tiene el mismo conjunto de parámetros que la acción **AddAppComponents**.

La siguiente solicitud de la API web quita una vista (savedquery) de la aplicación: 

```http
POST [Organization URI]/api/data/v9.0/RemoveAppComponents HTTP/1.1
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0
Accept: application/json

{
    "AppId":"dd621d4a-d898-e711-80e7-00155db763be",
    "Components":[
        {
            "savedqueryid":"00000000-0000-0000-00aa-000000666000",
            "@odata.type":"Microsoft.Dynamics.CRM.savedquery"
        }
    ]
}
```

## <a name="validate-your-model-driven-app"></a>Validar su aplicación controlada por modelos

Validar una aplicación implica comprobar las dependencias de los componentes que ha agregado a la aplicación basada en modelos para asegurarse de que la aplicación funciona correctamente. Es lo mismo que hacer clic en **Validar** en el diseñador de la aplicación. Más información: [Validar la aplicación](../../maker/model-driven-apps/validate-app.md)

Utilice la función <xref:Microsoft.Dynamics.CRM.ValidateApp> o el mensaje <xref:Microsoft.Crm.Sdk.Messages.ValidateAppRequest> para validar la aplicación. La siguiente solicitud de la API web muestra cómo validar la aplicación basada en modelos con identificador dd621d4a-d898-e711-80e7-00155db763be:

`GET [Organization URI]/api/data/v9.0/ValidateApp(AppModuleId=dd621d4a-d898-e711-80e7-00155db763be)`

Si no hay ningún error de validación, la respuesta es la siguiente:

```http
HTTP/1.1 200 OK
OData-Version: 4.0

{
    "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#Microsoft.Dynamics.CRM.ValidateAppResponse",
    "AppValidationResponse": {
        "ValidationSuccess": true,
        "ValidationIssueList": []
    }
}
```

Si hay problemas de validación en la aplicación, la respuesta muestra errores o advertencias en la colección **ValidationIssueList**:

```http
HTTP/1.1 200 OK
OData-Version: 4.0

{
    "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#Microsoft.Dynamics.CRM.ValidateAppResponse",
    "AppValidationResponse": {
        "ValidationSuccess": false,
        "ValidationIssueList": [
            {
                "ErrorType": "Error",
                "Message": "App does not contain Site Map",
                "DisplayName": null,
                "ComponentId": "00000000-0000-0000-0000-000000000000",
                "ComponentType": 0,
                "ComponentSubType": 0,
                "ParentEntityId": "00000000-0000-0000-0000-000000000000",
                "ParentEntityName": null,
                "CRMErrorCode": -2147155684,
                "RequiredComponents": []
            },
            {
                "ErrorType": "Warning",
                "Message": "Account doesn’t reference a form or view. App users will see all forms and views.",
                "DisplayName": null,
                "ComponentId": "00000000-0000-0000-0000-000000000000",
                "ComponentType": 0,
                "ComponentSubType": 0,
                "ParentEntityId": "00000000-0000-0000-0000-000000000000",
                "ParentEntityName": null,
                "CRMErrorCode": -2147155691,
                "RequiredComponents": []
            }
        ]
    }
}
```

## <a name="publish-your-model-driven-app"></a>Publicar su aplicación controlada por modelos

Después de agregar los componentes necesarios a la aplicación basada en modelos y validarla, debe publicarla para que esté disponible para los usuarios.

Utilice la acción <xref:Microsoft.Dynamics.CRM.PublishXml> o el mensaje <xref:Microsoft.Crm.Sdk.Messages.PublishXmlRequest> para publicar la aplicación basada en modelos. La siguiente solicitud de la API web muestra cómo publicar la aplicación basada en modelos con identificador dd621d4a-d898-e711-80e7-00155db763be:

```http
POST [Organization URI]/api/data/v9.0/PublishXml HTTP/1.1
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0
Accept: application/json

{  
  "ParameterXml":"<importexportxml><appmodules><appmodule>dd621d4a-d898-e711-80e7-00155db763be</appmodule></appmodules></importexportxml>"
}
```

## <a name="manage-access-to-model-driven-app-using-security-roles"></a>Administrar el acceso a la aplicación basada en modelos mediante roles de seguridad

Para proporcionar a los usuarios acceso a las aplicaciones de forma que puedan acceder a ellas desde su área **Configuración** > **Mis aplicaciones** o desde la página de inicio de Dynamics 365, puede asociar roles de seguridad a las aplicaciones basada en modelos. Los usuarios asignados a los roles de seguridad asociados pueden ver y usar las aplicaciones basada en modelos en CDS for Apps. 

Utilice la propiedad de navegación **appmoduleroles_association** de la entidad [Entidad AppModule](../common-data-service/reference/entities/appmodule.md) para asociar una aplicación basada en modelos con un rol de seguridad. La siguiente solicitud muestra cómo asociar una aplicación basada en modelos con un rol de seguridad:

```http
POST [Organization URI]/api/data/v9.0/appmodules(dd621d4a-d898-e711-80e7-00155db763be)appmoduleroles_association/$ref HTTP/1.1
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0
Accept: application/json

{  
  "@odata.id":"[Organization URI]/api/data/v9.0/roles(<roleId>)"
}
```

Para desvincular un rol de seguridad de una aplicación basada en modelos, use la solicitud DELETE con la misma propiedad de navegación. Por ejemplo:

`DELETE [Organization URI]/api/data/v9.0/appmodules(dd621d4a-d898-e711-80e7-00155db763be)/appmoduleroles_association/$ref?$id=[Organization URI]/api/data/v9.0/roles(<roleId)
`

## <a name="manage-your-model-driven-apps-and-its-components"></a>Administrar las aplicaciones basada en modelos y sus componentes

En esta sección se ofrece información acerca de cómo recuperar las aplicaciones, actualizar las propiedades de la aplicación, recuperar los componentes de la aplicación y eliminar aplicaciones.

### <a name="retrieve-published-apps"></a>Recuperar aplicaciones publicadas
Para recuperar las aplicaciones publicadas, utilice la solicitud siguiente:

`GET [Organization URI]/api/data/v9.0/appmodules?$select=name,clienttype`

### <a name="retrieve-unpublished-apps"></a>Recuperar aplicaciones no publicadas
Para recuperar aplicaciones no publicadas, utilice la función <xref:Microsoft.Dynamics.CRM.RetrieveUnpublishedMultiple>. Por ejemplo:

`GET [Organization URI]/api/data/v9.0/appmodules/Microsoft.Dynamics.CRM.RetrieveUnpublishedMultiple()?$select=name,clienttype`

### <a name="retrieve-components-in-a-published-model-driven-app"></a>Recuperar componentes de una aplicación basada en modelos publicada
Para recuperar componentes de una aplicación basada en modelos, utilice la función <xref:Microsoft.Dynamics.CRM.RetrieveAppComponents> o el mensaje <xref:Microsoft.Crm.Sdk.Messages.RetrieveAppComponentsRequest>. Por ejemplo:

`GET [Organization URI]/api/data/v9.0/RetrieveAppComponents(AppModuleId=dd621d4a-d898-e711-80e7-00155db763be)`

### <a name="retrieve-security-roles-associated-with-published-model-driven-app"></a>Recuperar roles de seguridad asociados con aplicaciones basadas en modelos publicadas

Para recuperar los roles de seguridad asociados con la aplicación basada en modelos, utilice la opción consulta del sistema `$expand` con la propiedad de navegación **appmoduleroles_association**. Por ejemplo, esta es la solicitud para recuperar todos los roles de seguridad asociados con una aplicación basada en modelos con el identificador siguiente: dd621d4a d898 e711 80e7 00155db763be:

`GET [Organization URI]/api/data/v9.0/appmodules(dd621d4a-d898-e711-80e7-00155db763be)?$expand=appmoduleroles_association&$select=name,appmoduleroles_association`

### <a name="delete-model-driven-apps"></a>Eliminar aplicaciones controlada por modelos

Utilice la solicitud DELETE para eliminar una aplicación basada en modelos. Por ejemplo:

`DELETE [Organization URI]/api/data/v9.0/appmodules(dd621d4a-d898-e711-80e7-00155db763be)`

## <a name="client-api-support-for-model-driven-apps"></a>Soporte API de clientes para las aplicaciones basadas en modelos

Puede usar las siguientes API de cliente para trabajar con aplicaciones basadas en modelos:

- [getCurrentAppName](clientapi/reference/xrm-utility/getglobalcontext/getcurrentappname.md)
- [getCurrentAppProperties](clientapi/reference/xrm-utility/getglobalcontext/getCurrentAppProperties.md)
- [getCurrentAppUrl](clientapi/reference/xrm-utility/getglobalcontext/getCurrentAppUrl.md) 
  
### <a name="see-also"></a>Vea también  
[Diseñar aplicaciones controladas por modelos usando el diseñador de aplicaciones](../../maker/model-driven-apps/design-custom-business-apps-using-app-designer.md)
 
