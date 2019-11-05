---
title: Creación de un portal en un entorno que contenga aplicaciones controladas por modelos en Dynamics 365 | Microsoft Docs
description: Instrucciones para crear un portal en un entorno que contenga aplicaciones controladas por modelos en Dynamics 365.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 50459f3fcd9ebe8894196f934c1b1d2275c490c4
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542630"
---
# <a name="create-a-portal-in-an-environment-containing-model-driven-apps-in-dynamics-365"></a>Creación de un portal en un entorno que contenga aplicaciones controladas por modelos en Dynamics 365

Si selecciona un entorno que contiene aplicaciones controladas por modelos en Dynamics 365 (como Dynamics 365 sales y Dynamics 365 Customer Service), puede crear los portales que se mencionan en [las plantillas del portal](portal-templates.md).

1.  Inicie sesión en [PowerApps](https://make.powerapps.com).

2.  Seleccione **crear** en el panel izquierdo y escriba **portal** en el campo **plantillas de búsqueda** para mostrar todas las plantillas de Dynamics 365 portal.

    > [!div class=mx-imgBorder]
    > ![Plantillas del portal de Dynamics 365](media/dynamics-portals.png "Plantillas del portal de Dynamics 365")  

3.  Seleccione la plantilla de portal requerida.

4.  En la ventana crear portal, escriba un nombre para el portal y la dirección del sitio web y seleccione un idioma en la lista desplegable. Cuando haya terminado, seleccione **crear**. El proceso de creación es el mismo que se describe en la sección [creación de un portal de inicio de Common Data Service](create-portal.md) .

> [!NOTE]
> - Si ha adquirido un complemento de portal anterior y desea aprovisionar un portal mediante el complemento, debe ir a la página del centro de administración de **Dynamics 365** . Más información: [aprovisionamiento de un portal mediante el complemento de portal anterior](provision-portal-add-on.md)
> - Si ha aprovisionado un portal mediante el complemento de portal anterior, puede personalizarlo y administrarlo desde [make.powerapps.com](https://make.powerapps.com).
> - El aprovisionamiento de portales desde [make.powerapps.com](https://make.powerapps.com) no usa los complementos más antiguos del portal. Además, estos portales no aparecen en la pestaña **aplicaciones** de la página **centro de administración de Dynamics 365** .
> - No se puede crear un portal de inicio de Common Data Service desde la página del **centro de administración de Dynamics 365** .
> - Para deshabilitar la creación del portal en un inquilino, consulte [deshabilitar la creación del portal en un inquilino](create-portal.md#disable-portal-creation-in-a-tenant).

