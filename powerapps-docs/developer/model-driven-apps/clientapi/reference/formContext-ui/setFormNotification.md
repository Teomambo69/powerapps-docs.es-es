---
title: setFormNotification (referencia API de cliente) en aplicaciones basadas en modelo| Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 48749e32-8490-4c8f-917c-3f1f8b9c028b
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="setformnotification-client-api-reference"></a>setFormNotification (referencia de la API de cliente)



[!INCLUDE[./includes/setFormNotification-description.md](./includes/setFormNotification-description.md)]

Puede mostrar cualquier número de notificaciones y se mostrarán hasta que se quiten mediante [clearFormNotification](clearFormNotification.md). El alto del área de notificación está limitado por lo que cada nuevo mensaje se agregará al principio. Los usuarios pueden desplazarse hacia abajo para ver mensajes más antiguos que aún no se han quitado.

## <a name="syntax"></a>Sintaxis

`formContext.ui.setFormNotification(message, level, uniqueId);`

## <a name="parameter"></a>Parámetro

|Nombre|Tipo|Obligatoria|Descripción|
|--|--|--|--|
|mensaje|String|Sí|El texto del mensaje.|
|level|String|Sí|El nivel del mensaje, que define cómo se mostrará. Especifique uno de los siguientes valores:<br>`ERROR` : Notificación usará el icono de error del sistema.<br/>`WARNING` : Notificación usará el icono de advertencia del sistema.<br/>`INFO` : Notificación usará el icono de información del sistema.|
|uniqueId|String|Sí|Identificador único para el mensaje que se puede usar después con [clearFormNotification](clearFormNotification.md) para quitar la notificación.|

## <a name="return-value"></a>Valor devuelto

**Tipo**: booleano

**Descripción**: True si el método tiene éxito, false de lo contrario. 


### <a name="related-topics"></a>Temas relacionados

[clearFormNotification](clearFormNotification.md)

[formContext.ui](../formContext-ui.md)

[formContext](../../clientapi-form-context.md)

