---
title: Creación de un entorno | Microsoft Docs
description: En este inicio rápido, obtendrá información sobre cómo crear un entorno
author: jimholtz
ms.service: powerapps
ms.component: pa-admin
ms.topic: quickstart
ms.date: 08/29/2018
ms.author: jimholtz
search.audienceType:
- admin
search.app:
- D365CE
- PowerApps
- Powerplatform
ms.openlocfilehash: 9d7a2093c938658d6717157fc6bd683aa3a55bb6
ms.sourcegitcommit: b8eee36e680036accb0e7d9fc7a434906af1c4d2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2018
ms.locfileid: "43297483"
---
# <a name="create-an-environment"></a>Creación de un entorno
Un entorno es un espacio para almacenar, administrar y compartir los datos empresariales, las aplicaciones y los flujos de la organización. También sirve como contenedor para separar aplicaciones que pueden tener otros roles, requisitos de seguridad o públicos de destino. PowerApps crea automáticamente un único entorno predeterminado para cada inquilino, que se comparte entre todos los usuarios de ese inquilino.

Cada entorno puede tener una o ninguna base de datos de Common Data Service, lo que proporciona almacenamiento para las aplicaciones. Cuando los usuarios crean una aplicación en un entorno, esa aplicación se puede conectar a cualquier origen de datos, incluidas las conexiones, las puertas de enlace y los flujos. Pero solo se permite que la aplicación se conecte a las bases de datos de Common Data Service en ese mismo entorno. La forma elegida para aprovechar los entornos depende de la organización y de las aplicaciones que se intentan compilar. Para más información, consulte [Environments overview](environments-overview.md) (Información general de los entornos).

En este tutorial, aprenderá a crear un entorno y una base de datos para el entorno.

## <a name="prerequisites"></a>Requisitos previos
 Para seguir este tema se requieren los elementos siguientes:
 * Licencia de Plan 2 de PowerApps o Plan 2 de Microsoft Flow. Como alternativa, se puede suscribir a una [evaluación gratuita del Plan 2 de PowerApps](https://web.powerapps.com/signup?redirect=marketing&email=).
 * Los permisos Administrador de entorno de PowerApps, Administrador global de Office 365 o Administrador de inquilinos de Azure Active Directory. Para obtener más información, vea [Administración de entornos en PowerApps](environments-administration.md).

## <a name="sign-in-to-the-powerapps-admin-center"></a>Iniciar sesión en el Centro de administración de PowerApps
Inicie sesión en el Centro de administración en [https://admin.powerapps.com](https://admin.powerapps.com).

## <a name="create-an-environment-and-database"></a>Crear un entorno y una base de datos
1. En el panel de navegación, pulse o haga clic en **Entornos** y, después, en **Nuevo entorno**.

    ![Archivo y Compartir](./media/create-environment/new-environment.png)
2. En el cuadro de diálogo **Nuevo entorno**, escriba un nombre para el entorno y, después, seleccione una región y tipo de entorno en las listas desplegables. El valor predeterminado de la región es la región principal Inquilino de Azure Active Directory, pero se puede seleccionar cualquier región en la lista desplegable. No se puede cambiar la región una vez creado el entorno. Cuando haya terminado, pulse o haga clic en **Crear entorno**.

    ![Archivo y Compartir](./media/create-environment/new-environment-dialog.png)

    Seleccione **Versión preliminar (Estados Unidos)** para obtener acceso anticipado a las próximas funcionalidades de PowerApps. Obtenga más información sobre el [programa de versión preliminar de PowerApps](preview-environments.md).
3. Una vez creado el entorno, recibirá un mensaje de confirmación en el cuadro de diálogo y se le pedirá que cree una base de datos. Pulse o haga clic en **Crear base de datos** para habilitar el acceso a Common Data Service.

    **Nota:** En la actualidad, solo se puede crear una base de datos en la región principal Inquilino de Azure Active Directory.

    ![Archivo y Compartir](./media/create-environment/create-database-dialog.png)
4. Seleccione la moneda y el idioma de los datos almacenados en la base de datos. No se puede cambiar la moneda ni el lenguaje una vez creada la base de datos. Cuando haya terminado, pulse o haga clic en **Crear base de datos**.

    ![Archivo y Compartir](./media/create-environment/create-database-dialog2.png)

    Se pueden tardar varios minutos en crear la base de datos en Common Data Service. Una vez creada la base de datos, el nuevo entorno aparece en la lista de entornos de la página **Entornos**.

    ![Archivo y Compartir](./media/create-environment/new-environment-created.png)

    Pulse o haga clic en el entorno para ver los detalles.

## <a name="next-steps"></a>Pasos siguientes
En este tema, ha aprendido a crear un entorno y una base de datos para ese entorno. A continuación, obtendrá información cómo administrar los entornos de la organización.

> [!div class="nextstepaction"]
> [Administración de entornos en PowerApps](environments-administration.md)
