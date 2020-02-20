---
title: Colaboración mediante SharePoint | Microsoft Docs
description: Aprenda a colaborar mediante SharePoint en una aplicación basada en modelo
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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/23/2019
ms.locfileid: "74418290"
---
# <a name="collaborate-using-sharepoint"></a>Colaboración con SharePoint 

Administre tipos de documentos comunes, como Word, Excel y PowerPoint, y cree carpetas para guardar y administrar esos documentos que se almacenan sin problemas en SharePoint desde una aplicación basada en modelo. 

> [!NOTE]
> Esta característica requiere que el administrador del sistema habilite la administración de documentos de SharePoint. Más información: [Administrar los documentos con SharePoint](/power-platform/admin/manage-documents-using-sharepoint)

En el caso de los registros de cuenta y contacto, se crea automáticamente una carpeta de ubicación de documentos predeterminada en SharePoint la primera vez que se va a la pestaña **Archivos**. En el caso de otros registros de entidad estándar o personalizada, vaya a la pestaña **Relacionados** > **Documentos**. El nombre de la ubicación de documentos tiene este formato: <nombre_registro>_<id._registro>.

De forma predeterminada, la ubicación se establece en Documentos en Sitio predeterminado 1.

## <a name="add-a-document"></a>Incorporación de un documento
1.  Abra un registro de cuenta o contacto y seleccione la pestaña **Archivos**. En el caso de otras entidades estándar o personalizadas habilitadas para la administración de documentos, seleccione la pestaña **Relacionados** y luego **Documentos**.
2.  Elija entre las siguientes opciones. 
    - Para crear un nuevo documento, seleccione **Nuevo**, seleccione el tipo de documento que quiere, como Word, Excel o OneNote, y escriba un nombre. Seleccione **Guardar**. El documento en blanco se abre en una nueva pestaña. 
    - Para agregar un documento existente, seleccione **Cargar**, **Elegir archivo**, busque y seleccione el archivo que quiere y seleccione **Abrir**. Seleccione **Aceptar**. 

El archivo del documento aparece en la vista **Cuadrícula asociada al documento**. 

> [!div class="mx-imgBorder"] 
> ![](media/add-doc-sharepoint.png "Add document to SharePoint")

El documento también aparece en la ubicación de la carpeta del sitio de SharePoint. 

> [!div class="mx-imgBorder"] 
> ![](media/doc-on-sharepoint.png "Document on SharePoint")

## <a name="manage-sharepoint-locations"></a>Administración de ubicaciones de SharePoint
Puede crear ubicaciones nuevas de SharePoint o editar las existentes desde una aplicación basada en modelo.

1. En la lista **Archivos** de la barra de comandos, seleccione **Abrir ubicación** y luego seleccione la ubicación.
2. Para editar la ubicación, en la barra de comandos, seleccione **Editar ubicación** <location name>.
Aparece el cuadro de diálogo **Editar ubicación**.
3. El nombre para mostrar, el sitio primario y el nombre de carpeta se rellenan automáticamente. Escriba los detalles sobre la nueva ubicación y seleccione **Guardar**.
4. Para agregar una ubicación, en la barra de comandos, seleccione **Agregar ubicación**.
5. Aparece el cuadro de diálogo **Agregar ubicación**.

    > [!div class="mx-imgBorder"] 
    > ![](media/add-location-dialog-box.png "Add location dialog box")
6. El nombre para mostrar, el sitio primario y el nombre de carpeta se rellenan automáticamente. Cambie los detalles si es necesario y seleccione **Guardar**.

## <a name="actions-on-documents"></a>Operaciones en documentos
Al seleccionar uno o más documentos de la lista Documentos, puede realizar estas otras operaciones comunes de SharePoint en ellos:
- Editar
- Eliminar
- Proteger
- Consulte
- Descartar la desprotección
- Modificar propiedades

## <a name="files-tab-faq"></a>Preguntas frecuentes sobre la pestaña Archivos
*¿Por qué se ha movido la ubicación para acceder a los documentos?* 
- Se ha movido el comando para que resulte más fácil encontrar los documentos con menos clics.

*¿La pestaña Documentos ha desaparecido?*
- No, no ha desaparecido. Los usuarios pueden seguir accediendo a los documentos asociados al registro en cuestión igual que antes, simplemente con hacer clic en el menú Relacionados y luego en el vínculo Documentos.

*Con el cambio, ¿las subcarpetas de SharePoint se siguen creando automáticamente?*
- Sí. El comportamiento es similar al del vínculo **Documentos** del menú **Relacionados**. Cuando un usuario selecciona la pestaña **Archivos** por primera vez, el sistema crea la subcarpeta de SharePoint correspondiente. 

*¿Hay alguna manera de agregar la pestaña Archivos a otras entidades o de quitarla?*
- Sí. Para agregar o quitar la pestaña Archivos, siga los pasos de este artículo. [Agregar la pestaña documentos de SharePoint al formulario principal de una entidad](../maker/model-driven-apps/add-documents-tab-entity-main-form.md)  

*¿A dónde puedo enviar comentarios sobre este cambio?*
- Puede enviar sus comentarios al equipo de Dynamics 365 Sales Office and Teams Integration a esta dirección de correo electrónico: d365_ot_crew@microsoft.com

### <a name="see-also"></a>Vea también
[Integración de SharePoint, OneNote y OneDrive con Common Data Service](../maker/common-data-service/sharepoint-onedrive-onenote-intro.md)