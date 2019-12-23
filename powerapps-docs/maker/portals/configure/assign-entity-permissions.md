---
title: Agregar seguridad basada en registros mediante permisos de entidad para un portal en | MicrosoftDocs
description: Instrucciones para agregar un permiso de entidad y asignarle roles web.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: c92b664c2c40c6bb6354e2666d583d5c7ed7aead
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "2874450"
---
# <a name="add-record-based-security-by-using-entity-permissions-for-portals"></a>Agregar seguridad basada en registros utilizando los permisos de entidad para portales

Para aplicar recursos basados en la seguridad en portales a registros individuales, use permisos de entidad. Agruegue permisos de entidad a roles web, para que pueda definir los roles de la organización que corresponden lógicamente a los privilegios y los conceptos de propiedad y acceso de registro que se introducen usando permisos de entidad. Recuerde que un contacto dado puede pertenecer a cualquier número de roles y un determinado rol puede contener cualquier número de permisos de entidad. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Crear roles web para portales](create-web-roles.md) 

Aunque los permisos para cambiar y acceder a direcciones URL en un mapa del sitio del portal se conceden a través de autorización de contenido, los administradores del sitio también deberán proteger sus aplicaciones web personalizadas creadas con formularios de entidad y listas de entidad. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Definir formularios de entidad](entity-forms.md) y [Definir listas de entidad](entity-lists.md)  

Para proteger estas características, los permisos de entidad permiten conceder derechos granulares para entidades arbitrarias y habilitar seguridad a nivel de registro mediante definiciones de relación.

## <a name="add-entity-permissions-to-a-web-role"></a>Agregar permisos de entidad a un rol web

1.  Abra la aplicación [Administración del portal](configure-portal.md).

2. Vaya a **Portales** &gt; **Roles web** y abra el rol web al que desea agregar permisos. 

3. En **Relacionado**, seleccione **Permisos de entidad**.

4. Seleccione **Agregar permiso de entidad existente** para agregar un permiso de entidad existente a un rol web. 

4. Busque un permiso de entidad o seleccione **Nuevo permiso de entidad** para crear un nuevo registro de permiso de entidad.

    ![Agregar permisos de entidad a un rol web](../media/add-entity-permission-web-role.png "Agregar permisos de entidad a un rol web")  

Cuando crea un nuevo registro de permisos de entidad, el primer paso es determinar la entidad que se protegerá. El paso siguiente es definir el ambito, como verá a continuación, y&mdash;para cualquier ámbito más allá de Global&mdash;, las relaciones que definen ese ámbito. Finalmente, determine los derechos que se están concediendo al rol a través de estos permisos. Tenga en cuenta que los derechos son acumulativos, por lo que si un usuario está en un rol que concede lectura y otro que concede lectura y actualización, el usuario tendrá derechos de lectura y actualización sobre cualquier registro que se solape entre los dos roles.

> [!Note]
> La selección de las entidades de CMS, como la página web y los archivos web, no es válida y podría tener otras consecuencias involuntarias. El portal validará la seguridad de las entidades de CMS basadas en los controles de acceso a contenido, no los permisos de entidad.

### <a name="global-scope"></a>Ámbito global

Si un registro de permiso de entidad con permiso de lectura se concede a un rol que tenga ámbito global, cualquier contacto en dicho rol tendrá acceso a todos los registros de la entidad definida. Por ejemplo, podrán ver todos los clientes potenciales, todas las cuentas, etc. Este permiso será respetado automáticamente por cualquier lista de entidades, esencialmente mostrando todos los registros de acuerdo con las vistas de la aplicación basada en modelo que se han definido para esa lista. Además, si un usuario intenta acceder a un registro mediante un formulario de entidad al que no tiene acceso, recibirá un error de permiso.

### <a name="contact-scope"></a>Ámbito de contacto

Con el ámbito de contacto, un usuario que ha iniciado sesión en el rol para el que se define el registro del permiso tendrá los derechos que otorga dicho permiso solo para los registros que están relacionados con el registro de contacto de ese usuario a través de una relación definida.

En una lista de entidades, esto significa que un filtro se agregará a las vistas de cualquier aplicación basada en modelo que hayan emergido de esa lista, que recupera solo los registros vinculados al usuario actual directamente. (En función del escenario, esta relación puede considerarse como propiedad o derechos de administración).

Los formularios de entidad permitirán sólo el permiso apropiado para lectura, creación, escritura, etc. si existe esta relación cuando el registro se carga. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Definir formularios de entidad](entity-forms.md).  

