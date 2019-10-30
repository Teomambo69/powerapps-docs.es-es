---
title: Crear una aplicación de lienzo desde Azure SQL Database | Microsoft Docs
description: Describe cómo crear una aplicación de lienzo a partir de los datos en Azure SQL Database
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 10/29/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: dd5fbbd05ac021b2362c387de845c8a3e1eb33a8
ms.sourcegitcommit: 80a9f5073eefe8813f672569e452e6af9ee72d79
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/29/2019
ms.locfileid: "73050246"
---
# <a name="preview-create-a-canvas-app-from-azure-sql-database"></a>Vista previa: cree una aplicación de lienzo desde Azure SQL Database

[Este tema es documentación preliminar y está sujeto a cambios.]

En este tema, usará los datos de la Azure SQL Database para crear una aplicación con PowerApps en minutos. Tendrá una aplicación totalmente funcional con los datos que puede personalizar para ajustarse a sus necesidades empresariales y compartir en cualquier dispositivo.

> [!IMPORTANT]
> - Se trata de una característica de vista previa.
> - Una característica de vista previa puede tener una disponibilidad limitada y una funcionalidad restringida. Una característica de vista previa está disponible antes de una versión oficial para que los clientes puedan obtener acceso temprano y proporcionar comentarios.

## <a name="prerequisites"></a>Requisitos previos

