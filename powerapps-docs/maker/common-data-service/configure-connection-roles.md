---
title: Configurar roles de conexión | MicrosoftDocs
ms.custom: ''
ms.date: 10/17/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
ms.author: matp
manager: kvivek
author: Mattp123
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 434dea11e5238167e824561e247bc23ddbb7839b
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "2874186"
---
# <a name="configure-connection-roles"></a>Configurar roles de conexión

Con Common Data Service puede definir **conexiones** entre registros de entidad sin crear una relación de entidad. En aplicaciones basadas en modelos los usuarios pueden establecer un vínculo con nombre entre registros para establecer una relación menos formal que no justifique la creación de una relación entre entidades real. Algunos ejemplos son *amigo*, *hermano*, *esposo*, *asistente* y *parte interesada*. Algunas conexiones puede que también sean recíprocas, como *hijo* y *padre*, *marido* y *esposa*, o *doctor* y *paciente*.

Cuando las personas establezcan una conexión entre dos registros, también pueden agregar una descripción e información adicional como fechas de inicio y finalización para la relación. Más información: [Creación de conexiones para definir y ver relaciones entre registros](/dynamics365/customer-engagement/basics/create-connections-view-relationships-between-records).

Cualquiera con acceso de escritura a la entidad **Rol de conexión** puede establecer qué conexión está disponible para que las personas la usen.

> [!IMPORTANT]
> Para que una entidad esté disponible como tipo de registro para un nuevo o existente rol de conexión, la propiedad **Habilitar conexiones** debe estar habilitado para la entidad. 

## <a name="enable-connection-roles-for-an-entity"></a>Habilitar roles de conexión para una entidad
1. Inicie sesión en [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc). 
2. Expanda **Datos**y, a continuación seleccione **Entidades**. 
3. Seleccione la entidad que desee habilitar para roles de conexión y, en la barra de comandos seleccione **Configuración**. 
4. En el panel **Configuración** expanda el área **Colaboración** y, a continuación seleccione **Habilitar conexiones**.
    > [!div class="mx-imgBorder"] 
    > ![Habilitar configuración de conexiones](media/enable-connections.png "Habilitar configuración de conexiones")

6. Seleccione **Listo**. 

## <a name="view-connection-roles"></a>Ver roles de conexión

Hay varios roles estándar de conexión ya configurados en Common Data Service. Para verlos debe desplazarse al área de Configuración. 

### <a name="navigate-to-the-settings-area"></a>Navegue al área de Configuración.

1. En una aplicación basada en modelo seleccione **Configuración** > **Configuración avanzada**. 
2. Navegue a **Configuración** > **Negocio** > **Administración de empresas** y después seleccione **Roles de conexión**.

   > [!div class="mx-imgBorder"] 
    > ![Roles de conexión en la configuración de Administración de empresas](media/navigate-settings-connection-roles.png "Roles de conexión en la configuración de Administración de empresas")

En esta vista puede ver todos los roles de conexión que estén disponibles para este entorno y puede editarlos aquí.

