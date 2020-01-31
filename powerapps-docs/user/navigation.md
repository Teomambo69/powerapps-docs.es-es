---
title: Navegación básica en una aplicación controlada por modelos | Microsoft Docs
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 10/03/2019
ms.author: mkaur
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 93c0f84dd5b37c8db67d66dbfa2d1af0ee532949
ms.sourcegitcommit: 4d858e628c89d245317d6192801d136f3591ea52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76832862"
---
#  <a name="basic-navigation-in-a-model-driven-app"></a>Navegación básica en una aplicación controlada por modelos 

En esta introducción se explica cómo buscar y abrir una aplicación y cómo trabajar con sus elementos de interfaz de usuario comunes, como listas, formularios y procesos empresariales.

## <a name="navigating-among-apps-areas-and-entities"></a>Navegar entre aplicaciones, áreas y entidades

Una aplicación controlada por modelos se crea a partir de aplicaciones (aplicaciones), áreas y entidades.

- *Aplicaciones* proporciona una colección de funcionalidades para realizar una clase específica de actividad, como administrar las cuentas y los contactos. Use el menú del selector de aplicaciones para navegar entre las aplicaciones que están disponibles para su organización.

- Un *área de trabajo* es una subdivisión de una aplicación, dedicada a una característica específica. Cada área de trabajo proporciona una colección de entidades de destino para trabajar en esa área. En algunos casos, la misma entidad aparece en más de un área (o incluso en más de una aplicación). Por ejemplo, las entidades contactos y cuentas aparecen en una variedad de aplicaciones y áreas de trabajo. Use el menú del área de trabajo para navegar entre las áreas de trabajo de la aplicación actual.

- Las *entidades* representan un tipo específico de datos, como contactos y cuentas. Las entidades utilizan un formato de datos estructurado, que define la colección de campos disponibles para la entidad. Cada entidad se compone de una colección de registros individuales. Por ejemplo, para la entidad contactos, cada registro describe una sola persona y cada registro incluye una colección de campos como el nombre, el apellido y la dirección de correo electrónico. Las entidades suelen presentar dos vistas: una vista de lista, que normalmente es una tabla que enumera los registros disponibles. y una vista de formulario, que muestra todos los datos y la configuración disponibles para un único registro. Use el navegador lateral para desplazarse entre las entidades del área de trabajo actual.

### <a name="move-between-apps"></a>Moverse entre aplicaciones

Use el menú selector de aplicaciones para cambiar entre las aplicaciones.

![Menú del selector de aplicaciones](media/app-selector.png "Menú del selector de aplicaciones")

Las aplicaciones que aparecen en el menú del selector de aplicaciones dependerán de las aplicaciones a las que tenga acceso. 

### <a name="move-between-entities-records-and-work-areas"></a>Moverse entre entidades, registros y áreas de trabajo

Es fácil ponerse en marcha y volver a los registros favoritos o más usados. En la ilustración siguiente se muestran los elementos de navegación principales.

![Controles de navegación, vista expandida](media/nav-expanded.png "Controles de navegación, vista expandida")

Situado

1. **Selector de aplicaciones**: abra este menú para desplazarse entre aplicaciones.
1. **Botón contraer/expandir**: Seleccione esta opción para contraer el navegador y así permitir más espacio para la parte principal de la página. Si el navegador ya está contraído, seleccione este botón para expandirlo de nuevo.
1. **Registros recientes**: expanda esta entrada para ver una lista de los registros que ha utilizado recientemente. Seleccione un registro aquí para abrirlo. Seleccione el icono de alfiler junto a un registro que aparece aquí para agregarlo a los favoritos (registros anclados).
1. **Registros favoritos**: expanda esta entrada para ver y abrir los registros favoritos (anclados). Use la lista **registros recientes** para agregar registros aquí. Seleccione el icono de quitar PIN junto a un registro que aparece aquí para quitarlo de la lista.
1. **Navegador de entidades**: en esta área se muestran todas las entidades y paneles disponibles para el área de trabajo actual. Seleccione cualquier entrada aquí para abrir el panel con nombre o la vista de lista para esa entidad.
1. **Selector de área de trabajo**: abra este menú para desplace a otro área de trabajo. El área de trabajo actual se denomina aquí.

## <a name="working-with-list-views"></a>Trabajar con vistas de lista

Normalmente, cuando se abre por primera vez una entidad, verá la vista de lista, que muestra una lista de los registros que pertenecen a esa entidad, con formato de tabla. Por ejemplo, si abre la entidad **cuentas** , verá una lista de cuentas.

![Una vista de lista típica](media/list-view.png "Una vista de lista típica")

Situado

1. **Seleccionar registros**: Seleccione uno o más registros; para ello, coloque una marca de verificación en esta columna. Dependiendo de dónde trabaje, es posible que pueda aplicar una sola operación a todos los registros seleccionados a la vez con los botones de la barra de comandos.
2. **Abrir un registro**: Seleccione cualquier registro de la lista para abrir su vista de registros, que muestra todos los detalles del registro. Normalmente, debe seleccionar en la columna **nombre** para abrir un registro de la entidad actual. Algunas entidades proporcionan vínculos a registros de entidades relacionadas en otras columnas (por ejemplo, un contacto relacionado).
3. **Ordenar o filtrar la lista**: Seleccione esta función para ordenar la lista por los valores de esa columna o filtre la lista por los valores de esa columna. Una flecha en el encabezado de columna indica qué columna se está ordenando y en qué dirección. 
4. **Barra de comandos**: Use los comandos de la barra de comandos para operar en los registros de la lista y realizar acciones relacionadas. Algunos comandos (como **eliminar**) requieren que primero seleccione uno o más registros de destino colocando una marca de verificación en la columna situada más a la izquierda, mientras que otros funcionan en toda la lista. Puede exportar la lista a un libro de Excel (posiblemente basado en una plantilla), abrir gráficos y paneles, etc., en función del tipo de registros con los que esté trabajando.
5. **Busque en la vista**: Escriba texto en el campo de búsqueda situado encima de la lista para mostrar solo los registros de la vista actual que contengan el texto.
6. **Filtrado y paginación**: Seleccione una letra para mostrar solo los registros cuyos nombres empiecen por esa letra. Si la lista contiene más registros de los que se pueden mostrar en una página, utilice las flechas de paginación situadas en la parte inferior de la lista para avanzar y retroceder por las páginas.

