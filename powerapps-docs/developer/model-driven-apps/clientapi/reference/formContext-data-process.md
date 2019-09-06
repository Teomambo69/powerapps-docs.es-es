---
title: formContext.data.process (referencia API de cliente) en aplicaciones basadas en modelo| Microsoft Docs
description: Aprenda a trabajar con procesos en aplicaciones basadas en modelos mediante la API de cliente.
ms.date: 06/30/2019
ms.service: powerapps
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 32e8d1d0-4093-4588-a517-2930eec34dce
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="formcontextdataprocess-client-api-reference"></a>formContext.data.process (referencia de la API de cliente)



Proporciona eventos, métodos y objetos para interactuar con los datos del flujo de proceso de negocio en un formulario. Vea [formContext.ui.process (referencia de la API de cliente)](formContext-ui-process.md) para métodos para interactuar con el control de flujo de proceso de negocio en el formulario.

## <a name="process-events-and-event-handler-methods"></a>Métodos de controlador de eventos y procesos de eventos

Utilice los siguientes eventos y métodos de controlador de eventos para escribir secuencias para flujos de procesos de negocio.

|Evento | Métodos de controlador de eventos|
|--|--|
|[OnPreProcessStatusChange](events/onpreprocessstatuschange.md)|[addOnPreProcessStatusChange](formContext-data-process/eventhandlers/addOnPreProcessStatusChange.md)<br/>[removeOnPreProcessStatusChange](formContext-data-process/eventhandlers/removeOnPreProcessStatusChange.md)|
|[OnProcessStatusChange](events/onprocessstatuschange.md)|[addOnProcessStatusChange](formContext-data-process/eventhandlers/addOnProcessStatusChange.md)<br/>[removeOnProcessStatusChange](formContext-data-process/eventhandlers/removeOnProcessStatusChange.md)|
|[OnStageChange](events/OnStageChange.md)|[addOnStageChange](formContext-data-process/eventhandlers/addOnStageChange.md)<br/>[removeOnStageChange](formContext-data-process/eventhandlers/removeOnStageChange.md)|
|[OnStageSelected](events/OnStageSelected.md)|[addOnStageSelected](formContext-data-process/eventhandlers/addOnStageSelected.md)<br/>[removeOnStageSelected](formContext-data-process/eventhandlers/removeOnStageSelected.md)|

## <a name="active-process-methods"></a>Métodos de proceso activo

Use estos métodos para recuperar información sobre el proceso activo y para definir otro proceso como proceso activo.

|Nombre | Descripción |
|--|--|
|[getActiveProcess](formcontext-data-process/activeprocess/getActiveProcess.md)|[!INCLUDE[formcontext-data-process/activeprocess/includes/getActiveProcess-description.md](formcontext-data-process/activeprocess/includes/getActiveProcess-description.md)]|
|[setActiveProcess](formcontext-data-process/activeprocess/setActiveProcess.md)|[!INCLUDE[formcontext-data-process/activeprocess/includes/setActiveProcess-description.md](formcontext-data-process/activeprocess/includes/setActiveProcess-description.md)]|

## <a name="process-methods"></a>Métodos de proceso 

Un proceso contiene los datos para un flujo de proceso de negocio. Uso los métodos para obtener acceso a las propiedades del proceso.

|Nombre | Descripción |
|--|--|
|[getId](formcontext-data-process/process/getId.md)|[!INCLUDE[formcontext-data-process/process/includes/getId-description.md](formcontext-data-process/process/includes/getId-description.md)]|
|[getName](formcontext-data-process/process/getName.md)|[!INCLUDE[formcontext-data-process/process/includes/getName-description.md](formcontext-data-process/process/includes/getName-description.md)]|
|[getStages](formcontext-data-process/process/getStages.md)|[!INCLUDE[formcontext-data-process/process/includes/getStages-description.md](formcontext-data-process/process/includes/getStages-description.md)]|
|[isRendered](formcontext-data-process/process/isRendered.md)|[!INCLUDE[formcontext-data-process/process/includes/isRendered-description.md](formcontext-data-process/process/includes/isRendered-description.md)]|


