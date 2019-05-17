---
title: Solución de problemas de complementos (Common Data Service para aplicaciones) | Microsoft Docs
description: Contiene información sobre los errores que se puedan producir debido a complementos y cómo corregirlos.
ms.custom: ''
ms.date: 04/21/2019
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
---
# <a name="troubleshoot-plug-ins"></a>Solución de problemas de complementos 

Este tema contiene información sobre los errores que se puedan producir debido a complementos y cómo corregirlos.

## <a name="error-there-is-no-active-transaction"></a>Error: No hay transacción activa. 

Código de error: `-2147220911`<br />
Mensaje de error: `There is no active transaction. This error is usually caused by custom plug-ins that ignore errors from service calls and continue processing.`

Este puede ser un error difícil de solucionar porque la causa puede estar en el código de otra persona. Para comprender el mensaje, debe apreciar que en el momento en que se produce un error relacionado con una operación de datos en un complemento sincrónico, se terminará la transacción de toda la operación.
[Diseño de personalización escalable en Common Data Service](scalable-customization-design/overview.md) La causa más común es simplemente que un desarrollador puede creer que puede intentar realizar una operación que *podría* tener éxito, por lo que envuelven esa operación en un bloque try/catch e intentan de tragar el error si produce error.

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