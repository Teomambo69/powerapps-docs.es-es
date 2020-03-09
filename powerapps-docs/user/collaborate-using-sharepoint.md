---
title: Colaboración mediante SharePoint | Microsoft Docs
description: Aprenda a colaborar mediante SharePoint en una aplicación basada en modelo
documentationcenter: ''
author: mduelae
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 03/02/2020
ms.author: matp
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3491468724662edcac932cf37345730defd6a006
ms.sourcegitcommit: 5b6e6b41a3fc4d7f1aea46ec66c086b784efacac
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/03/2020
ms.locfileid: "78236139"
---
# <a name="collaborate-using-sharepoint"></a>Colaboración con SharePoint 

Con Common Data Service, puede almacenar documentos en SharePoint y administrarlos desde su aplicación. Los documentos que cree en la aplicación se almacenarán en SharePoint y se sincronizarán automáticamente con sus dispositivos móviles y de escritorio.

Para poder usar SharePoint para almacenar documentos, el administrador del sistema debe habilitar la opción correspondiente. Más información:

-   [Búsqueda de un administrador o una persona de soporte técnico](find-admin.md)  

-   [Administrar los documentos con SharePoint](https://docs.microsoft.com/power-platform/admin/manage-documents-using-sharepoint)  

## <a name="where-do-you-access-the-documents-from"></a>¿Desde dónde se accede a los documentos?

1. Para los tipos de registro que son compatibles con la administración de documentos, abra el registro en cuestión, seleccione la pestaña **Relacionados** y, después, **Documentos**.

   > [!div class="mx-imgBorder"]
   > ![Apertura de la pestaña Documentos en un registro ](media/onedrive_nav.png "Apertura de la pestaña Documentos en un registro")

2. Seleccione **Ubicación del documento** > **Documentos en Ubicación predeterminada 1**. De forma predeterminada, cuando SharePoint está habilitado, la ubicación se establece en **Documentos en Ubicación predeterminada 1**.

   > [!div class="mx-imgBorder"]
   > ![Ubicación predeterminada](media/sharepoint_defualtsite.png "Ubicación predeterminada")


## <a name="create-a-new-document-and-save-it-to-sharepoint"></a>Creación de un documento nuevo y guardado en SharePoint

1. Abra un registro y vaya a la vista **Cuadrícula asociada al documento**. Por ejemplo, abra un registro de contacto.

2. En el registro abierto, seleccione la pestaña **Relacionados** y, después, **Documentos**.
 
    > [!div class="mx-imgBorder"]
    > ![Apertura de la pestaña Documentos en un registro](media/onedrive_nav.png "Apertura de la pestaña Documentos en un registro")

2. Seleccione **Ubicación del documento** y cambie la ubicación a **Documentos en Ubicación predeterminada 1**.

3. Seleccione **Nuevo** y, después, elija un tipo de documento, como Word, Excel o PowerPoint.

    > [!div class="mx-imgBorder"]
    > ![Creación de un documento](media/onedrive_new_doc.png "Creación de un documento")

4. Escriba un nombre para el documento y seleccione **Guardar**.  

## <a name="create-a-new-folder-in-the-default-sharepoint-site-location"></a>Creación de una carpeta nueva en la ubicación predeterminada del sitio de SharePoint

1. Abra un registro y vaya a la vista **Cuadrícula asociada al documento**. Por ejemplo, abra un registro de contacto.

2. En el registro abierto, seleccione la pestaña **Relacionados** y, después, **Documentos**.
 
    > [!div class="mx-imgBorder"]
    > ![Apertura de la pestaña Documentos en un registro](media/onedrive_nav.png "Apertura de la pestaña Documentos en un registro")

2. Seleccione **Ubicación del documento** y cambie la ubicación a **Documentos en Ubicación predeterminada 1**.

3. Seleccione **Nuevo** y elija **Carpeta**.

    > [!div class="mx-imgBorder"]
    > ![Creación de una carpeta](media/Sharepoint_new_folder.png "Crear una carpeta")
    
 4. Escriba un nombre para la carpeta y seleccione **Guardar**.  
 
 
 ## <a name="upload-an-existing-document-to-sharepoint-from-your-app"></a>Carga de un documento a SharePoint desde la aplicación

1. Vaya al registro para el que quiere crear un documento, seleccione la pestaña **Relacionados** y, después, **Documentos**.
 
2. Seleccione **Cargar**.

   > [!div class="mx-imgBorder"]
   > ![Carga de documentos](media/upload_doc.png "Cargar documentos")

3. Elija el archivo que quiera cargar. Solo puede elegir un archivo a la vez.

   El documento se creará en la ubicación en la que se encuentre.

   > [!Note]
   > Se pueden cargar archivos de hasta 50 MB. Si la conexión a Internet es lenta, es posible que se produzca un error al cargar archivos grandes.

4. Si hay archivos con el mismo nombre en SharePoint, seleccione si quiere sobrescribirlos.

5. Seleccione **Aceptar**.

## <a name="manage-sharepoint-locations"></a>Administración de ubicaciones de SharePoint

Puede crear ubicaciones de SharePoint nuevas o editar las existentes desde su aplicación en Common Data Service.

### <a name="edit-a-location"></a>Edición de una ubicación

1. Abra un registro, seleccione la pestaña **Relacionados** y, después, **Documentos**.

2. Seleccione **Editar ubicación** y, después, seleccione una ubicación para el sitio de SharePoint.

   Aparece el cuadro de diálogo **Editar ubicación**.

   > [!div class="mx-imgBorder"]
   > ![Editar ubicación](media/edit_location.png "Editar ubicación")

3. El nombre para mostrar, el sitio primario y el nombre de carpeta se rellenan automáticamente. Escriba los detalles sobre la nueva ubicación y seleccione **Guardar**.

### <a name="add-a-new-location"></a>Adición de una nueva ubicación

1. Abra un registro, seleccione la pestaña **Relacionados** y, después, **Documentos**.

2. Seleccione **Agregar ubicación**. 

   Aparece el cuadro de diálogo **Agregar ubicación**.

   > [!div class="mx-imgBorder"]
   > ![Agregar ubicación](media/add_location.png "Agregar ubicación")

3. El nombre para mostrar, el sitio primario y el nombre de carpeta se rellenan automáticamente. Cambie los detalles si es necesario y seleccione **Guardar**.

## <a name="files-tab-faq"></a>Preguntas frecuentes sobre la pestaña Archivos

*¿Por qué se ha movido la ubicación para acceder a los documentos?* 
- Se ha movido el comando para que resulte más fácil encontrar los documentos con menos clics.

*¿La pestaña Documentos ha desaparecido?*
- No, no ha desaparecido. Los usuarios pueden seguir accediendo a los documentos asociados al registro en cuestión igual que antes. Solo tienen que seleccionar el menú **Relacionados** y, después, el vínculo **Documentos**.

*Con el cambio, ¿las subcarpetas de SharePoint se siguen creando automáticamente?*
- Sí. El comportamiento es similar al del vínculo **Documentos** del menú **Relacionados**. Cuando un usuario selecciona la pestaña **Archivos** por primera vez, el sistema crea la subcarpeta de SharePoint correspondiente. 

*¿Hay alguna manera de agregar la pestaña Archivos a otras entidades o de quitarla?*
- Sí. Para agregar o quitar la pestaña **Archivos**, siga los pasos que se indican en este artículo: [Agregar la pestaña documentos de SharePoint al formulario principal de una entidad](../maker/model-driven-apps/add-documents-tab-entity-main-form.md)  
