---
title: Identifique y corrija los problemas de los clientes con un portal | MicrosoftDocs
description: Aprenda a identificar y corregir los problemas de los clientes con un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: b361efd6a1f44485e9b7337e3e5b3a29c1a826d4
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976194"
---
# <a name="portal-checker"></a>Comprobador del portal

El comprobador de portal es una herramienta de diagnóstico de autoservicio que pueden usar los administradores del portal para identificar problemas comunes en su portal. El comprobador del portal ayuda a identificar problemas con el portal examinando los distintos parámetros de configuración y proporciona sugerencias sobre cómo corregirlos.

Al ejecutar el comprobador de portal, los resultados se muestran en la sección **resultados de diagnóstico** en formato de cuadrícula. La cuadrícula de resultados tiene las siguientes columnas:

- **Problema**: muestra el problema de nivel superior al que se enfrenta un cliente. por ejemplo, problema de rendimiento.
- **Categoría**: muestra el área de nivel superior en la que se pueden clasificar los problemas. por ejemplo, el aprovisionamiento, la actualización de la solución, etc.
- **Resultado**: muestra el estado del problema. por ejemplo, error, ADVERTENCIA, etc.

De forma predeterminada, la información de la cuadrícula se ordena por la columna de **resultados** en este orden: error, warning y pass.

> [!div class=mx-imgBorder]
> ![](../media/diagnostic-results.png "Resultados de diagnóstico") de resultados de diagnóstico

Puede expandir un problema para ver información detallada y pasos de mitigación. Si la mitigación requiere alguna acción, verá un botón que realizará la acción. También puede proporcionar comentarios sobre si la mitigación era útil.

> [!div class=mx-imgBorder]
> ![Expandir un problema en los resultados de diagnóstico](../media/diagnostic-results-issue-expand.png "expandir un problema en los resultados de diagnóstico")

Si es necesario, puede volver a ejecutar las comprobaciones de diagnóstico, que actualizarán los resultados con los datos actualizados.

> [!NOTE]
> Si el portal está desactivado o el filtrado de direcciones IP está habilitado, no se ejecutarán determinadas comprobaciones de diagnóstico en el portal.

Para obtener una lista de problemas comunes diagnosticados por la herramienta del comprobador del portal, consulte [problemas comunes del portal diagnosticados por el comprobador del portal y sus prácticas recomendadas](https://docs.microsoft.com/dynamics365/customer-engagement/portals/portal-faq).

Para ejecutar el comprobador de portal:

1.  Abra el [centro de administración de portales de PowerApps](admin-overview.md).

2.  Vaya a **ejecutar el comprobador de portal**.

    > [!div class=mx-imgBorder]
    > ![Ejecutar]el comprobador de portal(../media/run-diagnostics.png "Ejecutar")

3.  Seleccione **ejecutar el comprobador de portal**. La sesión de diagnóstico iniciará y recopilará datos sobre los problemas del cliente. Los resultados se muestran en la sección **resultados de diagnóstico** .

    > [!div class=mx-imgBorder]
    > ![](../media/diagnostic-results.png "Resultados de diagnóstico") de resultados de diagnóstico

4.  Para volver a ejecutar las comprobaciones de diagnóstico, seleccione **Actualizar resultados**.

    > [!div class=mx-imgBorder]
    > Actualizar resultados de ![diagnóstico](../media/diagnostic-results-refresh.png "Actualizar resultados de diagnóstico")
