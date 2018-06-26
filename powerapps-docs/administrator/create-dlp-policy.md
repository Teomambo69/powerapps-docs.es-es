---
title: Inicio rápido para crear una directiva de prevención de pérdida de datos (DLP) | Microsoft Docs
description: En este inicio rápido, obtendrá información sobre cómo crear una directiva de prevención de pérdida de datos (DLP) en PowerApps
author: jimholtz
ms.service: powerapps
ms.component: pa-admin
ms.topic: quickstart
ms.date: 03/30/2018
ms.author: jimh
ms.openlocfilehash: da4be42ea0374d6cb50da2f9a9b17eef15d5b316
ms.sourcegitcommit: 91a102426f1bc37504142cc756884f3670da5110
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "34552378"
---
# <a name="quickstart-create-a-data-loss-prevention-dlp-policy"></a>Inicio rápido: Creación de una directiva de prevención de pérdida de datos (DLP)
Para proteger los datos de la organización, PowerApps permite crear y aplicar directivas que definen con qué conectores de consumidor se pueden compartir datos empresariales específicos. Estas directivas que definen cómo se pueden compartir los datos se conocen como directivas de prevención de pérdida de datos (DLP). Las directivas DLP garantizan que los datos se administran de manera uniforme en toda la organización e impiden que los datos empresariales importantes se publiquen accidentalmente a conectores como sitios de redes sociales.

En este inicio rápido, obtendrá información sobre cómo crear una directiva DLP para un único entorno que impida que los datos que se almacenan en Common Data Service y las bases de datos de SharePoint se publiquen en Twitter.

## <a name="prerequisites"></a>Requisitos previos
Para seguir este inicio rápido, se requiere **uno** de los elementos siguientes:
* Permisos de administrador de inquilinos de Azure Active Directory
* Permisos de administrador global de Office 365
* Permisos de administrador de entorno de PowerApps, así como una licencia de Plan 2 de PowerApps o Plan 2 de Microsoft Flow, o bien una licencia de prueba de [Plan 2 de PowerApps](https://web.powerapps.com/signup?redirect=marketing&email=)

Para obtener más información, vea [Administración de entornos en PowerApps](environments-administration.md).

## <a name="sign-in-to-the-powerapps-admin-center"></a>Iniciar sesión en el Centro de administración de PowerApps
Inicie sesión en el Centro de administración en [https://admin.powerapps.com]([https://admin.powerapps.com).

## <a name="create-a-dlp-policy"></a>Crear una directiva DLP
1. En el panel de navegación, pulse o haga clic en **Directivas de datos** y, después, en **Nueva directiva**.

    ![](./media/create-dlp-policy/new-data-policy.png)
2. El campo **Nombre de la directiva de datos** se rellena automáticamente con un nombre basado en la hora y la fecha de creación de la directiva. Reemplace esta información con **Acceso de datos seguro para Contoso**.

    ![](./media/create-dlp-policy/policy-name.png)
3. Las opciones de la pestaña **Entornos** varían según si es un administrador de entorno o de inquilino. Si es un administrador de entorno, seleccione un entorno de la lista desplegable y, después, pulse la opción **Continuar** o haga clic en ella.

    ![](./media/create-dlp-policy/select-environment.png)

    Si es un administrador de inquilinos, puede crear directivas DLP que se apliquen a uno o más entornos, o bien a todos los entornos del inquilino, incluidos aquellos creados con una licencia de prueba. Para este inicio rápido, haga clic en la opción **Aplicar SOLO a los entornos seleccionados** o tóquela, seleccione un entorno de la lista desplegable y, después, haga clic en la opción **Continuar** o tóquela.

    ![](./media/create-dlp-policy/select-environment-tenant.png)

    Tenga en cuenta que las directivas DLP de entorno no pueden reemplazar las directivas DLP de inquilino.
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
En este inicio rápido, ha obtenido información sobre cómo crear una directiva DLP para un único entorno para impedir que los datos empresariales importantes se publiquen accidentalmente en conectores como Twitter. Para obtener más información sobre las directivas DLP, vea el artículo sobre cómo administrarlas.

> [!div class="nextstepaction"]
> [Administración de directivas de prevención de pérdida de datos (DLP)](prevent-data-loss.md)
