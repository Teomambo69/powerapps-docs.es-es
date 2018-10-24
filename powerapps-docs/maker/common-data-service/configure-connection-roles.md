---
title: Configuración de roles de conexión | Microsoft Docs
ms.custom: ''
ms.date: 05/27/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
ms.author: matp
manager: brycho
ms.openlocfilehash: 4faf195f1c751e3796267d52725c1cb753c4889d
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39710922"
---
# <a name="configure-connection-roles"></a>Configuración de roles de conexión

Con Common Data Service (CDS) for Apps es posible definir **conexiones** entre registros de entidad sin necesidad de crear una relación entre entidades. En las aplicaciones controladas por modelos, los usuarios pueden establecer un vínculo con nombre entre registros para establecer una relación menos formal que no justifique la creación de una relación entre entidades real. Algunos ejemplos son *Amigo*, *Del mismo nivel*, *Cónyuge*, *Asistente* y *Parte interesada*. Algunas conexiones también pueden ser recíprocas, como *Elemento secundario* y *Elemento primario*, *Marido* y *Esposa*, o *Médico* y *Paciente*.

Cuando los usuarios establecen una conexión entre dos registros, también pueden agregar una descripción e información adicional, como las fechas de inicio y finalización de la relación. Más información: [Creación de conexiones para definir y ver las relaciones entre registros](/dynamics365/customer-engagement/basics/create-connections-view-relationships-between-records)

Cualquiera con acceso de escritura a la entidad **Rol de conexión** puede establecer qué conexión estará disponible para los usuarios.

## <a name="view-connection-roles"></a>Visualización de roles de conexión

Hay numerosos roles de conexión estándar ya configurados en CDS for Apps. Para verlos, debe ir al área de configuración. 

### <a name="navigate-to-the-settings-area"></a>Desplazamiento al área de configuración

1. Mientras visualiza una aplicación controlada por modelos, edite la URL para quitar todo lo que va después de `dynamics.com` y actualice la página.
1. Vaya a **Configuración** > **Empresa** > **Administración de empresas** y, a continuación, seleccione **Roles de conexión**.

![Roles de conexión en la configuración de Administración de empresas](media/navigate-settings-connection-roles.png)

En esta vista puede ver todos los roles de conexión que están disponibles para este entorno y puede editarlos ahí mismo.

