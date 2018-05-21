---
title: Respuesta a solicitudes DSR para datos de cliente de Common Data Service (CDS) for Apps | Microsoft Docs
description: Tutorial sobre cómo responder a solicitudes DSR para datos de cliente de Common Data Service (CDS) for Apps
author: jamesol-msft
ms.reviewer: paulliew
manager: kfile
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.date: 04/23/2018
ms.author: jamesol
ms.openlocfilehash: ef5d646e30f5d09dbfe5f111a3ad018b030f79d9
ms.sourcegitcommit: b3b6118790d6b7b4285dbcb5736e55f6e450125c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2018
---
# <a name="responding-to-data-subject-rights-dsr-requests-for-common-data-service-for-apps-customer-data"></a>Respuesta a solicitudes de derechos del interesado (DSR) sobre datos de cliente de Common Data Service for Apps

## <a name="introduction-to-dsr-requests"></a>Introducción a las solicitudes de DSR
El Reglamento general de protección de datos (RGPD) de la Unión Europea (UE) otorga derechos a las personas (denominadas *interesados* en el reglamento) para administrar los datos personales recopilados por un empleador u otro tipo de agencia u organización (denominado *poseedor de los datos* o simplemente *poseedor*). Los datos personales se definen de manera muy amplia en RGPD como cualquier dato que se refiera a una persona física identificada o identificable. El RGPD permite que los interesados hagan lo siguiente en cuanto a sus datos personales:

* Obtener copias
* Solicitar correcciones
* Restringir el procesamiento
* Eliminarlo
* Recibirlo en formato electrónico para poder moverlo a otro poseedor

Una solicitud formal realizada por un interesado al poseedor de los datos para que tome medidas en sus datos personales se denomina Solicitud de derechos del interesado (DSR).

En este artículo se describe cómo Microsoft se prepara para el RGPD y también se comparten ejemplos de los pasos que puede seguir como apoyo al cumplimiento del RGPD al usar PowerApps, Microsoft Flow y Common Data Service for Apps. Aprenderá a usar los productos, los servicios y las herramientas administrativas de Microsoft para ayudar a los clientes poseedores de los datos a buscar datos personales en la nube de Microsoft, acceder a ellos y actuar en ellos para responder a las solicitudes de DSR.

En este artículo se describen las acciones siguientes:

* **Descubrir**: usar herramientas de búsqueda y detección para encontrar más fácilmente los datos de cliente que pueden ser objeto de una solicitud DSR. Cuando se recopilan documentos potencialmente sensibles, puede realizar una o varias de las acciones de DSR siguientes para responder a la solicitud. Alternativamente, puede determinar que la solicitud no cumple con las directrices de la organización para responder a las solicitudes de DSR.

* **Acceso**: recuperar datos personales que residen en la nube de Microsoft y, si se solicita, hacer una copia de esos datos que pueda estar disponible para el interesado.

* **Rectificar**: realizar cambios o implementar otras acciones solicitadas sobre los datos personales, cuando corresponda.

* **Restringir**: restringir el procesamiento de datos personales, ya sea mediante la eliminación de licencias para varios servicios en línea o mediante la desactivación de los servicios deseados cuando sea posible. También puede quitar datos de la nube de Microsoft y conservarlos de manera local o en otra ubicación.

* **Eliminar**: quitar permanentemente los datos personales que residen en la nube de Microsoft.

* **Exportar**: proporcionar una copia electrónica (en formato legible por máquina) de los datos personales al interesado.

## <a name="cds-for-apps-customer-data"></a>CDS para datos de cliente de aplicaciones

> [!IMPORTANT]
> Se aplica tanto a CDS for Apps como a la versión anterior de Common Data Service

CDS for Apps y la versión anterior de Common Data Service (CDS) tienen proceso independientes para interactuar con los datos personales.

