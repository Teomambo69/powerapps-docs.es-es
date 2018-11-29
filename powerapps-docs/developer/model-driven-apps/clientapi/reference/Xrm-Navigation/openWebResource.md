---
title: openWebResource (referencia de API de cliente) en aplicaciones basadas en modelos | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 798dc921-1e80-42bc-b8ca-2056728bcba4
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="openwebresource-client-api-reference"></a>openWebResource (referencia de la API de cliente)



[!INCLUDE[./includes/openWebResource-description.md](./includes/openWebResource-description.md)]

## <a name="syntax"></a>Sintaxis

`Xrm.Navigation.openWebResource(webResourceName,windowOptions,data)`

## <a name="parameters"></a>Parámetros

|Nombre |Tipo |Obligatoria |Descripción |
|---|---|---|---|
|webResourceName|String|Sí|Nombre del recurso web HTML que se va a abrir.|
|windowOptions|Objeto|No|Opciones de ventana para abrir el recurso web. El objeto contiene los siguientes atributos:<br/>- **height**: número (opcional). Alto de la ventana que se va a abrir, en píxeles.<br/>- **openInNewWindow**: booleano. Indica si el recurso web se va a abrir en una nueva ventana.<br/>- **width**: número (opcional). Ancho de la ventana que se va a abrir, en píxeles.|
|data|String|No|Datos que se pasarán al parámetro de datos.|

## <a name="remarks"></a>Comentarios

Debe usar este método para mostrar recursos de web en lugar del método desusado [Xrm.Utility.openWebResource](https://msdn.microsoft.com/library/jj602956.aspx#BKMK_OpenWebResource).

Un recurso web HTML puede aceptar los valores de parámetro que se describen en [Pasar parámetros a recursos web HTML](../../../webpage-html-web-resources.md#BKMK_PassingParametersToWebResources). Esta función solo permite pasar el parámetro de datos opcional. Para pasar valores para los demás parámetros válidos, debe anexarlos al parámetro `webResourceName`.

> [!NOTE]
> El objeto **Xrm** no está disponible en recursos web de HTML. Por lo tanto, los scripts que contienen métodos `Xrm.*` no se admiten en recursos web HTML. `parent.Xrm.*` funcionará si el recurso web HTML se carga en un contenedor del formulario. Sin embargo, en otros casos, como al cargar un recurso web HTML como parte del mapa del sitio, `parent.Xrm.*` tampoco funcionará. Más información: [función GetGlobalContext y ClientGlobalContext.js.aspx](../GetGlobalContext-ClientGlobalContext.js.aspx.md)



## <a name="examples"></a>Ejemplos

- Abrir un recurso web HTML llamado "new_webResource.htm":
   
   `Xrm.Navigation.openWebResource("new_webResource.htm");`

- Abrir un recurso web HTML estableciendo windowOptions:

  ```
  var windowOptions = { openInNewWindow: true, height: 400, width: 400 }
  Xrm.Navigation.openWebResource("new_webResource.htm",windowOptions);
  ```

- Abrir un recurso web HTML incluyendo un elemento único de datos para el parámetro `data`

  `Xrm.Navigation.openWebResource("new_webResource.htm",null,"dataItemValue");`

 ### <a name="related-topics"></a>Temas relacionados

[Xrm.Navigation](../xrm-navigation.md)

