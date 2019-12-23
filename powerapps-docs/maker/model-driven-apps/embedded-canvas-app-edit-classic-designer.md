---
title: Editar una aplicación de lienzo incrustada en un formulario basado en modelos | MicrosoftDocs
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
ms.openlocfilehash: 3c93c6696efc39e4f2354418ad1743fca3ebea95
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "2873065"
---
# <a name="edit-a-canvas-app-embedded-on-a-model-driven-form"></a>Editar una aplicación de lienzo incrustada en un formulario basado en modelos.
En este tema se explica cómo editar una aplicación de lienzo incrustada en un formulario basado en modelos.

## <a name="edit-the-canvas-app-directly"></a>Edición de la aplicación de lienzo directamente
Puede editar una aplicación de lienzo incrustada en un formulario basado en modelos igual que cualquier otra aplicación de lienzo. Para obtener pasos sobre cómo editar una aplicación de lienzo consulte: [Editar una aplicación de lienzo](../canvas-apps/edit-app.md)

## <a name="edit-the-canvas-app-via-the-host-model-driven-form"></a>Edición de la aplicación de lienzo mediante el formulario basado en modelos
Una opción alternativa es editar la aplicación de lienzo incrustada mediante el formulario basado en modelos.

Imagine que desee editar una aplicación de lienzo incrustada en un formulario llamado Formulario principal de cuenta para la entidad Cuentas. Para ello, siga estos pasos: 

1.  Inicie sesión en [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).
2.  [Edición del formulario](create-and-edit-forms.md) llamado Formulario principal de cuenta para la entidad Cuentas. 
3.  En la barra de comandos, seleccione **Cambiar a clásico** para abrir el formulario en el diseñador de formularios clásico.
4.  En el diseñador de formularios clásico, seleccione el campo que está personalizado para mostrar la aplicación de lienzo incrustada.
5.  Con este campo seleccionado, en la pestaña **Inicio**, en el grupo **Editar**, haga clic en **Cambiar propiedades**.
6.  En el cuadro de diálogo **Propiedades de campo** , seleccione la pestaña **Controles** .
7.  En el cuadro de diálogo **Propiedades de campo**, en la lista de controles seleccione **Aplicación de lienzo**.
8.  En la sección bajo la lista de controles, seleccione **Personalizar** para editar la aplicación de lienzo. Esto abre la aplicación de lienzo para editar, en Power Apps Studio, en una nueva pestaña.
       > [!NOTE]
       > Si abrir Power Apps Studio está bloqueado debido a un bloqueador de elementos emergentes de explorador web, debe habilitar el sitio de make.powerapps.com o temporalmente deshabilitar el bloqueador de elementos emergentes y después seleccionar **Personalizar** de nuevo.
9. Cuando finalice de hacer cambios, seleccione la pestaña **Archivo** y, a continuación seleccione **Guardar**.
10. Para que los cambios pasen a estar disponibles a los usuarios finales, seleccione **Publicar** y luego seleccione **Publicar esta versión**.

## <a name="see-also"></a>Vea también
[Insertar una aplicación de lienzo en un formulario controlado por modelos](embed-canvas-app-in-form.md) <br />
[Agregar una aplicación de lienzo incrustada en un formulario basado en modelos](embedded-canvas-app-add-classic-designer.md) <br />
[Personalizar el tamaño y orientación de la pantalla de una aplicación de lienzo insertada en un formulario basado en modelos](embedded-canvas-app-customize-screen.md) <br />
[Realice acciones predefinidas en el formulario de host desde una aplicación de lienzo insertada](embedded-canvas-app-actions.md) <br />
[Propiedades y acciones del control ModelDrivenFormIntegration](embedded-canvas-app-properties-actions.md) <br />
[Compartir una aplicación incrustada de lienzo](share-embedded-canvas-app.md) <br />
[Directrices acerca de cómo trabajar con aplicaciones de lienzo incrustadas](embedded-canvas-app-guidelines.md) <br />
[Migrar aplicaciones de lienzo insertadas en formularios basados en modelos creados mediante la versión de vista previa pública a la más reciente](embedded-canvas-app-migrate-from-preview.md) <br />
