---
title: Agregar seguridad basada en registros mediante el uso de permisos de entidad para un portal | MicrosoftDocs
description: Instrucciones para agregar un permiso de entidad y asignarles roles Web.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 47730a2ba169b89534fa93221290c5598a95a8e8
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553403"
---
# <a name="add-record-based-security-by-using-entity-permissions-for-portals"></a>Agregar seguridad basada en registros mediante el uso de permisos de entidad para portales

Para aplicar la seguridad basada en registros en los portales a registros individuales, use permisos de entidad. Los permisos de entidad se agregan a los roles Web, por lo que puede definir los roles de su organización que correspondan lógicamente a los privilegios y los conceptos de propiedad del registro y acceso que se introducen mediante permisos de entidad. Recuerde que un contacto determinado puede pertenecer a cualquier número de roles, y un rol determinado puede contener cualquier número de permisos de entidad. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [crear roles web para portales](create-web-roles.md) 

Aunque los permisos para cambiar y acceder a las direcciones URL en un mapa del sitio del portal se conceden a través de la autorización de contenido, los administradores de sitio también querrán proteger sus aplicaciones web personalizadas compiladas con formularios de entidad y listas de entidades. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [definir formularios de entidad](entity-forms.md) y [definir listas de entidades](entity-lists.md)  

Para proteger estas características, los permisos de entidad permiten conceder derechos granulares para entidades arbitrarias y para habilitar la seguridad de nivel de registro a través de definiciones de relación.

## <a name="add-entity-permissions-to-a-web-role"></a>Agregar permisos de entidad a un rol Web

1.  Abra la [aplicación administración del portal](configure-portal.md).

2. Vaya a **portales** &gt; **roles web** y abra el rol Web al que desea agregar los permisos. 

3. Seleccione **Agregar** para agregar un permiso de entidad existente a un rol Web. 

4. Seleccione **nuevo** para crear un nuevo registro de permisos de entidad.

    ![Agregar permisos de entidad a un rol Web](../media/add-entity-permission-web-role.png "Agregar permisos de entidad a un rol Web")  

Al crear un nuevo registro de permisos de entidad, el primer paso es determinar la entidad que se va a proteger. El siguiente paso consiste en definir el ámbito, como se describe a continuación, y&mdash;para cualquier ámbito que no sea global&mdash;las relaciones que definen ese ámbito. Por último, determine los derechos que se conceden al rol a través de este permiso. Tenga en cuenta que los derechos son acumulativos, por lo que si un usuario está en un rol que concede lectura y otro que concede lectura y actualización, el usuario tendrá derechos de lectura y actualización para los registros que se superpongan entre los dos roles.

> [!Note]
> La selección de entidades CMS como páginas web y archivos Web no es válida y puede tener otras consecuencias no deseadas. El portal impondrá la seguridad de las entidades CMS en función de los controles de acceso a contenido, no de los permisos de entidad.

### <a name="global-scope"></a>Ámbito global

Si se concede un registro de permisos de entidad con permiso de lectura a un rol que tiene ámbito global, cualquier contacto de ese rol tendrá acceso a todos los registros de la entidad definida. Por ejemplo, podrán ver todos los clientes potenciales, todas las cuentas, etc. Este permiso se respetará automáticamente en todas las listas de entidades; en esencia, se mostrarán todos los registros según las vistas de aplicaciones controladas por modelos definidas para esa lista. Además, si un usuario intenta obtener acceso a un registro a través de un formulario de entidad al que no tiene acceso, recibirá un error de permiso.

### <a name="contact-scope"></a>Ámbito de contacto

Con el ámbito de contacto, un usuario con sesión iniciada en el rol para el que se define el registro de permisos tendrá los derechos concedidos por ese permiso solo para los registros relacionados con el registro de contacto de ese usuario a través de una relación definida.

En una lista de entidades, esto significa que se agregará un filtro a las vistas de aplicación controladas por modelos que se muestran en esa lista, que solo recupera los registros vinculados directamente al usuario actual. (Dependiendo del escenario, esta relación se puede considerar como propiedad o como derechos de administración).

Los formularios de entidad solo permitirán el permiso adecuado para lectura, creación, escritura, etc. Si esta relación existe cuando se carga el registro. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [definir formularios de entidad y lógica personalizada dentro de un portal](entity-forms.md).  

### <a name="account-scope"></a>Ámbito de la cuenta

