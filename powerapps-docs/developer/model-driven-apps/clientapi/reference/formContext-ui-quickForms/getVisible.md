---
title: getVisible (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 72c7ec48-1d27-499c-b56c-b7a449a347b8
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getvisible-client-api-reference"></a>getVisible (referencia de la API de cliente)



[!INCLUDE[./includes/getVisible-description.md](./includes/getVisible-description.md)]

>[!NOTE]
>Si la **sección** o la **pestaña** que contiene este control no está visible, este método aún puede devolver **true**. Para asegurarse de que el control realmente sea visible; también debe comprobar la visibilidad de los elementos que contiene.

## <a name="syntax"></a>Sintaxis

`quickViewControl.getVisible();`

## <a name="return-value"></a>Valor devuelto

**Tipo**: Booleano.

**Descripción**: true si el control está visible; false de lo contrario.

### <a name="related-topics"></a>Temas relacionados

[setVisible](setVisible.md)

[formContext.ui.quickForms](../formContext-ui-quickForms.md)



