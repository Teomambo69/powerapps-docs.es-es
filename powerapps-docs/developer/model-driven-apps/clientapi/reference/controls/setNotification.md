---
title: setNotification (referencia API de cliente) en aplicaciones basadas en modelo| Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 4d025f92-db16-440c-9f82-e40d71e09862
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="setnotification-client-api-reference"></a>setNotification (referencia de la API de cliente)



Muestra un mensaje de error para el control para indicar que los datos no son válidos. Cuando se usa este método, aparece un icono "X" rojo junto al control. En los clientes móviles de Dynamics 365, al tocar el icono se mostrará el mensaje. 

## <a name="control-types-supported"></a>Tipos de control admitidos

Todas

## <a name="syntax"></a>Sintaxis

`formContext.getControl(arg).setNotification(message,uniqueId);`

## <a name="parameters"></a>Parámetros

|Nombre | Tipo | Obligatoria | Descripción|
|--|--|--|--|
|mensaje |String |Sí|El mensaje para mostrar.| 
|uniqueId |String |No|El identificador que se usará para borrar este mensaje usando el método **clearNotification**.
| | |

## <a name="return-value"></a>Valor devuelto
**Tipo**: booleano 

**Descripción**: Indica si el método se realizó correctamente.

## <a name="remarks"></a>Comentarios

Establecer una notificación de error en un control impedirá que se guarde el formulario.

### <a name="related-topics"></a>Temas relacionados

[addNotification](addNotification.md)

[clearNotification](clearNotification.md)