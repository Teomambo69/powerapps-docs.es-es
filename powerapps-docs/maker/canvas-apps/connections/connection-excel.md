---
title: Introducción a la conexión de Excel | Microsoft Docs
description: Muestre y actualice datos en Excel almacenando el libro en una cuenta de almacenamiento en la nube y, después, conectándose a los datos desde la aplicación.
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 10/02/2016
ms.author: lanced
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 455ffff4813b457c2a439f2081c10418ace2e306
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74678727"
---
# <a name="connect-to-excel-from-powerapps"></a>Conexión a Excel desde PowerApps
![Excel](./media/connection-excel/excelicon.png)

Excel es una *variante* de una conexión. Para mostrar los datos de Excel en la aplicación:

1. [Dé formato a los datos de Excel como una tabla](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-E81AA349-B006-4F8A-9806-5AF9DF0AC664).
2. Almacene el archivo de Excel en una cuenta de almacenamiento en la nube, como Box, Dropbox, Google Drive, OneDrive o OneDrive para la Empresa.
3. [Conéctese a la cuenta de almacenamiento en la nube](../add-manage-connections.md) y, después, agregue la tabla de Excel como origen de datos.
4. Para mostrar esta información en la aplicación, [genere una aplicación automáticamente](../get-started-create-from-data.md) o agregue y configure, por ejemplo, un control **Galería**.

> [!NOTE]
> Al conectarse a la tabla de Excel desde Power Apps, se creará una columna denominada **\_PowerAppsId_** , con un identificador único para cada fila de la tabla de Excel.

[La introducción a la conexión de almacenamiento en la nube](cloud-storage-blob-connections.md) muestra cómo agregar la conexión, agregar una tabla de Excel como origen de datos y usar los datos de Excel en la aplicación.

Para más información sobre cómo conectarse a otros tipos de datos, consulte la [lista de conexiones para PowerApps](../connections-list.md).

### <a name="known-limitations"></a>Limitaciones conocidas
Para más información sobre cómo compartir datos de Excel en su organización, [repase estas limitaciones](cloud-storage-blob-connections.md#sharing-excel-tables).