Con el ámbito de la cuenta, un usuario con sesión iniciada en el rol para el que se define el registro de permisos tendrá los derechos concedidos por ese permiso solo para los registros relacionados con el registro de la cuenta primaria de ese usuario a través de una relación definida.

### <a name="self-scope"></a>Ámbito propio

El ámbito propio le permite definir los derechos que un usuario tiene en su propio registro de contacto (identidad). Esto permite a los usuarios utilizar formularios de entidad o formularios Web Forms para realizar cambios en su propio registro de contacto vinculado a su perfil. Tenga en cuenta que la página de perfil predeterminada tiene un formulario integrado especial que permite a cualquier usuario cambiar su información de contacto básica y participar o no en las listas de marketing. Si este formulario se incluye en el portal (que es de forma predeterminada), los usuarios no necesitarán este permiso para usarlo. Sin embargo, necesitará este permiso para usar cualquier formulario de entidad personalizado o formularios Web Forms que tengan como destino su registro de contacto de usuario.

### <a name="parental-scope"></a>Ámbito parental

En este caso más complejo, se conceden permisos para una entidad que es una relación fuera de una entidad para la que ya se ha definido un registro de permisos de entidad. Este permiso es realmente un registro secundario del permiso de entidad primaria.

El registro de permisos primario define un permiso y un ámbito para una entidad (probablemente global o de contacto, aunque también es posible). Esa entidad puede estar relacionada con un contacto (en el caso de ámbito de contacto) o definido globalmente. Con ese permiso en contexto, se crea un permiso secundario que define una relación de otra entidad con la entidad definida en la relación primaria.

Por lo tanto, los usuarios de un rol Web que tengan acceso a los registros definidos por los permisos de entidad primaria también tendrán los derechos definidos por el registro de permisos secundario en los registros relacionados con el Registro primario.

### <a name="attributes-and-relationships"></a>Atributos y relaciones

En la tabla siguiente se explican los atributos de permisos de entidad.

| Nombre                     | Descripción                                                                                                                                                                                                                                                                                                               |
|--------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Nombre                     | Nombre descriptivo del registro. Este campo es obligatorio.                                                                                                                                                                                                                                                               |
| Nombre de entidad              | El nombre lógico de la entidad que se va a proteger o que definirá la relación de contacto o la relación primaria para proteger una entidad relacionada en un permiso secundario. Este campo es obligatorio.                                                                                                                        |
| Ámbito (obligatorio)                   | <ul><li>**Global**: conceder privilegios al registro de entidad sin ningún requisito para un propietario (contacto).</li><li>**Contacto**: conceder privilegios al registro de entidad que tenga una relación directa con un propietario (contacto).</li><li>**Cuenta**: conceda privilegios al registro de entidad que tenga una relación con una cuenta, que actúa como propietario, suponiendo que la cuenta es el cliente primario del contacto.</li><li>**Primario**: concede privilegios al registro de entidad a través de la cadena de relaciones de sus permisos principales.</li></ul>|
| Relación de contacto     | Obligatorio solo si Scope = contact. El nombre de esquema de la relación entre el contacto y la entidad especificada por el campo Nombre de la entidad.|
| Relación primaria      | Solo es necesario si se asigna un permiso de entidad primaria. El nombre de esquema de la relación entre la entidad especificada por el campo Nombre de la entidad y la entidad especificada por el campo Nombre de la entidad en su registro de permisos de entidad primaria.                                                                                     |
| Permiso de entidad primaria | Obligatorio solo si Scope = Parent.                                                                                                                                                                                                                                                            |
| Lectura                     | Privilegio que controla si el usuario puede leer un registro.                                                                                                                                                                                                                                                               |
| Escribi                    | Privilegio que controla si el usuario puede actualizar un registro.                                                                                                                                                                                                                                                             |
| A                   | Privilegio que controla si el usuario puede crear un nuevo registro. El derecho a crear un registro para un tipo de entidad no se aplica a un registro individual, sino a una clase de entidades.                                                                                                                             |
| Elimínelos                   | Privilegio que controla si el usuario puede eliminar un registro.                                                                                                                                                                                                                                                             |
| anexar                   | Privilegio que controla si el usuario puede adjuntar otro registro al registro especificado. Los derechos de acceso para anexar y anexar a no funcionan en combinación. Cada vez que un usuario adjunta un registro a otro, el usuario debe tener ambos derechos. Por ejemplo, al adjuntar una nota a un caso, debe tener el derecho de acceso de anexión en la nota y el derecho de acceso de anexar a en el caso de que la operación funcione.  |
| Anexar a                | Privilegio que controla si el usuario puede anexar el registro en cuestión a otro registro. Los derechos de acceso para anexar y anexar a no funcionan en combinación. Para obtener más información, vea la descripción de Append.|
| | |

