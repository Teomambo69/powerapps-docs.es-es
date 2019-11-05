---
title: Problemas habituales de PowerApps y soluciones a los mismos | Microsoft Docs
description: Lista de problemas y soluciones habituales de PowerApps.
author: KumarVivek
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 08/21/2019
ms.author: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 2c093adb4b63b5374de118d8d7dbb3421e352f46
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73541070"
---
# <a name="common-issues-and-resolutions-for-powerapps"></a>Problemas y soluciones habituales de PowerApps

En este artículo se enumeran algunos de los problemas habituales que puede experimentar al usar PowerApps. Si procede, se proporcionan soluciones alternativas.

1. **Problema de inicio de sesión en determinados dispositivos móviles Android cuando se usa el autenticador** (21 de agosto de 2019)

    En ciertos dispositivos y escenarios, puede experimentar errores de inicio de sesión al usar el autenticador. Esto se debe a que el OEM limita esta funcionalidad. Para obtener más información sobre el error y las posibles mitigaciones, vea [aquí](https://github.com/AzureAD/azure-activedirectory-library-for-android/wiki/ADALError:-BROKER_AUTHENTICATOR_NOT_RESPONDING).    

1. **Problema de cámara en dispositivos móviles Android** (1 de enero de 2019)

    Si el control de cámara deja de funcionar en un dispositivo Android, vuelva a publicar la aplicación y vuelva a abrirla en el dispositivo. El control de cámara se actualizó en respuesta a un cambio en el sistema operativo Android y la aplicación se beneficiará de la actualización cuando vuelva a publicarla.

1. **Desplazamiento en galerías de alto flexible** (27 de noviembre de 2018)

    Si tiene una limitación al desplazarse con el dedo, levante el dedo y empiece a desplazarse de nuevo.

1. **Dibujar con mouse o entrada táctil no es suave en PowerApps para Windows** (Sep. 24, 2018)

    El control Pen solo tiene compatibilidad parcial con el dibujo mediante el mouse o la entrada táctil en la aplicación de Windows. Los trazos pueden ser intermitentes. Para suavizar el dibujo, use un lápiz o ejecute la aplicación en un explorador.

1. **Varios controles de medios en PowerApps Mobile** (2 de agosto de 2018)

    PowerApps Mobile se ejecuta en diversos tipos de dispositivos y, algunos de ellos, tienen limitaciones específicas de esa plataforma:

    - Puede reproducir vídeos en varios controles de **vídeo** al mismo tiempo en todas las plataformas, excepto en dispositivos iPhone.
    - Puede grabar audio con varios controles de **micrófono** al mismo tiempo en todas las plataformas, excepto en el reproductor de web.

1. **Volver a publicar aplicaciones** (2 de agosto de 2018)

    Si no ha actualizado la aplicación en varios meses, vuelva a publicarla para sincronizarla con la versión más reciente de PowerApps, que incluye mejoras de rendimiento y otras correcciones.

1. <a name="out-of-memory"></a>**Memoria insuficiente del explorador** (23 de julio de 2018)

    Si se queda sin memoria mientras usa PowerApps, considere la posibilidad de descargar una versión de 64 bits de Chrome, Microsoft Edge o Internet Explorer.

1. **Iniciar un sitio web desde una aplicación insertada** (10 de mayo de 2018)

    Los exploradores Internet Explorer y Microsoft Edge pueden bloquear una dirección URL o sitio web que esté en modo protegido o en una zona de seguridad más baja que el sitio web en el que se carga la aplicación. Para resolver este problema, [cambie la configuración de seguridad y privacidad](https://support.microsoft.com/help/17479/windows-internet-explorer-11-change-security-privacy-settings) de su explorador.

1. **Controles de cuadro combinado en galerías** (3 de mayo de 2018)

    Cuando se usa un control de **cuadro combinado** en una galería, sus selecciones no se conservan cuando el usuario se va desplazando por la galería. Esto no ocurre si se usa un control de **cuadro combinado** en una galería que no permite el desplazamiento. En estos momentos no existe una solución alternativa.

1. **Usar una imagen personalizada como icono de aplicación** (11 de abril de 2018)

    En la versión 3.18043 de PowerApps Studio para Windows, no se puede cargar una imagen personalizada para usarla como icono de aplicación. Para solucionar este problema, utilice para ello [PowerApps Studio para web](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc). Como alternativa, puede usar uno de los iconos que se incluyen con PowerApps Studio para Windows y personalizar el color de fondo.

1. **Copiar y pegar pantallas entre aplicaciones** (4 de abril de 2018)

    No se admite actualmente copiar y pegar pantallas entre aplicaciones. Para resolver este problema, agregue una nueva pantalla a la aplicación de destino, copie los controles de la pantalla de la aplicación de origen y, a continuación, péguelos en la pantalla de la aplicación de destino.

1. **Cambiar el diseño de los formularios de SharePoint** (7 de marzo de 2018)

    Al personalizar un formulario de lista de SharePoint en algunos idiomas, si se intenta cambiar el diseño de vertical (valor predeterminado) a horizontal, la aplicación puede mostrar varios errores (triángulos amarillos en controles). Para resolver estos errores y conservar el diseño horizontal, haga clic en **Deshacer**.

1. **Control Data Table**

    Si copia y pega un control **Data Table** en el que la propiedad **Elementos** se ha establecido en una fórmula que contenga una función **Filter**, la fórmula de la propiedad  **Elementos** del nuevo control **Data Table** termina una con nombres de campo que contienen el sufijo **_1**. Esto hace que los nombres de campo no sean válidos y que no se muestren datos en la tabla de datos. Para solucionar este problema, antes de copiar el control, confirme que la función **Filter** no hace referencia a ningún campo del origen de datos que se llame igual que alguna columna del control **Data Table**. En caso de que haga referencia, cambie el nombre de la columna en el control **Data Table**. O bien, quite el sufijo **_1** sufijo de los nombres de campo no válidos para que coincidan con los nombres de la entidad.

1. **Controles de la cámara en PowerApps Studio para Windows**

    PowerApps Studio para Windows puede bloquearse si agrega un control de cámara o abre una aplicación que utilice un control de cámara. Para evitar este problema, use [PowerApps Studio para web](create-app-browser.md) cuando agregue o use un control de cámara.

1. **Versión 2.0.700 en dispositivos Android**

    Si instala la versión 2.0.700 en un dispositivo Android y no puede abrir aplicaciones (o una aplicación deja de responder), desinstale PowerApps, reinicie el dispositivo y vuelva a instalar PowerApps.

1. **Galería "vacía" al abrir una aplicación**

    Si genera una aplicación automáticamente a partir de datos, guarda la aplicación y, a continuación, vuelve a abrirla, la galería podría no mostrar datos inmediatamente. Para resolver este problema, escriba al menos un carácter en el cuadro de búsqueda y, a continuación, elimine el texto que ha escrito. La galería mostrará los datos según lo previsto.

1. **Actualización de PowerApps en Windows 8.1**

    Si instala PowerApps en un equipo que ejecuta Windows 8 o Windows 8.1, mantenga la aplicación de la Tienda Windows abierta y activa, use el acceso a Configuración para comprobar si hay actualizaciones y, a continuación, instálelas.

1. **Conectores personalizados y Common Data Service**

    Si una aplicación creada con PowerApps compilación 2.0.540 o anterior está basada en una base de datos de Common Data Service y al menos un conector personalizado en un entorno diferente, tendrá que implementar el conector en el mismo entorno que la base de datos y actualizar la aplicación para que use el nuevo conector. De lo contrario, un cuadro de diálogo notificará a los usuarios de que no se encontró la API. Para más información, consulte [Environments overview](../../administrator/environments-overview.md) (Información general de los entornos).

1. **Ejecución de una aplicación en Windows 8.1**

    Si instala [esta actualización para Windows 8.1](https://technet.microsoft.com/library/security/ms16-118), no podrá ejecutar aplicaciones que se abran en PowerApps Studio en ese sistema operativo. Aunque todavía puede ejecutar aplicaciones que se abren en [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) o con PowerApps Mobile.

1. **Nombres de columna con espacios**

    Si usa una lista de SharePoint o una tabla de Excel en la que un nombre de columna contenga un espacio, PowerApps lo reemplazará por **"\_x0020\_"** . Por ejemplo, **"Nombre de columna"** en SharePoint o Excel aparecerá como **"Nombre_x0020_de_columna"** en PowerApps cuando se muestre en el diseño de datos o se use en una fórmula.

1. **Cambio de un flujo en una aplicación compartida**

    Si agrega un flujo a una aplicación, la comparte y, después, agrega un servicio o cambia una conexión en el flujo, debe quitar el flujo de la aplicación compartida, volver a agregar el flujo y volver a compartir la aplicación. De lo contrario, los usuarios que desencadenan el flujo obtendrán un error de autenticación.

1. **Uso de una versión localizada**.

    Si está ejecutando la versión 2.0.531 en Windows 8.1, no podrá escribir en un control de **entrada de texto** si el dispositivo está configurado para un idioma que requiere una ventana IME.

1. **Control de la cámara en Windows Phone**

    Una aplicación que contiene un control de la cámara puede bloquearse si abre la aplicación en Windows Phone que ejecuta la compilación 10.0.10586.107. Para evitar este problema, actualice a la compilación más reciente (por ejemplo, mediante la ejecución del [Asesor de actualizaciones](https://www.microsoft.com/store/p/upgrade-advisor/9nblggh0f5g4)).

1. **Abrir una aplicación a partir de una plantilla**

    Si está ejecutando la versión 2.0.500 o anterior, aparece un mensaje de error al intentar crear una aplicación a partir de una plantilla. Debe actualizar la versión para poder usar esta característica.

    Si está ejecutando la versión 2.0.510 o posterior, puede aparecer una advertencia al intentar crear una aplicación a partir de una plantilla. No obstante, puede cerrar el mensaje y crear la aplicación.

1. **Escaneo de un código de barras**

    Para más información sobre las limitaciones y los procedimientos recomendados al utilizar un control **Código de barras**, consulte [Escanear un código de barras](scan-barcode.md).

1. **Creación y modificación de aplicaciones en un explorador**

    En la versión web de PowerApps Studio puede hacer muchas de las cosas que puede hacer en PowerApps Studio para Windows, pero no todas. Para más información, consulte [Create an app in a browser](create-app-browser.md) (Crear una aplicación en un explorador).

1. **Cambio de un campo de título en una entidad**

    Si cambia el campo de título para una entidad que hace referencia a otras entidades mediante una o varias búsquedas, se producirá un error al intentar guardar el cambio. Para evitar este problema, quite todas las búsquedas de la entidad para la que desea cambiar el campo de título, realice el cambio y vuelva a crear las búsquedas. Para más información acerca de las búsquedas, consulte [Crear una relación entre entidades](../common-data-service/data-platform-entity-lookup.md).

1. **Aplicaciones que se conectan a SharePoint local**

    Si comparte una aplicación que se basa en conexiones que no se comparten automáticamente (por ejemplo, un sitio de SharePoint local), los usuarios que abran la aplicación en un explorador verán un cuadro de diálogo sin texto al hacer clic o pulsar en **Iniciar sesión**. Para cerrar el cuadro de diálogo, haga clic o pulse en el icono Cerrar (X) en la esquina superior derecha. El cuadro de diálogo no aparece si se abre la aplicación en PowerApps Studio o PowerApps Mobile. Para más información acerca de las conexiones compartidas, consulte [Share app resources](share-app-resources.md) (Uso compartido de recursos de la aplicación).

1. **Cuando PowerApps genera una aplicación a partir de datos, el campo utilizado para ordenar y buscar no está configurado automáticamente**.

   Para configurar este campo, modifique la fórmula **[Elementos](controls/properties-core.md)** de la galería, tal como se describe en las secciones para filtrar y ordenar en [Add a gallery](add-gallery.md) (Agregar una galería).

1. **Para las aplicaciones que se crean a partir de datos, solo se puede acceder a los 500 primeros registros de un origen de datos**.

     En general, PowerApps funciona con orígenes de datos de cualquier tamaño mediante la delegación de operaciones al origen de datos. Para las operaciones que no se pueden delegar, PowerApps mostrará una advertencia en el momento de la creación y operará solo en los 500 primeros registros del origen de datos.  Consulte el artículo [Filter function](functions/function-filter-lookup.md) (Función de filtro) para más información acerca de la delegación.

1. **Se debe dar un formato de tabla a los datos de Excel**.

     Para más información acerca de las limitaciones al usar Excel como origen de datos, consulte [Cloud-storage connections](connections/cloud-storage-blob-connections.md#known-limitations) (Conexiones de almacenamiento en la nube).

1. **Se admiten listas personalizadas de SharePoint pero no las bibliotecas, algunos tipos de columnas de la lista o las columnas que admiten varios valores o selecciones**.

     Para más información, consulte [SharePoint Online](connections/connection-sharepoint-online.md#known-issues).

1. **No se admite la co-autoría. Un autor a la vez, por favor**.

     Puede dañar una aplicación o sobrescribir los cambios de otros usuarios si más de una persona está modificando a la vez la misma aplicación. Cierre la aplicación antes de que otra persona la edite.

1. **A veces, se tarda un tiempo en poder usar una aplicación recién compartida**.

     En algunos casos, una aplicación recién compartida no estará disponible de inmediato. Espere unos instantes y estará disponible.

1. **En [Control de formulario](controls/control-form-detail.md), no puede modificar datos con una tarjeta personalizada**.

     Falta la propiedad **[Update](controls/control-card.md)** en la tarjeta personalizada de existencias, que es necesaria para escribir los cambios. Para solucionar este problema:

    * Seleccione el control de formulario e inserte una tarjeta mediante el panel derecho en función del campo que desee que muestre la tarjeta.  
    * Desbloquee la tarjeta, tal como se describe en [Understanding data cards](working-with-cards.md#unlock-a-card) (Comprender tarjetas de datos).
    * Quite o reorganice los controles dentro de la tarjeta como considere oportuno, tal como lo haría con la tarjeta personalizada.

1. **Una aplicación que se ejecuta en Android 5.0, Nexus 6 con Webview de versiones v48 o v49, puede bloquearse**.

     Los usuarios pueden solucionar este problema mediante la actualización a una versión anterior de Webview (3x) o a Android 6.0.

1. **El uso de la cámara puede estar deshabilitado temporalmente si hay poca memoria**.

     Si el dispositivo móvil tiene poca memoria, la cámara se deshabilita temporalmente para evitar el bloqueo del dispositivo.

1. **El conector de vídeo de Office 365 no es compatible**.

1. **La galería de tarjetas está en desuso**.

     Las aplicaciones existentes que utilizan esta característica seguirán ejecutándose por el momento pero no puede agregar una galería de tarjetas. Reemplace las galerías de tarjetas por los nuevos controles **[Editar formulario](controls/control-form-detail.md)** y **[Mostrar formulario](controls/control-form-detail.md)** .
