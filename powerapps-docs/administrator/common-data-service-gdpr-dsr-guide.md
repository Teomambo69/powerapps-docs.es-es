---
title: Guía de DSR sobre datos creados por el cliente | Microsoft Docs
description: Guía de DSR de PowerApps sobre datos creados por el cliente
services: powerapps
suite: powerapps
documentationcenter: na
author: jamesol-msft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 04/17/2018
ms.author: paulliew
ms.openlocfilehash: cff822e24f1384833caa0baa945a7d3d07a8ee9b
ms.sourcegitcommit: e3a2819c14ad67cc4ca6640b9064550d0f553d8f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="responding-to-data-subject-rights-dsr-requests-for-customer-data-in-common-data-service-for-apps"></a>Respuesta a solicitudes de derechos del interesado (DSR) sobre datos de cliente de Common Data Service for Apps

## <a name="introduction-to-dsr-requests"></a>Introducción a las solicitudes de DSR
Como parte de nuestro compromiso de asociarnos con usted en su viaje al Reglamento general de protección de datos (RGPD) de la Unión Europa, hemos desarrollado esta documentación para ayudarle a prepararse. La documentación no solo describe lo que hacemos para prepararnos para el RGPD, sino que también comparte ejemplos de pasos que puede seguir hoy en día con Microsoft como apoyo al cumplimiento del RGPD al usar PowerApps, Microsoft Flow y Common Data Service for Apps.

El RGPD otorga derechos a las personas (denominadas "interesados" en el reglamento) para administrar los datos personales recopilados por un empresario u otro tipo de agencia u organización (denominado "poseedor de los datos"). Los datos personales se definen de manera muy amplia en RGPD como cualquier dato que se refiera a una persona física identificada o identificable. El RGPD ofrece a los interesados derechos específicos sobre sus datos personales; entre estos derechos se incluye el de obtener copias de los datos personales, solicitar correcciones en ellos, restringir su procesamiento, eliminarlos o recibirlos en formato electrónico para poder trasladarlos a otro poseedor de los datos. Una solicitud formal realizada por un interesado al poseedor de los datos para que tome medidas en sus datos personales se denomina solicitud de derechos del interesado (DSR, por sus siglas en inglés).

La guía describe cómo utilizar los productos, los servicios y las herramientas administrativas de Microsoft para ayudar a nuestros clientes poseedores de los datos a buscar datos personales y actuar en ellos para responder a las solicitudes de DSR. Específicamente, esto incluye cómo encontrar, acceder y actuar sobre los datos personales que residen en la nube de Microsoft. Este es un breve resumen de los procesos descritos en esta guía:

1. **Descubrir**: usar herramientas de búsqueda y detección para encontrar más fácilmente los datos de cliente que pueden ser objeto de una solicitud DSR. Cuando se recopilan documentos potencialmente sensibles, se puede realizar una o varias de las acciones de DSR descritas en los pasos siguientes para responder a la solicitud. Alternativamente, puede determinar que la solicitud no cumple con las directrices de la organización para responder a las solicitudes de DSR.

2. **Acceso**: recuperar datos personales que residen en la nube de Microsoft y, si se solicita, hacer una copia de los mismos que pueda estar disponible para el interesado.

3. **Rectificar**: realizar cambios o implementar otras acciones solicitadas sobre los datos personales, cuando corresponda.

4. **Restringir**: restringir el procesamiento de datos personales, ya sea mediante la eliminación de licencias para varios servicios en línea o mediante la desactivación de los servicios deseados cuando sea posible. También puede quitar datos de la nube de Microsoft y conservarlos de manera local o en otra ubicación.

5. **Eliminar**: quitar permanentemente los datos personales que residían en la nube de Microsoft.

6. **Exportar**: proporcionar una copia electrónica (en formato legible por máquina) de los datos personales al interesado.

Cada sección de esta guía describe los procedimientos técnicos que puede llevar a cabo una organización poseedora de los datos para responder a una solicitud de DSR sobre datos personales en la nube de Microsoft.

## <a name="common-data-service-customer-data"></a>Datos de cliente de Common Data Service

> [!IMPORTANT]
> Se aplica tanto a Common Data Service for Apps como a Common Data Service (versión anterior).