Para poder identificar qué tipo de entorno CDS tiene, inicie sesión en [PowerApps](https://web.powerapps.com) y siga estos pasos:

1. En la lista desplegable **Entorno**, seleccione el entorno.
2. En el panel de navegación, pulse o haga clic en **Datos** y, después, en **Entidades**.

    Si ve las siguientes entidades, el entorno es CDS for Apps:

    ![Lista de entidades de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-entities-list.png)

    Si ve las siguientes entidades, el entorno es la versión anterior de CDS:

    ![Lista de entidades heredadas de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities-list.png)

Una vez que determine qué tipo de entorno CDS tiene, siga los pasos de las secciones siguientes para identificar los datos personales.

> [!NOTE]
> Es posible que tenga algunos entornos en CDS for Apps y otros en la versión anterior de CDS, por lo que deberá repetir los procesos que se describen a continuación para cada entorno de su organización.

## <a name="user-personal-data-in-cds-for-apps"></a>Datos personales del usuario en CDS for Apps

### <a name="prerequisites"></a>Requisitos previos
Debe crear usuarios en el Centro de administración de Office 365 y asignarles un rol de seguridad y una licencia de usuario correspondiente antes de que puedan acceder a CDS for Apps y usarlo.

Los datos personales de usuario estándar (por ejemplo, nombre de usuario, identificador de usuario, teléfono, correo y dirección) se guardan y mantienen en el Centro de administración de Office 365. Los administradores del sistema pueden actualizar estos datos personales solo en el Centro de administración de Office 365 y, después, los datos se sincronizan automáticamente con la entidad de usuario del sistema CDS for Apps en todos los entornos. Los administradores del sistema también pueden crear atributos personalizados para capturar datos personales adicionales del usuario dentro de la entidad de usuario del sistema CDS for Apps y, luego, mantener y administrar manualmente estos atributos.

Para evitar la interrupción de las aplicaciones empresariales que pueden ser críticas para las operaciones de la organización, los registros de un usuario no se quitan automáticamente de la entidad de usuario del sistema CDS for Apps cuando se elimina ese usuario del Centro de administración de Office 365. El estado del usuario se establece en Deshabilitado en CDS for Apps, pero un administrador del sistema de CDS for Apps debe ubicar y quitar los datos personales del usuario de CDS for Apps dentro de la aplicación.

Solo los administradores globales de Office 365 y los administradores del sistema de CDS pueden realizar las acciones Detectar, Rectificar, Exportar y Eliminar que se indican a continuación.

### <a name="discover"></a>Descubra
Los administradores del sistema pueden crear varias instancias de CDS for Apps. Estas instancias se pueden usar para fines de prueba, desarrollo o de producción. Cada una de estas instancias tiene una copia de la entidad de usuario del sistema con cualquier atributo personalizado que pueda haber agregado el administrador del sistema, así como los datos personales del usuario sincronizados desde el Centro de administración de Office 365.

Los administradores del sistema pueden encontrar una lista de todas las instancias de CDS for Apps en el Centro de administración de Dynamics 365 desde el Centro de administración de PowerApps.

En el [Centro de administración de PowerApps](https://admin.powerapps.com/), haga lo siguiente:

1. En el panel de navegación, pulse o haga clic en **Entornos** y, después, seleccione un entorno de la lista.

3.  Pulse o haga clic en **Centro de administración de Dynamics 365**.

    ![Detalles del entorno de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-environment-details.png)

    Aparece una lista con todas las instancias.

    ![Selector de instancias de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-instance-picker.png)

Puede encontrar los datos personales de los usuarios de CDS for Apps dentro de los recursos siguientes:

|Recurso | Propósito | Acceso al sitio web | Acceso mediante programación
| --- | --- | --- | ---
| Registro de entidad | Conocido como la entidad de usuario del sistema, almacena los datos personales de un usuario. | [Centro de administración de PowerApps](https://admin.powerapps.com) | A través de la [API web](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/webapi/update-delete-entities-using-web-api#basic-update)
| Historial de auditoría | Permite a los clientes identificar los recursos que los usuarios crearon, accedieron, cambiaron o eliminaron a nivel de entidad. | [Centro de administración de PowerApps](https://admin.powerapps.com) | A través de la [API web](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/webapi/update-delete-entities-using-web-api#basic-update)

#### <a name="user"></a>Usuario
Los datos personales del usuario se almacenan en Azure Active Directory y se sincronizan automáticamente con todos los entornos CDS for Apps. Los administradores del sistema no pueden actualizar estos datos personales directamente en CDS for Apps mientras el usuario está activo&mdash;deben actualizarlos en el Centro de administración de Office 365. Los administradores del sistema pueden agregar datos personales (por ejemplo, atributos personalizados) directamente en CDS for Apps, pero deben administrarlos manualmente.

Para buscar un usuario y sus datos personales, vaya al [Centro de administración de PowerApps](https://admin.powerapps.com/) y haga lo siguiente:

1. En el panel de navegación, pulse o haga clic en **Entornos** y, después, seleccione un entorno de la lista.

2. Pulse o haga clic en **Centro de administración de Dynamics 365**, seleccione un entorno de la lista y, luego, pulse o haga clic en **Abrir**.

3. Vaya a **Configuración** > **Seguridad** > **Usuarios**.

4. Escriba el nombre del usuario en el cuadro de **búsqueda** y pulse o haga clic en **Buscar**.

5. Para ver los datos personales del usuario, haga doble clic o pulse dos veces en el nombre del usuario.

    ![Formulario de usuario de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-user-form.png)

#### <a name="audit-history"></a>Historial de auditoría
Cuando el [seguimiento de auditoría](https://docs.microsoft.com/dynamics365/customer-engagement/admin/audit-data-user-activity) está habilitado para una entidad en CDS for Apps, los datos personales de un usuario se registran en el historial de auditorías junto con las acciones que el usuario realiza.

### <a name="rectify"></a>Rectificar
Si el interesado le pide que rectifique los datos personales que residen en los datos de su organización, usted y su organización tienen que determinar si es apropiado cumplir con la solicitud. La rectificación de los datos puede incluir la edición, redacción o eliminación de datos personales de un documento u otro tipo o elemento.

Puede usar Azure Active Directory para administrar las identidades (datos personales) de los usuarios dentro de CDS for Apps. Los clientes empresariales pueden administrar las solicitudes de rectificación DSR mediante el uso de las características de edición limitadas dentro de un servicio Microsoft determinado. Como procesador de datos, Microsoft no ofrece la capacidad de corregir los registros generados por el sistema porque reflejan actividades reales y constituyen un registro histórico de eventos dentro de los servicios de Microsoft. Consulte [GDPR: Data Subject Requests (DSRs)](https://servicetrust.microsoft.com/ViewPage/GDPRDSR) (RGPD: solicitudes de derechos del interesado [DSR]) para más información.

Una vez que el registro de un usuario se elimina de Azure Active Directory, los administradores del sistema pueden quitar cualquier dato personal restante relacionado con ese usuario (como los atributos personalizados) de todas las instancias.  

### <a name="export"></a>Exportar

#### <a name="system-user"></a>Usuario del sistema
Puede exportar los datos personales de un usuario almacenados en la entidad de usuario del sistema a Excel desde la lista de usuarios dentro del centro de administración.

En el [Centro de administración de PowerApps](https://admin.powerapps.com/), haga lo siguiente:

1. En el panel de navegación, pulse o haga clic en **Entornos** y, después, seleccione un entorno de la lista.

2. Pulse o haga clic en **Centro de administración de Dynamics 365**, seleccione un entorno de la lista y, luego, pulse o haga clic en **Abrir**.

3. Vaya a **Configuración** > **Seguridad** y, luego, seleccione **Enabled Users View** (Vista de usuarios habilitados).

4. Haga clic en **Exportar a Excel**.

#### <a name="audit-history"></a>Historial de auditoría
Puede tomar capturas de pantalla del historial de auditoría desde el centro de administración.

En el [Centro de administración de PowerApps](https://admin.powerapps.com/), haga lo siguiente:

1. En el panel de navegación, pulse o haga clic en **Entornos** y, después, seleccione un entorno de la lista.

2. Pulse o haga clic en **Centro de administración de Dynamics 365**, seleccione un entorno de la lista y, luego, pulse o haga clic en **Abrir**.

3. Vaya a **Configuración** > **Auditoría** y seleccione **Vista de resumen de auditorías**.

    ![Menú Historial de auditoría de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-audit-history-menu.png)

4. Ubique el registro de auditoría del usuario y presione Alt+ImprPant para tomar la captura de pantalla.

    ![Detalles del historial de auditoría de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-audit-history-details.png)

5. Guarde la captura de pantalla en un archivo, el que luego puede enviar al solicitante de DSR.

### <a name="delete"></a>Eliminar

#### <a name="user"></a>Usuario
Para evitar la interrupción de las aplicaciones empresariales que pueden ser críticas para las operaciones de la organización, los registros de un usuario no se quitan automáticamente de la entidad de usuario del sistema CDS for Apps cuando se elimina ese usuario del Centro de administración de Office 365. El estado del usuario se establece en Deshabilitado en CDS for Apps, pero un administrador del sistema de CDS for Apps debe ubicar y quitar los datos personales del usuario de CDS for Apps dentro de la aplicación.

#### <a name="remove-a-users-personal-data-from-the-users-summary-page"></a>Eliminación de los datos personales de un usuario de la página Resumen del usuario
Cuando el registro de un usuario se elimina de Azure Active Directory, aparece el mensaje siguiente en la página Resumen del usuario:

*Office 365 ya no administra la información de este usuario. Puede actualizar este registro para responder a las solicitudes de DSR mediante la eliminación o reemplazo de todos los datos personales asociados con este usuario.*

En el [Centro de administración de PowerApps](https://admin.powerapps.com/), haga lo siguiente:

1. En el panel de navegación, pulse o haga clic en **Entornos** y, después, seleccione un entorno de la lista.

2. Pulse o haga clic en **Centro de administración de Dynamics 365**, seleccione un entorno de la lista y, luego, pulse o haga clic en **Abrir**.

3. Vaya a **Configuración** > **Seguridad** > **Usuarios** y seleccione **Disabled Users View** (Vista de usuarios deshabilitados).

4. Escriba el nombre del usuario en el cuadro de **búsqueda** y pulse o haga clic en **Buscar**.

9. Haga doble clic en el nombre del usuario en la lista de resultados de la búsqueda.

10. En la página Resumen del usuario, quite todos los datos personales y pulse o haga clic en **Guardar**.

#### <a name="remove-a-users-personal-data-by-using-excel"></a>Eliminación de los datos personales de un usuario mediante Excel
En el [Centro de administración de PowerApps](https://admin.powerapps.com/), haga lo siguiente:

1. En el panel de navegación, pulse o haga clic en **Entornos** y, después, seleccione un entorno de la lista.

2. Pulse o haga clic en **Centro de administración de Dynamics 365**, seleccione un entorno de la lista y, luego, pulse o haga clic en **Abrir**.

3. Vaya a **Configuración** > **Seguridad** > **Usuarios** y seleccione **Disabled Users View** (Vista de usuarios deshabilitados).

4. Cree y descargue un archivo de plantilla de Excel de los datos personales del usuario. Consulte [Crear plantilla de Excel nueva](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/admin/analyze-your-data-with-excel-templates#create-a-new-excel-template) para instrucciones detalladas.

8. Abra el archivo de plantilla de Excel que descargó, quite los datos personales del usuario y guarde el archivo.

9. Vuelva a la página **Disabled Users View** (Vista de usuarios deshabilitados) y pulse o haga clic en **Importar datos**.

10. Seleccione el archivo de plantilla de Excel en el cuadro de diálogo **Cargar archivo de datos** y haga todos los cambios necesarios en la ventana **Asignar campos**.

12. Haga clic o pulse **Siguiente** y pulse o haga clic en **Enviar**.

#### <a name="remove-audit-history-from-the-audit-summary-view-page"></a>Eliminación del historial de auditoría de la página Vista de resumen de auditorías
En el [Centro de administración de PowerApps](https://admin.powerapps.com/), haga lo siguiente:

1. En el panel de navegación, pulse o haga clic en **Entornos** y, después, seleccione un entorno de la lista.

2. Pulse o haga clic en **Centro de administración de Dynamics 365**, seleccione un entorno de la lista y, luego, pulse o haga clic en **Abrir**.

3. Vaya a **Configuración** > **Auditoría** y seleccione **Vista de resumen de auditorías**.

4. Ubique el historial de cambios del usuario, pulse o haga clic en la casilla de verificación junto a las filas y pulse o haga clic en **Eliminar historial de cambios**.

## <a name="personal-data-stored-in-databases-of-cds-for-apps"></a>Datos personales almacenados en bases de datos de CDS for Apps

### <a name="prerequisites"></a>Requisitos previos
Puede estar almacenando datos personales de usuarios (como sus propios clientes) dentro de las entidades de CDS for Apps.  

Los administradores del sistema CDS son responsables de mantener un inventario de dónde se almacenan los datos personales dentro de varias entidades para cada usuario, de manera que pueda ubicar esos datos para responder cualquier solicitud de DSR.  

Los datos personales se pueden exportar, rectificar o eliminar en una entidad mediante la funcionalidad del producto.  

### <a name="discover"></a>Descubra
Cuando los administradores del sistema CDS reciben una solicitud de DSR de un usuario, deben identificar qué entornos o instancias de CDS contienen datos personales de ese usuario. Los datos personales se suelen almacenar en entidades clave (por ejemplo, Cuenta, Contacto, Cliente potencial, Oportunidad, etc.), pero es su responsabilidad desarrollar directivas y procedimientos para mantener un inventario de dónde almacena los datos personales de cada usuario para estar preparado para responder las solicitudes de DSR.

Con un inventario, los administradores del sistema CDS pueden configurar los campos y las entidades de búsqueda y luego acceder al entorno CDS for Apps para detectar los datos personales. Para más información, consulte [Configurar la búsqueda por relevancia para la organización](https://go.microsoft.com/fwlink/?linkid=872506).

En el [Centro de administración de PowerApps](https://admin.powerapps.com/), haga lo siguiente:

1. En el panel de navegación, pulse o haga clic en **Entornos** y, después, seleccione un entorno de la lista.

2. Pulse o haga clic en **Centro de administración de Dynamics 365**, seleccione un entorno de la lista, pulse o haga clic en el botón de búsqueda y, luego, pulse o haga clic en **Búsqueda por relevancia**.

    ![Menú Búsqueda por relevancia de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-relevance-search-menu.png)

3. Escriba los datos personales del usuario en el cuadro de búsqueda y pulse o haga clic en **Buscar**.

    ![Resultados de la búsqueda por relevancia de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-relevance-search-results.png)

### <a name="rectify"></a>Rectificar
Los administradores del sistema CDS pueden actualizar los datos personales de un usuario mediante la lista de resultados de la búsqueda por relevancia. Sin embargo, los datos personales de un usuario también se pueden almacenar en otras entidades personalizadas. Los administradores del sistema CDS son responsables de mantener un inventario de estas otras entidades personalizadas y de realizar las actualizaciones apropiadas de los datos personales del individuo.

En los resultados de la búsqueda por relevancia:

1. Pulse o haga clic en un elemento que contenga los datos personales del usuario.

2. Actualice los datos personales del usuario cuando corresponda y pulse o haga clic en **Guardar**.

    ![Detalles de una cuenta de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-account-details.png)

### <a name="export"></a>Exportar
Puede tomar una captura de pantalla de los datos y compartirla con el solicitante de DSR.

En el [Centro de administración de PowerApps](https://admin.powerapps.com/), haga lo siguiente:

1. En el panel de navegación, pulse o haga clic en **Entornos** y, después, seleccione un entorno de la lista.

2. Pulse o haga clic en **Centro de administración de Dynamics 365**, seleccione un entorno de la lista, pulse o haga clic en el botón de búsqueda y, luego, pulse o haga clic en **Búsqueda por relevancia**.

    ![Menú Búsqueda por relevancia de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-relevance-search-menu.png)

3. Escriba los datos personales del usuario en el cuadro de búsqueda y pulse o haga clic en **Buscar**.

    ![Resultados de la búsqueda por relevancia de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-relevance-search-results.png)

4. Haga doble clic en el elemento en la lista de resultados de la búsqueda.

5. Presione Alt+ImprPant para tomar la captura de pantalla.

6. Guarde la captura de pantalla en un archivo, el que luego puede enviar al solicitante de DSR.

### <a name="delete"></a>Eliminar
Los administradores del sistema CDS pueden eliminar los datos personales de un usuario de los registros donde se almacenan esos datos.  El administrador del sistema CDS puede elegir entre eliminar el registro donde se almacenan los datos personales o quitar el contenido de los datos personales del registro.  

> [!NOTE]
> Los administradores de CDS pueden personalizar un entorno para evitar que un registro se elimine de una entidad. Si se configura de esta manera, tendrá que quitar el contenido de los datos personales del registro, en lugar de eliminar el registro mismo.

En los resultados de la búsqueda por relevancia:

1. Pulse o haga clic en un elemento que contenga los datos personales del usuario.

2. En la cinta de opciones, pulse o haga clic en **Eliminar**. (Observe que la opción **Eliminar** está deshabilitada si no se puede eliminar el registro).

    ![Detalles de la cuenta de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-account-delete.png)

## <a name="personal-data-stored-in-databases-of-the-previous-version-of-cds"></a>Datos personales almacenados en bases de datos de la versión anterior de CDS

### <a name="prerequisites"></a>Requisitos previos
Puede estar almacenando datos personales de usuarios (como sus propios clientes) dentro de las entidades de CDS.  

Los administradores del sistema CDS son responsables de mantener un inventario de dónde se almacenan los datos personales dentro de varias entidades para cada usuario, de manera que pueda ubicar esos datos para responder cualquier solicitud de DSR.  

Los datos personales se pueden exportar, rectificar o eliminar en una entidad mediante la funcionalidad del producto.  

### <a name="discover"></a>Descubra
Cuando los administradores del sistema CDS reciben una solicitud de DSR de un usuario, deben identificar qué entornos o instancias de CDS contienen datos personales de ese usuario. Los datos personales se suelen almacenar en entidades clave (por ejemplo, Cuenta, Contacto, Cliente potencial, Oportunidad, etc.), pero es su responsabilidad desarrollar directivas y procedimientos para mantener un inventario de dónde almacena los datos personales de cada usuario para estar preparado para responder las solicitudes de DSR.

Puede encontrar los datos personales de los usuarios de la versión anterior de CDS dentro de los recursos siguientes:

|Recurso | Propósito | Acceso al sitio web |  Acceso mediante programación
| --- | --- | --- | ---
|Registros de entidad | Captura las transacciones comerciales en la entidad de negocio correspondiente. | [PowerApps](https://web.powerapps.com) |      No

#### <a name="entity-records"></a>Registros de entidad
Los datos personales de un usuario se pueden almacenar en cualquier entidad de negocio.

Esta versión de CDS contiene su propio esquema e infraestructura de base de datos. Tiene sus propias entidades y las administra en [PowerApps](http://web.powerapps.com/).

Para ver una lista de sus entidades:

1. En la lista desplegable **Entorno**, seleccione el entorno.

2. En el panel de navegación, pulse o haga clic en **Datos** y, después, en **Entidades**.

    ![Entidades heredadas de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities.png)

3. En la lista de entidades, pulse o haga clic en una entidad (por ejemplo, la entidad Cuenta), como se muestra a continuación.

    ![Lista de detalles de las entidades heredadas de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities-details-list.png)

4. Pulse o haga clic en la pestaña **Datos**. Aparece una lista de los registros de la entidad.

    ![Datos de la cuenta heredada de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-account-data.png)

5. Pulse o haga clic en **Exportar datos**.

6. Una vez que se complete la exportación, pulse o haga clic en **Abrir en Excel** y, luego, en **Habilitar edición**.

7. Pulse o haga clic en el botón de búsqueda, escriba los datos personales del usuario en él y pulse o haga clic en **Buscar**.

8. Con la lista de inventario, repita los pasos anteriores para cada una de las entidades de negocio a fin de detectar todos los datos personales del usuario.

### <a name="rectify"></a>Rectificar
Si el interesado le pide que rectifique los datos personales que residen en los datos de su organización, usted y su organización tienen que determinar si es apropiado cumplir con la solicitud. La rectificación de los datos puede incluir la edición, redacción o eliminación de datos personales de un documento u otro tipo o elemento.

Puede usar Azure Active Directory para administrar las identidades (datos personales) de los usuarios dentro de la versión anterior de CDS. Los clientes empresariales pueden administrar las solicitudes de rectificación DSR mediante el uso de las características de edición limitadas dentro de un servicio Microsoft determinado. Como procesador de datos, Microsoft no ofrece la capacidad de corregir los registros generados por el sistema porque reflejan actividades reales y constituyen un registro histórico de eventos dentro de los servicios de Microsoft. Consulte [GDPR: Data Subject Requests (DSRs)](https://servicetrust.microsoft.com/ViewPage/GDPRDSR) (RGPD: solicitudes de derechos del interesado [DSR]) para más información.

Para rectificar los datos personales que residen en el entorno de CDS, puede exportar los datos de la entidad a una hoja de cálculo de Excel, actualizarla e importar las actualizaciones a la base de datos.

Los administradores del sistema CDS son responsables de identificar todas las entidades que contienen los datos personales de un usuario y de repetir los pasos siguientes para cada una de esas identidades.

En [PowerApps](http://web.powerapps.com/):

1. En el panel de navegación, pulse o haga clic en **Datos** y, después, en **Entidades**.

    ![Entidades heredadas de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities.png)

2. En la lista de entidades, pulse o haga clic en una entidad (por ejemplo, la entidad Cuenta), como se muestra a continuación.

    ![Lista de detalles de las entidades heredadas de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities-details-list.png)

3. Pulse o haga clic en la pestaña **Datos**. Aparece una lista de los registros de la entidad.

    ![Datos de la cuenta heredada de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-account-data.png)

4. Pulse o haga clic en **Exportar datos**.

5. Una vez que se complete la exportación, pulse o haga clic en **Abrir en Excel** y, luego, en **Habilitar edición**.

6. En la barra de menús, pulse o haga clic en **Archivo**, en **Guardar como** y seleccione una ubicación en la que guardará el archivo.

7. Haga las actualizaciones necesarios de los datos personales y guarde la hoja de cálculo.

10. En PowerApps, vuelva a la pestaña **Datos** de la entidad y pulse o haga clic en **Importar datos**.

11. Haga clic en **Buscar** y seleccione y abra la hoja de cálculo de Excel que acaba de actualizar.

12. Haga clic en **Importar**.

### <a name="export"></a>Exportar
Puede exportar datos personales de cada entidad a una hoja de cálculo de Excel para verla.

En [PowerApps](http://web.powerapps.com/):

1. En el panel de navegación, pulse o haga clic en **Datos** y, después, en **Entidades**.

    ![Entidades heredadas de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities.png)

2. En la lista de entidades, pulse o haga clic en la entidad que quiere exportar y ver (por ejemplo, la entidad Cuenta), como se muestra a continuación.

    ![Lista de detalles de las entidades heredadas de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities-details-list.png)

3. Pulse o haga clic en la pestaña **Datos**. Aparece una lista de los registros de la entidad.

    ![Datos de la cuenta heredada de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-account-data.png)

4. Pulse o haga clic en **Exportar datos**.

    La operación de exportación se ejecuta en segundo plano y se le notificará cuando se haya completado.

5. Para ver los datos exportados, pulse o haga clic en **Abrir en Excel**.

### <a name="delete"></a>Eliminar
Puede eliminar los datos personales que están almacenados en entidades mediante la característica Exportar/Importar datos.

Los administradores del sistema CDS son responsables de identificar todas las entidades que contienen los datos personales de un usuario y de repetir los pasos siguientes para cada una de esas identidades.

En [PowerApps](http://web.powerapps.com/):

1. En el panel de navegación, pulse o haga clic en **Datos** y, después, en **Entidades**.

    ![Entidades heredadas de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities.png)

2. En la lista de entidades, pulse o haga clic en la entidad de la que quiere quitar los datos personales (por ejemplo, la entidad Cuenta), como se muestra a continuación.

    ![Lista de detalles de las entidades heredadas de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-entities-details-list.png)

3. Pulse o haga clic en la pestaña **Datos**. Aparece una lista de los registros de la entidad.

    ![Datos de la cuenta heredada de PowerApps](./media/common-data-service-gdpr-dsr-guide/powerapps-legacy-account-data.png)

4. Pulse o haga clic en **Exportar datos**.

5. Una vez que se complete la exportación, pulse o haga clic en **Abrir en Excel** y, luego, en **Habilitar edición**.

6. En la barra de menús, pulse o haga clic en **Archivo**, en **Guardar como** y seleccione una ubicación en la que guardará el archivo.

7. Elimine las filas que contienen los datos personales que quiere quitar de la entidad y guarde la hoja de cálculo.

10. En PowerApps, vuelva a la pestaña **Datos** de la entidad y pulse o haga clic en **Importar datos**.

11. Haga clic en **Buscar** y seleccione y abra la hoja de cálculo de Excel que acaba de actualizar.

12. Haga clic en **Importar**.