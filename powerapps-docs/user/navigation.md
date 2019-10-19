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
ms.openlocfilehash: a53aaf84530935e525f1177d85f74e125711fc40
ms.sourcegitcommit: 4c35aedde46380d5438687ae6f61a3b0cc7e7e2f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/05/2019
ms.locfileid: "71969157"
---
#  <a name="basic-navigation-in-a-model-driven-app"></a>Navegación básica en una aplicación controlada por modelos 

Use la barra de navegación para acceder a su área de trabajo, crear un registro, buscar elementos o realizar otras tareas en una aplicación controlada por modelos.

> [!div class="mx-imgBorder"]
> ![Navegación en una aplicación controlada por modelos](media/nav.png "Navegación en una aplicación controlada por modelos")

1. El mapa del sitio se expande y se conserva de forma predeterminada.
2. La subárea en la que se encuentra se resalta para indicarle su ubicación dentro de la aplicación.
3. Las secciones **Recientes** y **Anclados** se muestran en la parte superior para su comodidad. 
4. Utilice el selector de área para cambiar de aplicación.
5. Los iconos tienen colores únicos en la barra de comandos para poder distinguir los comandos.
  
## <a name="get-back-to-recent-records-items-or-view"></a>Vuelta a los registros, elementos o vistas recientes
Es probable que suela trabajar con los mismos registros. Por ejemplo, puede que normalmente acceda a un mismo contacto o a una misma cuenta, o bien que trabaje constantemente con las mismas listas (o vistas) de datos. Puede volver rápidamente a los registros o a las vistas que haya usado recientemente desde el mapa del sitio. También puede anclar los registros y las vistas para que sean fáciles de encontrar. 
  
1. En el **sitio del mapa**, seleccione **Recientes**.
  
2. En **Recientes**, elija a qué registro, elemento o vista quiere volver. 

## <a name="pin-records-items-or-view"></a>Anclaje de registros, elementos o vistas

1. En el **sitio del mapa**, seleccione **Recientes** para expandir la lista de elementos a los que ha accedido recientemente.
2. Seleccione el icono de anclaje junto a un elemento de la lista Recientes para agregarlo a la lista Anclados.

   > [!div class="mx-imgBorder"]
   > ![Registros anclados](media/pinnedrecords.png "Registros anclados")

## <a name="unpin-records-items-or-view"></a>Desanclaje de registros, elementos o vistas

1. En el **mapa del sitio**, seleccione **Anclados** para expandir la lista de elementos anclados.
2. Seleccione el icono para desanclar junto a un elemento para quitarlo de la lista.  

   > [!div class="mx-imgBorder"]
   > ![Desanclaje de registros](media/unpinnedrecords.png "Desanclaje de registros")

## <a name="record-set-navigation"></a>Navegación por el conjunto de registros 
Navegue por varios registros con vistas y consultas predefinidas. La navegación centrada en los registros mejora la productividad, ya que los usuarios pueden ir directamente de un registro de la lista a otro y volver atrás fácilmente sin perder la lista de trabajo.

> [!div class="mx-imgBorder"]
> ![Navegación por el conjunto de registros](media/recordset.png "Navegación por el conjunto de registros")

## <a name="reference-panel"></a>Panel de referencias
El panel de referencias es una excelente manera de trabajar sin salir de la pantalla en la que esté. Puede buscar otros elementos relacionados, como casos u oportunidades para una cuenta, dentro del contexto del registro que está viendo sin tener que navegar a otra pantalla.

> [!div class="mx-imgBorder"]
> ![Panel de referencias](media/reference-panel.png "Panel de referencias")

 Para obtener más información sobre el panel de referencias, vea este vídeo:

<div class="embeddedvideo"><iframe src="https://www.microsoft.com/en-us/videoplayer/embed/d8224c3f-6e20-4b8e-9d0d-b0f5602c7708" frameborder="0" allowfullscreen=""></iframe></div>

## <a name="notifications"></a>Notificaciones 

Hay tres tipos de notificaciones que se muestran en un formulario: informativo, ADVERTENCIA y error. Las notificaciones siempre están disponibles en la parte superior del formulario, justo encima del encabezado.

Al seleccionar la notificación de error, se le llevará al campo del formulario en el que se produjo el error.

![Ejemplo de notificaciones](media/notifications.png "Ejemplo de notificaciones")

Si solo hay una notificación, verá una única línea.

![Ejemplo de notificaciones únicas](media/single_notification.png "Ejemplo de notificaciones únicas")

Si hay más de una notificación, verá el número de notificaciones. Seleccione el botón de contenido adicional para ver cada mensaje.

![Ejemplo de varias notificaciones](media/multiple_notification.png "Ejemplo de varias notificaciones")

## <a name="grids"></a>Cuadrículas

Las cuadrículas de la interfaz unificada se han mejorado para aumentar la cantidad de datos que pueden verse en la pantalla. Las cuadrículas también tienen opciones de filtrado mejoradas que incluyen recordar el último filtro y ordenar el orden. 

Cuando el área de cuadrículas recupere datos, verá un indicador de carga que le permite saber que el sistema está trabajando en la recuperación de datos.

La Página principal de la cuadrícula recuerda el filtro, la ordenación y el estado de la página al navegar hacia delante y hacia atrás. Esto incluye la búsqueda rápida, el filtrado de columnas, el número de página, etc. La navegación fuera de la página se abre con el estado inicial.


   > [!div class="mx-imgBorder"]
   > ![Cuadrículas recordar]estado,(media/grid-remember-state-on-back-navigate.gif "recordar cuadrículas") de estado


La barra de saltos usa el primer campo ordenado. Si no se ha realizado ningún cambio de ordenación, la barra de saltos utiliza el campo principal. 

   > [!div class="mx-imgBorder"]
   > ![Cuadrículas recordar]estado,(media/jumpbar-filter-on-sorted-column.gif "recordar cuadrículas") de estado
   

Puede filtrar el campo **tipo de actividad** y seleccionar varios tipos de filtrado. Además, se pueden filtrar los campos de entidad relacionados como el propietario, el estado y el motivo.

   > [!div class="mx-imgBorder"]
   > ![](media/grid-activity-type-column-filter.gif "Filtrado") de cuadrículas de filtrado de cuadrículas
   
Al seleccionar el icono de jerarquía, se desplazará al formulario de jerarquía.

   > [!div class="mx-imgBorder"]
   > Icono de jerarquía ![icono]de(media/grid-row-hierarchy-icon.png "jerarquía")
   
También puede abrir el campo principal y los campos de búsqueda en una nueva pestaña o ventana.

   > [!div class="mx-imgBorder"]
   > ![Abrir en una nueva ventana](media/newtab.png "[abrir en una nueva ventana")