- El explorador debe tener habilitados los elementos emergentes.
- Necesita una suscripción de Azure. </br>Si no tiene una suscripción a Azure, [cree una cuenta gratuita](https://azure.microsoft.com/free/).
- Necesita acceso a un SQL Database existente. </br> Si no tiene un SQL Database existente, [cree una nueva base de datos](https://docs.microsoft.com/azure/sql-database/sql-database-single-database-get-started?tabs=azure-portal).
- Debe permitir que [las direcciones IP](#app-access-to-sql-database) de la región de PowerApps o los servicios de Azure tengan acceso a SQL Database en la configuración del firewall.
- La tabla SQL Database debe tener al menos una columna con el tipo de datos texto.
- Necesita una licencia de PowerApps válida o regístrese para obtener una [licencia de prueba de 30 días](../signup-for-powerapps.md).

## <a name="create-an-app"></a>Crear una aplicación

1. Inicie sesión en el [portal de Azure](https://portal.azure.com).
2. Navegue hasta el SQL Database.
3. Seleccione PowerApps.

    
    ![Opción PowerApps en opciones de SQL Database](./media/app-from-azure-sql-database/powerapps-link-azure-portal.png "Opción de PowerApps dentro de SQL Database")

    > [!NOTE]
    > Si no tiene una licencia de PowerApps, verá una barra de información azul con un vínculo para iniciar una prueba. Cuando seleccione iniciar la evaluación, se le dirigirá a una nueva pestaña en la que se suscribirá para obtener una licencia. Una vez completado, vuelva al Azure Portal y actualice la hoja para continuar.

4. Escriba un nombre para la aplicación como "inspección del sitio", "recaudador de fondos" o "seguimiento de presupuesto".

5. Escriba la contraseña de autenticación de SQL y, si es necesario, cambie el nombre de usuario.
6. Seleccione una tabla de la lista desplegable que desea usar para crear la aplicación.

7. Seleccione **Crear**.


    ![Especificar la información de la aplicación](./media/app-from-azure-sql-database/powerapps-create-page-azure-portal.png "Especificar la información de la aplicación")

    El [PowerApps Studio](https://create.powerapps.com/studio/) se abre en una nueva pestaña. Si el elemento emergente está bloqueado, actualice el explorador para permitir elementos emergentes e inténtelo de nuevo. Una vez creada, tendrá una aplicación de tres páginas con datos del SQL Database.

## <a name="accessing-your-app"></a>Acceder a la aplicación

Para acceder a la aplicación creada de nuevo, vaya a [make.powerapps.com](https://make.powerapps.com).

## <a name="app-environment-and-region"></a>Entorno y región de la aplicación

La aplicación que se crea con este método usa el [entorno predeterminado](https://docs.microsoft.com/power-platform/admin/environments-overview#the-default-environment) para el inquilino e implementa en la región de este entorno. Puede encontrar la región de una aplicación implementada o el entorno predeterminado de su inquilino desde el [centro de administración](https://docs.microsoft.com/power-platform/admin/regions-overview#how-do-i-find-out-where-my-app-is-deployed). Para revisar todas las aplicaciones de un entorno específico, vaya a [make.powerapps.com](https://make.powerapps.com), seleccione el **entorno** en la cinta de opciones y, a continuación, seleccione **aplicaciones** a la izquierda.

## <a name="app-access-to-sql-database"></a>Acceso de la aplicación a SQL Database

Puede configurar PowerApps para conectarse a SQL Database mediante direcciones IP o como un servicio de Azure.

### <a name="app-access-using-ip-address"></a>Acceso a la aplicación mediante la dirección IP

[Requisitos del sistema de powerapps](limits-and-config.md#ip-addresses) enumera las direcciones IP que usa PowerApps en función de la región de la aplicación.

Puede utilizar un procedimiento almacenado de Transact-SQL o el Azure Portal para configurar este acceso:

- Procedimiento almacenado [sp_set_firewall_rule](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database?view=azuresqldb-current) para reglas de Firewall de nivel de SQL Database o SQL Server.
- [Azure portal](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure) para las reglas de Firewall de nivel de SQL Server.

### <a name="app-access-as-an-azure-service"></a>Acceso a la aplicación como un servicio de Azure

PowerApps puede conectarse a SQL Database **permitir el acceso al control de servicios de Azure** mediante el Azure portal. Para configurar este acceso, inicie sesión en el [Azure portal](https://portal.azure.com/) y navegue por el portal hasta **SQL Server**. Seleccione **firewalls y redes virtuales** y establezca el control **permitir que los servicios y recursos de Azure tengan acceso a este servidor** en activado. Seleccione **Guardar** para enviar los cambios.

> [!IMPORTANT]
> Si deja el control establecido en activado, el servidor de Azure SQL Database aceptará la comunicación desde cualquier subred dentro del límite de Azure, es decir, que se origine en una de las direcciones IP que se reconocen como las que se encuentran dentro de los intervalos definidos para los centros de datos de Azure. Si se mantiene el control establecido en ON, podría ser un acceso excesivo desde un punto de vista de seguridad.

## <a name="limitations"></a>Límite

- El nombre de la aplicación solo puede incluir una letra, un dígito, '-', ' (', ') ' o ' _ '.
- PowerApps requiere la autenticación de SQL para conectarse a SQL Database.
- Puede seleccionar solo una tabla al crear una aplicación de lienzo desde el Azure Portal. Personalice la aplicación después de crear la aplicación si desea agregar más tablas y otros orígenes de datos agregando más conexiones de datos.
- PowerApps no puede conectarse a SQL Database mediante puntos de conexión de servicio de red virtual. Para obtener más información, consulte [permitir el acceso a través de puntos de conexión de servicio de red virtual](https://docs.microsoft.com/azure/sql-database/sql-database-vnet-service-endpoint-rule-overview).

## <a name="other-considerations"></a>Otras consideraciones

- El acceso de la aplicación a SQL Database se comparte implícitamente con todos los usuarios con los que se [comparte esta aplicación](share-app.md) . Asegúrese de que las credenciales de autenticación de SQL tienen el acceso adecuado para leer y escribir datos. </br> Por ejemplo, puede crear una aplicación independiente que se conecte al mismo SQL Database con distintas credenciales de autenticación de SQL para separar el acceso de lectura y escritura.
- Revise los límites de limitación, las funciones y operaciones que se deben delegar, los problemas conocidos y las limitaciones del conector de [SQL Database](https://docs.microsoft.com/connectors/sql/) que esta característica utiliza para las consideraciones de rendimiento.
- Cree una aplicación a partir de [make.powerapps.com](https://make.powerapps.com) cuando necesite crear una aplicación para un entorno no predeterminado y una región distinta para el inquilino con datos de SQL Database.

## <a name="next-steps"></a>Pasos siguientes

En esta guía de inicio rápido, ha creado una aplicación con datos de su SQL Database mediante el Azure Portal. Como paso siguiente, personalice la aplicación con controles, imágenes y lógica para que se adapten mejor a sus necesidades empresariales.

> [!div class="nextstepaction"]
> [Diseño de la interfaz de la aplicación Canvas en PowerApps](add-configure-controls.md)

## <a name="see-also"></a>Vea también

- [Compartir una aplicación de lienzo en PowerApps](share-app.md) </br>
- [Incorporación de una conexión de datos a una aplicación de lienzo en PowerApps](add-data-connection.md#add-data-source)</br>
- [Microsoft Learn: personalización de una aplicación de lienzo en PowerApps](https://docs.microsoft.com/learn/modules/customize-apps-in-powerapps/)
