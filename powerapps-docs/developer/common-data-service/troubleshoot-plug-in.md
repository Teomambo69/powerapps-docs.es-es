---
title: Solución de problemas complementos (Common Data Service for Apps) | Microsoft Docs
description: Contiene información sobre los errores que se puedan producir debido a complementos y cómo corregirlos.
ms.custom: ''
ms.date: 09/18/2019
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
ms.openlocfilehash: ea933534c38686a3766d52b98b82c96f878c13f0
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749782"
---
# <a name="troubleshoot-plug-ins"></a>Solución de problemas de complementos 

Este tema contiene información sobre los errores que se puedan producir debido a complementos y cómo corregirlos.

## <a name="transaction-errors"></a>Errores de transacción

Hay dos tipos comunes de errores relacionados con las transacciones: 

Código de error: `-2146893812`<br />
Mensaje de error: `ISV code reduced the open transaction count. Custom plug-ins should not catch exceptions from OrganizationService calls and continue processing.`

Código de error: `-2147220911`<br />
Mensaje de error: `There is no active transaction. This error is usually caused by custom plug-ins that ignore errors from service calls and continue processing.`

> [!NOTE]
> El error principal se agregó más recientemente. Debe aparecer inmediatamente y en el contexto del complemento que contiene el problema. El error inferior todavía puede aparecer en diferentes circunstancias, implicando normalmente actividades personalizadas del flujo de trabajo. Puede deberse a problemas en otro complemento.

Para comprender el mensaje, debe apreciar que en el momento en que se produce un error relacionado con una operación de datos en un complemento sincrónico, se terminará la transacción de toda la operación.

Más información: [Diseño de personalización escalable en Common Data Service](scalable-customization-design/overview.md)

La causa más común es simplemente que un desarrollador puede creer que puede intentar realizar una operación que *podría* tener éxito, por lo que envuelven esa operación en un bloque try/catch e intentan de tragar el error si produce error.

Si bien esto puede funcionar para una aplicación cliente, en la ejecución de un complemento los errores de operaciones de datos harán que se revierta toda la transacción. No se puede tragar el error, por lo que debe asegurarse de siempre devolver un <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException>.

## <a name="error-sql-error-execution-timeout-expired"></a>Error: Error de Sql: Se agotó el tiempo de espera de ejecución

Código de error: `-2147204783`<br />
Mensaje de error: `Sql error: 'Execution Timeout Expired.  The timeout period elapsed prior to completion of the operation or the server is not responding.'`

Existe una gran variedad de razones por las que un error de tiempo de espera de SQL puede producirse.

### <a name="blocking"></a>Bloqueo

El bloqueo es la causa más común en un error de tiempo de espera de SQL, en el que la operación espera recursos que está bloqueando otra transacción SQL. El error es el resultado de que el sistema protege la integridad de los datos y las solicitudes de larga duración que impactan en el rendimiento para los usuarios.

El bloqueo puede deberse a otras operaciones simultáneas. El código puede funcionar bien en aislamiento en un entorno de prueba y seguir siendo susceptible a las condiciones que solo aparecerán cuando varios usuarios estén iniciando la lógica en el complemento.

Al escribir complementos, es importante comprender cómo diseñar personalizaciones que son escalables. Más información: [Diseño de personalización escalable en Common Data Service](scalable-customization-design/overview.md)

### <a name="cascade-operations"></a>Operaciones en cascada

Algunas acciones que usted realiza en el complemento, como asignar o eliminar un registro, pueden iniciar operaciones en cascada en los registros relacionados. Estas acciones pueden aplicar bloqueos en registros relacionados, provocando el bloqueo de operaciones de datos posteriores, lo que a su vez pueden producir un tiempo de espera de SQL. 

Debe considerar el impacto posible de estas operaciones en cascada en las operaciones de datos del complemento. Más información: [Comportamiento de las relaciones de entidad](../../maker/common-data-service/entity-relationship-behavior.md)

Puesto que estos comportamientos se pueden configurar de forma diferente entre los entornos, el comportamiento puede resultar difícil de reproducir a menos que los entornos estén configuradas del mismo modo.

### <a name="indexes-on-new-entities"></a>Índices en entidades nuevas

Si el complemento está realizando operaciones usando una entidad o un atributo que se ha creado recientemente, algunas capacidades de Azure SQL para administrar índices pueden suponer una diferencia después de unos días.

## <a name="errors-due-to-user-privileges"></a>Errores debidos a privilegios de usuario

En una aplicación cliente puede deshabilitar comandos que los usuarios no están autorizados a realizar. En un complemento no tiene esto. El código puede incluir alguna automatización para la que el usuario que llama no tiene privilegios.

Puede registrar el complemento para ejecutarse en el contexto de un usuario conocido para tener los privilegios correctos estableciendo el valor **Ejecutar en contexto de usuario** a ese usuario. O bien puede ejecutar la operación suplantando a otro usuario. Más información:
 - [Registro de un complemento](register-plug-in.md)
 - [Suplantar a un usuario](impersonate-a-user.md)

<!-- But if you prefer that the logic in your plug-in adapt to the privileges that the calling user has, you really need to verify the user's privileges in your code.

TODO: Add content that shows how to do this -->

