---
title: Crear un portal en un entorno que contiene aplicaciones basadas en modelo en Dynamics 365 | Microsoft Docs
description: Instrucciones para crear un portal en un entorno que contiene aplicaciones basadas en modelo en Dynamics 365.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 896f6cfe9fabf08606e69b68b9957835a0147aee
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "2873417"
---
# <a name="create-a-portal-in-an-environment-containing-model-driven-apps-in-dynamics-365"></a>Crear un portal en un entorno que contiene aplicaciones basadas en modelo en Dynamics 365

Si selecciona un entorno que contiene aplicaciones basadas en modelo en Dynamics 365 (como Dynamics 365 Sales y Dynamics 365 Customer Service), puede crear los portales mencionados en [Plantillas de portal](portal-templates.md).

1.  Inicie sesión en [Power Apps](https://make.powerapps.com).

2.  Seleccione **Crear** en el panel izquierdo e introduzca **portal** en el campo **Plantillas de búsqueda** para mostrar todas las plantillas de portales de Dynamics 365.

    > [!div class=mx-imgBorder]
    > ![Plantillas de portales de Dynamics 365](media/dynamics-portals.png "Plantillas de portales de Dynamics 365")  

3.  Seleccione la plantilla de portal necesaria.

4.  En la ventana de creación del portal, escriba un nombre para el portal y la dirección de la página web, y seleccione un idioma de la lista desplegable. Cuando esté listo, seleccione **Crear**. El proceso de creación es el mismo que se describe en la sección [Creación de un portal de inicio de Common Data Service](create-portal.md).

> [!NOTE]
> - Si ha adquirido un complemento de portal más antiguo, y desea para aprovisionar un portal con el complemento, debe ir a la página **Centro de administración de Dynamics 365**. Más información: [Aprovisionar un portal con el complemento de portal más antiguo](provision-portal-add-on.md)
> - Si ha suministrado un portal con el complemento de portal más antiguo, puede seguir personalizándolo y administrándolo desde [make.powerapps.com](https://make.powerapps.com).
> - Aprovisionar portales desde [make.powerapps.com](https://make.powerapps.com) no consume los complementos de portal más antiguos. Además, estos portales no se muestran en la pestaña **Aplicaciones** en la página **Centro de administración de Dynamics 365**.
> - Un portal de inicio de Common Data Service no se puede crear desde la página **Centro de administración de Dynamics 365**.
> - Para deshabilitar la creación de portales en un inquilino, consulte [Deshabilitar creación de portales en un inquilino](create-portal.md#disable-portal-creation-in-a-tenant).
> - Cuando crea un portal, se instalan algunas soluciones y se importan datos de muestra.