## <a name="working-with-record-views"></a>Trabajar con vistas de registros

Las vistas de registros muestran todos los detalles sobre un único registro y a veces también proporcionan características especiales para trabajar con ellos. Normalmente, se abrirá una vista de registros seleccionando un registro que aparece en una vista de lista, pero también puede abrir una vista de registros siguiendo un vínculo de un registro relacionado.

![Una vista de registros típica](media/form-view.png "Una vista de registros típica")

Situado

1. **Pestañas**: la mayoría de las vistas de registros están divididas en pestañas. Cada pestaña proporciona una colección de campos relacionados del registro. Cuando las pestañas están disponibles, se enumeran debajo del nombre del registro. Seleccione cualquier nombre de ficha para ir a la pestaña. La pestaña actual se muestra subrayada.
2. **Relacionado**: casi todos los tipos de registros muestran una pestaña **relacionada** una vez que se han guardado al menos una vez. Esta pestaña es realmente una lista desplegable que se puede usar para buscar otros tipos de registros que usan o hacen referencia al registro mostrado. Al elegir un nombre de entidad en la lista desplegable **relacionada** , se abre una nueva pestaña denominada para esa entidad, que muestra una lista de todos los registros relacionados de ese tipo. La pestaña **relacionado** sigue estando disponible y puede utilizarla para buscar otros tipos de registros que hagan referencia al actual.
3. **Barra de comandos**: Use los comandos de la barra de comandos para operar en el registro actual o realizar una tarea relacionada con el registro. Los comandos disponibles varían en función del tipo de registro, pero normalmente puede usar la barra de comandos para guardar los cambios, eliminar el registro, actualizar la página, enviar por correo electrónico un vínculo al registro, reasignar el propietario del registro o exportar el registro mediante una plantilla de Word.
4. **Barra de encabezado**: algunas vistas de registros muestran algunos campos especialmente importantes en la barra de título, al contrario que el nombre del registro. Suelen ser campos fundamentales para trabajar con registros del tipo actual (como el nombre del registro o el propietario del registro).
5. **Ver y editar todos los valores de campo**: en el cuerpo principal de la vista de registros, encontrará todos los campos relacionados con la pestaña, la vista de formulario y el tipo de registro actuales. Los campos marcados con un asterisco rojo son obligatorios y no se puede guardar el registro sin tener valores válidos. Los campos marcados con un signo más azul son especialmente importantes o recomendables, pero no son estrictamente necesarios. Los campos que muestran un icono de candado son de solo lectura y no se pueden editar.

## <a name="record-set-navigation"></a>Navegación por el conjunto de registros 
Navegue por varios registros con vistas y consultas predefinidas. La navegación centrada en los registros mejora la productividad, ya que los usuarios pueden ir directamente de un registro de la lista a otro y volver atrás fácilmente sin perder la lista de trabajo.

> [!div class="mx-imgBorder"]
> ![Navegación por conjunto de registros](media/recordset1.png "Navegación por el conjunto de registros")

## <a name="reference-panel"></a>Panel de referencias
El panel de referencias es una excelente manera de trabajar sin salir de la pantalla en la que esté. Puede buscar otros elementos relacionados, como casos u oportunidades para una cuenta, dentro del contexto del registro que está viendo sin tener que navegar a otra pantalla.

> [!div class="mx-imgBorder"]
> ![Panel de referencia](media/reference-panel1.png "Panel de referencias")

 Para obtener más información sobre el panel de referencias, vea este vídeo:

<div class="embeddedvideo"><iframe src="https://www.microsoft.com/videoplayer/embed/d8224c3f-6e20-4b8e-9d0d-b0f5602c7708" frameborder="0" allowfullscreen=""></iframe></div>

## <a name="notifications"></a>Notificaciones 

Hay tres tipos de notificaciones que se muestran en un formulario: informativo, ADVERTENCIA y error. Las notificaciones siempre están disponibles en la parte superior del formulario, justo encima del encabezado.

Al seleccionar la notificación de error, se le llevará al campo del formulario en el que se produjo el error.

![Ejemplo de notificaciones](media/notifications.png "Ejemplo de notificaciones")

Situado

1. **Info**: la notificación es informativa.
2. **WARN**: la notificación es una advertencia. 
3. **Error**: la notificación es un error. 


### <a name="single-notification"></a>Notificación única
Si solo hay una notificación, verá una única línea.

![Ejemplo de notificaciones únicas](media/single_notification.png "Ejemplo de notificaciones únicas")

### <a name="multiple-notifications"></a>Varias notificaciones
Si hay más de una notificación, verá el número de notificaciones. Seleccione el botón de contenido adicional para ver cada mensaje.

![Ejemplo de varias notificaciones](media/multiple_notification.png "Ejemplo de varias notificaciones")

