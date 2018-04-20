---
title: Creación de una base de datos de Common Data Service | Microsoft Docs
description: Cree una base de datos de Common Data Service.
services: powerapps
documentationcenter: na
author: manasmams
manager: kfend
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/21/2018
ms.author: manasma
ms.openlocfilehash: cc068fc475643ae68e74d22981679dd9b038eb83
ms.sourcegitcommit: d7ed5144f96d1ecc17084c30ed0e2ba3c6b03c26
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="create-a-common-data-service-database"></a>Crear una base de datos de Common Data Service
Puede crear una base de datos y aplicaciones usando Common Data Service como almacén de datos. Puede crear sus propias entidades personalizadas o usar las predefinidas. Para crear una base de datos, primero debe crear un entorno o estar asignado a un entorno existente como **Administrador de entorno**. Además, debe tener asignada la licencia adecuada. Para más información sobre la compra de un plan para utilizar Common Data Service, consulte la [información sobre los precios](pricing-billing-skus.md).

Existen varias maneras de crear una base de datos:

* En el Centro de administración de PowerApps
* En el panel **Entidades** de powerapps.com

## <a name="create-a-database-in-the-admin-center"></a>Crear una base de datos en el centro de administración
1. En el [centro de administración](https://admin.powerapps.com), en el panel de navegación izquierdo, haga clic en **Entornos**.
    
2. Seleccione el entorno en el que quiere crear la base de datos.
    
    ![](./media/create-database/environment-list-new.png)

3. En la pestaña **Detalles**, haga clic en **Crear una base de datos**. 
    
    ![](./media/create-database/Create-DB-From-Details.png)

4. Elija la moneda y el idioma para continuar con la creación de la base de datos. 
    
    ![](./media/create-database/DB-Choose-options.png)



## <a name="create-a-database-in-the-entities-pane-of-powerappscom"></a>Crear una base de datos en el panel Entidades de powerapps.com
1. En [powerapps.com](https://web.powerapps.com), expanda la sección **Datos** y pulse o haga clic en **Entidades** en el panel de navegación de la izquierda.

2. Haga clic en **Crear base de datos** para crear la base de datos.

    ![](./media/create-database/Create-DB-From-Entities.png)


## <a name="security-model-for-the-databases"></a>Modelo de seguridad para las bases de datos
Cuando se crea una base de datos, los usuarios que tienen asignados roles de entorno continuarán manteniendo esos privilegios.  
    A los usuarios con el rol **Administrador de entorno** se les asigna ahora el rol **Administrador del sistema**. Los usuarios con el rol **Creador de entorno** continuarán con el mismo rol.

Se pueden asignar usuarios adicionales a los roles predefinidos o incluso crear [roles personalizados][1]. Vea [Seguridad de base de datos](create-database.md) para obtener más detalles.

> [!NOTE]
> Al crear la base de datos, los grupos de seguridad asignados al rol Administrador de entorno o Creador de entorno ya no serán válidos. Actualmente, la asignación de permisos de base de datos no es compatible con el grupo de seguridad de AAD.


## <a name="license-and-security-permissions"></a>Licencia y permisos de seguridad
Para crear una base de datos, debe ser administrador en el entorno seleccionado y tener asignada la licencia correspondiente. En el entorno, puede configurar más permisos de seguridad para otros usuarios mediante la pestaña **Seguridad**. Para más información, consulte [Configurar seguridad de base de datos](database-security.md) y [Modelo de seguridad](https://docs.microsoft.c../maker/common-data-service/entity-reference/security-model).

## <a name="privacy-notice"></a>Aviso de privacidad
Con el modelo de datos común de Microsoft PowerApps, recopilamos y almacenamos los nombres de los campos y las entidades personalizadas en nuestros sistemas de diagnóstico.  Usamos esta información para mejorar el modelo de datos común para nuestros clientes. Los nombres de entidades y de campos creados nos servirán para comprender qué escenarios son habituales en toda la comunidad de Microsoft PowerApps y determinar las carencias en la cobertura de entidades estándar del servicio, por ejemplo, los esquemas relacionados con las organizaciones. Microsoft no accede a los datos de las tablas de base de datos asociadas a estas entidades ni los usa; tampoco los replica fuera de la región en que esté aprovisionada la base de datos. Sin embargo, tenga en cuenta que es posible que los nombres de campos y entidades personalizadas se repliquen entre regiones y se eliminen de acuerdo con nuestras directivas de retención de datos. Microsoft se compromete a respetar su privacidad, como se describe con más detalle en nuestro [Centro de confianza](https://www.microsoft.com/trustcenter/Privacy/default.aspx).


<!--Reference links in article-->
[1]: https://technet.microsoft.com/library/dn531130.aspx