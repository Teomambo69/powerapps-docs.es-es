---
title: Identificar y corregir problemas de clientes con un portal | MicrosoftDocs
description: Aprenda a identificar y corregir problemas de clientes con un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: f2ef5f1f8f5cfd7eb7c81d1b8fba3c1c19736a10
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "2862552"
---
# <a name="portal-checker"></a>Comprobador del portal

El comprobador de portal es una herramienta de diagnóstico de autoservicio que se puede usar por los administradores de portal para identificar los problemas comunes del portal. El comprobador del portal ayuda a identificar problemas con el portal viendo diferentes parámetros de configuración y proporciona sugerencias sobre cómo corregirlos.

Al ejecutar el comprobador del portal, los resultados se muestran en la sección **Resultados de diagnóstico** en un formato de cuadrícula. La cuadrícula de resultados tiene las siguientes columnas:

- **Error**: Muestra el problema de nivel superior que tiene el cliente; por ejemplo, degradación de rendimiento.
- **Categoría**: Muestra el área de nivel superior donde los problemas se pueden dividir en categorías; por ejemplo, aprovisionar, actualización de una solución, etc.
- **Resultado**: Muestra el estado de problema; por ejemplo, error, advertencia, etc.

De forma predeterminada, la información de la cuadrícula se ordenará por la columna **Resultado** en este orden: error, advertencia, y paso.

> [!div class=mx-imgBorder]
> ![Resultados del diagnóstico](../media/diagnostic-results.png "Resultados del diagnóstico")

Puede expandir un problema para ver la información detallada y los pasos de mitigación. Si la mitigación requiere alguna acción, verá un botón que realizará la acción. También puede proporcionar comentarios sobre si la mitigación es útil.

> [!div class=mx-imgBorder]
> ![Expandir un problema en los resultados de diagnóstico](../media/diagnostic-results-issue-expand.png "Expandir un problema en los resultados de diagnóstico")

Si procede, puede volver a ejecutar las pruebas de diagnóstico, que actualizarán los resultados con datos actualizados.

> [!NOTE]
> Si se desactiva el portal o se habilita el filtrado de direcciones IP, algunas pruebas de diagnóstico no se ejecutarán en el portal.

Para obtener una lista de problemas comunes diagnosticados por la herramienta de comprobación del portal, consulte [Problemas comunes del portal diagnosticados por el comprobador del portal y sus prácticas recomendadas](https://docs.microsoft.com/dynamics365/customer-engagement/portals/portal-faq).

Para ejecutar el comprobador del portal:

1.  Abra [Centro de administración de Portales de Power Apps](admin-overview.md).

2.  Vaya a **Ejecutar comprobador del portal**.

    > [!div class=mx-imgBorder]
    > ![Ejecutar comprobador del portal](../media/run-diagnostics.png "Ejecutar comprobador del portal")

3.  Seleccione **Ejecutar comprobador del portal**. La sesión de diagnóstico se iniciará y recopilará datos acerca de los problemas de los clientes. Los resultados se muestran en la sección **Resultados de diagnóstico**.

    > [!div class=mx-imgBorder]
    > ![Resultados del diagnóstico](../media/diagnostic-results.png "Resultados del diagnóstico")

4.  Para volver a ejecutar las pruebas de diagnóstico, seleccione **Resultados de la actualización**.

    > [!div class=mx-imgBorder]
    > ![Actualizar resultados del diagnóstico](../media/diagnostic-results-refresh.png "Actualizar resultados del diagnóstico")