## <a name="error-message-size-exceeded-when-sending-context-to-sandbox"></a>Error: Se ha superado el tamaño de mensaje al enviar contexto a espacio aislado

<!-- This is the error code for an unexpected error we should be providing a specific error code. Bug 1470173 is tracking this. -->
Código de error: `-2147220970`<br />
Mensaje de error: `Message size exceeded when sending context to Sandbox. Message size: ### Mb`

Este error se produce cuando la carga de un mensaje es superior a 116,85 MB **Y** un complemento se registra para el mensaje. El mensaje de error incluirá el tamaño de la carga que produjo este error.
 
El límite le ayudará a asegurarse de que los usuarios que ejecuten aplicaciones no puedan interferir unos con otros basándose en limitaciones de recursos. El límite le ayudará a proporcionar cierto grado de protección contra cargas de mensaje excesivamente grandes que ponen en peligro las características de disponibilidad y rendimiento de la plataforma Common Data Service.
 
116,85 MB es bastante grande, por lo que debería ser raro que se produzca este caso. La situación más probable donde puede producirse este caso es cuando se recupera un registro con varios registros relacionados que incluyen archivos binarios grandes.
 
Si encuentra este error, puede hacer lo siguiente:

1.  Quitar el complemento del mensaje. Si no complementos registrados para el mensaje, la operación se completará sin un error.
2.  Si el error se produce en un cliente personalizado, puede modificar el código de forma que no intente realizar el trabajo en una sola operación. En su lugar, escriba código para recuperar los datos en partes menores.

## <a name="error-the-given-key-was-not-present-in-the-dictionary"></a>Error: La clave dada no estaba en el diccionario

Common Data Service usa con frecuencia clases derivadas de la clase abstracta <xref:Microsoft.Xrm.Sdk.DataCollection`2> que representa una colección de claves y valores. Por ejemplo, con los complementos la propiedad <xref:Microsoft.Xrm.Sdk.IExecutionContext>.<xref:Microsoft.Xrm.Sdk.IExecutionContext.InputParameters> es una <xref:Microsoft.Xrm.Sdk.ParameterCollection> derivada de la clase <xref:Microsoft.Xrm.Sdk.DataCollection`2>. Estas clases son esencialmente objetos de diccionario en las que puede tener acceso a un valor específico con el nombre de clave.

### <a name="error-codes"></a>Códigos de error

Este error se produce cuando el valor de clave en código no existe en la colección. Se trata de un error en tiempo de ejecución en lugar de un error de plataforma. Cuando este error aparece en un complemento, el código de error dependerá de si el error se capturó.

Si el desarrollador capturó la excepción y devolvió una <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> como se describe en[ Administrar excepciones en complementos](handle-exceptions.md), el siguiente error será devuelto:

Código de error: `-2147220891`<br />
Mensaje de error: `ISV code aborted the operation.`

No obstante, con este error es común que el desarrollador no lo capture correctamente y el siguiente error será devuelto:

Código de error: `-2147220956`<br />
Mensaje de error: `An unexpected error occurred from ISV code.`

> [!NOTE]
> "ISV" son las siglas de *Fabricante independiente de software*.

### <a name="causes"></a>Causas

Este error aparece con frecuencia en tiempo de diseño y puede deberse a la falta de ortografía o al uso incorrecto de mayúsculas y minúsculas. Los valores de clave distinguen entre mayúsculas y minúsculas.

En tiempo de ejecución el error es debido con frecuencia a que el desarrollador asume que el valor estará presente, aunque no lo estará. Por ejemplo, en un complemento que se registra para la actualización de una entidad, solo se incluirán los valores que se cambien en la <xref:Microsoft.Xrm.Sdk.Entity>.<xref:Microsoft.Xrm.Sdk.Entity.Attributes> .

### <a name="prevention"></a>Prevención

Para evitar este error que debe comprobar que existe la clave antes de intentar usarla para tener acceso a un valor. 

Por ejemplo, cuando tenga acceso a un atributo de entidad, puede usar el método <xref:Microsoft.Xrm.Sdk.Entity>.<xref:Microsoft.Xrm.Sdk.Entity.Contains(System.String)> para comprobar si un atributo existe en una entidad como se muestra en el siguiente código.

```csharp
// Obtain the execution context from the service provider.  
IPluginExecutionContext context = (IPluginExecutionContext)
    serviceProvider.GetService(typeof(IPluginExecutionContext));

// The InputParameters collection contains all the data passed in the message request.  
if (context.InputParameters.Contains("Target") &&
    context.InputParameters["Target"] is Entity)
    {
    // Obtain the target entity from the input parameters.  
    Entity entity = (Entity)context.InputParameters["Target"];

    //Check whether the name attribute exists.
    if(entity.Contains("name"))
    {
        string name = entity["name"];
    }
```

Algunos desarrolladores usan el método <xref:Microsoft.Xrm.Sdk.Entity>.<xref:Microsoft.Xrm.Sdk.Entity.GetAttributeValue``1(System.String)> para evitar este error cuando acceden a atributos de entidad, pero tenga en cuenta que este método devolverá el valor predeterminado del tipo si no existe el atributo. Si el valor predeterminado es nulo, esto funciona como se espera. Pero si el valor predeterminado no devuelve null, por ejemplo con un `DateTime`, el valor devuelto será `1/1/0001 00:00` en lugar de null.