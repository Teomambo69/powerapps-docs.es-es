---
title: "Creación de una base de datos de Common Data Service | Microsoft Docs"
description: Cree una base de datos de Common Data Service.
services: powerapps
documentationcenter: na
author: nimakms
manager: kfend
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/06/2016
ms.author: kfend
ms.openlocfilehash: 892f434d54c723d8de4ad6e9a48ced05cf23b311
ms.sourcegitcommit: e827813cd898ca9a1046b5952ea5e32ce2989a65
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="create-a-common-data-service-database"></a>Crear una base de datos de Common Data Service
Puede crear una base de datos y aplicaciones usando Common Data Service como almacén de datos. Puede crear sus propias entidades personalizadas o usar las predefinidas. Para crear una base de datos, primero debe crear un entorno o estar asignado a un entorno existente como administrador. Además, debe tener asignada la licencia adecuada. Para más información sobre la compra de un plan para utilizar Common Data Service, consulte la [información sobre los precios](pricing-billing-skus.md).

Existen tres maneras de crear una base de datos:

* En el centro de administración
* En el panel **Inicio** de powerapps.com
* En el panel **Entidades** de powerapps.com

## <a name="create-a-database-in-the-admin-center"></a>Crear una base de datos en el centro de administración
1. En el [centro de administración](https://admin.powerapps.com), en el panel de navegación izquierdo, haga clic en **Entornos**.
2. Seleccione el entorno o cree uno, si es necesario.
3. En la pestaña **Base de datos**, haga clic en **Crear una base de datos**. De forma predeterminada, se crea la base de datos en modo de acceso abierto.
4. Si desea aplicar la seguridad, seleccione **Restringir acceso**.

## <a name="create-a-database-in-the-home-pane-of-powerappscom"></a>Crear una base de datos en el panel Inicio de powerapps.com
1. En [powerapps.com](https://web.powerapps.com), en el panel de navegación izquierdo, haga clic en **Inicio**.
2. En la sección **Usar Microsoft Common Data Service**, busque el botón que se denomina **Crear base de datos** o **Comenzar**. El nombre del botón depende de la licencia y los permisos asignados. Es posible que no se le permita crear una base de datos en el entorno actual.

### <a name="create-database-in-current-environnmet"></a>Crear base de datos en el entorno actual
1. Haga clic en **Crear base de datos**.
2. En el cuadro de diálogo, active la casilla **Restringir acceso** si desea aplicar la seguridad.
3. Haga clic en **Crear mi base de datos**.

### <a name="get-started-by-creating-a-new-environment"></a>Comenzar creando un entorno
1. Haga clic en **Comenzar**.
2. En el cuadro de diálogo, haga clic en **Crear nuevo entorno** para empezar a crear un entorno y una base de datos.
3. En el campo **Nombre del entorno**, escriba un nombre único. En el campo **Región**, seleccione la región adecuada.
4. Active la casilla **Restringir acceso** si desea aplicar la seguridad.
5. Haga clic en **Crear**.

## <a name="create-a-database-in-the-entities-pane-of-powerappscom"></a>Crear una base de datos en el panel Entidades de powerapps.com
1. En [powerapps.com](https://web.powerapps.com), expanda la sección **Common Data Service** y pulse o haga clic en **Entidades** en el panel de navegación izquierdo.
2. Haga clic en **Comenzar**. Se crea la base de datos en modo de acceso abierto.

## <a name="open-and-restricted-databases"></a>Bases de datos abiertas y restringidas
De forma predeterminada, una base de datos se crea en modo de acceso abierto. En este modo, no se aplica la seguridad de acceso a las entidades. El administrador del entorno puede establecer la base de datos en el modo Restringir acceso. En este modo, se aplica la seguridad de acceso a las entidades, en función de los conjuntos de permisos y los roles.

1. En el [centro de administración](https://admin.powerapps.com), en el panel de navegación izquierdo, haga clic en **Entornos**.
2. Seleccione el entorno.
3. En la pestaña **Base de datos**, siga uno de estos pasos:
   * Para aplicar la seguridad, seleccione **Restringir acceso**.
   * Para deshabilitar la seguridad, seleccione **Open access** (Acceso abierto).

## <a name="license-and-security-permissions"></a>Licencia y permisos de seguridad
Para crear una base de datos, debe ser administrador en el entorno seleccionado y tener asignada la licencia correspondiente. En el entorno, puede configurar más permisos de seguridad para otros usuarios mediante la pestaña **Seguridad**. Para más información, consulte [Configurar seguridad de base de datos](database-security.md) y [Modelo de seguridad](https://docs.microsoft.com/common-data-service/entity-reference/security-model).

## <a name="privacy-notice"></a>Aviso de privacidad
Con el modelo de datos común de Microsoft PowerApps, recopilamos y almacenamos los nombres de los campos y las entidades personalizadas en nuestros sistemas de diagnóstico.  Usamos esta información para mejorar el modelo de datos común para nuestros clientes. Los nombres de entidades y de campos creados nos servirán para comprender qué escenarios son habituales en toda la comunidad de Microsoft PowerApps y determinar las carencias en la cobertura de entidades estándar del servicio, por ejemplo, los esquemas relacionados con las organizaciones. Microsoft no accede a los datos de las tablas de base de datos asociadas a estas entidades ni los usa; tampoco los replica fuera de la región en que esté aprovisionada la base de datos. Sin embargo, tenga en cuenta que es posible que los nombres de campos y entidades personalizadas se repliquen entre regiones y se eliminen de acuerdo con nuestras directivas de retención de datos. Microsoft se compromete a respetar su privacidad, como se describe con más detalle en nuestro [Centro de confianza](https://www.microsoft.com/trustcenter/Privacy/default.aspx).

