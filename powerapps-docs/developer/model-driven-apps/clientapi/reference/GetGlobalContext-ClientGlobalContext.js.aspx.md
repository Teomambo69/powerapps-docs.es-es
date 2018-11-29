---
title: GetGlobalContext y ClientGlobalContext.js.aspx en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: conceptual
applies_to:
  - Dynamics 365 (online)
ms.assetid: b58e6173-e3cd-4a3b-b39a-334c295503ec
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getglobalcontext-function-and-clientglobalcontextjsaspx-client-api-reference"></a>La función GetGlobalContext y ClientGlobalContext.js.aspx (referencia de la API cliente)



Utilice la función **GetGlobalContext** cuando programe con [recursos web](../../web-resources.md) para obtener acceso a la información de contexto global, como la información específica del cliente, organización o usuario para su instancia de aplicaciones basadas en modelos. 

Para obtener acceso a la función **GetGlobalContext** en el recurso web HTML, incluya una referencia a **ClientGlobalContext.js.aspx**.

> [!NOTE]
> Al incluir una referencia en **ClientGlobalContext.js.aspx** no pone el objeto **Xrm** disponible en recursos web HTML. Por lo tanto, los scripts que contienen métodos `Xrm.*` no se admiten en recursos web HTML. `parent.Xrm.*` funcionará si el recurso web HTML se carga en un contenedor del formulario. Sin embargo, en otros casos, como al cargar un recurso web HTML como parte del mapa del sitio, `parent.Xrm.*` tampoco funcionará.

## <a name="getglobalcontext-function"></a>Función GetGlobalContext

La función **GetGlobalContext** devuelve el mismo objeto de contexto tal como lo devuelve el método **Xrm.Utility.getGlobalContext**, lo que indica que el objeto de contexto tiene las mismas propiedades y métodos que están disponibles para **Xrm.Utility.getGlobalContext**. Más información: Xrm.Utility.[getGlobalContext](Xrm-Utility/getGlobalContext.md)

## <a name="clientglobalcontextjsaspx"></a>ClientGlobalContext.js.aspx

Debe incluir una referencia a la página **ClientGlobalContext.js.aspx** situada en la raíz del directorio de recursos web para poder usar la función **GetGlobalContext**.

- Si no está usando las caracteres de barra diagonal inversa en los nombres de recursos web HTML para simular una estructura de carpetas, puede incluir este script haciendo referencia directamente a él. Por ejemplo:

    ```HTML
    <head>
      <title>HTML Web Resource</title>
      <script src="ClientGlobalContext.js.aspx" type="text/javascript" ></script>
      
    </head>
    ```
- Si no está usando las caracteres de barra diagonal inversa en los nombres de recursos web HTML para simular una estructura de directorios, debe reflejar esto en el elemento de script. El siguiente ejemplo es para un recurso web HTML llamado **sdk_/Contoso.htm** y un recurso web JavaScript llamado **sdk_/Scripts/ContosoScript.js** con un recurso web CSS llamado **sdk_/Styles/ContosoStyles.css**.

    ```HTML
    <head>
      <title>HTML Web Resource</title>
      <script src="../ClientGlobalContext.js.aspx" type="text/javascript" ></script>

      <script src="Scripts/ContosoScript.js" type="text/javascript"></script>
      <link href="Styles/ContosoStyles.css" rel="stylesheet" type="text/css" />
    </head>

    ```

> [!NOTE]
> El uso de una ruta de acceso relativa que incluye la carpeta WebResources raíz, por ejemplo, /WebResources/ClientGlobalContext.js.aspx, no es recomendable porque puede hacer que la página pierda contexto de organización en un entorno multiempresa.

La página **ClientGlobalContext.js.aspx** incluirá algunos controladores de eventos globales. Estos controladores de eventos cancelarán los eventos [onselectstart](https://developer.mozilla.org/en-US/docs/Web/Events/selectstart), [contextmenu](https://developer.mozilla.org/en-US/docs/Web/Events/contextmenu) y [ondragstart](https://developer.mozilla.org/en-US/docs/Web/Events/dragstart). 

### <a name="related-topics"></a>Temas relacionados

[Xrm.Utility.getGlobalContext](Xrm-Utility/getGlobalContext.md)

[Comprender el modelo de objetos de la API de cliente](../understand-clientapi-object-model.md) 

[Recursos web para aplicaciones basadas en modelos](../../web-resources.md)

