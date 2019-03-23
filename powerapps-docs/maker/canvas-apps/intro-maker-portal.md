---
title: Inicio de sesión por primera vez | Microsoft Docs
description: Un nuevo lugar de encuentro para todos los creadores de aplicaciones.
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 08/06/2018
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 735894f8e28d25777aa7f66146f5782da2ab2f3e
ms.sourcegitcommit: 5b2b70c3fc7bcba5647d505a79276bbaad31c610
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2019
ms.locfileid: "58356802"
---
# <a name="sign-in-to-powerapps-for-the-first-time"></a>Inicio de sesión en PowerApps por primera vez

Cuando inicie sesión en [PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), el sitio ofrece diversas opciones para que cree sus propias aplicaciones, abra las aplicaciones que usted u otros usuarios hayan creado y realice tareas relacionadas. Estas tareas van desde las más sencillas, como la identificación de la licencia o licencias que le proporcionan acceso, hasta funcionalidades más avanzadas, como la creación de conexiones personalizadas para orígenes de datos específicos.

Puede seleccionar opciones en tres áreas generales:

- El encabezado de la parte superior de la página

    ![Encabezado](media/intro-maker-portal/header.png)

- La barra de navegación del borde izquierdo de la página

    ![Barra de navegación](media/intro-maker-portal/nav-bar.png)

- Los iconos grandes que aparecen en el centro de la página

    ![Área central de la página principal](media/intro-maker-portal/center-area.png)

Para obtener mejores resultados, asegúrese de que la página principal se establece en el entorno adecuado.

## <a name="choose-an-environment"></a>Selección de un entorno

Si va a crear una aplicación, un flujo, una conexión de datos o una entidad en común el servicio de datos, gran parte de lo que hacer en PowerApps se encuentra en un entorno específico. Los entornos crean límites entre distintos tipos de trabajo; por ejemplo, una organización podría tener entornos independientes para distintos departamentos. Muchas organizaciones usan entornos para separar aplicaciones que aún están en desarrollo de las que están listas para su uso generalizado. Puede que tenga acceso a varios entornos o solo a uno y, si cuenta con los permisos adecuados, tal vez pueda crear sus propios entornos.

Para comprobar en qué entorno se encuentra, busque el selector de entornos junto al margen derecho del encabezado.

![Selector de entornos](media/intro-maker-portal/environment-switcher.png)

Si crea una aplicación en un entorno, no podrá verla desde otro entorno. Además, las personas que quieran ejecutar la aplicación habrán de tener acceso al entorno en el que se creó.

> [!IMPORTANT]
> Asegúrese de que se encuentra en el entorno adecuado *antes* crear una aplicación, un flujo o un componente similar. No resulta fácil mover componentes de un entorno a otro.

Para más información, consulte [Environments overview](../../administrator/environments-overview.md) (Información general de los entornos).

## <a name="choose-an-app-type"></a>Elección de un tipo de aplicación

En PowerApps, puede crear y ejecutar estos tipos de aplicaciones:

- **Aplicaciones de lienzo**: admiten el diseño de interfaz de usuario personalizada y la conexión a datos desde diversos orígenes.
- **Las aplicaciones controladas por modelos** tiene una interfaz de usuario estándar y conectarse a datos solo en Common Data Service. Sin embargo, resulta más fácil crear otros elementos, tales como vistas, paneles y diferentes tipos de lógica de negocios.

Si elige un entorno que tiene una base de datos de Common Data Service, puede crear lienzo o controladas por modelos, las aplicaciones de la misma **inicio** página.

## <a name="play-or-edit-an-app"></a>Reproducción o edición de una aplicación

Si ha creado una aplicación, o bien otra persona ha creado una y la ha compartido con usted, la puede reproducir o editar en las páginas **Inicio** o **Aplicaciones**.

En la página **Aplicaciones**, puede filtrar la lista de aplicaciones por criterios tales como si se ha abierto recientemente.

![Lista de aplicaciones](./media/intro-maker-portal/find-apps.png)

También puede buscar una aplicación escribiendo uno o más caracteres en la barra de búsqueda que aparece cerca de la esquina superior derecha. Cuando encuentre la aplicación que quiera, seleccione el icono de banner para iniciar o modificar la aplicación.

## <a name="create-an-app"></a>Crear una aplicación

En la página **principal** se ofrecen varias formas de crear aplicaciones:

- [Generación automática de una aplicación de lienzo a partir de un conjunto de datos](data-platform-create-app.md)
- [Personalización de un ejemplo precompilado de una aplicación de lienzo](open-and-run-a-sample-app.md)
- [Compilación de una aplicación de lienzo a partir de una pantalla en blanco](data-platform-create-app-scratch.md)
- [Creación de su propia aplicación controlada por modelos](../model-driven-apps/overview-model-driven-samples.md)
- [Personalización de un ejemplo precompilado de una aplicación controlada por modelos](../model-driven-apps/build-first-model-driven-app.md)

## <a name="learn-more"></a>Más información

Hay dos formas de encontrar más información sobre las aplicaciones de lienzo o las aplicaciones controladas por modelos:

- En la barra de navegación izquierda, seleccione **Más información**.
- En el encabezado, seleccione el icono de signo de interrogación.

    ![Lista de aplicaciones controladas por modelos con un menú de puntos suspensivos abierto](media/intro-maker-portal/help-icon.png)

Ambas opciones muestran vínculos a este conjunto de documentación, la comunidad de PowerApps (donde puede compartir información con usuarios de otras organizaciones) y el blog de PowerApps (donde se anuncian las características más recientes).

## <a name="other-common-tasks"></a>Otras tareas frecuentes

Al seleccionar las opciones en el encabezado y la barra de navegación izquierda, puede hacer más que crear y abrir las aplicaciones.

### <a name="from-the-header"></a>Del encabezado

- Seleccione la flecha hacia abajo para descargar clientes para dispositivos móviles y de otro tipo en los que puede ejecutar las aplicaciones.

    Para más información, vea [Find and run apps](../../user/index.md) (Búsqueda y ejecución de aplicaciones).

- Seleccione el icono de engranaje para realizar tareas tales como conectarse a orígenes de datos, identificar la licencia o licencias de PowerApps y abrir la página donde puede realizar tareas administrativas.

    Para más información, vea estos temas:

  - [Introducción a los conectores para aplicaciones de lienzo](connections-list.md)
  - [Compilación y certificación de conectores personalizados para aplicaciones de lienzo](register-custom-api.md)
  - [Administración de una puerta de enlace de datos local](gateway-management.md)
  - [Administración de PowerApps](../../administrator/index.md)
  - [Introducción a las licencias](../../administrator/pricing-billing-skus.md)
  - [Información general sobre la compilación de una aplicación controlada por modelos](../model-driven-apps/model-driven-app-overview.md)

### <a name="from-the-left-navigation-bar"></a>En la barra de navegación izquierda

Extienda la funcionalidad de las aplicaciones mediante la realización de estas tareas:

- Administrar entidades, conjuntos de opciones y la integración de datos en [Common Data Service](../common-data-service/data-platform-intro.md).
- Configuración de la lógica de negocios en [Microsoft Flow](https://docs.microsoft.com/flow/getting-started).
- Cree, empaquete y mantenga [soluciones](../../developer/common-data-service/introduction-solutions.md).