## <a name="processinstance-methods"></a>Métodos ProcessInstance

Use estos métodos para recuperar información sobre todas las instancias de proceso para que un registro de entidad y para establecer una instancia de proceso como instancia activa.

|Nombre | Descripción |
|--|--|
|[getProcessInstances](formContext-data-process/getProcessInstances.md)|[!INCLUDE[formcontext-data-process/includes/getProcessInstances-description.md](formcontext-data-process/includes/getProcessInstances-description.md)]|
|[setActiveProcessInstance](formContext-data-process/setActiveProcessInstance.md)|[!INCLUDE[formcontext-data-process/includes/setActiveProcessInstance-description.md](formcontext-data-process/includes/setActiveProcessInstance-description.md)]|


## <a name="instance-methods"></a>Método de instancia 

Una instancia de proceso contiene los datos para una instancia del flujo de proceso de negocio. Uso los métodos para obtener acceso a las propiedades de la instancia de proceso.

|Nombre | Descripción |
|--|--|
|[getInstanceId](formcontext-data-process/instance/getInstanceId.md)|[!INCLUDE[formcontext-data-process/instance/includes/getInstanceId-description.md](formcontext-data-process/instance/includes/getInstanceId-description.md)]|
|[getInstanceName](formcontext-data-process/instance/getInstanceName.md)|[!INCLUDE[formcontext-data-process/instance/includes/getInstanceName-description.md](formcontext-data-process/instance/includes/getInstanceName-description.md)]|
|[getStatus](formcontext-data-process/instance/getStatus.md)|[!INCLUDE[formcontext-data-process/instance/includes/getStatus-description.md](formcontext-data-process/instance/includes/getStatus-description.md)]|
|[setStatus](formcontext-data-process/instance/setStatus.md)|[!INCLUDE[formcontext-data-process/instance/includes/setStatus-description.md](formcontext-data-process/instance/includes/setStatus-description.md)]|

## <a name="active-stage-methods"></a>Métodos de fase activa

Use estos métodos para recuperar la información sobre la fase activa y para establecer otra fase como la fase activa.

|Nombre | Descripción |
|--|--|
|[getActiveStage](formcontext-data-process/activestage/getActiveStage.md)|[!INCLUDE[formcontext-data-process/activestage/includes/getActiveStage-description.md](formcontext-data-process/activestage/includes/getActiveStage-description.md)]|
|[setActiveStage](formcontext-data-process/activestage/setActiveStage.md)|[!INCLUDE[formcontext-data-process/activestage/includes/setActiveStage-description.md](formcontext-data-process/activestage/includes/setActiveStage-description.md)]|

## <a name="stage-methods"></a>Métodos de fase 

Una fase contiene los datos para una fase en un flujo de proceso de negocio. Uso los métodos para obtener acceso a las propiedades de la fase.
|Nombre | Descripción|
|--|--|
|[getCategory](formcontext-data-process/stage/getCategory.md)|[!INCLUDE[formcontext-data-process/stage/includes/getCategory-description.md](formcontext-data-process/stage/includes/getCategory-description.md)]|
|[getEntityName](formcontext-data-process/stage/getEntityName.md)|[!INCLUDE[formcontext-data-process/stage/includes/getEntityName-description.md](formcontext-data-process/stage/includes/getEntityName-description.md)]|
|[getId](formcontext-data-process/stage/getId.md)|[!INCLUDE[formcontext-data-process/stage/includes/getId-description.md](formcontext-data-process/stage/includes/getId-description.md)]|
|[getName](formcontext-data-process/stage/getName.md)|[!INCLUDE[formcontext-data-process/stage/includes/getName-description.md](formcontext-data-process/stage/includes/getName-description.md)]|
|[getNavigationBehavior](formcontext-data-process/stage/getNavigationBehavior.md)|[!INCLUDE[formcontext-data-process/stage/includes/getNavigationBehavior-description.md](formcontext-data-process/stage/includes/getNavigationBehavior-description.md)]|
|[getStatus](formcontext-data-process/stage/getStatus.md)|[!INCLUDE[formcontext-data-process/stage/includes/getStatus-description.md](formcontext-data-process/stage/includes/getStatus-description.md)]|
|[getSteps](formcontext-data-process/stage/getSteps.md)|[!INCLUDE[formcontext-data-process/stage/includes/getSteps-description.md](formcontext-data-process/stage/includes/getSteps-description.md)]|

