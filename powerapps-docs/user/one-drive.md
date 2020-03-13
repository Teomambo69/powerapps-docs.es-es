---
title: Uso de vínculos de OneDrive para la Empresa | Microsoft Docs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 03/02/2020
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5cfbed161ca920db3ce474371aa435189dc12543
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79240014"
---
# <a name="use-onedrive-for-business"></a>Uso de OneDrive para la Empresa 

Cree y administre documentos privados desde las aplicaciones de Common Data Service usando OneDrive para la Empresa. Más información:  [¿Qué es OneDrive para la Empresa?](https://support.office.com/article/What-is-OneDrive-for-Business-187f90af-056f-47c0-9656-cc0ddca7fdc2)


Para poder usar OneNote para la Empresa, el administrador del sistema debe habilitarlo. Más información:

-   [Búsqueda de un administrador o una persona de soporte técnico](find-admin.md)  

-   [Habilitación de OneDrive para la Empresa](https://docs.microsoft.com/power-platform/admin/enable-onedrive-for-business)  


## <a name="the-first-time-you-view-your-documents"></a>Primera vez que se consultan los documentos  

1. Abra un registro y vaya a la vista **Cuadrícula asociada al documento**. Por ejemplo, abra un registro de contacto.

2.  En el registro abierto, seleccione la pestaña **Relacionados** y, después, **Documentos**.

     > [!div class="mx-imgBorder"]
     > ![Apertura de la pestaña Documentos en un registro ](media/onedrive_nav.png "Apertura de la pestaña Documentos en un registro")

3.  Seleccione **Ubicación del documento** > **OneDrive**.

     > [!div class="mx-imgBorder"]
     > ![Apertura de la pestaña Documentos y seleccionar OneDrive](media/onedrive_menu.png "Apertura de la pestaña Documentos y seleccionar OneDrive")

4. Después de habilitar OneDrive para la Empresa, verá el cuadro de diálogo que se indica a continuación cuando se dirija a la pestaña **Documentos** para ver documentos en Common Data Service y cargar un archivo a OneDrive, o bien cuando intente crear un documento o una carpeta nuevos.  

    > [!div class="mx-imgBorder"]
    > ![Cambio de la carpeta de OneDrive](media/setup_onedrive.png "Cambio de la carpeta de OneDrive")  

5. Seleccione **Cambiar ubicación de carpeta** para elegir una nueva ubicación en la que guardar los documentos de OneDrive, o seleccione **Continuar** para aceptar la ubicación predeterminada de la carpeta.

  
## <a name="view-existing-onedrive-documents"></a>Vista de documentos de OneDrive existentes 
 
1. Abra un registro y vaya a la vista **Cuadrícula asociada al documento**. Por ejemplo, abra un registro de contacto.

2. En el registro abierto, seleccione la pestaña **Relacionados** y, después, **Documentos**.
 
    > [!div class="mx-imgBorder"]
    > ![Apertura de la pestaña Documentos en un registro ](media/onedrive_nav.png "Apertura de la pestaña Documentos en un registro")
 
3. Seleccione **Ubicación del documento** para filtrar la lista de documentos.

    > [!div class="mx-imgBorder"]
    > ![Apertura de la ubicación del documento](media/onedrive_doc_location.png "Apertura de la ubicación del documento")

4.  Seleccione una ubicación tal como se describe en la tabla siguiente.  

   |    Ubicación del documento      |  Descripción                                   |
   |---------------------------|------------------------------------------------|
   |      OneDrive             | Documentos almacenados en OneDrive para la Empresa      |
   | Documentos en un sitio predeterminado | Documentos almacenados en el sitio de SharePoint predeterminado  |
   | Compartidos conmigo            | Documentos que otras personas han compartido con usted que están asociados a este registro<!--note from editor: Edit okay? I haven't seen an "app record" defined.-->    |
   |  Todas las ubicaciones            |     Todas las ubicaciones de documento asociadas a este registro     |

5. Después de seleccionar una ubicación, verá los documentos guardados ahí.

## <a name="create-a-new-document-and-save-it-to-onedrive"></a>Creación de un documento nuevo y guardado en OneDrive

1. Abra un registro y vaya a la vista **Cuadrícula asociada al documento**. Por ejemplo, abra un registro de contacto.

2. En el registro abierto, seleccione la pestaña **Relacionados** y, después, **Documentos**.
 
    > [!div class="mx-imgBorder"]
    > ![Apertura de la pestaña Documentos en un registro ](media/onedrive_nav.png "Apertura de la pestaña Documentos en un registro")

2. Seleccione **Ubicación del documento** y cámbiela a **OneDrive**.

3. Seleccione **Nuevo** y, después, elija un tipo de documento, como PowerPoint o Word. 

    > [!div class="mx-imgBorder"]
    > ![Creación de un documento](media/onedrive_new_doc.png "Creación de un documento")

4. Escriba un nombre para el documento y seleccione **Guardar**.  


## <a name="things-to-consider"></a>Aspectos que se deben tener en cuenta: 

Debe tener en cuenta lo siguiente en relación con OneDrive para la Empresa en Common Data Service:

- Las carpetas de almacenamiento de OneDrive se crean en el idioma actual del usuario de Common Data Service. Si el idioma cambia, las nuevas carpetas se crearán en el nuevo idioma. Las carpetas antiguas seguirán en el idioma anterior.  

- Es posible que se produzca un retraso entre el momento en el que se comparten documentos en OneDrive y el momento en el que estarán disponibles para los otros usuarios. 
