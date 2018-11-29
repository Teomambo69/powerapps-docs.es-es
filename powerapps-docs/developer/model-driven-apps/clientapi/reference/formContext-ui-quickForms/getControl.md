---
title: getControl (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 57eb6b4b-90c1-4d56-b4b0-a7160af17f8f
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getcontrol-client-api-reference"></a>getControl (referencia de la API de cliente)



[!INCLUDE[./includes/getControl-description.md](./includes/getControl-description.md)]

## <a name="syntax"></a>Sintaxis

`quickViewControl.getControl(arg);`

## <a name="parameter"></a>Parámetro

**arg**: opcional. Puede obtener acceso a un único control en la colección de controles constituyentes pasando un argumento como nombre o valor de índice del control constituyente en un control de vista rápida. Por ejemplo, `quickViewControl.getControl("firstname")` o `quickViewControl.getControl(0)`


## <a name="return-value"></a>Valor devuelto

**Tipo**: objeto o colección de objetos.

**Descripción**: un objeto si usa el método con parámetros; una colección de objetos si usa el método sin parámetros.

## <a name="remarks"></a>Comentarios

Tras recuperar un control constituyente en un control de vista rápida, puede usar cualquiera de los métodos admitidos para un control de aplicaciones basadas en modelos en el control constituyente que no modifique los datos del control constituyente. Esto se debe a que los controles constituyentes en un control de vista rápida son de solo lectura. Por ejemplo, puede usar: 

`quickViewControl.getControl(0).getAttribute()` 

Para obtener más información sobre los métodos admitidos para un control, consulte [Controles](../controls.md).

>[!IMPORTANT]
>El método [getAttribute](../controls/getAttribute.md) o cualquier método relacionado con datos de un control constituyente puede no funcionar en el evento [OnLoad](../events/form-onload.md) del formulario principal porque el formulario de vista rápida que está enlazado puede no haberse cargado completamente cuando el formulario principal se cargó. Debe usar el método [isLoaded](isLoaded.md) para que la instancia de control de vista rápida le ayude a determinar si el formulario de vista rápida enlazado se ha cargado completamente. 

>Además, la forma en que recupera los controles constituyentes en un control de vista rápida de formularios utilizando el nuevo motor de representación de formularios es diferente de los formularios heredados. Por lo tanto, si está usando formularios heredados y tiene controles constituyentes que apuntan a código en un control de vista rápida, debe actualizar el código cuando decida usar el nuevo motor de representación de formularios.

### <a name="related-topics"></a>Temas relacionados

[formContext.ui.quickForms](../formContext-ui-quickForms.md)