Existen dos tipos de Common Data Service (CDS): CDS for Apps y la versión anterior de CDS, cada uno con un proceso diferente para los datos personales.

Para identificar qué tipo de entorno CDS tiene, siga estos pasos desde el [sitio web de PowerApps](https://web.powerapps.com):

1.  Seleccione el **entorno** en la lista desplegable Entorno.
2.  Vaya a **Datos** > **Entidades**.

    Su entorno es CDS for Apps si aparecen estas entidades:

    ![Lista de entidades de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-entities-list.png)

    Su entorno es la versión anterior de CDS si aparecen estas entidades:

    ![Lista de entidades heredadas de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities-list.png)

Después de determinar qué tipo de entorno CDS tiene, puede seguir las secciones correspondientes de este documento para identificar los datos personales.

> [!NOTE]
> Es posible que tenga algunos entornos en CDS for Apps y otros en CDS (versión anterior), por lo que deberá repetir los procesos que se describen a continuación para cada entorno de su organización.

## <a name="user-personal-data-in-common-data-service-for-apps"></a>Datos personales del usuario en Common Data Service for Apps

### <a name="prerequisites"></a>Requisitos previos
Debe crearse un usuario desde el Centro de administración de Office 365 y asignarse una licencia de usuario de Common Data Service adecuada para acceder a CDS.  También se requiere un rol de seguridad antes de que el usuario pueda empezar a utilizar Common Data Service.

Los datos personales de los usuarios se guardan en el Centro de administración de Office 365 y en la entidad de usuario del sistema de CDS.  Existe un cierto conjunto de datos personales de usuario estándar que se guardan y mantienen en el Centro de administración de Office 365 (por ejemplo, nombre de usuario, identificación de usuario, teléfono, correo electrónico y dirección). Este conjunto de datos personales del usuario se sincroniza con la entidad de usuario del sistema CDS en todos los entornos.  El administrador del sistema solo puede actualizar este conjunto de datos personales en el Centro de administración de Office 365 y, después, estos atributos se sincronizan automáticamente con CDS for Apps. El administrador del sistema también puede crear atributos personalizados para capturar datos personales adicionales del usuario dentro de la entidad de usuario del sistema CDS.  El administrador del sistema mantiene y gestiona estos atributos personalizados dentro de CDS manualmente.

Cuando se elimina un usuario del Centro de administración de Office 365, el registro de usuario no se elimina automáticamente de la entidad de usuario del sistema CDS para evitar la interrupción de las aplicaciones empresariales que pueden ser críticas para las operaciones de la organización.  El administrador del sistema de CDS deberá tomar medidas para localizar y eliminar los datos personales de los usuarios de CDS mediante la aplicación.

Sólo los usuarios que tengan el rol de administrador global de Office 365 y el rol de seguridad de administrador del sistema de CDS pueden realizar las acciones Detectar, Descubrir, Exportar y Eliminar que se indican a continuación.

### <a name="discover"></a>Descubra

Los administradores del sistema pueden crear varias instancias de CDS.  Estas instancias se pueden usar para fines de prueba, desarrollo o de producción.   Cada una de estas instancias tiene una copia de la entidad de usuario del sistema con cualquier atributo personalizado que pueda haber agregado el administrador del sistema, así como los datos personales del usuario sincronizados desde el Centro de administración de Office 365.

Un administrador de sistema puede encontrar una lista de todas las instancias de CDS en el Centro de administración de Dynamics 365 desde el Centro de administración de PowerApps.

Desde el [Centro de administración de PowerApps](https://admin.powerapps.com/):

1.  Vaya a la pestaña Entornos.
2.  En la lista de entornos, seleccione uno.
3.  Haga clic en el vínculo Centro de administración de Dynamics 365.

    ![Detalles del entorno de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-environment-details.png)

    Se muestra una lista con todas las instancias.

    ![Selector de instancias de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-instance-picker.png)

Los datos personales de los usuarios de CDS se pueden encontrar aquí:

|Recursos que contienen datos personales | Propósito | Acceso al sitio web | Acceso mediante programación
| --- | --- | --- | ---
| Registro de entidad | Entidad del usuario del sistema | [Centro de administración de PowerApps](https://admin.powerapps.com) | [A través de la API web](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/webapi/update-delete-entities-using-web-api#basic-update)
| Historial de auditoría | Para permitir a los clientes identificar los recursos que los usuarios han creado, accedido, cambiado o eliminado a nivel de entidad. | [Centro de administración de PowerApps](https://admin.powerapps.com) | [A través de la API web](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/webapi/update-delete-entities-using-web-api#basic-update)

#### <a name="user"></a>Usuario
Los datos personales de los usuarios que se mantienen y administran en el Centro de administración de Office 365 se almacenan en Azure Active Directory.  Estos datos personales se administran en el Centro de administración de Office 365 y se sincronizan automáticamente con todos los entornos de CDS.  El administrador del sistema no puede actualizar estos datos personales directamente en CDS mientras el usuario está activo, sino que deben actualizarse directamente en el Centro de administración de Office 365.  Los datos personales adicionales (por ejemplo, atributos personalizados) pueden agregarse directamente a CDS y el administrador del sistema debe mantenerlos y administrarlos manualmente.

El administrador del sistema CDS puede localizar al usuario y buscar los datos personales asociados con un usuario determinado mediante estos pasos:

Desde el [Centro de administración de PowerApps](https://admin.powerapps.com/):

1.  Vaya a la pestaña Entornos.
2.  En la lista de entornos, seleccione uno.
3.  Haga clic en el vínculo Centro de administración de Dynamics 365.
4.  Haga clic en el nombre del entorno.
5.  Haga clic en el botón **Abrir**.
6.  Vaya a **Configuración** > **Seguridad**.
7.  Haga clic en **Usuarios**.
8.  Escriba el usuario en el cuadro de entrada de **búsqueda**.
9.  Haga clic en el botón **Buscar**.
10. Haga doble clic en el usuario.

    ![Formulario de usuario de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-user-form.png)

#### <a name="audit-history"></a>Historial de auditoría
Cuando [el seguimiento de auditoría está habilitado](https://docs.microsoft.com/dynamics365/customer-engagement/admin/audit-data-user-activity) para una entidad en Common Data Service, los datos personales del usuario se registran en el historial de auditoría junto con los eventos que el usuario estaba realizando.

### <a name="rectify"></a>Rectificar

Si el interesado le ha pedido que rectifique los datos personales que residen en los datos de su organización, usted y su organización tendrán que determinar si es apropiado cumplir con la solicitud.  La rectificación de los datos puede incluir la realización de acciones tales como la edición, redacción o eliminación de datos personales de un documento u otro tipo o elemento.

Puede usar Azure Active Directory para administrar identidades (datos personales) de los usuarios finales en Common Data Service for Apps. Los clientes empresariales tienen la capacidad de administrar las solicitudes de rectificación de DSR, incluidas las funciones de edición limitadas según la naturaleza de un determinado servicio de Microsoft.  Como procesador de datos, Microsoft no ofrece la capacidad de corregir los registros generados por el sistema porque reflejan actividades reales y constituyen un registro histórico de eventos dentro de los servicios de Microsoft. Consulte [GDPR: solicitudes de derechos del interesado (DSR)](https://servicetrust.microsoft.com/ViewPage/GDPRDSR) para más información.

Una vez que el registro de usuario se elimina de Azure Active Directory, los administradores del sistema pueden quitar cualquier dato personal restante de los usuarios (tales como atributos personalizados que se puedan haber agregado) de todas las instancias.  

### <a name="export"></a>Exportar

#### <a name="system-user"></a>Usuario del sistema
Los datos personales de los usuarios almacenados en la entidad de usuario del sistema se pueden exportar a Excel desde la lista de usuarios del portal.

Desde el [Centro de administración de PowerApps](https://admin.powerapps.com/):

1.  Vaya a la pestaña Entornos.
2.  En la lista de entornos, seleccione uno.
3.  Haga clic en el vínculo Centro de administración de Dynamics 365.
4.  Haga clic en el nombre del entorno.
5.  Haga clic en el botón Abrir. Vaya a Configuración > Seguridad.
6.  Seleccione la vista Usuarios habilitados.
7.  Haga clic en el botón Exportar a Excel.

#### <a name="audit-history"></a>Historial de auditoría
Las capturas de pantalla del historial de auditoría se pueden capturar y copiar desde la aplicación mediante los pasos que se indican a continuación.
En el [Centro de administración de PowerApps](https://admin.powerapps.com/),
1.  Vaya a la pestaña Entornos.
2.  En la lista de entornos, seleccione uno.
3.  Haga clic en el vínculo Centro de administración de Dynamics 365.
4.  Haga clic en el nombre del entorno.
5.  Haga clic en el botón Abrir.
6.  Vaya a Configuración > Auditoría.

    ![Menú Historial de auditoría de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-audit-history-menu.png)

7.  Haga clic en Vista de resumen de auditorías.
8.  Busque el registro de auditoría de usuario.

    ![Detalles del historial de auditoría de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-audit-history-details.png)

9.  Presione Alt-ImprPant para capturar la pantalla.
10. Guarde la captura de pantalla en un archivo.
11. Después, puede enviar el archivo al solicitante de DSR.

### <a name="delete"></a>Eliminar

#### <a name="user"></a>Usuario
Cuando se elimina un usuario del Centro de administración de Office 365, el estado del usuario se establece en Deshabilitado en CDS; sin embargo, los datos personales del usuario no se eliminan automáticamente para evitar la interrupción de las aplicaciones empresariales que pueden ser críticas para las operaciones de la organización.
Para eliminar los datos personales de los usuarios de CDS, el administrador del sistema debe quitar manualmente los datos personales del usuario deshabilitado.

#### <a name="remove-user-personal-data-via-user-form"></a>Quitar datos personales del usuario mediante el formulario de usuario
Cuando el registro de usuario se elimina de Azure Active Directory, se muestra el siguiente mensaje en el formulario de usuario.
Office 365 ya no administra la información de este usuario. Puede actualizar este registro para responder a las solicitudes de DSR mediante la eliminación o reemplazo de todos los datos personales asociados con este usuario.

En el [Centro de administración de PowerApps](https://admin.powerapps.com/),
1.  Vaya a la pestaña Entornos.
2.  En la lista de entornos, seleccione uno.
3.  Haga clic en el vínculo Centro de administración de Dynamics 365.
4.  Haga clic en el nombre del entorno.
5.  Haga clic en el botón **Abrir**.
6.  Haga clic en **Configuración** > **Seguridad** > **Usuarios**.
7.  Seleccione la vista **Usuarios habilitados**.
8.  Escriba el nombre de usuario en **Buscar registros** y haga clic en el botón **Buscar**.
9.  Haga doble clic en el nombre de usuario en los resultados de búsqueda.
10. Quite todos los datos personales y haga clic en **Guardar**.

#### <a name="remove-user-personal-data-via-excel-importexport"></a>Quitar los datos personales del usuario mediante la importación y exportación de Excel
1.  Haga clic en **Configuración** > **Seguridad** > **Usuarios**.
2.  Seleccione la vista **Usuarios habilitados**.
3.  Cree una plantilla de Excel con todas las columnas de datos personales del usuario que desea actualizar.
4.  Haga clic en **Descargar archivo**.
5.  Abra el archivo de Excel descargado, realice las actualizaciones y guarde el archivo.
6.  Vuelva a la ventana de vista de usuarios deshabilitados y haga clic en Importar datos.
7.  Elija el Excel actualizado en el cuadro de diálogo Cargar archivo de datos.
8.  Realice todos los cambios necesarios en la ventana Asignar campos.
9.  Haga clic en Siguiente y Enviar.

Consulte la [información adicional de Excel](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/admin/analyze-your-data-with-excel-templates) sobre el uso de plantillas de Excel.


#### <a name="remove-audit-history-via-the-audit-summary-view-form"></a>Quitar el historial de auditoría mediante el formulario Vista de resumen de auditorías

En el [Centro de administración de PowerApps](https://admin.powerapps.com/),
1.  Vaya a la pestaña Entornos.
2.  En la lista de entornos, seleccione uno.
3.  Haga clic en el vínculo Centro de administración de Dynamics 365.
4.  Haga clic en el nombre del entorno.
5.  Haga clic en el botón Abrir.
6.  Haga clic en Configuración > Auditoría.
7.  Seleccione Vista de resumen de auditorías.
8.  Buscar el historial de cambios realizados por el usuario
9.  Haga clic en la casilla de la fila o filas.
10. Haga clic en el icono Eliminar historial de cambios.

## <a name="personal-data-stored-in-common-data-service-for-apps-databases"></a>Datos personales almacenados en bases de datos de Common Data Service for Apps

### <a name="prerequisites"></a>Requisitos previos
Puede estar almacenando datos personales de usuarios (como sus propios clientes) en el contenido de las entidades de CDS.  

Cuando un usuario individual presenta una solicitud de DSR a su organización, el administrador del sistema de CDS necesitará localizar todas las entidades en las que el individuo podría estar referenciado dentro de su aplicación.  El administrador de CDS es responsable de mantener un inventario de dónde se almacenan los datos personales dentro de varias entidades que se están utilizando para poder responder a las solicitudes de DSR de los usuarios individuales.

Los datos personales dentro del contenido pueden exportarse, rectificarse o eliminarse en una entidad mediante la funcionalidad del producto.  

### <a name="discover"></a>Descubra
Cuando un administrador de CDS recibe una solicitud de DSR de un usuario, el administrador tendrá que identificar qué entornos o instancias de CDS contienen datos personales de ese usuario.  Debe desarrollar directivas y procedimientos para mantener un inventario de entornos, instancias y entidades en los que ha decidido almacenar datos personales de particulares para ayudarle a identificar los datos personales que ha almacenado dentro del contenido.

Mediante el inventario de entornos, instancias, entidades y campos en los que se almacenan datos personales, se puede configurar el motor de búsqueda de CDS para que descubra los datos personales.  Los administradores de CDS pueden configurar las entidades y los campos de búsqueda; consulte [Configurar la búsqueda por relevancia para la organización](https://go.microsoft.com/fwlink/?linkid=872506) para más información.
El administrador de CDS puede tener acceso entonces al entorno de CDS y realizar una búsqueda.

1.  Haga clic en el **icono de búsqueda**.
2.  Seleccione **Búsqueda por relevancia**

    ![Menú Búsqueda por relevancia de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-relevance-search-menu.png)

3.  Escriba los datos personales de la persona en el cuadro de búsqueda.
4.  Haga clic en el botón Buscar.

    ![Resultados de la búsqueda por relevancia de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-relevance-search-results.png)

Los datos personales del contenido se almacenan normalmente en las entidades clave, por ejemplo, cuenta, contacto, cliente potencial u oportunidad, entre otras, pero es su responsabilidad mantener un inventario de dónde se almacenan los datos personales de los usuarios individuales.

### <a name="rectify"></a>Rectificar
El administrador del sistema de CDS puede actualizar los datos personales de un usuario mediante la lista de resultados de la búsqueda por relevancia.  Sin embargo, es posible que también haya almacenado los datos personales de ese usuario en otras entidades personalizadas.  El administrador del sistema de CDS es responsable de mantener un inventario de estas otras entidades personalizadas y de realizar la actualización apropiada de los datos personales del individuo.

En los resultados de la búsqueda por relevancia:

1.  Haga clic en un elemento donde se encontraron datos personales del usuario.
2.  Actualice esos datos personales si procede.
3.  Haga clic en Guardar.

    ![Detalles de una cuenta de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-account-details.png)

### <a name="export"></a>Exportar
Se puede capturar una captura de pantalla de los datos y compartirla con el solicitante de DSR mediante los pasos que se describen a continuación.

En el [Centro de administración de PowerApps](https://admin.powerapps.com/),
1.  Vaya a la pestaña Entornos.
2.  En la lista de entornos, seleccione uno.
3.  Haga clic en el vínculo Centro de administración de Dynamics 365.
4.  Haga clic en el nombre del entorno.
5.  Haga clic en el **icono de búsqueda**.
6.  Seleccione Búsqueda por relevancia.
7.  Escriba los datos personales de la persona en el cuadro de búsqueda.
8.  Haga clic en el botón Buscar.
9.  Busque el elemento y haga doble clic en él.
10. Presione <alt> <PrtScn> para capturar la pantalla.
11. Guarde la captura de pantalla en un archivo.
12. Después, puede enviar el archivo al solicitante de DSR.

### <a name="delete"></a>Eliminar

El administrador de CDS puede eliminar los datos personales de un usuario de los registros donde se almacenan esos datos.  El administrador de CDS puede elegir entre (1) eliminar el registro donde se almacenan los datos personales o (2) quitar el contenido de los datos personales del registro.  

> [!NOTE]
> El administrador de CDS puede personalizar el entorno para evitar que un registro se elimine de una entidad. Si se configura de esta manera, tendrá que quitar el contenido de los datos personales del registro, en lugar de eliminar el mismo registro.

En los resultados de la búsqueda por relevancia,
1.  Haga clic en un elemento donde se encontraron datos personales del usuario.
2.  Haga clic en el icono Eliminar de la cinta (nota: este icono se deshabilita si el registro no se puede eliminar).

    ![Detalles de la cuenta de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-account-delete.png)

## <a name="personal-data-stored-in-common-data-service-previous-version-databases"></a>Datos personales almacenados en bases de datos de Common Data Service (versión anterior)

### <a name="prerequisites"></a>Requisitos previos

Puede estar almacenando datos personales de usuarios (como sus propios clientes o usuarios) en el contenido de las entidades de CDS.  

Cuando un usuario individual presenta una solicitud de DSR a su organización, el administrador del sistema de CDS necesitará localizar todas las entidades en las que el individuo podría estar referenciado dentro de su aplicación.  El administrador de CDS es responsable de mantener un inventario de dónde se almacenan los datos personales dentro de varias entidades que se están utilizando para poder responder a las solicitudes de DSR de los usuarios individuales.

Los datos personales dentro del contenido pueden exportarse, rectificarse o eliminarse en una entidad mediante la funcionalidad del producto.  

### <a name="discover"></a>Descubra
Cuando un administrador de CDS recibe una solicitud de DSR de un usuario, el administrador tendrá que identificar qué entornos o instancias de CDS contienen datos personales de ese usuario.  Debe desarrollar directivas y procedimientos para mantener un inventario de entornos, instancias y entidades en los que ha decidido almacenar datos personales de particulares para ayudarle a identificar los datos personales que ha almacenado dentro del contenido.

Los datos personales de los usuarios individuales se pueden encontrar aquí:

|Recursos que contienen datos personales | Propósito | Acceso al sitio web |    Acceso mediante programación
| --- | --- | --- | ---
|Registros de entidad | Capturar las transacciones de negocio en la entidad comercial correspondiente. | Portal de creadores de PowerApps |    No

#### <a name="entity-records"></a>Registros de entidad
Los datos personales individuales se pueden almacenar en cualquier entidad de negocio.
Esta versión de Common Data Service contiene su propio esquema e infraestructura de base de datos.  Tiene sus propias entidades y la administración de estas entidades se administra con el [sitio web de PowerApps](http://web.powerapps.com/).

Para ver una lista de entidades:

1.  Seleccione el entorno.

    ![Entidades heredadas de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities.png)

2.  Vaya a la pestaña **Datos** > **Entidades**.
3.  Seleccione la entidad, por ejemplo, la entidad Cuenta.

    ![Lista de detalles de las entidades heredadas de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities-details-list.png)

4.  Haga clic en la entidad.
5.  Haga clic en la pestaña **Datos**. Se mostrará una lista de registros de la entidad.

    ![Datos de la cuenta heredada de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-account-data.png)

6.  Haga clic en el icono **Exportar datos**.
7.  Abra la hoja de cálculo de Excel una vez completada la exportación.
8.  Haga clic en el cuadro Habilitar edición.
9.  Haga clic en el icono de encontrar y buscar.
10. Escriba la información personal que desee buscar.
Los datos personales del contenido se almacenan normalmente en las entidades clave, por ejemplo, cuenta, contacto, cliente potencial, oportunidad trabajo, entre otras, pero es su responsabilidad mantener un inventario de dónde se almacenan los datos personales de los usuarios individuales.
11. Con la lista de entidades de inventario donde se almacenan datos personales, **repita los pasos anteriores para que cada una de las entidades comerciales descubra los datos personales individuales**.

### <a name="rectify"></a>Rectificar
Si el interesado le ha pedido que rectifique los datos personales que residen en los datos de su organización, usted y su organización tendrán que determinar si es apropiado cumplir con la solicitud.  La rectificación de los datos puede incluir la realización de acciones tales como la edición, redacción o eliminación de datos personales de un documento u otro tipo o elemento.

Puede usar Azure Active Directory para administrar identidades (datos personales) de los usuarios finales en Common Data Service for Apps. Los clientes empresariales tienen la capacidad de administrar las solicitudes de rectificación de DSR, incluidas las funciones de edición limitadas según la naturaleza de un determinado servicio de Microsoft.  Como procesador de datos, Microsoft no ofrece la capacidad de corregir los registros generados por el sistema porque reflejan actividades reales y constituyen un registro histórico de eventos dentro de los servicios de Microsoft.  

Consulte [GDPR: solicitudes de derechos del interesado (DSR)](https://servicetrust.microsoft.com/ViewPage/GDPRDSR) para más información.

Para rectificar los datos personales que residen en el entorno de CDS, puede exportar los datos de la entidad a una hoja de cálculo de Excel, actualizarla e importar las actualizaciones a la base de datos.
El administrador de CDS es responsable de identificar todas las entidades en las que se almacenan los datos personales individuales y repetir los pasos siguientes para cada una de esas entidades.

Desde el [sitio web de PowerApps](http://web.powerapps.com/):

1.  Haga clic en **Datos** > **Entidades**.
2.  Haga clic en la entidad, por ejemplo, Cuenta.
3.  Haga clic en la opción **Datos**.
4.  Haga clic en el icono **Exportar datos**.
5.  Haga clic en el icono **Abrir en Excel** (cuando se realiza la exportación).
6.  **Habilite la edición** en la hoja de cálculo de Excel y asegúrese de actualizar los datos personales.
7.  **Guarde** la hoja de cálculo actualizada (utilice **Guardar como** para saber dónde se encuentra el archivo).

    ![Datos de la cuenta heredada de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-account-data.png)

8.  Realice las actualizaciones de los datos personales necesarias
9.  Guardar las actualizaciones
10. En el formulario Datos > Entidades > Cuenta, haga clic en el icono Importar datos.
11. Haga clic en el icono de búsqueda.
12. Elija el archivo que contiene las actualizaciones.
13. Haga clic en el cuadro Abrir.
14. Haga clic en el botón Importar.

### <a name="export"></a>Exportar

Puede ver y exportar datos personales de cada entidad a una hoja de trabajo de Excel.

Desde el [sitio web de PowerApps](http://web.powerapps.com/):

1.  Vaya a **Datos** > **Entidades**.
2.  Seleccione la **entidad** que desea ver y exporte los datos.
3.  Haga clic en la opción **Datos**.
4.  Haga clic en el icono **Exportar datos**. Esta operación de exportación se ejecuta en segundo plano y se le notificará cuando haya terminado.
5. Para ver los datos exportados, haga clic en el icono Abrir en Excel.

### <a name="delete"></a>Eliminar
Puede eliminar los datos personales que se almacenan en entidades mediante la funcionalidad Exportar/Importar datos.

El administrador de CDS es responsable de identificar todas las entidades que contienen los datos personales individuales y de repetir los pasos siguientes para cada una de esas entidades.

Desde el [sitio web de PowerApps](http://web.powerapps.com/):

1.  Haga clic en **Datos** > **Entidades**.
2.  Desplácese hacia abajo a la lista **Entidad** y ubique la entidad que desea quitar los datos personales.
3.  Haga clic en la entidad.
4.  Haga clic en la opción **Datos**.
5.  Haga clic en el icono **Exportar datos**.
6.  Haga clic en el icono **Abrir en Excel** (cuando se realiza la exportación).
7.  **Habilite la edición** en la hoja de cálculo de Excel.
8.  **Guarde** la hoja de cálculo actualizada (utilice Guardar como para saber dónde se encuentra el archivo).
9.  Elimine las filas de los registros de datos personales que desea quitar.
10. Guardar las actualizaciones
11. En el formulario **Entidades**, haga clic en el icono **Importar datos**.
12. Haga clic en el cuadro **Buscar**.
13. Elija el archivo que contiene las actualizaciones.
14. Haga clic en el cuadro **Abrir**.
15. Haga clic en el botón Importar.