> [!NOTE]
> Si desea distribuir los roles de conexión con una solución, asegúrese de que se incluyan en la solución que desea distribuir. Más información: [Adición de roles de conexión a una solución](#add-connection-roles-to-a-solution)

## <a name="view-connection-roles-in-the-solution-explorer"></a>Vea los roles de conexión en el Explorador de soluciones.

Dado que los roles de conexión son *compatibles con las soluciones*, lo que significa que pueden incluirse en una solución, también puede agregar roles de conexión a una solución que distribuya.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

La mayoría de los roles de conexión que puede ver en el área **Configuración** se definen en la **solución predeterminada** *interna* (no debe confundirse con la **solución predeterminada de Common Data Services**). Esta **solución predeterminada** interna contiene todas las personalizaciones del sistema. Para ver la **solución predeterminada**, seleccione la vista **Todas las soluciones - Interna**.

## <a name="add-connection-roles-to-a-solution"></a>Adición de roles de conexión a una solución

Por lo general, no se recomienda editar los componentes en la **solución predeterminada** interna. En la **solución predeterminada de Common Data Services** o cualquier otra que haya creado para trabajar con ella, puede usar el comando **Agregar existente** para mover cualquiera de los roles de conexión predeterminados a su solución.

![Adición de un rol de conexión existente](media/add-existing-connection-role.png)

Una vez que agregue el rol de conexión a la solución, se puede editar siempre que sea visible.

## <a name="create-or-edit-connection-roles"></a>Creación o edición de roles de conexión

> [!IMPORTANT]
> Si va a distribuir una solución que incluye nuevos roles de conexión o los cambios realizados en los existente, debe agregarlos a la solución que se va a distribuir. Si edita o agrega nuevos roles de conexión con el área **Configuración**, estos roles de conexión se agregarán a la **solución predeterminada** interna y no se incluirán en la solución que se va a distribuir, a menos que primero los agregue a la solución. Más información: [Adición de roles de conexión a una solución](#add-connection-roles-to-a-solution)

En la lista **Roles de conexión**, seleccione uno de los roles de conexión para editarlo.
Hay tres pasos para definir un rol de conexión que se indican claramente en el formulario.

![Creación del formulario Rol de conexión](media/create-connection-role-form.png)

### <a name="describe-the-connection-role"></a>Descripción del rol de conexión

Establezca los siguientes campos:

|Campo|Descripción|
|--|--|
|**Nombre**|(Obligatorio) El texto que describe la conexión.|
|**Categoría**|Un grupo que describe la categoría de la conexión. Más información: [Valores de la categoría de rol de conexión](#connection-role-category-values)|
|**Description**|Proporcione una definición al rol.|

#### <a name="connection-role-category-values"></a>Valores de la categoría de rol de conexión

Los valores predeterminados de **Categoría** son los siguientes:
- Business
- Family
- Social
- Ventas
- Otros
- Parte interesada
- Equipo de ventas
- Servicio

Puede agregar nuevas categorías o modificar las existentes editando el conjunto de opciones globales de **Categoría**. Más información: [Creación y edición de conjuntos de opciones globales de Common Data Service for Apps (listas desplegables)](create-edit-global-option-sets.md)

### <a name="select-record-types"></a>Selección de tipos de registro

Seleccione los tipos de registros que deben estar disponibles para conectarse.

> [!NOTE]
> Aunque la opción **Todo** está activada de forma predeterminada, tenga en cuenta qué tipos son los adecuados para el rol de conexión que va a agregar.

### <a name="matching-connection-roles"></a>Roles de conexión coincidentes

En este paso opcional, puede definir los roles que se aplicarán de manera recíproca. Aunque no es necesario, las conexiones tienen más sentido si se definen.

Por ejemplo, pueden establecer que Glen sea *amigo* de Mary, pero ¿significa esto que Mary es *amiga* de Glen? Esperemos que sí. Sin embargo, si Glen es el *padre* de Mary, no significa que Mary sea la *madre* de Glen. Para establecer la reciprocidad correcta, hay que seguir este paso adicional.

Cuando los usuarios establecen un rol de conexión que no tiene un rol de conexión coincidente, el rol solo se mostrará al ver la conexión del registro al que se aplicó la conexión. Cuando se ve desde el registro conectado, el rol estará vacío, a menos que se establezca un rol coincidente.

Para las definiciones de roles como *Amigo*, *Cónyuge*, *Compañero* o *Del mismo nivel*, resulta más conveniente asignar el rol coincidente a sí mismo. Si se configura un solo rol de conexión coincidente, se aplicará ese único rol de conexión coincidente en ambas direcciones.

> [!IMPORTANT]
> Deberá guardar un nuevo rol de conexión sin este rol de conexión coincidente antes de establecer el rol de conexión coincidente a sí mismo.

Se percatará de que algunos roles de conexión ya están configurados con los roles de conexión coincidentes. *Antiguo empleado* coincide con *Contratador anterior*, y viceversa. Este tipo de rol de conexión coincidente uno a uno es el más común.

Puede configurar varios roles de conexión coincidentes para describir relaciones complejas. Si crea un rol de conexión como *Padre*, podría configurar dos roles más, como *Hija* e *Hijo*, y aplicar ambos como roles de conexión coincidentes en *Padre*. A su vez, los roles de conexión *Hija* e *Hijo* deben asociarse a *Padre*. Por supuesto, después debe configurar un rol equivalente para *Madre* del mismo modo que se haría con *Hija* e *Hijo*.

> [!TIP]
> Antes de crear un conjunto complejo de roles de conexión, considere si bastaría con un conjunto de roles más simple. Por ejemplo, en lugar de crear un conjunto complejo de roles de conexión como *Padre*, *Madre*, *Hijo* e *Hija*, tenga en cuenta si simplemente bastaría con *Elemento primario* y *Elemento secundario*.

Si se configura más de un rol de conexión coincidente, esos roles de conexión representan solo las funciones recíprocas válidas. La primera de ellas se aplicará automáticamente como valor predeterminado. Si el valor predeterminado no es correcto, los usuarios deben editar la conexión manualmente y elegir entre las opciones válidas definidas en la configuración.

### <a name="see-also"></a>Vea también
<!-- This is in the basics guide. It needs to be migrated -->
[Creación de conexiones para definir y ver las relaciones entre registros](/dynamics365/customer-engagement/basics/create-connections-view-relationships-between-records)<br />
[Creación y edición de conjuntos de opciones globales de Common Data Service for Apps (listas desplegables)](create-edit-global-option-sets.md)<br />
[Creación y edición de relaciones entre entidades](create-edit-entity-relationships.md)


