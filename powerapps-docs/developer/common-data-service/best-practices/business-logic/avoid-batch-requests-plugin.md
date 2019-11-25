---
title: Evitar el uso de tipos de la solicitud por lotes en complementos y actividades de flujo de trabajo | MicrosoftDocs
description: No debería usar clases de solicitud de mensajes ExecuteMultipleRequest o ExecuteTransactionRequest en situaciones con complementos o actividad de flujo de trabajo.
services: ''
suite: powerapps
documentationcenter: na
author: jowells
manager: austinj
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 1/15/2019
ms.author: jowells
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: e0732dfee3d4824f33042936af7e8f6157bcec83
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749400"
---
# <a name="avoid-usage-of-batch-request-types-in-plug-ins-and-workflow-activities"></a>Evite usar de tipos de solicitud por lotes en complementos y actividades de flujo de trabajo

**Categoría**: uso, fiabilidad, rendimiento

**Potencial de impacto**: medio

<a name='symptoms'></a>

## <a name="symptoms"></a>Síntomas

A continuación se describen efectos posibles cuando se usan las clases de solicitud de mensajes <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> o <xref:Microsoft.Xrm.Sdk.Messages.ExecuteTransactionRequest> en situaciones con complementos o actividad de flujo de trabajo.

- Debido a la naturaleza de ejecución prolongada, los mensajes de solicitud por lotes exponen tipos de complemento en espacios aislados para la excepción de tiempo de espera del canal de dos minutos (2000-ms) y puede mermar la experiencia del usuario para los registros síncronos.

- La solicitudes por lotes están sujetas a la limitación de simultaneidad, que se puede producir excepciones innecesarias de servidor ocupado cuando se varios subprocesos ejecutan el complemento. Hay un límite de dos operaciones `ExecuteMultiple` simultáneas por cada instancia conectada.

    > [!NOTE]
    > En implementaciones locales, la configuración de [ExecuteAsyncPerOrMaxConnectionsPerServer](/dotnet/api/microsoft.xrm.sdk.deployment.throttlesettings.executeasyncmaxconnectionsperserver) habilita la misma limitación.  De forma predeterminada, no se define para entornos locales.

<a name='guidance'></a>

## <a name="guidance"></a>Instrucciones

Use estos mensajes por lotes cuando se ejecute código fuera de la canalización de ejecución de la plataforma, como en escenarios de integración donde la latencia de red reduciría el rendimiento e incrementaría la duración de operaciones masivas más voluminosas.

Más concretamente, úselos en los siguientes casos:

- Use <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> para cargar datos o procesos externos de forma masiva dirigidos a ejecutar operaciones prolongadas (superiores a dos minutos).

- Use <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> para minimizar los viajes de ida y vuelta entre los servidores del cliente personalizado y Microsoft Dynamics 365, lo que reduce consiguientemente la latencia total acumulada.

- Use <xref:Microsoft.Xrm.Sdk.Messages.ExecuteTransactionRequest> para clientes externos que requieren confirmar el lote de operaciones como una transacción o reversión de base de datos única y atómica si se producen excepciones. Tenga en cuenta un posible bloqueo de la base de datos mientras dure la transacción prolongada.

<a name='problem'></a>

## <a name="problematic-patterns"></a>Patrones problemáticos

A continuación, se ofrece un ejemplo de uso de <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> con un complemento.

> [!WARNING]
> Este escenario debe evitarse.

```csharp
public class ExecuteMultipleRequestInPlugin : IPlugin
{
    public void Execute(IServiceProvider serviceProvider)
    {
        IPluginExecutionContext context = (IPluginExecutionContext)serviceProvider.GetService(typeof(IPluginExecutionContext));
        IOrganizationServiceFactory factory = (IOrganizationServiceFactory)serviceProvider.GetService(typeof(IOrganizationServiceFactory));
        IOrganizationService service = factory.CreateOrganizationService(context.UserId);

        QueryExpression query = new QueryExpression("account")
        {
            ColumnSet = new ColumnSet("accountname", "createdon"),
        };

        //Obtain the results of previous QueryExpression
        EntityCollection results = service.RetrieveMultiple(query);

        if (results != null && results.Entities != null && results.Entities.Count > 0)
        {
            ExecuteMultipleRequest batch = new ExecuteMultipleRequest();
            foreach (Entity account in results.Entities)
            {
                account.Attributes["accountname"] += "_UPDATED";

                UpdateRequest updateRequest = new UpdateRequest();
                updateRequest.Target = account;

                batch.Requests.Add(updateRequest);
            }

            service.Execute(batch);
        }
        else return;

    }
}
```

Este ejemplo incluye el uso del tipo directamente con el método `Execute`. Este tipo de uso puede darse en cualquier momento durante la ejecución de un complemento o una actividad de flujo de trabajo. Esto podría ser también en un método contenido en la misma clase o en otra distinta. No se limita a estar directamente contenido en la definición del método `Execute`.

<a name='additional'></a>

## <a name="additional-information"></a>Información adicional

Los mensajes `ExecuteMultiple` y `ExecuteTransaction` se consideran mensajes de solicitud por lotes. Su objetivo es minimizar acciones de ida y vuelta entre el cliente y el servidor en conexiones latencia alta. Los complementos se ejecutan directamente en el proceso de la aplicación o muy cerca cuando están en espacios aislados y la latencia no suele ser un problema. El código del complemento tienen que ser operaciones muy concisas que se ejecuten rápidamente y minimicen el bloqueo para evitar superar los umbrales de tiempo de espera y asegurarse de que el sistema es dinámico en escenarios sincrónicos.

En el servidor, las operaciones incluidas en una solicitud por lotes se ejecutan de forma secuencial y no se realizan en paralelo. Es así aunque la propiedad <xref:Microsoft.Xrm.Sdk.ExecuteMultipleSettings>.<xref:Microsoft.Xrm.Sdk.ExecuteMultipleSettings.ReturnResponses> se haya establecido en false. Los programadores tienden a usar solicitudes por lotes de esta manera sabiendo que permitirán el procesamiento en paralelo. La solicitudes por lotes no lograrán este objetivo. Otro factor de motivación común es intentar asegurarse de que cada operación esté incluida en una transacción. Esto no es necesario porque el complemento ya se está ejecutando en la transacción de base de datos, lo que no hace necesario utilizar el mensaje `ExecuteTransaction`.

<a name='seealso'></a>

### <a name="see-also"></a>Vea también

[Marco de trabajo de eventos](../../event-framework.md)<br />
[Limitaciones al tiempo de ejecución](../../org-service/execute-multiple-requests.md#run-time-limitations)<br/>
[Ejecutar varias solicitudes con el servicio de la organización](../../org-service/execute-multiple-requests.md)<br/>
[Ejecutar mensajes en una sola transacción de la base de datos](../../org-service/use-executetransaction.md)
