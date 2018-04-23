---
title: Inicio rápido para crear un entorno | Microsoft Docs
description: En este inicio rápido, obtendrá información sobre cómo crear un entorno
services: powerapps
suite: powerapps
documentationcenter: na
author: skjerland
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
ms.openlocfilehash: a9138c636d70ea4701cbf685c3d7c7965c0e8469
ms.sourcegitcommit: aa2d0166dccb38100183c093f293233b46f3669d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2018
---
# <a name="quickstart-create-an-environment"></a>Inicio rápido: Creación de un entorno
Un entorno es un espacio para almacenar, administrar y compartir los datos empresariales, las aplicaciones y los flujos de la organización. También sirve como contenedor para separar aplicaciones que pueden tener otros roles, requisitos de seguridad o públicos de destino. PowerApps crea automáticamente un único entorno predeterminado para cada inquilino, que se comparte entre todos los usuarios de ese inquilino.

Cada entorno puede tener una o ninguna base de datos de Common Data Service, lo que proporciona almacenamiento para las aplicaciones. Cuando los usuarios crean una aplicación en un entorno, esa aplicación se puede conectar a cualquier origen de datos, incluidas las conexiones, las puertas de enlace y los flujos. Pero solo se permite que la aplicación se conecte a las bases de datos de Common Data Service en ese mismo entorno. La forma elegida para aprovechar los entornos depende de la organización y de las aplicaciones que se intentan compilar. Para más información, consulte [Environments overview](environments-overview.md) (Información general de los entornos).

En este tutorial, obtendrá información sobre cómo crear un entorno y una base de datos para ese entorno.

## <a name="prerequisites"></a>Requisitos previos
 Para seguir este tutorial rápido, se requieren los elementos siguientes:
 * Licencia de Plan 2 de PowerApps o Plan 2 de Microsoft Flow. Como alternativa, se puede suscribir a una [evaluación gratuita del Plan 2 de PowerApps](https://web.powerapps.com/signup?redirect=marketing&email=).
 * Los permisos Administrador de entorno de PowerApps, Administrador global de Office 365 o Administrador de inquilinos de Azure Active Directory. Para obtener más información, vea [Administración de entornos en PowerApps](environments-administration.md).

## <a name="sign-in-to-the-powerapps-admin-center"></a>Iniciar sesión en el Centro de administración de PowerApps
Inicie sesión en el Centro de administración en [https://admin.powerapps.com]([https://admin.powerapps.com).

## <a name="create-an-environment-and-database"></a>Crear un entorno y una base de datos
1. En el panel de navegación, pulse o haga clic en **Entornos** y, después, en **Nuevo entorno**.

    ![Archivo y Compartir](./media/create-environment/new-environment.png)
2. En el cuadro de diálogo **Nuevo entorno**, escriba un nombre para el entorno y, después, seleccione una región y tipo de entorno en las listas desplegables. El valor predeterminado de la región es la región principal Inquilino de Azure Active Directory, pero se puede seleccionar cualquier región en la lista desplegable. No se puede cambiar la región una vez creado el entorno. Cuando haya terminado, pulse o haga clic en **Crear entorno**.

    ![Archivo y Compartir](./media/create-environment/new-environment-dialog.png)
3. Una vez creado el entorno, recibirá un mensaje de confirmación en el cuadro de diálogo y se le pedirá que cree una base de datos. Pulse o haga clic en **Crear base de datos** para habilitar el acceso a Common Data Service.

    **Nota:** En la actualidad, solo se puede crear una base de datos en la región principal Inquilino de Azure Active Directory.

    ![Archivo y Compartir](./media/create-environment/create-database-dialog.png)
4. Seleccione la moneda y el idioma de los datos almacenados en la base de datos. No se puede cambiar la moneda ni el lenguaje una vez creada la base de datos. Cuando haya terminado, pulse o haga clic en **Crear base de datos**.

    ![Archivo y Compartir](./media/create-environment/create-database-dialog2.png)

    Se pueden tardar varios minutos en crear la base de datos en Common Data Service. Una vez creada la base de datos, el nuevo entorno aparece en la lista de entornos de la página **Entornos**.

    ![Archivo y Compartir](./media/create-environment/new-environment-created.png)

    Pulse o haga clic en el entorno para ver los detalles.

## <a name="next-steps"></a>Pasos siguientes
En este tutorial, ha obtenido información sobre cómo crear un entorno y una base de datos para ese entorno. A continuación, obtendrá información cómo administrar los entornos de la organización.

> [!div class="nextstepaction"]
> [Administración de entornos en PowerApps](environments-administration.md)
