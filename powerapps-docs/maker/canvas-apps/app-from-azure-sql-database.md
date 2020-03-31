---
title: Crear una aplicación de lienzo desde Azure SQL Database | Microsoft Docs
description: Describe cómo crear una aplicación de lienzo a partir de los datos en Azure SQL Database
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/30/2020
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c17fff957091a13e26e4bbbb3bc90f34fa5659f7
ms.sourcegitcommit: 204d73f30be2fd63e13e3c64cbfa62b8d667df33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/31/2020
ms.locfileid: "80406086"
---
# <a name="preview-create-a-canvas-app-from-azure-sql-database"></a>Vista previa: cree una aplicación de lienzo desde Azure SQL Database

[Este tema es documentación preliminar y está sujeto a cambios.]

En este tema, usará los datos de la Azure SQL Database para crear una aplicación con Power Apps en solo unos minutos. Tendrá una aplicación totalmente funcional con los datos que puede personalizar para ajustarse a sus necesidades empresariales y compartir en cualquier dispositivo.

> [!IMPORTANT]
> - Esta es una característica en vista previa.
> - Una característica en versión preliminar puede tener una disponibilidad limitada y una funcionalidad restringida. Una característica en versión preliminar está disponible antes de una versión oficial para que los clientes puedan obtener acceso anticipado y proporcionar comentarios.

## <a name="prerequisites"></a>Requisitos previos

