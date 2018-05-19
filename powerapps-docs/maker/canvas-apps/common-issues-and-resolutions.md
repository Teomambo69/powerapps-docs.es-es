---
title: Problemas habituales de PowerApps y soluciones a los mismos | Microsoft Docs
description: Lista de problemas y soluciones habituales de PowerApps.
author: skjerland
manager: kfile
ms.service: powerapps
ms.topic: conceptual
ms.component: canvas
ms.date: 05/10/2018
ms.author: sharik
ms.openlocfilehash: 71e6d6977ff84ac8131acb9353f919c5ee80995b
ms.sourcegitcommit: fe556abcfd6bdfeb5fdeea8f07b185b4b502d02f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/11/2018
---
# <a name="common-issues-and-resolutions-for-powerapps"></a>Problemas y soluciones habituales de PowerApps
En este artículo se enumeran algunos de los problemas habituales que puede experimentar al usar PowerApps. Si procede, se proporcionan soluciones alternativas.

## <a name="recently-addedchanged"></a>Agregado o cambiado recientemente
1. **Inicio de un sitio web desde una aplicación insertada**

    Los exploradores Internet Explorer y Microsoft Edge pueden bloquear una dirección URL o sitio web que esté en modo protegido o en una zona de seguridad más baja que el sitio web en el que se carga la aplicación. Para resolver este problema, [cambie la configuración de seguridad y privacidad](https://support.microsoft.com/en-us/help/17479/windows-internet-explorer-11-change-security-privacy-settings) de su explorador.

1. **Controles de cuadro combinado en galerías**

    Cuando se usa un control de **cuadro combinado** en una galería, sus selecciones no se conservan cuando el usuario se va desplazando por la galería. Esto no ocurre si se usa un control de **cuadro combinado** en una galería que no permite el desplazamiento. En estos momentos no existe una solución alternativa.


1. **Utilice una imagen personalizada como icono de aplicación**

    En la versión 3.18043 de PowerApps Studio para Windows, no se puede cargar una imagen personalizada para usarla como icono de aplicación. Para solucionar este problema, utilice para ello [PowerApps Studio para web](https://web.powerapps.com). Como alternativa, puede usar uno de los iconos que se incluyen con PowerApps Studio para Windows y personalizar el color de fondo.

1. **Copiar y pegar pantallas entre aplicaciones**

    No se admite actualmente copiar y pegar pantallas entre aplicaciones. Para resolver este problema, agregue una nueva pantalla a la aplicación de destino, copie los controles de la pantalla de la aplicación de origen y, a continuación, péguelos en la pantalla de la aplicación de destino.

1. **Cambio del diseño de los formularios de SharePoint**

    Al personalizar un formulario de lista de SharePoint en algunos idiomas, si se intenta cambiar el diseño de vertical (valor predeterminado) a horizontal, la aplicación puede mostrar varios errores (triángulos amarillos en controles). Para resolver estos errores y conservar el diseño horizontal, haga clic en **Deshacer**.

1. **La aplicación no funciona**

    Si una aplicación que ha creado deja de funcionar sin previo aviso, es posible que sea porque no la ha actualizado o vuelto a publicar en los últimos seis meses. Para resolver el problema, actualice o vuelva a publicar la aplicación para sincronizarla con la última versión de PowerApps y, a continuación, asegúrese de volver a hacerlo periódicamente en un máximo de seis meses.

1. **Control Data Table**

    Si copia y pega un control **Data Table** en el que la propiedad **Elementos** se ha establecido en una fórmula que contenga una función **Filter**, la fórmula de la propiedad  **Elementos** del nuevo control **Data Table** termina una con nombres de campo que contienen el sufijo **_1**. Esto hace que los nombres de campo no sean válidos y que no se muestren datos en la tabla de datos. Para solucionar este problema, antes de copiar el control, confirme que la función **Filter** no hace referencia a ningún campo del origen de datos que se llame igual que alguna columna del control **Data Table**. En caso de que haga referencia, cambie el nombre de la columna en el control **Data Table**. O bien, quite el sufijo **_1** sufijo de los nombres de campo no válidos para que coincidan con los nombres de la entidad.

1. **Controles de la cámara en PowerApps Studio para Windows**

    PowerApps Studio para Windows puede bloquearse si agrega un control de cámara o abre una aplicación que utilice un control de cámara. Para evitar este problema, use [PowerApps Studio para web](create-app-browser.md) cuando agregue o use un control de cámara.

2. **Versión 2.0.700 en dispositivos Android**

    Si instala la versión 2.0.700 en un dispositivo Android y no puede abrir aplicaciones (o una aplicación deja de responder), desinstale PowerApps, reinicie el dispositivo y vuelva a instalar PowerApps.

3. **Galería "vacía" al abrir una aplicación**

    Si genera una aplicación automáticamente a partir de datos, guarda la aplicación y, a continuación, vuelve a abrirla, la galería podría no mostrar datos inmediatamente. Para resolver este problema, escriba al menos un carácter en el cuadro de búsqueda y, a continuación, elimine el texto que ha escrito. La galería mostrará los datos según lo previsto.

4. **Actualización de PowerApps en Windows 8.1**

    Si instala PowerApps en un equipo que ejecuta Windows 8 o Windows 8.1, mantenga la aplicación de la Tienda Windows abierta y activa, use el acceso a Configuración para comprobar si hay actualizaciones y, a continuación, instálelas.

5. **Conectores personalizados y Common Data Service**

   Si una aplicación creada con PowerApps compilación 2.0.540 o anterior está basada en una base de datos de Common Data Service y al menos un conector personalizado en un entorno diferente, tendrá que implementar el conector en el mismo entorno que la base de datos y actualizar la aplicación para que use el nuevo conector. De lo contrario, un cuadro de diálogo notificará a los usuarios de que no se encontró la API. Para más información, consulte [Environments overview](../../administrator/environments-overview.md) (Información general de los entornos).

6. **Ejecución de una aplicación en Windows 8.1**

    Si instala [esta actualización para Windows 8.1](https://technet.microsoft.com/library/security/ms16-118), no podrá ejecutar aplicaciones que se abran en PowerApps Studio en ese sistema operativo. Sin embargo, todavía puede ejecutar aplicaciones que se abren en  [powerapps.com](https://web.powerapps.com) o con PowerApps Mobile.

7. **Nombres de columna con espacios**

    Si usa una lista de SharePoint o una tabla de Excel en la que un nombre de columna contenga un espacio, PowerApps lo reemplazará por **"\_x0020\_"**. Por ejemplo, **"Nombre de columna"** en SharePoint o Excel aparecerá como **"Nombre_x0020_de_columna"** en PowerApps cuando se muestre en el diseño de datos o se use en una fórmula.

## <a name="older"></a>Anteriores
1. **Cambio de un flujo en una aplicación compartida**

    Si agrega un flujo a una aplicación, la comparte y, después, agrega un servicio o cambia una conexión en el flujo, debe quitar el flujo de la aplicación compartida, volver a agregar el flujo y volver a compartir la aplicación. De lo contrario, los usuarios que desencadenan el flujo obtendrán un error de autenticación.

2. **Uso de una versión localizada**.

    Si está ejecutando la versión 2.0.531 en Windows 8.1, no podrá escribir en un control de **entrada de texto** si el dispositivo está configurado para un idioma que requiere una ventana IME.

3. **Control de la cámara en Windows Phone**

    Una aplicación que contiene un control de la cámara puede bloquearse si abre la aplicación en Windows Phone que ejecuta la compilación 10.0.10586.107. Para evitar este problema, actualice a la compilación más reciente (por ejemplo, mediante la ejecución del [Asesor de actualizaciones](https://www.microsoft.com/store/p/upgrade-advisor/9nblggh0f5g4)).

4. **Abrir una aplicación a partir de una plantilla**

    Si está ejecutando la versión 2.0.500 o anterior, aparece un mensaje de error al intentar crear una aplicación a partir de una plantilla. Debe actualizar la versión para poder usar esta característica.

    Si está ejecutando la versión 2.0.510 o posterior, puede aparecer una advertencia al intentar crear una aplicación a partir de una plantilla. No obstante, puede cerrar el mensaje y crear la aplicación.

5. **Escaneo de un código de barras**

    Para más información sobre las limitaciones y los procedimientos recomendados al utilizar un control **Código de barras**, consulte [Escanear un código de barras](scan-barcode.md).

6. **Creación y modificación de aplicaciones en un explorador**

    En la versión web de PowerApps Studio puede hacer muchas de las cosas que puede hacer en PowerApps Studio para Windows, pero no todas. Para más información, consulte [Create an app in a browser](create-app-browser.md) (Crear una aplicación en un explorador).

7. **Cambio de un campo de título en una entidad**

    Si cambia el campo de título para una entidad que hace referencia a otras entidades mediante una o varias búsquedas, se producirá un error al intentar guardar el cambio. Para evitar este problema, quite todas las búsquedas de la entidad para la que desea cambiar el campo de título, realice el cambio y vuelva a crear las búsquedas. Para más información acerca de las búsquedas, consulte [Crear una relación entre entidades](../common-data-service/data-platform-entity-lookup.md).

8. **Aplicaciones que se conectan a SharePoint local**

    Si comparte una aplicación que se basa en conexiones que no se comparten automáticamente (por ejemplo, un sitio de SharePoint local), los usuarios que abran la aplicación en un explorador verán un cuadro de diálogo sin texto al hacer clic o pulsar en **Iniciar sesión**. Para cerrar el cuadro de diálogo, haga clic o pulse en el icono Cerrar (X) en la esquina superior derecha. El cuadro de diálogo no aparece si se abre la aplicación en PowerApps Studio o PowerApps Mobile. Para más información acerca de las conexiones compartidas, consulte [Share app resources](share-app-resources.md) (Uso compartido de recursos de la aplicación).

9. **Cuando PowerApps genera una aplicación a partir de datos, el campo utilizado para ordenar y buscar no está configurado automáticamente**.

   Para configurar este campo, modifique la fórmula **[Elementos](controls/properties-core.md)** de la galería, tal como se describe en las secciones para filtrar y ordenar en [Add a gallery](add-gallery.md) (Agregar una galería).

10. **Para las aplicaciones que se crean a partir de datos, solo se puede acceder a los 500 primeros registros de un origen de datos**.

     En general, PowerApps funciona con orígenes de datos de cualquier tamaño mediante la delegación de operaciones al origen de datos. Para las operaciones que no se pueden delegar, PowerApps mostrará una advertencia en el momento de la creación y operará solo en los 500 primeros registros del origen de datos.  Consulte el artículo [Filter function](functions/function-filter-lookup.md) (Función de filtro) para más información acerca de la delegación.

11. **Se debe dar un formato de tabla a los datos de Excel**.

     Para más información acerca de las limitaciones al usar Excel como origen de datos, consulte [Cloud-storage connections](connections/cloud-storage-blob-connections.md#known-limitations) (Conexiones de almacenamiento en la nube).

12. **Se admiten listas personalizadas de SharePoint pero no las bibliotecas, algunos tipos de columnas de la lista o las columnas que admiten varios valores o selecciones**.

     Para más información, consulte [SharePoint Online](connections/connection-sharepoint-online.md#known-issues).

13. **No se admite la co-autoría. Solo un autor a la vez, por favor**.

     Puede dañar una aplicación o sobrescribir los cambios de otros usuarios si más de una persona está modificando a la vez la misma aplicación. Cierre la aplicación antes de que otra persona la edite.

14. **A veces, se tarda un tiempo en poder usar una aplicación recién compartida**.

     En algunos casos, una aplicación recién compartida no estará disponible de inmediato. Espere unos instantes y estará disponible.

15. **En [Control de formulario](controls/control-form-detail.md), no puede modificar datos con una tarjeta personalizada**.

     Falta la propiedad **[Update](controls/control-card.md)** en la tarjeta personalizada de existencias, que es necesaria para escribir los cambios. Para solucionar este problema:

    * Seleccione el control de formulario e inserte una tarjeta mediante el panel derecho en función del campo que desee que muestre la tarjeta.  
    * Desbloquee la tarjeta, tal como se describe en [Understanding data cards](working-with-cards.md#unlock-a-card) (Comprender tarjetas de datos).
    * Quite o reorganice los controles dentro de la tarjeta como considere oportuno, tal como lo haría con la tarjeta personalizada.

16. **Una aplicación que se ejecuta en Android 5.0, Nexus 6 con Webview de versiones v48 o v49, puede bloquearse**.

     Los usuarios pueden solucionar este problema mediante la actualización a una versión anterior de Webview (3x) o a Android 6.0.

17. **El uso de la cámara puede estar deshabilitado temporalmente si hay poca memoria**.

     Si el dispositivo móvil tiene poca memoria, la cámara se deshabilita temporalmente para evitar el bloqueo del dispositivo.

18. **El conector de vídeo de Office 365 no es compatible**.

19. **La galería de tarjetas está en desuso**.

     Las aplicaciones existentes que utilizan esta característica seguirán ejecutándose por el momento pero no puede agregar una galería de tarjetas. Reemplace las galerías de tarjetas por los nuevos controles **[Editar formulario](controls/control-form-detail.md)** y **[Mostrar formulario](controls/control-form-detail.md)**.
