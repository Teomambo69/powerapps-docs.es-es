---
title: Inicio de sesión por primera vez | Microsoft Docs
description: Un nuevo lugar de encuentro para todos los creadores de aplicaciones.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 08/06/2018
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 284d63d7ebc0eb57e11dae055a9178b3b92646cd
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74729510"
---
# <a name="sign-in-to-power-apps-for-the-first-time"></a>Iniciar sesión en Power apps por primera vez

Cuando inicia sesión en [Power apps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), el sitio ofrece una variedad de opciones para crear sus propias aplicaciones, abrir aplicaciones que usted u otros usuarios han creado y realizar tareas relacionadas. Estas tareas van desde las más sencillas, como la identificación de la licencia o licencias que le proporcionan acceso, hasta funcionalidades más avanzadas, como la creación de conexiones personalizadas para orígenes de datos específicos.

Puede seleccionar opciones en tres áreas generales:

- El encabezado de la parte superior de la página

    ![Encabezado](media/intro-maker-portal/header.png)

- La barra de navegación del borde izquierdo de la página

    ![Barra de navegación](media/intro-maker-portal/nav-bar.png)

- Los iconos grandes que aparecen en el centro de la página

    ![Área central de la página principal](media/intro-maker-portal/center-area.png)

Para obtener mejores resultados, asegúrese de que la página principal se establece en el entorno adecuado.

## <a name="choose-an-environment"></a>Selección de un entorno

Tanto si va a crear una aplicación, un flujo, una conexión de datos o una entidad en Common Data Service, gran parte de lo que se hace en Power apps se encuentra en un entorno específico. Los entornos crean límites entre distintos tipos de trabajo; por ejemplo, una organización podría tener entornos independientes para distintos departamentos. Muchas organizaciones usan entornos para separar aplicaciones que aún están en desarrollo de las que están listas para su uso generalizado. Puede que tenga acceso a varios entornos o solo a uno y, si cuenta con los permisos adecuados, tal vez pueda crear sus propios entornos.

Para comprobar en qué entorno se encuentra, busque el selector de entornos junto al margen derecho del encabezado.

![Selector de entornos](media/intro-maker-portal/environment-switcher.png)

Si crea una aplicación en un entorno, no podrá verla desde otro entorno. Además, las personas que quieran ejecutar la aplicación habrán de tener acceso al entorno en el que se creó.

> [!IMPORTANT]
> Asegúrese de que se encuentra en el entorno adecuado *antes* crear una aplicación, un flujo o un componente similar. No resulta fácil mover componentes de un entorno a otro.

Para más información, consulte [Environments overview](../../administrator/environments-overview.md) (Información general de los entornos).

## <a name="choose-an-app-type"></a>Elección de un tipo de aplicación

En Power Apps, puede crear y ejecutar estos tipos de aplicaciones:

- **Aplicaciones de lienzo**: admiten el diseño de interfaz de usuario personalizada y la conexión a datos desde diversos orígenes.
- Las **aplicaciones controladas por modelos** tienen una interfaz de usuario estándar y se conectan a los datos solo en Common Data Service. Sin embargo, resulta más fácil crear otros elementos, tales como vistas, paneles y diferentes tipos de lógica de negocios.

Si elige un entorno que tiene una base de datos Common Data Service, puede compilar aplicaciones de lienzo o controladas por modelos desde la misma página **principal** .

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

Ambas opciones muestran vínculos a este conjunto de documentación, la comunidad de Power apps (donde puede compartir información con usuarios de otras organizaciones) y el blog de Power apps (donde se anuncian las características más recientes).

## <a name="other-common-tasks"></a>Otras tareas frecuentes

Al seleccionar las opciones en el encabezado y la barra de navegación izquierda, puede hacer más que crear y abrir las aplicaciones.

### <a name="from-the-header"></a>Del encabezado

- Seleccione la flecha hacia abajo para descargar clientes para dispositivos móviles y de otro tipo en los que puede ejecutar las aplicaciones.

    Para más información, vea [Find and run apps](../../user/index.md) (Búsqueda y ejecución de aplicaciones).

- Seleccione el icono de engranaje para realizar tareas como conectarse a orígenes de datos, identificar la licencia o licencias de Power apps y abrir la página en la que puede realizar tareas administrativas.

    Para más información, vea estos temas:

  - [Introducción a los conectores para aplicaciones de lienzo](connections-list.md)
  - [Compilación y certificación de conectores personalizados para aplicaciones de lienzo](register-custom-api.md)
  - [Administración de una puerta de enlace de datos local](gateway-management.md)
  - [Administrar Power apps](../../administrator/index.md)
  - [Introducción a las licencias](../../administrator/pricing-billing-skus.md)
  - [Información general sobre la compilación de una aplicación controlada por modelos](../model-driven-apps/model-driven-app-overview.md)

### <a name="from-the-left-navigation-bar"></a>En la barra de navegación izquierda

Extienda la funcionalidad de las aplicaciones mediante la realización de estas tareas:

- Administrar entidades, conjuntos de opciones e integración de datos en [Common Data Service](../common-data-service/data-platform-intro.md).
- Configure la lógica de negocios en [Power Automatic](https://docs.microsoft.com/flow/getting-started).
- Cree, empaquete y mantenga [soluciones](../../developer/common-data-service/introduction-solutions.md).
