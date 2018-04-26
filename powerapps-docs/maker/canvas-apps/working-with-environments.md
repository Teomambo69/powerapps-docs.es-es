---
title: Uso de entornos | Microsoft Docs
description: Intercambie los entornos y comprenda cómo cambia el contenido de las páginas.
documentationcenter: na
author: linhtranms
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: canvas
ms.date: 10/14/2016
ms.author: litran
ms.openlocfilehash: fa1dcd264e99a2bea333d7b6aa0bbf2e04cd47e9
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="working-with-environments-and-microsoft-powerapps"></a>Trabajo con entornos y Microsoft PowerApps
Con PowerApps, puede trabajar en entornos diferentes y cambiar fácilmente entre ellos. Para obtener información general de los entornos, consulte [Environments overview](../../administrator/environments-overview.md) (Información general de los entornos), que explica en detalle por qué utilizar entornos y cómo puede crearlos y administrarlos. El ámbito de este artículo trata los siguientes temas sobre el entorno:

* Cómo cambiar el entorno en powerapps.com
* Cómo crear una aplicación en el entorno adecuado
* Cómo ver una aplicación en el entorno adecuado

## <a name="switch-the-environment"></a>Cambio de entorno
Cuando se registra y e inicia sesión por primera vez en powerapps.com, probablemente accederá al entorno predeterminado. Puede comprobarlo en la esquina superior derecha de la página.

![Entorno predeterminado](./media/working-with-environments/env-dropdown.png)

El *entorno predeterminado* es accesible a todos. Puede empezar a crear aplicaciones en este entorno y compartirlas con otros usuarios. También puede tener acceso a otros entornos, como aquellos que [ha creado usted mismo](../../administrator/environments-administration.md) o aquellos creados por otros usuarios, pero a los que tiene acceso. Para intercambiar los entornos, haga clic en la lista desplegable de entorno en la esquina superior derecha y seleccione otro entorno. En este ejemplo, se va a cambiar de *Entorno predeterminado* a *Entorno 1*.

![Cambio de entorno](./media/working-with-environments/switch-env.png)

Cuando cambie a un entorno diferente (por ejemplo, a Entorno 1), verá todas las aplicaciones que ha creado o a las que tiene acceso en este nuevo entorno.

## <a name="create-apps-in-the-right-environment"></a>Creación de aplicaciones en el entorno adecuado
Puede crear aplicaciones en entornos existentes a los que tiene acceso o en un entorno nuevo. Sin embargo, crear su propio entorno requiere un plan específico. Para más información, consulte [este tema](../../administrator/pricing-billing-skus.md). Antes de crear una aplicación, **asegúrese siempre de que selecciona el entorno en el que desea que se encuentre la aplicación**. De lo contrario, tendrá que tratar con el traslado de aplicaciones entre entornos.

1. Si se encuentra en [powerapps.com](http://web.powerapps.com), seleccione el entorno en el que desea crear la aplicación. Si se encuentra en *PowerApps Studio* o en *PowerApps Studio para web*, vaya al paso 4.

2. Seleccione **+ Nueva aplicación**.

3. Seleccione **Abrir PowerApps Studio** o **PowerApps Studio para web**.

4. Cuando se abre *PowerApps Studio* o *PowerApps Studio para web*, vuelva a seleccionar el entorno en la esquina superior derecha. Se mejorará esta experiencia en el futuro pero, en la versión actual, debe seleccionar esta opción cada vez que desee crear una aplicación en un entorno nuevo.

    ![Entorno de cambio de Studio](./media/working-with-environments/studio-switch-env.PNG)

5. En la página **Cuenta**, seleccione **Cambiar** junto al nombre del entorno actual.

    ![Entorno de cambio de Studio](./media/working-with-environments/studio-env-dropdown.PNG)

6. Seleccione el entorno en el que desea crear la aplicación.

    ![Entorno de cambio de Studio](./media/working-with-environments/studio-env-dropdown2.PNG)

7. Seleccione **Nuevo** para comenzar a crear una aplicación. La aplicación ahora reside en el entorno seleccionado en el paso 6.

    ![Entorno de cambio de Studio](./media/working-with-environments/new-app.PNG)

## <a name="view-apps-in-the-right-environment"></a>Visualización de aplicaciones en el entorno adecuado
Si está trabajando en [powerapps.com](http://web.powerapps.com), PowerApps Studio para Windows o PowerApps Studio para web, la lista de aplicaciones, conexiones, etc., que vea siempre se filtra según el entorno seleccionado en la lista desplegable. Si no ve las aplicaciones que está buscando, confirme siempre si se ha seleccionado el entorno adecuado.

De nuevo, para cambiar los entornos de [powerapps.com](http://web.powerapps.com):

![Cambio de entorno](./media/working-with-environments/switch-env.png)

Para cambiar los entornos en PowerApps Studio para Windows o PowerApps Studio para web:

![Entorno de cambio de Studio](./media/working-with-environments/studio-switch-env.PNG)

Para más información acerca de los entornos, consulte [esta información general](../../administrator/environments-overview.md).
