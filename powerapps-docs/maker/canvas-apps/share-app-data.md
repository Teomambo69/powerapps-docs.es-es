---
title: Uso compartido de archivos de Excel usados por una aplicación | Microsoft Docs
description: Compartir archivos de Excel en Dropbox, OneDrive y Google Drive. Los usuarios pueden editar ver archivos y carpetas.
author: jamesol-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/16/2016
ms.author: jamesol
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 65a828d33add99bbee086f24c3a4892abfaae048
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61536960"
---
# <a name="share-excel-data-used-by-your-app"></a>Compartir datos de Excel utilizados por la aplicación
Puede compartir datos de Excel con los usuarios de la aplicación en una [cuenta en la nube](connections/cloud-storage-blob-connections.md), como OneDrive.

Por ejemplo, podría crear una aplicación que mostrara los nombres y números de teléfono del grupo de soporte técnico de su empresa. La información se almacena en una hoja de cálculo de Excel, que coloca en una carpeta de Dropbox. A continuación, comparta la carpeta con los usuarios de aplicación para que puedan ver los nombres y números de teléfono.

Debe compartir los datos para que los usuarios puedan ejecutar e incluso modificar la aplicación. Los usuarios que no tengan permisos de uso compartido no verán los datos en el archivo de Excel.

En este tema se muestra cómo compartir datos en una hoja de cálculo de Excel con Dropbox, OneDrive y Google Drive. Para crear una aplicación que muestre los datos desde un archivo de Excel, consulte [Crear una aplicación desde un conjunto de datos](get-started-create-from-data.md).

## <a name="share-data-in-dropbox"></a>Compartir datos en Dropbox
1. Inicie sesión en Dropbox con la misma cuenta que usó para crear una conexión desde PowerApps en Dropbox.
2. Seleccione la carpeta que contiene el archivo de Excel y, a continuación, seleccione **Compartir**:  
   
    ![Comando Compartir](./media/share-app-data/dropbox-share.png)
3. En el cuadro de diálogo, escriba las direcciones de correo electrónico con las que los usuarios de la aplicación inician sesión en Dropbox.  
   
    ![Compartir en Dropbox](./media/share-app-data/dropbox-perms.png)
4. Si los usuarios de la aplicación van a agregar, modificar o eliminar datos en la aplicación, seleccione **Puede editar**. En caso contrario, seleccione **Puede ver**.
5. Seleccione **Compartir**.

Para obtener más información, consulte [Uso compartido de carpetas en Dropbox](https://www.dropbox.com/en/help/19).

## <a name="share-data-in-onedrive"></a>Compartir datos en OneDrive
1. Inicie sesión en OneDrive con la misma cuenta que usó para crear una conexión desde PowerApps en OneDrive.
2. Seleccione la carpeta que contiene el archivo y, a continuación, seleccione **Compartir**:  
   
    ![Comando Compartir](./media/share-app-data/onedrive-share.png)
   
    > [!NOTE]
   > En OneDrive para la Empresa, comparta el archivo en sí, no la carpeta que lo contiene.
3. En el cuadro de diálogo, seleccione **Correo electrónico**.
   
    ![Compartir por correo electrónico](./media/share-app-data/onedrive-email.png)
4. Especifique las direcciones de correo electrónico con las que los usuarios de la aplicación inician sesión en OneDrive y, a continuación, seleccione **Compartir**.  
   
    ![Especificar un usuario](./media/share-app-data/onedrive-perms.png)

Para obtener más información, consulte [Compartir archivos y carpetas de OneDrive](https://support.office.com/article/Share-OneDrive-files-and-folders-and-change-permissions-9fcc2f7d-de0c-4cec-93b0-a82024800c07).

## <a name="share-data-in-google-drive"></a>Compartir datos en Google Drive
1. Inicie sesión en Google Drive con la misma cuenta con la que creó una conexión desde PowerApps en Google Drive.
2. Haga clic con el botón derecho en la carpeta que contiene el archivo de Excel y, a continuación, seleccione **Compartir**.  
   
    ![Comando Compartir](./media/share-app-data/googledrive-share.png)
3. En el cuadro de diálogo, escriba las direcciones de correo electrónico con las que los usuarios de la aplicación inician sesión en Google Drive:  
   
    ![Especificar un usuario](./media/share-app-data/googledrive-perms.png)
4. Si los usuarios de la aplicación van a agregar, modificar o eliminar datos en la aplicación y, a continuación, seleccione **Puede editar** en la lista de permisos. En caso contrario, seleccione **Puede ver**.
5. Seleccione **Listo**.

Para obtener más información, consulte [Compartir archivos y carpetas de Google Drive](https://support.google.com/drive/answer/2494822).

### <a name="known-limitations"></a>Limitaciones conocidas
Para más información sobre cómo compartir datos de Excel en su organización, [repase estas limitaciones](connections/cloud-storage-blob-connections.md#known-limitations).

