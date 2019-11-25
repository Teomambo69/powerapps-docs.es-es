---
title: Migrar aplicaciones de lienzo insertadas en formularios basados en modelos creados mediante la versión de vista previa pública | MicrosoftDocs
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
- PowerApps maker portal impact
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: e53f4b1cfd01225285fb50626aa9ace3b804d9c2
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2756940"
---
# <a name="migrate-embedded-canvas-apps-on-model-driven-forms-created-using-the-public-preview-release"></a>Migrar aplicaciones de lienzo insertadas en formularios basados en modelos creados mediante la versión de vista previa pública
> [!IMPORTANT]
> Con la versión más reciente, las aplicaciones de lienzo incrustadas en formularios basados en modelos están disponibles en general. Las aplicaciones de lienzo incrustadas en formularios basados en modelos mediante la versión de vista previa pública deben migrarse a nuevas aplicaciones incrustadas creadas mediante la última versión.
> Pronto dejará de prestarse soporte técnico para aplicaciones de lienzo insertadas en formularios basados en modelos creados mediante la versión de vista previa pública 

Para migrar aplicaciones de lienzo incrustadas en formularios basados en modelos mediante la versión de vista previa pública a la más reciente, los creadores primero deben crear una nueva aplicación de lienzo incrustada creada mediante la última versión. A continuación los creadores pueden copiar los controles desde la aplicación de lienzo incrustada existente a la nueva, agregar orígenes de datos requeridos y actualizar referencias rotas si las hay. A continuación se proporcionan los pasos detallados.

1. Inicie sesión en [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).
2. Abra la aplicación de lienzo incrustada creada con la versión de vista previa pública para editar en PowerApps Studio. Para obtener pasos sobre cómo editar una aplicación de lienzo consulte: [Editar una aplicación de lienzo](../canvas-apps/edit-app.md).
3. En una nueva pestaña del explorador, siga los pasos para [agregar una nueva aplicación de lienzo incrustada en un formulario basado en modelos](embedded-canvas-app-add-classic-designer.md).
4. Copie los controles de la aplicación de lienzo incrustada creada con la versión de vista previa pública a la nueva aplicación de lienzo incrustada, una sola pantalla cada vez mediante los pasos indicados a continuación.
    1. Seleccione la pestaña del explorador del paso 2, que tiene la aplicación de lienzo incrustada, creada con la versión de vista previa pública, abierta en PowerApps Studio.
    2. Seleccione una pantalla para copiar los controles.
    3. Use **Ctrl + A** para seleccionar todos los controles en la pantalla.
    4. Use **Ctrl + C** para copiar todos los controles seleccionados.
    5. Seleccione la pestaña del explorador del paso 3, que tiene la nueva aplicación de lienzo incrustada creada con la versión más reciente.
    6. Seleccionar una pantalla o agregue una nueva.
    7. Use **Ctrl + V** para pegar los controles en la pantalla seleccionada.
    8. Repita los pasos para copiar cada pantalla.
5. Cuando termine de copiar todas las pantallas, seleccione la pestaña del explorador del paso 3, que tiene la nueva aplicación de lienzo incrustada creada con la versión más reciente.
6. Actualice todos lugares donde se accede al registro del formulario basado en modelos host. Reemplace **First(ModelDrivenFormIntegration.Data)** con **ModelDrivenFormIntegration.Item**.
7. Agregue los orígenes de datos que faltan en la nueva aplicación de lienzo incrustada.
8. Actualice todas las referencias rotas en la nueva aplicación de lienzo incrustada. 
9. Cuando finalice de hacer cambios, seleccione la pestaña **Archivo** y, a continuación seleccione **Guardar**.
10. Para que los cambios pasen a estar disponibles a los usuarios finales, seleccione **Publicar** y luego seleccione **Publicar esta versión**.

## <a name="migrating-embedded-canvas-apps-on-model-driven-forms-that-use-a-list-of-records-related-to-the-current-main-form-record"></a>Migrar aplicaciones de lienzo insertadas en formularios basados en modelos que usan una lista de registros relacionados con el registro actual (formulario principal)

En la versión de vista previa, para insertar una aplicación de lienzo en un formulario basado en modelos, los creadores tenían que decidir con antelación si querían pasar el registro actual (formulario principal) como contexto de datos o una lista de registros relacionados con el registro actual (formulario principal). A continuación tenían que agregar el control de la aplicación de lienzo a un control de campo o de subcuadrícula.

Con la última versión, agregar una aplicación de lienzo incrustada en un formulario basado en modelos se ha simplificado y agilizado solo al campo. Los creadores pueden seguir accediendo fácilmente a la lista de registros relacionados directamente en la aplicación de lienzo mediante el conector Common Data Service. 

Para migrar una aplicación de lienzo insertada en un formulario basado en modelos que usa una lista de registros relacionados con el registro actual (formulario principal), siga estos pasos.

1. Siga los pasos de la sección anterior para migrar aplicaciones de lienzo incrustadas en formularios basados en modelos creadas mediante la versión de vista previa pública a la versión más reciente.
2. Mediante el conector Common Data Service, agregue un origen de datos para la entidad relacionada a la aplicación. Para obtener más información sobre cómo agregar un origen de datos en una aplicación de lienzo, consulte [Agregar una conexión de datos a una aplicación de lienzo en PowerApps](../canvas-apps/add-data-connection.md).
3. Cuando se usa el origen de datos de la entidad relacionada para un control como [Galería](../canvas-apps/controls/control-gallery.md) o [Tabla de datos](../canvas-apps/controls/control-data-table.md), use la función **[Filtro](../canvas-apps/functions/function-filter-lookup.md)** para filtrar los registros a los que están relacionados con el registro actual (formulario principal). El registro actual (formulario principal) está disponible mediante **ModelDrivenFormIntegration.Item**.
    > [!NOTE]
    > La aplicación de lienzo incrustada tiene acceso total al registro desde el formulario basado en modelos host mediante ModelDrivenFormIntegration.Item. Por ejemplo, para obtener el valor de un campo con el nombre **accountnumber** y el nombre para mostrar **Número de cuenta**, puede usar **ModelDrivenFormIntegration.Item.accountnumber** o **ModelDrivenFormIntegration.Item.'Número de cuenta'**.
4. Con las actualizaciones recientes Common Data Service ahora también ofrece soporte para usar vistas de entidad como filtro. Consulte esta entrada de blog para los detalles: [Selección mejorada de origen de datos y Common Data Service vistas](https://powerapps.microsoft.com/blog/improved-data-source-selection-and-common-data-service-views/). 

## <a name="see-also"></a>Vea también
[Insertar una aplicación de lienzo en un formulario controlado por modelos](embed-canvas-app-in-form.md) <br />
[Agregar una aplicación de lienzo incrustada en un formulario basado en modelos](embedded-canvas-app-add-classic-designer.md) <br />
[Editar una aplicación de lienzo incrustada en un formulario basado en modelos](embedded-canvas-app-edit-classic-designer.md) <br />
[Personalizar el tamaño y orientación de la pantalla de una aplicación de lienzo insertada en un formulario basado en modelos](embedded-canvas-app-customize-screen.md) <br />
[Realice acciones predefinidas en el formulario de host desde una aplicación de lienzo insertada](embedded-canvas-app-actions.md) <br />
[Propiedades y acciones del control ModelDrivenFormIntegration](embedded-canvas-app-properties-actions.md) <br />
[Compartir una aplicación incrustada de lienzo](share-embedded-canvas-app.md) <br />
[Directrices acerca de cómo trabajar con aplicaciones de lienzo incrustadas](embedded-canvas-app-guidelines.md) <br />
