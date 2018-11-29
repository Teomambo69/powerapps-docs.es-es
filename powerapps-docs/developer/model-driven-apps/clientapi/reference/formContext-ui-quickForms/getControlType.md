---
title: getControlType (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 72d6c761-bcc7-4de6-b73f-5f2833297825
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getcontroltype-client-api-reference"></a>getControlType (referencia de la API de cliente)



[!INCLUDE[./includes/getControlType-description.md](./includes/getControlType-description.md)]

## <a name="syntax"></a>Sintaxis

`quickViewControl.getControlType();`

## <a name="return-value"></a>Valor devuelto

**Tipo**: Cadena.

**Descripción**: para un control de vista rápida, el método devuelve "quickform". 

Para un control constituyente en un control de vista rápida, el método devuelve la categoría real del control. Para obtener más información sobre otros valores devueltos, consulte [getControlType](../controls/getControlType.md).

### <a name="related-topics"></a>Temas relacionados

[formContext.ui.quickForms](../formContext-ui-quickForms.md)