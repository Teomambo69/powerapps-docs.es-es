---
title: Administrar excepciones en un complemento (Common Data Service) | Microsoft Docs
description: Conocer el comportamiento del sistema cuando un complemento devuelva una excepción al autor de la llamada.
ms.custom: ''
ms.date: 1/23/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: pehecke
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="handle-exceptions-in-plug-ins"></a>Administrar las excepciones en complementos

Hay dos posibles resultados cuando un complemento permite que se devuelva una excepción al sistema D365: la información sobre la excepción no está registrada ni se muestra al usuario y la solicitud actual de mensaje que se está procesando está cancelada. El comportamiento exacto como según se describe a continuación depende de cómo se ejecuta el complemento: en el espacio aislado o no, de forma sincrónica o asincrónica.

<a name='cancelling-an-operation'></a>

## <a name="cancelling-the-current-operation"></a>Cancelar la operación actual

El código puede producir que la operación de solicitud de mensaje actual se cancele lanzando una excepción o devolviendo una excepción desconocida al sistema D365. Cualquier excepción devuelta al autor de la llamada del complemento hará que la operación actual se cancele, por lo que es importante que aplique prácticas recomendadas de código para administrar las excepciones que se lancen y decidir si permite que la excepción cancele la operación actual o no.

Si la lógica de negocios dicta que la operación debe ser cancelada, debe lanzar una excepción <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> y proporcionar un mensaje para explicar por qué la operación se ha cancelado.

Idealmente, debe cancelar solo operaciones que utilicen complementos síncronos registrados en la fase de **PreValidation**. Esta fase *normalmente* se produce fuera de la transacción de la base de datos principal. La cancelación de una operación antes de que alcance la transacción es muy deseable porque la operación cancelada tiene que revertirse. La reversión de la operación requiere recursos significado y tiene un impacto en el rendimiento del sistema. Las operaciones en las fases **PreOperation** y **PostOperation** están siempre en la transacción de la base de datos.

Las fases **PreValidation** a veces estarán en una transacción cuando las inicie la lógica en otra operación. Por ejemplo, si crea un registro de entidad de tarea en la fase **PreOperation** de la creación de una cuenta, la creación de tarea pasará a través de la canalización de ejecuciones de eventos y se producirá en la fase **PreValidation**, pero será parte de la transacción que está creando el registro de la entidad de cuenta. Puede saber si una operación está en una transacción para el valor de la propiedad <xref:Microsoft.Xrm.Sdk.IExecutionContext>.<xref:Microsoft.Xrm.Sdk.IExecutionContext.IsInTransaction> .

## <a name="how-the-system-handles-plug-in-exceptions"></a>Cómo controla el sistema las excepciones de complementos

Cuando lanza una excepción <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> en un complemento sincrónico se mostrará al usuario un diálogo de error con el mensaje. Si no proporciona un mensaje, se mostrará un diálogo de error genérico al usuario. Si lanza a cualquier otro tipo de excepción, el usuario verá un cuadro de diálogo de error con un mensaje genérico y el mensaje de excepción y el seguimiento de la pila se escribirán en la [Entidad PluginTraceLog](reference/entities/plugintracelog.md).

El mensaje de excepción para los complementos asincrónicos registrados se escribe en un registro de trabajo del sistema [Entidad AsyncOperation](reference/entities/asyncoperation.md) que se puede ver en el área **Trabajos del sistema** de la aplicación web. No se mostrará ningún diálogo al usuario. Los complementos asincrónicos no participan en la transacción de base de datos que los colocó en la cola, por consiguiente no pueden cancelar la transacción.

> [!NOTE]
> Para los complementos locales no registrados en el espacio asilado, la información de la excepción se escribe en el registro de eventos de la aplicación del servidor de D365 que ejecuta el complemento. El registro de eventos se puede ver con la herramienta administrativa Visor de eventos.