---
title: Orígenes de datos delegables | Microsoft Docs
description: Lista de todos los orígenes de datos delegables admitidos
documentationcenter: na
author: archnair
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: canvas
ms.date: 08/15/2017
ms.author: archanan
ms.openlocfilehash: 87f1895801ec7d1121b042d6baf097b79801f019
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="delegable-data-sources"></a>Orígenes de datos delegables
Tal como se describe en detalle en el artículo [Descripción de delegación](delegation-overview.md), la delegación se produce cuando PowerApps delega el procesamiento de datos en el origen de datos en lugar de mover datos a la aplicación para procesarlos localmente.

Solo se admite la delegación para los orígenes de datos tabulares. En esta lista se identifican los orígenes de datos tabulares y si son compatibles con la delegación, con detalles en la sección siguiente.

* Common Data Service: **sí**
* SharePoint: **sí**
* SQL Server: **sí**
* Dynamics 365: **sí**
* Salesforce: **sí**
* Dynamics 365 for Operations: todavía no
* Dynamics 365 for Financials: todavía no
* Dynamics NAV: todavía no
* Hojas de cálculo de Google: todavía no

Se agregan continuamente más orígenes de datos tabulares y compatibilidad con la delegación para ellos.

En este documento se describe el estado actual de la delegación admitida para cada origen de datos.

## <a name="prerequisites"></a>Requisitos previos

* Familiarícese con el artículo [Descripción de delegación](delegation-overview.md).

## <a name="list-of-data-sources-and-supported-delegation"></a>Lista de orígenes de datos y delegación admitida
Esta lista de orígenes de datos, y funciones y predicados delegables se actualizará periódicamente para reflejar el estado actual de la compatibilidad con la delegación en PowerApps.

### <a name="top-level-delegable-functions"></a>Funciones delegables de nivel superior
| &nbsp; | Common Data Service | SharePoint | SQL Server | Dynamics 365 | Salesforce |
| --- | --- | --- | --- | --- | --- |
| Average |No |No |Sí |No |No |
| Filtro |Sí |Sí |Sí |Sí |Sí |
| Buscar |Sí |Sí |Sí |Sí |Sí |
| Máx. |No |No |Sí |No |No |
| Min |No |No |Sí |No |No |
| Search |Sí<sup>1</sup> |No |Sí |Sí |Sí |
| Ordenar |Sí |Sí |Sí |Sí |Sí |
| SortByColumns |Sí |Sí |Sí |Sí |Sí |
| Suma |No |No |Sí |No |No |

<sup>1</sup>Solo para campos de cadena

### <a name="filter-and-lookup-delegable-predicates"></a>Predicados delegables de Filtrar y Buscar
| &nbsp; | Common Data Service | SharePoint | SQL Server | Dynamics 365 | Salesforce |
| --- | --- | --- | --- | --- | --- |
| No |Sí |No |Sí |Sí |Sí |
| EsBlanco |No |No |Sí |Sí |No |
| TrimEnds |No |No |Sí |No |No |
| Largo |No |No |Sí |No |No |
| +, - |No |No |Sí |No |No |
| <, <=, =, <>, >, >= |Sí |Sí (solo =) |Sí |Sí |Sí |
| Y (&&), O (&#124;&#124;), No (!) |Sí<sup>2</sup> |Sí (excepto No (!)) |Sí |Sí |Sí |
| in |No |No |Sí |No |Sí |
| StartsWith |No |Sí |No |No |No |

<sup>2</sup>Solo para operadores. Función Y/O/No no delegada.