> [!NOTE]
> Si desea distribuir roles de conexión con una solución, asegúrese de que se incluyen en la solución que desea distribuir. Más información: [Agregue roles de conexión a una solución](#add-connection-roles-to-a-solution)

## <a name="view-connection-roles-in-the-solution-explorer"></a>Vea roles de conexión en el explorador de soluciones.

Puesto que los roles de conexión son *compatibles con las soluciones*, significa que se pueden incluir en una solución, también puede agregar roles de conexión a una solución que distribuye.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

La mayoría de los roles de conexión que puede ver en el área **Configuración** se definen en la **Solución predeterminada** *interna* (que no debe confundirse con **Solución predeterminada de Common Data Service**). La **Solución predeterminada** interna contiene todas las personalizaciones del sistema. Para ver la **Solución predeterminada** elija el vista **Todas las soluciones: internas**.

## <a name="add-connection-roles-to-a-solution"></a>Agregar roles de conexión a una solución

Generalmente no es recomendable editar los componentes de la **Solución predeterminada** interna. En la **Solución predeterminada de Common Data Service** o cualquier solución que haya creado para trabajar, puede usar el comando **Agregar existente** para llevar los roles de conexión predeterminados a la solución.

![Agregar rol de conexión existente](media/add-existing-connection-role.png)

Una vez que agrega el rol de conexión a la solución, puede editarlo donde esté visible.

## <a name="create-or-edit-connection-roles"></a>Creación o edición de roles de conexión.

> [!IMPORTANT]
> Si tiene previsto distribuir una solución que incluya nuevos roles o cambios en roles de conexión existentes debe agregarlos a la solución que se distribuirá. Al editar o agregar nuevos roles de conexión mediante el área **Configuración** se agregarán estos roles de conexión a la **Solución predeterminada** interna y no se incluirán en la solución que distribuirá a menos que primero la agregue a la solución. Más información [Agregue roles de conexión a una solución](#add-connection-roles-to-a-solution)

En la lista **Roles de conexión**, seleccione uno de los roles de conexión para editarlo.
Hay tres pasos para definir un rol de conexión que se indican claramente en el formulario.

![Crear formulario Rol de conexión](media/create-connection-role-form.png)

### <a name="describe-the-connection-role"></a>Describa el rol de conexión

Establezca los siguientes campos:

|Campo|Descripción|
|--|--|
|**Nombre**|(Necesario) Texto que describe la conexión.|
|**Categoría**|Grupo que describe la categoría de la conexión. Más información: [Valores de categoría de rol de conexión](#connection-role-category-values)|
|**Descripción**|Especifique una definición para el rol.|

#### <a name="connection-role-category-values"></a>Valores de categoría de rol de conexión

Los valores **Categoría** predeterminados son:
- Empresa
- Familia
- Social
- Sales
- Otras
- Parte interesada
- EQUIPO DE VENTAS
- Servicio

Puede agregar nuevas categorías o modificar las existentes editando el conjunto de opciones globales **Categoría**. Más información: [Creación y edición de conjuntos de opciones globales para Common Data Service (listas desplegables)](create-edit-global-option-sets.md)

### <a name="select-record-types"></a>Seleccionar tipos de registro

Seleccione los tipos de registro que deben estar disponibles para conectar.

> [!NOTE]
> Aunque **Todos** esté seleccionado de forma predeterminada, asegúrese de considerar los tipos adecuados para el rol de conexión que va a agregar.

### <a name="matching-connection-roles"></a>Roles de conexión coincidentes

En este paso opcional, puede definir los roles que se aplicarán de forma recíproca. No es necesario, pero las conexiones son más significativas si los define.

Por ejemplo, los usuarios pueden establecer que Glen es *Amigo* de Mary, pero ¿significa esto que Mary es *Amiga* de Glen? Esperamos que sí. Pero si Glen es el *Padre* de Mary no significa que Mary sea el *Padre* de Glen. El establecimiento de reciprocidad correcta requiere este paso adicional.

Cuando las personas establecen un rol de conexión que no tiene ningún rol de conexión coincidente, el rol solo se mostrará al ver la conexión desde el registro al que se aplicó la conexión. Cuando se ve desde el registro conectado, el rol estará vacío a menos que se establezca un rol coincidente.

Para definiciones de roles como *Amigo*, *Cónyuge*, *Compañero*, *Hermano*, es mejor asignar el rol coincidente a uno mismo. Si está configurado un único rol de conexión coincidente, el único rol de conexión coincidente se aplicará en ambas direcciones.

> [!IMPORTANT]
> Deberá guardar un nuevo rol de conexión sin este rol de conexión coincidente antes de poder establecer el rol de conexión coincidente a sí mismo.

Encontrará que algunos roles de conexión ya están configurados con roles de conexión coincidentes. *Empleado anterior* coincide con *Contratador anterior* y viceversa. Este tipo de rol de conexión coincidente uno a uno es el más común.

Puede configurar múltiples roles de conexión coincidentes para describir complejas relaciones. Si crea un rol de conexión como *Padre*, podrá configurar dos roles más como *Hija* e *Hijo* y aplicar ambos como roles de conexión coincidentes a *Padre*. A su vez, los roles de conexión *Hija* e *Hijo* deben asociarse con *Padre*. Por supuesto, después debe configurar un rol equivalente para *Madre* que coincida semejantemente con *Hija* e *Hijo*.

> [!TIP]
> Antes de crear un conjunto complejos de roles de conexión, piense si un conjunto más sencillo de roles es suficiente. Por ejemplo, en lugar de crear un conjunto complejo de roles de conexión como *Padre*, *Madre*, *Hijo*, e *Hija*, piense si usar simplemente *Progenitor* y *Descendiente* le servirá.

Si configura más de un rol de conexión coincidente, esos roles de conexión representan los únicos roles recíprocos válidos. El primero se aplicará automáticamente como valor predeterminado. Si el valor predeterminado no es correcto, los usuarios deben editar manualmente la conexión y elegir entre opciones válidas definidas en la configuración.

### <a name="see-also"></a>Vea también
<!-- This is in the basics guide. It needs to be migrated -->
[Crear conexiones para definir y ver relaciones entre registros](/dynamics365/customer-engagement/basics/create-connections-view-relationships-between-records)<br />
[Crear y editar conjuntos de opciones globales para Common Data Service (listas desplegables)](create-edit-global-option-sets.md)<br />
[Crear y editar relaciones entre entidades](create-edit-entity-relationships.md)