## <a name="step-methods"></a>Métodos de paso

Un paso contiene los datos para un paso de una fase de un flujo de proceso de negocio. Uso los métodos para obtener acceso a las propiedades del paso.

|Nombre | Descripción|
|--|--|
|[getAttribute](formcontext-data-process/step/getAttribute.md)|[!INCLUDE[formcontext-data-process/step/includes/getAttribute-description.md](formcontext-data-process/step/includes/getAttribute-description.md)]|
|[getName](formcontext-data-process/step/getName.md)|[!INCLUDE[formcontext-data-process/step/includes/getName-description.md](formcontext-data-process/step/includes/getName-description.md)]|
|[getProgress](formcontext-data-process/step/getProgress.md)|[!INCLUDE[formcontext-data-process/step/includes/getProgress-description.md](formcontext-data-process/step/includes/getProgress-description.md)]|
|[isRequired](formcontext-data-process/step/isRequired.md)|[!INCLUDE[formcontext-data-process/step/includes/isRequired-description.md](formcontext-data-process/step/includes/isRequired-description.md)]|
|[setProgress](formcontext-data-process/step/setProgress.md)|[!INCLUDE[formcontext-data-process/step/includes/setProgress-description.md](formcontext-data-process/step/includes/setProgress-description.md)]|

## <a name="navigation-methods"></a>Métodos de navegación

Utilice estos métodos para desplazarse a etapas anteriores y siguientes. Ambos métodos harán que se produzca el evento OnStageChange.

|Nombre | Descripción|
|--|--|
|[moveNext](formContext-data-process/navigation/moveNext.md)|[!INCLUDE[formcontext-data-process/navigation/includes/moveNext-description.md](formcontext-data-process/navigation/includes/moveNext-description.md)]|
|[movePrevious](formContext-data-process/navigation/movePrevious.md)|[!INCLUDE[formcontext-data-process/navigation/includes/movePrevious-description.md](formcontext-data-process/navigation/includes/movePrevious-description.md)]|

## <a name="other-useful-methods"></a>Otros métodos útiles

Utilice estos métodos para obtener información sobre las fases en la ruta activa, procesos habilitados y fase seleccionada.

|Nombre | Descripción|
|--|--|
|[getActivePath](formContext-data-process/activepath/getActivePath.md)|[!INCLUDE[formcontext-data-process/activepath/includes/getActivePath-description.md](formcontext-data-process/activepath/includes/getActivePath-description.md)]|
|[getEnabledProcesses](formContext-data-process/getEnabledProcesses.md)|[!INCLUDE[formcontext-data-process/includes/getEnabledProcesses-description.md](formcontext-data-process/includes/getEnabledProcesses-description.md)]|
|[getSelectedStage](formContext-data-process/getSelectedStage.md)|[!INCLUDE[formcontext-data-process/includes/getSelectedStage-description.md](formcontext-data-process/includes/getSelectedStage-description.md)]|

### <a name="related-topics"></a>Temas relacionados

[formContext.ui.process (referencia de la API de cliente)](formContext-ui-process.md)

[Comprender el modelo de objetos Xrm](../understand-clientapi-object-model.md)

[Controles (referencia de la API de cliente)](controls.md)




