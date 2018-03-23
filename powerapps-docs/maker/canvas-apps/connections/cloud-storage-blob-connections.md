---
title: Introducción a la conexión de almacenamiento en la nube | Microsoft Docs
description: Consulte cómo conectarse a una cuenta de almacenamiento en la nube y cómo mostrar los datos de Excel en la aplicación
services: ''
suite: powerapps
documentationcenter: ''
author: archnair
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 07/12/2016
ms.author: archanan
ms.openlocfilehash: fbe6cf68dace0ae8924f1ec5dc12b1a1ec1cde25
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="connect-to-cloud-storage-from-powerapps"></a>Conectar al almacenamiento en la nube desde PowerApps
PowerApps ofrece varias conexiones de almacenamiento en la nube. Con cualquiera de estas conexiones, puede almacenar un archivo de Excel y usar la información almacenada en él en toda la aplicación. Estas conexiones incluyen las siguientes:  

| **Azure Blob** | **Box** | **Dropbox** | **Google Drive** | **OneDrive** | **OneDrive<br>para la Empresa** |
| --- | --- | --- | --- | --- | --- |
| ![Icono](./media/cloud-storage-blob-connections/blobicon.png) |![Icono API][boxicon] |![Icono API][dropboxicon] |![Icono API][googledriveicon] |![Icono API][onedriveicon] |![Icono API][onedriveforbusinessicon] |

[!INCLUDE [connection-requirements](../../../includes/connection-requirements.md)]

* Un archivo de Excel con datos [con formato de tabla](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-E81AA349-B006-4F8A-9806-5AF9DF0AC664):
  
  1. Abra el archivo de Excel y seleccione cualquier celda de los datos que desea utilizar.
  2. En la pestaña **Insertar**, seleccione **Tabla**.
  3. En el cuadro de diálogo **Guardar como tabla**, active la casilla **La tabla tiene encabezados** y seleccione **Aceptar**.
  4. Guarde los cambios.

## <a name="connect-to-the-cloud-storage-connection"></a>Conexión al almacenamiento en la nube
1. En [powerapps.com](https://web.powerapps.com), expanda **Administrar** y seleccione **Conexiones**:  
   
    ![Seleccionar Conexiones](./media/cloud-storage-blob-connections/connections.png)
2. Seleccione **Nueva conexión** y seleccione la conexión de almacenamiento en la nube. Por ejemplo, seleccione **OneDrive**.
3. Se le solicitará el nombre de usuario y la contraseña de la cuenta de almacenamiento en la nube. Escríbalos y seleccione **Iniciar sesión**:  
    ![Escribir el nombre de usuario y contraseña](./media/cloud-storage-blob-connections/signin.png)
   
    Cuando haya iniciado sesión, esta conexión estará lista para usarse en las aplicaciones.
4. En la aplicación, pulse o haga clic en **Orígenes de datos** en la pestaña **Vista** de la cinta de opciones. En el panel derecho, pulse o haga clic en **Agregar un origen de datos**, pulse o haga clic en la conexión de almacenamiento en la nube y, luego, elija la tabla de Excel.
5. Seleccione **Conectar**.
   
    La tabla aparece como un origen de datos:
   
    ![Seleccionar la tabla de Excel](./media/cloud-storage-blob-connections/selecttable.png)
   
    > [!NOTE]
> Recuerde que los datos de Excel deben tener formato de tabla.

## <a name="using-the-excel-data-in-your-app"></a>Usar los datos de Excel en la aplicación
1. En la pestaña **Insertar**, seleccione **Galería** y seleccione un control de la galería **Con texto**.
2. Establezca la propiedad **[Elementos](../controls/properties-core.md)** de la galería en la tabla de Excel. Por ejemplo, si la tabla de Excel se denomina **Tabla1**, vuelva a establecerla en Tabla1:  
   
    ![Propiedad Items](./media/cloud-storage-blob-connections/itemsproperty.png)  
   
    La galería se actualiza automáticamente con la información de la tabla de Excel.
3. En la galería, seleccione el segundo o tercer control **Etiqueta**. De manera predeterminada, se ve que la propiedad **Texto** de la segunda y tercera etiqueta se establece automáticamente en `ThisItem.something`. Estas etiquetas se pueden establecer en cualquier columna de la tabla.
   
    En el ejemplo siguiente, la segunda etiqueta se establece en `ThisItem.Name` y la tercera en `ThisItem.Notes`:  
   
    ![Segunda etiqueta](./media/cloud-storage-blob-connections/items-secondtextbox.png)  
   
    ![Tercera etiqueta](./media/cloud-storage-blob-connections/items-thirdtextbox.png)  
   
    Salida de ejemplo:  
    ![Segunda y tercera etiqueta](./media/cloud-storage-blob-connections/secondthirdtextboxes.png)
   
> [!NOTE]
> El primer cuadro es en realidad un control de imagen. Si no tiene ninguna imagen en la tabla de Excel, puede eliminar el control de imagen y agregar una etiqueta en su lugar. [Agregar y configurar controles](../add-configure-controls.md) es un buen recurso.

[Comprender las tablas y los registros](../working-with-tables.md) ofrece más detalles y algunos ejemplos.  

## <a name="sharing-your-app"></a>Uso compartido de la aplicación
Puede compartir [la aplicación](../share-app.md), [los recursos](../share-app-resources.md) como, por ejemplo, los conectores, y [los datos](../share-app-data.md) con otras personas de la organización.

Si desea compartir una carpeta de Dropbox, la carpeta compartida debe asociarse a la cuenta de Dropbox del usuario.

Hay [ciertas limitaciones](#sharing-excel-tables) con los conectores relacionados con archivos de Excel.

## <a name="known-limitations"></a>Limitaciones conocidas
Si aparece un mensaje de **tipo de datos no admitido** o **no tiene el formato de tabla** cuando intenta utilizar una conexión de Excel en la aplicación, [dé formato a los datos como tabla](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-E81AA349-B006-4F8A-9806-5AF9DF0AC664).

Si los datos de Excel incluyen una columna calculada, no podrá utilizarlo para crear la aplicación y no podrá agregar datos a una aplicación existente.

### <a name="sharing-excel-tables"></a>Uso compartido de tablas de Excel
Para compartir datos en un archivo de Excel:

* En OneDrive para la Empresa, comparta el archivo en sí.
* En OneDrive, comparta la carpeta que contiene el archivo y especifique las rutas de acceso al archivo, no las direcciones URL, para todos los soportes físicos.
* En Dropbox o Google Drive, comparta el archivo o la carpeta.

## <a name="helpful-links"></a>Vínculos útiles
Consulte todas las [conexiones disponibles](../connections-list.md).  
Aprenda a [agregar conexiones](../add-manage-connections.md) y [orígenes de datos](../add-data-connection.md) a sus aplicaciones.  
[Comprenda las tablas y los registros](../working-with-tables.md) con orígenes de datos tabulares.  
Algunos recursos de la galería adicionales incluyen la posibilidad de [mostrar una lista de elementos](../add-gallery.md) y de [mostrar texto e imágenes de una galería](../show-images-text-gallery-sort-filter.md).

<!--Icon references-->
[boxicon]: ./media/cloud-storage-blob-connections/boxicon.png
[dropboxicon]: ./media/cloud-storage-blob-connections/dropboxicon.png
[googledriveicon]: ./media/cloud-storage-blob-connections/googledriveicon.png
[onedriveicon]: ./media/cloud-storage-blob-connections/onedriveicon.png
[onedriveforbusinessicon]: ./media/cloud-storage-blob-connections/onedriveforbusinessicon.png
