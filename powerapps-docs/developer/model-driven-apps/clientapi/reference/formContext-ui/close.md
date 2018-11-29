---
title: close (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 1261a94d-4f5c-446d-8c29-a326e819696b
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="close-client-api-reference"></a>close (referencia de la API de cliente)



[!INCLUDE[./includes/close-description.md](./includes/close-description.md)]

## <a name="syntax"></a>Sintaxis

`formContext.ui.close();`

## <a name="remarks"></a>Comentarios

El método **Window.close** de HTML se ha suprimido. Para cerrar una ventana, primero debe usar este método. Si hay cambios sin guardar en el formulario, se le preguntará al usuario si desea guardar los cambios antes de cerrar la ventana.

Para Microsoft Dynamics 365 for tablets, este método imita el comportamiento del botón atrás de navegación.

### <a name="related-topics"></a>Temas relacionados

[formContext.ui](../formContext-ui.md)

[formContext](../../clientapi-form-context.md)