### <a name="account-scope"></a>Ámbito de cuenta

Con el ámbito de cuenta, un usuario que haya iniciado sesión en el rol para el que se define el registro del permiso tendrá los derechos que otorga dicho permiso solo para los registros que estén relacionados con el registro de cuenta primaria de ese usuario, a través de una relación definida.

### <a name="self-scope"></a>Ámbito propio

El ámbito propio permite definir los derechos que tiene un usuario sobre su propio registro de contacto (identidad). Esto permite que los usuarios usen formularios de entidad o formularios web para realizar cambios en su propio registro de contacto vinculado con su perfil. Tenga en cuenta que la página de Perfil predeterminada tiene un formulario integrado especial que permite que que cualquier usuario cambie su información de contacto básica y opte por recibir o anular las a listas de marketing. Si este formulario se incluye en su portal (que es la opción predeterminada), los usuarios no necesitarán este permiso para usarlo. Sin embargo, mecesitarán este permiso para usar cualquier formulario de entidad personalizado o formularios web destinados a su registro de contacto de usuario.

### <a name="parental-scope"></a>Ámbito jerárquico

En este caso más complejo, se conceden permisos para una entidad que esté en una relación separada de una entidad para la que ya se haya definido un registro de permiso de entidad. Este permiso es realmente un registro secundario del permiso de la entidad principal.

El registro del permiso principal define un permiso y un ámbito para una entidad (probablemente de ámbito global o de contacto, aunque jerárquico también es posible). Esa entidad podría estar relacionada con un contacto (en el caso de ámbito de contacto) o definida globalmente. Con ese permiso instalado, se crea un permiso secundario que define una relación de otra entidad en la entidad definida en la relación principal.

Así, los usuarios de un rol web que tengan acceso a los registros definidos por los permisos de la entidad principal, también tendrán derechos definidos por el registro secundario a los registros relacionados con el registro primario.

### <a name="attributes-and-relationships"></a>Atributos y relaciones

La tabla de abajo explica los atributos de permiso de entidad.

| Nombre                     | Descripción                                                                                                                                                                                                                                                                                                               |
|--------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Nombre                     | Nombre descriptivo del registro. Este campo es obligatorio.                                                                                                                                                                                                                                                               |
| Nombre de entidad              | El nombre lógico de la entidad que se va a proteger o que definirá la relación de contacto o relación principal para proteger a una entidad relacionada en un permiso secundario. Este campo es obligatorio.                                                                                                                        |
| Ámbito (obligatorio)                   | <ul><li>**Global**: Conceda privilegios al registro de entidad sin requisitos para un propietario (contacto).</li><li>**Contacto**: Conceda privilegios al registro de entidad que tiene una relación directa con un propietario (contacto).</li><li>**Cuenta**: Conceda privilegios al registro de entidad que tiene una relación con una cuenta, que sirve como propietario, suponiendo que la cuenta es el cliente principal del contacto.</li><li>**Principal**: Conceda privilegios al registro de entidad a través de la cadena de relaciones de permisos primarios.</li></ul>|
| Relación de contacto     | Sólo se requiere si Ámbito = Contacto. El nombre de esquema de la relación entre el contacto y la entidad especificada por el campo Nombre de entidad.|
| Relación primaria      | Sólo se requiere si se asigna un permiso de entidad principal. El nombre de esquema de la relación entre la entidad especificada por el campo Nombre de entidad y la entidad especificada por el campo Nombre de entidad en su registro de permiso de entidad principal.                                                                                     |
| Permiso de entidad primaria | Sólo se requiere si Ámbito = Principal.                                                                                                                                                                                                                                                            |
| Leer                     | Privilegio que controla si el usuario puede leer un registro.                                                                                                                                                                                                                                                               |
| Escribir                    | Privilegio que controla si el usuario puede actualizar un registro.                                                                                                                                                                                                                                                             |
| Crear                   | Privilegio que controla si el usuario puede crear un nuevo registro. El derecho para crear un registro de un tipo de entidad no se aplica a un registro individual, sino a una clase de entidades.                                                                                                                             |
| Supr                   | Privilegio que controla si el usuario puede eliminar un registro.                                                                                                                                                                                                                                                             |
| Anexar                   | Privilegio que controla si el usuario puede adjuntar otro registro al registro especificado. Los derechos de acceso de Anexar y Anexar a funcionan conjuntamente. Cada vez que un usuario asocia un registro a otro, el usuario debe tener ambos derechos. Por ejemplo, si adjunta una nota a un caso, debe tener el derecho de acceso Anexar en la nota y el derecho de acceso Anexar a en el caso para que la operación funcione.  |
| Anexar a                | Privilegio que controla si el usuario puede anexar el registro en cuestión a otro registro. Los derechos de acceso de Anexar y Anexar a funcionan conjuntamente. Para obtener más información, consulte la descripción para Anexar.|
| | |

