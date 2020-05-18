---
title: Navegación básica en una aplicación controlada por modelos | Microsoft Docs
description: Navegación básica en una aplicación basada en modelo. En este artículo se explica cómo buscar y abrir una aplicación, además de cómo trabajar con sus elementos comunes de la interfaz de usuario, como las listas, los formularios y los procesos empresariales.
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 02/03/2019
ms.author: mkaur
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 1932699e669b47eba91c4e576416d287d590b5e8
ms.sourcegitcommit: d500f44e77747a3244b6691ad9b3528e131dbfa5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2020
ms.locfileid: "3303309"
---
#  <a name="basic-navigation-in-a-model-driven-app"></a>Navegación básica en una aplicación controlada por modelos 

En esta introducción se explica cómo buscar y abrir una aplicación, además de cómo trabajar con sus elementos comunes de la interfaz de usuario, como las listas, los formularios y los procesos empresariales.

## <a name="navigating-among-apps-areas-and-entities"></a>Navegación por aplicaciones, áreas y entidades

Una aplicación basada en modelo consta de aplicaciones, áreas y entidades.

- Las *aplicaciones* proporcionan una colección de funciones para llevar a cabo una clase específica de actividad, como administrar las cuentas y los contactos. Use el menú del selector de aplicaciones para navegar por las aplicaciones que están disponibles para su organización.

- Un *área de trabajo* es una subdivisión de una aplicación, dedicada a una característica específica. Cada área de trabajo proporciona una colección de entidades de destino para trabajar en dicha área. En algunos casos, la misma entidad aparece en más de un área (o incluso en más de una aplicación). Las entidades Contacto y Cuenta, por ejemplo, aparecen en varias aplicaciones y áreas de trabajo. Use el menú del área de trabajo para desplazarse por las áreas de trabajo para la aplicación actual.

- Las *entidades* representan un tipo específico de datos, como contactos y cuentas. Las entidades usan un formato de datos estructurados, que define la colección de campos disponibles en la entidad. Cada entidad consta de una colección de registros individuales. Por ejemplo, en el caso de la entidad Contacto, cada registro describe una sola persona e incluye una colección de campos (como el nombre, los apellidos y la dirección de correo electrónico). Normalmente, las entidades presentan dos vistas: una vista de lista, que suele ser una tabla donde se enumeran los registros disponibles, y una vista de formulario, que muestra todos los datos y valores de configuración disponibles para un solo registro. Use el navegador lateral para desplazarse entre las entidades del área de trabajo actual.

### <a name="move-between-apps"></a>Desplazamiento por las aplicaciones

Use el menú del selector de aplicaciones para cambiar entre las aplicaciones.

![Menú del selector de aplicaciones](media/app-selector.png "Menú del selector de aplicaciones")

Las aplicaciones que aparecen en el menú del selector de aplicaciones dependerán de las aplicaciones a las que tenga acceso. 

### <a name="move-between-entities-records-and-work-areas"></a>Desplazamiento por las entidades, los registros y las áreas de trabajo

Es fácil desplazarse por sus registros favoritos o más usados y volver a ellos. En la siguiente ilustración se muestran los elementos de navegación principales.

![Controles de navegación, vista expandida](media/nav-expanded.png "Controles de navegación, vista expandida")

Leyenda:

1. **Selector de aplicaciones**: abra este menú para moverse entre aplicaciones.
2. **Botón Contraer/Expandir**: seleccione este botón para contraer el navegador y permitir que haya más espacio para la parte principal de la página. Si el navegador ya está contraído, seleccione este botón para volver a expandirlo.
3. **Registros recientes**: expanda esta entrada para ver una lista de registros utilizados recientemente. Seleccione un registro para abrirlo. Seleccione el icono de alfiler situado junto a uno de los registros que aparecen aquí para agregarlo a los favoritos (registros anclados).
4. **Registros favoritos**: expanda esta entrada para ver y a abrir sus registros favoritos (anclados). Use la lista **Registros recientes** para agregar registros aquí. Seleccione el icono de quitar alfiler situado junto a uno de los registros que aparecen aquí para eliminarlo de la lista.
5. **Navegador entre entidades**: esta área muestra todas las entidades y todos los paneles disponibles para el área de trabajo actual. Seleccione cualquiera de estas entradas para abrir el panel con nombre o la vista de lista de dicha entidad.
6. **Selector del área de trabajo**: abra este menú para ir a otra área de trabajo. El área de trabajo actual aparece aquí.

## <a name="working-with-list-views"></a>Trabajo con vistas de lista

Normalmente, la primera vez que abra una entidad, verá la vista de lista, en la que se muestra una lista de los registros que pertenecen a esa entidad, con formato de tabla. Por ejemplo, si abre la entidad **Cuentas**, verá una lista de cuentas.

![Vista de lista habitual](media/list-view.png "Vista de lista habitual")

Leyenda:

1. **Seleccionar registros**: seleccione uno o varios registros poniendo una marca de verificación en esta columna. En función de dónde esté trabajando, es posible que pueda aplicar una única operación a todos los registros seleccionados a la vez mediante los botones de la barra de comandos.
2. **Abrir un registro**: seleccione un registro de la lista para abrir la vista de registro, que muestra todos los detalles del registro. Normalmente, para abrir un registro de la entidad actual, tiene que seleccionar uno de la columna **Nombre**. Algunas entidades proporcionan vínculos a registros de entidades relacionadas en otras columnas (por ejemplo, un contacto relacionado).
3. **Ordenar o filtrar la lista:** seleccione esta opción para ordenar o filtrar la lista por los valores de esa columna. Una flecha en el encabezado de columna indica qué columna se está ordenando y en qué dirección. 
4. **Barra de comandos**: use los comandos de la barra de comandos para operar en registros de la lista y llevar a cabo acciones relacionadas. Algunos comandos (como **Eliminar**) requieren que seleccione primero uno o varios registros de destino poniendo una marca de verificación en la columna situada más a la izquierda, mientras que otros operan en toda la lista. Puede exportar la lista a un libro de Excel (posiblemente basado en una plantilla), abrir gráficos y paneles, etc., en función del tipo de registros con los que esté trabajando.
5. **Buscar en la vista**: escriba el texto en el campo de búsqueda que aparece encima de la lista para mostrar solo los registros en la vista actual que contienen ese texto.
6. **Filtrar y paginar**: seleccione una letra para mostrar solo aquellos registros cuyos nombres empiezan por esa letra. Si la lista contiene más registros de los que se pueden mostrar en una página, use las flechas de paginación situadas en la parte inferior de la lista para avanzar y retroceder por las páginas.

## <a name="working-with-record-views"></a>Trabajo con vistas de registros

Las vistas de registros muestran todos los detalles sobre un único registro y a veces también proporcionan características especiales para trabajar con él. Normalmente, para abrir una vista de registros, seleccionará un registro que aparece en una vista de lista, pero también puede abrir una vista de registros si sigue un vínculo de un registro relacionado.

![Vista de registros habitual](media/form-view.png "Vista de registros habitual")

Leyenda:


1. **Pestañas**: la mayoría de las vistas de registros se dividen en pestañas. En cada pestaña se proporciona una colección de campos relacionados del registro. Si las pestañas están disponibles, aparecen debajo del nombre del registro. Seleccione cualquier nombre de pestaña para ir a esa pestaña. La pestaña actual se muestra subrayada.
2. **Relacionado**: en casi todos los tipos de registros se muestra una pestaña **Relacionado** después de haberlos guardado al menos una vez. Esta pestaña es en realidad una lista desplegable que puede usar para buscar otros tipos de registros que utilizan el registro mostrado o hacen referencia a este. Al elegir el nombre de una entidad en la lista desplegable **Relacionado**, se abre una nueva pestaña con el nombre de dicha entidad, en la que se muestra una lista de todos los registros relacionados de ese tipo. La pestaña **Relacionado** sigue estando disponible y puede usarla para buscar otros tipos de registros que hagan referencia al actual.
3. **Barra de comandos**: use los comandos de la barra de comandos para operar en el registro actual o llevar a cabo una tarea relacionada con el registro. Los comandos disponibles varían en función del tipo de registro, pero normalmente puede usar la barra de comandos para guardar los cambios, eliminar el registro, actualizar la página, enviar un vínculo al registro por correo electrónico, reasignar el propietario del registro o exportar el registro mediante una plantilla de Word.
4. **Barra de encabezado**: algunas vistas de registro muestran algunos campos especialmente importantes en la barra de encabezado, frente al nombre del registro. Suelen ser campos fundamentales para trabajar con registros del tipo actual (como el nombre o el propietario del registro).
5. **Ver y editar todos los valores de campo**: en el cuerpo de la vista de registro se encuentran todos los campos relacionados con la pestaña, la vista de formulario y el tipo de registro actuales. Los campos marcados con un asterisco rojo son obligatorios y no se puede guardar el registro sin que tengan valores válidos. Los campos marcados con un signo más azul son especialmente importantes o recomendados, pero no son estrictamente obligatorios. Los campos en los que se muestra un icono de candado son de solo lectura y no se pueden editar.

## <a name="record-set-navigation"></a>Navegación por el conjunto de registros 

Navegue por varios registros mediante vistas y consultas predefinidas. La navegación centrada en los registros mejora la productividad, ya que los usuarios pueden ir directamente de un registro de la lista a otro y volver atrás fácilmente sin perder la lista de trabajo.

> [!div class="mx-imgBorder"]
> ![Navegación por el conjunto de registros](media/recordset1.png "Navegación por el conjunto de registros")

## <a name="reference-panel"></a>Panel de referencia

El panel de referencias es una excelente manera de trabajar sin salir de la pantalla en la que esté. Puede buscar otros elementos relacionados, como casos u oportunidades de una cuenta, en el contexto del registro que está viendo sin tener que ir a otras pantallas.

> [!div class="mx-imgBorder"]
> ![Panel de referencia](media/reference-panel1.png "Panel de referencia")

 Para obtener más información sobre el panel de referencias, vea este vídeo:

<div class="embeddedvideo"><iframe src="https://www.youtube.com/embed/ruAPEKY5vNc" frameborder="0" allowfullscreen=""></iframe></div>

## <a name="notifications"></a>Notificaciones 

Hay tres tipos de notificaciones que se muestran en un formulario: informativas, de advertencia y de error. Las notificaciones siempre están disponibles en la parte superior del formulario, justo encima del encabezado.

Al seleccionar la notificación de error, se le llevará al campo del formulario en el que se ha producido el error.

![Ejemplo de notificaciones](media/notifications.png "Ejemplos de notificaciones")

Leyenda:

1. **Información**: la notificación es informativa.
2. **Advertencia**: la notificación es una advertencia. 
3. **Error**: la notificación es un error. 



### <a name="single-notification"></a>Notificación única

Si solo hay una notificación, verá una única línea.

![Ejemplo de notificaciones únicas](media/single_notification.png "Ejemplo de una única notificación")

### <a name="multiple-notifications"></a>Varias notificaciones

Si hay varias notificaciones, verá el número de estas. Seleccione el botón de contenido adicional para ver cada mensaje.

![Ejemplo de varias notificaciones](media/multiple_notification.png "Ejemplo de varias notificaciones")
