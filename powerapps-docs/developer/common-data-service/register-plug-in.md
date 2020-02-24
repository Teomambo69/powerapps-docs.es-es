---
title: Registrar un complemento (Common Data Service) | Microsoft Docs
description: Aprenda a registrar un complemento para aplicar lógica de negocios personalizada a Common Data Service.
ms.custom: ''
ms.date: 02/19/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: bba0a473d76fc69832e05ec316a6ed6da6ad899d
ms.sourcegitcommit: 6b2961308c41867756ecdd55f55eccbebf70f7f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "2975743"
---
# <a name="register-a-plug-in"></a>Registrar un complemento


El proceso para escribir, registrar y depurar un complemento es:

1. Crear un proyecto de biblioteca de clases de .NET Framework en Visual Studio
1. Agregar el paquete `Microsoft.CrmSdk.CoreAssemblies` NuGet al proyecto
1. Implementar la interfaz <xref:Microsoft.Xrm.Sdk.IPlugin> en clases que se registrarán como pasos.
1. Agregar su código al método <xref:Microsoft.Xrm.Sdk.IPlugin.Execute*> requerido por la interfaz
    1. Obtener las referencias a los servicios que necesita
    1. Adición de lógica de negocios
1. Firmar y crear el ensamblado
1. Probar el ensamblado
    1. **Registrar el ensamblado en un entorno de prueba**
    1. **Agregar el ensamblado registrado y pasos a una solución no administrada**
    1. Probar el comportamiento del ensamblado
    1. Comprobar que se escriben los registros de seguimiento esperados
    1. Depure el ensamblado según sea necesario


El contenido de este tema describe los pasos anteriores **en negrita** y ofrece los tutoriales siguientes:

- [Tutorial: Escribir y registrar un complemento](tutorial-write-plug-in.md)
- [Tutorial: Depurar un complemento](tutorial-debug-plug-in.md)
- [Tutorial: Actualizar un complemento](tutorial-update-plug-in.md)

## <a name="plugin-registration-tool-prt"></a>Plugin Registration Tool (PRT)

Usará la Plugin Registration Tool (PRT) (PRT) para registrar los pasos y ensamblados de complementos.

PRT es una de las herramientas disponibles para descargar de NuGet. Siga las instrucciones de [Descargar herramientas de NuGet](download-tools-nuget.md). Este tema incluye instrucciones para usar un script de PowerShell para descargar las últimas herramientas de NuGet.

