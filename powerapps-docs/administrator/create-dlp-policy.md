---
title: Inicio rápido para crear una directiva de prevención de pérdida de datos (DLP) | Microsoft Docs
description: En este inicio rápido, obtendrá información sobre cómo crear una directiva de prevención de pérdida de datos (DLP) en PowerApps
services: powerapps
suite: powerapps
documentationcenter: na
author: SKjerland
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: quickstart
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/21/2018
ms.author: sharik
ms.openlocfilehash: 651510bbe4ed71dbdb267ebee04e10ea13d36e15
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="quickstart-create-a-data-loss-prevention-dlp-policy"></a>Inicio rápido: Creación de una directiva de prevención de pérdida de datos (DLP)
Para proteger los datos de la organización, PowerApps permite crear y aplicar directivas que definen con qué conectores de consumidor se pueden compartir datos empresariales específicos. Estas directivas que definen cómo se pueden compartir los datos se conocen como directivas de prevención de pérdida de datos (DLP). Las directivas DLP garantizan que los datos se administran de manera uniforme en toda la organización e impiden que los datos empresariales importantes se publiquen accidentalmente a conectores como sitios de redes sociales.

En este inicio rápido, obtendrá información sobre cómo crear una directiva DLP que impida que los datos que se almacenan en Common Data Service y bases de datos de SharePoint se publiquen en Twitter.

## <a name="prerequisites"></a>Requisitos previos
Para seguir este tutorial rápido, se requieren los elementos siguientes:
* Plan 2 de PowerApps o Plan 2 de Flow. Como alternativa, se puede suscribir a una [evaluación gratuita del Plan 2 de PowerApps](https://web.powerapps.com/signup?redirect=marketing&email=).
* Los permisos Administrador de entorno de PowerApps o Administrador de inquilinos de Azure Active Directory, y permisos para al menos un entorno. Para obtener más información, vea [Administración de entornos en PowerApps](environments-administration.md).

## <a name="sign-in-to-the-powerapps-admin-center"></a>Iniciar sesión en el Centro de administración de PowerApps
Inicie sesión en el Centro de administración en [https://admin.powerapps.com]([https://admin.powerapps.com).

## <a name="create-a-dlp-policy"></a>Crear una directiva DLP
1. En el panel de navegación, pulse o haga clic en **Directivas de datos** y, después, en **Nueva directiva**.

    ![](./media/create-dlp-policy/new-data-policy.png)
2. Para el nombre de la directiva de datos, escriba **Acceso a datos seguro para Contoso**.
3. En la pestaña **Entornos**, seleccione un entorno de la lista desplegable y, después, pulse o haga clic en **Continuar**.

    ![](./media/create-dlp-policy/select-environment.png)
4. En la pestaña **Grupos de datos**, en **Business data only** (Solo datos empresariales), pulse o haga clic en **Agregar**.

    ![](./media/create-dlp-policy/data-groups.png)
5. En la ventana **Agregar conectores**, seleccione **Common Data Service** y **SharePoint** (tendrá que desplazarse hacia abajo o buscar para encontrarlos) y, después, pulse o haga clic en **Agregar conectores** para agregarlos al grupo de datos **Business data only** (Solo datos empresariales).

    ![](./media/create-dlp-policy/add-connectors.png)

    Los conectores solo pueden residir en un grupo de datos a la vez y de forma predeterminada se agregan al grupo **No business data allowed** (No se permiten datos empresariales). Al mover Common Data Service y SharePoint al grupo **Business data only** (Solo datos empresariales), se impide a los usuarios crear flujos y aplicaciones que combinen estos dos conectores con cualquiera de los conectores del grupo **No business data allowed** (No se permiten datos empresariales).
6. Haga clic en **Guardar directiva**.

    ![](./media/create-dlp-policy/save-policy.png)

Se crea la directiva Acceso a datos seguro para Contoso y aparece en la lista de directivas de prevención de pérdida de datos. Como el conector de Twitter reside en el grupo de datos **No business data allowed** (No se permiten datos empresariales), esta directiva garantiza que Common Data Service y SharePoint no comparten sus datos con Twitter.

Se recomienda que los administradores compartan una lista de directivas DLP con su organización para que los usuarios sean conscientes de las directivas antes de crear aplicaciones.

## <a name="next-steps"></a>Pasos siguientes
En este tutorial, ha obtenido información sobre cómo crear una directiva DLP para impedir que los datos empresariales importantes se publiquen accidentalmente en conectores como Twitter. Para obtener más información sobre las directivas DLP, vea el artículo sobre cómo administrarlas.

> [!div class="nextstepaction"]
> [Administración de directivas de prevención de pérdida de datos (DLP)](prevent-data-loss.md)
