---
title: Visualización de registros de error del portal y su almacenamiento en Azure Blob | MicrosoftDocs
description: Aprenda a ver registros de error del portal y a almacenarlos en su cuenta de almacenamiento de Azure Blob.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 4b7fe184dce7475bf2b7fc373fc98d875fffb515
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "2979885"
---
# <a name="view-portal-error-logs"></a>Ver los logs de error del portal

Como administrador o desarrollador de un portal, puede usar portales de Power Apps para crear un sitio web para sus clientes. Una tarea habitual entre los desarrolladores es depurar problemas mientras desarrollan el portal. Para ayudar a depurar, puede acceder a los registros de errores detallados para todos los problemas en el portal. Hay varias formas en las que puede obtener registros de errores para sus portales.

## <a name="custom-error"></a>Error personalizado

Si se produce cualquier tipo de excepción de servidor en el portal, se muestra una página de error personalizada con un mensaje de error fácil de entender de forma predeterminada. Para configurar el mensaje de error, vea [mostrar un mensaje de error personalizado ](#display-a-custom-error-message).

Sin embargo, es mejor ver la página de error detallada de ASP.NET, también conocida como pantalla amarilla de muerte (YSOD), para fines de depuración. La página de error detallada le ayuda a obtener la pila completa de errores de servidor.

> [!div class=mx-imgBorder]
> ![Pantalla amarilla de muerte](../media/ysod.png "Pantalla amarilla de muerte")

Para habilitar YSOD, debe [deshabilitar los errores personalizados](#disable-custom-error) en el portal.

> [!NOTE]
> Es recomendable deshabilitar los errores personalizados solo cuando se encuentra en la fase de desarrollo y habilitar los errores personalizados en la puesta en marcha.

Más información sobre el error personalizado: [mostrar una página de Error personalizada](https://docs.microsoft.com/aspnet/web-forms/overview/older-versions-getting-started/deploying-web-site-projects/displaying-a-custom-error-page-cs)

### <a name="disable-custom-error"></a>Deshabilitar un error personalizado

Puede deshabilitar los errores personalizados en los portales para visualizar el mensaje detallado de excepción si se produce una excepción de lado de servidor en el portal.

1. Abra [Centro de administración de Portales de Power Apps](admin-overview.md).

2. Vaya a **Acciones del portal** > **deshabilitar errores personalizados**.

   > [!div class=mx-imgBorder]
   > ![Deshabilitar un error personalizado](../media/disable-custom-errors.png "Deshabilitar un error personalizado")

3. Seleccione **Deshabilitar** en el mensaje de confirmación. Mientras los errores personalizados se deshabilitan, el portal se reinicia y deja de estar disponible. Cuando se deshabilitan los errores personalizados, aparece un mensaje.

### <a name="enable-custom-error"></a>Habilitar un error personalizado

Puede habilitar los errores personalizados en el portal para mostrar una página de aspecto profesional en lugar de YSOD. Esta página ofrece información importante si se produce cualquier excepción en la aplicación.

1. Abra [Centro de administración de Portales de Power Apps](admin-overview.md).

2. Vaya a **Acciones del portal** > **habilitar errores personalizados**.

   > [!div class=mx-imgBorder]
   > ![Habilitar un error personalizado](../media/enable-custom-errors.png "Habilitar un error personalizado")

3. Seleccione **Habilitar** en el mensaje de confirmación. Mientras los errores personalizados se habilitan, el portal se reinicia y deja de estar disponible. Cuando se habilitan los errores personalizados, aparece un mensaje.

> [!NOTE]
> - Si cambia la instancia a la que está conectado su portal, la configuración de errores personalizados se establece en habilitado. Debe deshabilitar los errores personalizados de nuevo, si es necesario.
> - No debe habilitar o deshabilitar los errores personalizados cuando se ha cambiado la instancia a la que está conectado su portal; de lo contrario, aparece un mensaje de error.

### <a name="display-a-custom-error-message"></a>Mostrar un mensaje de error personalizado

Puede configurar su portal para mostrar un error personalizado de aspecto profesional en lugar de un error genérico.

Para definir un error personalizado, utilice el fragmento de contenido `Portal Generic Error`. El contenido definido en este fragmento se muestra en la página de error. Este fragmento de contenido no está disponible directamente y debe crearlo. El fragmento de contenido **tipo** puede ser **texto** o **HTML**. Para crear o editar el fragmento de contenido, consulte [Personalizar el contenido mediante fragmentos de contenido](../configure/customize-content-snippets.md).

> [!NOTE]
> Si se escribe código de líquido en el fragmento de contenido, se omitirá y no se representará.

Al habilitar los errores personalizados, aparece el mensaje en la siguiente estructura de la página de error:

<Content Snippet> 
<Error ID >
<Date and time>
<Portal ID>

A continuación se muestra un ejemplo de un mensaje de error personalizado que usa un fragmento de contenido de tipo HTML:

Este es un error personalizado, presente un vale de soporte con la captura de pantalla del error haciendo clic aquí.

> [!div class=mx-imgBorder]
> ![Mensaje de error personalizado](../media/custom-error-message.png "Mensaje de error personalizado")

> [!NOTE]
> Si el portal no puede recuperar un fragmento de contenido porque no se puede conectar a Common Data Service o bien, si el fragmento no está disponible en Common Data Service, aparece un mensaje de error.

## <a name="access-portal-error-logs"></a>Los registros de error del portal de acceso

Después de desarrollar y publicar el portal, debe poder seguir teniendo acceso a los registros del portal para depurar los problemas notificados por sus clientes. Para obtener acceso a los registros, puede configurar su portal para enviar todos los errores de aplicación a una cuenta de Azure Blob Storage propia. Mediante el acceso a registros de error del portal, puede responder a consultas de clientes eficazmente porque tiene detalles del problema. Para obtener los registros de error del portal en Azure Blob Storage, debe habilitar el registro de diagnóstico en el centro de administración de portales de Power Apps.

> [!NOTE]
> Si cambia la instancia Common Data Service a la que está conectado su portal, el registro de diagnóstico se deshabilita. Debe habilitar el registro de diagnóstico de nuevo.

### <a name="enable-diagnostic-logging"></a>Habilitar registro de diagnóstico

1. Abra [Centro de administración de Portales de Power Apps](admin-overview.md).

2. Vaya a **Acciones del portal** > **habilitar registro de diagnóstico**.

   > [!div class=mx-imgBorder]
   > ![Habilitar registro de diagnóstico](../media/enable-diagnostic-logging.png "Habilitar registro de diagnóstico")

3. En la ventana **Habilitar registro de diagnóstico**, especifique los valores siguientes:

   - **Cadena de conexión del servicio Azure Blob Storage**: dirección URL del servicio de Azure Blob Storage para almacenar los registros de errores del portal. La longitud máxima de la URL es de 2048 caracteres. Si la dirección URL tiene más de 2048 caracteres, aparece un mensaje de error. Para obtener más información sobre la cadena de conexión: [cadenas de conexión de configuración de Azure Storage](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
   - **Seleccionar período de retención**: duración de mantenimiento de los registros de error del portal en el almacenamiento de blobs. Se eliminan los registros de errores después de la duración seleccionada. Puede seleccionar uno de los siguientes valores:
     - 1 día
     - 7 días
     - 30 días
     - 60 días
     - 90 días
     - 180 días
     - Siempre

   De forma predeterminada, el período de retención es 30 días.
  
   > [!div class=mx-imgBorder]
   > ![Habilitar ventana de registro de diagnóstico](../media/enable-diagnostic-logging-window.png "Habilitar ventana de registro de diagnóstico")

4. Haga clic en **Configurar**.

Una vez que se ha configurado el registro de diagnóstico, se crea un nuevo contenedor de blobs **registros de telemetría** en su cuenta de Azure Storage y los registros se escriben en los archivos de blobs que se almacenan en el contenedor. La siguiente captura de pantalla muestra el contenedor de blobs **registros de telemetría** en el Explorador de Azure Storage:

> [!div class=mx-imgBorder]
> ![Cuenta de almacenamiento de blog de Azure](../media/azure-blob-storage.png "Cuenta de almacenamiento de blog de Azure")

Cuando el registro de diagnóstico se habilita correctamente, la acción siguiente pasa a estar disponible:
- **Actualizar configuración de registro de diagnóstico**: permite actualizar o quitar la configuración de registro de diagnóstico para el portal.
- **Deshabilitar el registro de diagnóstico**: permite deshabilitar la configuración de registro de diagnóstico para el portal.
 
### <a name="update-diagnostic-logging"></a>Actualizar el registro de diagnóstico

1. Abra [Centro de administración de Portales de Power Apps](admin-overview.md).

2. Vaya a **Acciones de portal** > **Actualizar configuración de registro de diagnóstico**.

   > [!div class=mx-imgBorder]
   > ![Actualizar configuración de registro de diagnóstico](../media/update-diagnostic-logging.png "Actualizar configuración de registro de diagnóstico")

3. En la ventana de actualizar registro de diagnóstico, especifique los valores siguientes:
   - **¿Desea actualizar la cadena de conexión del servicio Azure Blob Storage?**: permite especificar si se actualiza la cadena de conexión del servicio de Azure Blob Storage. La opción se encuentra seleccionada de forma predeterminada.
   - **Cadena de conexión del servicio Azure Blob Storage**: dirección URL del servicio de Azure Blob Storage para almacenar los registros de errores del portal. La longitud máxima de la URL puede ser de 2048 caracteres. Si la dirección URL tiene más de 2048 caracteres, aparece un mensaje de error. Este campo se muestra solo si la casilla **¿Desea actualizar la cadena de conexión del servicio Azure Blob Storage?** está seleccionada. Para obtener más información sobre la cadena de conexión: [cadenas de conexión de configuración de Azure Storage](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
   - **Seleccionar período de retención**: duración de mantenimiento de los registros de error del portal en el almacenamiento de blobs. Se eliminan los registros de errores después de la duración seleccionada. Puede seleccionar uno de los siguientes valores:
     - 1 día
     - 7 días
     - 30 días
     - 60 días
     - 90 días
     - 180 días
     - Siempre

   De forma predeterminada, el período de retención es 30 días.

   > [!div class=mx-imgBorder]
   > ![Actualizar ventana de configuración de registro de diagnóstico](../media/update-diagnostic-logging-window.png "Actualizar ventana de configuración de registro de diagnóstico")

4. Haga clic en **Actualizar**.

### <a name="disable-diagnostic-logging"></a>Deshabilitar el registro de diagnóstico

1. Abra [Centro de administración de Portales de Power Apps](admin-overview.md).

2. Vaya a **Acciones del portal** > **deshabilitar el registro de diagnóstico**.

   > [!div class=mx-imgBorder]
   > ![Deshabilitar el registro de diagnóstico](../media/disable-diagnostic-logging.png "Deshabilitar el registro de diagnóstico")

3. Haga clic en **Deshabilitar** en el mensaje de confirmación.

## <a name="display-plugin-error"></a>Mostrar error de complemento

Otro escenario que a menudo se produce al desarrollar un portal es un error generado por los complementos personalizados y la lógica de negocios escrita en su entorno de Common Data Service. Suele poder accederse a estos errores [deshabilitando errores personalizados](#disable-custom-error) o [habilitando el registro de diagnóstico](#enable-diagnostic-logging). Sin embargo, en algunos casos, es más rápido mostrar estos errores directamente en el portal para diagnosticar el problema con mayor rapidez. Para ello, puede configurar su portal para mostrar errores de complemento personalizados de Common Data Service en la pantalla del portal.

Para mostrar los errores de los complementos personalizados, cree la configuración de sitio `Site/EnableCustomPluginError` y establezca su valor en True. Los errores de complementos personalizados se mostrarán en la pantalla en lugar de un error genérico. El error mostrará solo la parte de mensaje del error de complemento y no el seguimiento de pila completo.

A continuación se muestran las pantallas donde aparecerán los errores de complementos personalizados: 
- Lista de entidades 
    - Recuperación de registros 
- Formulario de entidad 
    - Recuperar 
    - Creación o actualización, etc. 
- Formularios web 
    - Recuperar 
    - Creación o actualización, etc.

Si no hay configuración del sitio, se tratará como falso de forma predeterminada y los errores de complementos no se procesarán.