Después de descargar la PRT, siga los pasos de [Conectar con la Plugin Registration Tool](tutorial-write-plug-in.md#connect-using-the-plug-in-registration-tool) del [Tutorial: Escribir y registrar un complemento](tutorial-write-plug-in.md) para conectarse al entorno de Common Data Service.

## <a name="register-an-assembly"></a>Registrar un ensamblado

Registrar un ensamblado es el proceso de cargar el ensamblado a la base de datos de Common Data Service. Consulte las instrucciones que se encuentran en [Registrar el ensamblado](tutorial-write-plug-in.md#register-your-assembly) en el [Tutorial: Escribir y registrar un complemento](tutorial-write-plug-in.md)

> [!NOTE]
> Encontrará opciones relacionadas con el *modo aislado* y *ubicación* para el ensamblado. Estos hacen referencia a opciones que se aplican a implementaciones locales. Common Data Service no está disponible para implementaciones locales, por lo que usted siempre aceptará las opciones predeterminadas de **Espacio aislado** y **Base de datos** para estas opciones.

Cuando un ensamblado se carga se almacena en la entidad `PluginAssembly`. La mayoría de las propiedades se establecen utilizando la reflexión de la entidad importada. Los bytes codificados base64 del ensamblado se almacenan en el atributo `Content`. Mientras ve las **Propiedades** del ensamblado en la PRT, solo puede editar el valor de atributo **Descripción**.

### <a name="view-registered-assemblies"></a>Ver ensamblados registrados

Puede ver información sobre los ensamblados registrados en el explorador de soluciones de la aplicación sin usar la PRT.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

> [!NOTE]
> Cada ensamblado que agregue mediante PRT se agregará al sistema **Solución predeterminada** (que no debe confundirse con la **Solución predeterminada de Commmon Data Services**). Para ver la **Solución predeterminada**, seleccione **Todas las soluciones** en **Soluciones** y después cambie la vista a **Todas las soluciones - internas**.
> 
> Para obtener más información acerca de soluciones, vea [Introducción a soluciones](introduction-solutions.md)

![Todas las soluciones internas](media/all-solutions-internal-view.png)

Después de seleccionar el nombre de la Solución predeterminada en la lista de soluciones internas, puede encontrar todos los ensamblados registrados para este entorno.

![Ver todos los ensamblados registrados](media/view-plug-in-assemblies-default-solution.png)

### <a name="query-registered-assemblies-with-code"></a>Consultar ensamblados registrados con código

Para ver información sobre ensamblados registrados sin la PRT o la aplicación, use la siguiente consulta de la API web en su explorador:

```
[org uri]]/api/data/v9.0/pluginassemblies
?$filter=ishidden/Value eq false
&$select=
createdon,
culture,
customizationlevel,
description,
isolationmode,
major,
minor,
modifiedon,
name,
pluginassemblyid,
publickeytoken,
version
```

O use el siguiente FetchXml para recuperarlo en un programa que escriba:

```xml
<fetch>
  <entity name='pluginassembly' >
    <attribute name='createdon' />
    <attribute name='culture' />
    <attribute name='customizationlevel' />
    <attribute name='description' />
    <attribute name='isolationmode' />
    <attribute name='major' />
    <attribute name='minor' />
    <attribute name='modifiedon' />
    <attribute name='name' />
    <attribute name='pluginassemblyid' />
    <attribute name='publickeytoken' />
    <attribute name='version' />
    <filter type='and' >
      <filter>
        <condition attribute='ishidden' operator='eq' value='false' />
      </filter>
    </filter>
  </entity>
</fetch>
```
Más información: [Uso de FetchXML con FetchExpression](org-service/entity-operations-query-data.md#use-fetchxml-with-fetchexpression)

## <a name="add-your-assembly-to-a-solution"></a>Agregar el ensamblado a una solución

Como se describe en [Ver ensamblados registrados](#view-registered-assemblies), el registro de ensamblados que ha creado se agregó a la **Solución predeterminada** del sistema. Debe agregar el ensamblado a una solución no administrada para poder distribuirla a otras organizaciones.

En la solución no administrada que está usando, use el explorador de soluciones para navegar a **Ensamblados de complementos**. En el menú de lista, seleccione **Agregar existente**. Tenga en cuenta que en las siguientes figuras se utiliza una solución personalizada llamada Solución predeterminada de Common Data Service.

![Agregar ensamblado de complementos existente](media/add-existing-plug-in-assembly.png)

A continuación agregue su ensamblado como componente a la solución.

![Seleccione el ensamblado de complementos como componente de la solución](media/select-plug-in-assembly-as-solution-component.png)

Cuando seleccione el ensamblado de complementos que ha agregado, puede ver las clases de complementos que incluye.

![Ensamblados y clases de complementos](media/view-plug-in-classes-solution-explorer.png)

> [!NOTE]
> Los registros de pasos existentes o posteriores no se agregan a la solución no administrada que incluye los ensamblados de complementos. Debe agregar cada paso registrado a la solución por separado. Más información: [Agregar paso a solución](#add-step-to-solution)

## <a name="register-plug-in-step"></a>Registrar paso de complemento

Cuando un ensamblado se carga o actualiza, las clases que implementen <xref:Microsoft.Xrm.Sdk.IPlugin> estarán disponibles en la PRT. Use las instrucciones en [Registrar un nuevo paso](tutorial-write-plug-in.md) en el [Tutorial: Escribir y registrar un complemento](tutorial-write-plug-in.md#register-a-new-step) para crear un nuevo registro de paso.

Al registrar una paso, hay muchas opciones disponibles para usted que dependen de la fase de la canalización de eventos y la naturaleza de la operación que registrará para que responda el código.

### <a name="general-configuration-information-fields"></a>Campos de información de configuración general

|Campo|Descripción|
|--|--|
|**Mensaje**|PRT autocompletará nombres de mensaje disponibles en el sistema. Más información: [Usar mensajes con el servicio de la organización](org-service/use-messages.md)|
|**Entidad principal**|PRT autocompletará las entidades válidas que se aplican al mensaje seleccionado. Estos mensajes tienen un parámetro `Target` que acepta un tipo <xref:Microsoft.Xrm.Sdk.Entity> o <xref:Microsoft.Xrm.Sdk.EntityReference>. Si se aplican las entidades válidas, debe configurar esto cuando desee limitar el número de veces que se llama al complemento. <br />Si lo deja en blanco para los mensajes de la entidad principal como `Update`, `Delete`, `Retrieve` y `RetrieveMultiple` o cualquier mensaje que se puede aplicar con el mensaje, el complemento será invocado para todas las entidades que admitan este mensaje.|
|**Entidad secundaria**|Este campo se mantiene para la compatibilidad con versiones anteriores para los mensajes obsoletos que aceptaban una matriz de <xref:Microsoft.Xrm.Sdk.EntityReference> como el parámetro `Target`. Este campo no se suele usar más.|
|**Atributos de filtro**|Con el mensaje `Update`, cuando configura la **Entidad principal**, al filtrar atributos se limita la ejecución del complemento a casos donde los atributos seleccionados se incluyen en la actualización. Esta es una práctica recomendada para rendimiento. |
|**Controlador de eventos**|Este valor se rellenará en función del nombre del ensamblado y de la clase del complemento. |
|**Nombre del paso**|Nombre del paso. Se indica previamente un valor en función de la configuración del paso, pero este valor puede ser reemplazado.|
|**Ejecutar en contexto de usuario**|Proporciona opciones para aplicar suplantación para el paso. El valor predeterminado es **Usuario que llama**. Si el usuario que llama no tiene privilegios para realizar operaciones en el paso, es posible que necesite configurar esto como un usuario que tiene estos privilegios. Más información: [Suplantar a un usuario](impersonate-a-user.md) |
|**Pedido de ejecución**|Pueden registrarse múltiples pasos para la misma fase del mismo mensaje. El número de este campo determina el orden en el que se aplicarán del más bajo al más alto. <br/> **Nota**: debe establecer esta opción para controlar el orden en el que los complementos se aplican en la fase. No se recomendado para aceptar simplemente el valor predeterminado. Si todos los complementos de la misma fase, la entidad y el mensaje tienen el mismo valor, el valor [SdkMessageProcessingStep.SdkMessageFilterId](/dynamics365/customer-engagement/developer/entities/sdkmessageprocessingstep#BKMK_SdkMessageFilterId) determinará el orden en el que se ejecutan.|
|**Descripción**|Descripción del paso. Este valor se rellena previamente pero puede sobrescribirse.|

> [!NOTE]
> Existen algunos casos donde los complementos registrados para el evento `Update` se pueden llamar dos veces. Más información: [Comportamiento de operaciones de actualización especializadas](special-update-operation-behavior.md)


### <a name="event-pipeline-stage-of-execution"></a>Fase de canalización de eventos de ejecución

Elija la fase de la canalización de eventos que mejor se adapte al objetivo del complemento.

|Opción|Descripción|
|--|--|
|**PreValidation**|[!INCLUDE [cc-prevalidation-description](../../includes/cc-prevalidation-description.md)]|
|**PreOperation**|[!INCLUDE [cc-preoperation-description](../../includes/cc-preoperation-description.md)]|
|**PostOperation**|[!INCLUDE [cc-postoperation-description](../../includes/cc-postoperation-description.md)]|

Más información: [Canalización de ejecución de eventos](event-framework.md#event-execution-pipeline)

### <a name="execution-mode"></a>Modo de ejecución

Hay dos modos de ejecución: asincrónico y sincrónico.

|Opción|Descripción|
|--|--|
|**Asincrónico**|El contexto de ejecución y la definición de la lógica de negocios que se aplicará pasa al trabajo del sistema que se ejecutará después de que la operación se complete.|
|**Sincrónico**|Los complementos se ejecutan inmediatamente según la fase de ejecución y el orden de ejecución. La operación completa esperará hasta que se complete.|

Los complementos asincrónicos solo pueden registrarse para la fase **PostOperation**. Para obtener más información sobre el funcionamiento de los trabajos del sistema, consulte [Servicio asincrónico](asynchronous-service.md)

### <a name="deployment"></a>Implementación

|Opción|Descripción|
|--|--|
|**Servidor**|El complemento se ejecutará en el servidor de Common Data Service.|
|**Sin conexión**|El complemento se ejecutará en el cliente de Dynamics 365 for Outlook cuando el usuario esté en modo sin conexión.|

<!-- TODO Add link to where more information about offline-plugins will be documented -->

### <a name="set-configuration-data"></a>Establecer datos de configuración

Los campos **Configuración no segura** y **Configuración segura** permiten especificar datos de configuración para pasar al complemento para un paso específico.

Puede escribir el complemento para que acepte valores de cadena en el constructor para utilizar estos datos para controlar cómo el complemento debe funcionar para el paso. Más información: [Pasar datos de configuración al complemento](write-plug-in.md#pass-configuration-data-to-your-plug-in)

### <a name="define-entity-images"></a>Definir imágenes de entidad

En el complemento, es posible que desee hacer referencia a valores de propiedad de la entidad principal que no se incluyeron en una operación. Por ejemplo, en una operación `Update` es posible que desee conocer cuál era un valor antes de que cambiara, pero el contexto de ejecución no proporciona esta información, solo incluye el valor cambiado. 

Si el paso del complemento se registra en las fases **PreValidation** o **PreOperation** de la canalización de ejecución, puede usar el servicio de la organización para recuperar el valor actual de la propiedad, pero no es una buena práctica para rendimiento. Un ejercicio mejor es definir una imagen previa de la entidad con el registro del paso del ensamblado. Esto capturará una "instantánea” de la entidad con los campos que le interesan tal como estaban antes de la operación que puede usar para comparar con los valores cambiados. 

#### <a name="messages-that-support-entity-images"></a>Mensajes que admiten imágenes de la entidad

En Common Data Service, solo de los mensajes siguientes admiten imágenes de la entidad:

|Mensaje|Propiedad de clases de solicitud| Descripción|
|--|--|--|
|`Assign`|`Target`|La entidad asignada.|
|`Create`|`Target`|La entidad creada.|
|`Delete`|`Target`|La entidad eliminada.|
|`DeliverIncoming`|`EmailId`|Identificador de correo electrónico entregado.|
|`DeliverPromote`|`EmailId`|Identificador de correo electrónico entregado.|
|`Merge`|`Target` o `SubordinateId`|   La entidad principal, en la que se combinan los datos de la entidad secundaria o la entidad secundaria que se está combinando en la entidad principal.|
|`Route`|`Target`|El elemento que se enruta.|
|`Send`|`FaxId`, `EmailId` o `TemplateId` |El elemento que se envía.|
|`SetState`|`EntityMoniker`|La entidad para la que se establece el estado.|
|`Update`|`Target`|La entidad actualizada.|


#### <a name="types-of-entity-images"></a>Tipos de imágenes de la entidad

Existen dos tipos de imágenes de la entidad: **Imagen previa** y **Imagen posterior**. Cuando se configuran, estas imágenes estarán disponibles en el contexto de ejecución como propiedades <xref:Microsoft.Xrm.Sdk.IExecutionContext.PreEntityImages> y <xref:Microsoft.Xrm.Sdk.IExecutionContext.PostEntityImages> respectivamente. Como los nombres sugieren, estas instantáneas representan el aspecto que tiene la entidad antes de la operación y tras la operación. Cuando configura una imagen de la entidad, definirá un valor *alias de entidad* que será el valor clave que se usará para acceder a una imagen específica de la entidad desde las propiedades `PreEntityImages` o `PostEntityImages`.

#### <a name="availability-of-images"></a>Disponibilidad de imágenes

Cuando configura una imagen de la entidad es importante que reconozca que el tipo de imágenes de la entidad disponibles depende de la fase de paso registrado y del tipo de operación. Por ejemplo:

- No puede tener una **Imagen previa** para el mensaje `Create` porque la entidad aún no existe.
- No puede tener una **Imagen posterior** para el mensaje `Delete` porque la entidad ya no existirá.
- Puede tener solo una **Imagen posterior** para los pasos registrados en la fase **PostOperation** de la canalización de ejecución porque no hay forma de conocer cuáles serán las propiedades de la entidad hasta que se complete la transacción.
- Para una operación `Update` que se registra en la fase **PostOperation** puede tener una **Imagen previa** Y una **Imagen posterior**.


#### <a name="add-an-entity-image"></a>Agregar imagen de la entidad

Vea el paso [Agregar una imagen](tutorial-update-plug-in.md#add-an-image) en el [Tutorial: Actualizar un complemento](tutorial-update-plug-in.md) para los pasos para agregar una imagen de la entidad.

### <a name="add-step-to-solution"></a>Agregar paso a solución

Como se ha indicado en [Agregar el ensamblado a una solución](#add-your-assembly-to-a-solution), los **Ensamblados de complemento** son componentes de la solución que se pueden agregar a una solución no administrada. Los **Pasos de procesamiento de mensajes de SDK** son también componentes de la solución y también se deben agregar a una solución no administrada para distribuir.

El procedimiento para agregar un paso a una solución es similar a agregar un ensamblado. Usará el comando **Agregar existentes** para moverlo a la solución no administrada deseada. La única diferencia es que si intenta agregar un paso pero que aún no haya agregado el ensamblado que contiene la clase usada en el paso, se le pedirá que agregue los componentes necesarios que faltan.

![Diálogo Faltan componentes necesarios](media/missing-required-component.png)

Si encuentra esto, debe seleccionar **Aceptar** normalmente para llevar el ensamblado con la solución no administrada. La única vez que no seleccionaría esto es si la solución está diseñado para instalarse en un entorno donde otra solución que contiene el ensamblado ya está instalada.

De forma similar, debe tener en cuenta que al quitar el ensamblado de la solución no quitará ningún paso que dependa de ella.

## <a name="update-an-assembly"></a>Actualizar un ensamblado

Cuando cambia y vuelva a crear un ensamblado que ya ha registrado anteriormente, deberá actualizarlo. Consulte el paso [Actualizar el registro de ensamblado del complementos](tutorial-update-plug-in.md#update-the-plug-in-assembly-registration) en el [Tutorial: Actualizar un complemento](tutorial-update-plug-in.md) para conocer los pasos.

### <a name="assembly-versioning"></a>Versiones de ensamblado

Se está realizando cambios a un complemento de ensamblado que forma parte de una solución administrada que se ha implementado debe considerar el impacto que pueden tener los cambios al actualizar esa solución administrada. La versión del ensamblado controlará el comportamiento.

Pueden crearse versiones de los ensamblados del complemento con un formato semántico de control de versiones de `major.minor.build.revision` definido en el archivo `Assembly.info` del proyecto de Microsoft Visual Studio. Según la parte del número de versión de ensamblado que se cambie en una solución más reciente, se aplica el siguiente comportamiento cuando se actualiza una solución existente a través de la importación.

- **Se modifica el número de versión de compilación o de ensamblado de revisión**

  Esto se considera una actualización en contexto. La versión anterior del ensamblado desaparece cuando se importa la solución que contiene el ensamblado actualizado. Los pasos preexistentes de la solución anterior cambian automáticamente para hacer referencia a la versión más reciente del ensamblado.

- **Se modifica el número de versión principal o secundaria del ensamblado**

  Cuando una solución actualizada que contiene el ensamblado revisado se importa, el ensamblado se considera un ensamblado completamente distinto al de la versión anterior del ensamblado en la solución existente. Los pasos de registro de complementos de la solución existente continuarán haciendo referencia a la versión anterior del ensamblado. Si desea que los pasos de registro de complementos para el ensamblado anterior señalen al ensamblado revisado, deberá usar la herramienta de registro de complementos para cambiar manualmente la configuración del paso para hacer referencia al tipo de ensamblado revisado. Esto debe hacerse antes de exportar el ensamblado actualizado a una solución para importación posterior.


## <a name="unregister-or-disable-plug-in-components"></a>Anule el registre o deshabilite componentes de complementos

Puede anular el registro o deshabilitar componentes de complementos.

### <a name="unregister-components"></a>Anular el registro de componentes

PRT proporciona comandos para anular el registro de ensamblados, tipos, pasos e imágenes. Consulte las instrucciones de [Anular registro de ensamblado, complemento y paso](tutorial-update-plug-in.md#unregister-assembly-plug-in-and-step) en el [Tutorial: Actualizar un complemento](tutorial-update-plug-in.md) para conocer el procedimiento.

Éstas son operaciones de eliminación en las entidades [PluginAssembly](reference/entities/pluginassembly.md), [PluginType](reference/entities/plugintype.md), [SdkMessageProcessingStep](reference/entities/sdkmessageprocessingstep.md) y [SdkMessageProcessingStepImage](reference/entities/sdkmessageprocessingstepimage.md).

También puede eliminar **Ensamblados de complementos** y **Pasos de procesamiento de mensajes de SDK** en el explorador de soluciones para lograr los mismos resultados. En la figura siguiente se muestra una solución personalizada llamada Solución predeterminada de Common Data Service.

![Eliminar el paso en el Explorador de soluciones](media/delete-sdk-message-processing-step.png)

> [!NOTE]
> No puede eliminar **Ensamblados de complementos** mientras haya **Pasos de procesamiento de mensajes de SDK** existentes que dependen de ellos. Las imágenes de la entidad no están disponibles para eliminar por separado, pero se eliminarán cuando se eliminen los pasos que los usan.

### <a name="disable-steps"></a>Deshabilitar pasos

PRT proporciona comandos para deshabilitar y habilitar pasos.

![deshabilitar un paso mediante PRT](media/disable-step-prt.png)

![habilitar un paso mediante PRT](media/enable-step-prt.png)

También puede deshabilitar pasos en el explorador de soluciones mediante los comandos **Activar** y **Desactivar**.

![foo](media/step-activate-deactivate-commands-solution-explorer.png)

## <a name="next-steps"></a>Pasos siguientes

[Depuración de complementos](debug-plug-in.md)

### <a name="see-also"></a>Vea también
[Escriba complementos para ampliar los procesos de negocio](plug-ins.md)<br />
[Escribir un complemento](write-plug-in.md)<br />
[Tutorial: Escribir y registrar un complemento](tutorial-write-plug-in.md)<br />
[Tutorial: Depurar un complemento](tutorial-debug-plug-in.md)<br />
[Tutorial: Actualizar un complemento](tutorial-update-plug-in.md)<br />
