---
title: Ver los registros de errores del portal y almacenarlos en Azure BLOB Storage | MicrosoftDocs
description: Obtenga información sobre cómo ver los registros de errores del portal y almacenarlos en la cuenta de Azure BLOB Storage.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 7989c15b0c5c4cf50d4b55f518244758afc067e1
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542922"
---
# <a name="view-portal-error-logs"></a>Visualización de los registros de errores del portal

Como administrador o desarrollador del portal, puede usar los portales de PowerApps para crear un sitio web para sus clientes. Una tarea común para un desarrollador es depurar problemas durante el desarrollo del portal. Para ayudar a depurar, puede tener acceso a los registros de errores detallados para cualquier problema en el portal. Hay varias maneras de obtener los registros de errores de los portales.

## <a name="custom-error"></a>Error personalizado

Si se produce cualquier excepción del servidor en el portal, se muestra de forma predeterminada una página de error personalizada con un mensaje de error descriptivo. Para configurar el mensaje de error, vea [Mostrar un mensaje de error personalizado](#display-a-custom-error-message).

Sin embargo, es mejor ver la página de error detallado de ASP.NET, también conocida como pantalla amarilla de muerte (YSOD), para fines de depuración. La página de error detallada le ayuda a obtener la pila completa de errores del servidor.

> [!div class=mx-imgBorder]
> ![Pantalla amarilla de muerte](../media/ysod.png "Pantalla amarilla de muerte")

Para habilitar YSOD, debe [deshabilitar los errores personalizados](#disable-custom-error) en el portal.

> [!NOTE]
> Es aconsejable deshabilitar solo los errores personalizados cuando se encuentre en la fase de desarrollo y habilitar los errores personalizados una vez que se haya puesto en marcha.

Más información sobre el error personalizado: [Mostrar una página de error personalizada](https://docs.microsoft.com/aspnet/web-forms/overview/older-versions-getting-started/deploying-web-site-projects/displaying-a-custom-error-page-cs)

### <a name="disable-custom-error"></a>Deshabilitar error personalizado

Puede deshabilitar los errores personalizados en los portales para mostrar el mensaje de excepción detallado si se produce cualquier excepción del servidor en el portal.

1. Abra el [centro de administración de portales de PowerApps](admin-overview.md).

2. Vaya a **acciones del Portal** > **deshabilitar errores personalizados**.

   > [!div class=mx-imgBorder]
   > ![Deshabilitar error personalizado](../media/disable-custom-errors.png "Deshabilitar error personalizado")

3. Seleccione **deshabilitar** en el mensaje de confirmación. Mientras se deshabilitan los errores personalizados, el portal se reinicia y no estará disponible. Aparece un mensaje cuando se deshabilitan los errores personalizados.

### <a name="enable-custom-error"></a>Habilitar error personalizado

Puede habilitar errores personalizados en los portales para mostrar una página de aspecto profesional en lugar de YSOD. Esta página proporciona información significativa si se produce alguna excepción en la aplicación.

1. Abra el [centro de administración de portales de PowerApps](admin-overview.md).

2. Vaya a **acciones del Portal** > **Habilitar errores personalizados**.

   > [!div class=mx-imgBorder]
   > ![Habilitar error personalizado](../media/enable-custom-errors.png "Habilitar error personalizado")

3. Seleccione **Habilitar** en el mensaje de confirmación. Mientras se habilitan los errores personalizados, el portal se reinicia y no estará disponible. Aparece un mensaje cuando se habilitan los errores personalizados.

> [!NOTE]
> - Si cambia la instancia de a la que está conectado el portal, el valor de errores personalizados se establece en habilitado. Debe volver a deshabilitar los errores personalizados, si es necesario.
> - No debe habilitar o deshabilitar los errores personalizados cuando se cambia la instancia a la que está conectado el portal. en caso contrario, aparece un mensaje de error.

### <a name="display-a-custom-error-message"></a>Mostrar un mensaje de error personalizado

Puede configurar el portal para que muestre un error personalizado de aspecto profesional en lugar de un error genérico.

Para definir un error personalizado, use el `Portal Generic Error`de código de contenido. El contenido definido en este fragmento de código se muestra en la página de error. Este fragmento de contenido no está disponible de forma integrada y debe crearlo. El **tipo** de fragmento de contenido puede ser **texto** o **HTML**. Para crear o editar el fragmento de código, vea [personalizar el contenido mediante fragmentos de código](../configure/customize-content-snippets.md).

> [!NOTE]
> Si el código de líquido se escribe en el fragmento de contenido, se omitirá y no se representará.

Cuando se habilitan los errores personalizados, el mensaje aparece en la siguiente estructura de la página de error:

<Content Snippet> 
<Error ID >
<Date and time>
<Portal ID>

A continuación se muestra un ejemplo de un mensaje de error personalizado con un fragmento de contenido de tipo HTML:

Se trata de un error personalizado. Haga clic aquí para archivar una incidencia de soporte técnico con la captura de pantalla.

> [!div class=mx-imgBorder]
> ![Mensaje de error personalizado](../media/custom-error-message.png "Mensaje de error personalizado")

> [!NOTE]
> Si el portal no puede recuperar un fragmento de código porque no se puede conectar a Common Data Service o si el fragmento de código no está disponible en Common Data Service, aparece un mensaje de error.

## <a name="access-portal-error-logs"></a>Acceder a los registros de errores del portal

Después de desarrollar y publicar el portal, debe tener acceso a los registros del portal para depurar los problemas de los clientes. Para acceder a los registros, puede configurar el portal para enviar todos los errores de la aplicación a una cuenta de Azure BLOB Storage que posea. Al acceder a los registros de errores del portal, puede responder a las consultas de los clientes de forma eficaz porque tiene detalles del problema. Para obtener los registros de errores del portal en el almacenamiento de blobs de Azure, debe habilitar el registro de diagnóstico desde el centro de administración de portales de PowerApps.

> [!NOTE]
> Si cambia la instancia de Common Data Service a la que está conectado el portal, el registro de diagnóstico está deshabilitado. Debe volver a habilitar el registro de diagnóstico.

### <a name="enable-diagnostic-logging"></a>Habilitación del registro de diagnóstico

1. Abra el [centro de administración de portales de PowerApps](admin-overview.md).

2. Vaya a **acciones del Portal** > **Habilitar el registro de diagnóstico**.

   > [!div class=mx-imgBorder]
   > ![Habilitación del registro de diagnóstico](../media/enable-diagnostic-logging.png "Habilitación del registro de diagnóstico")

3. En la ventana **Habilitar registro de diagnóstico** , escriba los valores siguientes:

   - **Cadena de conexión de Azure BLOB Storage servicio**: la dirección URL del servicio Azure BLOB Storage para almacenar los registros de errores del portal. La longitud máxima de la dirección URL es de 2048 caracteres. Si la dirección URL tiene más de 2048 caracteres, aparece un mensaje de error. Más información sobre la cadena de conexión: [configuración de Azure Storage cadenas de conexión](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
   - **Seleccione el período de retención**: duración para mantener los registros de errores del portal en el almacenamiento de blobs. Los registros de errores se eliminan después de la duración seleccionada. Puede seleccionar uno de los siguientes valores:
     - 1 día
     - 7 días
     - 30 días
     - 60 días
     - 90 días
     - 180 días
     - Deben

   De forma predeterminada, el período de retención es de 30 días.
  
   > [!div class=mx-imgBorder]
   > ![Habilitar ventana de registro de diagnóstico](../media/enable-diagnostic-logging-window.png "Habilitar ventana de registro de diagnóstico")

4. Haga clic en **configurar**.

Una vez configurado el registro de diagnóstico, se crea un nuevo contenedor de blobs **de telemetría-registros** en la cuenta de Azure Storage y los registros se escriben en los archivos de blobs almacenados en el contenedor. En la captura de pantalla siguiente se muestra el contenedor de blobs **de telemetría-logs** en el explorador de Azure Storage:

> [!div class=mx-imgBorder]
> ![Cuenta de Azure blog Storage](../media/azure-blob-storage.png "Cuenta de Azure blog Storage")

Cuando el registro de diagnóstico se habilita correctamente, la siguiente acción está disponible:
- **Actualizar configuración del registro de diagnóstico**: permite actualizar o quitar la configuración del registro de diagnóstico para el portal.
- **Deshabilitar el registro de diagnóstico**: permite deshabilitar la configuración del registro de diagnóstico para el portal.
 
### <a name="update-diagnostic-logging"></a>Actualización del registro de diagnóstico

1. Abra el [centro de administración de portales de PowerApps](admin-overview.md).

2. Vaya a **acciones del Portal** > **actualizar la configuración del registro de diagnóstico**.

   > [!div class=mx-imgBorder]
   > ![Actualizar configuración del registro de diagnóstico](../media/update-diagnostic-logging.png "Actualizar configuración del registro de diagnóstico")

3. En la ventana de configuración de registro de diagnósticos de actualización, escriba los valores siguientes:
   - **¿Desea actualizar la cadena de conexión del servicio Azure BLOB Storage?** : le permite especificar si desea actualizar la cadena de conexión del servicio Azure BLOB Storage. De forma predeterminada, está seleccionada.
   - **Cadena de conexión de Azure BLOB Storage servicio**: la dirección URL del servicio Azure BLOB Storage para almacenar los registros de errores del portal. La longitud máxima de la dirección URL puede ser de 2048 caracteres. Si la dirección URL tiene más de 2048 caracteres, aparece un mensaje de error. Este campo solo se muestra si la casilla **¿desea actualizar la cadena de conexión del servicio Azure BLOB Storage?** está activada. Más información sobre la cadena de conexión: [configuración de Azure Storage cadenas de conexión](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
   - **Seleccione el período de retención**: duración para mantener los registros de errores del portal en el almacenamiento de blobs. Los registros de errores se eliminan después de la duración seleccionada. Puede seleccionar uno de los siguientes valores:
     - 1 día
     - 7 días
     - 30 días
     - 60 días
     - 90 días
     - 180 días
     - Deben

   De forma predeterminada, el período de retención es de 30 días.

   > [!div class=mx-imgBorder]
   > ![Actualizar la ventana de configuración de registro de diagnóstico](../media/update-diagnostic-logging-window.png "Actualizar la ventana de configuración de registro de diagnóstico")

4. Haga clic en **Actualizar**.

### <a name="disable-diagnostic-logging"></a>Deshabilitar el registro de diagnóstico

1. Abra el [centro de administración de portales de PowerApps](admin-overview.md).

2. Vaya a **acciones del Portal** > **deshabilitar el registro de diagnóstico**.

   > [!div class=mx-imgBorder]
   > ![Deshabilitar el registro de diagnóstico](../media/disable-diagnostic-logging.png "Deshabilitar el registro de diagnóstico")

3. Haga clic en **deshabilitar** en el mensaje de confirmación.

## <a name="display-plugin-error"></a>Mostrar error de complemento

Otro escenario que se suele producir al desarrollar un portal es un error generado por complementos personalizados y lógica de negocios escritos en el entorno de Common Data Service. Normalmente se puede tener acceso a estos errores mediante la [deshabilitación de errores personalizados](#disable-custom-error) o la [habilitación del registro de diagnóstico](#enable-diagnostic-logging). Sin embargo, en algunos casos, es más rápido mostrar estos errores directamente en el portal para diagnosticar el problema con más rapidez. Para ello, puede configurar el portal para mostrar los errores de complementos personalizados desde Common Data Service en la pantalla del portal.

Para mostrar los errores de complementos personalizados, cree la configuración del sitio `Site/EnableCustomPluginError` y establezca su valor en true. Los errores del complemento personalizado se mostrarán en la pantalla en lugar de un error genérico. El error mostrará solo la parte de mensaje del error del complemento y no el seguimiento de la pila completo.

A continuación se muestran las pantallas en las que aparecerán errores de complementos personalizados: 
- Lista de entidades 
    - Recuperación de registros 
- Formulario de la entidad 
    - Extra 
    - Crear/actualizar, etc. 
- Formularios Web Forms 
    - Extra 
    - Crear/actualizar, etc.

Si la configuración del sitio no está presente, se tratará como false de forma predeterminada y los errores del complemento no se representarán.