## <a name="global-permissions-for-tasks-related-to-leads"></a>Permisos globales para tareas relacionadas con clientes potenciales

En un escenario, podríamos desear usar una lista de entidad y formularios de entidad para exponer a todos los clientes potenciales en el portal a cualquiera en un rol web de Administrador de clientes potenciales personalizado. En el formulario de edición de cliente potencial, que se inicia cada vez que se selecciona una fila de cliente potencial en la lista, se mostrará una subcuadrícula de los registros de tareas relacionados. Estos registros deben ser accesibles para cualquiera con el rol de administrador de clientes potenciales. Como primer paso, daremos permisos globales sobre clientes potenciales a cualquiera en nuestro rol de administrador de clientes potenciales.

Este rol tiene un permiso de entidad relacionado para la entidad Cliente potencial, con un ámbito global.

Los usuarios de este rol pueden obtener acceso a todos los clientes potenciales mediante listas de entidades o formularios en el portal.

![Conceder permisos globales a un cliente potencial](../media/grant-global-permission-leads.png "Conceder permisos globales a un cliente potencial")  

Ahora agregaremos un permiso secundario al permiso de clientes potenciales global. Con el registro de permiso primario abierto, vaya a la subcuadrícula **Permisos de entidad secundaria** y seleccione **Nuevo** para abrir una búsqueda de permisos de entidad, seleccione la lupa y luego seleccione **Nuevo** para agregar un nuevo registro.

![Agregar permisos de entidad a un rol web](../media/add-entity-permission-web-role.png "Agregar permisos de entidad a un rol web")  

Seleccione la entidad como Tareas y el ámbito como Jerárquica. Tenga en cuenta que a continuación puede seleccionar la relación principal (**Lead\_Tasks**). Este permiso implica que un contacto que es un rol web con el permiso primario tendrán permiso global a todas las tareas que estén relacionadas con clientes potenciales.

Recuerde que para que la lista respete estos permisos, debe haber habilitado permisos de entidad en la lista Y debe haber acciones que permitan realmente que los usuarios realicen las acciones para las que se les han concedido sus permisos. Además, los permisos también se deben habilitar en el registro de [formulario de entidad](entity-forms.md) y de ese formulario debe emerger una página con una subcuadrícula para la entidad que desea habilitar con permisos secundarios, en este caso Tareas. Además, para habilitar permisos de lectura o creación para tareas, deberá configurar esos formularios de entidad también y editar los formularios para quitar el campo de búsqueda referente.  

![Edición de un formulario de página web](../media/edit-webpage-form.png "Edición de un formulario de página web")  

Esto le concederá permisos para todas las tareas que estén relacionados con clientes potenciales. Si las tareas emergen en una lista de entidad, esencialmente se agrega un filtro a la lista de modo que solo las tareas relacionadas con un cliente potencial aparezcan en la lista. En nuestro ejemplo, emergen con una subcuadrícula en un formulario de entidad.

![Ejemplo de tarea](../media/tasks-example.png "Ejemplo de tarea")  

## <a name="contact-scoped-permissions-for-tasks"></a>Permisos con ámbito de contacto para tareas

Otro ejemplo sería si deseara permitir el acceso a las tareas para las que un contacto está relacionado con el cliente potencial principal de esa tarea. Este escenario es prácticamente idéntico a la sección anterior, salvo que en este caso el permiso principal tiene un ámbito de contacto, en lugar de global. Debe especificar una relación en la relación principal entre la entidad de cliente potencial y la entidad de contacto.

Una vez establecidos estos permisos, los usuarios en el rol de administrador de clientes potenciales pueden tener acceso a los clientes potenciales relacionados con ellos directamente especificados por el permiso de ámbito de contacto y las tareas de acceso relacionadas con esos mismos clientes potenciales especificadas por el registro de permiso secundario.

### <a name="see-also"></a>Vea también

[Crear roles web para portales](create-web-roles.md)  
[Controlar el acceso a páginas web para los portales](webpage-access-control.md)