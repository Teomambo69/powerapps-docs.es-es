---
title: Colaborar con SharePoint | Microsoft Docs
description: Aprenda a colaborar con SharePoint dentro de una aplicación controlada por modelos
documentationcenter: ''
author: Mattp123
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 11/20/2019
ms.author: matp
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 428291712f91e90cea515723a93e1871ec94de2e
ms.sourcegitcommit: 8f32eed48adf4b24b9ca607bbf6db3d19749c46f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/23/2019
ms.locfileid: "74418290"
---
# <a name="collaborate-using-sharepoint"></a>Colaboración con SharePoint 

Administrar tipos de documentos comunes, como Word, Excel y PowerPoint, y crear carpetas para guardar y administrar los documentos que se almacenan sin problemas en SharePoint desde una aplicación controlada por modelos. 

> [!NOTE]
> Esta característica requiere que el administrador del sistema haya habilitado la administración de documentos de SharePoint. Más información: [Administración de documentos mediante SharePoint](/power-platform/admin/manage-documents-using-sharepoint)

En el caso de los registros de cuenta y contacto, se crea automáticamente una carpeta de ubicación del documento predeterminada en SharePoint la primera vez que se visita la pestaña **archivos** . Para otros registros de entidad estándar o personalizado, vaya a la pestaña **documentos** > **relacionados** . El nombre de la ubicación del documento tiene este formato: < record_name > _ < record_id >.

De forma predeterminada, la ubicación se establece en documentos en el sitio predeterminado 1.

## <a name="add-a-document"></a>Agregar un documento
1.  Abra un registro de cuenta o de contacto y seleccione la pestaña **archivos** . Para otras entidades estándar o personalizadas habilitadas para la administración de documentos, seleccione la pestaña **relacionado** y, a continuación, seleccione **documentos**.
2.  Elija una de las siguientes opciones. 
    - Para crear un nuevo documento, seleccione **nuevo**, seleccione el tipo de documento que desee, como Word, Excel o OneNote, y escriba un nombre. Seleccione **Guardar**. El documento en blanco se abre en una nueva pestaña. 
    - Para agregar un documento existente, seleccione **cargar**, seleccione **elegir archivo**, busque y seleccione el archivo que desee y, a continuación, seleccione **abrir**. Seleccione **Aceptar**. 

El archivo de documento aparece en la vista de **cuadrícula asociada del documento** . 

> [!div class="mx-imgBorder"] 
> ![](media/add-doc-sharepoint.png "Add document to SharePoint")

El documento también aparece en la ubicación de la carpeta del sitio de SharePoint. 

> [!div class="mx-imgBorder"] 
> ![](media/doc-on-sharepoint.png "Document on SharePoint")

## <a name="manage-sharepoint-locations"></a>Administrar ubicaciones de SharePoint
Puede crear nuevas ubicaciones de SharePoint o editarlas desde una aplicación controlada por modelos.

1. En la lista **archivos** de la barra de comandos, seleccione **abrir ubicación**y, a continuación, seleccione la ubicación.
2. Para editar la ubicación, en la barra de comandos, seleccione Editar <location name>de **Ubicación** .
Aparece el cuadro de diálogo **Editar ubicación** .
3. El nombre para mostrar, el sitio primario y el nombre de carpeta se rellenan automáticamente. Escriba los detalles sobre la nueva ubicación y, a continuación, seleccione **Guardar**.
4. Para agregar una ubicación, en la barra de comandos, seleccione **Agregar ubicación**.
5. Aparece el cuadro de diálogo **Agregar ubicación** .

    > [!div class="mx-imgBorder"] 
    > ![](media/add-location-dialog-box.png "Add location dialog box")
6. El nombre para mostrar, el sitio primario y el nombre de carpeta se rellenan automáticamente. Cambie los detalles si es necesario y, a continuación, seleccione **Guardar**.

## <a name="actions-on-documents"></a>Acciones en documentos
Al seleccionar uno o varios documentos en la lista documentos, puede realizar las siguientes acciones comunes de SharePoint en los documentos:
- Edit
- Eliminar
- Facturar
- Consulta
- Descartar desproteger
- Editar propiedades

## <a name="files-tab-faq"></a>Preguntas más frecuentes sobre la pestaña archivos
*¿Por qué se ha migrado la ubicación para acceder a los documentos?* 
- Hemos cambiado el comando para que los documentos sean más fáciles de encontrar con menos clics.

*¿La pestaña documentos desaparece?*
- No, no ha desaparecido. Los usuarios aún pueden tener acceso a los documentos asociados al registro en cuestión de la manera antigua, simplemente haciendo clic en el menú relacionado y, a continuación, en el vínculo documentos.

*Con el cambio, ¿se crearán automáticamente subcarpetas en SharePoint?*
- Sí. El comportamiento es similar al del vínculo **documentos** en el menú **relacionado** . Cuando un usuario selecciona la pestaña **archivos** por primera vez, el sistema crea la subcarpeta de SharePoint correspondiente. 

*¿Hay alguna manera de agregar la pestaña archivos a otras entidades o quitarla?*
- Sí. Para agregar o quitar la pestaña archivo, siga los pasos de este artículo. [Agregar la pestaña documentos de SharePoint al formulario principal de una entidad](../maker/model-driven-apps/add-documents-tab-entity-main-form.md)  

*¿Dónde puedo enviar mis comentarios sobre este cambio?*
- Puede enviar sus comentarios al equipo de integración de Dynamics 365 sales y Teams en esta dirección de correo electrónico: d365_ot_crew@microsoft.com

### <a name="see-also"></a>Vea también
[Integración de SharePoint, OneNote y OneDrive con Common Data Service](../maker/common-data-service/sharepoint-onedrive-onenote-intro.md)