---
title: Introducción al comprobador de AppSource | Microsoft Docs
description: Aprender a usar el comprobador de AppSource
services: ''
suite: powerapps
documentationcenter: na
author: nkrb
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.reviewer: pehecke
ms.workload: na
ms.date: 04/07/2020
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5a0cd90c78b0654ded91d13761b228f4a6f4ba34
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2020
ms.locfileid: "3275772"
---
# <a name="appsource-checker"></a>Comprobador de AppSource

[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Puedes usar el comprobador de AppSource para comprobar si su aplicación cumple con los criterios de certificación antes de enviarla a [AppSource](https://appsource.microsoft.com/). El comprobador le indica si su archivo de solución tiene errores que hay que corregir y comprueba si se cumplen los criterios de certificación de AppSource. 

En ISV Studio, puede cargar un [paquete](/powerapps/developer/common-data-service/package-deployer/create-packages-package-deployer) completo o soluciones. Se le notificará si es necesario solucionar algún problema.

**Para ejecutar el comprobador de AppSource**

1. En ISV Studio, seleccione **Comprobador de AppSource** en el panel de la izquierda y, a continuación, seleccione **Validar la aplicación**.

    > [!div class="mx-imgBorder"]
    > ![Comprobador de AppSource](media/appsource-checker.png "Comprobador de AppSource")

2. Seleccione **Examinar** para cargar un archivo de solución desde su equipo local y, a continuación, seleccione **Ejecutar comprobación**.
   
   > [!div class="mx-imgBorder"]
   > ![Comando Ejecutar comprobación](media/appsource-browse-solution-files.png "Comando Ejecutar comprobación")
 
   > [!NOTE]
   > Si cargó previamente una solución para su validación, verá un historial de envíos en lugar de la captura de pantalla anterior.

3. Una vez completada la comprobación de validación, se muestra un resumen de los resultados con el número de problemas detectados (si los hubiera). Haga doble clic para seleccionar el archivo de solución y ver los detalles de los problemas.

   > [!div class="mx-imgBorder"]
   > ![Resumen de los resultados del comprobador de AppSource](media/appsource-results-page.png "Resumen de los resultados del comprobador de AppSource")

4. Si el envío no tiene errores, verá el siguiente mensaje:
 
   > [!div class="mx-imgBorder"]
   > ![Mensaje de éxito del comprobador de AppSource](media/appsource-no-error-page.png "Mensaje de éxito del comprobador de AppSource")
   
Ahora puede descargar el informe de validación de su aplicación e incluirlo en su envío a AppSource. 

### <a name="see-also"></a>Vea también

[Página principal](isv-app-management-homepage.md)<br/>
[Página de aplicación](isv-app-management-apppage.md)<br/>
[Página de inquilino](isv-app-management-tenantpage.md)<br/>
[Certificación de conector](isv-app-management-certification.md)

