---
title: Ver datos de la entidad en Power BI Desktop (vista previa) | MicrosoftDocs
description: Más información acerca de cómo ver los datos de entidad en Power BI Desktop
ms.custom: ''
ms.date: 05/01/2020
ms.reviewer: matp
ms.service: powerapps
author: Mattp123
ms.assetid: ''
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 446381f491fac0cb5d60c3945f5404983f1ed364
ms.sourcegitcommit: 0ede8e3bc795e151aa94ffcbce15cff7a949c57a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "3335426"
---
# <a name="view-entity-data-in-power-bi-desktop-preview"></a>Ver datos de entidad en Power BI Desktop (vista previa)

[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Puede usar Power BI Desktop para ver entidades en Common Data Service. Los datos de registro de entidad a los que puede obtener acceso desde su entorno son de solo lectura. El acceso a datos utiliza el modelo de seguridad de Common Data Service que es el mismo que se utiliza para obtener acceso a los datos de registro de entidad mediante una aplicación Power Apps.

> [!IMPORTANT]
> - Esta es una característica en vista previa y no está disponible en todas las regiones.
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)]

1.  Inicie sesión en [Power Apps](https://make.powerapps.com/) y luego seleccione el entorno adecuado en la esquina superior derecha.

2.  En el panel de navegación izquierdo, expanda **Datos**, seleccione **Entidades**y luego seleccione **Analizar en Power BI** en la barra de comandos.

    El archivo pbids para su entorno se descarga en la carpeta de descargas predeterminada de su navegador.
    
    > [!NOTE]
    > Si no tiene la opción **Analizar en Power BI** en su entorno de Power Apps, aún no tiene acceso a la característica de conexión de SQL.

3.  Abra el archivo .pbids para obtener acceso a él en Power BI Desktop. ¿No tiene Power BI Desktop? [Instálelo ahora](https://powerbi.microsoft.com/downloads/).

4.  El archivo pbids se carga en Power BI Desktop. En el cuadro de diálogo **Base de datos de SQL Server**, seleccione **Cuenta de Microsoft**, seleccione **Iniciar sesión** y luego introduzca sus credenciales en la ventana del navegador que aparece.

    > [!div class="mx-imgBorder"] 
    > ![](media/power-bi-environment-signin.png)

5.  En el cuadro de diálogo **Base de datos de SQL Server** en Power BI Desktop, seleccione **Conectar**.

    El entorno aparece en la ventana **Navegador**, Power BI Desktop. Amplíela para ver las tablas de entidades disponibles para analizar. Seleccione una entidad para ver sus datos.

    > [!div class="mx-imgBorder"] 
    > ![](media/entity-record-data-displayed.png)

> [!NOTE]
> No se admiten las opciones de SQL, como las consultas T-SQL.

Para obtener más información sobre Power BI Desktop, vea [Introducción a Power BI Desktop](/power-bi/desktop-getting-started)..

### <a name="see-also"></a>Vea también
[Usar SQL para consultar datos](../../developer/common-data-service/cds-sql-query.md)
