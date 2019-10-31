---
title: Referencia API de cliente para aplicaciones basadas en modelos | MicrosoftDocs
description: El tema se proporciona la referencia de API de clientes para aplicaciones basadas en modelos.
ms.date: 06/27/2019
ms.service: powerapps
ms.topic: conceptual
applies_to:
  - Dynamics 365 (online)
ms.assetid: null
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="client-api-reference-for-model-driven-apps"></a>Referencia API de cliente para aplicaciones basadas en modelos



Esta sección contiene documentación de referencia para modelos de objetos de API de cliente que se pueden usar con las bibliotecas JavaScript.

> [!IMPORTANT]
> - El modelo de objetos de API de cliente también contiene el espacio de nombres **Xrm.Internal** y no se pueden usar los objetos/métodos en este espacio de nombres. Estos objetos, así como partes del Document Object Model (DOM) HTML, está sujetos a modificaciones sin previo aviso. Recomendamos no usar estas funciones o cualquier script que dependa del DOM.
> - También, al depurar puede encontrar métodos y objetos en el modelo de API de cliente sin documentar. Solo se admiten objetos y métodos documentados.
> - Los API de script del cliente disponible en esta documentación también se aplica a Dynamics 365 Customer Engagement (on-premises).

Los temas de esta sección se organizan del siguiente modo:
- Comienza con la referencia de todos los eventos, colecciones y el objeto de contexto de ejecución.
- Continúa proporcionando información sobre métodos para **atributos** y **controles** en Customer Enagagement que son realmente colecciones que aparecen bajo objetos diferentes en el modelo de objetos de API de cliente.
- Proporciona una referencia de las propiedades y los métodos de los objetos **formContext** y **gridContext**.
- Por último, incluye una referencia para espacios de nombres en el modelo de objetos **Xrm**. 

### <a name="related-topics"></a>Temas relacionados

[Aplicar la lógica de negocios usando scripting de cliente en aplicaciones basadas en modelos](../client-scripting.md)<br/>
[Comprender el modelo de objetos de la API de cliente](understand-clientapi-object-model.md)<br/>
[Resumen de las aplicaciones orientadas a modelos de desarrollador](../overview.md)