## <a name="global-permissions-for-tasks-related-to-leads"></a>Permisos globales para tareas relacionadas con clientes potenciales

En un escenario, es posible que deseemos usar una lista de entidades y formularios de entidad para mostrar todos los clientes potenciales en el portal a cualquiera de los roles Web de administrador de clientes potenciales. En el formulario de edición de clientes potenciales, que se inicia cada vez que se selecciona una fila de cliente potencial en la lista, una subcuadrícula mostrará los registros de tareas relacionados. Estos registros deben ser accesibles para cualquiera de los roles de administrador de clientes potenciales. Como primer paso, concederemos permisos globales a cualquier persona de nuestro rol de administrador de clientes potenciales.

Este rol tiene un permiso de entidad relacionada para la entidad del cliente potencial, con un ámbito global.

Los usuarios de este rol pueden tener acceso a todos los clientes potenciales a través de listas de entidades o formularios en el portal.

![Conceder permisos globales a un cliente potencial](../media/grant-global-permission-leads.png "Conceder permisos globales a un cliente potencial")  

Ahora vamos a agregar un permiso secundario al permiso de responsable global. Con el registro de permisos primario abierto, vaya a la subcuadrícula de **permisos de entidad secundaria** , seleccione **nuevo** para abrir una búsqueda de permisos de entidad, seleccione la lupa y, a continuación, seleccione **nuevo** para agregar un nuevo registro.

![Agregar permisos de entidad a un rol Web](../media/add-entity-permission-web-role.png "Agregar permisos de entidad a un rol Web")  

Seleccione la entidad como tareas y el ámbito como parental. Tenga en cuenta que, a continuación, puede seleccionar la relación primaria (**tareas de cliente potencial\_** ). Este permiso implica que un contacto que está en un rol Web con el permiso principal tendrá permiso global para todas las tareas relacionadas con los clientes potenciales.

Recuerde que para que la lista respete estos permisos, debe tener habilitados los permisos de entidad en la lista y debe haber acciones que permitan a los usuarios realizar las acciones para las que se han concedido sus permisos. Además, los permisos también se deben habilitar en el registro del formulario de la [entidad](entity-forms.md) y ese formulario debe estar en la superficie de una página que tenga una subcuadrícula en él para la entidad que desea habilitar con permisos secundarios, en este caso tareas. Además, para habilitar permisos de lectura o creación para las tareas, también tendrá que configurar esos formularios de entidad y editar los formularios para quitar el campo de búsqueda relacionado.  

![Editar un formulario de página web](../media/edit-webpage-form.png "Editar un formulario de página web")  

A continuación, concede permisos para todas las tareas relacionadas con clientes potenciales. Si las tareas se muestran en una lista de entidades, se agrega un filtro a la lista para que solo se muestren en la lista las tareas relacionadas con un cliente potencial. En nuestro ejemplo, se muestran con una subcuadrícula en un formulario de entidad.

![Ejemplo de tarea](../media/tasks-example.png "Ejemplo de tarea")  

## <a name="contact-scoped-permissions-for-tasks"></a>Permisos de ámbito de contacto para las tareas

Otro ejemplo sería si desea permitir el acceso a las tareas para las que un contacto está relacionado con el responsable principal de esa tarea. Este escenario es casi idéntico a la sección anterior, excepto en este caso el permiso primario tiene un ámbito de contacto, en lugar de global. Se debe especificar una relación en la relación primaria entre la entidad cliente potencial y la entidad contacto.

Una vez que estos permisos se hayan implementado, los usuarios del rol administrador de clientes potenciales pueden tener acceso a los clientes potenciales que están relacionados directamente según lo especificado por el permiso de ámbito de contacto y a las tareas relacionadas con esos mismos clientes como especifica el registro de permisos secundario.

### <a name="see-also"></a>Vea también

[Crear roles web para portales](create-web-roles.md)  
[Control del acceso a la página web para portales](webpage-access-control.md)