- El explorador debe tener habilitados los elementos emergentes.
- Necesita una suscripción de Azure. </br>Si no tiene una suscripción a Azure, [cree una cuenta gratuita](https://azure.microsoft.com/free/).
- Necesita acceso a un SQL Database existente. </br> Si no tiene un SQL Database existente, [cree una nueva base de datos](https://docs.microsoft.com/azure/sql-database/sql-database-single-database-get-started?tabs=azure-portal).
- Debe permitir que [las direcciones IP](#app-access-to-sql-database) de la región de Power Apps o los servicios de Azure tengan acceso a SQL Database en la configuración del firewall.
- La tabla SQL Database debe tener al menos una columna con el tipo de datos texto.

## <a name="create-an-app-from-azure-portal"></a>Crear una aplicación a partir de Azure Portal

> [!TIP]
> También puede crear una aplicación que use Azure SQL Database desde [Power apps](https://make.powerapps.com). Para obtener más información, lea [SQL Server Connector para Power apps](https://docs.microsoft.com/powerapps/maker/canvas-apps/connections/connection-azure-sqldatabase).

1. Inicie sesión en [Azure portal](https://portal.azure.com).
2. Navegue hasta el SQL Database.
3. Seleccione Power apps.
    
    ![Opción de Power Apps en SQL Database opciones](./media/app-from-azure-sql-database/powerapps-link-azure-portal.png "Opción de Power apps dentro de SQL Database")

4. Escriba un nombre para la aplicación como "inspección del sitio", "recaudador" o "seguimiento de presupuesto".

5. Escriba una contraseña de autenticación de SQL y, si es necesario, cambie el nombre de usuario.
    
    > [!NOTE]
    > Si desea usar Azure AD la autenticación integrada en lugar de la autenticación de SQL con Azure SQL Database, cree una aplicación desde [Power apps](https://make.powerapps.com) en su lugar y use [SQL Server Connector](https://docs.microsoft.com/powerapps/maker/canvas-apps/connections/connection-azure-sqldatabase).

6. Seleccione una tabla de la lista desplegable que desea usar para crear la aplicación.

7. Seleccione **Crear**.


    ![Especificar la información de la aplicación](./media/app-from-azure-sql-database/powerapps-create-page-azure-portal.png "Especificar la información de la aplicación")

    [Power apps Studio](https://create.powerapps.com/studio/) se abre en una nueva pestaña. Si el elemento emergente está bloqueado, actualice el explorador para permitir elementos emergentes e inténtelo de nuevo. Una vez creada, tendrá una aplicación de tres páginas con datos del SQL Database.

## <a name="accessing-your-app"></a>Acceder a la aplicación

Para acceder a la aplicación creada de nuevo, vaya a [make.powerapps.com](https://make.powerapps.com).

## <a name="app-environment-and-region"></a>Entorno y región de la aplicación

La aplicación que se crea con este método usa el [entorno predeterminado](https://docs.microsoft.com/power-platform/admin/environments-overview#the-default-environment) para el inquilino e implementa en la región de este entorno. Puede encontrar la región de una aplicación implementada o el entorno predeterminado de su inquilino desde el [centro de administración](https://docs.microsoft.com/power-platform/admin/regions-overview#how-do-i-find-out-where-my-app-is-deployed). Para revisar todas las aplicaciones de un entorno específico, vaya a [make.powerapps.com](https://make.powerapps.com), seleccione el **entorno** en la cinta de opciones y, a continuación, seleccione **aplicaciones** a la izquierda.

## <a name="app-access-to-sql-database"></a>Acceso de la aplicación a SQL Database

Puede configurar Power apps para que se conecte a SQL Database mediante direcciones IP o como un servicio de Azure.

### <a name="app-access-using-ip-address"></a>Acceso a la aplicación mediante la dirección IP

[Requisitos del sistema de Power apps](limits-and-config.md#ip-addresses) muestra las direcciones IP que usa Power Apps en función de la región de la aplicación.

Puede utilizar un procedimiento almacenado de Transact-SQL o el Azure Portal para configurar este acceso:

- [Sp_set_firewall_rule](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database?view=azuresqldb-current) de procedimientos almacenados para reglas de firewall de SQL Database o SQL Server
- [Azure portal](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure) para las reglas de firewall de SQL Server

### <a name="app-access-as-an-azure-service"></a>Acceso a la aplicación como un servicio de Azure

Power apps puede conectarse al SQL Database **permitir el acceso al control de servicios de Azure** mediante el Azure portal. Para configurar este acceso, inicie sesión en el [Azure portal](https://portal.azure.com/) y navegue en el portal hasta **SQL Server**. Seleccione **firewalls y redes virtuales** y establezca el control **permitir que los servicios y recursos de Azure tengan acceso a este servidor** **en activado**. Seleccione **Guardar** para enviar los cambios.

> [!IMPORTANT]
> Si deja el control establecido en activado, el servidor de Azure SQL Database acepta la comunicación desde cualquier subred dentro del límite de Azure, que se origina en una de las direcciones IP que se reconocen como las que se encuentran dentro de los intervalos definidos para los centros de datos de Azure. Si se mantiene el control establecido en ON, podría ser un acceso excesivo desde un punto de vista de seguridad.

## <a name="limitations"></a>Limitaciones

- El nombre de la aplicación solo puede incluir letras, números, guiones, paréntesis o caracteres de subrayado.
- La creación de una aplicación desde Azure Portal requiere la autenticación de SQL.
- Puede seleccionar solo una tabla mientras crea una aplicación de lienzo desde el Azure Portal. Personalice la aplicación después de crear la aplicación si desea agregar más tablas y otros orígenes de datos agregando más conexiones de datos.
- Power apps no se puede conectar a SQL Database mediante puntos de conexión de servicio de red virtual. Para obtener más información, consulte [permitir el acceso a través de puntos de conexión de servicio de red virtual](https://docs.microsoft.com/azure/sql-database/sql-database-vnet-service-endpoint-rule-overview).

## <a name="other-considerations"></a>Otras consideraciones

- El acceso de la aplicación a SQL Database se comparte implícitamente con todos los usuarios con los que se [comparte esta aplicación](share-app.md) . Asegúrese de que las credenciales de autenticación de SQL tienen el acceso adecuado para leer y escribir datos. </br> Por ejemplo, puede crear una aplicación independiente que se conecte al mismo SQL Database con distintas credenciales de autenticación de SQL para separar el acceso de lectura y escritura.
- Revise los límites de limitación, las funciones y operaciones que se deben delegar, los problemas conocidos y las limitaciones del conector de [SQL Database](https://docs.microsoft.com/connectors/sql/) que usa esta característica para las consideraciones de rendimiento.
- Cree una aplicación a partir de [make.powerapps.com](https://make.powerapps.com) cuando necesite crear una aplicación para un entorno no predeterminado y una región distinta para el inquilino con datos de SQL Database.

## <a name="next-steps"></a>Pasos siguientes

Como paso siguiente, use [Power apps](https://make.powerapps.com) Studio para personalizar la aplicación agregando controles, imágenes y lógica adicionales para satisfacer mejor sus necesidades empresariales.

> [!div class="nextstepaction"]
> [Diseño de la interfaz de la aplicación Canvas en Power apps](add-configure-controls.md)

## <a name="see-also"></a>Vea también

- [Compartir una aplicación de lienzo en Power apps](share-app.md) </br>
- [Agregar una conexión de datos a una aplicación de lienzo en Power apps](add-data-connection.md#add-data-source)</br>
- [Microsoft Learn: personalización de una aplicación de lienzo en Power apps](https://docs.microsoft.com/learn/modules/customize-apps-in-powerapps/)
