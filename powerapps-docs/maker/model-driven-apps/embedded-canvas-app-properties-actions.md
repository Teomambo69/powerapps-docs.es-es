---
title: Propiedades y acciones del control ModelDrivenFormIntegration | MicrosoftDocs
ms.custom: ''
ms.date: 06/25/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
ms.assetid: 00e62904-2ce9-4730-a113-02b1fedbf22e
author: Aneesmsft
ms.author: matp
manager: kvivek
tags:
- Power Apps maker portal impact
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 674147425097d75b96e14bfbf76b3c937f9fd999
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "2868474"
---
# <a name="modeldrivenformintegration-control-properties-and-actions"></a>Propiedades y acciones del control ModelDrivenFormIntegration
Las aplicaciones de lienzo incrustadas en formularios basados en modelos incluyen un control especial llamado **ModelDrivenFormIntegration**. Este control es responsable de llevar datos contextuales del formulario controlado por modelos del host a la aplicación incrustada de lienzo.  

En este tema se explican las propiedades y acciones disponibles en el control de ModelDrivenFormIntegration.

| Propiedad o acción | Descripción |
|:--------------|:-------------------------|
|**DataSource** | Debe establecerse en el origen de datos conectado a la entidad principal del formulario basado en modelos host. <br />Establezca automáticamente cuando [incruste una nueva aplicación de lienzo](embedded-canvas-app-add-classic-designer.md). |
|**Elemento** | Propiedad de solo lectura que permite a la aplicación de lienzo incrustada acceder al registro desde el formulario basado en modelos host. <br />Por ejemplo, para obtener el valor de un campo con el nombre accountnumber y el nombre para mostrar Número de cuenta, puede usar ModelDrivenFormIntegration.Item.accountnumber o ModelDrivenFormIntegration.Item.'Número de cuenta'. |
|**OnDataRefresh** | La fórmula en esta propiedad se evalúa cuando el formulario basado en modelos host guarda datos. <br />Úsela para actualizar el origen de datos conectado a la entidad principal del formulario basado en modelos host y para realizar otras acciones como ajustar o actualizar variables. <br /> Por ejemplo, al establecerlo en la fórmula de abajo se actualizará el origen de datos Cuentas y se establecerá una variable llamada CurrentAccountNumber con el valor del campo Número de cuenta del registro actual. <br /> Refresh(Cuentas); Set(CurrentAccountNumber, ModelDrivenFormIntegration.Item.'Número de cuenta') |
|**RefreshForm** | Actualiza los datos en el formulario basado en modelos host. <br />Vea [Realizar acciones predefinidas en el formulario host](embedded-canvas-app-actions.md#refreshformshowprompt) para los detalles. |
|**SaveForm** | Guarda los datos en el formulario basado en modelos host. <br />Vea [Realizar acciones predefinidas en el formulario host](embedded-canvas-app-actions.md#saveform) para los detalles.  |
|**NavigateToMainForm** | Navega el formulario basado en modelos host a un formulario principal y muestra el registro especificado. <br />Vea [Realizar acciones predefinidas en el formulario host](embedded-canvas-app-actions.md#navigatetomainformentityname-mainformname-recordid) para los detalles. |
|**NavigateToView** | Navega el formulario basado en modelos host a una vista. <br />Vea [Realizar acciones predefinidas en el formulario host](embedded-canvas-app-actions.md#navigatetoviewentityname-viewname) para los detalles.  |
|**OpenQuickCreateForm** | Abre el formulario de creación rápida predeterminado para una entidad.  <br />Vea [Realizar acciones predefinidas en el formulario host](embedded-canvas-app-actions.md#openquickcreateformentityname) para los detalles.  |
|**Datos** | La propiedad de sólo lectura usada por el marco de trabajo para enviar algunos datos clave del formulario basado en modelos host a la aplicación de lienzo incrustada.  <br /> No use esta propiedad. Use el elemento para tener acceso al registro del formulario basado en modelos host.  |

## <a name="see-also"></a>Vea también
[Insertar una aplicación de lienzo en un formulario controlado por modelos](embed-canvas-app-in-form.md) <br />
[Agregar una aplicación de lienzo incrustada en un formulario basado en modelos](embedded-canvas-app-add-classic-designer.md) <br />
[Editar una aplicación de lienzo incrustada en un formulario basado en modelos](embedded-canvas-app-edit-classic-designer.md) <br />
[Personalizar el tamaño y orientación de la pantalla de una aplicación de lienzo insertada en un formulario basado en modelos](embedded-canvas-app-customize-screen.md) <br />
[Realice acciones predefinidas en el formulario de host desde una aplicación de lienzo insertada](embedded-canvas-app-actions.md) <br />
[Compartir una aplicación incrustada de lienzo](share-embedded-canvas-app.md) <br />
[Directrices acerca de cómo trabajar con aplicaciones de lienzo incrustadas](embedded-canvas-app-guidelines.md) <br />
[Migrar aplicaciones de lienzo insertadas en formularios basados en modelos creados mediante la versión de vista previa pública a la más reciente](embedded-canvas-app-migrate-from-preview.md) <br />
