---
title: Códigos de error de servicio web (Common Data Service) | Microsoft Docs
description: 'Este tema enumera los códigos de error que puede encontrar al depurar el código. '
ms.custom: ''
ms.date: 02/21/2020
ms.reviewer: pehecke
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
ms.openlocfilehash: 5da0e8248a1a65115f6c3ae2d084a6a6dec56cac
ms.sourcegitcommit: 0e41cc0c944e6b0ee22a7e183e40c52fd553b7be
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2020
ms.locfileid: "3081452"
---
# <a name="web-service-error-codes"></a>Códigos de error de servicio web

Este tema enumera los códigos de error que puede encontrar al depurar el código.

<a name="BKMK_CRMErrors"></a>   

## <a name="common-data-service-errors"></a>Errores Common Data Service 

 En la lista siguiente se muestran los códigos de error que se utilizan en Common Data Service. Para obtener más información, consulte [Controlar excepciones en el código](handle-exceptions-code.md).  

> [!div class="mx-tdBreakAll"]
>
> |Error|Mensaje|
> |---|---|
> |**Nombre**:<br />AADError<br />**Hex**:<br />80072559<br />**Número**:<br />-2147015335|Error de AAD|
> |**Nombre**:<br />AccessDenied<br />**Hex**:<br />80048405<br />**Número**:<br />-2147187707|Acceso denegado.|
> |**Nombre**:<br />AccessDeniedSharePointRecord<br />**Hex**:<br />80060904<br />**Número**:<br />-2147088124|Acceso denegado en registro SharePoint de Dynamics 365.|
> |**Nombre**:<br />AccessTokenExpired<br />**Hex**:<br />8005F101<br />**Número**:<br />-2147094271|El recurso solicitado requiere la autenticación.|
> |**Nombre**:<br />AccountDoesNotExist<br />**Hex**:<br />80040502<br />**Número**:<br />-2147220222|La cuenta no existe.|
> |**Nombre**:<br />AccountLoopBeingCreated<br />**Hex**:<br />80040507<br />**Número**:<br />-2147220217|La creación de esta asociación jerárquica crearía un bucle en la jerarquía de contabilidad.|
> |**Nombre**:<br />AccountLoopExists<br />**Hex**:<br />80040506<br />**Número**:<br />-2147220218|Existe un bucle en la jerarquía de la cuenta.|
> |**Nombre**:<br />ActionCardDisabledError<br />**Hex**:<br />80071100<br />**Número**:<br />-2147020544|La característica Tarjeta de acción no está habilitada.|
> |**Nombre**:<br />ActionCardInvalidStateCodeException<br />**Hex**:<br />80071103<br />**Número**:<br />-2147020541|Se pasó un código de estado no válido en la expresión.|
> |**Nombre**:<br />ActionStepInvalidPipelineStageid<br />**Hex**:<br />8006040e<br />**Número**:<br />-2147089394|ActionStep hace referencia a identificador de fase de canalización no válido.|
> |**Nombre**:<br />ActionStepInvalidProcessAction<br />**Hex**:<br />8006041c<br />**Número**:<br />-2147089380|ActionStep {0} hace referencia a una acción de proceso {1} no válido.|
> |**Nombre**:<br />ActionStepInvalidProcessid<br />**Hex**:<br />8006040d<br />**Número**:<br />-2147089395|ActionStep hace referencia a identificador de proceso no válido.|
> |**Nombre**:<br />ActionStepInvalidStageid<br />**Hex**:<br />8006040c<br />**Número**:<br />-2147089396|ActionStep hace referencia a identificador de fase no válido.|
> |**Nombre**:<br />ActionSupportNotEnabled<br />**Hex**:<br />80060382<br />**Número**:<br />-2147089534| Los procesos de negocio que contienen un paso de acción no se pueden exportar porque la compatibilidad con paso de acción es todavía una característica en Versión preliminar pública y actualmente no está habilitada para esta organización.|
> |**Nombre**:<br />ActivePropertyValidationFailed<br />**Hex**:<br />80061001<br />**Número**:<br />-2147086335|No puede crear una instancia de propiedad para una propiedad inactiva.|
> |**Nombre**:<br />ActiveQueueItemAlreadyExists<br />**Hex**:<br />80040526<br />**Número**:<br />-2147220186|Ya existe una cola activa para el objeto determinado. No se puede crear más de un elemento de cola activo para este objeto.|
> |**Nombre**:<br />ActiveSlaCannotEdit<br />**Hex**:<br />8004F871<br />**Número**:<br />-2147157903|No puede editar un SKA activo. Desactive la SLA y, a continuación, intente editarla.|
> |**Nombre**:<br />ActiveStageIdDoesNotMatchLastStageInTraversedPath<br />**Hex**:<br />80060455<br />**Número**:<br />-2147089323|El identificador de fase activa '{0}' no coincide con el último ID de fase en ruta atravesada '{1}'. Póngase en contacto con el administrador del sistema.|
> |**Nombre**:<br />ActiveStageIDIsNull<br />**Hex**:<br />80060449<br />**Número**:<br />-2147089335|Error al actualizar el proceso de negocio: el identificador de fase activa no puede estar vacío.|
> |**Nombre**:<br />ActiveStageIsNotOnLeadEntity<br />**Hex**:<br />80100002<br />**Número**:<br />-2146435070|La fase activa no está en la entidad "Cliente potencial".|
> |**Nombre**:<br />ActivityAnalysisOrganizationUpdateError<br />**Hex**:<br />80044275<br />**Número**:<br />-2147204491|La configuración de la organización de Análisis de relaciones solo se puede habilitar si está instalada la solución Análisis de relaciones.|
> |**Nombre**:<br />ActivityCannotHaveRelatedActivities<br />**Hex**:<br />8004F121<br />**Número**:<br />-2147159775|Una entidad personalizada que se define como actividad no debe tener relación con actividades.|
> |**Nombre**:<br />ActivityEntityCannotBeActivityParty<br />**Hex**:<br />80048501<br />**Número**:<br />-2147187455|Una entidad de actividad no puede ser también un grupo de actividad|
> |**Nombre**:<br />ActivityInvalidObjectTypeCode<br />**Hex**:<br />80043513<br />**Número**:<br />-2147207917|El método de lanzamiento especificó un código de tipo no válido|
> |**Nombre**:<br />ActivityInvalidSessionToken<br />**Hex**:<br />80043512<br />**Número**:<br />-2147207918|Un token de sesión no válido se pasó al método de lanzamiento|
> |**Nombre**:<br />ActivityMetadataUpdate<br />**Hex**:<br />8004F126<br />**Número**:<br />-2147159770|Los metadatos especificados de la actividad no son válidos.|
> |**Nombre**:<br />ActivityMustHaveRelatedNotes<br />**Hex**:<br />8004F123<br />**Número**:<br />-2147159773|Una entidad personalizada que se define como una actividad debe tener una relación con notas de forma predeterminada.|
> |**Nombre**:<br />ActivityPartyObjectTypeNotAllowed<br />**Hex**:<br />80043506<br />**Número**:<br />-2147207930|No se puede crear un grupo de actividad del tipo de objeto especificado.|
> |**Nombre**:<br />AdminProfileCannotBeEditedOrDeleted<br />**Hex**:<br />8004F50C<br />**Número**:<br />-2147158772|El perfil de seguridad del campo Administrador del sistema no se puede modificar o eliminar.|
> |**Nombre**:<br />AdvancedSimilarityAzureSearchUnexpectedError<br />**Hex**:<br />80061696<br />**Número**:<br />-2147084650|Se ha producido un error inesperado al ejecutar la búsqueda. Vuelva a intentarlo más tarde.|
> |**Nombre**:<br />AggregateInnerQuery<br />**Hex**:<br />8004D2B1<br />**Número**:<br />-2147167567|La consulta interna no debe ser una consulta agregada.|
> |**Nombre**:<br />AggregateQueryRecordLimitExceeded<br />**Hex**:<br />8004E023<br />**Número**:<br />-2147164125|Se ha superado el límite máximo de registros. Reduzca el número de registros.|
> |**Nombre**:<br />AlreadyLinkedToAnotherAttribute<br />**Hex**:<br />8004F0FE<br />**Número**:<br />-2147159810|El atributo vinculado proporcionado ya está vinculado a otro atributo.|
> |**Nombre**:<br />AppConfigFeatureNotEnabled<br />**Hex**:<br />80072200<br />**Número**:<br />-2147016192|La característica de configuración de aplicaciones de personalización en la aplicación no está habilitada.|
> |**Nombre**:<br />AppEntityLimitExceeded<br />**Hex**:<br />80048547<br />**Número**:<br />-2147187385|{0}|
> |**Nombre**:<br />ApplicationMetadataConverterFailed<br />**Hex**:<br />8005F231<br />**Número**:<br />-2147093967|Lo sentimos, se ha producido un error. Vuelva a intentarlo o reinicie la aplicación.|
> |**Nombre**:<br />ApplicationMetadatadaCreateFailed<br />**Hex**:<br />8005F233<br />**Número**:<br />-2147093965|Lo sentimos, se ha producido un error. Vuelva a intentarlo o reinicie la aplicación.|
> |**Nombre**:<br />ApplicationMetadatadaNullData<br />**Hex**:<br />8005F232<br />**Número**:<br />-2147093966|Lo sentimos, se ha producido un error. Vuelva a intentarlo o reinicie la aplicación.|
> |**Nombre**:<br />ApplicationMetadatadaUpdateFailed<br />**Hex**:<br />8005F234<br />**Número**:<br />-2147093964|Lo sentimos, se ha producido un error. Vuelva a intentarlo o reinicie la aplicación.|
> |**Nombre**:<br />ApplicationMetadataFailedWithContinue<br />**Hex**:<br />8005F241<br />**Número**:<br />-2147093951|Se ha producido un problema con los cambios de configuración del servidor.  Puede seguir usando la aplicación, pero puede haber dificultades, incluida la incapacidad de guardar cambios. Póngase en contacto con el administrador de Dynamics 365 e indíquele la información que aparece al elegir ‘más información’.|
> |**Nombre**:<br />ApplicationMetadataGetPreviewMetadataUnknownError<br />**Hex**:<br />8005F230<br />**Número**:<br />-2147093968|Lo sentimos, se ha producido un error. Vuelva a intentarlo o reinicie la aplicación.|
> |**Nombre**:<br />ApplicationMetadataPrepareCustomizationsAppLock<br />**Hex**:<br />8005F237<br />**Número**:<br />-2147093961|Se han producido algunos problemas cuando intentamos preparar sus personalizaciones para los usuarios. Los usuarios en algunos clientes no podrán descargar las actualizaciones de personalización hasta que se solucione este problema.|
> |**Nombre**:<br />ApplicationMetadataPrepareCustomizationsRetrieverError<br />**Hex**:<br />8005F235<br />**Número**:<br />-2147093963|Se ha producido un problema con los cambios de configuración del servidor.  Los usuarios pueden seguir usando la aplicación, pero puede haber dificultades, incluida la incapacidad de guardar cambios.|
> |**Nombre**:<br />ApplicationMetadataPrepareCustomizationsTimeout<br />**Hex**:<br />8005F236<br />**Número**:<br />-2147093962|Lo sentimos pero los cambios de personalización del cliente no se han podido procesar.  Esto puede ser debido a un gran número de entidades habilitadas para los usuarios o el número de idiomas habilitados.  Los usuarios no recibirán personalizaciones hasta que se solucione este problema.|
> |**Nombre**:<br />ApplicationMetadataPrepareCustomizationsUnknownError<br />**Hex**:<br />8005F226<br />**Número**:<br />-2147093978|Lo sentimos, se ha producido un error. Vuelva a intentarlo o reinicie la aplicación.|
> |**Nombre**:<br />ApplicationMetadataRetrieveUnknownError<br />**Hex**:<br />8005F229<br />**Número**:<br />-2147093975|Lo sentimos, se ha producido un error. Vuelva a intentarlo o reinicie la aplicación.|
> |**Nombre**:<br />ApplicationMetadataRetrieveUserContextUnknownError<br />**Hex**:<br />8005F227<br />**Número**:<br />-2147093977|Lo sentimos, se ha producido un error. Vuelva a intentarlo o reinicie la aplicación.|
> |**Nombre**:<br />ApplicationMetadataSyncAppLock<br />**Hex**:<br />8005F244<br />**Número**:<br />-2147093948|Lo sentimos, su servidor está ocupado por lo que las configuraciones no se pueden descargar ahora. Los cambios deben estar disponibles en unos minutos.  Espere unos minutos y vuelva a iniciar sesión.|
> |**Nombre**:<br />ApplicationMetadataSyncAppLockWithContinue<br />**Hex**:<br />8005F245<br />**Número**:<br />-2147093947|Lo sentimos, su servidor está ocupado por lo que los cambios de configuración no se pueden descargar ahora. Los cambios deben estar disponibles en unos minutos.  Mientras tanto, puede seguir utilizando la aplicación y recibirá un aviso más adelante para que intente descargar los cambios. O bien, puede esperar unos minutos, reiniciar la aplicación y aceptar el mensaje para intentarlo de nuevo.|
> |**Nombre**:<br />ApplicationMetadataSyncFailed<br />**Hex**:<br />8005F240<br />**Número**:<br />-2147093952|Se ha producido un problema con los cambios de configuración del servidor.  No se puede cargar la aplicación, póngase en contacto con su administrador de Dynamics 365.|
> |**Nombre**:<br />ApplicationMetadataSyncTimeout<br />**Hex**:<br />8005F242<br />**Número**:<br />-2147093950|Lo sentimos pero los cambios de configuración del servidor no se han podido descargar.  Esto puede ser debido a una conexión lenta o a un gran número de entidades habilitadas para usarlo en dispositivos móviles.  Compruebe la conexión e inténtelo de nuevo.  Si continúa este problema, póngase en contacto con su administrador de Dynamics 365.|
> |**Nombre**:<br />ApplicationMetadataSyncTimeoutWithContinue<br />**Hex**:<br />8005F243<br />**Número**:<br />-2147093949|Lo sentimos pero los cambios de configuración del servidor no se han podido descargar.  Esto puede ser debido a una conexión lenta o a un gran número de entidades habilitadas para usarlo en dispositivos móviles.  Compruebe la conexión e inténtelo de nuevo. Puede continuar usando la aplicación con la configuración de una versión anterior, sin embargo, puede que tenga problemas con errores al guardar.  Si continúa este problema, póngase en contacto con su administrador de Dynamics 365.|
> |**Nombre**:<br />ApplicationMetadataSyncUnknownError<br />**Hex**:<br />8005F228<br />**Número**:<br />-2147093976|Lo sentimos, se ha producido un error. Vuelva a intentarlo o reinicie la aplicación.|
> |**Nombre**:<br />ApplicationMetadataUserValidationUnknownError<br />**Hex**:<br />8005F225<br />**Número**:<br />-2147093979|Lo sentimos, se ha producido un error. Vuelva a intentarlo o reinicie la aplicación.|
> |**Nombre**:<br />ApplicationNotRegisteredWithDeployment<br />**Hex**:<br />80041d49<br />**Número**:<br />-2147214007|La aplicación debe registrarse y habilitarse en el nivel de implementación antes de poder ser creada para esta organización|
> |**Nombre**:<br />ApplicationProfileMustContainEntity<br />**Hex**:<br />80071131<br />**Número**:<br />-2147020495|El perfil de aplicación debe contener al menos una entidad.|
> |**Nombre**:<br />ApplicationUserCannotBeUpdated<br />**Hex**:<br />80041d48<br />**Número**:<br />-2147214008|No se puede actualizar el usuario que representa a una aplicación OAuth|
> |**Nombre**:<br />AppLockTimeout<br />**Hex**:<br />8004Ed47<br />**Número**:<br />-2147160761|El tiempo de espera ha expirado antes de que se pudiera adquirir el bloque de aplicaciones.|
> |**Nombre**:<br />ApplyActiveSLAOnly<br />**Hex**:<br />80055001<br />**Número**:<br />-2147135487|Solo puede aplicar los contratos de nivel de servicio (SLA) activos a los casos.|
> |**Nombre**:<br />AppModuleComponentEntityMustHaveFormOrView<br />**Hex**:<br />80050115<br />**Número**:<br />-2147155691|La entidad "{0}" debe tener al menos un formulario o vista en la aplicación.|
> |**Nombre**:<br />AppModuleFeatureNotEnabled<br />**Hex**:<br />80050117<br />**Número**:<br />-2147155689|La característica no está activada para la organización.|
> |**Nombre**:<br />AppModuleMustHaveOnlyValidClientEntity<br />**Hex**:<br />8005012A<br />**Número**:<br />-2147155670|La entidad “{0}” no es válida para el cliente elegido y no se mostrará en tiempo de ejecución.|
> |**Nombre**:<br />AppModuleNotContainMOCAEnabledEntity<br />**Hex**:<br />80050118<br />**Número**:<br />-2147155688|La aplicación Module con MOCA como cliente compatible debe tener al menos una entidad habilitada para MOCA|
> |**Nombre**:<br />AppModuleNotReferEntity<br />**Hex**:<br />8005011D<br />**Número**:<br />-2147155683|La aplicación Module no hace referencia al menos a una entidad|
> |**Nombre**:<br />AppModulesImportError<br />**Hex**:<br />80050123<br />**Número**:<br />-2147155677|Se ha producido un error al importar módulos de aplicaciones|
> |**Nombre**:<br />AppModuleWithClientExists<br />**Hex**:<br />80050127<br />**Número**:<br />-2147155673|No se pudo crear la aplicación Hay ya una aplicación de este tipo de cliente.|
> |**Nombre**:<br />AppointmentDeleted<br />**Hex**:<br />8004E106<br />**Número**:<br />-2147163898|La instancia de la entidad de cita ya se ha borrado.|
> |**Nombre**:<br />AppointmentScheduleNotSet<br />**Hex**:<br />80040275<br />**Número**:<br />-2147220875|El inicio programado y el final programado deben establecerse para citas con el fin de sincronizarse con Outlook.|
> |**Nombre**:<br />ArgumentDirectionMismatch<br />**Hex**:<br />80060388<br />**Número**:<br />-2147089528|Error de coincidencia de direcciones para el argumento {0}.|
> |**Nombre**:<br />ArgumentTypeMismatch<br />**Hex**:<br />80060387<br />**Número**:<br />-2147089529|Error de coincidencia de tipos para el argumento {0}.|
> |**Nombre**:<br />ArrayMappingFoundForSingletonParameter<br />**Hex**:<br />8004037f<br />**Número**:<br />-2147220609|La asignación de parámetros de una transformación de matriz se define para un solo parámetro.|
> |**Nombre**:<br />ArticleIsPublished<br />**Hex**:<br />800404fe<br />**Número**:<br />-2147220226|El artículo no se puede actualizar ni borrar porque está en estado publicado|
> |**Nombre**:<br />AssociateProductFailureDifferentUom<br />**Hex**:<br />80061040<br />**Número**:<br />-2147086272|No se puede agregar el producto a la agrupación. Tiene que usar una unidad de producto que pertenezca a la unidad de venta del producto.|
> |**Nombre**:<br />AssociationRoleOrdinalInvalid<br />**Hex**:<br />80048468<br />**Número**:<br />-2147187608|El ordinal del rol de asociación no es válido; debe ser 1 o 2.|
> |**Nombre**:<br />AsyncAssignOperationOngoing<br />**Hex**:<br />80048555<br />**Número**:<br />-2147187371|Esta entidad se está asignando actualmente como parte de un trabajo de asignación en cascada asíncrono. Espere a que se complete el trabajo asincrónico antes de intentar asignar esta entidad nuevamente. (EntityId: {0}, EntityName: {1}, AsyncJobName: {2}, AsyncJobId: {3}, AsyncAssignOperationId: {4})|
> |**Nombre**:<br />AsyncCommunicationError<br />**Hex**:<br />80044307<br />**Número**:<br />-2147204345|Un error de comunicación se produjo al procesar la operación asincrónica.|
> |**Nombre**:<br />AsyncDeleteOperationOngoing<br />**Hex**:<br />80048549<br />**Número**:<br />-2147187383|Esta entidad se está eliminando actualmente como parte de un trabajo de eliminación en cascada asíncrono. Espere a que se complete el trabajo asincrónico antes de intentar eliminar esta entidad nuevamente. (EntityId: {0}, EntityName: {1}, AsyncJobName: {2}, AsyncJobId: {3}, AsyncDeleteOperationId: {4})|
> |**Nombre**:<br />AsyncNetworkError<br />**Hex**:<br />80044306<br />**Número**:<br />-2147204346|Se ha producido un error al acceder a la red.|
> |**Nombre**:<br />AsyncOperationCannotCancel<br />**Hex**:<br />80044F00<br />**Número**:<br />-2147201280|Este trabajo de sistema seleccionado no se pudo cancelar.|
> |**Nombre**:<br />AsyncOperationCannotDeleteUnlessCompleted<br />**Hex**:<br />8004416a<br />**Número**:<br />-2147204758|No se puede eliminar la operación asincrónica a menos que se encuentre en estado completado.|
> |**Nombre**:<br />AsyncOperationCannotPause<br />**Hex**:<br />80044F01<br />**Número**:<br />-2147201279|Este trabajo de sistema seleccionado no se pudo pausar.|
> |**Nombre**:<br />AsyncOperationCannotUpdateNonrecurring<br />**Hex**:<br />80044168<br />**Número**:<br />-2147204760|No se puede actualizar el patrón de periodicidad de un trabajo que no es recurrente.|
> |**Nombre**:<br />AsyncOperationCannotUpdateRecurring<br />**Hex**:<br />80044169<br />**Número**:<br />-2147204759|No se puede actualizar el patrón de periodicidad de un tipo que no está admitido.|
> |**Nombre**:<br />AsyncOperationInvalidStateChange<br />**Hex**:<br />80044162<br />**Número**:<br />-2147204766|No se puede establecer el estado de destino porque la transición de estado no es válida.|
> |**Nombre**:<br />AsyncOperationInvalidStateChangeToComplete<br />**Hex**:<br />80044165<br />**Número**:<br />-2147204763|No se puede completar el estado de destino porque la transición de estado no es válida.|
> |**Nombre**:<br />AsyncOperationInvalidStateChangeToReady<br />**Hex**:<br />80044166<br />**Número**:<br />-2147204762|No se puede establecer como listo el estado de destino porque la transición de estado no es válida.|
> |**Nombre**:<br />AsyncOperationInvalidStateChangeToSuspended<br />**Hex**:<br />80044167<br />**Número**:<br />-2147204761|No se puede establecer como suspendido el estado de destino porque la transición de estado no es válida.|
> |**Nombre**:<br />AsyncOperationInvalidStateChangeUnexpected<br />**Hex**:<br />80044163<br />**Número**:<br />-2147204765|No se puede establecer el estado de destino porque otro proceso ha cambiado el estado.|
> |**Nombre**:<br />AsyncOperationMissingId<br />**Hex**:<br />80044164<br />**Número**:<br />-2147204764|El AsyncOperationId es necesario para realizar la actualización.|
> |**Nombre**:<br />AsyncOperationPostponed<br />**Hex**:<br />80040328<br />**Número**:<br />-2147220696|Esta operación se ha pospuesto porque ha fallado más de {0} veces en {1} minutos|
> |**Nombre**:<br />AsyncOperationPostponedByExceptionCountThrottle<br />**Hex**:<br />80060917<br />**Número**:<br />-2147088105|Actualmente, no podemos completar esta acción. Se han pospuesto. Lo intentaremos de nuevo más tarde.|
> |**Nombre**:<br />AsyncOperationSuspendedOrLocked<br />**Hex**:<br />80040339<br />**Número**:<br />-2147220679|>Un trabajo de segundo plano asociado con esta importación se suspenderá o bloqueará. Para eliminar esta importación, en el Área de trabajo, haga clic en Importaciones, abra la importación, haga clic en Trabajos del sistema y reanude los trabajos suspendidos.|
> |**Nombre**:<br />AsyncOperationTypeIsNotRecognized<br />**Hex**:<br />80044303<br />**Número**:<br />-2147204349|No se reconoce el tipo de operación de la operación asincrónica.|
> |**Nombre**:<br />AsyncOperationTypeThrottled<br />**Hex**:<br />80060916<br />**Número**:<br />-2147088106|El trabajo no puede realizarse porque el servidor está ocupado. Reintentaremos el trabajo de nuevo pronto.|
> |**Nombre**:<br />AttachmentBlocked<br />**Hex**:<br />80043e09<br />**Número**:<br />-2147205623|El archivo adjunto no es de un tipo válido o es demasiado grande. No pueden cargarse o descargarse.|
> |**Nombre**:<br />AttachmentInvalidFileName<br />**Hex**:<br />80044a08<br />**Número**:<br />-2147202552|El nombre de archivo adjunto contiene caracteres no válidos.|
> |**Nombre**:<br />AttachmentNotFound<br />**Hex**:<br />80048493<br />**Número**:<br />-2147187565|No se encontró la referencia a los datos adjuntos.|
> |**Nombre**:<br />AttachmentNotRelatedToEmail<br />**Hex**:<br />80050006<br />**Número**:<br />-2147155962|Estos datos adjuntos no pertenecen a un correo.|
> |**Nombre**:<br />AttributeCannotBeUpdated<br />**Hex**:<br />80060413<br />**Número**:<br />-2147089389|El atributo - {0} no se puede actualizar para un flujo de proceso de negocio|
> |**Nombre**:<br />AttributeCannotBeUsedInAggregate<br />**Hex**:<br />80060559<br />**Número**:<br />-2147089063|El atributo {0} no se puede usar con una función de agregación en una fórmula.|
> |**Nombre**:<br />AttributeDeprecated<br />**Hex**:<br />80044335<br />**Número**:<br />-2147204299|"Atributo '{0}'en la entidad'{1}' es obsoleto."|
> |**Nombre**:<br />AttributeDoesNotSupportLocalizedLabels<br />**Hex**:<br />80044198<br />**Número**:<br />-2147204712|El atributo especificado no admite etiquetas localizadas.|
> |**Nombre**:<br />AttributeFormulaDefinitionIsEmpty<br />**Hex**:<br />80060439<br />**Número**:<br />-2147089351|La fórmula está vacía.|
> |**Nombre**:<br />AttributeIsNotCustomAttribute<br />**Hex**:<br />80047009<br />**Número**:<br />-2147192823|El atributo especificado no es un atributo personalizado|
> |**Nombre**:<br />AttributeIsNotFacetable<br />**Hex**:<br />80060305<br />**Número**:<br />-2147089659|No se pueden establecer facetas de búsqueda de usuario de la entidad {0} porque atributo {1} no es facetable. Quítelo de la lista para continuar.|
> |**Nombre**:<br />AttributeMapHasAnUnmanagedBaseInstance<br />**Hex**:<br />8004F223<br />**Número**:<br />-2147159517|Un AttributeMap, con Id: {0}, entre atributo {1} y {2} de entidad {3} y {4}, tiene una instancia base no administrada y, por lo tanto, no puede actualizarse con un solución administrada.|
> |**Nombre**:<br />AttributeMapIsManagedException<br />**Hex**:<br />8004F224<br />**Número**:<br />-2147159516|No se puede eliminar el mapa de atributos administrados con Id: {0} entre atributo {1} y {2} de entidad {3} y {4}.|
> |**Nombre**:<br />AttributeNameConflictWithNavigationPropertyName<br />**Hex**:<br />80048834<br />**Número**:<br />-2147186636|Nombre del Atributo {0} conflicto con el nombre de NavigationProerty en la entidad. Utilice un nombre único para el atributo.|
> |**Nombre**:<br />AttributeNotCreatedForOfficeGraphError<br />**Hex**:<br />80044237<br />**Número**:<br />-2147204553|Este atributo no se puede crear porque la ayuda para habilitar el atributo para Office Graph no está disponible.|
> |**Nombre**:<br />AttributeNotOfTypePicklist<br />**Hex**:<br />8004033c<br />**Número**:<br />-2147220676|Este atributo no está asignado a un atributo de lista desplegable, booleano o estado. Sin embargo, se ha incluido un elemento ListValueMap para ello.  Solucione esta incoherencia y vuelva a importar esta asignación de datos.|
> |**Nombre**:<br />AttributeNotOfTypeReference<br />**Hex**:<br />80040390<br />**Número**:<br />-2147220592|Este atributo no tiene asignado un atributo de referencia. Sin embargo, se ha incluido ReferenceMap para ello.  Solucione esta incoherencia y vuelva a importar esta asignación de datos.|
> |**Nombre**:<br />AttributeNotSecured<br />**Hex**:<br />8004F508<br />**Número**:<br />-2147158776|Uno o más campos no están habilitados para el nivel de seguridad del campo. La seguridad de nivel de campo no está habilitada hasta que publique las personalizaciones.|
> |**Nombre**:<br />AttributeNotUpdatedForOfficeGraphError<br />**Hex**:<br />80044238<br />**Número**:<br />-2147204552|Este atributo no se puede actualizar porque la compatibilidad para habilitar el atributo para Office Graph no está disponible.|
> |**Nombre**:<br />AttributePermissionIsInvalid<br />**Hex**:<br />8004F50E<br />**Número**:<br />-2147158770|El permiso '{0}' para el campo '{1}' con el identificador ={2} no es válido.|
> |**Nombre**:<br />AttributePermissionReadIsMissing<br />**Hex**:<br />8004F504<br />**Número**:<br />-2147158780|El usuario no tiene permisos de lectura para un campo protegido. No se ha podido completar la operación solicitada.|
> |**Nombre**:<br />AttributePermissionUpdateIsMissingDuringShare<br />**Hex**:<br />8004F503<br />**Número**:<br />-2147158781|El usuario no tiene permisos de actualización para un campo protegido. No se ha podido completar la operación solicitada.|
> |**Nombre**:<br />AttributePermissionUpdateIsMissingDuringUpdate<br />**Hex**:<br />8004F507<br />**Número**:<br />-2147158777|El usuario no tiene AttributePrivilegeUpdate y no se le ha concedido acceso compartido a un atributo protegido durante la operación de actualización|
> |**Nombre**:<br />AttributePrivilegeCreateIsMissing<br />**Hex**:<br />8004F502<br />**Número**:<br />-2147158782|El usuario no tiene permisos de creación para un campo protegido. No se ha podido completar la operación solicitada.|
> |**Nombre**:<br />AttributePrivilegeInvalidToUnsecure<br />**Hex**:<br />8004F50D<br />**Número**:<br />-2147158771|Debe tener suficientes permisos en un campo protegido para poder cambiar el nivel de seguridad del campo.|
> |**Nombre**:<br />AttributesExceeded<br />**Hex**:<br />80061501<br />**Número**:<br />-2147085055|Los atributos no pueden ser más de 4|
> |**Nombre**:<br />AttributeSharingCreateDuplicate<br />**Hex**:<br />8004F50B<br />**Número**:<br />-2147158773|El atributo fue compartido.|
> |**Nombre**:<br />AttributeSharingCreateShouldSetReadOrAndUpdateAccess<br />**Hex**:<br />8004F509<br />**Número**:<br />-2147158775|Debe definir el acceso de lectura y/o actualización al compartir un atributo protegido. ID Atributo: {0}|
> |**Nombre**:<br />AttributeSharingUpdateInvalid<br />**Hex**:<br />8004F50A<br />**Número**:<br />-2147158774|readAccess y updateAccess son falsos: invoque Delete en lugar de Update.|
> |**Nombre**:<br />AttributeTypeNotSupportedForCalculatedField<br />**Hex**:<br />80050221<br />**Número**:<br />-2147155423|El campo calculado/consolidado no se admite para el tipo de atributo MultiSelectPicklist.|
> |**Nombre**:<br />AttributeTypeNotSupportedForGroupByOrderByQuery<br />**Hex**:<br />80050224<br />**Número**:<br />-2147155420|No se admite la consulta GroupBy u OrderBy para el tipo de atributo MultiSelectPickList.|
> |**Nombre**:<br />AttributeUpdateNotAllowed<br />**Hex**:<br />80060463<br />**Número**:<br />-2147089309|Error al actualizar el flujo de proceso de negocio. La actualización del atributo "{0}" en flujo de trabajo "{1}" no está permitida.|
> |**Nombre**:<br />AuthenticateToServerBeforeRequestingProxy<br />**Hex**:<br />8004D228<br />**Número**:<br />-2147167704|Autenticar en serverType: {0} antes de solicitar un proxy.|
> |**Nombre**:<br />AutoDataCaptureAuthorizationFailureException<br />**Hex**:<br />80091042<br />**Número**:<br />-2146889662|No tiene la licencia de Office 365 adecuada para recibir correos electrónicos sin seguimiento. Póngase en contacto con el administrador del sistema.|
> |**Nombre**:<br />AutoDataCaptureDisabledError<br />**Hex**:<br />80091041<br />**Número**:<br />-2146889663|La función de captura automática no está habilitada.|
> |**Nombre**:<br />AutoDataCaptureResponseRetrievalFailureException<br />**Hex**:<br />80091043<br />**Número**:<br />-2146889661|Error al capturar correos electrónicos sin seguimiento de Exchange.|
> |**Nombre**:<br />AutoNumberAttributeSequenceMissing<br />**Hex**:<br />80060885<br />**Número**:<br />-2147088251|Falta la secuencia SQL para el atributo de número automático {0} de entidad {1}. Ahora intentará volver a crear la secuencia SQL.|
> |**Nombre**:<br />AzureApplicationIdNotFound<br />**Hex**:<br />8004F510<br />**Número**:<br />-2147158768|No encontramos el identificador de la aplicación {0} en su Azure Active Directory (Azure AD) con CorrelationID {1}. Asegúrese de que la aplicación está registrada en Azure AD.|
> |**Nombre**:<br />AzureApplicationIdNotFoundInOrgDB<br />**Hex**:<br />8004F512<br />**Número**:<br />-2147158766|Id. de aplicación de Azure no encontrado. No hemos podido encontrar el identificador de aplicación {0} en la base de datos CRM. Resuelva el identificador de la aplicación y vuelva a enviar la actualización.|
> |**Nombre**:<br />AzureOperationResponseTimedOut<br />**Hex**:<br />80061635<br />**Número**:<br />-2147084747|Una solicitud de operación de Azure no devolvió una respuesta en el período de tiempo de espera establecido. Intente de nuevo la operación o aumente el tiempo de espera proporcionado para la operación.|
> |**Nombre**:<br />AzureRecommendationModelBuildNotExist<br />**Hex**:<br />80061604<br />**Número**:<br />-2147084796|No existe la compilación del modelo de recomendaciones de Azure correspondiente a la versión del modelo utilizada.|
> |**Nombre**:<br />AzureRecommendationModelNotExist<br />**Hex**:<br />80061603<br />**Número**:<br />-2147084797|El modelo de recomendación de Azure no existe|
> |**Nombre**:<br />AzureServiceConnectionCascadeDeleteFailed<br />**Hex**:<br />80061636<br />**Número**:<br />-2147084746|Uno o varios modelos use la conexión. Elimine todos los modelos que usan esta conexión e intente eliminar la conexión de nuevo.|
> |**Nombre**:<br />AzureServiceConnectionInvalidUri<br />**Hex**:<br />80061630<br />**Número**:<br />-2147084752|Especifique una URL de servicio válida.|
> |**Nombre**:<br />AzureSqlDatabaseResourceLimitExceededError<br />**Hex**:<br />80072323<br />**Número**:<br />-2147015901|Se ha alcanzado el límite de recurso para la base de datos. Compruebe la excepción para obtener más detalles.|
> |**Nombre**:<br />AzureSqlDatabaseStorageQuotaExceededError<br />**Hex**:<br />80072325<br />**Número**:<br />-2147015899|Se ha alcanzado el límite de almacenamiento para la base de datos.|
> |**Nombre**:<br />AzureSqlMaxConcurrentWorkersLimitExceededError<br />**Hex**:<br />80072324<br />**Número**:<br />-2147015900|Demasiadas solicitudes simultáneas detectadas.|
> |**Nombre**:<br />AzureWebAppPluginsDisabled<br />**Hex**:<br />80050241<br />**Número**:<br />-2147155391|Complementos basados en Azure WebApp deshabilitados para la organización.|
> |**Nombre**:<br />BadAuthTicket<br />**Hex**:<br />8004A102<br />**Número**:<br />-2147180286|El vale especificado para la autenticación no es válido|
> |**Nombre**:<br />BadRequest<br />**Hex**:<br />8005F100<br />**Número**:<br />-2147094272|El servidor no ha entendido la solicitud.|
> |**Nombre**:<br />BaseAttributeNameNotPresentError<br />**Hex**:<br />80044240<br />**Número**:<br />-2147204544|El nombre BaseAttribute debería estar en condición XML.|
> |**Nombre**:<br />BaseCurrencyCannotBeDeactivated<br />**Hex**:<br />80048cf4<br />**Número**:<br />-2147185420|La divisa base no se puede desactivar.|
> |**Nombre**:<br />BaseCurrencyNotDeletable<br />**Hex**:<br />80048cff<br />**Número**:<br />-2147185409|La divisa base de una organización no se puede eliminar.|
> |**Nombre**:<br />BaseCurrencyOverflow<br />**Hex**:<br />80048cec<br />**Número**:<br />-2147185428|El tipo de cambio establecido para la divisa especificada en este registro ha generado un valor para {0} mayor que el máximo permitido para la divisa base ({1}).|
> |**Nombre**:<br />BaseCurrencyUnderflow<br />**Hex**:<br />80048ceb<br />**Número**:<br />-2147185429|El tipo de cambio establecido para la divisa especificada en este registro ha generado un valor para {0} menor que el mínimo permitido para la divisa base ({1}).|
> |**Nombre**:<br />BaseMatchingAttributeNotSameError<br />**Hex**:<br />80044245<br />**Número**:<br />-2147204539|Los atributos base y coincidente deben ser del mismo tipo.|
> |**Nombre**:<br />BaseUnitDoesNotExist<br />**Hex**:<br />80043b1c<br />**Número**:<br />-2147206372|La unidad base no existe.|
> |**Nombre**:<br />BaseUnitNotDeletable<br />**Hex**:<br />80043b03<br />**Número**:<br />-2147206397|La unidad base de una programación no se puede eliminar.|
> |**Nombre**:<br />BaseUnitNotNull<br />**Hex**:<br />80043b17<br />**Número**:<br />-2147206377|No utilice una unidad base como el valor de una unidad principal. Este valor siempre debe ser nulo.|
> |**Nombre**:<br />BaseUomNameNotSpecified<br />**Hex**:<br />80043810<br />**Número**:<br />-2147207152|No se ha especificado baseuomname|
> |**Nombre**:<br />BDK_E_ADDRESS_VALIDATION_FAILURE<br />**Hex**:<br />8004B540<br />**Número**:<br />-2147175104|{0}  |
> |**Nombre**:<br />BDK_E_AGREEMENT_ALREADY_SIGNED<br />**Hex**:<br />8004B541<br />**Número**:<br />-2147175103|{0}  |
> |**Nombre**:<br />BDK_E_AUTHORIZATION_FAILED<br />**Hex**:<br />8004B542<br />**Número**:<br />-2147175102|{0}  |
> |**Nombre**:<br />BDK_E_AVS_FAILED<br />**Hex**:<br />8004B543<br />**Número**:<br />-2147175101|{0}  |
> |**Nombre**:<br />BDK_E_BAD_CITYNAME_LENGTH<br />**Hex**:<br />8004B544<br />**Número**:<br />-2147175100|{0}  |
> |**Nombre**:<br />BDK_E_BAD_STATECODE_LENGTH<br />**Hex**:<br />8004B545<br />**Número**:<br />-2147175099|{0}  |
> |**Nombre**:<br />BDK_E_BAD_ZIPCODE_LENGTH<br />**Hex**:<br />8004B546<br />**Número**:<br />-2147175098|{0}  |
> |**Nombre**:<br />BDK_E_BADXML<br />**Hex**:<br />8004B547<br />**Número**:<br />-2147175097|{0}  |
> |**Nombre**:<br />BDK_E_BANNED_PAYMENT_INSTRUMENT<br />**Hex**:<br />8004B548<br />**Número**:<br />-2147175096|{0}  |
> |**Nombre**:<br />BDK_E_BANNEDPERSON<br />**Hex**:<br />8004B549<br />**Número**:<br />-2147175095|{0}  |
> |**Nombre**:<br />BDK_E_CANNOT_EXCEED_MAX_OWNERSHIP<br />**Hex**:<br />8004B54A<br />**Número**:<br />-2147175094|{0}  |
> |**Nombre**:<br />BDK_E_COUNTRY_CURRENCY_PI_MISMATCH<br />**Hex**:<br />8004B54B<br />**Número**:<br />-2147175093|{0}  |
> |**Nombre**:<br />BDK_E_CREDIT_CARD_EXPIRED<br />**Hex**:<br />8004B54C<br />**Número**:<br />-2147175092|{0}  |
> |**Nombre**:<br />BDK_E_DATE_EXPIRED<br />**Hex**:<br />8004B54D<br />**Número**:<br />-2147175091|{0}  |
> |**Nombre**:<br />BDK_E_ERROR_COUNTRYCODE_MISMATCH<br />**Hex**:<br />8004B54E<br />**Número**:<br />-2147175090|{0}  |
> |**Nombre**:<br />BDK_E_ERROR_COUNTRYCODE_REQUIRED<br />**Hex**:<br />8004B54F<br />**Número**:<br />-2147175089|{0}  |
> |**Nombre**:<br />BDK_E_EXTRA_REFERRAL_DATA<br />**Hex**:<br />8004B550<br />**Número**:<br />-2147175088|{0}  |
> |**Nombre**:<br />BDK_E_GUID_EXISTS<br />**Hex**:<br />8004B551<br />**Número**:<br />-2147175087|{0}  |
> |**Nombre**:<br />BDK_E_INVALID_ADDRESS_ID<br />**Hex**:<br />8004B552<br />**Número**:<br />-2147175086|{0}  |
> |**Nombre**:<br />BDK_E_INVALID_BILLABLE_ACCOUNT_ID<br />**Hex**:<br />8004B553<br />**Número**:<br />-2147175085|{0} La cuenta de facturación especificada no es válida.  O bien, aunque el objectID es del tipo correcto, la cuenta a la que identifica no existe en el sistema.|
> |**Nombre**:<br />BDK_E_INVALID_BUF_SIZE<br />**Hex**:<br />8004B554<br />**Número**:<br />-2147175084|{0}  |
> |**Nombre**:<br />BDK_E_INVALID_CATEGORY_NAME<br />**Hex**:<br />8004B555<br />**Número**:<br />-2147175083|{0}  |
> |**Nombre**:<br />BDK_E_INVALID_COUNTRY_CODE<br />**Hex**:<br />8004B556<br />**Número**:<br />-2147175082|{0}  |
> |**Nombre**:<br />BDK_E_INVALID_CURRENCY<br />**Hex**:<br />8004B557<br />**Número**:<br />-2147175081|{0}  |
> |**Nombre**:<br />BDK_E_INVALID_CUSTOMER_TYPE<br />**Hex**:<br />8004B558<br />**Número**:<br />-2147175080|{0}  |
> |**Nombre**:<br />BDK_E_INVALID_DATE<br />**Hex**:<br />8004B559<br />**Número**:<br />-2147175079|{0}  |
> |**Nombre**:<br />BDK_E_INVALID_EMAIL_ADDRESS<br />**Hex**:<br />8004B55A<br />**Número**:<br />-2147175078|{0}  |
> |**Nombre**:<br />BDK_E_INVALID_FILTER<br />**Hex**:<br />8004B55B<br />**Número**:<br />-2147175077|{0}  |
> |**Nombre**:<br />BDK_E_INVALID_GUID<br />**Hex**:<br />8004B55C<br />**Número**:<br />-2147175076|{0}  |
> |**Nombre**:<br />BDK_E_INVALID_INPUT_TO_TAXWARE_OR_VERAZIP<br />**Hex**:<br />8004B55D<br />**Número**:<br />-2147175075|{0}  |
> |**Nombre**:<br />BDK_E_INVALID_LOCALE<br />**Hex**:<br />8004B55E<br />**Número**:<br />-2147175074|{0}  |
> |**Nombre**:<br />BDK_E_INVALID_OBJECT_ID<br />**Hex**:<br />8004B55F<br />**Número**:<br />-2147175073|{0} El sistema de facturación no puede encontrar el objeto (por ejemplo, cuenta, suscripción u oferta).|
> |**Nombre**:<br />BDK_E_INVALID_OFFERING_GUID<br />**Hex**:<br />8004B560<br />**Número**:<br />-2147175072|{0}  |
> |**Nombre**:<br />BDK_E_INVALID_PAYMENT_INSTRUMENT_STATUS<br />**Hex**:<br />8004B561<br />**Número**:<br />-2147175071|{0}  |
> |**Nombre**:<br />BDK_E_INVALID_PAYMENT_METHOD_ID<br />**Hex**:<br />8004B562<br />**Número**:<br />-2147175070|{0}  |
> |**Nombre**:<br />BDK_E_INVALID_PHONE_TYPE<br />**Hex**:<br />8004B563<br />**Número**:<br />-2147175069|{0}  |
> |**Nombre**:<br />BDK_E_INVALID_POLICY_ID<br />**Hex**:<br />8004B564<br />**Número**:<br />-2147175068|{0}  |
> |**Nombre**:<br />BDK_E_INVALID_REFERRALDATA_XML<br />**Hex**:<br />8004B565<br />**Número**:<br />-2147175067|{0}  |
> |**Nombre**:<br />BDK_E_INVALID_STATE_FOR_COUNTRY<br />**Hex**:<br />8004B566<br />**Número**:<br />-2147175066|{0}  |
> |**Nombre**:<br />BDK_E_INVALID_SUBSCRIPTION_ID<br />**Hex**:<br />8004B567<br />**Número**:<br />-2147175065|{0} El id de suscripción especificado no es válido.  O bien, aunque el objectID es del tipo correcto y además apunta a una cuenta válida en SCS, no existe en SCS la suscripción a la que identifica.|
> |**Nombre**:<br />BDK_E_INVALID_TAX_EXEMPT_TYPE<br />**Hex**:<br />8004B568<br />**Número**:<br />-2147175064|{0}  |
> |**Nombre**:<br />BDK_E_MEG_CONFLICT<br />**Hex**:<br />8004B569<br />**Número**:<br />-2147175063|{0}  |
> |**Nombre**:<br />BDK_E_MULTIPLE_CITIES_FOUND<br />**Hex**:<br />8004B56A<br />**Número**:<br />-2147175062|{0}  |
> |**Nombre**:<br />BDK_E_MULTIPLE_COUNTIES_FOUND<br />**Hex**:<br />8004B56B<br />**Número**:<br />-2147175061|{0}  |
> |**Nombre**:<br />BDK_E_NON_ACTIVE_ACCOUNT<br />**Hex**:<br />8004B56C<br />**Número**:<br />-2147175060|{0}  |
> |**Nombre**:<br />BDK_E_NOPERMISSION<br />**Hex**:<br />8004B56D<br />**Número**:<br />-2147175059|{0} El asociado no tiene acceso a este método o cuando el solicitante no tiene permiso para hacer búsquedas en la búsqueda PUID proporcionada.|
> |**Nombre**:<br />BDK_E_OBJECT_ROLE_LIMIT_EXCEEDED<br />**Hex**:<br />8004B56E<br />**Número**:<br />-2147175058|{0}  |
> |**Nombre**:<br />BDK_E_OFFERING_ACCOUNT_CURRENCY_MISMATCH<br />**Hex**:<br />8004B56F<br />**Número**:<br />-2147175057|{0}  |
> |**Nombre**:<br />BDK_E_OFFERING_COUNTRY_ACCOUNT_MISMATCH<br />**Hex**:<br />8004B570<br />**Número**:<br />-2147175056|{0}  |
> |**Nombre**:<br />BDK_E_OFFERING_NOT_PURCHASEABLE<br />**Hex**:<br />8004B571<br />**Número**:<br />-2147175055|{0}  |
> |**Nombre**:<br />BDK_E_OFFERING_PAYMENT_INSTRUMENT_MISMATCH<br />**Hex**:<br />8004B572<br />**Número**:<br />-2147175054|{0}  |
> |**Nombre**:<br />BDK_E_OFFERING_REQUIRES_PI<br />**Hex**:<br />8004B573<br />**Número**:<br />-2147175053|{0}  |
> |**Nombre**:<br />BDK_E_PARTNERNOTINBILLING<br />**Hex**:<br />8004B574<br />**Número**:<br />-2147175052|{0}  |
> |**Nombre**:<br />BDK_E_PAYMENT_PROVIDER_CONNECTION_FAILED<br />**Hex**:<br />8004B575<br />**Número**:<br />-2147175051|{0}  |
> |**Nombre**:<br />BDK_E_POLICY_DEAL_COUNTRY_MISMATCH<br />**Hex**:<br />8004B577<br />**Número**:<br />-2147175049|{0}  |
> |**Nombre**:<br />BDK_E_PRIMARY_PHONE_REQUIRED<br />**Hex**:<br />8004B576<br />**Número**:<br />-2147175050|{0}  |
> |**Nombre**:<br />BDK_E_PUID_ROLE_LIMIT_EXCEEDED<br />**Hex**:<br />8004B578<br />**Número**:<br />-2147175048|{0}  |
> |**Nombre**:<br />BDK_E_RATING_FAILURE<br />**Hex**:<br />8004B579<br />**Número**:<br />-2147175047|{0}  |
> |**Nombre**:<br />BDK_E_REQUIRED_FIELD_MISSING<br />**Hex**:<br />8004B57A<br />**Número**:<br />-2147175046|{0}  |
> |**Nombre**:<br />BDK_E_STATE_CITY_INVALID<br />**Hex**:<br />8004B57B<br />**Número**:<br />-2147175045|{0}  |
> |**Nombre**:<br />BDK_E_STATE_INVALID<br />**Hex**:<br />8004B57C<br />**Número**:<br />-2147175044|{0}  |
> |**Nombre**:<br />BDK_E_STATE_ZIP_CITY_INVALID<br />**Hex**:<br />8004B57D<br />**Número**:<br />-2147175043|{0}  |
> |**Nombre**:<br />BDK_E_STATE_ZIP_CITY_INVALID2<br />**Hex**:<br />8004B57E<br />**Número**:<br />-2147175042|{0}  |
> |**Nombre**:<br />BDK_E_STATE_ZIP_CITY_INVALID3<br />**Hex**:<br />8004B57F<br />**Número**:<br />-2147175041|{0}  |
> |**Nombre**:<br />BDK_E_STATE_ZIP_CITY_INVALID4<br />**Hex**:<br />8004B580<br />**Número**:<br />-2147175040|{0}  |
> |**Nombre**:<br />BDK_E_STATE_ZIP_COVERS_MULTIPLE_CITIES<br />**Hex**:<br />8004B581<br />**Número**:<br />-2147175039|{0}  |
> |**Nombre**:<br />BDK_E_STATE_ZIP_INVALID<br />**Hex**:<br />8004B582<br />**Número**:<br />-2147175038|{0}  |
> |**Nombre**:<br />BDK_E_TAXID_EXPDATE<br />**Hex**:<br />8004B583<br />**Número**:<br />-2147175037|{0}  |
> |**Nombre**:<br />BDK_E_TOKEN_BLACKLISTED<br />**Hex**:<br />8004B584<br />**Número**:<br />-2147175036|{0}  |
> |**Nombre**:<br />BDK_E_TOKEN_EXPIRED<br />**Hex**:<br />8004B585<br />**Número**:<br />-2147175035|{0}  |
> |**Nombre**:<br />BDK_E_TOKEN_NOT_VALID_FOR_OFFERING<br />**Hex**:<br />8004B586<br />**Número**:<br />-2147175034|{0}  |
> |**Nombre**:<br />BDK_E_TOKEN_RANGE_BLACKLISTED<br />**Hex**:<br />8004B587<br />**Número**:<br />-2147175033|{0}  |
> |**Nombre**:<br />BDK_E_TRANS_BALANCE_TO_PI_INVALID<br />**Hex**:<br />8004B588<br />**Número**:<br />-2147175032|{0}  |
> |**Nombre**:<br />BDK_E_UNKNOWN_SERVER_FAILURE<br />**Hex**:<br />8004B589<br />**Número**:<br />-2147175031|{0} Error de servidor desconocido.|
> |**Nombre**:<br />BDK_E_UNSUPPORTED_CHAR_EXIST<br />**Hex**:<br />8004B58A<br />**Número**:<br />-2147175030|{0}  |
> |**Nombre**:<br />BDK_E_USAGE_COUNT_FOR_TOKEN_EXCEEDED<br />**Hex**:<br />8004B58F<br />**Número**:<br />-2147175025|{0} Token de facturación ya está utilizado.|
> |**Nombre**:<br />BDK_E_VATID_DOESNOTHAVEEXPDATE<br />**Hex**:<br />8004B58B<br />**Número**:<br />-2147175029|{0}  |
> |**Nombre**:<br />BDK_E_ZIP_CITY_MISSING<br />**Hex**:<br />8004B58C<br />**Número**:<br />-2147175028|{0}  |
> |**Nombre**:<br />BDK_E_ZIP_INVALID<br />**Hex**:<br />8004B58D<br />**Número**:<br />-2147175027|{0} Error de código de facturación.|
> |**Nombre**:<br />BDK_E_ZIP_INVALID_FOR_ENTERED_STATE<br />**Hex**:<br />8004B58E<br />**Número**:<br />-2147175026|{0} Error de código de facturación.|
> |**Nombre**:<br />BidsAuthenticationError<br />**Hex**:<br />8005E003<br />**Número**:<br />-2147098621|Se ha producido un error durante la autenticación con el servidor {0}.|
> |**Nombre**:<br />BidsAuthenticationFailed<br />**Hex**:<br />8005E006<br />**Número**:<br />-2147098618|Error de autenticación al intentar conectarse al servidor {0}. El nombre de usuario o la contraseña no son correctos.|
> |**Nombre**:<br />BidsInvalidConnectionString<br />**Hex**:<br />8005E000<br />**Número**:<br />-2147098624|Cadena de conexión no válida Uso: ServerUrl[;OrganizationName][;HomeRealmUrl]|
> |**Nombre**:<br />BidsInvalidUrl<br />**Hex**:<br />8005E001<br />**Número**:<br />-2147098623|Entrada de la dirección url {0} no es válida.|
> |**Nombre**:<br />BidsNoOrganizationsFound<br />**Hex**:<br />8005E004<br />**Número**:<br />-2147098620|No se encontraron organizaciones para el usuario.|
> |**Nombre**:<br />BidsOrganizationNotFound<br />**Hex**:<br />8005E005<br />**Número**:<br />-2147098619|No se encontró la organización {0} para el usuario.|
> |**Nombre**:<br />BidsServerConnectionFailed<br />**Hex**:<br />8005E002<br />**Número**:<br />-2147098622|No se pudo establecer la conexión con servidor {0}.|
> |**Nombre**:<br />BillingNoSettingError<br />**Hex**:<br />8004B531<br />**Número**:<br />-2147175119|No se encontró configuración de la aplicación de facturación [{0}].|
> |**Nombre**:<br />BillingPartnerCertificate<br />**Hex**:<br />8004B530<br />**Número**:<br />-2147175120|No se puede determinar el certificado partner correcto para usar con facturación.  Emisor: {0} asunto: {1} distintivo coincide con: [{2}] el nombre coincide con: [{3}] todos los certificados válidos: [{4}].|
> |**Nombre**:<br />BillingRetrieveKeyError<br />**Hex**:<br />8004B538<br />**Número**:<br />-2147175112|No se puede recuperar la clave de sesión de facturación: "{0}"|
> |**Nombre**:<br />BillingTestConnectionError<br />**Hex**:<br />8004B532<br />**Número**:<br />-2147175118|Facturación no está disponible: llamada a IsServiceAvailable devuelve 'False'.|
> |**Nombre**:<br />BillingTestConnectionException<br />**Hex**:<br />8004B533<br />**Número**:<br />-2147175117|Excepción de facturación TestConnection.|
> |**Nombre**:<br />BillingUnknownErrorCode<br />**Hex**:<br />8004B536<br />**Número**:<br />-2147175114|Código de error de facturación [{0}] se produjo con excepciones {1}|
> |**Nombre**:<br />BillingUnknownException<br />**Hex**:<br />8004B537<br />**Número**:<br />-2147175113|Código de error de facturación se produjo con excepciones {0}|
> |**Nombre**:<br />BillingUnmappedErrorCode<br />**Hex**:<br />8004B535<br />**Número**:<br />-2147175115|Código de error de facturación [{0}] se produjo con excepciones {1}|
> |**Nombre**:<br />BillingUserPuidNullError<br />**Hex**:<br />8004B534<br />**Número**:<br />-2147175116|El Puid de usuario es necesario, pero es nulo.|
> |**Nombre**:<br />BookFirstInstanceFailed<br />**Hex**:<br />8004E10E<br />**Número**:<br />-2147163890|Error al reservar la primera instancia.|
> |**Nombre**:<br />BooleanOptionOutOfRange<br />**Hex**:<br />8004431C<br />**Número**:<br />-2147204324|Opciones de atributo booleano deben tener un valor de 0 o 1.|
> |**Nombre**:<br />BothConnectionSidesAreNeeded<br />**Hex**:<br />80048218<br />**Número**:<br />-2147188200|Debe proporcionar un nombre o seleccionar un rol para ambas partes de esta conexión.|
> |**Nombre**:<br />BPFEntityAlreadyExists<br />**Hex**:<br />80060384<br />**Número**:<br />-2147089532|Ya existe entidad de flujo de proceso de negocio con este nombre.|
> |**Nombre**:<br />BpfEntityServiceIsNull<br />**Hex**:<br />80060446<br />**Número**:<br />-2147089338|Error al crear o actualizar proceso de negocios: BpfEntityService no puede ser nulo.|
> |**Nombre**:<br />BpfFactoryIsNull<br />**Hex**:<br />80060447<br />**Número**:<br />-2147089337|Error al crear o actualizar proceso de negocios: BpfFactory no puede ser nulo.|
> |**Nombre**:<br />BpfInstanceAlreadyExists<br />**Hex**:<br />80060397<br />**Número**:<br />-2147089513|Ya existe un flujo de proceso de negocio para el registro de destino y no se puede crear. Póngase en contacto con el administrador del sistema.|
> |**Nombre**:<br />BpfVisitorIsNull<br />**Hex**:<br />80060448<br />**Número**:<br />-2147089336|Error al crear o actualizar proceso de negocios: BpfVisitor no puede ser nulo.|
> |**Nombre**:<br />BulkDeleteChildFailure<br />**Hex**:<br />80048459<br />**Número**:<br />-2147187623|Uno de las eliminaciones masivas de trabajos secundarios da error|
> |**Nombre**:<br />BulkDeleteRecordDeletionFailure<br />**Hex**:<br />80048435<br />**Número**:<br />-2147187659|El registro no se puede eliminar.|
> |**Nombre**:<br />BulkDetectInvalidEmailRecipient<br />**Hex**:<br />80048422<br />**Número**:<br />-2147187678|El destinatario de correo electrónico no existe o su dirección de correo electrónico no es válida.|
> |**Nombre**:<br />BulkMailOperationFailed<br />**Hex**:<br />8004502D<br />**Número**:<br />-2147200979|Trabajo de correo electrónico masivo completado con {0} errores. Los errores pueden estar provocados por la falta de direcciones de correo electrónico o porque no tiene permiso para enviar correo electrónico. Para buscar registros con direcciones de correo electrónico faltantes, utilice la búsqueda avanzada. Si necesita aumentar permisos de correo electrónico, póngase en contacto con el administrador del sistema.|
> |**Nombre**:<br />BulkMailServiceNotAccessible<br />**Hex**:<br />80048304<br />**Número**:<br />-2147187964|El Servicio de correo en masa de Microsoft Dynamics 365 no se está ejecutando.|
> |**Nombre**:<br />BundleCannotContainBundle<br />**Hex**:<br />8004F972<br />**Número**:<br />-2147157646|No puede agregar una agrupación a otra.|
> |**Nombre**:<br />BundleCannotContainProductFamily<br />**Hex**:<br />8004F992<br />**Número**:<br />-2147157614|No puede agregar una familia de productos a una agrupación.|
> |**Nombre**:<br />BundleCannotContainProductKit<br />**Hex**:<br />80061014<br />**Número**:<br />-2147086316|No se puede agregar un kit a una agrupación.|
> |**Nombre**:<br />BundleMaxPropertyLimitExceeded<br />**Hex**:<br />8008100E<br />**Número**:<br />-2146955250|Este paquete no se puede publicar porque tiene demasiadas propiedades. Una agrupación en su organización no puede tener más de {0} propiedades.|
> |**Nombre**:<br />BusinessManagementInvalidUserId<br />**Hex**:<br />80041d1f<br />**Número**:<br />-2147214049|El identificador de usuario [{0}] no es válido.|
> |**Nombre**:<br />BusinessManagementLoopBeingCreated<br />**Hex**:<br />80041d21<br />**Número**:<br />-2147214047|La creación de esta asociación jerárquica crearía un bucle en la jerarquía de negocios.|
> |**Nombre**:<br />BusinessManagementLoopExists<br />**Hex**:<br />80041d20<br />**Número**:<br />-2147214048|Existe un bucle en la jerarquía de la empresa.|
> |**Nombre**:<br />BusinessManagementObjectAlreadyExists<br />**Hex**:<br />8004022a<br />**Número**:<br />-2147220950|Ya existe un objeto con el nombre especificado.|
> |**Nombre**:<br />BusinessNotEnabled<br />**Hex**:<br />8004032c<br />**Número**:<br />-2147220692|La unidad de negocio especificada está deshabilitada.|
> |**Nombre**:<br />BusinessProcessFlowDefinitionOutdated<br />**Hex**:<br />80060375<br />**Número**:<br />-2147089547|Esta acción no puede realizarse porque la definición de flujo de proceso de negocio se encuentra fuera de sincronización con la acción de proceso. Póngase en contacto con el administrador del sistema de Dynamics 365 para actualizar el flujo de proceso de negocio.|
> |**Nombre**:<br />BusinessProcessFlowMissingEntityErrorMessage<br />**Hex**:<br />80060440<br />**Número**:<br />-2147089344|No se pudo importar el proceso de negocio '{0}' porque la solución no incluye la entidad de proceso de negocio correspondiente '{1}'.|
> |**Nombre**:<br />BusinessProcessFlowStepHasInvalidParent<br />**Hex**:<br />80060405<br />**Número**:<br />-2147089403|{0} el primario no es de tipo {1}|
> |**Nombre**:<br />BusinessRuleEditorSupportsOnlyIfConditionBranch<br />**Hex**:<br />80060008<br />**Número**:<br />-2147090424|El editor de reglas de negocio solo admite una condición si. Solucione la regla.|
> |**Nombre**:<br />BusinessUnitCannotBeDisabled<br />**Hex**:<br />80041d59<br />**Número**:<br />-2147213991|La unidad de negocio no se puede deshabilitar: no existe usuario activo con el rol de administrador de sistema fuera del subárbol de la unidad de negocio.|
> |**Nombre**:<br />BusinessUnitDefaultTeamOwnsRecords<br />**Hex**:<br />80041d62<br />**Número**:<br />-2147213982|El equipo de unidad de negocio predeterminado es propietario de registros. No se puede eliminar la unidad de negocio (ID = {0}).|
> |**Nombre**:<br />BusinessUnitHasChildAndCannotBeDeleted<br />**Hex**:<br />80041d61<br />**Número**:<br />-2147213983|La unidad de negocio tiene una unidad de negocio secundaria y no se puede eliminar.|
> |**Nombre**:<br />BusinessUnitIsNotDisabledAndCannotBeDeleted<br />**Hex**:<br />80041d60<br />**Número**:<br />-2147213984|No se puede eliminar ninguna unidad de negocio deshabilitada.|
> |**Nombre**:<br />BusinessUnitQueuesAssociatedWithBU<br />**Hex**:<br />80072526<br />**Número**:<br />-2147015386|Hay {0} colas que hacen referencia a esta BusinessUnit con Id. ={1}, Nombre = {2}. Elimine debe las colas antes de eliminar esta unidad de negocio o asignarla a otra unidad de negocio.|
> |**Nombre**:<br />CalculatedFieldsAssignmentMismatch<br />**Hex**:<br />8006042b<br />**Número**:<br />-2147089365|No se puede definir el valor {0}, que es del tipo {1}, en el tipo {2}.|
> |**Nombre**:<br />CalculatedFieldsCyclicReference<br />**Hex**:<br />80060431<br />**Número**:<br />-2147089359|No se puede usar el campo {0} en el campo calculado {1} porque crearía una referencia circular.|
> |**Nombre**:<br />CalculatedFieldsDateOnlyBehaviorTypeMismatch<br />**Hex**:<br />8006043a<br />**Número**:<br />-2147089350|Solo puede usar un tipo de campo Solo fecha.|
> |**Nombre**:<br />CalculatedFieldsDepthExceeded<br />**Hex**:<br />80060432<br />**Número**:<br />-2147089358|No puede crear o actualizar el campo {0} porque el campo {1} ya tiene una cadena de campos calculados de {2} niveles.|
> |**Nombre**:<br />CalculatedFieldsDivideByZero<br />**Hex**:<br />8006042d<br />**Número**:<br />-2147089363|No se puede dividir por {0}, que da como resultado cero.|
> |**Nombre**:<br />CalculatedFieldsEntitiesExceeded<br />**Hex**:<br />80060433<br />**Número**:<br />-2147089357|No se puede crear o actualizar el campo {0} porque el campo {1} contiene una fórmula adicional que usa un registro primario.|
> |**Nombre**:<br />CalculatedFieldsFeatureNotEnabled<br />**Hex**:<br />80060422<br />**Número**:<br />-2147089374|La característica Campo calculado no está disponible|
> |**Nombre**:<br />CalculatedFieldsFunctionMismatch<br />**Hex**:<br />8006042c<br />**Número**:<br />-2147089364|No se puede utilizar {0}, que es del tipo {1}, con la función actual.|
> |**Nombre**:<br />CalculatedFieldsInvalidAttribute<br />**Hex**:<br />80060428<br />**Número**:<br />-2147089368|El campo {0} no existe.|
> |**Nombre**:<br />CalculatedFieldsInvalidAttributes<br />**Hex**:<br />8006042e<br />**Número**:<br />-2147089362|La fórmula hace referencia a los siguientes atributos inexistentes: {0}.|
> |**Nombre**:<br />CalculatedFieldsInvalidEntity<br />**Hex**:<br />80060423<br />**Número**:<br />-2147089373|La fórmula contiene una referencia no válida: {0}.|
> |**Nombre**:<br />CalculatedFieldsInvalidFunction<br />**Hex**:<br />80060427<br />**Número**:<br />-2147089369|La función {0} no existe.|
> |**Nombre**:<br />CalculatedFieldsInvalidSourceTypeMask<br />**Hex**:<br />80060438<br />**Número**:<br />-2147089352|No se puede guardar la fórmula porque contiene referencias a los siguientes campos que tienen definiciones no válidas: {0}.|
> |**Nombre**:<br />CalculatedFieldsInvalidValue<br />**Hex**:<br />8006042f<br />**Número**:<br />-2147089361|La fórmula hace referencia a un valor inexistente.|
> |**Nombre**:<br />CalculatedFieldsInvalidValues<br />**Hex**:<br />80060430<br />**Número**:<br />-2147089360|La fórmula hace referencia a los siguientes valores inexistentes: {0}.|
> |**Nombre**:<br />CalculatedFieldsInvalidXaml<br />**Hex**:<br />80060424<br />**Número**:<br />-2147089372|El campo {0} tiene una definición de fórmula XAML no válida.|
> |**Nombre**:<br />CalculatedFieldsNonCalculatedFieldAssignment<br />**Hex**:<br />80060425<br />**Número**:<br />-2147089371|Solo los campos calculados pueden tener una definición de fórmula.|
> |**Nombre**:<br />CalculatedFieldsPrimitiveOverflow<br />**Hex**:<br />8006042a<br />**Número**:<br />-2147089366|No se puede convertir el valor {0} al tipo {1}.|
> |**Nombre**:<br />CalculatedFieldsTimeInvBehaviorTypeMismatch<br />**Hex**:<br />8006043b<br />**Número**:<br />-2147089349|Solo puede usar un tipo de campo de fecha y hora independiente de la zona horaria.|
> |**Nombre**:<br />CalculatedFieldsTypeMismatch<br />**Hex**:<br />80060426<br />**Número**:<br />-2147089370|No puede utilizar {0}, que es del tipo {1}, con el operador actual.|
> |**Nombre**:<br />CalculatedFieldsUserLocBehaviorTypeMismatch<br />**Hex**:<br />8006043c<br />**Número**:<br />-2147089348|Solo puede usar un tipo de campo de fecha y hora Local del usuario.|
> |**Nombre**:<br />CalculatedFieldUsedInRollupFieldCannotBeComplex<br />**Hex**:<br />80060550<br />**Número**:<br />-2147089072|Uno o varios campos consolidados dependen de este campo calculado. El campo calculado no puede usar un campo consolidado; otro campo calculado está usando un campo consolidado o un campo de entidad relacionada.|
> |**Nombre**:<br />CalculateNowOverflowError<br />**Hex**:<br />80060558<br />**Número**:<br />-2147089064|No se pudo calcular debido a un error de desbordamiento.|
> |**Nombre**:<br />CallerCannotChangeOwnDomainName<br />**Hex**:<br />80044161<br />**Número**:<br />-2147204767|El autor de la llamada no puede cambiar su propio nombre de dominio|
> |**Nombre**:<br />CalloutException<br />**Hex**:<br />8004025b<br />**Número**:<br />-2147220901|Se produjo una excepción de llamada.|
> |**Nombre**:<br />CampaignActivityAlreadyPropagated<br />**Hex**:<br />80040326<br />**Número**:<br />-2147220698|Esta actividad de campaña ya se ha distribuido. Las actividades de campaña no se pueden distribuir más de una vez.|
> |**Nombre**:<br />CampaignActivityClosed<br />**Hex**:<br />80040331<br />**Número**:<br />-2147220687|Esta actividad de campaña está cerrada o cancelada. Las actividades de campaña no se pueden distribuir una vez cerradas o canceladas.|
> |**Nombre**:<br />CampaignNotSpecifiedForCampaignActivity<br />**Hex**:<br />80040309<br />**Número**:<br />-2147220727|RegardingObjectId es un campo obligatorio.|
> |**Nombre**:<br />CampaignNotSpecifiedForCampaignResponse<br />**Hex**:<br />8004030a<br />**Número**:<br />-2147220726|RegardingObjectId es un campo obligatorio.|
> |**Nombre**:<br />CanAssociateOnlyMobileOfflineEnabledEntityToProfileItem<br />**Hex**:<br />8006099E<br />**Número**:<br />-2147087970|{0} debe estar habilitada para Mobile Offline.|
> |**Nombre**:<br />CanAssociateOnlyMobileOfflineEnableEntityToProfileItem<br />**Hex**:<br />8006099C<br />**Número**:<br />-2147087972|Esta entidad debe estar habilitada para Mobile Offline.|
> |**Nombre**:<br />CanAssociateOnlyOneEntityPerProfileItem<br />**Hex**:<br />8006099D<br />**Número**:<br />-2147087971|Puede agregar un solo registro de elemento de perfil de Mobile Offline por entidad a un registro de perfil de Mobile Offline. |
> |**Nombre**:<br />CancelActiveChildCaseFirst<br />**Hex**:<br />8003F451<br />**Número**:<br />-2147224495|Cancele el caso secundario activo antes de cancelar el caso principal.|
> |**Nombre**:<br />CannotAcceptEmail<br />**Hex**:<br />8005E20B<br />**Número**:<br />-2147098101|Microsoft Dynamics 365 no puede aceptar el correo electrónico que intenta entregar. Código de motivo: {0}.|
> |**Nombre**:<br />CannotAccessExchangeOptinStatus<br />**Hex**:<br />80071110<br />**Número**:<br />-2147020528|El estado de Exchange optin no está accesible.|
> |**Nombre**:<br />CannotActivateDeactivateOnAnyEntityRoutingRuleFCBOff<br />**Hex**:<br />8004F849<br />**Número**:<br />-2147157943|No se puede activar o desactivar el registro de conjunto de reglas de enrutamiento para las entidades (excepto la entidad de caso), ya que el bit de control de la característica para el enrutamiento de registros de entidad está deshabilitado.|
> |**Nombre**:<br />CannotActivateMailboxForDisabledUserOrQueue<br />**Hex**:<br />8005E230<br />**Número**:<br />-2147098064|No se puede activar buzón porque el usuario o la cola asociados con el buzón están en estado deshabilitado. Solo se puede activar el buzón para usuario o cola activos.|
> |**Nombre**:<br />CannotActivateRecord<br />**Hex**:<br />80081017<br />**Número**:<br />-2146955241|No puede activar una agrupación o familia de producto retirada. Además, no se puede activar un producto retirado que forma parte de una familia de productos.|
> |**Nombre**:<br />CannotActOnBehalfOfAnotherUser<br />**Hex**:<br />8004A110<br />**Número**:<br />-2147180272|El usuario no tiene el privilegio para que actuar en nombre de otro usuario.|
> |**Nombre**:<br />CannotActOnBehalfOfExternalParty<br />**Hex**:<br />80061116<br />**Número**:<br />-2147086058|El usuario no tiene el privilegio para que actuar en nombre de una parte externa.|
> |**Nombre**:<br />CannotAddActivityPartyEntityToMobileOfflineProfileItem<br />**Hex**:<br />800609AD<br />**Número**:<br />-2147087955|No se puede agregar la entidad ActivityParty al elemento del perfil de Mobile Offline debido a que se agrega automáticamente cuando se agrega una entidad de actividad al perfil.|
> |**Nombre**:<br />CannotAddBundleToItself<br />**Hex**:<br />80061031<br />**Número**:<br />-2147086287|No se puede agregar una agrupación a sí misma.|
> |**Nombre**:<br />CannotAddBundleToPricelist<br />**Hex**:<br />80061007<br />**Número**:<br />-2147086329|No se puede agregar la agrupación {0} a la lista de precios porque el producto de agrupación {1} no está en la lista de precios.|
> |**Nombre**:<br />CannotAddBusinessDataLocalizedLabelEntityToMobileOfflineProfileItem<br />**Hex**:<br />800609AC<br />**Número**:<br />-2147087956|No se puede agregar la entidad BusinessDataLocalizedLabel al elemento del perfil de Mobile Offline debido a que se agrega automáticamente cuando se agrega la entidad del producto al perfil.|
> |**Nombre**:<br />CannotAddDraftFamilyProductBundleToCases<br />**Hex**:<br />8004F984<br />**Número**:<br />-2147157628|No puede agregar una familia de productos, un borrador de producto o un borrador de agrupación.|
> |**Nombre**:<br />CannotAddIntersectEntityToMobileOfflineProfileItem<br />**Hex**:<br />800609AB<br />**Número**:<br />-2147087957|No se puede agregar la entidad de intersección al elemento del perfil de Mobile Offline debido a que se agrega automáticamente cuando se agregan sus entidades principales al perfil.|
> |**Nombre**:<br />CannotAddKitToItself<br />**Hex**:<br />80061032<br />**Número**:<br />-2147086286|No se puede agregar un kit a sí mismo.|
> |**Nombre**:<br />CannotAddMembersToDefaultTeam<br />**Hex**:<br />8004830B<br />**Número**:<br />-2147187957|No se pueden agregar miembros al equipo de unidad de negocio predeterminado.|
> |**Nombre**:<br />CannotAddNewBooleanValue<br />**Hex**:<br />8004431D<br />**Número**:<br />-2147204323|No puede agregar una opción a un atributo booleano.|
> |**Nombre**:<br />CannotAddNewStateValue<br />**Hex**:<br />8004431E<br />**Número**:<br />-2147204322|No puede agregar opciones de estado al atributo de estado.|
> |**Nombre**:<br />CannotAddNonCustomizableComponent<br />**Hex**:<br />8004F015<br />**Número**:<br />-2147160043|El componente {0} {1} no se puede agregar a la solución porque no se puede personalizar|
> |**Nombre**:<br />CannotAddOrActonBehalfAnotherUserPrivilege<br />**Hex**:<br />8004Ed43<br />**Número**:<br />-2147160765|Actuar en nombre de los privilegios de otro usuario no se puede agregar o quitar.|
> |**Nombre**:<br />CannotAddParentToAKit<br />**Hex**:<br />80061015<br />**Número**:<br />-2147086315|No se puede especificar un registro primario para un kit.|
> |**Nombre**:<br />CannotAddPricelistToProductFamily<br />**Hex**:<br />8004F902<br />**Número**:<br />-2147157758|No puede agregar una familia de productos a una lista de precios.|
> |**Nombre**:<br />CannotAddProduct<br />**Hex**:<br />8004F908<br />**Número**:<br />-2147157752|Solo se pueden agregar productos activos.|
> |**Nombre**:<br />CannotAddProductBundleToKit<br />**Hex**:<br />80061022<br />**Número**:<br />-2147086302|No se puede agregar una agrupación a un kit.|
> |**Nombre**:<br />CannotAddProductFamilyToKit<br />**Hex**:<br />80061023<br />**Número**:<br />-2147086301|No se puede agregar una familia de productos a un kit.|
> |**Nombre**:<br />CannotAddProductToBundle<br />**Hex**:<br />8004F976<br />**Número**:<br />-2147157642|No puede agregar productos a esta agrupación. Se ha alcanzado el límite de {0} para esta agrupación.|
> |**Nombre**:<br />CannotAddProductToKit<br />**Hex**:<br />80061024<br />**Número**:<br />-2147086300|No se puede agregar un producto que pertenece a una familia de productos a un kit.|
> |**Nombre**:<br />CannotAddProductToRetiredKit<br />**Hex**:<br />80061026<br />**Número**:<br />-2147086298|No se puede agregar un producto a un kit retirado.|
> |**Nombre**:<br />CannotAddQueueItemsToInactiveQueue<br />**Hex**:<br />80040522<br />**Número**:<br />-2147220190|El usuario seleccionado no tiene los permisos suficientes para trabajar en los elementos de esta cola.|
> |**Nombre**:<br />CannotAddRetiredProduct<br />**Hex**:<br />80061033<br />**Número**:<br />-2147086285|No puede crear una relación de producto con un producto retirado.|
> |**Nombre**:<br />CannotAddRetiredProductToKit<br />**Hex**:<br />80061027<br />**Número**:<br />-2147086297|No se puede agregar un producto retirado a un kit.|
> |**Nombre**:<br />CannotAddRetiredProductToPricelist<br />**Hex**:<br />80061009<br />**Número**:<br />-2147086327|Los productos retirados no se pueden agregar a listas de precios.|
> |**Nombre**:<br />CannotAddSingleQueueEnabledEntityToQueue<br />**Hex**:<br />8004051c<br />**Número**:<br />-2147220196|El registro de entidad no se puede agregar a la cola ya que existe en otra cola.|
> |**Nombre**:<br />CannotAddSolutionComponentWithoutRoots<br />**Hex**:<br />8004F018<br />**Número**:<br />-2147160040|Este artículo no es un componente de solución válido. Para obtener más información sobre cómo organizar los componentes de la solución, consulte la documentación del SDK de Microsoft Dynamics 365.|
> |**Nombre**:<br />CannotAddUserToMobileOfflineProfile<br />**Hex**:<br />800609A6<br />**Número**:<br />-2147087962|No se puede agregar este usuario a este perfil de Mobile Offline debido a que el rol del usuario no se encuentra o no dispone del privilegio Dynamics 365 para móviles.|
> |**Nombre**:<br />CannotAddWorkflowActivationToSolution<br />**Hex**:<br />8004F00C<br />**Número**:<br />-2147160052|No se puede agregar la activación de flujo de trabajo a la solución.|
> |**Nombre**:<br />CannotAssignAddressBookFilters<br />**Hex**:<br />80048448<br />**Número**:<br />-2147187640|No se pueden asignar filtros de libreta de direcciones|
> |**Nombre**:<br />CannotAssignOfflineFilters<br />**Hex**:<br />800404ff<br />**Número**:<br />-2147220225|No se pueden asignar filtros sin conexión|
> |**Nombre**:<br />CannotAssignOutlookFilters<br />**Hex**:<br />80040264<br />**Número**:<br />-2147220892|No se pueden asignar filtros de outlook|
> |**Nombre**:<br />CannotAssignRolesOrProfilesToAccessTeam<br />**Hex**:<br />80048331<br />**Número**:<br />-2147187919|No se puede asignar roles o perfiles a un equipo de acceso (ID = {0}).|
> |**Nombre**:<br />CannotAssignRolesToSupportUser<br />**Hex**:<br />80041d51<br />**Número**:<br />-2147213999|Dado que el usuario de soporte es de solo lectura, no se le pueden asignar otros roles.|
> |**Nombre**:<br />CannotAssignSupportUser<br />**Hex**:<br />80041d44<br />**Número**:<br />-2147214012|El rol de usuario de soporte no se puede asignar al usuario.|
> |**Nombre**:<br />CannotAssignToAccessTeam<br />**Hex**:<br />80048340<br />**Número**:<br />-2147187904|No puede asignar un registro al equipo de acceso. Puede asignar un registro al equipo de propietario.|
> |**Nombre**:<br />CannotAssignToDisabledBusiness<br />**Hex**:<br />8004032d<br />**Número**:<br />-2147220691|La unidad de negocio especificada no se puede asignar porque está deshabilitada.|
> |**Nombre**:<br />CannotAssociateExternalPartyItem<br />**Hex**:<br />80061117<br />**Número**:<br />-2147086057|No puede asociar más de un elemento de la parte externa a un registro de entidad habilitado como parte externa.|
> |**Nombre**:<br />CannotAssociateInactiveItemToCampaign<br />**Hex**:<br />80040304<br />**Número**:<br />-2147220732|No se puede asociar un elemento inactivo a una campaña.|
> |**Nombre**:<br />CannotAssociateInvalidEntityToProfileItem<br />**Hex**:<br />8006099B<br />**Número**:<br />-2147087973|Código de tipo de objeto no válido.|
> |**Nombre**:<br />CannotAssociateProductFamily<br />**Hex**:<br />8004F999<br />**Número**:<br />-2147157607|No puede crear una relación con una familia de productos.|
> |**Nombre**:<br />CannotAssociateRetiredBundles<br />**Hex**:<br />80081011<br />**Número**:<br />-2146955247|No puede crear una relación de producto con una agrupación retirada.|
> |**Nombre**:<br />CannotAssociateRetiredProducts<br />**Hex**:<br />8004F974<br />**Número**:<br />-2147157644|No puede crear una relación de producto con un producto retirado.|
> |**Nombre**:<br />CannotBindToSession<br />**Hex**:<br />80040254<br />**Número**:<br />-2147220908|No se puede enlazar a otra sesión, sesión ya enlazada.|
> |**Nombre**:<br />CannotCancelInvoice<br />**Hex**:<br />80100001<br />**Número**:<br />-2146435071|La factura no se puede cancelar porque no se encuentra en estado activa o pagada.|
> |**Nombre**:<br />CannotChangeAccessModeForInternetMarketingUser<br />**Hex**:<br />80045035<br />**Número**:<br />-2147200971|El usuario de Marketing de Internet es un usuario del sistema. No puede cambiar su modo de acceso.|
> |**Nombre**:<br />CannotChangeAttributeRequiredLevel<br />**Hex**:<br />8004D293<br />**Número**:<br />-2147167597|El nivel requerido de un atributo no se puede cambiar de SystemRequired|
> |**Nombre**:<br />CannotChangeConnectorDisplayName<br />**Hex**:<br />80072607<br />**Número**:<br />-2147015161|El atributo del conector nombre para mostrar no se puede cambiar.|
> |**Nombre**:<br />CannotChangeConvertRuleState<br />**Hex**:<br />800608F4<br />**Número**:<br />-2147088140|Error al activar la regla de conversión. Por favor, verifique sus privilegios en el flujo de trabajo e inténtelo de nuevo o póngase en contacto con el administrador del sistema.|
> |**Nombre**:<br />CannotChangeDaysSinceRecordLastModified<br />**Hex**:<br />800609A4<br />**Número**:<br />-2147087964|Necesita habilitar esta entidad para Mobile Offline para poder establecer o cambiar el número de días que han transcurrido desde la última modificación del registro.|
> |**Nombre**:<br />CannotChangeInvitationStatusForInternetMarketingUser<br />**Hex**:<br />80045036<br />**Número**:<br />-2147200970|El usuario de Marketing de Internet es un usuario del sistema. No puede cambiar el estado de la invitación.|
> |**Nombre**:<br />CannotChangeProductRelationship<br />**Hex**:<br />80061013<br />**Número**:<br />-2147086317|No se puede agregar ni modificar la relación de producto de un producto retirado.|
> |**Nombre**:<br />CannotChangeSelectedBundleToAnotherValue<br />**Hex**:<br />8004F986<br />**Número**:<br />-2147157626|Si una agrupación está seleccionada como producto existente, no puede cambiarla a otro valor.|
> |**Nombre**:<br />CannotChangeSelectedProductWithBundle<br />**Hex**:<br />8004F987<br />**Número**:<br />-2147157625|Si un producto está seleccionado como producto existente, no puede cambiarlo a una agrupación.|
> |**Nombre**:<br />CannotChangeState<br />**Hex**:<br />8004F863<br />**Número**:<br />-2147157917|Error al activar SLA. Por favor, verifique sus privilegios en el flujo de trabajo e inténtelo de nuevo o póngase en contacto con el administrador del sistema.|
> |**Nombre**:<br />CannotChangeStateOfNonpublicView<br />**Hex**:<br />80040279<br />**Número**:<br />-2147220871|Solo se pueden desactivar y activar las vistas públicas.|
> |**Nombre**:<br />CannotChangeTeamTypeDueToOwnership<br />**Hex**:<br />80048337<br />**Número**:<br />-2147187913|No puede modificar el tipo del equipo porque hay registros propiedad del equipo.|
> |**Nombre**:<br />CannotChangeTeamTypeDueToRoleOrProfile<br />**Hex**:<br />80048336<br />**Número**:<br />-2147187914|No puede modificar el tipo del equipo porque hay roles de seguridad o perfiles de seguridad de campo asignados al equipo.|
> |**Nombre**:<br />CannotClearChannelPropertyGroupFromConvertRule<br />**Hex**:<br />800608ED<br />**Número**:<br />-2147088147|El grupo de propiedades de canal se está usando en uno o varios pasos. Elimine las propiedades de las condiciones y los pasos que usan el registro antes de guardar o activar la regla.|
> |**Nombre**:<br />CannotCloneBundleAsProductLimitExceeded<br />**Hex**:<br />8004F985<br />**Número**:<br />-2147157627|No puede crear esta nueva agrupación porque contiene más del número permitido de {0} productos que una agrupación puede contener.|
> |**Nombre**:<br />CannotCloneBundleWithRetiredProducts<br />**Hex**:<br />80061034<br />**Número**:<br />-2147086284|No puede clonar una agrupación que contenga productos retirados.|
> |**Nombre**:<br />CannotCloneProductKit<br />**Hex**:<br />80061020<br />**Número**:<br />-2147086304|No se puede clonar un kit.|
> |**Nombre**:<br />CannotCloseCase<br />**Hex**:<br />8004F456<br />**Número**:<br />-2147158954|No se puede completar esta operación. Uno o más casos secundarios no se pueden cerrar debido a las reglas de transición de estado definidas para los casos.|
> |**Nombre**:<br />CannotCompleteLockRequest<br />**Hex**:<br />8004026c<br />**Número**:<br />-2147220884|No se puede completar la solicitud debido al bloqueo de tiempo de espera {0}.|
> |**Nombre**:<br />CannotConnectToSelf<br />**Hex**:<br />80048217<br />**Número**:<br />-2147188201|No se puede conectar un registro en sí mismo.|
> |**Nombre**:<br />CannotConvertBundleToKit<br />**Hex**:<br />80061030<br />**Número**:<br />-2147086288|No se puede convertir una agrupación en un kit.|
> |**Nombre**:<br />CannotConvertProductAssociatedWithBundleToKit<br />**Hex**:<br />80061018<br />**Número**:<br />-2147086312|No se puede convertir un producto que forma parte de una agrupación en un kit.|
> |**Nombre**:<br />CannotConvertProductAssociatedWithFamilyToKit<br />**Hex**:<br />80061016<br />**Número**:<br />-2147086314|No se puede convertir un producto que pertenece a una familia de productos en un kit.|
> |**Nombre**:<br />CannotConvertProductFamilyToKit<br />**Hex**:<br />80061029<br />**Número**:<br />-2147086295|No se puede convertir una familia de productos en un kit.|
> |**Nombre**:<br />CannotCopyIncompatibleListType<br />**Hex**:<br />80040306<br />**Número**:<br />-2147220730|No se pueden copiar listas de tipos diferentes.|
> |**Nombre**:<br />CannotCopyStaticList<br />**Hex**:<br />8004F704<br />**Número**:<br />-2147158268|Esta acción solo es válida para la lista dinámica.|
> |**Nombre**:<br />CannotCreateActivityRelationship<br />**Hex**:<br />80047006<br />**Número**:<br />-2147192826|La relación con las actividades no se puede crear mediante esta operación|
> |**Nombre**:<br />CannotCreateAddressBookFilters<br />**Hex**:<br />80048447<br />**Número**:<br />-2147187641|No se pueden crear filtros de libreta de direcciones|
> |**Nombre**:<br />CannotCreateCase<br />**Hex**:<br />80060853<br />**Número**:<br />-2147088301|No puede crear este caso como derecho predeterminado, ya que el cliente especificado no tiene ningún término restante.|
> |**Nombre**:<br />CannotCreateComponentDefinition<br />**Hex**:<br />80072001<br />**Número**:<br />-2147016703|La creación de una nueva definición de componente no se admite|
> |**Nombre**:<br />CannotCreateExternalPartyWithSameCorrelationKey<br />**Hex**:<br />80061112<br />**Número**:<br />-2147086062|Ya existe un registro de entidad externa con el mismo valor de clave de correlación.|
> |**Nombre**:<br />CannotCreateFromSupportUser<br />**Hex**:<br />80041d46<br />**Número**:<br />-2147214010|No se puede crear un rol desde el rol de soporte técnico de usuario.|
> |**Nombre**:<br />CannotCreateKitOfTypeFamilyOrBundle<br />**Hex**:<br />80061012<br />**Número**:<br />-2147086318|No se puede crear un kit del tipo agrupación o familia de productos.|
> |**Nombre**:<br />CannotCreateOrEnablePositionDueToParentPositionIsDisabled<br />**Hex**:<br />80048344<br />**Número**:<br />-2147187900|No puede crear o habilitar una posición secundaria bajo una posición primaria deshabilitada.|
> |**Nombre**:<br />CannotCreateOutlookFilters<br />**Hex**:<br />80040263<br />**Número**:<br />-2147220893|No se pueden crear filtros de outlook|
> |**Nombre**:<br />CannotCreatePluginInstance<br />**Hex**:<br />8004A201<br />**Número**:<br />-2147180031|No se puede crear la instancia de un complemento. Compruebe que el tipo de complemento no se define como abstracto y que tiene un constructor admitido por Dynamics 365 SDK.|
> |**Nombre**:<br />CannotCreatePropertyOptionSetItem<br />**Hex**:<br />80081013<br />**Número**:<br />-2146955245|Solo puede crear un registro de elemento de conjunto de opciones de propiedad que haga referencia a una propiedad que tenga su tipo de datos establecido en Conjunto de opciones.|
> |**Nombre**:<br />CannotCreateQueueItemInactiveObject<br />**Hex**:<br />8004051e<br />**Número**:<br />-2147220194|No se puede agregar a la cola un objeto desactivado.|
> |**Nombre**:<br />CannotCreateResponseForTemplate<br />**Hex**:<br />80040312<br />**Número**:<br />-2147220718|No se puede crear CampaignResponse para la campaña de plantilla.|
> |**Nombre**:<br />CannotCreateRuleOnAnyEntityRoutingRuleFCBOff<br />**Hex**:<br />8004F848<br />**Número**:<br />-2147157944|No se puede crear el registro de conjunto de regla de enrutamiento para las entidades (excepto la entidad de caso), ya que el bit de control de la característica para el enrutamiento de registros de entidad está deshabilitado.|
> |**Nombre**:<br />CannotCreateSelfReferencingParentChild<br />**Hex**:<br />8007200C<br />**Número**:<br />-2147016692|La relación Primario-Elemento secundario {0} no puede hacer referencia a sí misma.|
> |**Nombre**:<br />CannotCreateSLAForEntity<br />**Hex**:<br />80055005<br />**Número**:<br />-2147135483|No puede crear un contrato de nivel de servicio (SLA) para esta entidad porque no se ha habilitado para crear SLA|
> |**Nombre**:<br />CannotCreateSyncUserIsLicensedField<br />**Hex**:<br />80041d4d<br />**Número**:<br />-2147214003|La propiedad que IsLicensed no se puede establecer para sincronizar la creación de usuarios.|
> |**Nombre**:<br />CannotCreateSyncUserObjectMissing<br />**Hex**:<br />80041d4b<br />**Número**:<br />-2147214005|Este no es un identificador de Microsoft Online Services válido para la organización.|
> |**Nombre**:<br />CannotCreateSystemOrDefaultTheme<br />**Hex**:<br />800608D5<br />**Número**:<br />-2147088171|No puede crear temas del sistema o predeterminados. No se pueden crear como predeterminados el sistema y el tema.|
> |**Nombre**:<br />CannotCreateUpdateSourceAttribute<br />**Hex**:<br />80044804<br />**Número**:<br />-2147203068|Atributo de origen no válido para crear o actualizar si el tipo de métrica es Contar.|
> |**Nombre**:<br />CannotDeactivateDefaultView<br />**Hex**:<br />8004027a<br />**Número**:<br />-2147220870|Las vistas predeterminadas no se pueden desactivar.|
> |**Nombre**:<br />CannotDeactivateGuestProfile<br />**Hex**:<br />80061105<br />**Número**:<br />-2147086075|No puede establecer este perfil de acceso al canal de invitado como inactivo.|
> |**Nombre**:<br />CannotDefineMultipleValuesOnOwnerFieldInProfileItemEntityFilter<br />**Hex**:<br />80071129<br />**Número**:<br />-2147020503|No pueden definir varios valores en este campo.|
> |**Nombre**:<br />CannotDeleteActiveCaseCreationRule<br />**Hex**:<br />8004F880<br />**Número**:<br />-2147157888|No puede eliminar una regla activa. Desactive la regla de creación de registros y actualización e intente eliminarla.|
> |**Nombre**:<br />CannotDeleteActiveRecordCreationRuleItem<br />**Hex**:<br />8004F894<br />**Número**:<br />-2147157868|No puede eliminar un elemento de reglas de creación de registro activo. Desactive la regla de creación de registros y, a continuación, intente eliminarla.|
> |**Nombre**:<br />CannotDeleteActiveRule<br />**Hex**:<br />8004F850<br />**Número**:<br />-2147157936|No se puede eliminar una regla de enrutamiento activa. Desactive la regla para eliminarla.|
> |**Nombre**:<br />CannotDeleteActiveSla<br />**Hex**:<br />8004F870<br />**Número**:<br />-2147157904|No puede eliminar un SKA activo. Desactive la SLA y, a continuación, intente eliminarla.|
> |**Nombre**:<br />CannotDeleteAppModuleAdministration<br />**Hex**:<br />80050130<br />**Número**:<br />-2147155664|Esta aplicación no se puede eliminar.|
> |**Nombre**:<br />CannotDeleteAppModuleClientType<br />**Hex**:<br />80050129<br />**Número**:<br />-2147155671|Esta aplicación no se puede eliminar.|
> |**Nombre**:<br />CannotDeleteAsBackgroundOperationInProgress<br />**Hex**:<br />8004032b<br />**Número**:<br />-2147220693|Microsoft Dynamics 365 está usando actualmente este registro y no se puede eliminar. Vuelva a intentarlo más tarde. Si el problema continúa, póngase en contacto con el administrador del sistema.|
> |**Nombre**:<br />CannotDeleteAsItIsReadOnly<br />**Hex**:<br />80040228<br />**Número**:<br />-2147220952|No se pudo eliminar el objeto porque es de solo lectura.|
> |**Nombre**:<br />CannotDeleteAttributeUsedInWorkflow<br />**Hex**:<br />80045030<br />**Número**:<br />-2147200976|Este atributo no se puede eliminar porque se usa en uno o varios flujos de trabajo. Cancele los trabajos del sistema para flujos de trabajo que usan este atributo, luego elimine o modifique los flujos de trabajo que utilicen el atributo y después intente eliminar el atributo de nuevo.|
> |**Nombre**:<br />CannotDeleteBaseMoneyCalculationAttribute<br />**Hex**:<br />80048cfe<br />**Número**:<br />-2147185410|El atributo de cálculo del dinero base no es válido para la eliminación|
> |**Nombre**:<br />CannotDeleteCannedView<br />**Hex**:<br />8004022f<br />**Número**:<br />-2147220945|Las vistas definidas por el sistema no se pueden eliminar.|
> |**Nombre**:<br />CannotDeleteCDSUser<br />**Hex**:<br />80041d5a<br />**Número**:<br />-2147213990|El rol de usuario de Common Data Service no se puede eliminar.|
> |**Nombre**:<br />CannotDeleteChannelAccessProfileRule<br />**Hex**:<br />80061108<br />**Número**:<br />-2147086072|No se puede eliminar una regla de perfil de acceso al canal activo. Desactive la regla y, a continuación, elimínela.|
> |**Nombre**:<br />CannotDeleteChannelProperty<br />**Hex**:<br />800608EB<br />**Número**:<br />-2147088149|No puede eliminar una propiedad de canal a la que se hace referencia en una regla de conversión.|
> |**Nombre**:<br />CannotDeleteChildAttribute<br />**Hex**:<br />80047016<br />**Número**:<br />-2147192810|El atributo secundario no es válido para la eliminación|
> |**Nombre**:<br />CannotDeleteCustomEntityUsedInWorkflow<br />**Hex**:<br />8004502C<br />**Número**:<br />-2147200980|No se puede eliminar la entidad porque se usa en un flujo de trabajo.|
> |**Nombre**:<br />CannotDeleteDefaultProfile<br />**Hex**:<br />8006099A<br />**Número**:<br />-2147087974|Para eliminar este perfil, primero es necesario definirlo para que deje de ser un perfil de Mobile Offline predeterminado.|
> |**Nombre**:<br />CannotDeleteDefaultStatusOption<br />**Hex**:<br />80044341<br />**Número**:<br />-2147204287|No se pueden eliminar las opciones de estado predeterminadas.|
> |**Nombre**:<br />CannotDeleteDefaultTeam<br />**Hex**:<br />80048307<br />**Número**:<br />-2147187961|No se puede eliminar el equipo predeterminado de la unidad de negocio.|
> |**Nombre**:<br />CannotDeleteDueToAssociation<br />**Hex**:<br />80040227<br />**Número**:<br />-2147220953|El objeto que se ha intentado eliminar está asociado a otro objeto y no se puede eliminar.|
> |**Nombre**:<br />CannotDeleteDueToBasketEntityAssociation<br />**Hex**:<br />80061612<br />**Número**:<br />-2147084782|No se puede eliminar una entidad de recomendación si tiene una entidad de la cesta correspondiente.|
> |**Nombre**:<br />CannotDeleteDynamicPropertyInRetiredState<br />**Hex**:<br />8004F892<br />**Número**:<br />-2147157870|No puede eliminar una propiedad de un producto retirado.|
> |**Nombre**:<br />CannotDeleteDynamicPropertyInUse<br />**Hex**:<br />80081003<br />**Número**:<br />-2146955261|Las propiedades retiradas empleadas en las transacciones no se pueden eliminar.|
> |**Nombre**:<br />CannotDeleteEnumOptionsFromAttributeType<br />**Hex**:<br />80044323<br />**Número**:<br />-2147204317|Puede eliminar opciones solo de los atributos de estado y de la lista desplegable.|
> |**Nombre**:<br />CannotDeleteGuestProfile<br />**Hex**:<br />80061104<br />**Número**:<br />-2147086076|No puede eliminar este perfil de acceso al canal de invitado.|
> |**Nombre**:<br />CannotDeleteInheritedDynamicProperty<br />**Hex**:<br />80081014<br />**Número**:<br />-2146955244|No puede eliminar una propiedad heredada de una familia de productos.|
> |**Nombre**:<br />CannotDeleteInUseAttribute<br />**Hex**:<br />80048418<br />**Número**:<br />-2147187688|El atributo seleccionado no se puede eliminar porque una o varias reglas de detección de duplicados que se están publicando hacen referencia al campo.|
> |**Nombre**:<br />CannotDeleteInUseComponent<br />**Hex**:<br />8004F01F<br />**Número**:<br />-2147160033|El componente {0}({1}) no se puede eliminar porque otros {2} componentes le hacen referencia. Para obtener una lista de componentes de referencia, utilice RetrieveDependenciesForDeleteRequest.|
> |**Nombre**:<br />CannotDeleteInUseEntity<br />**Hex**:<br />80048420<br />**Número**:<br />-2147187680|La entidad seleccionada no se puede eliminar porque una o varias reglas de detección de duplicados en proceso de publicación hacen referencia a la entidad.|
> |**Nombre**:<br />CannotDeleteInUseOptionSet<br />**Hex**:<br />80048417<br />**Número**:<br />-2147187689|No se puede eliminar este conjunto de opciones. El conjunto actual de entidades que hace referencia a este conjunto de opciones es: {0}. Deben quitarse estas referencias para poder eliminar este conjunto de opciones|
> |**Nombre**:<br />CannotDeleteLastEmailAttribute<br />**Hex**:<br />80046FFF<br />**Número**:<br />-2147192833|No se puede eliminar este campo porque se ha habilitado el tipo de registro para correo electrónico.|
> |**Nombre**:<br />CannotDeleteMetadata<br />**Hex**:<br />8004F032<br />**Número**:<br />-2147160014|La operación '{2}' del componente actual (nombre ='{0}', identificador ='{1}') ha dado error durante la evaluación de propiedades administradas de la condición: '{3}'|
> |**Nombre**:<br />CannotDeleteMetricWithGoals<br />**Hex**:<br />80044800<br />**Número**:<br />-2147203072|Uno o varios objetivos están usando la métrica de este objetivo y no se pueden eliminar.|
> |**Nombre**:<br />CannotDeleteNonLeafNode<br />**Hex**:<br />8004F200<br />**Número**:<br />-2147159552|Solo se puede eliminar la declaración de una hoja. Esta declaración tiene una relación jerárquica con alguna otra declaración.|
> |**Nombre**:<br />CannotDeleteNotOwnedDynamicProperty<br />**Hex**:<br />80081006<br />**Número**:<br />-2146955258|No puede eliminar una propiedad dinámica de una familia de productos.|
> |**Nombre**:<br />CannotDeleteOneNoteTableOfContent<br />**Hex**:<br />800608B7<br />**Número**:<br />-2147088201|No puede eliminar este archivo porque contiene vínculos con las secciones de bloc de notas OneNote. Para eliminar el contenido del bloc de notas, abra el bloc de notas en OneNote y elimine el contenido desde allí. Para eliminar un bloc de notas, abra SharePoint y elimine desde allí el bloc de notas.|
> |**Nombre**:<br />CannotDeleteOnlineRecord<br />**Hex**:<br />8005F248<br />**Número**:<br />-2147093944|No se puede eliminar este registro porque no existe en el modo sin conexión.|
> |**Nombre**:<br />CannotDeleteOptionSet<br />**Hex**:<br />80048404<br />**Número**:<br />-2147187708|El OptionSet seleccionado no se pudo eliminar|
> |**Nombre**:<br />CannotDeleteOrCancelSystemJobs<br />**Hex**:<br />80044F02<br />**Número**:<br />-2147201278|No puede cancelar o eliminar este trabajo del sistema porque el sistema lo necesita. Solo puede pausar, reanudar o posponer esta tarea.|
> |**Nombre**:<br />CannotDeleteOverriddenProperty<br />**Hex**:<br />80081100<br />**Número**:<br />-2146955008|No puede eliminar esta propiedad porque se ha reemplazado en uno o varios registros secundarios. Quite las versiones reemplazadas de la propiedad, vuelva a publicar la jerarquía de la familia de productos e intente eliminar la propiedad.|
> |**Nombre**:<br />CannotDeletePartnerSolutionWithOrganizations<br />**Hex**:<br />8004A10e<br />**Número**:<br />-2147180274|No se puede eliminar una solución primaria porque tiene asociadas una o varias organizaciones|
> |**Nombre**:<br />CannotDeletePartnerWithPartnerSolutions<br />**Hex**:<br />8004A10d<br />**Número**:<br />-2147180275|No se puede eliminar un partner porque tiene asociadas una o varias soluciones|
> |**Nombre**:<br />CannotDeletePrimaryUIAttribute<br />**Hex**:<br />80047002<br />**Número**:<br />-2147192830|El atributo principal de la interfaz de usuario no es válido para la eliminación|
> |**Nombre**:<br />CannotDeleteProductFromActiveBundle<br />**Hex**:<br />80061010<br />**Número**:<br />-2147086320|No puede quitar productos de una agrupación que esté activa o bajo revisión.|
> |**Nombre**:<br />CannotDeleteProductStatusCode<br />**Hex**:<br />80081016<br />**Número**:<br />-2146955242|No puede eliminar una razón para el estado generada por el sistema.|
> |**Nombre**:<br />CannotDeleteProfileWithExternalPartyItem<br />**Hex**:<br />80061107<br />**Número**:<br />-2147086073|No puede eliminar este perfil de acceso al canal porque está asociado a un elemento de la parte externa. Quite la asociación e inténtelo de nuevo.|
> |**Nombre**:<br />CannotDeleteProfileWithProfileRules<br />**Hex**:<br />80061106<br />**Número**:<br />-2147086074|No puede eliminar este perfil de acceso al canal porque lo están usando una o varias reglas de perfil de acceso al canal. Quite este perfil de las reglas de perfil de acceso de canal e inténtelo de nuevo.|
> |**Nombre**:<br />CannotDeletePropertyOverriddenByBundleItem<br />**Hex**:<br />80081015<br />**Número**:<br />-2146955243|No puede eliminar esta propiedad porque se ha reemplazado en uno o varios productos de agrupación relacionados. Quite las versiones reemplazadas de la propiedad de los productos de la agrupación relacionada, publique las agrupaciones que hayan cambiado y vuelva a intentarlo.|
> |**Nombre**:<br />CannotDeleteQueueWithQueueItems<br />**Hex**:<br />80631117<br />**Número**:<br />-2140991209|No puede eliminar esta cola porque tiene elementos asignados. Asigne estos elementos a otro usuario, equipo o cola e inténtelo de nuevo.|
> |**Nombre**:<br />CannotDeleteQueueWithRouteRules<br />**Hex**:<br />80731118<br />**Número**:<br />-2139942632|No puede eliminar esta cola porque uno o más conjuntos de reglas de enrutamiento utilizan esta cola. Quite la cola de los conjuntos de reglas de enrutamiento e inténtelo de nuevo.|
> |**Nombre**:<br />CannotDeleteRelatedSla<br />**Hex**:<br />8004F859<br />**Número**:<br />-2147157927|No se pudo eliminar el registro de SLA. Inténtelo de nuevo o póngase en contacto con el administrador del sistema.|
> |**Nombre**:<br />CannotDeleteRestrictedPublisher<br />**Hex**:<br />8004F006<br />**Número**:<br />-2147160058|Intentando eliminar un editor restringido.|
> |**Nombre**:<br />CannotDeleteRestrictedSolution<br />**Hex**:<br />8004F005<br />**Número**:<br />-2147160059|Intentando eliminar una solución restringida.|
> |**Nombre**:<br />CannotDeleteSupportUser<br />**Hex**:<br />80041d42<br />**Número**:<br />-2147214014|El rol de usuario de soporte no se puede eliminar.|
> |**Nombre**:<br />CannotDeleteSysAdmin<br />**Hex**:<br />80041d2e<br />**Número**:<br />-2147214034|No se puede eliminar el rol de administrador del sistema.|
> |**Nombre**:<br />CannotDeleteSystemCustomizer<br />**Hex**:<br />80041d4a<br />**Número**:<br />-2147214006|No se puede eliminar el rol de personalizador de sistema.|
> |**Nombre**:<br />CannotDeleteSystemEmailTemplate<br />**Hex**:<br />80048432<br />**Número**:<br />-2147187662|Las plantillas de correo electrónico no se pueden eliminar.|
> |**Nombre**:<br />CannotDeleteSystemForm<br />**Hex**:<br />8004F652<br />**Número**:<br />-2147158446|No se pueden eliminar los formularios del sistema.|
> |**Nombre**:<br />CannotDeleteSystemTheme<br />**Hex**:<br />800608DA<br />**Número**:<br />-2147088166|No puede suprimir los temas del sistema.|
> |**Nombre**:<br />CannotDeleteTeamOwningRecords<br />**Hex**:<br />8004830E<br />**Número**:<br />-2147187954|No se puede eliminar un equipo (ID = {0}) que sea propietario de registros. Reasignar los registros e inténtelo de nuevo.|
> |**Nombre**:<br />CannotDeleteUpdateInUseRule<br />**Hex**:<br />80048428<br />**Número**:<br />-2147187672|La regla de detección de duplicados se está usando actualmente y no se puede actualizar ni eliminar. Vuelva a intentarlo más tarde.|
> |**Nombre**:<br />CannotDeleteUserMailbox<br />**Hex**:<br />8005E200<br />**Número**:<br />-2147098112|No es posible eliminar el buzón asociado a un usuario o una cola.|
> |**Nombre**:<br />CannotDeleteUserProfile<br />**Hex**:<br />800609A3<br />**Número**:<br />-2147087965|No puede eliminar un perfil de Mobile Offline activo. Quite todos los usuarios del perfil e inténtelo de nuevo.|
> |**Nombre**:<br />CannotDeserializeRequest<br />**Hex**:<br />8004416f<br />**Número**:<br />-2147204753|No se ha podido deserializar la solicitud de SDK.|
> |**Nombre**:<br />CannotDeserializeWorkflowInstance<br />**Hex**:<br />8004501F<br />**Número**:<br />-2147200993|No se puede deserializar la instancia de flujo de trabajo. Un posible motivo de este error es un flujo de trabajo que hace referencia a una actividad personalizada que se ha eliminado del registro.|
> |**Nombre**:<br />CannotDeserializeXamlWorkflow<br />**Hex**:<br />80045020<br />**Número**:<br />-2147200992|No se puede deserializar el flujo de trabajo que representa XAML en una DynamicActivity.|
> |**Nombre**:<br />CannotDisableAutoCreateAccessTeams<br />**Hex**:<br />80048338<br />**Número**:<br />-2147187912|No puede deshabilitar la configuración de creación automática de equipos de acceso mientras haya plantillas de equipo asociadas.|
> |**Nombre**:<br />CannotDisableDuplicateDetection<br />**Hex**:<br />80048462<br />**Número**:<br />-2147187614|La detección de duplicados no se puede deshabilitar porque hay un trabajo de detección de duplicados en curso. Vuelva a intentarlo más tarde.|
> |**Nombre**:<br />CannotDisableInternetMarketingUser<br />**Hex**:<br />80045033<br />**Número**:<br />-2147200973|No se puede deshabilitar el usuario asociado de Marketing por Internet. Este usuario no usa ninguna licencia de usuario y no genera cargos para la organización.|
> |**Nombre**:<br />CannotDisableMobileOfflineFlagForEntity<br />**Hex**:<br />800609A5<br />**Número**:<br />-2147087963|No se puede deshabilitar la marca de Mobile Offline para esta entidad porque se está usando en los perfiles de Mobile Offline|
> |**Nombre**:<br />CannotDisableMobileOfflineFlagForImportEntity<br />**Hex**:<br />80071111<br />**Número**:<br />-2147020527|No puede deshabilitar Mobile Offline para la entidad {0} mediante la importación de la solución. Si no desea usar esta entidad en modo sin conexión, desactive el indicador 'Habilitar para Mobile Offline' desde la pantalla de personalización|
> |**Nombre**:<br />CannotDisableOrDeletePositionDueToAssociatedUsers<br />**Hex**:<br />80048343<br />**Número**:<br />-2147187901|No se puede eliminar esta posición hasta que no se eliminen todos los usuarios asociados de esta posición.|
> |**Nombre**:<br />CannotDisableRelevanceSearchManagedProperty<br />**Hex**:<br />80060303<br />**Número**:<br />-2147089661|La entidad {0} se está sincronizando con un índice de búsqueda externo.  Debe quitar la entidad del índice de búsqueda externo para poder establecer la propiedad "Se puede habilitar la sincronización con el índice de búsqueda externo" como False.|
> |**Nombre**:<br />CannotDisableSysAdmin<br />**Hex**:<br />80041d2f<br />**Número**:<br />-2147214033|Un usuario no puede estar deshabilitado si es el único que tiene el rol de administrador del sistema.|
> |**Nombre**:<br />CannotDisableTenantAdmin<br />**Hex**:<br />80041d65<br />**Número**:<br />-2147213979|Los usuarios a quienes se concede el rol de administrador global o administrador de servicios de Microsoft Office 365 no se pueden deshabilitar en Microsoft Dynamics 365 Online. Debe quitar primero el rol de Microsoft Office 365 e intentarlo de nuevo.|
> |**Nombre**:<br />CannotEditActiveRule<br />**Hex**:<br />8004F851<br />**Número**:<br />-2147157935|No se puede editar una regla de enrutamiento activa. Desactive la regla para eliminarla.|
> |**Nombre**:<br />CannotEditActiveSla<br />**Hex**:<br />8004F860<br />**Número**:<br />-2147157920|No puede eliminar el SLA activo. Desactive el SLA para eliminarlo o póngase en contacto con el administrador del sistema.|
> |**Nombre**:<br />CannotEnableDuplicateDetection<br />**Hex**:<br />80048421<br />**Número**:<br />-2147187679|No se puede habilitar la detección de duplicados porque se están publicando una o más reglas.|
> |**Nombre**:<br />CannotEnableEntityForRelevanceSearch<br />**Hex**:<br />80060302<br />**Número**:<br />-2147089662|La entidad {0} no se puede habilitar para la búsqueda por relevancia debido a la configuración de sus propiedades administradas.|
> |**Nombre**:<br />CannotExceedFilterLimit<br />**Hex**:<br />8004027c<br />**Número**:<br />-2147220868|No se puede superar el límite de filtro de sincronización.|
> |**Nombre**:<br />CannotExecuteRequestBecauseHttpsIsRequired<br />**Hex**:<br />8004852C<br />**Número**:<br />-2147187412|Son necesarios protocolos HTTPS para este tipo de solicitud, por favor habilite protocolos HTTPS e inténtelo de nuevo.|
> |**Nombre**:<br />CannotExportRuleOnAnyEntityRoutingRuleFCBOff<br />**Hex**:<br />8004F847<br />**Número**:<br />-2147157945|No se puede exportar el registro de conjunto de regla de enrutamiento para las entidades (excepto la entidad de caso), ya que el bit de control de la característica para el enrutamiento de registros de entidad está deshabilitado.|
> |**Nombre**:<br />CannotFindDomainAccount<br />**Hex**:<br />80044342<br />**Número**:<br />-2147204286|Cuenta de dominio no válida|
> |**Nombre**:<br />CannotFindLayerToMerge<br />**Hex**:<br />8004F060<br />**Número**:<br />-2147159968|No se puede encontrar una capa adecuada para fusionar el Componente: [{0}] con Id: [{1}]. No se puede continuar con la operación. Compruebe las capas del componente.|
> |**Nombre**:<br />CannotFindObjectInQueue<br />**Hex**:<br />800404eb<br />**Número**:<br />-2147220245|No se encontró el objeto en la cola determinada|
> |**Nombre**:<br />CannotFindUserQueue<br />**Hex**:<br />800404ec<br />**Número**:<br />-2147220244|No se puede encontrar la cola de usuario|
> |**Nombre**:<br />CannotFollowInactiveEntity<br />**Hex**:<br />8004F6A3<br />**Número**:<br />-2147158365|No se puede seguir el registro inactivo. |
> |**Nombre**:<br />CannotGrantAccessToAddressBookFilters<br />**Hex**:<br />80048446<br />**Número**:<br />-2147187642|No se puede conceder acceso a los filtros de la libreta de direcciones|
> |**Nombre**:<br />CannotGrantAccessToOfflineFilters<br />**Hex**:<br />80040271<br />**Número**:<br />-2147220879|No se puede conceder acceso a los filtros sin conexión|
> |**Nombre**:<br />CannotGrantAccessToOutlookFilters<br />**Hex**:<br />80040268<br />**Número**:<br />-2147220888|No se puede conceder acceso a los filtros de outlook|
> |**Nombre**:<br />CannotHaveDuplicateYomi<br />**Hex**:<br />80047018<br />**Número**:<br />-2147192808|Un atributo se puede vincular a solo yomi a la vez|
> |**Nombre**:<br />CannotHaveMultipleDefaultFilterTemplates<br />**Hex**:<br />8004027d<br />**Número**:<br />-2147220867|No se pueden tener varias plantilla de sincronización predeterminadas para una única entidad.|
> |**Nombre**:<br />CannotImportNullStringsForBaseLanguage<br />**Hex**:<br />80044246<br />**Número**:<br />-2147204538|La cadena de traducción del idioma base presente en la hoja de cálculo {0}, fila {1}, columna {2} es nula.|
> |**Nombre**:<br />CannotImportRuleOnAnyEntityRoutingRuleFCBOff<br />**Hex**:<br />8004F845<br />**Número**:<br />-2147157947|No se puede importar el registro de conjunto de regla de enrutamiento para las entidades (excepto la entidad de caso), ya que el bit de control de la característica para el enrutamiento de registros de entidad está deshabilitado.|
> |**Nombre**:<br />CannotImportRuleOnFieldMetadataUnavailable<br />**Hex**:<br />8004F846<br />**Número**:<br />-2147157946|No se puede importar el registro de conjunto de regla de enrutamiento para las entidades (excepto la entidad de caso), ya que los metadatos para el campo msdyn_entitylogicalname no están disponibles.|
> |**Nombre**:<br />CannotInviteDisabledUser<br />**Hex**:<br />8004D212<br />**Número**:<br />-2147167726|No se puede enviar una invitación a un usuario deshabilitado|
> |**Nombre**:<br />CannotLocateRecordForWorkflowActivity<br />**Hex**:<br />80045031<br />**Número**:<br />-2147200975|No se pudo encontrar el registro que este flujo de trabajo requiere.|
> |**Nombre**:<br />CannotMakeReadOnlyUser<br />**Hex**:<br />80041d38<br />**Número**:<br />-2147214024|Un usuario no puede configurarse como usuario de solo lectura si es el último usuario de no solo lectura que tiene el rol de administrador del sistema.|
> |**Nombre**:<br />CannotMakeSelfReadOnlyUser<br />**Hex**:<br />80041d39<br />**Número**:<br />-2147214023|No puede hacerse usted mismo usuario de solo lectura|
> |**Nombre**:<br />CannotMergeCase<br />**Hex**:<br />8004F457<br />**Número**:<br />-2147158953|No se pudo realizar la fusión. No se han podido cancelar uno o varios de los casos seleccionados debido a las reglas de transición de estado definidas para los casos.|
> |**Nombre**:<br />CannotModifyAccessToAddressBookFilters<br />**Hex**:<br />80048445<br />**Número**:<br />-2147187643|No se puede modificar el acceso a los filtros de la libreta de direcciones|
> |**Nombre**:<br />CannotModifyAccessToOfflineFilters<br />**Hex**:<br />80040272<br />**Número**:<br />-2147220878|No se puede modificar el acceso a los filtros sin conexión|
> |**Nombre**:<br />CannotModifyAccessToOutlookFilters<br />**Hex**:<br />80040269<br />**Número**:<br />-2147220887|No se puede modificar el acceso a los filtros de outlook|
> |**Nombre**:<br />CannotModifyOldDataFromImport<br />**Hex**:<br />80040376<br />**Número**:<br />-2147220618|El registro correspondiente en Microsoft Dynamics 365 tiene más datos recientes, por lo que se ha ignorado este registro.|
> |**Nombre**:<br />CannotModifyPatchedSolution<br />**Hex**:<br />80048538<br />**Número**:<br />-2147187400|La solución no se puede modificar porque contiene las siguientes revisiones {0}.|
> |**Nombre**:<br />CannotModifyReportOutsideSolutionIfManaged<br />**Hex**:<br />8004F038<br />**Número**:<br />-2147160008|La solución administrado no puede actualizar los informes que no estén presentes en el paquete de la solución.|
> |**Nombre**:<br />CannotModifyRollupDependentField<br />**Hex**:<br />80060555<br />**Número**:<br />-2147089067|El campo consolidado {0} ha creado este campo. No se puede modificar directamente.|
> |**Nombre**:<br />CannotModifySpecialUser<br />**Hex**:<br />80041d33<br />**Número**:<br />-2147214029|No se permiten modificaciones al usuario 'Sistema' o 'Integración'.|
> |**Nombre**:<br />CannotModifySupportUser<br />**Hex**:<br />80041d43<br />**Número**:<br />-2147214013|El rol de usuario de soporte no se puede modificar.|
> |**Nombre**:<br />CannotModifySysAdmin<br />**Hex**:<br />80041d31<br />**Número**:<br />-2147214031|No se puede modificar el rol de administrador del sistema.|
> |**Nombre**:<br />CannotOverrideOwnedDynamicProperty<br />**Hex**:<br />80081005<br />**Número**:<br />-2146955259|No puede reemplazar una propiedad no heredada de una familia de productos.|
> |**Nombre**:<br />CannotOverrideProperty<br />**Hex**:<br />8004F887<br />**Número**:<br />-2147157881|No puede reemplazar esta propiedad ya que existe otra versión reemplazada de esta propiedad. Elimine la versión previamente anulada e inténtelo de nuevo.|
> |**Nombre**:<br />CannotOverridePropertyFromDifferentHierarchy<br />**Hex**:<br />8004F914<br />**Número**:<br />-2147157740|No se puede reemplazar una propiedad que pertenece a una jerarquía de productos diferente.|
> |**Nombre**:<br />CannotOverwriteActiveComponent<br />**Hex**:<br />8004F016<br />**Número**:<br />-2147160042|Una solución administrada no se puede sobrescribir el {0} componente {1} con identificador={2} que tiene una instancia de base no administrada.  El escenario más probable de este error es que una solución no administrada ha instalado un nuevo componente {0} no administrado en el sistema de destino y ahora una solución administrada del mismo editor está intentando instalar el mismo {0} componente como administrado.  Esto tiene como resultado una disposición en capas de las soluciones no válida en el sistema de destino y no está permitido.|
> |**Nombre**:<br />CannotOverwriteProperty<br />**Hex**:<br />80061036<br />**Número**:<br />-2147086282|No puede sobrescribir esta propiedad ya que existe otra versión sobrescrita de esta propiedad. Elimine la versión previamente sobrescrita e inténtelo de nuevo.|
> |**Nombre**:<br />CannotPayNonActiveInvoice<br />**Hex**:<br />80100000<br />**Número**:<br />-2146435072|La factura no se puede pagar porque no se encuentra en estado activa.|
> |**Nombre**:<br />CannotPropagateCamapaignActivityForTemplate<br />**Hex**:<br />80040311<br />**Número**:<br />-2147220719|No se puede ejecutar (distribuir) la CampaignActivity para una campaña de plantilla.|
> |**Nombre**:<br />CannotProvisionPartnerSolution<br />**Hex**:<br />8004A10f<br />**Número**:<br />-2147180273|No se pueden proporcionar solución primaria porque o está ya aprovisionado o está en proceso de aprovisionamiento.|
> |**Nombre**:<br />CannotPublishAppModule<br />**Hex**:<br />80050114<br />**Número**:<br />-2147155692|No podemos publicar la aplicación porque tiene errores de validación.|
> |**Nombre**:<br />CannotPublishBundleWithProductStateDraftOrRetire<br />**Hex**:<br />8004F907<br />**Número**:<br />-2147157753|No puede publicar esta agrupación porque sus productos asociados están en estado Borrador, están retirados o se están revisando.|
> |**Nombre**:<br />CannotPublishChildOfNonActiveProductFamily<br />**Hex**:<br />8004F909<br />**Número**:<br />-2147157751|No puede publicar este registro porque pertenece a una familia de productos que no está publicada.|
> |**Nombre**:<br />CannotPublishEmptyRule<br />**Hex**:<br />80048414<br />**Número**:<br />-2147187692|Se han especificado sin criterios. Agregue criterios y, después, publique la regla de detección de duplicados.|
> |**Nombre**:<br />CannotPublishInactiveRule<br />**Hex**:<br />80048413<br />**Número**:<br />-2147187693|La regla de detección de duplicados seleccionada está marcada como inactiva. Antes de su publicación, debe activar la regla.|
> |**Nombre**:<br />CannotPublishKitWithProductStateDraftOrRetire<br />**Hex**:<br />8004F916<br />**Número**:<br />-2147157738|No puede publicar este kit porque sus productos asociados están en estado Borrador, están retirados o se están revisando.|
> |**Nombre**:<br />CannotPublishMoreRules<br />**Hex**:<br />80048419<br />**Número**:<br />-2147187687|El tipo de registro seleccionado ya tiene el número máximo de reglas publicadas. Anule la publicación o elimine las reglas existentes para este tipo de registro e inténtelo de nuevo.|
> |**Nombre**:<br />CannotPublishNestedBundle<br />**Hex**:<br />80061011<br />**Número**:<br />-2147086319|No puede publicar una agrupación que contenga agrupaciones. Quite las agrupaciones de esta agrupación e intente publicar de nuevo.|
> |**Nombre**:<br />CannotQualifyLead<br />**Hex**:<br />80081018<br />**Número**:<br />-2146955240|No puede clasificar este cliente potencial porque no tiene permiso para crear cuentas. Trabaje con el administrador del sistema para crear la cuenta e inténtelo de nuevo.|
> |**Nombre**:<br />CannotQueryBaseTableWithAggregates<br />**Hex**:<br />8004F00D<br />**Número**:<br />-2147160051|La consulta no es válida en la tableta base.  Agregados no se pueden incluir en la consulta de tabla base.|
> |**Nombre**:<br />CannotRelateObjectTypeToCampaign<br />**Hex**:<br />80040307<br />**Número**:<br />-2147220729|El tipo de objeto especificado no se admite|
> |**Nombre**:<br />CannotRelateObjectTypeToCampaignActivity<br />**Hex**:<br />8004030d<br />**Número**:<br />-2147220723|El tipo de objeto especificado no se admite|
> |**Nombre**:<br />CannotRemoveComponentFromDefaultSolution<br />**Hex**:<br />8004F000<br />**Número**:<br />-2147160064|No se puede quitar un componente de la solución de la solución predeterminada.|
> |**Nombre**:<br />CannotRemoveComponentFromSolution<br />**Hex**:<br />8004F021<br />**Número**:<br />-2147160031|No se puede encontrar el componente de la solución {0} {1} en la solución {2}.|
> |**Nombre**:<br />CannotRemoveComponentFromSystemSolution<br />**Hex**:<br />8004F035<br />**Número**:<br />-2147160011|No se puede quitar un componente de la solución de la solución del sistema.|
> |**Nombre**:<br />CannotRemoveFromSupportUser<br />**Hex**:<br />80041d45<br />**Número**:<br />-2147214011|Un usuario no puede ser eliminado del rol de usuario de soporte.|
> |**Nombre**:<br />CannotRemoveFromSysAdmin<br />**Hex**:<br />80041d30<br />**Número**:<br />-2147214032|Un usuario no puede ser eliminado del rol de administrador del sistema si es el único que tiene ese rol.|
> |**Nombre**:<br />CannotRemoveMembersFromDefaultTeam<br />**Hex**:<br />8004830C<br />**Número**:<br />-2147187956|No se pueden eliminar miembros del equipo de unidad de negocio predeterminado.|
> |**Nombre**:<br />CannotRemoveNonListMember<br />**Hex**:<br />80048458<br />**Número**:<br />-2147187624|El elemento especificado no es miembro de la lista indicada.|
> |**Nombre**:<br />CannotRemoveProductFromPricelist<br />**Hex**:<br />80061008<br />**Número**:<br />-2147086328|No puede quitar este producto de la lista de precios porque existen una o más agrupaciones que hacen referencia a él.|
> |**Nombre**:<br />CannotRemoveSysAdminProfileFromSysAdminUser<br />**Hex**:<br />8004F505<br />**Número**:<br />-2147158779|No se puede quitar el perfil de administrador del sistema de un usuario con el rol de administrador del sistema|
> |**Nombre**:<br />CannotRemoveTenantAdminFromSysAdminRole<br />**Hex**:<br />80041d64<br />**Número**:<br />-2147213980|Los usuarios a quienes se concede el rol de administrador global o administrador de servicios de Microsoft Office 365 no se pueden quitar del rol de seguridad Administrador del sistema de Microsoft Dynamics 365. Debe quitar primero el rol de Microsoft Office 365 e intentarlo de nuevo.|
> |**Nombre**:<br />CannotResetAppointmentsToDraft<br />**Hex**:<br />8004026a<br />**Número**:<br />-2147220886|Las citas no se pueden restablecer a borrador.|
> |**Nombre**:<br />CannotResetSysAdminInvite<br />**Hex**:<br />8004D214<br />**Número**:<br />-2147167724|No puede restablecerse una invitación para un usuario si es el único que tiene el rol de administrador del sistema.|
> |**Nombre**:<br />CannotRetireProduct<br />**Hex**:<br />8004F915<br />**Número**:<br />-2147157739|No puede retirar este producto porque pertenece a agrupaciones o listas de precios activas. Quítelo de las agrupaciones o de las listas de precios antes de retirarlo.|
> |**Nombre**:<br />CannotRetireProductFromActiveBundle<br />**Hex**:<br />8004F997<br />**Número**:<br />-2147157609|Este producto no se pueden retirar puesto que es parte de algunas agrupaciones o listas de precios activas. Quítelo de las agrupaciones o de las listas de precios antes de retirarlo.|
> |**Nombre**:<br />CannotRevokeAccessToAddressBookFilters<br />**Hex**:<br />80048444<br />**Número**:<br />-2147187644|No se puede revocar el acceso a los filtros de la libreta de direcciones|
> |**Nombre**:<br />CannotRevokeAccessToOfflineFilters<br />**Hex**:<br />80040273<br />**Número**:<br />-2147220877|No se puede revocar el acceso a los filtros sin conexión|
> |**Nombre**:<br />CannotRevokeAccessToOutlookFilters<br />**Hex**:<br />80040270<br />**Número**:<br />-2147220880|No se puede revocar el acceso a los filtros de outlook|
> |**Nombre**:<br />CannotRouteInactiveQueueItem<br />**Hex**:<br />80040527<br />**Número**:<br />-2147220185|No se puede distribuir un elemento de cola desactivado.|
> |**Nombre**:<br />CannotRoutePrivateQueueItemNonmember<br />**Hex**:<br />80631121<br />**Número**:<br />-2140991199|No se puede asignar el elemento de cola privado al usuario seleccionado.|
> |**Nombre**:<br />CannotRouteToNonQueueMember<br />**Hex**:<br />80731119<br />**Número**:<br />-2139942631|Este elemento no se puede enrutar a un miembro externo a la cola.|
> |**Nombre**:<br />CannotRouteToQueue<br />**Hex**:<br />800404ea<br />**Número**:<br />-2147220246|No se puede redirigir a la cola de trabajo en curso|
> |**Nombre**:<br />CannotRouteToSameQueue<br />**Hex**:<br />8004051b<br />**Número**:<br />-2147220197|El elemento de cola no se puede enrutar a la misma cola|
> |**Nombre**:<br />CannotSecureAttribute<br />**Hex**:<br />8004F501<br />**Número**:<br />-2147158783|El campo '{0}' no se puede proteger|
> |**Nombre**:<br />CannotSecureEntityKeyAttribute<br />**Hex**:<br />80060896<br />**Número**:<br />-2147088234|El campo {0} no se puede proteger como parte de claves de entidad ( {1} ). Quite el campo de todas las claves de entidad para asegurarse de que se puede proteger.|
> |**Nombre**:<br />CannotSelectReadOnlyPublisher<br />**Hex**:<br />8004F034<br />**Número**:<br />-2147160012|Intentando seleccionar un editor de solo lectura para la solución.|
> |**Nombre**:<br />CannotSendInviteToDuplicateWindowsLiveId<br />**Hex**:<br />8004D215<br />**Número**:<br />-2147167723|No se puede enviar una invitación porque hay varios usuarios con este WLID.|
> |**Nombre**:<br />CannotSetCaseOnHold<br />**Hex**:<br />80055000<br />**Número**:<br />-2147135488|No dispone de los permisos para poner este caso en estado de suspensión. Póngase en contacto con el administrador del sistema.|
> |**Nombre**:<br />CannotSetEntitlementTermsDecrementBehavior<br />**Hex**:<br />80060851<br />**Número**:<br />-2147088303|No dispone de los privilegios adecuados para especificar si se pueden reducir los términos de derecho para este registro de caso.|
> |**Nombre**:<br />CannotSetEntityOnHold<br />**Hex**:<br />80055004<br />**Número**:<br />-2147135484|No tiene permiso para poner en espera este registro. Póngase en contacto con el administrador del sistema.|
> |**Nombre**:<br />CannotSetInactiveViewAsDefault<br />**Hex**:<br />8004027b<br />**Número**:<br />-2147220869|No se pueden configurar como vista predeterminada las vistas inactivas.|
> |**Nombre**:<br />CannotSetParentDefaultTeam<br />**Hex**:<br />80048308<br />**Número**:<br />-2147187960|No se puede establecer el elemento primario del equipo predeterminado de la unidad de negocio.|
> |**Nombre**:<br />CannotSetProductAsParent<br />**Hex**:<br />8004F998<br />**Número**:<br />-2147157608|Solo puede seleccionar una familia de productos como elemento primario.|
> |**Nombre**:<br />CannotSetPublishRetiredProductsToDraft<br />**Hex**:<br />80061035<br />**Número**:<br />-2147086283|No puede establecer en estado Borrador un registro del producto publicado o retirado.|
> |**Nombre**:<br />CannotSetSolutionSystemAttributes<br />**Hex**:<br />8004F008<br />**Número**:<br />-2147160056|Los atributos del sistema ({0}) no se pueden establecer fuera de instalación o actualización.|
> |**Nombre**:<br />CannotSetWindowsLiveIdForInternetMarketingUser<br />**Hex**:<br />80045034<br />**Número**:<br />-2147200972|No puede cambiar el Windows Live ID del usuario asociado de marketing por Internet. Este usuario no usa ninguna licencia de usuario y no genera cargos para la organización.|
> |**Nombre**:<br />CannotShareSystemManagedTeam<br />**Hex**:<br />80048339<br />**Número**:<br />-2147187911|No puede compartir o dejar de compartir un registro con un equipo de acceso generado por el sistema.|
> |**Nombre**:<br />CannotShareWithOwner<br />**Hex**:<br />80040214<br />**Número**:<br />-2147220972|No se puede compartir un elemento con el usuario propietario.|
> |**Nombre**:<br />CannotSpecifyAttendeeForAppointmentPropagation<br />**Hex**:<br />8004031c<br />**Número**:<br />-2147220708|No se puede especificar un asistente para distribución de cita.|
> |**Nombre**:<br />CannotSpecifyBothProductAndProductDesc<br />**Hex**:<br />80043afb<br />**Número**:<br />-2147206405|No puede establecer 'productid' y 'productdescription' para el mismo registro.|
> |**Nombre**:<br />CannotSpecifyBothUomAndProductDesc<br />**Hex**:<br />80043afa<br />**Número**:<br />-2147206406|No puede establecer 'uomid' y 'productdescription' para el mismo registro.|
> |**Nombre**:<br />CannotSpecifyCommunicationAttributeOnActivityForPropagation<br />**Hex**:<br />8004031e<br />**Número**:<br />-2147220706|No se puede especificar un atributo de comunicación en la actividad para su distribución|
> |**Nombre**:<br />CannotSpecifyOrganizerForAppointmentPropagation<br />**Hex**:<br />8004031a<br />**Número**:<br />-2147220710|No se puede especificar un organizador para distribución de cita.|
> |**Nombre**:<br />CannotSpecifyOwnerForActivityPropagation<br />**Hex**:<br />80040327<br />**Número**:<br />-2147220697|No se puede especificar un propietario en una actividad para distribución|
> |**Nombre**:<br />CannotSpecifyRecipientForActivityPropagation<br />**Hex**:<br />8004031d<br />**Número**:<br />-2147220707|No se puede especificar un destinatario para la distribución de actividad.|
> |**Nombre**:<br />CannotSpecifySenderForActivityPropagation<br />**Hex**:<br />8004031b<br />**Número**:<br />-2147220709|No se puede especificar un remitente para distribución de cita.|
> |**Nombre**:<br />CannotUndeleteLabel<br />**Hex**:<br />8004F003<br />**Número**:<br />-2147160061|Intentando recuperar una etiqueta no marcada para como eliminada.|
> |**Nombre**:<br />CannotUninstallReferencedProtectedSolution<br />**Hex**:<br />8004F020<br />**Número**:<br />-2147160032|Esta solución no se puede desinstalar porque el '{0}' con id '{1}' es requerido por la solución '{2}'. Desinstale la solución {2} e inténtelo de nuevo.|
> |**Nombre**:<br />CannotUninstallWithDependencies<br />**Hex**:<br />8004F01D<br />**Número**:<br />-2147160035|Existen dependencias de la solución, no se puede desinstalar.|
> |**Nombre**:<br />CannotUpdateActiveModernFlow<br />**Hex**:<br />80060466<br />**Número**:<br />-2147089306|No puede actualizar la propiedad "{0}" en un proceso de flujo moderno publicado.|
> |**Nombre**:<br />CannotUpdateAppDefaultValueForStateAttribute<br />**Hex**:<br />80044343<br />**Número**:<br />-2147204285|No se puede actualizar el valor predeterminado de un atributo de estado (statecode).|
> |**Nombre**:<br />CannotUpdateAppDefaultValueForStatusAttribute<br />**Hex**:<br />80044344<br />**Número**:<br />-2147204284|No se puede utilizar el valor predeterminado de un atributo de razón para el estado (statecode). La razón para el estado predeterminada se establece en la opción de atributo de estado asociado (statecode).|
> |**Nombre**:<br />CannotUpdateAppModuleClientType<br />**Hex**:<br />80050128<br />**Número**:<br />-2147155672|No puede cambiar el tipo de cliente de esta aplicación.|
> |**Nombre**:<br />CannotUpdateAppModuleUniqueName<br />**Hex**:<br />80050119<br />**Número**:<br />-2147155687|No puede cambiar el nombre único.|
> |**Nombre**:<br />CannotUpdateAzureActiveDirectoryObjectIdField<br />**Hex**:<br />80041d4f<br />**Número**:<br />-2147214001|No se puede modificar la propiedad AzureActiveDirectoryObjectId.|
> |**Nombre**:<br />CannotUpdateBecauseItIsReadOnly<br />**Hex**:<br />8004022e<br />**Número**:<br />-2147220946|No se pudo actualizar el objeto porque es de solo lectura.|
> |**Nombre**:<br />CannotUpdateCampaignForCampaignActivity<br />**Hex**:<br />8004030b<br />**Número**:<br />-2147220725|La campaña principal no se puede actualizar.|
> |**Nombre**:<br />CannotUpdateCampaignForCampaignResponse<br />**Hex**:<br />8004030c<br />**Número**:<br />-2147220724|La campaña principal no se puede actualizar.|
> |**Nombre**:<br />CannotUpdateDeactivatedQueueItem<br />**Hex**:<br />8004051d<br />**Número**:<br />-2147220195|Este artículo está desactivado. Para trabajar con este elemento, reactívelo e inténtelo de nuevo.|
> |**Nombre**:<br />CannotUpdateDefaultField<br />**Hex**:<br />800608D8<br />**Número**:<br />-2147088168|No puede actualizar el atributo isdefaultTheme.|
> |**Nombre**:<br />CannotUpdateDefaultSolution<br />**Hex**:<br />8004F009<br />**Número**:<br />-2147160055|El atributo de la solución predeterminado{0} {1} solo se puede establecer en la instalación o actualización.  El valor{0} no se puede modificar.|
> |**Nombre**:<br />CannotUpdateDelaySendTimeForEmailWhenEmailIsNotInProperState<br />**Hex**:<br />80050020<br />**Número**:<br />-2147155936|No podemos actualizar el tiempo de envío retrasado porque el correo electrónico no es un borrador o no está programado para que se envíe.|
> |**Nombre**:<br />CannotUpdateDelaySendTimeWhenEEFeatureNotEnabled<br />**Hex**:<br />80050021<br />**Número**:<br />-2147155935|No podemos actualizar el tiempo de envío retrasado porque no está activada la interacción por correo electrónico para la organización.|
> |**Nombre**:<br />CannotUpdateDraftProducts<br />**Hex**:<br />8004F975<br />**Número**:<br />-2147157643|Solo puede actualizar borradores de productos.|
> |**Nombre**:<br />CannotUpdateEmailStatisticForEmailNotFollowed<br />**Hex**:<br />80050002<br />**Número**:<br />-2147155966|No podemos actualizar las estadísticas de correo electrónico porque no se está siguiendo el correo electrónico.|
> |**Nombre**:<br />CannotUpdateEmailStatisticForEmailNotSent<br />**Hex**:<br />80050001<br />**Número**:<br />-2147155967|No podemos actualizar las estadísticas de correo electrónico porque no se ha enviado el correo electrónico.|
> |**Nombre**:<br />CannotUpdateEmailStatisticWhenEEFeatureNotEnabled<br />**Hex**:<br />80050018<br />**Número**:<br />-2147155944|No podemos actualizar las estadísticas de correo electrónico porque no está activada la interacción por correo electrónico para la organización.|
> |**Nombre**:<br />CannotUpdateEntitlement<br />**Hex**:<br />80060852<br />**Número**:<br />-2147088302|Solo puede establecer registros de derecho activos como predeterminados.|
> |**Nombre**:<br />CannotUpdateEntitySetName<br />**Hex**:<br />8004F663<br />**Número**:<br />-2147158429|No se puede actualizar EntitySetName para las entidades OOB|
> |**Nombre**:<br />CannotUpdateExternalPartyWithSameCorrelationKey<br />**Hex**:<br />80061114<br />**Número**:<br />-2147086060|Ya existe un registro de entidad externa con el mismo valor de clave de correlación.|
> |**Nombre**:<br />CannotUpdateGoalPeriodInfoChildGoal<br />**Hex**:<br />80044901<br />**Número**:<br />-2147202815|No se pueden actualizar los atributos relacionados con el período del objetivo en un objetivo secundario.|
> |**Nombre**:<br />CannotUpdateGoalPeriodInfoClosedGoal<br />**Hex**:<br />80044910<br />**Número**:<br />-2147202800|No se puede cambiar el período de tiempo del objetivo porque hay uno o varios objetivos subordinados cerrados.|
> |**Nombre**:<br />CannotUpdateLogicalAttribute<br />**Hex**:<br />80048461<br />**Número**:<br />-2147187615|No se puede actualizar el atributo lógico {0} |
> |**Nombre**:<br />CannotUpdateManagedSolution<br />**Hex**:<br />8004F024<br />**Número**:<br />-2147160028|No se puede actualizar la solución '{0}' porque es una solución administrada.|
> |**Nombre**:<br />CannotUpdateMetricOnChildGoal<br />**Hex**:<br />80044900<br />**Número**:<br />-2147202816|No se puede actualizar la métrica en un objetivo secundario.|
> |**Nombre**:<br />CannotUpdateMetricOnGoalWithChildren<br />**Hex**:<br />80044902<br />**Número**:<br />-2147202814|No se puede actualizar la métrica en un objetivo que tiene objetivos secundarios relacionados.|
> |**Nombre**:<br />CannotUpdateMetricWithGoals<br />**Hex**:<br />80044803<br />**Número**:<br />-2147203069|Los cambios realizados en este registro no se pueden guardar porque esta métrica del objetivo se está usando en uno o más objetivos.|
> |**Nombre**:<br />CannotUpdateNameDefaultTeam<br />**Hex**:<br />8004830A<br />**Número**:<br />-2147187958|No se puede actualizar el nombre del equipo predeterminado de la unidad de negocio.|
> |**Nombre**:<br />CannotUpdateNonCustomizableString<br />**Hex**:<br />80044247<br />**Número**:<br />-2147204537|La cadena de traducción presente en la hoja de cálculo {0}, fila {1}, columna {2} no se puede personalizar.|
> |**Nombre**:<br />CannotUpdateObjectBecauseItIsInactive<br />**Hex**:<br />80040230<br />**Número**:<br />-2147220944|No se pudo actualizar el objeto porque es inactivo.|
> |**Nombre**:<br />CannotUpdateOpportunityCurrency<br />**Hex**:<br />80048479<br />**Número**:<br />-2147187591|No se puede cambiar la divisa porque esta oportunidad tiene ofertas de productos o pedidos asociados.  Si desea cambiar la divisa, elimine todos los productos/ofertas/pedidos y, después, cambie la divisa o cree una nueva oportunidad con la divisa correspondiente.|
> |**Nombre**:<br />CannotUpdateOrgDBOrgSettingWhenOffline<br />**Hex**:<br />80048515<br />**Número**:<br />-2147187435|La configuración de organización almacenada en la base de datos de la organización no se puede establecer sin conexión.|
> |**Nombre**:<br />CannotUpdateParentAndDependents<br />**Hex**:<br />8004480c<br />**Número**:<br />-2147203060|No se puede actualizar la métrica o atributos de períodos cuando se está actualizando el elemento principal.|
> |**Nombre**:<br />CannotUpdatePrivateOrWIPQueue<br />**Hex**:<br />800404ee<br />**Número**:<br />-2147220242|No se permite actualizar ni eliminar la cola de ubicaciones WIP o privadas.|
> |**Nombre**:<br />CannotUpdateProductCurrency<br />**Hex**:<br />80048cfa<br />**Número**:<br />-2147185414|La divisa de un producto no se puede actualizar porque tiene elementos de la lista de precios asociados con el porcentaje de método de cálculo de precios.|
> |**Nombre**:<br />CannotUpdateQuoteCurrency<br />**Hex**:<br />8004480e<br />**Número**:<br />-2147203058|No se puede cambiar la divisa porque esta oferta tiene productos asociados. Si desea cambiar la divisa, elimine todos los productos y, después, cambie la divisa o cree una nueva oferta con la divisa correspondiente.|
> |**Nombre**:<br />CannotUpdateReadOnlyPublisher<br />**Hex**:<br />8004F033<br />**Número**:<br />-2147160013|Intentando actualizar un editor de solo lectura.|
> |**Nombre**:<br />CanNotUpdateRequiredBundleItem<br />**Hex**:<br />80100009<br />**Número**:<br />-2146435063|No puede actualizar este elemento de agrupación porque es un producto necesario en la agrupación.|
> |**Nombre**:<br />CannotUpdateRestrictedPublisher<br />**Hex**:<br />8004F017<br />**Número**:<br />-2147160041|El editor restringido ({0}) no se puede actualizar.|
> |**Nombre**:<br />CannotUpdateRestrictedSolution<br />**Hex**:<br />8004F00A<br />**Número**:<br />-2147160054|La solución restringida ({0}) no se puede actualizar.|
> |**Nombre**:<br />CannotUpdateRollupAttributeWithClosedGoals<br />**Hex**:<br />80044801<br />**Número**:<br />-2147203071|Los cambios realizados en la definición del campo de informe no se pueden guardar porque uno o varios objetivos cerrados están usando la métrica del objetivo relacionada.|
> |**Nombre**:<br />CannotUpdateRollupFields<br />**Hex**:<br />80044911<br />**Número**:<br />-2147202799|No se puede escribir en los campos consolidados si isoverride no está establecida en true en la solicitud de crear o actualizar.|
> |**Nombre**:<br />CannotUpdateSolutionPatch<br />**Hex**:<br />8004F042<br />**Número**:<br />-2147159998|La revisión de la solución con la versión {0} ya existe. Actualizar la revisión no se admite.|
> |**Nombre**:<br />CannotUpdateSupportUser<br />**Hex**:<br />80041d47<br />**Número**:<br />-2147214009|No se puede actualizar el rol de usuario de soporte .|
> |**Nombre**:<br />CannotUpdateSyncUserIsLicensedField<br />**Hex**:<br />80041d4c<br />**Número**:<br />-2147214004|No se puede modificar la propiedad IsLicensed.|
> |**Nombre**:<br />CannotUpdateSyncUserIsSyncWithDirectoryField<br />**Hex**:<br />80041d4e<br />**Número**:<br />-2147214002|No se puede modificar la propiedad IsSyncUserWithDirectory.|
> |**Nombre**:<br />CannotUpdateSystemEntityIcons<br />**Hex**:<br />8004F653<br />**Número**:<br />-2147158445|No se pueden actualizar los iconos de entidad del sistema.|
> |**Nombre**:<br />CannotUpdateSystemTheme<br />**Hex**:<br />800608D6<br />**Número**:<br />-2147088170|No puede modificar los temas del sistema.|
> |**Nombre**:<br />CannotUpdateTemplateIdForEmailInNonDraftState<br />**Hex**:<br />80050017<br />**Número**:<br />-2147155945|No podemos actualizar la plantilla porque el correo electrónico ya se ha enviado o no está en un estado de borrador.|
> |**Nombre**:<br />CannotUpdateTriggerForPublishedRules<br />**Hex**:<br />80060002<br />**Número**:<br />-2147090430|Un desencadenador no se puede agregar, eliminar o actualizar para una regla publicada.|
> |**Nombre**:<br />CannotUpdateUnpublishedDeleteInstance<br />**Hex**:<br />8004F00F<br />**Número**:<br />-2147160049|Se ha eliminado el componente que intenta actualizar.|
> |**Nombre**:<br />CannotUseOpportunitySetStateMessage<br />**Hex**:<br />80100005<br />**Número**:<br />-2146435067|Este mensaje no se puede usar para establecer el estado de la oportunidad a {0}. Para establecer el estado de la oportunidad a {1}, use el mensaje {1} en su lugar.|
> |**Nombre**:<br />CannotUseUserCredentials<br />**Hex**:<br />8005E229<br />**Número**:<br />-2147098071|El conector de correo electrónico no puede usar las credenciales especificadas en la entidad de buzón. Esto se puede deber a que el usuario no lo permite. Utilice otro modo de obtención de credenciales o permita el uso de credenciales por conector de correo electrónico.|
> |**Nombre**:<br />CanOnlySetActiveOrDraftProductFamilyAsParent<br />**Hex**:<br />8004F906<br />**Número**:<br />-2147157754|Solo puede establecer como elemento primario aquellas familias de productos que tengan el estado Borrador o Activo.|
> |**Nombre**:<br />CantSaveRecordInOffline<br />**Hex**:<br />8005F214<br />**Número**:<br />-2147093996|No puede guardar este registro mientras está sin conexión.|
> |**Nombre**:<br />CantSetIsGuestProfile<br />**Hex**:<br />8006111A<br />**Número**:<br />-2147086054|No puede establecer ni cambiar el valor del campo IsGuestProfile puesto que es solo para uso interno.|
> |**Nombre**:<br />CantUpdateOnlineRecord<br />**Hex**:<br />8005F224<br />**Número**:<br />-2147093980|No puede actualizar este registro porque no existe en el modo sin conexión.|
> |**Nombre**:<br />CanvasAppsExpectedFileMissing<br />**Hex**:<br />80072356<br />**Número**:<br />-2147015850|La solución especificó un archivo de activos esperado pero ese archivo faltaba o no era válido.|
> |**Nombre**:<br />CanvasAppsInvalidSolutionFileContent<br />**Hex**:<br />80072354<br />**Número**:<br />-2147015852|La solicitud para importar una aplicación de lienzo debe contener al menos un archivo de activos.|
> |**Nombre**:<br />CanvasAppsNotEnabled<br />**Hex**:<br />80072351<br />**Número**:<br />-2147015855|La creación y la edición de las aplicaciones de lienzo no está habilitada.|
> |**Nombre**:<br />CanvasAppsServiceRequestClientFailure<br />**Hex**:<br />80072352<br />**Número**:<br />-2147015854|La solicitud al servicio de PowerApps falló con un error de cliente.|
> |**Nombre**:<br />CanvasAppsServiceRequestServerFailure<br />**Hex**:<br />80072353<br />**Número**:<br />-2147015853|La solicitud al servicio de PowerApps falló con un error de sevidor.|
> |**Nombre**:<br />CanvasAppsUnexpectedCanvasAppId<br />**Hex**:<br />80072355<br />**Número**:<br />-2147015851|La solicitud al servicio de PowerApps dio lugar a un nuevo canvasappid cuando se esperaba el valor previamente existente.|
> |**Nombre**:<br />CanvasAppVersionDoesNotMatchLatestPublishedVersion<br />**Hex**:<br />80072358<br />**Número**:<br />-2147015848|La última versión publicada de la aplicación de lienzo no coincide con la versión conocida por el servicio de Dynamics.|
> |**Nombre**:<br />CanvasAppVersionMissingOrInvalid<br />**Hex**:<br />80072357<br />**Número**:<br />-2147015849|La versión de la aplicación de lienzo no se estableció o era un valor no válido.|
> |**Nombre**:<br />CAPolicyValidationFailedLateBind<br />**Hex**:<br />80072561<br />**Número**:<br />-2147015327|El usuario está en una ubicación limitada de administración.|
> |**Nombre**:<br />CascadeDeleteNotAllowDelete<br />**Hex**:<br />80048103<br />**Número**:<br />-2147188477|No se permite eliminar el objeto|
> |**Nombre**:<br />CascadeFailToCreateNativeDAWrapper<br />**Hex**:<br />80048108<br />**Número**:<br />-2147188472|No se puede crear contenedor de acceso de datos no administrados|
> |**Nombre**:<br />CascadeInvalidExtraConditionValue<br />**Hex**:<br />80048101<br />**Número**:<br />-2147188479|Valor de condición adicional no válido|
> |**Nombre**:<br />CascadeInvalidLinkType<br />**Hex**:<br />80048102<br />**Número**:<br />-2147188478|Tipo de CascadeLink no válido|
> |**Nombre**:<br />CascadeInvalidLinkTypeTransition<br />**Hex**:<br />80044155<br />**Número**:<br />-2147204779|Tipo de vínculo no válido para las acciones en cascada de la entidad del sistema.|
> |**Nombre**:<br />CascadeMergeInvalidSpecialColumn<br />**Hex**:<br />80048106<br />**Número**:<br />-2147188474|Nombre de columna no válido para combinación de mayúsculas y minúsculas especiales|
> |**Nombre**:<br />CascadeOperationConcurrentRequested<br />**Hex**:<br />80048105<br />**Número**:<br />-2147188475|Se ha detectado más de una solicitud {0} simultánea para una Entidad {1} y el ObjectTypeCode {2}.|
> |**Nombre**:<br />CascadeProxyEmptyCallerId<br />**Hex**:<br />8004810b<br />**Número**:<br />-2147188469|Id. de autor de la llamada vacío|
> |**Nombre**:<br />CascadeProxyInvalidNativeDAPtr<br />**Hex**:<br />80048109<br />**Número**:<br />-2147188471|Puntero no válido del objeto de acceso de datos no administrados|
> |**Nombre**:<br />CascadeProxyInvalidPrincipalType<br />**Hex**:<br />8004810a<br />**Número**:<br />-2147188470|Tipo principal de seguridad no válido|
> |**Nombre**:<br />CascadeRemoveLinkOnNonNullable<br />**Hex**:<br />80048104<br />**Número**:<br />-2147188476|CascadeDelete se define como RemoveLink mientras la clave externa no admita valores null|
> |**Nombre**:<br />CascadeReparentOnNonUserOwned<br />**Hex**:<br />80048107<br />**Número**:<br />-2147188473|No se puede cambiar el valor primario de cascada en las entidades que no pertenecen a usuarios|
> |**Nombre**:<br />CaseAlreadyResolved<br />**Hex**:<br />800404cf<br />**Número**:<br />-2147220273|Este caso ya se ha resuelto. Cierre y vuelva a abrir el registro de caso para ver las actualizaciones.|
> |**Nombre**:<br />CaseStateChangeInvalid<br />**Hex**:<br />8006074<br />**Número**:<br />134242420|Debido a las reglas de transición de estado, no se puede resolver un caso en el estado actual. Cambie el estado del caso e intente resolverlo o póngase en contacto con el administrador del sistema.|
> |**Nombre**:<br />CategoryDataTypeInvalid<br />**Hex**:<br />8004E01A<br />**Número**:<br />-2147164134|La descripción de datos para la visualización no es válida. El tipo de atributo para el grupo de una de las categorías no es válido. Solucione la descripción de datos.|
> |**Nombre**:<br />CategoryNotSetToBusinessProcessFlow<br />**Hex**:<br />80060404<br />**Número**:<br />-2147089404|La categoría se debe definir en BusinessProcessFlow al crear la categoría de flujo de proceso de negocio|
> |**Nombre**:<br />CDSOrgNotSupported<br />**Hex**:<br />80044510<br />**Número**:<br />-2147203824|Dynamics 365 for Outlook no se admite para esta organización.|
> |**Nombre**:<br />CertificateNotFound<br />**Hex**:<br />8005E239<br />**Número**:<br />-2147098055|No se encuentra el certificado especificado.|
> |**Nombre**:<br />ChangeTrackingDisabledForMobileOfflineError<br />**Hex**:<br />800609A1<br />**Número**:<br />-2147087967|No puede deshabilitar el seguimiento de cambios para esta entidad porque Mobile Offline ya está habilitado.|
> |**Nombre**:<br />ChangeTrackingNotEnabledForEntity<br />**Hex**:<br />80072491<br />**Número**:<br />-2147015535|La entidad {0} no está habilitada para seguimiento de cambios.|
> |**Nombre**:<br />ChangeTrackingNotEnabledForRelatedEntities<br />**Hex**:<br />80072492<br />**Número**:<br />-2147015534|Los cambios no se pueden recuperar para entidad de intersección {0} ya que ambas entidades no están habilitadas para seguimiento de cambios.|
> |**Nombre**:<br />ChannelAccessProfileRuleAlreadyInDraftState<br />**Hex**:<br />80061115<br />**Número**:<br />-2147086059|No se puede desactivar un borrador de regla de perfil de acceso al canal.|
> |**Nombre**:<br />ChannelPropertyGroupAlreadyExistsWithSameSourceType<br />**Hex**:<br />800608EC<br />**Número**:<br />-2147088148|Ya existe un registro para el tipo de origen especificado. No puede crear otra.|
> |**Nombre**:<br />ChannelPropertyNameInvalid<br />**Hex**:<br />800608F2<br />**Número**:<br />-2147088142|El nombre de la propiedad del canal no es válida. El nombre sólo puede contener '_', caracteres numéricos y alfanuméricos. Elija un nombre diferente e inténtelo de nuevo.|
> |**Nombre**:<br />ChartAreaCategoryMismatch<br />**Hex**:<br />8004E005<br />**Número**:<br />-2147164155|La cantidad de áreas del gráfico debe ser igual a la cantidad de categorías.|
> |**Nombre**:<br />ChartTypeNotSupportedForComparisonChart<br />**Hex**:<br />8004E018<br />**Número**:<br />-2147164136|No se admite este tipo de gráfico para gráficos de comparación.|
> |**Nombre**:<br />ChartTypeNotSupportedForMultipleSeriesChart<br />**Hex**:<br />8004E021<br />**Número**:<br />-2147164127|La serie de tipo de gráficos {0} no es compatible para gráficos de series múltiples.|
> |**Nombre**:<br />CheckPrivilegeGroupForUserOnPremiseError<br />**Hex**:<br />80048401<br />**Número**:<br />-2147187711|Seleccione una cuenta que sea un miembro del grupo de seguridad PrivUserGroup e inténtelo de nuevo.|
> |**Nombre**:<br />CheckPrivilegeGroupForUserOnSplaError<br />**Hex**:<br />80048400<br />**Número**:<br />-2147187712|Seleccione una cuenta de Administrador del sistema de Dynamics 365 que pertenezca a la unidad de negocio raíz y vuelva a intentarlo.|
> |**Nombre**:<br />ChildBusinessDoesNotExist<br />**Hex**:<br />80041d22<br />**Número**:<br />-2147214046|El id. de empresa secundaria no es válido.|
> |**Nombre**:<br />ChildUserDoesNotExist<br />**Hex**:<br />80041d26<br />**Número**:<br />-2147214042|El usuario secundario no es válido.|
> |**Nombre**:<br />ChildWorkflowNotFound<br />**Hex**:<br />8004502F<br />**Número**:<br />-2147200977|Este flujo de trabajo no se puede ejecutar porque uno o varios de los flujos de trabajo secundarios que utiliza no se han publicado o se han eliminado. Compruebe los flujos de trabajo secundarios e intente ejecutar de nuevo este flujo de trabajo.|
> |**Nombre**:<br />ChildWorkflowParameterMismatch<br />**Hex**:<br />80045048<br />**Número**:<br />-2147200952|Este flujo de trabajo no se puede ejecutar porque los argumentos proporcionados por el flujo de trabajo principal no coinciden con los parámetros especificados en el flujo de trabajo secundario vinculado. Compruebe la referencia de flujo de trabajo secundaria en el flujo de trabajo primario y ejecute de nuevo este flujo de trabajo.|
> |**Nombre**:<br />ChunkSizeExceeded<br />**Hex**:<br />80090008<br />**Número**:<br />-2146893816|Tamaño de fragmento de archivo no válido: {0} MB. Tamaño máximo de fragmento admitido: {1} MB.|
> |**Nombre**:<br />CircularDependency<br />**Hex**:<br />80071157<br />**Número**:<br />-2147020457|La operación de la solución falló debido a una dependencia circular con otras soluciones. Compruebe la excepción para obtener más detalles: {0}|
> |**Nombre**:<br />ClientAuthCanceled<br />**Hex**:<br />8004D224<br />**Número**:<br />-2147167708|El usuario canceló la autenticación.|
> |**Nombre**:<br />ClientAuthNoConnectivity<br />**Hex**:<br />8004D226<br />**Número**:<br />-2147167706|No hay ninguna conectividad.|
> |**Nombre**:<br />ClientAuthNoConnectivityOffline<br />**Hex**:<br />8004D225<br />**Número**:<br />-2147167707|No hay ninguna conectividad cuando se ejecuta en modo sin conexión.|
> |**Nombre**:<br />ClientAuthOfflineInvalidCallerId<br />**Hex**:<br />8004D227<br />**Número**:<br />-2147167705|Las llamadas SDK sin conexión deben hacerse en el contexto de un usuario sin conexión.|
> |**Nombre**:<br />ClientAuthSignedOut<br />**Hex**:<br />8004D221<br />**Número**:<br />-2147167711|El usuario ha cerrado sesión.|
> |**Nombre**:<br />ClientAuthSyncIssue<br />**Hex**:<br />8004D223<br />**Número**:<br />-2147167709|Fallo en la sincronización entre procesos.|
> |**Nombre**:<br />ClientServerDateTimeMismatch<br />**Hex**:<br />80044503<br />**Número**:<br />-2147203837|La fecha y hora de su equipo está desincronizada con el servidor en más de 5 minutos.|
> |**Nombre**:<br />ClientServerEmailAddressMismatch<br />**Hex**:<br />80044504<br />**Número**:<br />-2147203836|La dirección de correo electrónico de Outlook y la dirección de correo electrónico del usuario de Dynamics 365 no coinciden.|
> |**Nombre**:<br />ClientUpdateAvailable<br />**Hex**:<br />8004D294<br />**Número**:<br />-2147167596|Hay una actualización disponible para Dynamics 365 for Outlook.|
> |**Nombre**:<br />ClientVersionTooHigh<br />**Hex**:<br />80044501<br />**Número**:<br />-2147203839|Esta versión del cliente de Outlook no es compatible con su organización de Dynamics 365 (versión actual {0} demasiado alta).|
> |**Nombre**:<br />ClientVersionTooLow<br />**Hex**:<br />80044500<br />**Número**:<br />-2147203840|Esta versión del cliente de Outlook no es compatible con su organización de Dynamics 365 (versión actual {0} demasiado baja).|
> |**Nombre**:<br />CloneSolutionException<br />**Hex**:<br />80048539<br />**Número**:<br />-2147187399|Error de la operación de clonación de solución.|
> |**Nombre**:<br />CloneSolutionPatchException<br />**Hex**:<br />80061771<br />**Número**:<br />-2147084431|La revisión '{0}' tiene la misma versión o una versión superior ({1}) que la revisión que se va a instalar.|
> |**Nombre**:<br />CloneTitleTooLong<br />**Hex**:<br />80071112<br />**Número**:<br />-2147020526|Se ha producido un error de validación. La longitud del atributo Name de la entidad mobileofflineprofile superó la longitud máxima permitida de 200.|
> |**Nombre**:<br />CloseActiveChildCaseFirst<br />**Hex**:<br />8003F452<br />**Número**:<br />-2147224494|Cierre el caso secundario activo antes de cerrar el caso principal.|
> |**Nombre**:<br />ColorStripAttributesExceeded<br />**Hex**:<br />80061500<br />**Número**:<br />-2147085056|La sección de la franja de colores no puede tener más de 1 atributo|
> |**Nombre**:<br />ColorStripAttributesInvalid<br />**Hex**:<br />80061502<br />**Número**:<br />-2147085054|La sección de la franja de colores solo puede tener atributos del tipo Dos opciones, Conjunto de opciones y Razón para el estado.|
> |**Nombre**:<br />CombinedManagedPropertyFailure<br />**Hex**:<br />8004F027<br />**Número**:<br />-2147160025|La evaluación del componente actual (nombre{0}, id={1}) en la operación actual ({2}) ha dado error durante al menos una evaluación de propiedades administradas: {3}|
> |**Nombre**:<br />CommandNotSupported<br />**Hex**:<br />80154B52<br />**Número**:<br />-2146088110|El comando no se admite en modo sin conexión.|
> |**Nombre**:<br />CommitFileFailure<br />**Hex**:<br />80072556<br />**Número**:<br />-2147015338|Error al confirmar el archivo. (Tamaño chunkList : {0}, uploadToken: {1}, fileName:{2}, mimeType:{3})|
> |**Nombre**:<br />CommunicationBlocked<br />**Hex**:<br />80044506<br />**Número**:<br />-2147203834|Debido a una excepción de socket se ha bloqueado la comunicación.|
> |**Nombre**:<br />ComponentDefinitionDoesNotExists<br />**Hex**:<br />8004F019<br />**Número**:<br />-2147160039|No existe definición componente para el tipo de componente {0}.|
> |**Nombre**:<br />ConcurrencyVersionMismatch<br />**Hex**:<br />80060882<br />**Número**:<br />-2147088254|La versión de un registro existente no coincide con la propiedad RowVersion proporcionada.|
> |**Nombre**:<br />ConcurrencyVersionNotProvided<br />**Hex**:<br />80060883<br />**Número**:<br />-2147088253|Debe proporcionar la propiedad RowVersion cuando el valor de ConcurrencyBehavior sea IfVersionMatches.|
> |**Nombre**:<br />ConcurrentOperationFailure<br />**Hex**:<br />80071154<br />**Número**:<br />-2147020460|La operación {0} actual generó un error debido a otra operación simultánea que se estaba ejecutando al mismo tiempo. Inténtelo de nuevo más tarde.|
> |**Nombre**:<br />ConditionAttributesNotAnSubsetOfStepAttributes<br />**Hex**:<br />80060436<br />**Número**:<br />-2147089354|Los atributos de la condición no son el subconjunto de los atributos en el paso, para la fase: {0}|
> |**Nombre**:<br />ConditionBranchDoesHaveSetNextStageOnlyChildInXaml<br />**Hex**:<br />80060434<br />**Número**:<br />-2147089356|La condición de rama puede contener solo SetNextStage como secundario.|
> |**Nombre**:<br />ConditionStepCountInXamlExceedsMaxAllowed<br />**Hex**:<br />80060435<br />**Número**:<br />-2147089355|{0} no puede tener más de una {1}.|
> |**Nombre**:<br />ConfigDBCannotDeleteDefaultOrganization<br />**Hex**:<br />8004D23B<br />**Número**:<br />-2147167685|La organización predeterminada {0} no se puede eliminar de la base de datos MSCRM_CONFIG.|
> |**Nombre**:<br />ConfigDBCannotDeleteObjectDueState<br />**Hex**:<br />8004D232<br />**Número**:<br />-2147167694|No se puede eliminar '{0}' con un valor = ({1}) en este estado = ({2}) de la base de datos MSCRM_CONFIG|
> |**Nombre**:<br />ConfigDBCannotUpdateObjectDueState<br />**Hex**:<br />8004D237<br />**Número**:<br />-2147167689|No se puede actualizar '{0}' con un valor = ({1}) en este estado = ({2}) de la base de datos MSCRM_CONFIG|
> |**Nombre**:<br />ConfigDBCascadeDeleteNotAllowDelete<br />**Hex**:<br />8004D233<br />**Número**:<br />-2147167693|No se puede eliminar '{0}' con un valor = ({1}) debido a referencias secundarias '{2}' de base de datos MSCRM_CONFIG|
> |**Nombre**:<br />ConfigDBDuplicateRecord<br />**Hex**:<br />8004D231<br />**Número**:<br />-2147167695|Duplicado '{0}' con un valor = ({1}) existe en la base de datos MSCRM_CONFIG|
> |**Nombre**:<br />ConfigDBObjectDoesNotExist<br />**Hex**:<br />8004D230<br />**Número**:<br />-2147167696|'{0}' con un valor = ({1}) no existe en la base de datos MSCRM_CONFIG|
> |**Nombre**:<br />ConfigMissingDescription<br />**Hex**:<br />80044197<br />**Número**:<br />-2147204713|Se debe especificar una descripción.|
> |**Nombre**:<br />ConfigNullPrimaryKey<br />**Hex**:<br />80044196<br />**Número**:<br />-2147204714|La clave principal no puede ser nula.|
> |**Nombre**:<br />ConfigurationPageNotValidForSolution<br />**Hex**:<br />8004701D<br />**Número**:<br />-2147192803|La página de configuración de la solución debe existir dentro de la solución que representa.|
> |**Nombre**:<br />ConfigureClaimsBeforeIfd<br />**Hex**:<br />8004D266<br />**Número**:<br />-2147167642|Debe configurar la autenticación basada en notificaciones antes de que pueda configurar una implementación con conexión a Internet.|
> |**Nombre**:<br />ConfiguredUserIsDifferentThanSuppliedUser<br />**Hex**:<br />80044508<br />**Número**:<br />-2147203832|El usuario configurado es diferente del usuario proporcionado.|
> |**Nombre**:<br />ConflictForOverriddenPropertiesEncountered<br />**Hex**:<br />80081010<br />**Número**:<br />-2146955248|Este registro no se puede publicar. Una de las propiedades que se ha cambiado para este registro está en conflicto con la versión hereda. Quite la propiedad en conflicto e inténtelo de nuevo.|
> |**Nombre**:<br />ConflictingProvisionTypes<br />**Hex**:<br />8004B02C<br />**Número**:<br />-2147176404|El componente servicio {0} tiene tipos de aprovisionamiento en conflicto.|
> |**Nombre**:<br />ConnectionCannotBeEnabledOnThisEntity<br />**Hex**:<br />80048214<br />**Número**:<br />-2147188204|No se pueden habilitar las conexiones en esta entidad {0} con el id {1}.|
> |**Nombre**:<br />ConnectionExists<br />**Hex**:<br />80048208<br />**Número**:<br />-2147188216|La conexión ya existe.|
> |**Nombre**:<br />ConnectionInvalidStartEndDate<br />**Hex**:<br />80048209<br />**Número**:<br />-2147188215|La fecha de inicio/finalización no es válida.|
> |**Nombre**:<br />ConnectionNotSupported<br />**Hex**:<br />80048213<br />**Número**:<br />-2147188205|El registro seleccionado no admite conexiones. No puede agregar la conexión.|
> |**Nombre**:<br />ConnectionObjectsMissing<br />**Hex**:<br />80048210<br />**Número**:<br />-2147188208|Faltan los dos objetos que se desea conectar.|
> |**Nombre**:<br />ConnectionRoleNotValidForObjectType<br />**Hex**:<br />80048215<br />**Número**:<br />-2147188203|El registro de tipo {0} (Código de tipo de objeto {1}) no está definido para su uso con el rol de conexión {2} con id {3}.|
> |**Nombre**:<br />ConnectionTimeOut<br />**Hex**:<br />80071024<br />**Número**:<br />-2147020764|No se pueden copiar los documentos porque se superó el tiempo de espera de la conexión de red. Vuelva a intentarlo más tarde o póngase en contacto con el administrador del sistema.|
> |**Nombre**:<br />ConnectorLogicalNameAlreadyExists<br />**Hex**:<br />80072606<br />**Número**:<br />-2147015162|El nombre lógico del conector '{0}' ya existe en la organización.|
> |**Nombre**:<br />ConnectorNotEnabled<br />**Hex**:<br />80072600<br />**Número**:<br />-2147015168|La creación y la edición de Conector no están habilitadas.|
> |**Nombre**:<br />ContactDoesNotExist<br />**Hex**:<br />80040503<br />**Número**:<br />-2147220221|El contacto no existe.|
> |**Nombre**:<br />ContactLoopBeingCreated<br />**Hex**:<br />8004050a<br />**Número**:<br />-2147220214|La creación de esta asociación jerárquica crearía un bucle en la jerarquía de contactos.|
> |**Nombre**:<br />ContactLoopExists<br />**Hex**:<br />80040509<br />**Número**:<br />-2147220215|Existe un bucle en la jerarquía de los contactos.|
> |**Nombre**:<br />ContextIsNull<br />**Hex**:<br />80060445<br />**Número**:<br />-2147089339|Error al crear o actualizar proceso de negocios: contexto no puede ser nulo.|
> |**Nombre**:<br />ContractDetailDiscountAmount<br />**Hex**:<br />80044413<br />**Número**:<br />-2147204077|El tipo de descuento del contrato no admite descuentos de 'porcentaje'.|
> |**Nombre**:<br />ContractDetailDiscountAmountAndPercent<br />**Hex**:<br />80044414<br />**Número**:<br />-2147204076|No se puede establecer 'importe' y 'porcentaje'.|
> |**Nombre**:<br />ContractDetailDiscountPercent<br />**Hex**:<br />80044412<br />**Número**:<br />-2147204078|El tipo de descuento del contrato no admite descuentos de 'importe'.|
> |**Nombre**:<br />ContractInvalidAllotmentTypeCode<br />**Hex**:<br />80043205<br />**Número**:<br />-2147208699|El código de tipo de cobertura no es válido.|
> |**Nombre**:<br />ContractInvalidBillToAddress<br />**Hex**:<br />8004320f<br />**Número**:<br />-2147208689|La dirección de facturación del contrato no es válida.|
> |**Nombre**:<br />ContractInvalidBillToCustomer<br />**Hex**:<br />80043210<br />**Número**:<br />-2147208688|El cliente de facturación del contrato no es válido.|
> |**Nombre**:<br />ContractInvalidContract<br />**Hex**:<br />80043213<br />**Número**:<br />-2147208685|El contrato no es válido.|
> |**Nombre**:<br />ContractInvalidContractTemplate<br />**Hex**:<br />80043211<br />**Número**:<br />-2147208687|La plantilla de contrato no es válida.|
> |**Nombre**:<br />ContractInvalidCustomer<br />**Hex**:<br />8004320d<br />**Número**:<br />-2147208691|El cliente del contrato no es válido.|
> |**Nombre**:<br />ContractInvalidDatesForRenew<br />**Hex**:<br />80043218<br />**Número**:<br />-2147208680|La fecha de inicio o de finalización de este contrato renovado no puede coincidir con ningún otro contrato facturado o activo con el mismo número de contrato.|
> |**Nombre**:<br />ContractInvalidDiscount<br />**Hex**:<br />80044193<br />**Número**:<br />-2147204717|El descuento no puede ser superior al precio total.|
> |**Nombre**:<br />ContractInvalidPrice<br />**Hex**:<br />80043215<br />**Número**:<br />-2147208683|El precio no es válido.|
> |**Nombre**:<br />ContractInvalidServiceAddress<br />**Hex**:<br />8004320e<br />**Número**:<br />-2147208690|La dirección de servicio del contrato no es válida.|
> |**Nombre**:<br />ContractInvalidStartEndDate<br />**Hex**:<br />80043202<br />**Número**:<br />-2147208702|La fecha de inicio/finalización o la fecha de inicio/finalización de facturación no es válida.|
> |**Nombre**:<br />ContractInvalidState<br />**Hex**:<br />80043203<br />**Número**:<br />-2147208701|El estado del contrato no es válido.|
> |**Nombre**:<br />ContractLineInvalidState<br />**Hex**:<br />80043204<br />**Número**:<br />-2147208700|El estado del elemento de línea de contrato no es válido.|
> |**Nombre**:<br />ContractNoLineItems<br />**Hex**:<br />8004320c<br />**Número**:<br />-2147208692|No hay ningún elemento de línea de contrato para este contrato.|
> |**Nombre**:<br />ContractTemplateDoesNotExist<br />**Hex**:<br />80043206<br />**Número**:<br />-2147208698|La plantilla de contrato no existe.|
> |**Nombre**:<br />ContractTemplateNoAbbreviation<br />**Hex**:<br />8004320b<br />**Número**:<br />-2147208693|Abreviatura no puede ser NULO.|
> |**Nombre**:<br />ControlIdIsNotUnique<br />**Hex**:<br />80060411<br />**Número**:<br />-2147089391|Id. de control {0} en el Xaml no es único|
> |**Nombre**:<br />ControlIdIsNullOrEmpty<br />**Hex**:<br />80072344<br />**Número**:<br />-2147015868|El Id. de control no puede ser nulo o estar vacío.|
> |**Nombre**:<br />ConvertFetchDataSetError<br />**Hex**:<br />8004832e<br />**Número**:<br />-2147187922|Se ha producido un error inesperado al procesar el conjunto de datos Fetch.|
> |**Nombre**:<br />ConvertReportToCrmError<br />**Hex**:<br />8004832d<br />**Número**:<br />-2147187923|Se ha producido un error inesperado al convertir el informe proporcionado al formato de Dynamics 365.|
> |**Nombre**:<br />ConvertRuleActivateDeactivateByNonOwner<br />**Hex**:<br />8004F886<br />**Número**:<br />-2147157882|Solo el propietario puede activar o desactivar este conjunto de reglas de conversión.|
> |**Nombre**:<br />ConvertRuleAlreadyActive<br />**Hex**:<br />80060731<br />**Número**:<br />-2147088591|La ConvertRule seleccionada ya está en estado Activo. Seleccione otro registro e inténtelo de nuevo.|
> |**Nombre**:<br />ConvertRuleAlreadyInDraftState<br />**Hex**:<br />80060732<br />**Número**:<br />-2147088590|La ConvertRule seleccionada ya está en estado Borrador. Seleccione otro registro e inténtelo de nuevo.|
> |**Nombre**:<br />ConvertRuleInvalidAutoResponseSettings<br />**Hex**:<br />8004F879<br />**Número**:<br />-2147157895|Seleccione una plantilla de correo electrónico para una respuesta automática o defina la opción de respuesta automática en No.|
> |**Nombre**:<br />ConvertRulePermissionToPerformAction<br />**Hex**:<br />80060733<br />**Número**:<br />-2147088589|No tiene los permisos necesarios sobre sobre ConvertRules y los procesos para realizar esta acción.|
> |**Nombre**:<br />ConvertRuleQueueIdMissingForEmailSource<br />**Hex**:<br />8004F896<br />**Número**:<br />-2147157866|Se requiere el valor de cola. Especifique un valor par ala cola.|
> |**Nombre**:<br />ConvertRuleResponseTemplateValidity<br />**Hex**:<br />80060730<br />**Número**:<br />-2147088592|Seleccione una plantilla de caso o global.|
> |**Nombre**:<br />CopyGenericError<br />**Hex**:<br />80071027<br />**Número**:<br />-2147020761|Se ha producido un error al copiar archivos. Vuelva a intentarlo más tarde. Si el problema continúa, póngase en contacto con el administrador del sistema.|
> |**Nombre**:<br />CopyNotAllowedForInternetMarketing<br />**Hex**:<br />80048474<br />**Número**:<br />-2147187596|No se permite la duplicación de las campañas que tienen actividades de campañas de Marketing de Internet|
> |**Nombre**:<br />CorruptedHiddensheetData<br />**Hex**:<br />800609B7<br />**Número**:<br />-2147087945|Los datos de una hoja oculta está dañados.|
> |**Nombre**:<br />CouldNotDecryptOAuthToken<br />**Hex**:<br />8005F110<br />**Número**:<br />-2147094256|No se ha podido descifrar el token OAuth de Yammer. Pruebe a configurar Yammer otra vez.|
> |**Nombre**:<br />CouldNotFindQueueItemInQueue<br />**Hex**:<br />80040524<br />**Número**:<br />-2147220188|No se encontró un elemento de cola asociado con el objetivo en el SourceQueueId especificado. El SourceQueueId o destino no es válido o no existe el elemento de cola.|
> |**Nombre**:<br />CouldNotObtainLockOnResource<br />**Hex**:<br />80044339<br />**Número**:<br />-2147204295|No se puede obtener el bloqueo de recursos de la base de datos. Para obtener más información, consulte http://docs.microsoft.com/dynamics365/customer-engagement/customize/best-practices-workflow-processes#limit-the-number-of-workflows-that-update-the-same-entity|
> |**Nombre**:<br />CouldNotReadAccessToken<br />**Hex**:<br />8005F105<br />**Número**:<br />-2147094267|El sistema no puede leer el token de acceso a Yammer del usuario aunque pasó un código no vacío.|
> |**Nombre**:<br />CouldNotSetLocationTypeToOneNote<br />**Hex**:<br />80060905<br />**Número**:<br />-2147088123|No se pudo establecer el tipo de ubicación de la ubicación de documento en OneNote.|
> |**Nombre**:<br />CountSpecifiedWithoutOrder<br />**Hex**:<br />8004E01F<br />**Número**:<br />-2147164129|La descripción de datos para la visualización no es válida ya que no especifica un nodo de pedido para el atributo de recuento.|
> |**Nombre**:<br />CreatePropertyError<br />**Hex**:<br />8004F889<br />**Número**:<br />-2147157879|Error al guardar la propiedad {0}.|
> |**Nombre**:<br />CreatePropertyInstanceError<br />**Hex**:<br />8004F890<br />**Número**:<br />-2147157872|Error al guardar la instancia de propiedad {0}.|
> |**Nombre**:<br />CreatePublishedWorkflowDefinitionWorkflowDependency<br />**Hex**:<br />8004500A<br />**Número**:<br />-2147201014|No se puede crear una dependencia de flujo de trabajo para una definición de un flujo de trabajo publicada.|
> |**Nombre**:<br />CreateRecurrenceRuleFailed<br />**Hex**:<br />8004E101<br />**Número**:<br />-2147163903|No se puede crear la regla de periodicidad.|
> |**Nombre**:<br />CreateWorkflowActivationWorkflowDependency<br />**Hex**:<br />80045009<br />**Número**:<br />-2147201015|No se puede crear una dependencia de flujo de trabajo asociada con la activación de un flujo de trabajo.|
> |**Nombre**:<br />CreateWorkflowDependencyForPublishedTemplate<br />**Hex**:<br />80045019<br />**Número**:<br />-2147200999|No se puede crear una dependencia de flujo de trabajo para una plantilla de flujo de trabajo publicada.|
> |**Nombre**:<br />CrmConstraintEvaluationError<br />**Hex**:<br />80040261<br />**Número**:<br />-2147220895|Ocurrió un error de evaluación de restricción de CRM.|
> |**Nombre**:<br />CrmConstraintParsingError<br />**Hex**:<br />80040262<br />**Número**:<br />-2147220894|Ocurrió un error de análisis de restricción de CRM.|
> |**Nombre**:<br />CrmExpressionBodyParsingError<br />**Hex**:<br />8004025e<br />**Número**:<br />-2147220898|Se produjo un error de análisis de expresión de cuerpo de CRM.|
> |**Nombre**:<br />CrmExpressionEvaluationError<br />**Hex**:<br />80040260<br />**Número**:<br />-2147220896|Ocurrió un error de evaluación de expresión de CRM.|
> |**Nombre**:<br />CrmExpressionParametersParsingError<br />**Hex**:<br />8004025f<br />**Número**:<br />-2147220897|Se produjo un error de análisis de expresión de parámetros de CRM.|
> |**Nombre**:<br />CrmExpressionParsingError<br />**Hex**:<br />8004025d<br />**Número**:<br />-2147220899|Se produjo un error de análisis de expresión de CRM.|
> |**Nombre**:<br />CRMGlobalMetadataVersionMismatch<br />**Hex**:<br />80072494<br />**Número**:<br />-2147015532|No coinciden en la versión de metadatos globales de CRM al recuperar datos para la entidad: '{0}'. Versión de metadatos globales antes de recuperar datos: '{1}'. Versión de metadatos globales después de recuperar datos: '{2}'|
> |**Nombre**:<br />CrmHttpError<br />**Hex**:<br />8006088A<br />**Número**:<br />-2147088246|Error en Wep Api en Dynamics 365.|
> |**Nombre**:<br />CrmImpersonationError<br />**Hex**:<br />80040245<br />**Número**:<br />-2147220923|Error en CRM AutoReimpersonator.|
> |**Nombre**:<br />CrmLicensingError<br />**Hex**:<br />80050300<br />**Número**:<br />-2147155200|Se produjo un error durante la verificación de licencia.|
> |**Nombre**:<br />CrmLicensingNoServicePlan<br />**Hex**:<br />80050301<br />**Número**:<br />-2147155199|La aplicación requiere una licencia. Póngase en contacto con el administrador.Identificador de usuario llamante={0} no tiene ninguna licencia para leer el appmodule de la entidad uniqueName={1} con Id={2} del editor={3}. Se requiere una licencia con uno de los planes de servicio (cuenta={4}): {5}.|
> |**Nombre**:<br />CrmLicensingNoUserPass<br />**Hex**:<br />80050302<br />**Número**:<br />-2147155198|La aplicación requiere una licencia y la organización no tiene pases de usuario. Póngase en contacto con el administrador.Identificador de usuario llamante={0} no tiene ninguna licencia para leer el appmodule de la entidad uniqueName={1} con Id={2} del editor={3}.|
> |**Nombre**:<br />CrmLiveAddOnAddLicenseLimitReached<br />**Hex**:<br />8004B056<br />**Número**:<br />-2147176362|La suscripción ha alcanzado el número máximo de licencias de usuario disponibles.  Para obtener licencias adicionales, póngase en contacto con nuestra organización de ventas en 1-877-Dynamics 365-CHOICE (276-2464).|
> |**Nombre**:<br />CrmLiveAddOnAddStorageLimitReached<br />**Hex**:<br />8004B057<br />**Número**:<br />-2147176361|Su consumo de almacenamiento ha almacenado el límite máximo de almacenamiento asignado a este entorno. Los entornos de prueba se asignan con recursos limitados. Si no usa un entorno de prueba, póngase en contacto con soporte.|
> |**Nombre**:<br />CrmLiveAddOnDataChanged<br />**Hex**:<br />8004B05C<br />**Número**:<br />-2147176356|Debido a los últimos cambios realizados en su cuenta, estos cambios no se pueden realizar en este momento.   Cierre a este asistente e inténtelo de nuevo.  Si el problema persiste, póngase en contacto con nuestra organización de ventas en 1-877-Dynamics 365-CHOICE (276-2464).|
> |**Nombre**:<br />CrmLiveAddOnOrgInNoUpdateMode<br />**Hex**:<br />8004B059<br />**Número**:<br />-2147176359|No se puede procesar los cambios en este momento. La organización se está actualizando.  No se han realizado cambios en su cuenta.  Cierre a este asistente e inténtelo de nuevo.  Si el problema persiste, póngase en contacto con nuestra organización de ventas en 1-877-Dynamics 365-CHOICE (276-2464).|
> |**Nombre**:<br />CrmLiveAddOnRemoveStorageLimitReached<br />**Hex**:<br />8004B058<br />**Número**:<br />-2147176360|La organización tiene la cantidad de almacenamiento mínima permitida.  Puede quitar solo almacenamiento que se haya agregado a su organización y que no se esté utilizando.|
> |**Nombre**:<br />CrmLiveAddOnUnexpectedError<br />**Hex**:<br />8004B055<br />**Número**:<br />-2147176363|Se ha producido un error al ponerse en contacto con el sistema de facturación.  No se puede procesar la solicitud en este momento.  No se han realizado cambios en su cuenta.  Cierre a este asistente e inténtelo de nuevo.  Si el problema persiste, póngase en contacto con nuestra organización de ventas en 1-877-Dynamics 365-CHOICE (276-2464).|
> |**Nombre**:<br />CrmLiveCannotFindExternalMessageProvider<br />**Hex**:<br />8004B051<br />**Número**:<br />-2147176367|No se encuentra proveedor externo de mensajesde para el tipo de elemento de cola de: {0}.|
> |**Nombre**:<br />CrmLiveDnsDomainAlreadyExists<br />**Hex**:<br />8004B048<br />**Número**:<br />-2147176376|El dominio ya existe en la tabla DNS.|
> |**Nombre**:<br />CrmLiveDnsDomainNotFound<br />**Hex**:<br />8004B047<br />**Número**:<br />-2147176377|No se encontró el dominio en la tabla DNS.|
> |**Nombre**:<br />CrmLiveDuplicateWindowsLiveId<br />**Hex**:<br />8004B046<br />**Número**:<br />-2147176378|Ya existe un usuario con este nombre de usuario.|
> |**Nombre**:<br />CrmLiveExecuteCustomCodeDisabled<br />**Hex**:<br />8004B063<br />**Número**:<br />-2147176349|La ejecución de la característica de código personalizado está deshabilitado para la organización.|
> |**Nombre**:<br />CrmLiveGenericError<br />**Hex**:<br />8004B000<br />**Número**:<br />-2147176448|Se ha producido un error al procesar la solicitud.|
> |**Nombre**:<br />CrmLiveInternalProvisioningError<br />**Hex**:<br />8004B003<br />**Número**:<br />-2147176445|Se ha producido un error iniesperado en el sistema de aprovisionamiento.|
> |**Nombre**:<br />CrmLiveInvalidEmail<br />**Hex**:<br />8004B05D<br />**Número**:<br />-2147176355|Dirección de correo electrónico introducida no válida.|
> |**Nombre**:<br />CrmLiveInvalidExternalMessageData<br />**Hex**:<br />8004B052<br />**Número**:<br />-2147176366|Los datos de mensajes externos tienen algunos datos no válidos.  Datos: {0} Mensaje externo: {1}|
> |**Nombre**:<br />CrmLiveInvalidInvoicingAccountNumber<br />**Hex**:<br />8004B05B<br />**Número**:<br />-2147176357|Este número de cuenta de facturación no es válido porque contiene un carácter no válido.|
> |**Nombre**:<br />CrmLiveInvalidPhone<br />**Hex**:<br />8004B05E<br />**Número**:<br />-2147176354|El número de teléfono introducido no es válido.|
> |**Nombre**:<br />CrmLiveInvalidQueueItemSchedule<br />**Hex**:<br />8004B039<br />**Número**:<br />-2147176391|El elemento de cola tiene una programación no válida de hora de inicio {0} y la hora de finalización {1}.|
> |**Nombre**:<br />CrmLiveInvalidSetupParameter<br />**Hex**:<br />8004B005<br />**Número**:<br />-2147176443|El parámetro de configuración de Dynamics 365 Online es incorrecto o no se ha especificado.|
> |**Nombre**:<br />CrmLiveInvalidTaxId<br />**Hex**:<br />8004B064<br />**Número**:<br />-2147176348|TaxId especificado no válido.|
> |**Nombre**:<br />CrmLiveInvalidZipCode<br />**Hex**:<br />8004B05F<br />**Número**:<br />-2147176353|Código zip introducido no válido.|
> |**Nombre**:<br />CrmLiveInvoicingAccountIdMissing<br />**Hex**:<br />8004B045<br />**Número**:<br />-2147176379|El número de cuenta (Id. de SAP) de facturación no puede estar vacío para una facturación sku.|
> |**Nombre**:<br />CrmLiveMissingActiveDirectoryGroup<br />**Hex**:<br />8004B002<br />**Número**:<br />-2147176446|El grupo de Active Directory especificado no existe.|
> |**Nombre**:<br />CrmLiveMissingServerRolesInScaleGroup<br />**Hex**:<br />8004B007<br />**Número**:<br />-2147176441|Al scalegroup le faltan algunos roles de servidor necesarios. 1 servidor de testigo y 2 servidores Sql son necesarios para aprovisionamiento.|
> |**Nombre**:<br />CrmLiveMonitoringOrganizationExistsInScaleGroup<br />**Hex**:<br />8004B026<br />**Número**:<br />-2147176410|Solo se permite una organización de supervisión en un scalegroup.|
> |**Nombre**:<br />CrmLiveMultipleWitnessServersInScaleGroup<br />**Hex**:<br />8004B006<br />**Número**:<br />-2147176442|El ScaleGroup tiene varios servidores testigo especificados. Debe haber solo 1 servidor testigo en un grupo de escalas.|
> |**Nombre**:<br />CrmLiveOrganizationDeleteFailed<br />**Hex**:<br />8004B02E<br />**Número**:<br />-2147176402|Se ha producido un error al eliminar la organización.|
> |**Nombre**:<br />CrmLiveOrganizationDetailsNotFound<br />**Hex**:<br />8004B030<br />**Número**:<br />-2147176400|No se pueden buscar los detalles de la organización.|
> |**Nombre**:<br />CrmLiveOrganizationDisableFailed<br />**Hex**:<br />8004B054<br />**Número**:<br />-2147176364|Fallo de deshabilitación de organización.|
> |**Nombre**:<br />CrmLiveOrganizationEnableFailed<br />**Hex**:<br />8004B053<br />**Número**:<br />-2147176365|Fallo de habilitación de organización.|
> |**Nombre**:<br />CrmLiveOrganizationFriendlyNameTooLong<br />**Hex**:<br />8004B032<br />**Número**:<br />-2147176398|El nombre de la organización proporcionado es demasiado largo.|
> |**Nombre**:<br />CrmLiveOrganizationFriendlyNameTooShort<br />**Hex**:<br />8004B031<br />**Número**:<br />-2147176399|El nombre de la organización proporcionado es demasiado corto.|
> |**Nombre**:<br />CrmLiveOrganizationProvisioningFailed<br />**Hex**:<br />8004B001<br />**Número**:<br />-2147176447|Se ha producido un error al aprovisionar la organización.|
> |**Nombre**:<br />CrmLiveOrganizationUniqueNameInvalid<br />**Hex**:<br />8004B035<br />**Número**:<br />-2147176395|El nombre único especificado no es válido.|
> |**Nombre**:<br />CrmLiveOrganizationUniqueNameReserved<br />**Hex**:<br />8004B036<br />**Número**:<br />-2147176394|El nombre único ya se ha reservado.|
> |**Nombre**:<br />CrmLiveOrganizationUniqueNameTooLong<br />**Hex**:<br />8004B034<br />**Número**:<br />-2147176396|El nombre único proporcionado es demasiado largo.|
> |**Nombre**:<br />CrmLiveOrganizationUniqueNameTooShort<br />**Hex**:<br />8004B033<br />**Número**:<br />-2147176397|El nombre único proporcionado es demasiado corto.|
> |**Nombre**:<br />CrmLiveOrganizationUpgradeFailed<br />**Hex**:<br />8004B014<br />**Número**:<br />-2147176428|Error en la actualización de la organización de CRM.|
> |**Nombre**:<br />CrmLiveQueueItemDoesNotExist<br />**Hex**:<br />8004B004<br />**Número**:<br />-2147176444|El elemento de cola especificado no existe en la cola. Es posible que se haya eliminado o su identificador haya sido especificado correctamente|
> |**Nombre**:<br />CrmLiveQueueItemTimeInPast<br />**Hex**:<br />8004B040<br />**Número**:<br />-2147176384|Un elemento de cola no se puede programar para comenzar o terminar en el pasado.|
> |**Nombre**:<br />CrmLiveRegisterCustomCodeDisabled<br />**Hex**:<br />8004B062<br />**Número**:<br />-2147176350|El registro de la característica de código personalizado está deshabilitado para la organización.|
> |**Nombre**:<br />CrmLiveServerCannotHaveWitnessAndDataServerRoles<br />**Hex**:<br />8004B008<br />**Número**:<br />-2147176440|Un servidor no puede tener ambos, rol de servidor testigo y rol de servidor de datos.|
> |**Nombre**:<br />CrmLiveSupportOrganizationExistsInScaleGroup<br />**Hex**:<br />8004B025<br />**Número**:<br />-2147176411|Solo se permite una organización de soporte en un scalegroup.|
> |**Nombre**:<br />CrmLiveUnknownCategory<br />**Hex**:<br />8004B05A<br />**Número**:<br />-2147176358|Esta categoría especificada no es válida.|
> |**Nombre**:<br />CrmLiveUnknownSku<br />**Hex**:<br />8004B041<br />**Número**:<br />-2147176383|Este sku especificado no es válido.|
> |**Nombre**:<br />CrmMalformedExpressionError<br />**Hex**:<br />8004025c<br />**Número**:<br />-2147220900|Ocurrió un error de expresión incorecta de CRM.|
> |**Nombre**:<br />CrmQueryExpressionNotInitialized<br />**Hex**:<br />8004024d<br />**Número**:<br />-2147220915|No se inicializó la QueryExpression. Utilice el constructor que toma el nombre de la entidad para crear una instancia correctamente inicializada|
> |**Nombre**:<br />CrmSecurityError<br />**Hex**:<br />80040256<br />**Número**:<br />-2147220906|Error en CrmSecurity.|
> |**Nombre**:<br />CrmSQLCharLengthTooLong<br />**Hex**:<br />80073001<br />**Número**:<br />-2147012607|Se ha producido un error de validación. Un valor de cadena proporcionado es demasiado largo.|
> |**Nombre**:<br />CrmSqlGovernorDatabaseRequestDenied<br />**Hex**:<br />8004A001<br />**Número**:<br />-2147180543|El servidor está ocupado y no se ha completado la solicitud. Vuelva a intentarlo más tarde.|
> |**Nombre**:<br />CrmSQLNetworkingError<br />**Hex**:<br />80073000<br />**Número**:<br />-2147012608|Un error de conexión de red causó el error de esta operación. Inténtelo de nuevo.|
> |**Nombre**:<br />CrmSQLUniqueIndexOrConstraintViolation<br />**Hex**:<br />80073002<br />**Número**:<br />-2147012606|La operación intentada para insertar un valor duplicado para un atributo con una restricción exclusiva.|
> |**Nombre**:<br />CRMUserDoesNotExist<br />**Hex**:<br />80040354<br />**Número**:<br />-2147220652|No existe ningún usuario de Microsoft Dynamics 365 con el nombre de dominio y el Id. de usuario especificados|
> |**Nombre**:<br />CrossEntityRelationshipInvalidOperation<br />**Hex**:<br />80092006<br />**Número**:<br />-2146885626|Transición de fase entre entidades no válida. La relación especificada no se puede modificar.|
> |**Nombre**:<br />CurrencyCannotBeNullDueToNonNullMoneyFields<br />**Hex**:<br />80048cfb<br />**Número**:<br />-2147185413|La divisa no puede ser nula.|
> |**Nombre**:<br />CurrencyFieldMissing<br />**Hex**:<br />8004E026<br />**Número**:<br />-2147164122|La divisa de registro es obligatoria para calcular el campo consolidado del tipo de divisa. Indique una divisa e inténtelo de nuevo.|
> |**Nombre**:<br />CurrencyNotEqual<br />**Hex**:<br />80048cea<br />**Número**:<br />-2147185430|La divisa de {0} no coincide con la divisa de {1}.|
> |**Nombre**:<br />CurrencyRequiredForDiscountTypeAmount<br />**Hex**:<br />80048cf7<br />**Número**:<br />-2147185417|La divisa no puede ser nula para el importe de tipo de descuento.|
> |**Nombre**:<br />CurrentFormEntityIsNull<br />**Hex**:<br />80060371<br />**Número**:<br />-2147089551|La entidad del formulario actual no puede ser NULL|
> |**Nombre**:<br />CustomActionMustBeMarked<br />**Hex**:<br />80060381<br />**Número**:<br />-2147089535|La acción personalizada se debe marcar 'Como un paso de acción Flujo de proceso de negocio' para usar como paso de acción de BPF.|
> |**Nombre**:<br />CustomActivityCannotBeMailMergeEnabled<br />**Hex**:<br />8004F124<br />**Número**:<br />-2147159772|Una entidad personalizada ya definida como una actividad no puede tener MailMerge habilitado.|
> |**Nombre**:<br />CustomActivityInvalid<br />**Hex**:<br />8004501D<br />**Número**:<br />-2147200995|Estado de actividad personalizada no válido.|
> |**Nombre**:<br />CustomActivityMustHaveOfflineAvailability<br />**Hex**:<br />8004F122<br />**Número**:<br />-2147159774|Una entidad personalizada que se define como actividad debe tener disponibilidad sin conexión.|
> |**Nombre**:<br />CustomControlsDependentPropertyConfiguration<br />**Hex**:<br />80160002<br />**Número**:<br />-2146041854|La propiedad "{0}" solo se puede configurar después de que se haya asignado un valor en la propiedad "{1}".|
> |**Nombre**:<br />CustomControlsImportError<br />**Hex**:<br />80160000<br />**Número**:<br />-2146041856|Se ha producido un error al importar controles personalizados. Intente importar de nuevo esta solución.|
> |**Nombre**:<br />CustomControlsPropertySetConfiguration<br />**Hex**:<br />80160003<br />**Número**:<br />-2146041853|La propiedad "{0}" solo se puede configurar después de asignar el valor al conjunto de datos correspondiente "{1}".|
> |**Nombre**:<br />CustomerIsInactive<br />**Hex**:<br />80040517<br />**Número**:<br />-2147220201|Un cliente inactivo no se puede establecer como primario de un objeto.|
> |**Nombre**:<br />CustomerOpportunityRoleExists<br />**Hex**:<br />80048202<br />**Número**:<br />-2147188222|Existe el rol de oportunidad de cliente.|
> |**Nombre**:<br />CustomerRelationshipCannotBeDeleted<br />**Hex**:<br />8004847d<br />**Número**:<br />-2147187587|Esta relación {1} la requiere el {0} atributo y no se puede eliminar. Para eliminar esta relación, elimine primero el atributo de búsqueda.|
> |**Nombre**:<br />CustomerRelationshipExists<br />**Hex**:<br />80048201<br />**Número**:<br />-2147188223|Las relaciones con el cliente ya existen. CustomerRelationshipId: {0}, CustomerId: {1}, CustomerIdType: {2}, PartnerId: {3}, PartnerIdType: {4}, CustomerRoleId: {5}, PartnerRoleId: {6}, UniqueDscId: {7}|
> |**Nombre**:<br />CustomImageAttributeOnlyAllowedOnCustomEntity<br />**Hex**:<br />80048531<br />**Número**:<br />-2147187407|Un atributo de imagen personalizado solo se puede agregar a una entidad personalizada.|
> |**Nombre**:<br />CustomOperationNotActivated<br />**Hex**:<br />80045052<br />**Número**:<br />-2147200942|La acción de proceso asociada a este proceso no está activada.|
> |**Nombre**:<br />CustomParentingSystemNotSupported<br />**Hex**:<br />80047102<br />**Número**:<br />-2147192574|Una entidad personalizada no puede tener una relación jerárquica con una entidad del sistema|
> |**Nombre**:<br />CustomPeriodGoalHavingExtraInfo<br />**Hex**:<br />80044904<br />**Número**:<br />-2147202812|El año fiscal y el atributo de período fiscal deben dejarse en blanco para un objetivo de tipo de período personalizado.|
> |**Nombre**:<br />CustomPeriodGoalMissingInfo<br />**Hex**:<br />80044907<br />**Número**:<br />-2147202809|Para un objetivo de tipo de período personalizado, los atributos de goalstartdate y goalenddate deben contener datos.|
> |**Nombre**:<br />CustomReflexiveRelationshipNotAllowedForEntity<br />**Hex**:<br />8004432C<br />**Número**:<br />-2147204308|Esta entidad no es válida para una relación reflexiva personalizada|
> |**Nombre**:<br />CustomWorkflowActivitiesNotSupported<br />**Hex**:<br />80045051<br />**Número**:<br />-2147200943|No están habilitadas actividades personalizadas de flujo de trabajo.|
> |**Nombre**:<br />CyclicalRelationship<br />**Hex**:<br />80047004<br />**Número**:<br />-2147192828|La relación especificada dará como resultado un ciclo.|
> |**Nombre**:<br />CyclicDependency<br />**Hex**:<br />80071156<br />**Número**:<br />-2147020458|Dependencia de componentes cíclico detectada Compruebe la excepción para obtener más detalles. Corrija las dependencias no válidas y pruebe la operación una vez más. Detalles: {0}|
> |**Nombre**:<br />CyclicReferencesNotSupported<br />**Hex**:<br />8004417F<br />**Número**:<br />-2147204737|La entrada contiene una referencia cíclica, que no se admite.|
> |**Nombre**:<br />DatabaseCallsBlockedFailure<br />**Hex**:<br />80072401<br />**Número**:<br />-2147015679|Esta invocación puede llevar a llamadas a la base de datos que no están permitidas.|
> |**Nombre**:<br />DatacenterNotAvailable<br />**Hex**:<br />8004B065<br />**Número**:<br />-2147176347|Este punto de conexión del centro de datos no está disponible actualmente para la organización.|
> |**Nombre**:<br />DataColumnsNumberMismatch<br />**Hex**:<br />80040345<br />**Número**:<br />-2147220667|El número de campos difiere del número de encabezados de columnas.|
> |**Nombre**:<br />DataEngineQueryThrottling<br />**Hex**:<br />80048544<br />**Número**:<br />-2147187388|Esta consulta no puede ser ejecutada porque está en conflicto con la optimización del rendimiento.|
> |**Nombre**:<br />DatafieldNameShouldBeNull<br />**Hex**:<br />8006041b<br />**Número**:<br />-2147089381|ActionStep {0} hace referencia a DataFieldName {1} no válido.|
> |**Nombre**:<br />DataMigrationManagerMandatoryUpdatesNotInstalled<br />**Hex**:<br />80044336<br />**Número**:<br />-2147204298|Se ha cancelado la configuración del administrador de migración de datos por primera vez. No podrás usar el Administrador de migración de datos hasta que finalice la configuración.|
> |**Nombre**:<br />DataMigrationManagerUnknownProblem<br />**Hex**:<br />80044333<br />**Número**:<br />-2147204301|El Administrador de migración de datos encontró un problema desconocido y no puede continuar. Para volver a intentarlo, reinicie el Administrador de migración de datos.|
> |**Nombre**:<br />DatasheetNotAvailable<br />**Hex**:<br />800609B5<br />**Número**:<br />-2147087947|La hoja de datos no está disponible.|
> |**Nombre**:<br />DataSourceInitializeFailedErrorCode<br />**Hex**:<br />8005F210<br />**Número**:<br />-2147094000|Vuelva a intentarlo. Si el problema persiste, busque alguna solución en {0} o póngase en contacto con el administrador de {#Brand_CRM} de su organización. Finalmente, puede contactar {1}.|
> |**Nombre**:<br />DataSourceOfflineErrorCode<br />**Hex**:<br />8005F211<br />**Número**:<br />-2147093999|Esta operación produjo un error porque está sin conexión. Vuelva a conectarse e inténtelo de nuevo.|
> |**Nombre**:<br />DataSourceProhibited<br />**Hex**:<br />8004830D<br />**Número**:<br />-2147187955|Un origen de datos en basados en fetch no se admite en este informe|
> |**Nombre**:<br />DataStoreKeyNotFoundErrorCode<br />**Hex**:<br />8005F21d<br />**Número**:<br />-2147093987|La clave no está en el almacén local '{0}'|
> |**Nombre**:<br />DataSyncBadRequest<br />**Hex**:<br />80072514<br />**Número**:<br />-2147015404|El servidor no ha entendido la solicitud|
> |**Nombre**:<br />DataSyncNoContent<br />**Hex**:<br />80072512<br />**Número**:<br />-2147015406|No hay contenido de sincronización de datos|
> |**Nombre**:<br />DataSyncRequestAccepted<br />**Hex**:<br />80072511<br />**Número**:<br />-2147015407|Solicitud de sincronización de datos aceptada|
> |**Nombre**:<br />DataTableNotAvailable<br />**Hex**:<br />800609B0<br />**Número**:<br />-2147087952|La tabla de datos original se eliminó o se le cambió el nombre.|
> |**Nombre**:<br />DataTypeMismatchForLinkedAttribute<br />**Hex**:<br />8004F0FC<br />**Número**:<br />-2147159812|Tipo de datos incorrectos encontrados para atributos vinculados.|
> |**Nombre**:<br />DateTimeFormatFailed<br />**Hex**:<br />8004025a<br />**Número**:<br />-2147220902|No se puede generar un valor con formato de fecha y hora.|
> |**Nombre**:<br />DBConnectionOrTransactionInitializationFailed<br />**Hex**:<br />80048551<br />**Número**:<br />-2147187375|La inicialización de la conexión de la base de datos o la transacción falló. Esta operación se debe volver a intentar más tarde. Mensaje de inicialización de la excepción: {0}|
> |**Nombre**:<br />DBUpgradeCauseTimeout<br />**Hex**:<br />80048553<br />**Número**:<br />-2147187373|La operación ha excedido el tiempo de espera porque la base de datos se está actualizando. Vuelva a intentarlo una vez que finalice la actualización de la base de datos.|
> |**Nombre**:<br />DecimalValueOutOfRange<br />**Hex**:<br />80044330<br />**Número**:<br />-2147204304|Se ha producido un error de validación. El valor decimal especificado no está comprendido en el intervalo de valores permitidos para este atributo.|
> |**Nombre**:<br />DecoupleChildEntity<br />**Hex**:<br />80048206<br />**Número**:<br />-2147188218|No se puede separar una entidad secundaria.|
> |**Nombre**:<br />DecoupleUserOwnedEntity<br />**Hex**:<br />80048207<br />**Número**:<br />-2147188217|Solo se pueden separar entidades de usuario.|
> |**Nombre**:<br />DecreasingDaysWillDeleteOlderData<br />**Hex**:<br />80060992<br />**Número**:<br />-2147087982|Al reducir el número de días se eliminarán los datos mobile offline anteriores al número de días especificado.|
> |**Nombre**:<br />DefaultSiteCollectionUrlChanged<br />**Hex**:<br />8004F100<br />**Número**:<br />-2147159808|La dirección Url de colección de sitios predeterminada ha cambiado esta organización después de que se creara esta operación.|
> |**Nombre**:<br />DefaultSiteMapDeleteFailure<br />**Hex**:<br />80048070<br />**Número**:<br />-2147188624|El mapa del sitio predeterminado no se puede eliminar.|
> |**Nombre**:<br />DelegatedAdminUserCannotBeCreateNorUpdated<br />**Hex**:<br />80041d67<br />**Número**:<br />-2147213977|No se puede actualizar el usuario administrador delegado|
> |**Nombre**:<br />DeleteActiveWorkflowTemplateDependency<br />**Hex**:<br />8004501A<br />**Número**:<br />-2147200998|No se puede eliminar una dependencia de flujo de trabajo de una plantilla de flujo de trabajo publicada.|
> |**Nombre**:<br />DeletePublishedWorkflowDefinitionWorkflowDependency<br />**Hex**:<br />80045006<br />**Número**:<br />-2147201018|No se puede eliminar una dependencia de flujo de trabajo para una definición de un flujo de trabajo publicada.|
> |**Nombre**:<br />DeleteWorkflowActivation<br />**Hex**:<br />80045004<br />**Número**:<br />-2147201020|No se puede eliminar la activación de un flujo de trabajo.|
> |**Nombre**:<br />DeleteWorkflowActivationWorkflowDependency<br />**Hex**:<br />80045005<br />**Número**:<br />-2147201019|No se puede eliminar una dependencia de flujo de trabajo asociada con la activación de un flujo de trabajo.|
> |**Nombre**:<br />DeleteWorkflowActiveDefinition<br />**Hex**:<br />8004500F<br />**Número**:<br />-2147201009|No se puede eliminar una definición de flujo de trabajo activa.|
> |**Nombre**:<br />DeleteWorkflowActiveTemplate<br />**Hex**:<br />8004501C<br />**Número**:<br />-2147200996|No se puede eliminar una plantilla de flujo de trabajo activa.|
> |**Nombre**:<br />DelveActionHubAttributeMissingInResponseException<br />**Hex**:<br />80071002<br />**Número**:<br />-2147020798|Atributo no presente en la respuesta oData de Exchange.|
> |**Nombre**:<br />DelveActionHubAuthorizationFailureException<br />**Hex**:<br />80071007<br />**Número**:<br />-2147020793|No tiene la licencia de Office 365 adecuada para acciones de vista. Póngase en contacto con el administrador del sistema.|
> |**Nombre**:<br />DelveActionHubDisabledError<br />**Hex**:<br />80071000<br />**Número**:<br />-2147020800|La característica del centro de acciones Delve no está habilitada.|
> |**Nombre**:<br />DelveActionHubInvalidResponseFormatException<br />**Hex**:<br />80071004<br />**Número**:<br />-2147020796|Formato de respuesta no válido.|
> |**Nombre**:<br />DelveActionHubInvalidStateCodeException<br />**Hex**:<br />80071003<br />**Número**:<br />-2147020797|Se pasó un código de estado no válido en la expresión.|
> |**Nombre**:<br />DelveActionHubResponseRetievalFailureException<br />**Hex**:<br />80071005<br />**Número**:<br />-2147020795|Error al capturar acciones de Exchange.|
> |**Nombre**:<br />DelveActionHubS2SSetupFailureException<br />**Hex**:<br />80071008<br />**Número**:<br />-2147020792|No se ha configurado la autenticación de servidor a servidor con Exchange para el Centro de acciones de Delve.|
> |**Nombre**:<br />DependencyAlreadyExists<br />**Hex**:<br />8004F01A<br />**Número**:<br />-2147160038|Ya existe una dependencia {0} entre {1}({2}) y {3}({4}).  No se pueden crear también {5} dependencia.|
> |**Nombre**:<br />DependencyTableNotEmpty<br />**Hex**:<br />8004F01B<br />**Número**:<br />-2147160037|En la tabla de dependencias debe estar vacía para que la inicialización se complete correctamente.|
> |**Nombre**:<br />DependencyTrackingClosed<br />**Hex**:<br />8004F025<br />**Número**:<br />-2147160027|Intento no válido de procesar una dependencia después de cerrar el contexto de transacciones actual.|
> |**Nombre**:<br />DeploymentServiceCannotChangeStateForDeploymentService<br />**Hex**:<br />8004D262<br />**Número**:<br />-2147167646|No puede cambiar el estado de este servidor porque contiene el rol de servidor del servicio de implementación.|
> |**Nombre**:<br />DeploymentServiceCannotDeleteOperationInProgress<br />**Hex**:<br />8004D265<br />**Número**:<br />-2147167643|El servicio de implementación no puede eliminar la operación especificada porque está actualmente en curso.|
> |**Nombre**:<br />DeploymentServiceNotAllowOperation<br />**Hex**:<br />8004D261<br />**Número**:<br />-2147167647|Servicio de implementación para {0} no admite {1} operación.|
> |**Nombre**:<br />DeploymentServiceNotAllowSetToThisState<br />**Hex**:<br />8004D260<br />**Número**:<br />-2147167648|Servicio de implementación para {0} permite el estado habilitado o deshabilitado. No se puede establecer el estado en {1}.|
> |**Nombre**:<br />DeploymentServiceOperationIdentifierNotFound<br />**Hex**:<br />8004D264<br />**Número**:<br />-2147167644|El servicio de implementación no ha podido encontrar una operación diferida con el identificador especificado.|
> |**Nombre**:<br />DeploymentServiceRequestValidationFailure<br />**Hex**:<br />8004D263<br />**Número**:<br />-2147167645|El servicio de implementación no puede procesar la solicitud porque una o varias comprobaciones han fallado.|
> |**Nombre**:<br />DeprecatedFormActivation<br />**Hex**:<br />8004F662<br />**Número**:<br />-2147158430|Este formulario pasó a ser obsoleto en la versión anterior y no se puede usar ya. Migre los cambios a un formulario diferente. Formularios obsoletos se quitarán del sistema en el futuro.|
> |**Nombre**:<br />DeprecatedMobileFormsCreation<br />**Hex**:<br />8004F667<br />**Número**:<br />-2147158425|Se han quedado obsoletos los formularios móviles. No se pueden crear nuevos formularios de Mobile Express.|
> |**Nombre**:<br />DeprecatedMobileFormsEdit<br />**Hex**:<br />8004F668<br />**Número**:<br />-2147158424|Se han quedado obsoletos los formularios móviles. No se puede abrir el editor de formularios móviles.|
> |**Nombre**:<br />DeprovisionRIAccessNotAllowed<br />**Hex**:<br />80044274<br />**Número**:<br />-2147204492|Solo el administrador del sistema puede desactivar Información de relaciones.|
> |**Nombre**:<br />DesignerAccessDenied<br />**Hex**:<br />80050100<br />**Número**:<br />-2147155712|No tiene privilegios suficientes para realizar la operación solicitada. Para obtener más información, póngase en contacto con el administrador.|
> |**Nombre**:<br />DesignerInvalidParameter<br />**Hex**:<br />80050101<br />**Número**:<br />-2147155711|El {0} se ha indicado de manera incorrecta o falta. Inténtelo de nuevo con el {1} correcto.|
> |**Nombre**:<br />DestinationFolderNotExists<br />**Hex**:<br />80071022<br />**Número**:<br />-2147020766|No se pueden copiar los documentos. La ubicación del documento de destino ya no existe.|
> |**Nombre**:<br />DialogNameCannotBeNull<br />**Hex**:<br />80060873<br />**Número**:<br />-2147088269|"DialogName no puede ser nulo para tipo de diálogo|
> |**Nombre**:<br />DisabledCRMAddinLoadFailure<br />**Hex**:<br />80044202<br />**Número**:<br />-2147204606|Se ha producido un error durante la carga de la funcionalidad de Microsoft Dynamics 365. Intente reiniciar Outlook. Si el problema persiste, póngase en contacto con el administrador del sistema.|
> |**Nombre**:<br />DisabledCRMClientVersionHigher<br />**Hex**:<br />80044204<br />**Número**:<br />-2147204604|Debe actualizarse Microsoft Dynamics 365 Server antes de usar el cliente de Microsoft Dynamics 365. Póngase en contacto con el administrador del sistema para obtener asistencia.|
> |**Nombre**:<br />DisabledCRMClientVersionLower<br />**Hex**:<br />80044203<br />**Número**:<br />-2147204605|Si está ejecutando una versión de Microsoft Dynamics 365 for Outlook que no se admite para el modo sin conexión con esta organización de Microsoft Dynamics 365 {0}. Deberá actualizar a una versión compatible de Dynamics 365 for Outlook. Asegúrese de que la versión actual de Dynamics 365 for Outlook se admite para actualizar a la versión compatible.|
> |**Nombre**:<br />DisabledCRMGoingOffline<br />**Hex**:<br />80044200<br />**Número**:<br />-2147204608|La funcionalidad de Microsoft Dynamics 365 no está disponible mientras se está realizando la sincronización sin conexión|
> |**Nombre**:<br />DisabledCRMGoingOnline<br />**Hex**:<br />80044201<br />**Número**:<br />-2147204607|La funcionalidad de Microsoft Dynamics 365 no está disponible mientras se está realizando la sincronización con conexión|
> |**Nombre**:<br />DisabledCRMOnlineCrmNotAvailable<br />**Hex**:<br />80044206<br />**Número**:<br />-2147204602|Microsoft Dynamics 365 Server no está disponible|
> |**Nombre**:<br />DisabledCRMPostOfflineUpgrade<br />**Hex**:<br />80044205<br />**Número**:<br />-2147204603|La funcionalidad de Microsoft Dynamics 365 no estará disponible hasta que el cliente de Microsoft Microsoft Dynamics 365 vuelva a estar conectado.|
> |**Nombre**:<br />DisableRIFeatureNotAllowed<br />**Hex**:<br />80044280<br />**Número**:<br />-2147204480|Necesita privilegios de administrador del sistema para desactivar Información de relaciones en su organización.|
> |**Nombre**:<br />DiscountAmount<br />**Hex**:<br />80043b20<br />**Número**:<br />-2147206368|El tipo de descuento no admite descuentos de 'porcentaje'.|
> |**Nombre**:<br />DiscountAmountAndPercent<br />**Hex**:<br />80043b1f<br />**Número**:<br />-2147206369|No se puede establecer 'importe' y 'porcentaje'.|
> |**Nombre**:<br />DiscountPercent<br />**Hex**:<br />80043b21<br />**Número**:<br />-2147206367|El tipo de descuento no admite descuentos de 'importe'.|
> |**Nombre**:<br />DiscountRangeOverlap<br />**Hex**:<br />80043b02<br />**Número**:<br />-2147206398|Las nuevas cantidades se superponen con el intervalo cubierto por las cantidades existentes.|
> |**Nombre**:<br />DiscountTypeAndPriceLevelCurrencyNotEqual<br />**Hex**:<br />80048cf8<br />**Número**:<br />-2147185416|La divisa del descuento debe coincidir con la divisa de la lista de precios del importe del tipo de descuento.|
> |**Nombre**:<br />DiskSpaceNotEnough<br />**Hex**:<br />80050124<br />**Número**:<br />-2147155676|No hay suficiente espacio en la carpeta Temp.|
> |**Nombre**:<br />DistinctWithImageAttributeError<br />**Hex**:<br />80072531<br />**Número**:<br />-2147015375|No se permite la distinción cuando se seleccionan los atributos de imagen.|
> |**Nombre**:<br />DistributeListAssociatedVary<br />**Hex**:<br />80048453<br />**Número**:<br />-2147187629|Esta actividad de campaña no se puede distribuir. Solo puede realizar actividades de combinación de correspondencia en las listas de marketing que sean todas del mismo tipo de registro. En esta actividad de campaña, elimine las listas de marketing para que las restantes sean del mismo tipo de registro y, después, inténtelo de nuevo.|
> |**Nombre**:<br />DistributeNoListAssociated<br />**Hex**:<br />80048454<br />**Número**:<br />-2147187628|Esta actividad de campaña no se puede distribuir. No hay listas de marketing asociados con él. Agregue al menos una lista de marketing e inténtelo de nuevo.|
> |**Nombre**:<br />DocumentManagementDisabled<br />**Hex**:<br />8004F0FF<br />**Número**:<br />-2147159809|Se deshabilitó la administración de documentos de esta organización.|
> |**Nombre**:<br />DocumentManagementDisabledForEmail<br />**Hex**:<br />80050010<br />**Número**:<br />-2147155952|La administración de documentos debe estar habilitada en la entidad de correo electrónico para seguimiento de adjuntos. Póngase en contacto con su administrador para habilitar la administración de documentos.|
> |**Nombre**:<br />DocumentManagementDisabledOnEntity<br />**Hex**:<br />80060908<br />**Número**:<br />-2147088120|Debe habilitar la administración de documentos para esta Entidad para habilitar la integración de OneNote.|
> |**Nombre**:<br />DocumentManagementIsDisabled<br />**Hex**:<br />8004F312<br />**Número**:<br />-2147159278|La administración de documentos no está habilitada para esta organización.|
> |**Nombre**:<br />DocumentManagementIsDisabledOnEntity<br />**Hex**:<br />80071011<br />**Número**:<br />-2147020783|Debe habilitar la administración de documentos para esta entidad para habilitar las recomendaciones de documentos.|
> |**Nombre**:<br />DocumentManagementNotEnabledNoPrimaryField<br />**Hex**:<br />8004F313<br />**Número**:<br />-2147159277|No se pudo habilitar la administración de documentos debido a que un campo principal no está definido para esta entidad con el nombre {0} y el id {1}.|
> |**Nombre**:<br />DocumentRecommendationsFCBOff<br />**Hex**:<br />80071019<br />**Número**:<br />-2147020775|La característica de sugerencia del documento no está habilitada.|
> |**Nombre**:<br />DocumentTemplateFeatureNotEnabled<br />**Hex**:<br />800608C9<br />**Número**:<br />-2147088183|La función de plantillas de documentos no está habilitada.|
> |**Nombre**:<br />DocxExportGeneratingWordFailed<br />**Hex**:<br />800608CD<br />**Número**:<br />-2147088179|Se produjo un error al generar el documento de Word. Inténtelo de nuevo.|
> |**Nombre**:<br />DocxValidationFailed<br />**Hex**:<br />800608CE<br />**Número**:<br />-2147088178|La carga ha fallado porque el archivo seleccionado no es coherente con el diseño de la plantilla. Inténtelo de nuevo tras seleccionar un archivo con el diseño de plantilla.|
> |**Nombre**:<br />DoNotTrackItem<br />**Hex**:<br />80044228<br />**Número**:<br />-2147204568|No se realizará el seguimiento del elemento seleccionado.|
> |**Nombre**:<br />DownloadAllEntityRecordsChangedOrCreatedWithinTheseDays<br />**Hex**:<br />8006098F<br />**Número**:<br />-2147087985|Descargar todos los registros de la entidad modificados o creados en este número de días.|
> |**Nombre**:<br />DownloadRelatedDataOnlyMustHaveRelationship<br />**Hex**:<br />80071140<br />**Número**:<br />-2147020480|La entidad '{0}' del perfil '{1}' está configurada solo con datos relacionados con descarga de filtro, sin embargo no hay relaciones especificadas para esta entidad en asociaciones del elemento de perfil. Si se establece una entidad para descargar datos relacionados solo usted debe especificar una asociación de elemento de perfil a esta entidad.|
> |**Nombre**:<br />DraftBundleToProduct<br />**Hex**:<br />8004F994<br />**Número**:<br />-2147157612|Solo puede agregar productos a una agrupación de borrador.|
> |**Nombre**:<br />DSSThrottlingConcurrencyLimitExceededError<br />**Hex**:<br />80072327<br />**Número**:<br />-2147015897|Demasiadas solicitudes simultáneas detectadas.|
> |**Nombre**:<br />DuplicateAliasFound<br />**Hex**:<br />8004E00B<br />**Número**:<br />-2147164149|Descripción de datos no válida Se encontró un alias duplicado.|
> |**Nombre**:<br />DuplicateApplicationUser<br />**Hex**:<br />8004F511<br />**Número**:<br />-2147158767|Está intentando crear un id. de aplicación = {0} que ya exista.|
> |**Nombre**:<br />DuplicateAppModuleUniqueName<br />**Hex**:<br />8005011F<br />**Número**:<br />-2147155681|El nombre que ha escrito ya se está usando.|
> |**Nombre**:<br />DuplicateAttributePhysicalName<br />**Hex**:<br />80060304<br />**Número**:<br />-2147089660|El atributo {0} ya existe para la entidad {1}.|
> |**Nombre**:<br />DuplicateAttributeSchemaName<br />**Hex**:<br />80047013<br />**Número**:<br />-2147192813|{0}|
> |**Nombre**:<br />DuplicateChannelPropertyName<br />**Hex**:<br />800608F1<br />**Número**:<br />-2147088143|Ya existe una propiedad de canal con el nombre especificado. No puede crear otra.|
> |**Nombre**:<br />DuplicateCheckNotEnabled<br />**Hex**:<br />80048412<br />**Número**:<br />-2147187694|La detección de duplicados no está habilitada. Para habilitar la detección de duplicados, haga clic en Configuración, en Administración de datos y, a continuación, en Configuración de detección de duplicados.|
> |**Nombre**:<br />DuplicateCheckNotSupportedOnEntity<br />**Hex**:<br />80048410<br />**Número**:<br />-2147187696|Este tipo de registro no admite la detección de duplicados.|
> |**Nombre**:<br />DuplicateComponentInSolutionXml<br />**Hex**:<br />80071153<br />**Número**:<br />-2147020461|El componente duplicado se encuentra en el XML.|
> |**Nombre**:<br />DuplicateDetectionNotSupportedOnAttributeType<br />**Hex**:<br />80048430<br />**Número**:<br />-2147187664|La condición de regla no se puede crear ni actualizar porque la detección de duplicados no se admite en el tipo de datos del atributo seleccionado.|
> |**Nombre**:<br />DuplicateDetectionRulesWereUnpublished<br />**Hex**:<br />8004F039<br />**Número**:<br />-2147160007|Debido a posibles modificaciones de la entidad, se anuló la publicación de reglas de detección de duplicados de esta entidad.|
> |**Nombre**:<br />DuplicateDetectionTemplateNotFound<br />**Hex**:<br />80048424<br />**Número**:<br />-2147187676|Microsoft Dynamics 365 no puede recuperar la plantilla de notificación de correo.|
> |**Nombre**:<br />DuplicateDisplayCollectionName<br />**Hex**:<br />80047012<br />**Número**:<br />-2147192814|Ya existe un objeto con el nombre de recopilación especificado.|
> |**Nombre**:<br />DuplicateDisplayName<br />**Hex**:<br />80047011<br />**Número**:<br />-2147192815|Ya existe un objeto con el nombre especificado.|
> |**Nombre**:<br />DuplicatedJobId<br />**Hex**:<br />80071152<br />**Número**:<br />-2147020462|El parámetro ImportJobId debe ser único.|
> |**Nombre**:<br />DuplicatedJobIdDueToConcurrency<br />**Hex**:<br />80071155<br />**Número**:<br />-2147020459|No se puede crear el trabajo de solución con el JobId proporcionado ({0}) porque ya está en uso. Esto puede indicar que otra operación de la solución está en progreso. Inténtelo de nuevo más tarde.|
> |**Nombre**:<br />DuplicatedPrivilege<br />**Hex**:<br />8004140f<br />**Número**:<br />-2147216369|El privilegio {0} está duplicado.|
> |**Nombre**:<br />DuplicateFileNamesInZip<br />**Hex**:<br />80048484<br />**Número**:<br />-2147187580|Dos o más archivos tienen el mismo nombre. Los nombres de archivo deben ser únicos.|
> |**Nombre**:<br />DuplicateGroupByFound<br />**Hex**:<br />8004E01B<br />**Número**:<br />-2147164133|Descripción de datos no válida No se puede usar el mismo atributo como un grupo más de una vez.|
> |**Nombre**:<br />DuplicateHeaderColumn<br />**Hex**:<br />80040338<br />**Número**:<br />-2147220680|Existe un encabezado de columna duplicado.|
> |**Nombre**:<br />DuplicateIsoCurrencyCode<br />**Hex**:<br />80048cf3<br />**Número**:<br />-2147185421|No se puede insertar registro de divisa duplicado. Moneda con el mismo código de divisa ya existe en el sistema.|
> |**Nombre**:<br />DuplicateLookupFound<br />**Hex**:<br />80040352<br />**Número**:<br />-2147220654|Se encontró una referencia de búsqueda duplicada|
> |**Nombre**:<br />DuplicateMapName<br />**Hex**:<br />80048443<br />**Número**:<br />-2147187645|Ya existe una asignación de datos con el nombre especificado.|
> |**Nombre**:<br />DuplicateName<br />**Hex**:<br />80047010<br />**Número**:<br />-2147192816|Ya existe un objeto con el nombre especificado|
> |**Nombre**:<br />DuplicateOfflineFilter<br />**Hex**:<br />80048449<br />**Número**:<br />-2147187639|Puede crear solo un grupo de datos locales para cada tipo de registro.|
> |**Nombre**:<br />DuplicateOutlookAppointment<br />**Hex**:<br />80040274<br />**Número**:<br />-2147220876|Ya se ha realizado el seguimiento en Dynamics 365 de la cita que se está promocionando desde Outlook.|
> |**Nombre**:<br />DuplicatePrimaryNameAttribute<br />**Hex**:<br />8004701E<br />**Número**:<br />-2147192802|El nuevo atributo {2} se ha establecido como el atributo de nombre principal de la entidad {1}. La entidad {1} ya tiene el juego de atributos {0} como el atributo nombre principal. Una entidad solo puede tener un atributo de nombre principal.|
> |**Nombre**:<br />DuplicatePrivilegeInRolecontrol<br />**Hex**:<br />80061118<br />**Número**:<br />-2147086056|La matriz de privilegios de perfil de acceso al canal contiene referencias de privilegios duplicadas.|
> |**Nombre**:<br />DuplicateProductPriceLevel<br />**Hex**:<br />80043b08<br />**Número**:<br />-2147206392|Esta combinación de producto y unidad ya tiene un precio para esta lista de precios.|
> |**Nombre**:<br />DuplicateProductRelationship<br />**Hex**:<br />8004F891<br />**Número**:<br />-2147157871|Ya existe una relación de producto entre el mismo producto y el producto relacionado.|
> |**Nombre**:<br />DuplicateRecord<br />**Hex**:<br />80040237<br />**Número**:<br />-2147220937|La operación da error debido a una infracción de integridad de SQL.|
> |**Nombre**:<br />DuplicateRecordEntityKey<br />**Hex**:<br />80060892<br />**Número**:<br />-2147088238|Clave de entidad {0} violada. Ya existe un registro con el mismo valor para {1}. No se puede crear un registro duplicado. Seleccione uno o varios valores únicos e inténtelo de nuevo.|
> |**Nombre**:<br />DuplicateRecordsFound<br />**Hex**:<br />80040333<br />**Número**:<br />-2147220685|No se creó ni actualizó ningún registro porque ya existe un duplicado del registro actual.|
> |**Nombre**:<br />DuplicateReportVisibility<br />**Hex**:<br />80040495<br />**Número**:<br />-2147220331|Ya existe ReportVisibility con el mismo ReportId y VisibilityCode. No se permiten duplicados.|
> |**Nombre**:<br />DuplicateSalesTeamMember<br />**Hex**:<br />80048341<br />**Número**:<br />-2147187903|El usuario que intenta agregar ya es miembro del equipo de ventas.|
> |**Nombre**:<br />DuplicateUIStatementRootsFound<br />**Hex**:<br />8004F201<br />**Número**:<br />-2147159551|Puede haber solo una declaración raíz para un determinado uiscript.|
> |**Nombre**:<br />DynamicPropertyDefaultValueNeeded<br />**Hex**:<br />80061038<br />**Número**:<br />-2147086280|Debe especificar un valor predeterminado ya que esta propiedad es obligatoria y de solo lectura.|
> |**Nombre**:<br />DynamicPropertyInstanceMissingRequiredColumns<br />**Hex**:<br />8008100A<br />**Número**:<br />-2146955254|La instancia de propiedad no se puede actualizar. Compruebe que existen los campos siguientes: dynamicpropertyid, dynamicpropertyoptionsetvalueid y regardingobjectid.|
> |**Nombre**:<br />DynamicPropertyInstanceUpdateValuesDifferentRegarding<br />**Hex**:<br />8008100B<br />**Número**:<br />-2146955253|No se han podido guardar las instancias de propiedad porque hacen referencia a elementos de línea de producto diferentes.|
> |**Nombre**:<br />DynamicPropertyInvalidRegardingForUpdate<br />**Hex**:<br />80081004<br />**Número**:<br />-2146955260|No puede crear ni cambiar las propiedades de un producto publicado o eliminado.|
> |**Nombre**:<br />DynamicPropertyInvalidStateChange<br />**Hex**:<br />80081001<br />**Número**:<br />-2146955263|No puede establecer en estado Activo una propiedad inactiva.|
> |**Nombre**:<br />DynamicPropertyInvalidStateForDelete<br />**Hex**:<br />80081002<br />**Número**:<br />-2146955262|No puede eliminar una propiedad que está en el estado Activo.|
> |**Nombre**:<br />DynamicPropertyInvalidStateForUpdate<br />**Hex**:<br />80081000<br />**Número**:<br />-2146955264|No puede actualizar una propiedad que no está en el estado Borrador.|
> |**Nombre**:<br />DynamicPropertyOptionSetInvalidStateForUpdate<br />**Hex**:<br />8008100C<br />**Número**:<br />-2146955252|No puede modificar el elemento del conjunto de opciones de propiedad para una propiedad que no se encuentra en el estado de borrador.|
> |**Nombre**:<br />EditorOnlySupportAndOperatorForLogicalConditions<br />**Hex**:<br />80060005<br />**Número**:<br />-2147090427|La expresión de regla contiene un operador lógico que no se admite. El editor solo admite el operador Y para las condiciones lógicas.|
> |**Nombre**:<br />EditQueryInDynamicExcelNotSupported<br />**Hex**:<br />800609B8<br />**Número**:<br />-2147087944|No puede editar la consulta en una hoja de cálculo dinámica una vez que ha exportado el archivo de Excel. Si desea realizar cambios, vuelva a Dynamics 365 y a continuación reexporte.|
> |**Nombre**:<br />EESiteDBFetchFailure<br />**Hex**:<br />80050025<br />**Número**:<br />-2147155931|No se pueden capturar datos de la dase de datos del sitio.|
> |**Nombre**:<br />EmailAlreadyExistsInDestinationQueue<br />**Hex**:<br />80040523<br />**Número**:<br />-2147220189|No puede agregar este correo electrónico a la cola seleccionada. Ya existe un elemento de cola para este correo electrónico en cola. Puede eliminar el elemento de la cola e intentarlo de nuevo.|
> |**Nombre**:<br />EmailDoesNotExist<br />**Hex**:<br />80050007<br />**Número**:<br />-2147155961|No existe correo para unos datos adjuntos determinados.|
> |**Nombre**:<br />EmailEngagementFeatureDisabled<br />**Hex**:<br />80050003<br />**Número**:<br />-2147155965|Habilite la característica Interacción de correo para la organización actual para seguir o dejar de seguir los datos adjuntos de correo.|
> |**Nombre**:<br />EmailEngagementFeatureDisabledForAttachmentTracking<br />**Hex**:<br />80050015<br />**Número**:<br />-2147155947|Habilite la característica Interacción por correo electrónico de la organización para el seguimiento de los datos adjuntos del correo electrónico.|
> |**Nombre**:<br />EmailInteractionsFetchFailure<br />**Hex**:<br />80050022<br />**Número**:<br />-2147155934|No se puede capturar interacciones de correo electrónico.|
> |**Nombre**:<br />EmailMessageSizeExceeded<br />**Hex**:<br />8005E237<br />**Número**:<br />-2147098057|El tamaño del correo electrónico supera el MaximumMessageSizeLimit especificado por la implementación.|
> |**Nombre**:<br />EmailMonitoringDeProvisionFailed<br />**Hex**:<br />80050014<br />**Número**:<br />-2147155948|La característica de desaprovisionamiento de interacción de correo electrónico da error|
> |**Nombre**:<br />EmailMonitoringNotProvisioned<br />**Hex**:<br />80050011<br />**Número**:<br />-2147155951|Fallo en el servicio de aprovisionamiento de RI|
> |**Nombre**:<br />EmailMonitoringProvisionFailed<br />**Hex**:<br />80050012<br />**Número**:<br />-2147155950|La característica de aprovisionamiento de interacción de correo electrónico da error|
> |**Nombre**:<br />EmailNotFollowed<br />**Hex**:<br />80050008<br />**Número**:<br />-2147155960|No se pueden seguir estos datos adjuntos porque no se sigue su correo correspondiente.|
> |**Nombre**:<br />EmailOpenActionCardCreationFailure<br />**Hex**:<br />80050024<br />**Número**:<br />-2147155932|No se puede crear tarjeta de acción de apertura de correo electrónico.|
> |**Nombre**:<br />EmailRecipientNotSpecified<br />**Hex**:<br />80040b04<br />**Número**:<br />-2147218684|El correo electrónico debe tener al menos un destinatario para poder enviarlo|
> |**Nombre**:<br />EmailReminderActionCardCreationFailure<br />**Hex**:<br />80050023<br />**Número**:<br />-2147155933|No se puede crear tarjeta de acción de recuerdo de correo electrónico.|
> |**Nombre**:<br />EmailRouterFileTooLargeToProcess<br />**Hex**:<br />8005F031<br />**Número**:<br />-2147094479|Uno o varios de los archivos de configuración de E-mail Router es demasiado grande para procesar.|
> |**Nombre**:<br />EmailServerProfileADBasedAuthenticationProtocolNotAllowed<br />**Hex**:<br />8005E23C<br />**Número**:<br />-2147098052|El protocolo de autenticación no se puede establecer en Negociar o NTLM para su organización porque estos requieren Active Directory. Utilice un protocolo de autenticación diferente o póngase en contacto con el administrador del sistema para habilitar el protocolo de autenticación basado en Active Directory.|
> |**Nombre**:<br />EmailServerProfileAutoDiscoverNotAllowed<br />**Hex**:<br />8005E204<br />**Número**:<br />-2147098108|La detección automática de la ubicación de servidor URL solo puede usarse para un tipo de servidor de correo electrónico de intercambio.|
> |**Nombre**:<br />EmailServerProfileBasicAuthenticationProtocolNotAllowed<br />**Hex**:<br />8005E23D<br />**Número**:<br />-2147098051|No se puede usar el protocolo de autenticación especificado porque el protocolo requiere enviar las credenciales en un canal seguro. Utilice un protocolo de autenticación diferente o póngase en contacto con el administrador para habilitar el protocolo de autenticación básico en un canal no seguro.|
> |**Nombre**:<br />EmailServerProfileDelegateAccessNotAllowed<br />**Hex**:<br />8005E235<br />**Número**:<br />-2147098059|Para un tipo de servidor de correo electrónico SMTP, no se puede usar acceso delegado concedido automáticamente.|
> |**Nombre**:<br />EmailServerProfileImpersonationNotAllowed<br />**Hex**:<br />8005E236<br />**Número**:<br />-2147098058|Para un tipo de servidor de correo electrónico no Exchange, no se puede usar suplantación.|
> |**Nombre**:<br />EmailServerProfileInvalidAuthenticationProtocol<br />**Hex**:<br />8005E23B<br />**Número**:<br />-2147098053|El protocolo de autenticación no es válido para el servidor y el tipo de conexión especificados. Para obtener más información, póngase en contacto con el administrador del sistema.|
> |**Nombre**:<br />EmailServerProfileInvalidCredentialRetrievalForExchange<br />**Hex**:<br />8005E203<br />**Número**:<br />-2147098109|No hay credenciales (anónimo) que puedan usar un tipo de conexión para tipo de servidor de correo electrónico de exchange.|
> |**Nombre**:<br />EmailServerProfileInvalidCredentialRetrievalForOnline<br />**Hex**:<br />8005E202<br />**Número**:<br />-2147098110|La autenticación anónima o integrada en Windows no se puede emplear como tipo de conexión para Microsoft Dynamics 365 Online.|
> |**Nombre**:<br />EmailServerProfileInvalidServerLocation<br />**Hex**:<br />8005E20A<br />**Número**:<br />-2147098102|La ubicación de servidor especificada {0} no es válida. Solucione el la ubicación del servidor e inténtelo de nuevo.|
> |**Nombre**:<br />EmailServerProfileLocationNotRequired<br />**Hex**:<br />8005E205<br />**Número**:<br />-2147098107|No se puede especificar la ubicación del servidor de correo electrónico entrante o saliente cuando se ha establecido la ubicación de servidor Autodiscover en true.|
> |**Nombre**:<br />EmailServerProfileNotAssociated<br />**Hex**:<br />8005E222<br />**Número**:<br />-2147098078|El perfil de servidor de correo electrónico no está asociado con el buzón actual. Asocie un perfil válido para enviar/recibir mensajes.|
> |**Nombre**:<br />EmailServerProfileSslRequiredForOnline<br />**Hex**:<br />8005E201<br />**Número**:<br />-2147098111|No se puede establecer SSL como falso para Microsoft Dynamics 365 Online.|
> |**Nombre**:<br />EmailServerProfileSslRequiredForOnPremise<br />**Hex**:<br />8005E234<br />**Número**:<br />-2147098060|El uso de SSL al ponerse en contacto con servidores de correo electrónico externos es obligatorio para esta implementación de Dynamics 365.|
> |**Nombre**:<br />EmptyCommandOrEntity<br />**Hex**:<br />80154B51<br />**Número**:<br />-2146088111|El nombre del comando o la entidad no puede estar vacío.|
> |**Nombre**:<br />EmptyContent<br />**Hex**:<br />80040365<br />**Número**:<br />-2147220635|El archivo está vacío.|
> |**Nombre**:<br />EmptyEntityFilterXml<br />**Hex**:<br />80071118<br />**Número**:<br />-2147020520|Falta FetchXML.|
> |**Nombre**:<br />EmptyFileForImport<br />**Hex**:<br />80048487<br />**Número**:<br />-2147187577|El archivo seleccionado no contiene ningún dato.|
> |**Nombre**:<br />EmptyFilesInZip<br />**Hex**:<br />80048486<br />**Número**:<br />-2147187578|Uno o más archivos en el archivo comprimido (.zip) o .cab no contienen datos. Compruebe los archivos e inténtelo de nuevo.|
> |**Nombre**:<br />EmptyHeaderColumn<br />**Hex**:<br />80040337<br />**Número**:<br />-2147220681|El encabezado de columna no puede estar vacío.|
> |**Nombre**:<br />EmptyHeaderRow<br />**Hex**:<br />80040366<br />**Número**:<br />-2147220634|La primera fila del archivo está vacía.|
> |**Nombre**:<br />EmptyImportFileRow<br />**Hex**:<br />80040347<br />**Número**:<br />-2147220665|Fila vacía.|
> |**Nombre**:<br />EmptyRecord<br />**Hex**:<br />80040373<br />**Número**:<br />-2147220621|El registro está vacío|
> |**Nombre**:<br />EmptySecretInDataSource<br />**Hex**:<br />80044818<br />**Número**:<br />-2147203048|Los secretos de origen de datos no se incluyen en soluciones. Necesitará editar los orígenes de datos para volver a agregar los secretos después de importar la solución.|
> |**Nombre**:<br />EmptySiteMapXml<br />**Hex**:<br />8004F402<br />**Número**:<br />-2147159038|El xml de Sitemap está vacío.|
> |**Nombre**:<br />EmptyXml<br />**Hex**:<br />80040202<br />**Número**:<br />-2147220990|XML vacío.|
> |**Nombre**:<br />EnableMobileOfflineDisableChangeTrackingError<br />**Hex**:<br />800609A2<br />**Número**:<br />-2147087966|Debe habilitar el seguimiento de cambios para esta entidad porque el cliente de Mobile Offline está habilitado.|
> |**Nombre**:<br />EnableRIFeatureNotAllowed<br />**Hex**:<br />80044279<br />**Número**:<br />-2147204487|Necesita privilegios de administrador del sistema para actualizar la información del inquilino de Información de relaciones.|
> |**Nombre**:<br />EndUserNotificationTypeNotValidForEmail<br />**Hex**:<br />8004D291<br />**Número**:<br />-2147167599|No se puede enviar correo electrónico para el tipo de EndUserNotification: {0}.|
> |**Nombre**:<br />EntitiesExceedMaxAllowed<br />**Hex**:<br />80060415<br />**Número**:<br />-2147089387|No puede cubrir más de cinco entidades en un flujo de proceso. Quite algunas entidades e inténtelo de nuevo.|
> |**Nombre**:<br />EntitiesInViewNotAvailableOffline<br />**Hex**:<br />80071125<br />**Número**:<br />-2147020507|Una o varias entidades a las que se hace referencia no están disponibles sin conexión.|
> |**Nombre**:<br />EntitiesInViewNotInProfile<br />**Hex**:<br />80071124<br />**Número**:<br />-2147020508|Una o varias entidades en esta vista no forman parte de este perfil.|
> |**Nombre**:<br />EntitlementAlreadyInactiveState<br />**Hex**:<br />80060615<br />**Número**:<br />-2147088875|No puede activar un derecho que se encuentra en el estado activo.|
> |**Nombre**:<br />EntitlementAlreadyInCanceledState<br />**Hex**:<br />80044208<br />**Número**:<br />-2147204600|No puede cancelar un derecho con el estado Cancelado.|
> |**Nombre**:<br />EntitlementAlreadyInDraftState<br />**Hex**:<br />80060614<br />**Número**:<br />-2147088876|No puede desactivar un derecho que se encuentra en el estado de borrador.|
> |**Nombre**:<br />EntitlementBlankTerms<br />**Hex**:<br />80060622<br />**Número**:<br />-2147088862|Los términos totales no pueden estar en blanco. Especifique un valor e inténtelo de nuevo.|
> |**Nombre**:<br />EntitlementChannelInvalidState<br />**Hex**:<br />80060603<br />**Número**:<br />-2147088893|Un término de canal de derecho no se puede crear, cambiar o eliminar cuando su derecho asociado no se encuentra en estado de borrador.|
> |**Nombre**:<br />EntitlementChannelWithoutEntitlementId<br />**Hex**:<br />80060612<br />**Número**:<br />-2147088878|Asocie el canal de derecho con un derecho o una plantilla de derecho.|
> |**Nombre**:<br />EntitlementEditDraft<br />**Hex**:<br />80060613<br />**Número**:<br />-2147088877|Solo puede editar un derecho de borrador.|
> |**Nombre**:<br />EntitlementInvalidRemainingTerms<br />**Hex**:<br />80060624<br />**Número**:<br />-2147088860|El número de términos restantes no puede ser mayor que el número de términos totales.|
> |**Nombre**:<br />EntitlementInvalidStartEndDate<br />**Hex**:<br />80060600<br />**Número**:<br />-2147088896|La fecha de inicio no puede ser posterior a la fecha de finalización|
> |**Nombre**:<br />EntitlementInvalidState<br />**Hex**:<br />80060601<br />**Número**:<br />-2147088895|No puede eliminar un derecho que está en estado activo o en espera|
> |**Nombre**:<br />EntitlementInvalidTerms<br />**Hex**:<br />80060604<br />**Número**:<br />-2147088892|Especifique un valor más alto para los términos totales con el fin de que los términos restantes no tengan valor negativo.|
> |**Nombre**:<br />EntitlementNotActiveInAssociationToCase<br />**Hex**:<br />80060616<br />**Número**:<br />-2147088874|No puede crear un caso para este derecho porque el derecho no se encuentra en estado activo.|
> |**Nombre**:<br />EntitlementTemplateTotalTerms<br />**Hex**:<br />80060620<br />**Número**:<br />-2147088864|Si el tipo de asignación es el número de casos, los términos totales no pueden ser un valor decimal. Especifique un número entero.|
> |**Nombre**:<br />EntitlementTotalTerms<br />**Hex**:<br />80060619<br />**Número**:<br />-2147088871|Si el tipo de asignación es el número de casos, los términos totales no pueden ser un valor decimal. Especifique un número entero.|
> |**Nombre**:<br />EntityCannotBeChildInCustomRelationship<br />**Hex**:<br />8004432D<br />**Número**:<br />-2147204307|Esta entidad no es válida como un secundario en una relación jerárquica personalizada o ya es un secundario de una relación jerárquica|
> |**Nombre**:<br />EntityCannotHaveOwnedByMeFilter<br />**Hex**:<br />80071136<br />**Número**:<br />-2147020490|La entidad '{0} en el perfil '{1}' tiene OwnedByMe establecido como True. Esta propiedad no es una propiedad válida para la entidad '{0}'.|
> |**Nombre**:<br />EntityCannotHaveOwnedByMyTeamFilter<br />**Hex**:<br />80071137<br />**Número**:<br />-2147020489|La entidad '{0} en el perfil '{1}' tiene OwnedByMyTeam establecido como True. Esta propiedad no es una propiedad válida para la entidad '{0}'.|
> |**Nombre**:<br />EntityCannotParticipateInEntityAssociation<br />**Hex**:<br />80044332<br />**Número**:<br />-2147204302|Esta entidad no puede participar en una asociación de entidades|
> |**Nombre**:<br />EntityDupCheckNotSupportedSystemWide<br />**Hex**:<br />80048431<br />**Número**:<br />-2147187663|La detección de duplicados no está habilitada para una o varias de las entidades seleccionadas. No se puede iniciar el trabajo de detección de duplicados.|
> |**Nombre**:<br />EntityExceedsMaxActiveBusinessProcessFlows<br />**Hex**:<br />80060420<br />**Número**:<br />-2147089376|La entidad {0} supera el número máximo de flujos de proceso de negocio activo. El límite es {1}.|
> |**Nombre**:<br />EntityFilterContainerMustNotBeNullFormatString<br />**Hex**:<br />80071132<br />**Número**:<br />-2147020494|No hay filtros especificados para la entidad '{0}'. Debe definir al menos un filtro|
> |**Nombre**:<br />EntityGroupNameOrEntityNamesMustBeProvided<br />**Hex**:<br />80060205<br />**Número**:<br />-2147089915|Falta el parámetro. Debe indicar EntityGroupName o EntityNames.|
> |**Nombre**:<br />EntityHasNoStateCode<br />**Hex**:<br />80047015<br />**Número**:<br />-2147192811|La entidad especificada no tiene un statecode.|
> |**Nombre**:<br />EntityInstanceIsNull<br />**Hex**:<br />80060444<br />**Número**:<br />-2147089340|Error al crear o actualizar proceso de negocios: instancia de entidad no puede ser nulo.|
> |**Nombre**:<br />EntityInstantiationFailed<br />**Hex**:<br />80040243<br />**Número**:<br />-2147220925|No se pudo crear una instancia de una entidad de servicio de instancia.|
> |**Nombre**:<br />EntityIsIntersect<br />**Hex**:<br />8004830F<br />**Número**:<br />-2147187953|La entidad especificada es una entidad de intersect|
> |**Nombre**:<br />EntityIsLocked<br />**Hex**:<br />80043b1d<br />**Número**:<br />-2147206371|La entidad ya está bloqueada.|
> |**Nombre**:<br />EntityIsNotBusinessProcessFlowEnabled<br />**Hex**:<br />80060421<br />**Número**:<br />-2147089375|La propiedad IsBusinessProcessEnabled de la etidad {0} es falsa.|
> |**Nombre**:<br />EntityIsNotCustomizable<br />**Hex**:<br />80047008<br />**Número**:<br />-2147192824|La entidad especificada no se puede personalizar|
> |**Nombre**:<br />EntityIsNotEnabledForExternalParty<br />**Hex**:<br />8006111B<br />**Número**:<br />-2147086053|No puede crear/actualizar un elemento de la parte externa asociado a una entidad no habilitada para parte externa.|
> |**Nombre**:<br />EntityIsNotEnabledForFollow<br />**Hex**:<br />8004F6A2<br />**Número**:<br />-2147158366|Esta entidad no está habilitada para su seguimiento. |
> |**Nombre**:<br />EntityIsNotEnabledForFollowUser<br />**Hex**:<br />8004F6A1<br />**Número**:<br />-2147158367|Esta entidad no está habilitada para su seguimiento. |
> |**Nombre**:<br />EntityIsUnlocked<br />**Hex**:<br />80043b1e<br />**Número**:<br />-2147206370|La entidad ya está desbloqueada.|
> |**Nombre**:<br />EntityKeyNameExists<br />**Hex**:<br />80060893<br />**Número**:<br />-2147088237|Ya existe una clave de entidad con el nombre {0} en la entidad {1}.|
> |**Nombre**:<br />EntityKeyNotDefined<br />**Hex**:<br />80060890<br />**Número**:<br />-2147088240|Los atributos de clave especificados no son una clave definida para la {0} entidad|
> |**Nombre**:<br />EntityKeyNotSupportedForSolutionAwareComponents<br />**Hex**:<br />8006089F<br />**Número**:<br />-2147088225|Las claves de entidad no son compatibles con la entidad {0} porque la entidad es un componente consciente de la solución|
> |**Nombre**:<br />EntityKeyWithSelectedAttributesExists<br />**Hex**:<br />80060894<br />**Número**:<br />-2147088236|Ya existe una clave de entidad con los atributos seleccionados en la entidad.|
> |**Nombre**:<br />EntityLimitExceeded<br />**Hex**:<br />80060200<br />**Número**:<br />-2147089920|MultiEntitySearch ha superado el límite de entidades definido para la organización.|
> |**Nombre**:<br />EntityLoopBeingCreated<br />**Hex**:<br />80040387<br />**Número**:<br />-2147220601|La creación de esta asociación jerárquica crearía un bucle en la jerarquía de esta entidad.|
> |**Nombre**:<br />EntityLoopExists<br />**Hex**:<br />80040386<br />**Número**:<br />-2147220602|Existe un bucle en la jerarquía de la entidad.|
> |**Nombre**:<br />EntityMetadataSyncFailed<br />**Hex**:<br />8005F238<br />**Número**:<br />-2147093960|Se produjeron problemas con las configuraciones del servidor.  Se ha producido un problema con los cambios de configuración del servidor.  No se puede cargar la aplicación, póngase en contacto con su administrador de Dynamics 365.|
> |**Nombre**:<br />EntityMetadataSyncFailedWithContinue<br />**Hex**:<br />8005F239<br />**Número**:<br />-2147093959|Se han producido dificultades con los cambios de configuración del servidor.  Puede continuar usando la aplicación con la configuración de una versión anterior, sin embargo, puede que tenga problemas con errores al guardar.  Póngase en contacto con el administrador de Dynamics 365. |
> |**Nombre**:<br />EntityNotEnabledForAutoCreatedAccessTeams<br />**Hex**:<br />80048334<br />**Número**:<br />-2147187916|Esta entidad no está habilitada para crear automáticamente equipos de acceso.|
> |**Nombre**:<br />EntityNotEnabledForCharts<br />**Hex**:<br />8004E00C<br />**Número**:<br />-2147164148|Los gráficos no están habilitados en el código de tipo de entidad principal especificado: {0}.|
> |**Nombre**:<br />EntityNotEnabledForThisDevice<br />**Hex**:<br />8005F200<br />**Número**:<br />-2147094016|Entidad no habilitada para ser vista en este dispositivo|
> |**Nombre**:<br />EntityNotRule<br />**Hex**:<br />8004E112<br />**Número**:<br />-2147163886|El nombre de colección no es una regla de periodicidad.|
> |**Nombre**:<br />EntityReferenceArgumentsNotBound<br />**Hex**:<br />80060395<br />**Número**:<br />-2147089515|Los argumentos necesarios de tipo EntityReference deben estar enlazados a alguna entidad.|
> |**Nombre**:<br />EntityReferenceLinkNull<br />**Hex**:<br />80048466<br />**Número**:<br />-2147187610|El enlace de referencia de entidad no puede ser nulo|
> |**Nombre**:<br />EntityRelationshipRoleCustomLabelsMissing<br />**Hex**:<br />80044328<br />**Número**:<br />-2147204312|Si un rol de relación de entidad tiene una opción de visualización de UseCustomLabels se deben proporcionar etiquetas personalizadas|
> |**Nombre**:<br />EntityRelationshipSchemaNameNotUnique<br />**Hex**:<br />8004432B<br />**Número**:<br />-2147204309|Ya existe una relación con el nombre especificado. Especifique un nombre exclusivo.|
> |**Nombre**:<br />EntityRelationshipSchemaNameRequired<br />**Hex**:<br />8004432A<br />**Número**:<br />-2147204310|Las relaciones entre entidades requieren un nombre.|
> |**Nombre**:<br />EntityTypeNotSupported<br />**Hex**:<br />80100008<br />**Número**:<br />-2146435064|La entidad {0} no admite este mensaje.|
> |**Nombre**:<br />EntityTypeSpecifiedForDashboard<br />**Hex**:<br />8004E30B<br />**Número**:<br />-2147163381|No se puede especificar un tipo de entidad para un panel.|
> |**Nombre**:<br />ErrorConnectingToDiscoveryService<br />**Hex**:<br />8004B066<br />**Número**:<br />-2147176346|Error al intentar conectar con el servicio de detección del cliente.|
> |**Nombre**:<br />ErrorConnectingToOrganizationService<br />**Hex**:<br />8004B068<br />**Número**:<br />-2147176344|Error al intentar conectar con el servicio de organización del cliente.|
> |**Nombre**:<br />ErrorDeleteStatementTextIsReferenced<br />**Hex**:<br />8004F203<br />**Número**:<br />-2147159549|Puesto que se hace referencia a una o varias declaraciones de script de la interfaz de usuario, no puede eliminar el texto de la declaración de script de la interfaz de usuario.|
> |**Nombre**:<br />ErrorFetchingBaseUrl<br />**Hex**:<br />80044290<br />**Número**:<br />-2147204464|No podemos obtener la dirección URL de base para el id. de organización {0}. Detalles de la excepción {1}|
> |**Nombre**:<br />ErrorFetchingRIProvisionStatus<br />**Hex**:<br />80044291<br />**Número**:<br />-2147204463|No podemos capturar el estado de aprovisionamiento de RI para el id. de organización {0}. Detalles de la excepción {1}|
> |**Nombre**:<br />ErrorGeneratingActionHub<br />**Hex**:<br />80071001<br />**Número**:<br />-2147020799|Se ha producido un error. Vuelva a intentarlo más tarde.|
> |**Nombre**:<br />ErrorGeneratingInvitation<br />**Hex**:<br />8004B013<br />**Número**:<br />-2147176429|Se ha producido un error interno al generar el token de invitación. Inténtelo más tarde.|
> |**Nombre**:<br />ErrorImportInvalidForPublishedScript<br />**Hex**:<br />8004F216<br />**Número**:<br />-2147159530|No se pueden guardar los datos en un script de interfaz de usuario publicado. Anule la publicación del script de la interfaz de usuario e inténtelo de nuevo.|
> |**Nombre**:<br />ErrorIncreate<br />**Hex**:<br />80040359<br />**Número**:<br />-2147220647|No se puede crear el registro de Microsoft Dynamics 365|
> |**Nombre**:<br />ErrorInDelete<br />**Hex**:<br />8004035a<br />**Número**:<br />-2147220646|No se puede eliminar el registro de Microsoft Dynamics 365.|
> |**Nombre**:<br />ErrorInFetchingEmailEngagementProvisioningStatus<br />**Hex**:<br />80050013<br />**Número**:<br />-2147155949|Error al obtener la característica de estado de aprovisionamiento de interacción por correo electrónico.|
> |**Nombre**:<br />ErrorInFieldWidthIncrease<br />**Hex**:<br />80044351<br />**Número**:<br />-2147204271|Se ha producido un error al aumentar el ancho de campo.|
> |**Nombre**:<br />ErrorInImportConfig<br />**Hex**:<br />80040323<br />**Número**:<br />-2147220701|No se puede procesar con importación masiva porque la configuración de la importación tiene algunos errores.|
> |**Nombre**:<br />ErrorInParseRow<br />**Hex**:<br />80040346<br />**Número**:<br />-2147220666|No se ha podido analizar la fila. Esto se suele deber a que la fila es demasiado larga.|
> |**Nombre**:<br />ErrorInSetState<br />**Hex**:<br />80040357<br />**Número**:<br />-2147220649|No se puede establecer el estado o la razón para el estado del registro de Microsoft Dynamics 365|
> |**Nombre**:<br />ErrorInStoringImportFile<br />**Hex**:<br />80048497<br />**Número**:<br />-2147187561|Se ha producido un error al almacenar el archivo de importación en la base de datos.|
> |**Nombre**:<br />ErrorInUnzip<br />**Hex**:<br />80048483<br />**Número**:<br />-2147187581|Se ha producido un error al extraer el archivo cargado comprimido (.zip) o .cab. Asegúrese de que el archivo no está protegido por contraseña e intente cargar el archivo de nuevo. Si este problema continúa, póngase en contacto con el administrador del sistema.|
> |**Nombre**:<br />ErrorInUnzipAlternate<br />**Hex**:<br />80048503<br />**Número**:<br />-2147187453|Se ha producido un error al extraer el archivo cargado comprimido (.zip) o .cab. Intente cargar el archivo de nuevo. Si el problema continúa, póngase en contacto con el administrador del sistema.|
> |**Nombre**:<br />ErrorInUpdate<br />**Hex**:<br />80040358<br />**Número**:<br />-2147220648|No se puede actualizar el registro de Microsoft Dynamics 365|
> |**Nombre**:<br />ErrorInvalidFileNameChars<br />**Hex**:<br />8004F214<br />**Número**:<br />-2147159532|Los nombres de archivo de Microsoft Excel no pueden contener ninguno de los caracteres siguientes: *  \ : > < | ? " /. Cambie el nombre del archivo utilizando caracteres válidos e inténtelo de nuevo.|
> |**Nombre**:<br />ErrorInvalidUIScriptImportFile<br />**Hex**:<br />8004F211<br />**Número**:<br />-2147159535|No se admite el tipo de archivo. Seleccione un archivo xml para la importación.|
> |**Nombre**:<br />ErrorMigrationProcessExcessOnServer<br />**Hex**:<br />8005F034<br />**Número**:<br />-2147094476|El servidor está ocupado con otros procesos de migración. Inténtelo más tarde.|
> |**Nombre**:<br />ErrorMimeTypeNullOrEmpty<br />**Hex**:<br />8004F215<br />**Número**:<br />-2147159531|El valor de propiedad MimeType del método UploadFromBase64DataUIScriptRequest es nulo o está vacío. Especifique un valor de propiedad válido e inténtelo de nuevo.|
> |**Nombre**:<br />ErrorNoActiveRoutingRuleExists<br />**Hex**:<br />8004F874<br />**Número**:<br />-2147157900|Actualmente no hay ninguna regla activa para enrutar este caso.|
> |**Nombre**:<br />ErrorNoQueryData<br />**Hex**:<br />8004F220<br />**Número**:<br />-2147159520|Se ha producido un error. O los datos no existen o no tiene suficientes privilegios para ver los datos. Póngase en contacto con el administrador del sistema para obtener ayuda.|
> |**Nombre**:<br />ErrorOnFeatureStatusChange<br />**Hex**:<br />80044289<br />**Número**:<br />-2147204471|No podemos habilitar o deshabilitar la característica {0} del Id. de la organización {1}. Detalles de la excepción {2}.|
> |**Nombre**:<br />ErrorOnGetRecord<br />**Hex**:<br />80044286<br />**Número**:<br />-2147204474|Error al obtener un registro para la tabla {0}. Detalles de la excepción {1}.|
> |**Nombre**:<br />ErrorOnGetRIProvisionStatus<br />**Hex**:<br />80044282<br />**Número**:<br />-2147204478|No podemos obtener el estado de aprovisionamiento de Información de relaciones para el id. de organización {0}. Detalles de la excepción {1}.|
> |**Nombre**:<br />ErrorOnGetRITenantEndPoint<br />**Hex**:<br />80044283<br />**Número**:<br />-2147204477|No podemos obtener la información de extremo del inquilino de Información de relaciones para el id. de organización {0}. Detalles de la excepción {1}.|
> |**Nombre**:<br />ErrorOnQryPropertyBagCollection<br />**Hex**:<br />80044287<br />**Número**:<br />-2147204473|La consulta no devolvió todas las columnas de {0}.|
> |**Nombre**:<br />ErrorOnStartOfRIProvision<br />**Hex**:<br />80044284<br />**Número**:<br />-2147204476|No podemos iniciar el aprovisionamiento para el id. de organización {0}. Detalles de la excepción {1}.|
> |**Nombre**:<br />ErrorOnTenantVerifyUpdate<br />**Hex**:<br />80044285<br />**Número**:<br />-2147204475|No podemos comprobar o actualizar la información de inquilino para el id. de organización {0}. Detalles de la excepción {1}.|
> |**Nombre**:<br />ErrorPropertyBagCollectionMissedColumn<br />**Hex**:<br />80044288<br />**Número**:<br />-2147204472|Falta la columna {0} de la tabla {1}.|
> |**Nombre**:<br />ErrorReactivatingComponentInstance<br />**Hex**:<br />8004F004<br />**Número**:<br />-2147160060|Después de recuperar una etiqueta, no hay ninguna etiqueta subyacente que reactivar.|
> |**Nombre**:<br />ErrorScriptCannotDeletePublishedScript<br />**Hex**:<br />8004F209<br />**Número**:<br />-2147159543|No se puede eliminar un script de la interfaz de usuario que se ha publicado. Debe anular la publicación primero.|
> |**Nombre**:<br />ErrorScriptCannotUpdatePublishedScript<br />**Hex**:<br />8004F213<br />**Número**:<br />-2147159533|No se puede actualizar un script de la interfaz de usuario que se ha publicado. Debe anular la publicación primero.|
> |**Nombre**:<br />ErrorScriptFileParse<br />**Hex**:<br />8004F212<br />**Número**:<br />-2147159534|Error en el análisis del archivo XML.|
> |**Nombre**:<br />ErrorScriptInitialStatementNotInScript<br />**Hex**:<br />8004F207<br />**Número**:<br />-2147159545|La declaración inicial de este script no pertenece a este script.|
> |**Nombre**:<br />ErrorScriptInitialStatementNotRoot<br />**Hex**:<br />8004F208<br />**Número**:<br />-2147159544|La declaración inicial debe ser la declaración de raíz y no puede tener definida una declaración anterior.|
> |**Nombre**:<br />ErrorScriptLanguageNotInstalled<br />**Hex**:<br />8004F206<br />**Número**:<br />-2147159546|No se admite el idioma especificado en la instalación de Dynamics 365. Compruebe con el administrador del sistema en la lista de idiomas "habilitados".|
> |**Nombre**:<br />ErrorScriptPublishMalformedScript<br />**Hex**:<br />8004F20B<br />**Número**:<br />-2147159541|No se puede publicar el script de interfaz de usuario seleccionado. El script de la interfaz de usuario contiene una o varias rutas que no terminan en un nodo de acción end-script o next-script. Corrija las rutas de acceso correctas e intente volver a publicar.|
> |**Nombre**:<br />ErrorScriptPublishMissingInitialStatement<br />**Hex**:<br />8004F20A<br />**Número**:<br />-2147159542|No se puede publicar el script de interfaz de usuario seleccionado. Especifique un valor para "Primer número de declaración" e intente volver a publicar.|
> |**Nombre**:<br />ErrorScriptSessionCannotCreateForDraftScript<br />**Hex**:<br />8004F204<br />**Número**:<br />-2147159548|No se puede crear una sesión de script de la interfaz de usuario para un script de interfaz de usuario que no se ha publicado.|
> |**Nombre**:<br />ErrorScriptSessionCannotSetStateForDraftScript<br />**Hex**:<br />8004F20D<br />**Número**:<br />-2147159539|No se puede definir el estado de una sesión de script de la interfaz de usuario para un script de interfaz de usuario que no se ha publicado.|
> |**Nombre**:<br />ErrorScriptSessionCannotUpdateForDraftScript<br />**Hex**:<br />8004F205<br />**Número**:<br />-2147159547|No se puede actualizar una sesión de script de la interfaz de usuario para un script de interfaz de usuario que no se ha publicado.|
> |**Nombre**:<br />ErrorScriptStatementResponseTypeOnlyForPrompt<br />**Hex**:<br />8004F20E<br />**Número**:<br />-2147159538|No puede asociar el tipo de control de respuesta para una declaración que no es un mensaje.|
> |**Nombre**:<br />ErrorScriptUnpublishActiveScript<br />**Hex**:<br />8004F20C<br />**Número**:<br />-2147159540|Este script se está usando y tiene sesiones activas (razón para el estado = incompleto). Finalice las sesiones activas (es decir, motivo de estado = cancelado) e intenta anular la publicación de nuevo.|
> |**Nombre**:<br />ErrorsInEmailRouterMigrationFiles<br />**Hex**:<br />8005F032<br />**Número**:<br />-2147094478|Archivo o archivos no válidos para migración de E-mail Router|
> |**Nombre**:<br />ErrorsInImportFiles<br />**Hex**:<br />8004034a<br />**Número**:<br />-2147220662|Archivo no válido para importar|
> |**Nombre**:<br />ErrorsInProfileRuleWorkflowActivation<br />**Hex**:<br />80061119<br />**Número**:<br />-2147086055|No puede activar esta regla de perfil. No tiene los permisos necesarios en los tipos de registro a los que hace referencia esta regla de perfil.|
> |**Nombre**:<br />ErrorsInSlaWorkflowActivation<br />**Hex**:<br />80048535<br />**Número**:<br />-2147187403|No puede activar este contrato de nivel de servicio (SLA). No tiene los permisos necesarios en los tipos de registro a los que hace referencia este SLA.|
> |**Nombre**:<br />ErrorsInWorkflowDefinition<br />**Hex**:<br />80048455<br />**Número**:<br />-2147187627|El flujo de trabajo seleccionado tiene errores y no se puede publicar. Abra el flujo de trabajo, quite los errores e inténtelo de nuevo.|
> |**Nombre**:<br />ErrorStatementDeleteOnlyForDraftScript<br />**Hex**:<br />8004F210<br />**Número**:<br />-2147159536|No se puede eliminar una declaración de script de la interfaz de usuario que no sea un borrador.|
> |**Nombre**:<br />ErrorStatementOnlyForDraftScript<br />**Hex**:<br />8004F20F<br />**Número**:<br />-2147159537|No se puede crear una declaración de script de la interfaz de usuario que no sea un borrador.|
> |**Nombre**:<br />ErrorTemplate<br />**Hex**:<br />80050102<br />**Número**:<br />-2147155710|{0}|
> |**Nombre**:<br />ErrorUIScriptPromptMissing<br />**Hex**:<br />8004F221<br />**Número**:<br />-2147159519|El cuadro de diálogo que se está activando no tiene ningún mensaje o respuesta.|
> |**Nombre**:<br />ErrorUpdateStatementTextIsReferenced<br />**Hex**:<br />8004F202<br />**Número**:<br />-2147159550|Puesto que se hace referencia a uno o varios scripts de la interfaz de usuario no publicados, no puede actualizar el texto de la declaración de este script de la interfaz de usuario.|
> |**Nombre**:<br />ErrorUploadingReport<br />**Hex**:<br />80048298<br />**Número**:<br />-2147188072|Se ha producido un error al intentar agregar el informe a Microsoft Dynamics 365. Intente agregar el informe de nuevo. Si este problema continúa, póngase en contacto con el administrador del sistema.|
> |**Nombre**:<br />EventNotSupportedForBusinessRule<br />**Hex**:<br />80060001<br />**Número**:<br />-2147090431|Evento {0} no se admite para la regla de negocio del cliente.|
> |**Nombre**:<br />EventTypeAndControlNameAreMismatched<br />**Hex**:<br />80060003<br />**Número**:<br />-2147090429|Esta combinación de tipo de evento y nombre de control no se esperaba|
> |**Nombre**:<br />EvoStsAuthorizationServerRecordCreationFailureException<br />**Hex**:<br />80071006<br />**Número**:<br />-2147020794|Error en la operación de la base de datos al crear el registro de autorización para Evo STS.|
> |**Nombre**:<br />ExceedCustomEntityQuota<br />**Hex**:<br />8004b042<br />**Número**:<br />-2147176382|Se ha llegado al límite de entidades personalizadas.|
> |**Nombre**:<br />ExceededLimitForAllowedFacetableAttributes<br />**Hex**:<br />80060306<br />**Número**:<br />-2147089658|No se pueden establecer facetas de búsqueda de usuario de la entidad {0} porque el límite de atributos facetable permitido es 4. Quite algunos atributos para continuar.|
> |**Nombre**:<br />ExceededNumberOfRecordsCanFollow<br />**Hex**:<br />8004F6A0<br />**Número**:<br />-2147158368|Ha superado el número de registros que puede seguir. Deje de seguir algunos registros para comenzarlos a seguir de nuevo.|
> |**Nombre**:<br />ExceededRollupFieldsPerEntityQuota<br />**Hex**:<br />80060543<br />**Número**:<br />-2147089085|No se puede agregar un campo consolidado con el nombre {4} que tiene Id {3} para la entidad con nombre {2} e Id {1}. Ha alcanzado el número máximo de {0} permitido para este tipo de registro.|
> |**Nombre**:<br />ExceededRollupFieldsPerOrgQuota<br />**Hex**:<br />80060542<br />**Número**:<br />-2147089086|No puede agregar un campo consolidado. Ha alcanzado el número máximo de {0} permitido para la organización.|
> |**Nombre**:<br />ExcelFileNotFound<br />**Hex**:<br />80060805<br />**Número**:<br />-2147088379|No se encontró el archivo solicitado.|
> |**Nombre**:<br />ExcelOnlineNotUpdated<br />**Hex**:<br />80060808<br />**Número**:<br />-2147088376|El archivo de Excel Online {0} no fue actualizado por el servidor Wopi en el tiempo de espera especificado.|
> |**Nombre**:<br />ExchangeAutodiscoverError<br />**Hex**:<br />8004503A<br />**Número**:<br />-2147200966|La detección automática no encuentra la dirección URL de los Servicios Web Exchange para el buzón especificado. Compruebe que la dirección del buzón y las credenciales suministradas son correctas y que Autodiscover está habilitado y se ha configurado correctamente.|
> |**Nombre**:<br />ExchangeCardAttributeMissingInResponseException<br />**Hex**:<br />80071102<br />**Número**:<br />-2147020542|Atributo no presente en la respuesta oData de Exchange.|
> |**Nombre**:<br />ExchangeCardInvalidResponseFormatException<br />**Hex**:<br />80071104<br />**Número**:<br />-2147020540|Formato de respuesta no válido.|
> |**Nombre**:<br />ExchangeCardS2SSetupFailureException<br />**Hex**:<br />80071105<br />**Número**:<br />-2147020539|No se ha configurado la autenticación de servidor a servidor con Exchange para la Tarjeta de acción.|
> |**Nombre**:<br />ExchangeOptinNotEnabled<br />**Hex**:<br />80071106<br />**Número**:<br />-2147020538|Exchange optin no está habilitado.|
> |**Nombre**:<br />ExchangeRateOfBaseCurrencyNotUpdatable<br />**Hex**:<br />80048cf5<br />**Número**:<br />-2147185419|No se puede modificar el tipo de cambio de la divisa base.|
> |**Nombre**:<br />ExecuteNotOnDemandWorkflow<br />**Hex**:<br />80045046<br />**Número**:<br />-2147200954|El flujo de trabajo debe marcarse como a petición o flujo de trabajo secundario.|
> |**Nombre**:<br />ExecuteUnpublishedWorkflow<br />**Hex**:<br />80045047<br />**Número**:<br />-2147200953|El flujo de trabajo debe estar en estado publicado.|
> |**Nombre**:<br />ExistingExternalReport<br />**Hex**:<br />80040488<br />**Número**:<br />-2147220344|No se puede ha podido publicar el informe para uso externo porque ya existe un informe del mismo nombre. Elimine ese informe en SQL Server Reporting Services o cambie el nombre de este informe e inténtelo de nuevo.|
> |**Nombre**:<br />ExistingParentalRelationship<br />**Hex**:<br />80048205<br />**Número**:<br />-2147188219|Ya existe una relación jerárquica.|
> |**Nombre**:<br />ExpansionRequestIsOutsideExpansionWindow<br />**Hex**:<br />8004E10C<br />**Número**:<br />-2147163892|La serie ya se ha ampliado para CutOffWindow.|
> |**Nombre**:<br />ExpectingAtLeastOneBusinessRuleStep<br />**Hex**:<br />80060011<br />**Número**:<br />-2147090415|Debe haber un mínimo de un solo paso de regla de negocio.|
> |**Nombre**:<br />ExpiredAuthTicket<br />**Hex**:<br />8004A101<br />**Número**:<br />-2147180287|El vale especificado para la autenticación ha expirado|
> |**Nombre**:<br />ExpiredEntitlementActivate<br />**Hex**:<br />80060617<br />**Número**:<br />-2147088873|No puede activar un derecho expirado.|
> |**Nombre**:<br />ExpiredKey<br />**Hex**:<br />8004A106<br />**Número**:<br />-2147180282|La clave especificada para calcular el que valor de hash ha expirado; solo son válidas las claves activas.  Clave expirada: {0}.|
> |**Nombre**:<br />ExpiredOAuthToken<br />**Hex**:<br />80041d52<br />**Número**:<br />-2147213998|El token OAuth ha expirado|
> |**Nombre**:<br />ExpiredVersionStamp<br />**Hex**:<br />80044352<br />**Número**:<br />-2147204270|La marca de versión asociada al cliente ha expirado. Vuelva a realizar una sincronización completa.|
> |**Nombre**:<br />ExportAttributeMapException<br />**Hex**:<br />80044415<br />**Número**:<br />-2147204075|Error al exportar AttributeMap desde el atributo {0} a {1} en EntityMap de la entidad {2} a {3} durante la exportación de la solución. AttributeMapId = {4}, EntityMapId = {5}|
> |**Nombre**:<br />ExportDefaultAsPackagedError<br />**Hex**:<br />80048048<br />**Número**:<br />-2147188664|La solución predeterminada no se puede exportar como un paquete.|
> |**Nombre**:<br />ExportEntityMapException<br />**Hex**:<br />80044416<br />**Número**:<br />-2147204074|Error al exportar EntityMap desde la entidad {0} a {1} durante la exportación de la solución. EntityMapId = {2}|
> |**Nombre**:<br />ExportKeyAttributeInvalidPrefix<br />**Hex**:<br />800608AD<br />**Número**:<br />-2147088211|Exportar atributo clave {0} para componente {1} debe comenzar con un prefijo de personalización válido.|
> |**Nombre**:<br />ExportKeyAttributeNotBeginWithLetterOrNonAlphaNumericCharacters<br />**Hex**:<br />800608AB<br />**Número**:<br />-2147088213|Exportar atributo clave {0} para componente {1} debe comenzar con una letra y solo constar de caracteres alfanuméricos y subrayados.|
> |**Nombre**:<br />ExportKeyAttributeValuesIncorrectNumber<br />**Hex**:<br />800608AC<br />**Número**:<br />-2147088212|Número incorrecto de valores de atributo de clave de exportación para clave de exportación {0} por entidad {1}.|
> |**Nombre**:<br />ExportKeyNotSupported<br />**Hex**:<br />800608A8<br />**Número**:<br />-2147088216|Las claves de exportación no son compatibles con la entidad {0} porque las claves de exportación no son compatibles|
> |**Nombre**:<br />ExportKeyNotSupportedForMaxAttributes<br />**Hex**:<br />800608AA<br />**Número**:<br />-2147088214|No se puede crear la clave de exportación para la entidad {0} porque la clave excede {1} atributos|
> |**Nombre**:<br />ExportKeyNotSupportedForNonCustomizableComponents<br />**Hex**:<br />800608A7<br />**Número**:<br />-2147088217|Las claves de exportación no son compatibles con la entidad {0} porque la entidad no es personalizable|
> |**Nombre**:<br />ExportKeyNotSupportedForNonSolutionAwareComponents<br />**Hex**:<br />800608A6<br />**Número**:<br />-2147088218|Las claves de exportación no son compatibles con la entidad {0} porque la entidad no es un componente consciente de la solución|
> |**Nombre**:<br />ExportManagedSolutionError<br />**Hex**:<br />80048036<br />**Número**:<br />-2147188682|Se ha producido un error durante la exportación de una solución. La solución administrada no puede ser exportada.|
> |**Nombre**:<br />ExportMissingSolutionError<br />**Hex**:<br />80048037<br />**Número**:<br />-2147188681|Se ha producido un error durante la exportación de una solución. La solución no existe en el sistema.|
> |**Nombre**:<br />ExportSolutionError<br />**Hex**:<br />80048035<br />**Número**:<br />-2147188683|Error durante la exportación de una solución.|
> |**Nombre**:<br />ExportToExcelOnlineFeatureNotEnabled<br />**Hex**:<br />80060804<br />**Número**:<br />-2147088380|La exportación a la función de Excel Online no está habilitada.|
> |**Nombre**:<br />ExportToXlsxFeatureNotEnabled<br />**Hex**:<br />800608C1<br />**Número**:<br />-2147088191|La exportación a la función de archivos Excel no está habilitada.|
> |**Nombre**:<br />ExpressionNotSupportedForEditor<br />**Hex**:<br />80060004<br />**Número**:<br />-2147090428|Regla, se incluye una expresión que no se admite el Editor.|
> |**Nombre**:<br />ExternalNameExists<br />**Hex**:<br />80046F8F<br />**Número**:<br />-2147192945|Ya existe una entidad con el nombre especificado para el origen de datos - {0}. Especifique un nuevo nombre externo.|
> |**Nombre**:<br />ExternalSearchAttributeLimitExceeded<br />**Hex**:<br />80060300<br />**Número**:<br />-2147089664|Se ha alcanzado el número máximo de campos indexados. Actualice la configuración de Búsqueda por relevancia para reducir el número total de campos indexados {1} debajo de {0}.|
> |**Nombre**:<br />ExtraPartyInformation<br />**Hex**:<br />80040316<br />**Número**:<br />-2147220714|No se debe proporcionar información adicional para esta operación.|
> |**Nombre**:<br />FailedToDeserializeAsyncOperationData<br />**Hex**:<br />80044304<br />**Número**:<br />-2147204348|No se pueden deserializar los datos de la operación asincŕonica.|
> |**Nombre**:<br />FailedToFindDependentConnectorsForModernFlow<br />**Hex**:<br />80060475<br />**Número**:<br />-2147089291|No se pudo encontrar ninguno de los conectores personalizados dependientes del Modern Flow actual.|
> |**Nombre**:<br />FailedToGetNetworkServiceName<br />**Hex**:<br />80047103<br />**Número**:<br />-2147192573|No se puede obtener el nombre localizado de cuenta NetworkService|
> |**Nombre**:<br />FailedToLoadAssembly<br />**Hex**:<br />8004024e<br />**Número**:<br />-2147220914|No se pudo cargar el ensamblado|
> |**Nombre**:<br />FailedToScheduleActivity<br />**Hex**:<br />80047000<br />**Número**:<br />-2147192832|Error al programar actividad.|
> |**Nombre**:<br />FailToDeleteConnectorFromExternalPartner<br />**Hex**:<br />80072601<br />**Número**:<br />-2147015167|No se puede eliminar el conector de destino de un asociado externo.|
> |**Nombre**:<br />FallbackCardFormDeactivation<br />**Hex**:<br />8004F664<br />**Número**:<br />-2147158428|No se puede completar esta operación. Debe tener al menos un formulario de tarjeta activo.|
> |**Nombre**:<br />FallbackFormDeactivation<br />**Hex**:<br />8004F661<br />**Número**:<br />-2147158431|No se puede completar esta operación. Debe tener al menos un formulario principal activo.|
> |**Nombre**:<br />FallbackFormDeletion<br />**Hex**:<br />8004F654<br />**Número**:<br />-2147158444|No puede eliminar este formulario porque es el único formulario de reserva del tipo {0} para la entidad {1}. Cada entidad debe tener al menos un formulario de reserva para cada tipo de formulario.|
> |**Nombre**:<br />FallbackMainInteractionCentricFormDeactivation<br />**Hex**:<br />8004F666<br />**Número**:<br />-2147158426|No se puede completar esta operación. Debe tener al menos un formulario MainInteractionCentric activo.|
> |**Nombre**:<br />FallbackQuickFormDeactivation<br />**Hex**:<br />8004F665<br />**Número**:<br />-2147158427|No se puede completar esta operación. Debe tener al menos un formulario rápido activo.|
> |**Nombre**:<br />FaxNoData<br />**Hex**:<br />80043516<br />**Número**:<br />-2147207914|No se puede enviar el fax porque no hay datos para enviar. Especifique al menos uno de los siguientes valores: una portada, datos adjuntos de fax, una descripción de fax.|
> |**Nombre**:<br />FaxNoSupport<br />**Hex**:<br />80043517<br />**Número**:<br />-2147207913|No se puede enviar el fax porque no se permite este tipo de datos adjuntos o no admite impresión virtual en un dispositivo de fax.|
> |**Nombre**:<br />FaxSendBlocked<br />**Hex**:<br />80043510<br />**Número**:<br />-2147207920|El destinatario está marcado para que no se le envíen faxes.|
> |**Nombre**:<br />FaxServiceNotRunning<br />**Hex**:<br />80043511<br />**Número**:<br />-2147207919|El Servicio de fax Microsoft Windows no se está ejecutando o no está instalado.|
> |**Nombre**:<br />FeatureNotEnabled<br />**Hex**:<br />80061113<br />**Número**:<br />-2147086061|Esta operación no se pudo completar porque esta característica no está habilitada para su organización.|
> |**Nombre**:<br />FederatedEndpointError<br />**Hex**:<br />80044505<br />**Número**:<br />-2147203835|El punto de conexión ADFS de nombre de usuario está habilitado, lo que está bloqueando el acceso al punto de conexión de autenticación previsto.|
> |**Nombre**:<br />FeedbackFeatureNotEnabled<br />**Hex**:<br />80061770<br />**Número**:<br />-2147084432|La característica comentarios no está habilitada.|
> |**Nombre**:<br />FeedbackMinMaxRequired<br />**Hex**:<br />80061772<br />**Número**:<br />-2147084430|Es necesario un valor máximo y mínimo.|
> |**Nombre**:<br />FeedbackMinRatingValue<br />**Hex**:<br />80061774<br />**Número**:<br />-2147084428|El valor de clasificación mínimo enviado {0} tiene que ser menor que el valor de clasificación máximo enviado {1}.|
> |**Nombre**:<br />FeedbackRatingValue<br />**Hex**:<br />80061773<br />**Número**:<br />-2147084429|La clasificación tiene que ser un valor entre {0} y {1}.|
> |**Nombre**:<br />FetchDataSetQueryTimeout<br />**Hex**:<br />8005E00E<br />**Número**:<br />-2147098610|La consulta del conjunto de datos de Fetch ha superado el tiempo de espera después de {0} segundos. Aumente el tiempo de espera de la consulta e inténtelo de nuevo.|
> |**Nombre**:<br />FieldLevelSecurityNotSupported<br />**Hex**:<br />80044817<br />**Número**:<br />-2147203049|La seguridad de nivel de campo no es compatible con una entidad virtual.|
> |**Nombre**:<br />FileContentIsNull<br />**Hex**:<br />80090004<br />**Número**:<br />-2146893820|El contenido del archivo no puede ser NULL.|
> |**Nombre**:<br />FileInUse<br />**Hex**:<br />80048837<br />**Número**:<br />-2147186633|No se pudo leer el archivo porque lo está usando otra aplicación.|
> |**Nombre**:<br />FileNotFound<br />**Hex**:<br />80048440<br />**Número**:<br />-2147187648|No se encontró el archivo adjunto.|
> |**Nombre**:<br />FilePickerErrorApplicationInSnapView<br />**Hex**:<br />8005F20D<br />**Número**:<br />-2147094003|Vuelva a intentarlo. Si el problema persiste, busque alguna solución en {0} o póngase en contacto con el administrador de {#Brand_CRM} de su organización. Finalmente, puede contactar {1}.|
> |**Nombre**:<br />FilePickerErrorAttachmentTypeBlocked<br />**Hex**:<br />8005F204<br />**Número**:<br />-2147094012|Vuelva a intentarlo. Si el problema persiste, busque alguna solución en {0} o póngase en contacto con el administrador de {#Brand_CRM} de su organización. Finalmente, puede contactar {1}.|
> |**Nombre**:<br />FilePickerErrorFileSizeBreached<br />**Hex**:<br />8005F205<br />**Número**:<br />-2147094011|Vuelva a intentarlo. Si el problema persiste, busque alguna solución en {0} o póngase en contacto con el administrador de {#Brand_CRM} de su organización. Finalmente, puede contactar {1}.|
> |**Nombre**:<br />FilePickerErrorFileSizeCannotBeZero<br />**Hex**:<br />8005F206<br />**Número**:<br />-2147094010|Vuelva a intentarlo. Si el problema persiste, busque alguna solución en {0} o póngase en contacto con el administrador de {#Brand_CRM} de su organización. Finalmente, puede contactar {1}.|
> |**Nombre**:<br />FilePickerErrorUnableToOpenFile<br />**Hex**:<br />8005F207<br />**Número**:<br />-2147094009|Vuelva a intentarlo. Si el problema persiste, busque alguna solución en {0} o póngase en contacto con el administrador de {#Brand_CRM} de su organización. Finalmente, puede contactar {1}.|
> |**Nombre**:<br />FileReadError<br />**Hex**:<br />80048437<br />**Número**:<br />-2147187657|Error al leer el archivo del sistema de archivos. Asegúrese de que tiene permiso de lectura para este archivo y, después, intente migrar el archivo de nuevo.|
> |**Nombre**:<br />FileSizeExceeded<br />**Hex**:<br />80071026<br />**Número**:<br />-2147020762|No se pueden copiar los documentos. El archivo seleccionado supera el límite de tamaño máximo de 128 MB.|
> |**Nombre**:<br />FileSizeExceededForNonChunkedRequest<br />**Hex**:<br />80090001<br />**Número**:<br />-2146893823|El tamaño máximo de archivo permitido para {0} es de [{1}] MB. Archivo de [{2} MB] de tamaño solo puede ser {0}ed usando un trozo preparado {0}.|
> |**Nombre**:<br />FileStoreFeatureNotEnabled<br />**Hex**:<br />80072520<br />**Número**:<br />-2147015392|Característica no habilitada para esta organización|
> |**Nombre**:<br />FileTypeNotSupported<br />**Hex**:<br />800609B4<br />**Número**:<br />-2147087948|No se admite el tipo de archivo especificado como plantilla.|
> |**Nombre**:<br />FilteredDuetoAntiSpam<br />**Hex**:<br />80040325<br />**Número**:<br />-2147220699|Este cliente está filtrado debido a la configuración contra correo no deseado|
> |**Nombre**:<br />FilteredDuetoInactiveState<br />**Hex**:<br />8004032a<br />**Número**:<br />-2147220694|Este cliente está filtrado debido a un estado de inactividad.|
> |**Nombre**:<br />FilteredDuetoMissingEmailAddress<br />**Hex**:<br />8004032e<br />**Número**:<br />-2147220690|Este cliente está filtrado debido a que falta la dirección de correo electrónico.|
> |**Nombre**:<br />FinalMergedEntityIsNull<br />**Hex**:<br />80060443<br />**Número**:<br />-2147089341|Error al crear o actualizar proceso de negocios: entidad combinada final no puede ser nulo.|
> |**Nombre**:<br />FirstStageIdInTraversedPathDoesNotMatchFirstStageIdInBusinessProcess<br />**Hex**:<br />80060456<br />**Número**:<br />-2147089322|El identificador de primera fase en ruta atravesada '{0}' no coincide con el identificador de la primera fase en proceso de negocio '{1}'. Póngase en contacto con el administrador del sistema.|
> |**Nombre**:<br />FiscalPeriodGoalMissingInfo<br />**Hex**:<br />80044903<br />**Número**:<br />-2147202813|Debe establecerse el atributo de período fiscal para un objetivo de tipo de período fiscal.|
> |**Nombre**:<br />FiscalSettingsAlreadyUpdated<br />**Hex**:<br />80043809<br />**Número**:<br />-2147207159|La configuración fiscal ya se han actualizado. Solo se pueden actualizar una vez.|
> |**Nombre**:<br />FlowIsNotActive<br />**Hex**:<br />80060469<br />**Número**:<br />-2147089303|El flujo moderno debe estar activo para utilizarse en un paso de flujo.|
> |**Nombre**:<br />FlowMissingRecord<br />**Hex**:<br />80050262<br />**Número**:<br />-2147155358|Debe seleccionar al menos un registro para desencadenar este flujo.|
> |**Nombre**:<br />FlowServiceClientError<br />**Hex**:<br />80060467<br />**Número**:<br />-2147089305|Error de cliente de flujo devuelto con código de estado "{0}" y detalles "{1}".|
> |**Nombre**:<br />FlowTriggerNotificationDisabled<br />**Hex**:<br />80072342<br />**Número**:<br />-2147015870|Las notificaciones de desencadenador de flujo están deshabilitados para la organización.|
> |**Nombre**:<br />FlowTriggerNotificationFailed<br />**Hex**:<br />80072341<br />**Número**:<br />-2147015871|La llamada de notificación de desencadenador de flujo falló durante la publicación de http. Compruebe la excepción para obtener más detalles.|
> |**Nombre**:<br />FolderDoesNotExist<br />**Hex**:<br />80060901<br />**Número**:<br />-2147088127|La carpeta no existe.|
> |**Nombre**:<br />Forbidden<br />**Hex**:<br />8005F102<br />**Número**:<br />-2147094270|El servidor rechaza completar la solicitud.|
> |**Nombre**:<br />FormDoesNotExist<br />**Hex**:<br />80048406<br />**Número**:<br />-2147187706|El formulario no existe|
> |**Nombre**:<br />FormTransitionError<br />**Hex**:<br />80040242<br />**Número**:<br />-2147220926|La importación ha fallado porque el sistema no puede pasar el formulario de entidad {0} de no administrado a administrado. Agregue al menos un componente completo (raíz) a la solución administrada e intente importar de nuevo.|
> |**Nombre**:<br />ForwardMailboxCannotAssociateWithUser<br />**Hex**:<br />8005E207<br />**Número**:<br />-2147098105|No es posible crear un buzón de enrutamiento para un usuario o cola específico.  Quite el campo correspodiente e inténtelo de nuevo.|
> |**Nombre**:<br />ForwardMailboxEmailAddressRequired<br />**Hex**:<br />8005E211<br />**Número**:<br />-2147098095|La dirección de correo electrónico es un campo obligatorio para un buzón de enrutamiento.|
> |**Nombre**:<br />ForwardMailboxUnexpectedIncomingDeliveryMethod<br />**Hex**:<br />8005E212<br />**Número**:<br />-2147098094|El método de entrega entrante para un buzón de enrutamiento solo se puede establecer en ninguno o enrutador.|
> |**Nombre**:<br />ForwardMailboxUnexpectedOutgoingDeliveryMethod<br />**Hex**:<br />8005E213<br />**Número**:<br />-2147098093|El método de entrega saliente para un buzón de enrutamiento solo se puede establecer en ninguno.|
> |**Nombre**:<br />GenericActiveDirectoryError<br />**Hex**:<br />80041d37<br />**Número**:<br />-2147214025|Error de Active Directory.|
> |**Nombre**:<br />GenericAzureActiveDirectoryError<br />**Hex**:<br />80041d54<br />**Número**:<br />-2147213996|Error de Azure Active Directory.|
> |**Nombre**:<br />GenericImportTranslationsError<br />**Hex**:<br />80060752<br />**Número**:<br />-2147088558|Se encontraron errores al procesar el archivo de importación de traducciones.|
> |**Nombre**:<br />GenericManagedPropertyFailure<br />**Hex**:<br />8004F026<br />**Número**:<br />-2147160026|La evaluación del componente actual (nombre{0}, id={1}) en la operación actual ({2}) ha dado error durante al menos una evaluación de condición: {3}|
> |**Nombre**:<br />GenericMetadataSyncFailed<br />**Hex**:<br />8005F246<br />**Número**:<br />-2147093946|Lo sentimos, se ha producido un error. Vuelva a intentarlo o reinicie la aplicación.|
> |**Nombre**:<br />GenericMetadataSyncFailedWithContinue<br />**Hex**:<br />8005F247<br />**Número**:<br />-2147093945|Lo sentimos, algo ha fallado al descargar los cambios de la configuración de servidor.  Puede continuar usando la aplicación con la configuración de una versión anterior, sin embargo, puede que tenga problemas con errores al guardar.  Si continúa este problema, póngase en contacto con su administrador de Dynamics 365 y proporcione la información disponible cuando elija 'obtener más información'.|
> |**Nombre**:<br />GenericTransformationInvocationError<br />**Hex**:<br />8004037b<br />**Número**:<br />-2147220613|La transformación devuelve datos no válidos.|
> |**Nombre**:<br />GetOnPolymorphicAttributeError<br />**Hex**:<br />80072532<br />**Número**:<br />-2147015374|No se puede consultar por {0} en {1}|
> |**Nombre**:<br />GetPhotoFromGalleryFailed<br />**Hex**:<br />8005F208<br />**Número**:<br />-2147094008|Vuelva a intentarlo. Si el problema persiste, busque alguna solución en {0} o póngase en contacto con el administrador de {#Brand_CRM} de su organización. Finalmente, puede contactar {1}.|
> |**Nombre**:<br />GetTenantIdFailure<br />**Hex**:<br />80071109<br />**Número**:<br />-2147020535|Error producido al obtener TenantId.|
> |**Nombre**:<br />GoalAttributeAlreadyMapped<br />**Hex**:<br />80044807<br />**Número**:<br />-2147203065|El detalle de la métrica del atributo de objetivo especificado ya existe.|
> |**Nombre**:<br />GoalMissingPeriodTypeInfo<br />**Hex**:<br />80044908<br />**Número**:<br />-2147202808|El tipo de período de objetivo debe ser especificado cuando se crea un objetivo. Este campo no puede ser nulo.|
> |**Nombre**:<br />GoalPercentageAchievedValueOutOfRange<br />**Hex**:<br />8004F682<br />**Número**:<br />-2147158398|El valor de porcentaje logrado se ha establecido en 0 porque el valor calculado no está en el intervalo permitido.|
> |**Nombre**:<br />GoOfflineBCPFileSize<br />**Hex**:<br />80044224<br />**Número**:<br />-2147204572|El cliente no puede descargar el archivo BCP. Póngase en contacto con el administrador del sistema para obtener asistencia e intente desconectarse de nuevo.|
> |**Nombre**:<br />GoOfflineDbSizeLimit<br />**Hex**:<br />80044222<br />**Número**:<br />-2147204574|Ha alcanzado el límite de almacenamiento de su base de datos sin conexión. Debe reducir la cantidad de datos adquiridos sin conexión cambiando los grupos de datos locales.|
> |**Nombre**:<br />GoOfflineEmptyFileForDelete<br />**Hex**:<br />80044230<br />**Número**:<br />-2147204560|El archivo de datos para eliminar está vacío.|
> |**Nombre**:<br />GoOfflineFailedMoveData<br />**Hex**:<br />80044225<br />**Número**:<br />-2147204571|El cliente no puede descargar los datos. Póngase en contacto con el administrador del sistema para obtener asistencia e intente desconectarse de nuevo.|
> |**Nombre**:<br />GoOfflineFailedPrepareMsde<br />**Hex**:<br />80044226<br />**Número**:<br />-2147204570|Fallo al preparar MSDE. Póngase en contacto con el administrador del sistema para obtener asistencia e intente desconectarse de nuevo.|
> |**Nombre**:<br />GoOfflineFailedReloadMetadataCache<br />**Hex**:<br />80044227<br />**Número**:<br />-2147204569|Microsoft Dynamics 365 for Outlook no pudo desconectarse. Intente ponerse sin conexión de nuevo.|
> |**Nombre**:<br />GoOfflineFeatureNotEnabled<br />**Hex**:<br />8004422a<br />**Número**:<br />-2147204566|La capacidad sin conexión no es compatible con Microsoft Dynamics 365 for Outlook.|
> |**Nombre**:<br />GoOfflineFileWasDeleted<br />**Hex**:<br />80044229<br />**Número**:<br />-2147204567|El archivo de datos se eliminó en el servidor antes de ser enviado al cliente.|
> |**Nombre**:<br />GoOfflineGetBCPFileException<br />**Hex**:<br />80044221<br />**Número**:<br />-2147204575|Dynamics 365 server no puede procesar su solicitud. Póngase en contacto con el administrador del sistema para obtener asistencia e intente desconectarse de nuevo.|
> |**Nombre**:<br />GoOfflineMetadataVersionsMismatch<br />**Hex**:<br />80044220<br />**Número**:<br />-2147204576|Cliente y versiones de metadatos del servidor son diferentes debido a la nueva personalización en el servidor. Intente ponerse sin conexión de nuevo.|
> |**Nombre**:<br />GoOfflineServerFailedGenerateBCPFile<br />**Hex**:<br />80044223<br />**Número**:<br />-2147204573|Dynamics 365 server no es capaz de generar el archivo BCP. Póngase en contacto con el administrador del sistema para obtener asistencia e intente desconectarse de nuevo.|
> |**Nombre**:<br />GraphApiS2SSetupFailureException<br />**Hex**:<br />80044260<br />**Número**:<br />-2147204512|No se ha configurado la autenticación de servidor a servidor con Exchange para la API de Office Graph.|
> |**Nombre**:<br />GuidNotPresent<br />**Hex**:<br />80040362<br />**Número**:<br />-2147220638|Falta el identificador único global (GUID) requerido en esta fila|
> |**Nombre**:<br />HeaderValueDoesNotMatchAttributeDisplayLabel<br />**Hex**:<br />80040370<br />**Número**:<br />-2147220624|El encabezado de la columna no coincide con la etiqueta para mostrar de atributo.|
> |**Nombre**:<br />HiddenPropertyValidationFailed<br />**Hex**:<br />80061000<br />**Número**:<br />-2147086336|No puede crear una instancia de propiedad para una propiedad oculta.|
> |**Nombre**:<br />HiddensheetNotAvailable<br />**Hex**:<br />800609B6<br />**Número**:<br />-2147087946|La hoja oculta no está disponible.|
> |**Nombre**:<br />HierarchicalOperationFailed<br />**Hex**:<br />8008100F<br />**Número**:<br />-2146955249|Esta operación no se puede completar en esta jerarquía. Se ha producido un error al realizar esta operación para {0}. Puede realizar la operación de manera independiente de este producto para solucionar el error e intentarlo de nuevo para la jerarquía completa.|
> |**Nombre**:<br />HierarchyCalculateLimitReached<br />**Hex**:<br />80060547<br />**Número**:<br />-2147089081|Los cálculos no se pueden llevar a cabo en línea porque se ha alcanzado el límite de profundidad de jerarquía de registro maestro de {0}.|
> |**Nombre**:<br />HipInvalidCertificate<br />**Hex**:<br />8004Ed45<br />**Número**:<br />-2147160763|Certificado no válido para el uso de HIP.|
> |**Nombre**:<br />HipNoSettingError<br />**Hex**:<br />8004Ed44<br />**Número**:<br />-2147160764|No se encontró configuración de la aplicación Hip [{0}].|
> |**Nombre**:<br />HonorPauseWithoutSLAKPIError<br />**Hex**:<br />80045000<br />**Número**:<br />-2147201024|El SLA se puede definir para poder pausarse y reanudarse solo si el KPI de SLA del usuario está establecido en Sí.|
> |**Nombre**:<br />HybridSSSExchangeOnlineS2SCertActsExpired<br />**Hex**:<br />80131500<br />**Número**:<br />-2146233088|El certificado que se usa para la autenticación de S2S de Dynamics 365 Onpremise con Exchange Online ha expirado|
> |**Nombre**:<br />HybridSSSExchangeOnlineS2SCertExpired<br />**Hex**:<br />80131509<br />**Número**:<br />-2146233079|El certificado que se usa para la autenticación de S2S de Dynamics 365 Onpremise con Exchange Online ha expirado|
> |**Nombre**:<br />ImageAttributeNotSupportedFullImage<br />**Hex**:<br />8009000D<br />**Número**:<br />-2146893811|El atributo de imagen {0} de entidad {1} no admite el almacenamiento de la imagen completa.|
> |**Nombre**:<br />ImageInvalidMaxSizeInKB<br />**Hex**:<br />8009000E<br />**Número**:<br />-2146893810|MaxSizeInKB no válido para el atributo de imagen {0} de la entidad {1}. El tamaño válido debe estar entre [{2} - {3}] KB|
> |**Nombre**:<br />ImportArticleTemplateError<br />**Hex**:<br />8004800D<br />**Número**:<br />-2147188723|Se ha producido un error al analizar las plantillas de artículo en la importación Xml|
> |**Nombre**:<br />ImportAttributeNameError<br />**Hex**:<br />80048062<br />**Número**:<br />-2147188638|Nombre no válido para el atributo {0}.  El nombre del atributo personalizado debe comenzar con un prefijo de personalización válido. El prefijo para el componente de una solución debe coincidir con el prefijo especificado para el editor de la solución.|
> |**Nombre**:<br />ImportChannelPropertyGroupError<br />**Hex**:<br />800608F3<br />**Número**:<br />-2147088141|Se ha producido un error al importar el grupo de propiedades de canal.|
> |**Nombre**:<br />ImportComponentDeletedIgnored<br />**Hex**:<br />8004847c<br />**Número**:<br />-2147187588|No se puede actualizar este componente porque no existe en esta organización de Microsoft Dynamics 365.|
> |**Nombre**:<br />ImportConfigNotSpecified<br />**Hex**:<br />80040322<br />**Número**:<br />-2147220702|No se puede procesar con importación masiva porque la configuración de la importación no está especificada.|
> |**Nombre**:<br />ImportContractTemplateError<br />**Hex**:<br />8004800B<br />**Número**:<br />-2147188725|Se ha producido un error al analizar las plantillas de contrato en la importación Xml|
> |**Nombre**:<br />ImportConvertRuleError<br />**Hex**:<br />8004F869<br />**Número**:<br />-2147157911|Error al importar reglas de conversión.|
> |**Nombre**:<br />ImportCustomizationsBadZipFileError<br />**Hex**:<br />80048060<br />**Número**:<br />-2147188640|El archivo de solución no es válido. El archivo comprimido debe contener los siguientes archivos en su raíz: solution.xml, customizations.xml y [Content_Types].xml. No se admiten archivos de personalización exportados desde versiones anteriores de Microsoft Dynamics 365.|
> |**Nombre**:<br />ImportDashboardDeletedError<br />**Hex**:<br />8004E308<br />**Número**:<br />-2147163384|Un panel con el mismo identificador se marca como eliminado en el sistema. Publique primero la entidad de formulario del sistema y vuelva a importar de nuevo.|
> |**Nombre**:<br />ImportDefaultAsPackageError<br />**Hex**:<br />80048049<br />**Número**:<br />-2147188663|El paquete proporcionado para la solución predeterminada está intentando instalarse en modo administrado. La solución predeterminada no se puede administrar. En el XML de la solución predeterminada, establezca el valor de la administración en "false" e intente volver a importar la solución.|
> |**Nombre**:<br />ImportDependencySolutionError<br />**Hex**:<br />80048034<br />**Número**:<br />-2147188684|{0} requiere soluciones que no se está instaladas. Importar las siguientes soluciones antes de importar esta. {1} |
> |**Nombre**:<br />ImportDuplicateEntity<br />**Hex**:<br />8004810c<br />**Número**:<br />-2147188468|Esta importación presentó un error debido a que ya existe una entidad diferente con el nombre idéntico {0} en la organización de destino.|
> |**Nombre**:<br />ImportEmailTemplateError<br />**Hex**:<br />8004800C<br />**Número**:<br />-2147188724|Se ha producido un error al analizar las plantillas de correo electrónico en la importación Xml|
> |**Nombre**:<br />ImportEmailTemplateErrorMissingFile<br />**Hex**:<br />8004802B<br />**Número**:<br />-2147188693|La plantilla de correo electrónico '{0}' importación: los datos adjuntos '{1}' no se encontraron en el archivo zip de importación.|
> |**Nombre**:<br />ImportEmailTemplatePersonalError<br />**Hex**:<br />80048014<br />**Número**:<br />-2147188716|No se ha importado la plantilla de correo electrónico. La plantilla es una plantilla personal en el sistema de destino. La importación no puede sobrescribir las plantillas personales.|
> |**Nombre**:<br />ImportEntityCustomResourcesError<br />**Hex**:<br />80048002<br />**Número**:<br />-2147188734|Recursos personalizados en el archivo de importación no válidos|
> |**Nombre**:<br />ImportEntityCustomResourcesNewStringError<br />**Hex**:<br />80048003<br />**Número**:<br />-2147188733|Nueva cadena de entidad en los recursos personalizados no válida.|
> |**Nombre**:<br />ImportEntityIconError<br />**Hex**:<br />80048001<br />**Número**:<br />-2147188735|Icono no válido en el archivo de importación|
> |**Nombre**:<br />ImportEntityNameMismatchError<br />**Hex**:<br />80048008<br />**Número**:<br />-2147188728|El número de parámetros de formato pasado a la cadena de entrada es incorrecto|
> |**Nombre**:<br />ImportEntitySystemUserLiveMismatchError<br />**Hex**:<br />80048025<br />**Número**:<br />-2147188699|La entidad systemuser se ha importado pero no se han importado formularios personalizados para la entidad. Los formularios de entidad de usuario del sistema de Microsoft Dynamics 365 no se pueden importar en Microsoft Dynamics 365 Online.|
> |**Nombre**:<br />ImportEntitySystemUserOnPremiseMismatchError<br />**Hex**:<br />80048024<br />**Número**:<br />-2147188700|La entidad systemuser se ha importado pero no se han importado formularios personalizados para la entidad. Los formularios de entidad de usuario del sistema de Microsoft Dynamics 365 Online no se pueden importar en local u hospedados versiones de Microsoft Dynamics 365.|
> |**Nombre**:<br />ImportExportDeprecatedError<br />**Hex**:<br />80048045<br />**Número**:<br />-2147188667|Este mensaje ya no está disponible. Consulte el SDK para mensajes alternativos.|
> |**Nombre**:<br />ImportFieldSecurityProfileAttributesMissingError<br />**Hex**:<br />80048064<br />**Número**:<br />-2147188636|No se pudieron importar algunos permisos de seguridad de campo porque los siguientes permisos no están en el sistema: {0}.|
> |**Nombre**:<br />ImportFieldSecurityProfileIsSecuredMissingError<br />**Hex**:<br />80048063<br />**Número**:<br />-2147188637|No se pudieron importar algunos permisos de seguridad de campo porque los siguientes campos no se pueden proteger: {0}.|
> |**Nombre**:<br />ImportFieldXmlError<br />**Hex**:<br />80048006<br />**Número**:<br />-2147188730|El número de parámetros de formato pasado a la cadena de entrada es incorrecto|
> |**Nombre**:<br />ImportFileFailed<br />**Hex**:<br />80050125<br />**Número**:<br />-2147155675|La importación y la extracción del archivo ha fallado.|
> |**Nombre**:<br />ImportFileSignatureInvalid<br />**Hex**:<br />80048065<br />**Número**:<br />-2147188635|El archivo de importación tiene una firma digital no válida.|
> |**Nombre**:<br />ImportFileTooLargeToUpload<br />**Hex**:<br />80040375<br />**Número**:<br />-2147220619|El archivo de importación es demasiado grande para cargarlo.|
> |**Nombre**:<br />ImportFileUnprocessed<br />**Hex**:<br />80072035<br />**Número**:<br />-2147016651|Archivos sin procesar encontrados: {0}|
> |**Nombre**:<br />ImportFormXmlError<br />**Hex**:<br />80048007<br />**Número**:<br />-2147188729|El número de parámetros de formato pasado a la cadena de entrada es incorrecto|
> |**Nombre**:<br />ImportGenericEntitiesError<br />**Hex**:<br />80048020<br />**Número**:<br />-2147188704|Se ha producido un error al importar entidades genéricas.|
> |**Nombre**:<br />ImportGenericError<br />**Hex**:<br />8004801E<br />**Número**:<br />-2147188706|Error de importación. Para obtener más información, vea los mensajes de error relacionados.|
> |**Nombre**:<br />ImportHierarchyRuleDeletedError<br />**Hex**:<br />8004F9A1<br />**Número**:<br />-2147157599|Una regla de jerarquía con el mismo id. está marcada como eliminada en el sistema. Primero publique la entidad personalizada e impórtela de nuevo.|
> |**Nombre**:<br />ImportHierarchyRuleExistingError<br />**Hex**:<br />8004F9A2<br />**Número**:<br />-2147157598|No se puede volver a usar la regla de jerarquía existente.|
> |**Nombre**:<br />ImportHierarchyRuleOtcMismatchError<br />**Hex**:<br />8004F9A3<br />**Número**:<br />-2147157597|Error al procesar reglas de jerarquía del mismo código de tipo de objeto. (conflicto sin solución en el sistema)|
> |**Nombre**:<br />ImportInvalidFileError<br />**Hex**:<br />80048000<br />**Número**:<br />-2147188736|Archivo de importación no válido|
> |**Nombre**:<br />ImportInvalidXmlError<br />**Hex**:<br />8004802C<br />**Número**:<br />-2147188692|Este paquete de soluciones no se puede importar porque contiene XML no válido. Puede intentar reparar el archivo editando manualmente el contenido XML con la información encontrada en los errores de validación del esquema, o puede ponerse en contacto con su proveedor de soluciones.|
> |**Nombre**:<br />ImportIsvConfigError<br />**Hex**:<br />8004800E<br />**Número**:<br />-2147188722|Error al analizar la IsvConfig durante la importación|
> |**Nombre**:<br />ImportLanguagesIgnoredError<br />**Hex**:<br />80048026<br />**Número**:<br />-2147188698|No se pudieron importar las etiquetas traducidas para los siguientes idiomas porque no se han habilitado para esta organización: {0}|
> |**Nombre**:<br />ImportMailMergeTemplateEntityMissingError<br />**Hex**:<br />80048480<br />**Número**:<br />-2147187584|La plantilla de combinación de correspondencia {0} no se importó porque la entidad {1} asociada a esta plantilla no se encuentra en el sistema de destino.|
> |**Nombre**:<br />ImportMailMergeTemplateError<br />**Hex**:<br />80048456<br />**Número**:<br />-2147187626|Se ha producido un error al analizar las plantillas de combinar correspondencia en la importación Xml|
> |**Nombre**:<br />ImportMapInUse<br />**Hex**:<br />80048465<br />**Número**:<br />-2147187611|Una o varias de las asignaciones de datos seleccionadas no se pueden eliminar porque se están usando en una importación de datos.|
> |**Nombre**:<br />ImportMappingsInvalidIdSpecified<br />**Hex**:<br />80048427<br />**Número**:<br />-2147187673|El archivo XML tiene uno o más ID no válidos. El identificador especificado no se puede usar como un identificador único.|
> |**Nombre**:<br />ImportMappingsMissingEntityMapError<br />**Hex**:<br />80048010<br />**Número**:<br />-2147188720|Este archivo de personalización contiene una referencia a una asignación de entidad que no existe en el sistema de destino.|
> |**Nombre**:<br />ImportMappingsSystemMapError<br />**Hex**:<br />8004800F<br />**Número**:<br />-2147188721|La importación no puede crear asignaciones de atributo de sistema|
> |**Nombre**:<br />ImportMissingComponent<br />**Hex**:<br />8004801F<br />**Número**:<br />-2147188705|No se puede agregar un componente raíz {0} de tipo {1} porque no está en el sistema de destino.|
> |**Nombre**:<br />ImportMissingDependenciesError<br />**Hex**:<br />8004801D<br />**Número**:<br />-2147188707|La siguiente solución no se puede importar: {0}. Faltan algunas dependencias.|
> |**Nombre**:<br />ImportMissingRootComponentEntry<br />**Hex**:<br />8004803A<br />**Número**:<br />-2147188678|La importación ha fallado porque el componente {0} del tipo {1} no está declarado en el archivo de la solución como componente raíz. Para solucionar esto, importe de nuevo con el archivo XML que se generó cuando exportó la solución.|
> |**Nombre**:<br />ImportMobileOfflineProfileError<br />**Hex**:<br />8006099F<br />**Número**:<br />-2147087969|Error al importar los perfiles de Mobile Offline.|
> |**Nombre**:<br />ImportNewPluginTypesError<br />**Hex**:<br />80048071<br />**Número**:<br />-2147188623|Se han quitado los tipos de complementos existentes. Actualice la versión mayor o menor del ensamblado de complemento.|
> |**Nombre**:<br />ImportNonWellFormedFileError<br />**Hex**:<br />80048013<br />**Número**:<br />-2147188717|Archivo de personalización no válido. Este archivo no está bien formado.|
> |**Nombre**:<br />ImportNotComplete<br />**Hex**:<br />80048472<br />**Número**:<br />-2147187598|Una o más importaciones no está en estado completo. Solo se pueden eliminar los registros importados desde trabajos completados. Espere hasta que finalice el trabajo e inténtelo de nuevo.|
> |**Nombre**:<br />ImportOperationChildFailure<br />**Hex**:<br />80044334<br />**Número**:<br />-2147204300|Uno o varios de los trabajos de secundarios importación da error|
> |**Nombre**:<br />ImportOptionSetAttributeError<br />**Hex**:<br />80048039<br />**Número**:<br />-2147188679|El atributo '{0}' no se importó porque hace referencia a un conjunto de opciones global inexistente ('{1}').|
> |**Nombre**:<br />ImportOptionSetsError<br />**Hex**:<br />80048030<br />**Número**:<br />-2147188688|Se ha producido un error durante la importación de OptionSets.|
> |**Nombre**:<br />ImportOrgSettingsError<br />**Hex**:<br />80048019<br />**Número**:<br />-2147188711|Error al analizar la configuración de la organización durante la importación.|
> |**Nombre**:<br />ImportPluginTypesError<br />**Hex**:<br />80048012<br />**Número**:<br />-2147188718|Se ha producido un error al importar tipos de complementos.|
> |**Nombre**:<br />ImportRelationshipRoleMapsError<br />**Hex**:<br />8004800A<br />**Número**:<br />-2147188726|El número de parámetros de formato pasado a la cadena de entrada es incorrecto|
> |**Nombre**:<br />ImportRelationshipRolesError<br />**Hex**:<br />80048009<br />**Número**:<br />-2147188727|El número de parámetros de formato pasado a la cadena de entrada es incorrecto|
> |**Nombre**:<br />ImportRelationshipRolesPrivilegeError<br />**Hex**:<br />8004802F<br />**Número**:<br />-2147188689|{0} no se puede importar. Se necesita el privilegio {1} para importar este componente.|
> |**Nombre**:<br />ImportReportsError<br />**Hex**:<br />80048032<br />**Número**:<br />-2147188686|Se ha producido un error durante la importación de informes.|
> |**Nombre**:<br />ImportRestrictedSolutionError<br />**Hex**:<br />8004F007<br />**Número**:<br />-2147160057|El identificador de solución proporcionado está restringido y no se puede importar.|
> |**Nombre**:<br />ImportRibbonsError<br />**Hex**:<br />80048031<br />**Número**:<br />-2147188687|Se ha producido un error durante la importación de cintas.|
> |**Nombre**:<br />ImportRoleError<br />**Hex**:<br />80048017<br />**Número**:<br />-2147188713|No se puede importar el rol de seguridad. No puede actualizar el rol con el identificador de rol especificado o el nombre del rol no es único.|
> |**Nombre**:<br />ImportRolePermissionError<br />**Hex**:<br />80048018<br />**Número**:<br />-2147188712|No tiene los privilegios necesarios para importar roles de seguridad.|
> |**Nombre**:<br />ImportRoutingRuleError<br />**Hex**:<br />8004F867<br />**Número**:<br />-2147157913|Se ha producido un error al importar conjuntos de reglas de enrutamiento.|
> |**Nombre**:<br />ImportSavedQueryDeletedError<br />**Hex**:<br />8004801B<br />**Número**:<br />-2147188709|Una consulta guardada con el mismo identificador se marca como eliminada en el sistema. Publique primero la entidad personalizada y vuelva a importar de nuevo.|
> |**Nombre**:<br />ImportSavedQueryExistingError<br />**Hex**:<br />80048005<br />**Número**:<br />-2147188731|El número de parámetros de formato pasado a la cadena de entrada es incorrecto|
> |**Nombre**:<br />ImportSavedQueryOtcMismatchError<br />**Hex**:<br />80048004<br />**Número**:<br />-2147188732|Error al procesar las consultas guardadas del mismo código de tipo de objeto (conflicto sin solución en el sistema)|
> |**Nombre**:<br />ImportSdkMessagesError<br />**Hex**:<br />80048016<br />**Número**:<br />-2147188714|Se ha producido un error al importar mensajes de Sdk.|
> |**Nombre**:<br />ImportSiteMapError<br />**Hex**:<br />80048011<br />**Número**:<br />-2147188719|Error al importar el mapa del sitio.|
> |**Nombre**:<br />ImportSlaError<br />**Hex**:<br />8004F868<br />**Número**:<br />-2147157912|Se ha producido un error durante la importación de SLA.|
> |**Nombre**:<br />ImportSolutionError<br />**Hex**:<br />80048033<br />**Número**:<br />-2147188685|Error durante la importación de una solución.|
> |**Nombre**:<br />ImportSolutionIsvConfigWarning<br />**Hex**:<br />80048042<br />**Número**:<br />-2147188670|Se ha sobrescrito la configuración ISV.|
> |**Nombre**:<br />ImportSolutionManagedError<br />**Hex**:<br />80048038<br />**Número**:<br />-2147188680|La solución '{0}' ya existe en este sistema como administrada y no se puede actualizar.|
> |**Nombre**:<br />ImportSolutionManagedToUnmanagedMismatch<br />**Hex**:<br />80048040<br />**Número**:<br />-2147188672|La solución ya está instalada en este sistema como una solución no administrada y el paquete proporcionado está intentando instalarlo en el modo administrado. La importación solo puede actualizar soluciones cuando los modos coinciden. Desinstale la solución actual e inténtelo de nuevo.|
> |**Nombre**:<br />ImportSolutionOrganizationSettingsWarning<br />**Hex**:<br />80048044<br />**Número**:<br />-2147188668|Se ha sobrescrito la configuración de la organización.|
> |**Nombre**:<br />ImportSolutionPackageInvalidSku<br />**Hex**:<br />8004806B<br />**Número**:<br />-2147188629|El paquete de solución que está importando se generó en Microsoft Dynamics 365 Online. No puede importarlo en versiones locales u hospedadas de Microsoft Dynamics 365.|
> |**Nombre**:<br />ImportSolutionPackageInvalidSolutionPackageVersion<br />**Hex**:<br />80048068<br />**Número**:<br />-2147188632|Solo puede importar soluciones con una versión de paquete de {0} o una versión anterior en esta organización. Asimismo, no se puede importar ninguna solución a esta organización que haya sido exportada desde Microsoft Dynamics 365 2011 o anteriores.|
> |**Nombre**:<br />ImportSolutionPackageMinimumVersionNeeded<br />**Hex**:<br />00000001<br />**Número**:<br />1|Obsoletas, no quitar ahora ya que puede producir problemas durante la integración.|
> |**Nombre**:<br />ImportSolutionPackageNeedsUpgrade<br />**Hex**:<br />80048067<br />**Número**:<br />-2147188633|El paquete de la solución que está importando se generó en una versión diferente de Microsoft Dynamics 365. El sistema intentará transformar el paquete antes de importar. Versión de paquete: {0} {1}, versión del sistema: {2} {3}.|
> |**Nombre**:<br />ImportSolutionPackageNotValid<br />**Hex**:<br />80048066<br />**Número**:<br />-2147188634|El paquete de solución que va a importar se generó en una versión de Microsoft Dynamics 365 que no se puede importar en este sistema. Versión de paquete: {0} {1}, versión del sistema: {2} {3}.|
> |**Nombre**:<br />ImportSolutionPackageRequiresOptInAvailable<br />**Hex**:<br />80048069<br />**Número**:<br />-2147188631|Algunos componentes en el paquete de la solución que está importando requieren optar por participar. La suscripción en está disponible, consulte con el administrador.|
> |**Nombre**:<br />ImportSolutionPackageRequiresOptInNotAvailable<br />**Hex**:<br />8004806A<br />**Número**:<br />-2147188630|El paquete de la solución que está importando se generó en una SKU de Microsoft Dynamics 365 que admite optar por recibir. No se pueden importar en el sistema.|
> |**Nombre**:<br />ImportSolutionSiteMapWarning<br />**Hex**:<br />80048043<br />**Número**:<br />-2147188669|Se ha sobrescrito el mapa del sitio.|
> |**Nombre**:<br />ImportSolutionUnmanagedToManagedMismatch<br />**Hex**:<br />80048041<br />**Número**:<br />-2147188671|La solución ya está instalada en este sistema como una solución administrada y el paquete proporcionado está intentando instalarlo en el modo no administrado. La importación solo puede actualizar soluciones cuando los modos coinciden. Desinstale la solución actual e inténtelo de nuevo.|
> |**Nombre**:<br />ImportSystemSolutionError<br />**Hex**:<br />80048046<br />**Número**:<br />-2147188666|No se puede importar la solución del sistema.|
> |**Nombre**:<br />ImportTemplateLanguageIgnored<br />**Hex**:<br />8004847a<br />**Número**:<br />-2147187590|No se puede importar esta plantilla debido a que su idioma no está habilitado en la organización de Microsoft Dynamics 365.|
> |**Nombre**:<br />ImportTemplatePersonalIgnored<br />**Hex**:<br />8004847b<br />**Número**:<br />-2147187589|No puede importar esta plantilla debido a que está definida como "personal" en su organización de Microsoft Dynamics 365.|
> |**Nombre**:<br />ImportTranslationMissingSolutionError<br />**Hex**:<br />80048047<br />**Número**:<br />-2147188665|Se ha producido un error al importar las traducciones. La solución asociada con las traducciones no existe en el sistema.|
> |**Nombre**:<br />ImportTranslationsBadZipFileError<br />**Hex**:<br />80048061<br />**Número**:<br />-2147188639|El archivo de traducción no es válido. El archivo comprimido debe contener los siguientes archivos en su raíz: {0}, [Content_Types].xml.|
> |**Nombre**:<br />ImportVisualizationDeletedError<br />**Hex**:<br />8004E013<br />**Número**:<br />-2147164141|Una visualización guardada de una consulta con identificador {0} se marca para su eliminación en el sistema. Publique primero la entidad personalizada y vuelva a importar de nuevo.|
> |**Nombre**:<br />ImportVisualizationExistingError<br />**Hex**:<br />8004E014<br />**Número**:<br />-2147164140|La visualización guardada de una consulta con identificador {0} ya existe en el sistema y no se puede reutilizar por una nueva entidad personalizada.|
> |**Nombre**:<br />ImportWillExceedCustomEntityQuota<br />**Hex**:<br />8004b043<br />**Número**:<br />-2147176381|Este proceso de importación intenta importar {0} nuevas entidades personalizadas. Esto superará los límites de entidad personalizada para la organización.|
> |**Nombre**:<br />ImportWorkflowAttributeDependencyError<br />**Hex**:<br />80048022<br />**Número**:<br />-2147188702|No se puede importar la definición de flujo de trabajo. Falta la dependencia de atributos necesaria.|
> |**Nombre**:<br />ImportWorkflowEntityDependencyError<br />**Hex**:<br />80048023<br />**Número**:<br />-2147188701|No se puede importar la definición de flujo de trabajo. Falta la dependencia de entidades necesaria.|
> |**Nombre**:<br />ImportWorkflowError<br />**Hex**:<br />80048021<br />**Número**:<br />-2147188703|No se puede importar la definición de flujo de trabajo. No puede actualizar el flujo de trabajo con el id de flujo de trabajo especificado o el nombre del flujo de trabajo no es único.|
> |**Nombre**:<br />ImportWorkflowNameConflictError<br />**Hex**:<br />80048027<br />**Número**:<br />-2147188697|El flujo de trabajo {0} no se puede importar porque existe un flujo de trabajo con el mismo nombre y un identificador único diferente en el sistema de destino. Cambie el nombre del flujo de trabajo y, después, inténtelo de nuevo.|
> |**Nombre**:<br />ImportWorkflowPublishedError<br />**Hex**:<br />80048028<br />**Número**:<br />-2147188696|El flujo de trabajo {0}({1}) no se puede importar porque está publicado en el sistema de destino un flujo de trabajo con el mismo identificador único. Anule la publicación del flujo de trabajo en el sistema de destino antes de intentar volver a importar este flujo de trabajo.|
> |**Nombre**:<br />ImportWrongPublisherError<br />**Hex**:<br />8004801C<br />**Número**:<br />-2147188708|La siguiente solución administrada no se puede importar: {0}. No se puede cambiar el nombre del editor de {1} a {2}.|
> |**Nombre**:<br />ImportXsdValidationError<br />**Hex**:<br />8004801A<br />**Número**:<br />-2147188710|El archivo de importación no es válido. Se produjo el siguiente error en la validación XSD: '{0}'. Error en la validación en : '...{1} <<<<<ERROR LOCATION>>>>> {2}...'."|
> |**Nombre**:<br />InaccessibleSmtpServer<br />**Hex**:<br />8005E227<br />**Número**:<br />-2147098073|No se puede alcanzar el servidor smtp. Compruebe que el servidor smtp es accesible.|
> |**Nombre**:<br />InactiveEmailServerProfile<br />**Hex**:<br />8005E228<br />**Número**:<br />-2147098072|El perfil de servidor de correo electrónico está deshabilitado. No se puede procesar correo electrónico para un perfil deshabilitado.|
> |**Nombre**:<br />InactiveMailbox<br />**Hex**:<br />8005E219<br />**Número**:<br />-2147098087|El buzón se encuentra en estado inactivo. Enviar y recibir mensajes se permite solo para los buzones activos.|
> |**Nombre**:<br />InactiveMetricSetOnGoal<br />**Hex**:<br />8004F686<br />**Número**:<br />-2147158394|No se puede establecer una métrica inactiva en un objetivo.|
> |**Nombre**:<br />InactiveRollupQuerySetOnGoal<br />**Hex**:<br />8004F685<br />**Número**:<br />-2147158395|No se puede establecer una consulta de consolidación inactiva en un objetivo.|
> |**Nombre**:<br />IncidentCannotCancel<br />**Hex**:<br />8004440e<br />**Número**:<br />-2147204082|No se puede cancelar el incidente porque hay actividades abiertas para este incidente.|
> |**Nombre**:<br />IncidentContractDoesNotHaveAllotments<br />**Hex**:<br />80044403<br />**Número**:<br />-2147204093|El contrato no tiene una cobertura suficiente. El caso no se puede crear para este contrato.|
> |**Nombre**:<br />IncidentInvalidAllotmentType<br />**Hex**:<br />8004440b<br />**Número**:<br />-2147204085|El tipo de cobertura del contrato no es válido.|
> |**Nombre**:<br />IncidentInvalidContractLineStateForCreate<br />**Hex**:<br />8004440d<br />**Número**:<br />-2147204083|No se puede crear el caso para este elemento de línea de contrato porque el elemento de línea de contrato se ha cancelado o ha expirado.|
> |**Nombre**:<br />IncidentInvalidContractStateForCreate<br />**Hex**:<br />80044400<br />**Número**:<br />-2147204096|El caso no se puede crear para este contrato debido al estado del contrato.|
> |**Nombre**:<br />IncidentIsAlreadyClosedOrCancelled<br />**Hex**:<br />80044411<br />**Número**:<br />-2147204079|Ya cerrado o cancelado|
> |**Nombre**:<br />IncidentMissingActivityRegardingObject<br />**Hex**:<br />80044409<br />**Número**:<br />-2147204087|Falta el identificador del incidente.|
> |**Nombre**:<br />IncidentMissingContractDetail<br />**Hex**:<br />80044401<br />**Número**:<br />-2147204095|Falta el identificador de detalles del contrato.|
> |**Nombre**:<br />IncidentNullSpentTimeOrBilled<br />**Hex**:<br />8004440c<br />**Número**:<br />-2147204084|El timespent en la incidencia es NULO o IsBilled de la actividad de IncidentResolution es NULO.|
> |**Nombre**:<br />IncomingDeliveryIsForwardMailbox<br />**Hex**:<br />8005E223<br />**Número**:<br />-2147098077|No se pueden sondear mensajes desde el buzón. Su método de entrega entrante es buzón de enrutamiento.|
> |**Nombre**:<br />IncomingServerLocationAndSslSetToNo<br />**Hex**:<br />8005E23E<br />**Número**:<br />-2147098050|La dirección URL especificada para Ubicación de servidor entrante utiliza HTTPS, pero la opción Usar SSL para conexión entrante se ha establecido en No. Establezca esta opción en Sí e inténtelo de nuevo.|
> |**Nombre**:<br />IncomingServerLocationAndSslSetToYes<br />**Hex**:<br />8005E240<br />**Número**:<br />-2147098048|La dirección URL especificada para Ubicación de servidor entrante utiliza HTTP, pero la opción Usar SSL para conexión entrante se ha establecido en Sí. Especifique una ubicación de servidor que utilice HTTPS e inténtelo de nuevo.|
> |**Nombre**:<br />IncompatibleStepsEncountered<br />**Hex**:<br />8006088B<br />**Número**:<br />-2147088245|No puede habilitar la configuración de EnforceReadOnlyPlugins porque algunos complementos que cambian datos están registrados en mensajes SDK de solo lectura. {0}|
> |**Nombre**:<br />IncompleteTransformationParameterMappingsFound<br />**Hex**:<br />8004037d<br />**Número**:<br />-2147220611|Uno o más parámetros de transformación obligatorios no tiene asignaciones definidas.|
> |**Nombre**:<br />InconsistentAttributeConfiguration<br />**Hex**:<br />80072009<br />**Número**:<br />-2147016695|Se encontró más de una configuración para atributo con id {0}.|
> |**Nombre**:<br />InconsistentAttributeNameCasing<br />**Hex**:<br />8004F043<br />**Número**:<br />-2147159997|Detectado uso incoherente de mayúsculas y minúsculas en nombre de atributo, esperado: {0}, real: {1}.|
> |**Nombre**:<br />InconsistentProductRelationshipState<br />**Hex**:<br />8004F996<br />**Número**:<br />-2147157610|La otra fila de la relación de producto no está disponible.|
> |**Nombre**:<br />IncorrectActiveStageEntity<br />**Hex**:<br />80060462<br />**Número**:<br />-2147089310|La fase activa no está en la entidad '{0}'.|
> |**Nombre**:<br />IncorrectAttributeValueType<br />**Hex**:<br />80044354<br />**Número**:<br />-2147204268|Tipo de valor de atributo para {0} no válido. Esperado: {1}, Encontrado: {2}|
> |**Nombre**:<br />IncorrectEntitySetName<br />**Hex**:<br />8006089C<br />**Número**:<br />-2147088228|El nombre del conjunto de entidades {0} debe comenzar con un prefijo de personalización válido.|
> |**Nombre**:<br />IncorrectFileFormat<br />**Hex**:<br />80072037<br />**Número**:<br />-2147016649|El archivo {0} no se puede importar.|
> |**Nombre**:<br />IncorrectSingleFileMultipleEntityMap<br />**Hex**:<br />80048502<br />**Número**:<br />-2147187454|Debe haber dos o más asignaciones de entidad definidos cuando se establece EntitiesPerFile en ImportMap en Varios|
> |**Nombre**:<br />IncreasingDaysWillResetMobileOfflineData<br />**Hex**:<br />80060991<br />**Número**:<br />-2147087983|Al aumentar el número de días se restablecerán los datos de mobile offline y se volverá a sincronizar con los dispositivos móviles.|
> |**Nombre**:<br />IndexOutOfRange<br />**Hex**:<br />8005E008<br />**Número**:<br />-2147098616|El índice {0} está fuera del intervalo {1}. El número de elementos presentes es {2}.|
> |**Nombre**:<br />IndexSizeConstraintViolated<br />**Hex**:<br />80060895<br />**Número**:<br />-2147088235|El tamaño de índice supera el límite de tamaño de {0} bytes. La clave es demasiado grande. Intente quitar algunas columnas o marcar las cadenas en las columnas de cadenas más cortas.|
> |**Nombre**:<br />InitializeErrorNoReadOnSource<br />**Hex**:<br />8004F800<br />**Número**:<br />-2147158016|No se pudo completar la operación porque no tiene acceso de lectura en algunos campos del registro {0}.|
> |**Nombre**:<br />InitializeFileRequestFailure<br />**Hex**:<br />80072555<br />**Número**:<br />-2147015339|Se produjo un error durante la solicitud de inicialización del archivo. (RecordId: {0}, EntityName: {1}) Detalles:{2}|
> |**Nombre**:<br />InputParameterFieldIncorrect<br />**Hex**:<br />80060378<br />**Número**:<br />-2147089544|El parámetro de entrada “{0}” no coincide con el campo de parámetros de entrada configurado. Póngase en contacto con el administrador del sistema para comprobar los metadatos de configuración si persiste el error.|
> |**Nombre**:<br />InsertOptionValueInvalidType<br />**Hex**:<br />80044320<br />**Número**:<br />-2147204320|Puede agregar valores opcionales solo a los atributos de estado y de la lista desplegable.|
> |**Nombre**:<br />InstanceOutsideEffectiveRange<br />**Hex**:<br />8004E115<br />**Número**:<br />-2147163883|No se puede realizar la operación. Una instancia está fuera series de rango de expansión efectiva.|
> |**Nombre**:<br />InsufficientAccessMode<br />**Hex**:<br />80044502<br />**Número**:<br />-2147203838|El usuario no tiene acceso de lectura y escritura en la organización de Dynamics 365.|
> |**Nombre**:<br />InsufficientAuthTicket<br />**Hex**:<br />8004A103<br />**Número**:<br />-2147180285|El vale especificado para la autenticación no cumple la directiva|
> |**Nombre**:<br />InsufficientColumnsInSubQuery<br />**Hex**:<br />8004E022<br />**Número**:<br />-2147164126|Una o varias columnas requeridas por la consulta externa no están disponibles desde la subconsulta.|
> |**Nombre**:<br />InsufficientCreatePrivilege<br />**Hex**:<br />8006110A<br />**Número**:<br />-2147086070|Los proveedores externos no tienen privilegios suficientes para crear un registro nuevo con los parámetros porporcionados.|
> |**Nombre**:<br />InsufficientPrivilegesSupportUser<br />**Hex**:<br />80048345<br />**Número**:<br />-2147187899|El usuario de soporte no tiene permiso para realizar esta operación.|
> |**Nombre**:<br />InsufficientPrivilegeToQueueOwner<br />**Hex**:<br />80040520<br />**Número**:<br />-2147220192|El propietario de esta cola no tiene los privilegios suficientes para trabajar con la cola.|
> |**Nombre**:<br />InsufficientRetrievePrivilege<br />**Hex**:<br />80061109<br />**Número**:<br />-2147086071|Los proveedores externos no tiene suficientes privilegios de recuperar registro.|
> |**Nombre**:<br />InsufficientTransformationParameters<br />**Hex**:<br />80048506<br />**Número**:<br />-2147187450|Insuficientes parámetros para ejecutar la asignación de transformación.|
> |**Nombre**:<br />InsufficientUpdatePrivilege<br />**Hex**:<br />8006110B<br />**Número**:<br />-2147086069|Los proveedores externos no tiene suficientes privilegios de actualizar registro.|
> |**Nombre**:<br />IntegerValueOutOfRange<br />**Hex**:<br />8004432F<br />**Número**:<br />-2147204305|Se ha producido un error de validación. El número entero especificado no está comprendido en el intervalo de valores permitidos para este atributo.|
> |**Nombre**:<br />IntegratedAuthenticationIsNotAllowed<br />**Hex**:<br />80044301<br />**Número**:<br />-2147204351|No se permite la autenticación integrada.|
> |**Nombre**:<br />InvalidAbsoluteUrlFormat<br />**Hex**:<br />80048055<br />**Número**:<br />-2147188651|La URL absoluta contiene caracteres no válidos. Utilice un nombre diferente. La dirección url absoluta válida no termina con las siguientes cadenas: .aspx, .ashx, .asmx, .svc|
> |**Nombre**:<br />InvalidAccessMaskForTeamTemplate<br />**Hex**:<br />80048335<br />**Número**:<br />-2147187915|Máscara de acceso no válida se especificó para plantilla de equipo.|
> |**Nombre**:<br />InvalidAccessModeTransition<br />**Hex**:<br />80041d66<br />**Número**:<br />-2147213978|No se puede cambiar la licencia de acceso del cliente porque el usuario no tiene una licencia de Microsoft Dynamics 365 Online. Para cambiar el modo de acceso, primero debe agregar una licencia para este usuario en el portal de Microsoft Online Service.|
> |**Nombre**:<br />InvalidAccessRights<br />**Hex**:<br />8004020d<br />**Número**:<br />-2147220979|Derechos de acceso no válidos|
> |**Nombre**:<br />InvalidAccessRightsPassed<br />**Hex**:<br />80048347<br />**Número**:<br />-2147187897|Pasados derechos de acceso no válidos.|
> |**Nombre**:<br />InvalidActivityMimeAttachmentId<br />**Hex**:<br />80050005<br />**Número**:<br />-2147155963|activityMimeAttachmentId no válido.|
> |**Nombre**:<br />InvalidActivityOwnershipTypeMask<br />**Hex**:<br />8004F120<br />**Número**:<br />-2147159776|Una entidad personalizada que se define como una actividad debe ser propiedad de un usuario o equipo.|
> |**Nombre**:<br />InvalidActivityPartyAddress<br />**Hex**:<br />80043518<br />**Número**:<br />-2147207912|Uno o varios grupos de actividad tienen direcciones no válidas.|
> |**Nombre**:<br />InvalidActivityType<br />**Hex**:<br />80040321<br />**Número**:<br />-2147220703|Se especificó un tipo de objeto no válido para la distribución de las actividades.|
> |**Nombre**:<br />InvalidActivityTypeForCampaignActivityPropagate<br />**Hex**:<br />8004030f<br />**Número**:<br />-2147220721|Especifique un CommunicationActivity válido|
> |**Nombre**:<br />InvalidActivityTypeForList<br />**Hex**:<br />80040305<br />**Número**:<br />-2147220731|No se pueden crear actividades del tipo de lista especificado.|
> |**Nombre**:<br />InvalidActivityXml<br />**Hex**:<br />80043514<br />**Número**:<br />-2147207916|Xml no válido en un archivo de configuración de la actividad.|
> |**Nombre**:<br />InvalidAllotmentsCalc<br />**Hex**:<br />800404ef<br />**Número**:<br />-2147220241|Cobertura: restante + usada != total|
> |**Nombre**:<br />InvalidAllotmentsOverage<br />**Hex**:<br />8004430B<br />**Número**:<br />-2147204341|Excedente de cobertura no es válido.|
> |**Nombre**:<br />InvalidAllotmentsRemaining<br />**Hex**:<br />800404f2<br />**Número**:<br />-2147220238|La cobertura restante no es válida|
> |**Nombre**:<br />InvalidAllotmentsTotal<br />**Hex**:<br />800404f0<br />**Número**:<br />-2147220240|La cobertura total no es válida|
> |**Nombre**:<br />InvalidAllotmentsUsed<br />**Hex**:<br />800404f1<br />**Número**:<br />-2147220239|La cobertura utilizada no es válida|
> |**Nombre**:<br />InvalidAmountFreeResourceLimit<br />**Hex**:<br />8004B060<br />**Número**:<br />-2147176352|El tipo de recurso {0} no puede tener un valor libre de importe de {1}.|
> |**Nombre**:<br />InvalidAmountProvided<br />**Hex**:<br />8004B02D<br />**Número**:<br />-2147176403|El componente servicio {0} no puede tener un proveedor {1} del tipo de recurso {2}.|
> |**Nombre**:<br />InvalidAppModuleClientType<br />**Hex**:<br />80050126<br />**Número**:<br />-2147155674|El valor de tipo de cliente pasado es incorrecto y no corresponde a un intervalo válido.|
> |**Nombre**:<br />InvalidAppModuleComponent<br />**Hex**:<br />80050113<br />**Número**:<br />-2147155693|El identificador {0} no existe o no es válido para el tipo de componente "{1}".|
> |**Nombre**:<br />InvalidAppModuleComponentType<br />**Hex**:<br />80050112<br />**Número**:<br />-2147155694|Una aplicación no puede hacer referencia al tipo de componente "{0}".|
> |**Nombre**:<br />InvalidAppModuleEventHandlers<br />**Hex**:<br />8005012F<br />**Número**:<br />-2147155665|Los controladores de eventos proporcionados para la aplicación no son válidos.|
> |**Nombre**:<br />InvalidAppModuleId<br />**Hex**:<br />80050116<br />**Número**:<br />-2147155690|El id. de aplicación no es válido o no tiene acceso a la aplicación.|
> |**Nombre**:<br />InvalidAppModuleOptimizedFor<br />**Hex**:<br />8005013A<br />**Número**:<br />-2147155654|Los valores optimizados para la aplicación no son válidos.|
> |**Nombre**:<br />InvalidAppModuleSiteMap<br />**Hex**:<br />80050110<br />**Número**:<br />-2147155696|No se puede usar el mapa del sitio personalizado para este módulo de aplicación porque está configurado incorrectamente. Para resolver este problema, navegue por la experiencia completa para reparar el mapa del sitio personalizado y vuelva a importarlo.|
> |**Nombre**:<br />InvalidAppModuleSiteMapXml<br />**Hex**:<br />80050109<br />**Número**:<br />-2147155703|El mapa del sitio del módulo de la aplicación es válido.|
> |**Nombre**:<br />InvalidAppModuleUniqueName<br />**Hex**:<br />8005011E<br />**Número**:<br />-2147155682|El nombre único supera la longitud máxima de 40 caracteres o contiene caracteres no válidos. Solo se permiten letras y números.|
> |**Nombre**:<br />InvalidAppModuleUrl<br />**Hex**:<br />8005011A<br />**Número**:<br />-2147155686|La dirección URL de la aplicación no es única o el formato no es válido.|
> |**Nombre**:<br />InvalidAppointmentInstance<br />**Hex**:<br />8004E104<br />**Número**:<br />-2147163900|Instancia de entidad de cita no es válida.|
> |**Nombre**:<br />InvalidApproveFromDraftArticle<br />**Hex**:<br />80048dfd<br />**Número**:<br />-2147185155|Está intentando aprobar un artículo que tiene un estado de borrador. Solo puede aprobar un artículo con el estado de no autorizado.|
> |**Nombre**:<br />InvalidApproveFromPublishedArticle<br />**Hex**:<br />80048dfb<br />**Número**:<br />-2147185157|Está intentando aprobar un artículo que tiene un estado de publicado. Solo puede aprobar un artículo con el estado de no autorizado.|
> |**Nombre**:<br />InvalidArgument<br />**Hex**:<br />80040203<br />**Número**:<br />-2147220989|Argumento no válido.|
> |**Nombre**:<br />InvalidArticleState<br />**Hex**:<br />800404fb<br />**Número**:<br />-2147220229|El estado de artículo no está definido|
> |**Nombre**:<br />InvalidArticleStateTransition<br />**Hex**:<br />800404fc<br />**Número**:<br />-2147220228|Esta transición de estado del artículo no es válida debido al estado actual del artículo|
> |**Nombre**:<br />InvalidArticleTemplateState<br />**Hex**:<br />800404fd<br />**Número**:<br />-2147220227|El estado de la plantilla del artículo no está definido|
> |**Nombre**:<br />InvalidAssemblyProcessorArchitecture<br />**Hex**:<br />8004417E<br />**Número**:<br />-2147204738|El ensamblado de complementos determinado complemento se creó con una plataforma de destino no admitida y no se puede cargar.|
> |**Nombre**:<br />InvalidAssemblySourceType<br />**Hex**:<br />8004417D<br />**Número**:<br />-2147204739|No se admite este tipo de origen de ensamblado de complementos para ensamblados de complementos aislados.|
> |**Nombre**:<br />InvalidAssigneeId<br />**Hex**:<br />80040210<br />**Número**:<br />-2147220976|Identificador de usuario asignado no válido.|
> |**Nombre**:<br />InvalidAssociatedSavedQuery<br />**Hex**:<br />800609AE<br />**Número**:<br />-2147087954|La consulta guardada seleccionada no pertenece a la entidad asociada del elemento del perfil de Mobile Offline.|
> |**Nombre**:<br />InvalidAttachmentsFolder<br />**Hex**:<br />80048490<br />**Número**:<br />-2147187568|No se puede cargar el archivo comprimido (.zip) debido a que la carpeta "Adjuntos" contiene una o más subcarpetas. Quite las subcarpetas y vuelva a intentarlo.|
> |**Nombre**:<br />InvalidAttribute<br />**Hex**:<br />8005E009<br />**Número**:<br />-2147098615|No se encontró el atributo {0} para la entidad {1}.|
> |**Nombre**:<br />InvalidAttributeCopyTarget<br />**Hex**:<br />80048545<br />**Número**:<br />-2147187387|Un atributo de destino debe estar sin establecer o tener el mismo valor que el atributo de origen al copiar.|
> |**Nombre**:<br />InvalidAttributeDataType<br />**Hex**:<br />80044815<br />**Número**:<br />-2147203051|Tipo de datos de atributo: {0} no es válida para esta entidad.|
> |**Nombre**:<br />InvalidAttributeFieldType<br />**Hex**:<br />80044816<br />**Número**:<br />-2147203050|Tipo de campo de atributo: {0} no es válida para entidad virtual.|
> |**Nombre**:<br />InvalidAttributeFound<br />**Hex**:<br />8004E303<br />**Número**:<br />-2147163389|Un panel formulario XML no puede contener atributo: {0}.|
> |**Nombre**:<br />InvalidAttributeInXaml<br />**Hex**:<br />80060412<br />**Número**:<br />-2147089390|El atributo {0} en XAML no es válido.|
> |**Nombre**:<br />InvalidAttributeMap<br />**Hex**:<br />80046203<br />**Número**:<br />-2147196413|Se ha producido un error InvalidAttributeMap|
> |**Nombre**:<br />InvalidAttributeMapping<br />**Hex**:<br />80048438<br />**Número**:<br />-2147187656|Una o más asignaciones de atributos no son válidas.|
> |**Nombre**:<br />InvalidAttributeQuery<br />**Hex**:<br />80072527<br />**Número**:<br />-2147015385|Los atributos deben ser parte de las propiedades de EntityMetadata solicitadas cuando se especifica una AttributeQuery. Propiedad esperada = {0} en lista de propiedades de entidad solicitada.|
> |**Nombre**:<br />InvalidAuth<br />**Hex**:<br />80048516<br />**Número**:<br />-2147187434|La autenticación de la organización no coincide con el rol de servicio de detección actual.|
> |**Nombre**:<br />InvalidAuthTicket<br />**Hex**:<br />8004A100<br />**Número**:<br />-2147180288|El vale especificado para la autenticación no ha superado la validación|
> |**Nombre**:<br />InvalidBaseAttributeError<br />**Hex**:<br />80044242<br />**Número**:<br />-2147204542|Atributo base no válido.|
> |**Nombre**:<br />InvalidBaseUnit<br />**Hex**:<br />80043b0b<br />**Número**:<br />-2147206389|La unidad base no pertenece a la programación.|
> |**Nombre**:<br />InvalidBehavior<br />**Hex**:<br />800608A1<br />**Número**:<br />-2147088223|No se puede modificar el valor de comportamiento de este atributo.|
> |**Nombre**:<br />InvalidBehaviorSelection<br />**Hex**:<br />800608A0<br />**Número**:<br />-2147088224|El comportamiento de este campo Fecha y hora solo se puede cambiar a "Solo fecha".|
> |**Nombre**:<br />InvalidBlockList<br />**Hex**:<br />80090006<br />**Número**:<br />-2146893818|La operación de confirmación de archivo falló. La lista de bloqueo especificada no es válida o faltan algunos fragmentos para cargar.|
> |**Nombre**:<br />InvalidBrowserToConfigureOrganization<br />**Hex**:<br />8004D255<br />**Número**:<br />-2147167659|El explorador no es compatible para configurar la organización|
> |**Nombre**:<br />InvalidBusinessProcess<br />**Hex**:<br />80060389<br />**Número**:<br />-2147089527|Proceso de negocio no válido.|
> |**Nombre**:<br />InvalidCaller<br />**Hex**:<br />80040257<br />**Número**:<br />-2147220905|No puede cambiar de ExecutionContext al usuario del sistema sin establecer llamador primero.|
> |**Nombre**:<br />InvalidCascadeLinkType<br />**Hex**:<br />80048204<br />**Número**:<br />-2147188220|El tipo de vínculo en cascada no es válido para la acción en cascada.|
> |**Nombre**:<br />InvalidCategory<br />**Hex**:<br />8004E009<br />**Número**:<br />-2147164151|La categoría no es válida. Todas las medidas de la categoría, o no tienen el mismo grupo primario, o son una combinación de datos agregados y no agregados.|
> |**Nombre**:<br />InvalidCertificate<br />**Hex**:<br />8005E23A<br />**Número**:<br />-2147098054|El certificado especificado no es válido.|
> |**Nombre**:<br />InvalidChangeProcess<br />**Hex**:<br />80092002<br />**Número**:<br />-2146885630|Petición de cambio de estado del proceso no válida. El estado actual del proceso es {0}, el cual no puede pasar a {1}.|
> |**Nombre**:<br />InvalidChannelForCampaignActivityPropagate<br />**Hex**:<br />80040310<br />**Número**:<br />-2147220720|No puede distribuir actividades para actividades de campaña del tipo de canal especificado.|
> |**Nombre**:<br />InvalidChannelOrigin<br />**Hex**:<br />80060602<br />**Número**:<br />-2147088894|Ya existe un término de canal de derecho con el mismo canal. Especifique un canal diferente e inténtelo de nuevo.|
> |**Nombre**:<br />InvalidCharactersInField<br />**Hex**:<br />80040278<br />**Número**:<br />-2147220872|El campo '{0}' contiene uno o más caracteres no válidos.|
> |**Nombre**:<br />InvalidCharInConnectorName<br />**Hex**:<br />80072604<br />**Número**:<br />-2147015164|El nombre del conector debe ser alfanumérico, '-' o '_' y comenzar con alfanumérico.|
> |**Nombre**:<br />InvalidClassIdInReferencePanelSection<br />**Hex**:<br />80061503<br />**Número**:<br />-2147085053|La sección Panel de referencia solo puede tener controles de subcuadrícula, formulario de vista rápida, búsqueda en Knowledge Base, y recursos web i-frame y HTML. Encontrado control con classid no válido {0}.|
> |**Nombre**:<br />InvalidCollectionName<br />**Hex**:<br />8006088E<br />**Número**:<br />-2147088242|Ya existe una entidad con ese nombre de recopilación. Especifique un nombre único.|
> |**Nombre**:<br />InvalidColumnMapping<br />**Hex**:<br />80040377<br />**Número**:<br />-2147220617|ColumnMapping no es válido. Compruebe que existe el atributo de destino.|
> |**Nombre**:<br />InvalidColumnNumber<br />**Hex**:<br />80040336<br />**Número**:<br />-2147220682|El número de columna especificado en la asignación de datos no existe.|
> |**Nombre**:<br />InvalidCommand<br />**Hex**:<br />8005E100<br />**Número**:<br />-2147098368|Comando no válido.|
> |**Nombre**:<br />InvalidComplexControlId<br />**Hex**:<br />8005E103<br />**Número**:<br />-2147098365|El id. de control complejo no es válido.|
> |**Nombre**:<br />InvalidComponentType<br />**Hex**:<br />80072004<br />**Número**:<br />-2147016700|El tipo de componente {0} no pudo ser encontrado|
> |**Nombre**:<br />InvalidConnectionString<br />**Hex**:<br />8004023f<br />**Número**:<br />-2147220929|La cadena de conexión no se ha encuentro o no es válida.|
> |**Nombre**:<br />InvalidContentRangeForFileUpload<br />**Hex**:<br />80090005<br />**Número**:<br />-2146893819|El rango de contenido no es válido o el tamaño de la carga útil [{0}] no coincide con el tamaño del fragmento proporcionado.|
> |**Nombre**:<br />InvalidContractDetailId<br />**Hex**:<br />800404f6<br />**Número**:<br />-2147220234|El id. de detalles del contrato no es válido.|
> |**Nombre**:<br />InvalidControlClass<br />**Hex**:<br />8004E307<br />**Número**:<br />-2147163385|El panel formulario XML no puede contener elementos de control con el identificador de clase: {0}.|
> |**Nombre**:<br />InvalidConversionRule<br />**Hex**:<br />800608F6<br />**Número**:<br />-2147088138|La ConversionRule especificada {0} no es válida. Especifique una ConversionRule válida.|
> |**Nombre**:<br />InvalidCreateOnProtectedComponent<br />**Hex**:<br />8004F011<br />**Número**:<br />-2147160047|No puede crear {0} {1}. La creación no se puede realizar cuando {0} está administrada.|
> |**Nombre**:<br />InvalidCredentialTypeForNonExchangeIncomingConnection<br />**Hex**:<br />8005E214<br />**Número**:<br />-2147098092|Para un tipo de servidor de correo electrónico POP3, solamente puede conectarse mediante credenciales especificadas por un usuario o cola.|
> |**Nombre**:<br />InvalidCrmDateTime<br />**Hex**:<br />8004E103<br />**Número**:<br />-2147163901|CrmDateTime no válidas.|
> |**Nombre**:<br />InvalidCrossEntityOperation<br />**Hex**:<br />80092004<br />**Número**:<br />-2146885628|Transición de fase entre entidades no válida. Debe especificar la entidad de destino.|
> |**Nombre**:<br />InvalidCrossEntityTargetOperation<br />**Hex**:<br />80092005<br />**Número**:<br />-2146885627|Transición de fase entre entidades no válida. El destino especificado debe coincidir con {0}.|
> |**Nombre**:<br />InvalidCurrency<br />**Hex**:<br />80048cfc<br />**Número**:<br />-2147185412|La divisa no es válida.|
> |**Nombre**:<br />InvalidCustomActivityType<br />**Hex**:<br />8004F125<br />**Número**:<br />-2147159771|Una entidad personalizada que se define como una actividad debe ser del tipo de actividad de comunicación.|
> |**Nombre**:<br />InvalidCustomDataDownloadFilters<br />**Hex**:<br />80060996<br />**Número**:<br />-2147087978|No se pueden definir filtros de descarga personalizados porque Criterios de distribución de registros no se ha establecido en Otros filtros de datos.|
> |**Nombre**:<br />InvalidCustomer<br />**Hex**:<br />8004022d<br />**Número**:<br />-2147220947|El cliente no es válido.|
> |**Nombre**:<br />InvalidCustomerLookupXml<br />**Hex**:<br />80048051<br />**Número**:<br />-2147188655|La búsqueda de clientes Xml no es válida. Faltan una o más relaciones.|
> |**Nombre**:<br />InvalidCustomReportingWizardXml<br />**Hex**:<br />80040491<br />**Número**:<br />-2147220335|Asistente XML no válido|
> |**Nombre**:<br />InvalidDataDescription<br />**Hex**:<br />8004E000<br />**Número**:<br />-2147164160|La descripción de datos para la visualización no es válida.|
> |**Nombre**:<br />InvalidDataDownloadFilterBusinessUnit<br />**Hex**:<br />8005F222<br />**Número**:<br />-2147093982|Para una entidad propiedad del propietario del negocio, solo puede usar los siguientes filtros de descarga de datos: todos los registros o descarga únicamente de datos relacionados.|
> |**Nombre**:<br />InvalidDataDownloadFilterOrganization<br />**Hex**:<br />8005F223<br />**Número**:<br />-2147093981|Para una entidad propiedad la organización, solo puede usar los siguientes filtros de descarga de datos: todos los registros o descarga únicamente de datos relacionados.|
> |**Nombre**:<br />InvalidDataFiltersForBUOwnedEntities<br />**Hex**:<br />80060994<br />**Número**:<br />-2147087980|No se pueden definir los Registros de mi propiedad ni los Registros propiedad de mi equipo para las entidades que son propiedad de una unidad de negocio.|
> |**Nombre**:<br />InvalidDataFiltersForOrgOwnedEntities<br />**Hex**:<br />80060995<br />**Número**:<br />-2147087979|No se puede definir Otro filtro de datos para entidades que son propiedad de la organización.|
> |**Nombre**:<br />InvalidDataFiltersForUnownedEntities<br />**Hex**:<br />80060993<br />**Número**:<br />-2147087981|No se pueden definir los filtros Todos los tipos de registros u Otro filtro de datos para entidades sin propietario.|
> |**Nombre**:<br />InvalidDataFormat<br />**Hex**:<br />80040356<br />**Número**:<br />-2147220650|Los datos de origen no están en el formato necesario|
> |**Nombre**:<br />InvalidDataSourceEndPoint<br />**Hex**:<br />80044826<br />**Número**:<br />-2147203034|URI no válido: se debe proporcionar un URI completo sin una cadena de consulta.|
> |**Nombre**:<br />InvalidDataXml<br />**Hex**:<br />8005E101<br />**Número**:<br />-2147098367|Datos XML no válidos.|
> |**Nombre**:<br />InvalidDateAttribute<br />**Hex**:<br />80044805<br />**Número**:<br />-2147203067|El atributo de fecha especificado no es un atributo de entidad de origen.|
> |**Nombre**:<br />InvalidDateTime<br />**Hex**:<br />80040239<br />**Número**:<br />-2147220935|El formato de fecha y hora no es válido, o el valor no pertenece al intervalo admitido.|
> |**Nombre**:<br />InvalidDateTimeFormat<br />**Hex**:<br />800608A2<br />**Número**:<br />-2147088222|No puede cambiar el valor de formato de este atributo a "Fecha y hora" cuando el comportamiento es "Solo fecha".|
> |**Nombre**:<br />InvalidDaysInFebruary<br />**Hex**:<br />8004E124<br />**Número**:<br />-2147163868|29 de febrero solo puede ocurrir si el modelo de fecha de inicio está en año bisiesto.|
> |**Nombre**:<br />InvalidDeactivateFormType<br />**Hex**:<br />8004F660<br />**Número**:<br />-2147158432|No puede desactivar formularios {0}. Solo los formularios principales pueden estar inactivos.|
> |**Nombre**:<br />InvalidDeleteModification<br />**Hex**:<br />80048203<br />**Número**:<br />-2147188221|No se puede modificar la eliminación de una relación de sistema de acción en cascada .|
> |**Nombre**:<br />InvalidDeleteOnProtectedComponent<br />**Hex**:<br />8004F013<br />**Número**:<br />-2147160045|No puede eliminar {0} {1}. La eliminación no se puede realizar cuando {0} está administrada.|
> |**Nombre**:<br />InvalidDeleteProcess<br />**Hex**:<br />80060691<br />**Número**:<br />-2147088751|Este proceso no se puede eliminar porque está generado por el sistema.|
> |**Nombre**:<br />InvalidDependency<br />**Hex**:<br />8004F036<br />**Número**:<br />-2147160010|El {2} componente {1} (Id={0}) no existe.  Error al intentar asociar con {3} (identificador ={4}) como dependencia. Falta el tipo de búsqueda dependencia = {5}.|
> |**Nombre**:<br />InvalidDependencyComponent<br />**Hex**:<br />8004F040<br />**Número**:<br />-2147160000|El componente necesario {1} (identificador ={0}) que se ha definido para {2} no se encontró en el sistema.|
> |**Nombre**:<br />InvalidDependencyEntity<br />**Hex**:<br />8004F041<br />**Número**:<br />-2147159999|El componente necesario {1} (nombre ={0}) que se ha definido para {2} no se encontró en el sistema.|
> |**Nombre**:<br />InvalidDependencyFetchXml<br />**Hex**:<br />8004F037<br />**Número**:<br />-2147160009|El FetchXml ({2}) no es válido.  Error al calcular las dependencias para {1} (identificador ={0}).|
> |**Nombre**:<br />InvalidDeviceToConfigureOrganization<br />**Hex**:<br />8004D254<br />**Número**:<br />-2147167660|Los dispositivos móviles no se pueden usar para configurar la organización|
> |**Nombre**:<br />InvalidDisplayName<br />**Hex**:<br />8004700c<br />**Número**:<br />-2147192820|El nombre especificado no es válido|
> |**Nombre**:<br />InvalidDocumentTemplate<br />**Hex**:<br />800608CB<br />**Número**:<br />-2147088181|Plantilla de documento no válida.|
> |**Nombre**:<br />InvalidDomainName<br />**Hex**:<br />80048015<br />**Número**:<br />-2147188715|El inicio de sesión de dominio para este usuario no es válido. Seleccione otro inicio de sesión de dominio e inténtelo de nuevo.|
> |**Nombre**:<br />InvalidDundasPresentationDescription<br />**Hex**:<br />8004E016<br />**Número**:<br />-2147164138|La descripción de la presentación no es válida para gráfico de dundas.|
> |**Nombre**:<br />InvalidElementFound<br />**Hex**:<br />8004E300<br />**Número**:<br />-2147163392|Un panel formulario XML no puede contener elemento: {0}.|
> |**Nombre**:<br />InvalidEmail<br />**Hex**:<br />8004B016<br />**Número**:<br />-2147176426|El correo electrónico generado desde la plantilla no es válido|
> |**Nombre**:<br />InvalidEmailAddressFormat<br />**Hex**:<br />80044192<br />**Número**:<br />-2147204718|Dirección de correo electrónico no válida. Para obtener más información, póngase en contacto con el administrador del sistema.|
> |**Nombre**:<br />InvalidEmailAddressFormatWithEntityTypeAndId<br />**Hex**:<br />80040b0b<br />**Número**:<br />-2147218677|Dirección de correo electrónico no válida para el destinatario de tipo '{0}' con el identificador '{1}'|
> |**Nombre**:<br />InvalidEmailAddressInMailbox<br />**Hex**:<br />8005E221<br />**Número**:<br />-2147098079|La dirección de correo electrónico del buzón no es correcta. Escriba la dirección de correo electrónico correcta para procesar mensajes.|
> |**Nombre**:<br />InvalidEmailServerLocation<br />**Hex**:<br />8005E218<br />**Número**:<br />-2147098088|La ubicación del servidor falta o no es válida. Corrija la ubicación del servidor.|
> |**Nombre**:<br />InvalidEmailTemplate<br />**Hex**:<br />80040313<br />**Número**:<br />-2147220717|Especifique un id. de plantilla válido|
> |**Nombre**:<br />InvalidEntitlementActivate<br />**Hex**:<br />80060606<br />**Número**:<br />-2147088890|No puede activar un derecho expirado, en espera o cancelado.|
> |**Nombre**:<br />InvalidEntitlementAssociationToCase<br />**Hex**:<br />80060609<br />**Número**:<br />-2147088887|No puede crear un caso para este derecho porque no hay términos disponibles.|
> |**Nombre**:<br />InvalidEntitlementCancel<br />**Hex**:<br />80060607<br />**Número**:<br />-2147088889|No puede cancelar un derecho en estado de borrador o expirado.|
> |**Nombre**:<br />InvalidEntitlementChannelTerms<br />**Hex**:<br />80060605<br />**Número**:<br />-2147088891|Los términos totales de un origen del caso específico en un canal de derecho no pueden ser más que los términos totales del derecho correspondiente.|
> |**Nombre**:<br />InvalidEntitlementContacts<br />**Hex**:<br />80044207<br />**Número**:<br />-2147204601|El contacto especificado no está asociado al cliente seleccionado.|
> |**Nombre**:<br />InvalidEntitlementDeactivate<br />**Hex**:<br />80060608<br />**Número**:<br />-2147088888|Solo puede desactivar derechos que están activos o en espera|
> |**Nombre**:<br />InvalidEntitlementExpire<br />**Hex**:<br />80060618<br />**Número**:<br />-2147088872|No puede establecer un derecho en el estado Expirado. Los derechos de Active expiran automáticamente cuando se supera la fecha de finalización.|
> |**Nombre**:<br />InvalidEntitlementForSelectedCustomerOrProduct<br />**Hex**:<br />8004F866<br />**Número**:<br />-2147157914|Seleccione un derecho activo que pertenezca al cliente, contacto o producto especificados e inténtelo de nuevo.|
> |**Nombre**:<br />InvalidEntitlementRenew<br />**Hex**:<br />80060610<br />**Número**:<br />-2147088880|Solo puede renovar derechos que hayan expirado o que se hayan cancelado.|
> |**Nombre**:<br />InvalidEntitlementStateAssociateToCase<br />**Hex**:<br />80060611<br />**Número**:<br />-2147088879|Solo puede asociar un caso con un derecho activo.|
> |**Nombre**:<br />InvalidEntitlementTotalTerms<br />**Hex**:<br />800443FF<br />**Número**:<br />-2147204097|Los términos totales de un derecho no pueden ser menores que los términos totales de cualquiera de sus EntitlementChannels correspondientes.|
> |**Nombre**:<br />InvalidEntity<br />**Hex**:<br />8005E00C<br />**Número**:<br />-2147098612|La entidad {0} no se puede encontrar.|
> |**Nombre**:<br />InvalidEntityClassException<br />**Hex**:<br />80040249<br />**Número**:<br />-2147220919|Clase de ntidad no válida.|
> |**Nombre**:<br />InvalidEntityForDateAttribute<br />**Hex**:<br />80044812<br />**Número**:<br />-2147203054|La entidad para atributo de fecha puede ser la entidad de origen o bien su primaria.|
> |**Nombre**:<br />InvalidEntityForLinkedAttribute<br />**Hex**:<br />8004F0FD<br />**Número**:<br />-2147159811|Entidad no válida para el atributo vinculado.|
> |**Nombre**:<br />InvalidEntityForRollup<br />**Hex**:<br />80044813<br />**Número**:<br />-2147203053|La entidad {0} no es válida para el elemento consolidado.|
> |**Nombre**:<br />InvalidEntityKeyOperation<br />**Hex**:<br />8006088F<br />**Número**:<br />-2147088241|Se realizó una operación EntityKey no válida: {0}|
> |**Nombre**:<br />InvalidEntityLogicalName<br />**Hex**:<br />80072493<br />**Número**:<br />-2147015533|El nombre de entidad '{0}' no es un nombre lógico válido.|
> |**Nombre**:<br />InvalidEntityName<br />**Hex**:<br />80048416<br />**Número**:<br />-2147187690|El tipo de registro no coincide con el tipo de registro base y el tipo de registro coincidente de la regla de detección de duplicados.|
> |**Nombre**:<br />InvalidEntitySetName<br />**Hex**:<br />8006089B<br />**Número**:<br />-2147088229|Ya existe una entidad con el nombre de entidad especificado {0}. Especifique un nombre único.|
> |**Nombre**:<br />InvalidEntitySpecified<br />**Hex**:<br />800609B1<br />**Número**:<br />-2147087951|La entidad no está especificada en la plantilla.|
> |**Nombre**:<br />InvalidExchangeRate<br />**Hex**:<br />80048cfd<br />**Número**:<br />-2147185411|El tipo de cambio no es válido.|
> |**Nombre**:<br />InvalidExportProcessFlowNotActivated<br />**Hex**:<br />80060376<br />**Número**:<br />-2147089546|No se pudo exportar el proceso de negocio "{0}" porque la solución no incluye la entidad de proceso de negocio correspondiente "{1}". Si se trata de un proceso de negocio recién creado en estado de borrador, actívelo una vez para generar la entidad de proceso de negocio y para incluirla en la solución. Para obtener más información, consulte http://support.microsoft.com/kb/4337537.|
> |**Nombre**:<br />InvalidExternalCollectionName<br />**Hex**:<br />80046BA7<br />**Número**:<br />-2147193945|El nombre de colección externa especificado no es válido.|
> |**Nombre**:<br />InvalidExternalName<br />**Hex**:<br />80046BC0<br />**Número**:<br />-2147193920|El nombre externo especificado no es válido.|
> |**Nombre**:<br />InvalidExternalPartyConfiguration<br />**Hex**:<br />8006110F<br />**Número**:<br />-2147086065|Existen varios elementos de proveedores externos para parámetros de solicitud.|
> |**Nombre**:<br />InvalidExternalPartyOperation<br />**Hex**:<br />80061111<br />**Número**:<br />-2147086063|No se permite proveedor externo.|
> |**Nombre**:<br />InvalidExternalPartyParent<br />**Hex**:<br />80061110<br />**Número**:<br />-2147086064|El proveedor externo tiene un atributo primario no válido.|
> |**Nombre**:<br />InvalidFeatureType<br />**Hex**:<br />80044272<br />**Número**:<br />-2147204494|El tipo de característica no es válido.|
> |**Nombre**:<br />InvalidFetchCollection<br />**Hex**:<br />8004E019<br />**Número**:<br />-2147164135|La colección de Fetch para la visualización no es válida.|
> |**Nombre**:<br />InvalidFetchXml<br />**Hex**:<br />80040303<br />**Número**:<br />-2147220733|FetchXml con estructura incorrecta.|
> |**Nombre**:<br />InvalidFileAttributeName<br />**Hex**:<br />80090007<br />**Número**:<br />-2146893817|Nombre de atributo no válido para el archivo: [{0}].|
> |**Nombre**:<br />InvalidFileBadCharacters<br />**Hex**:<br />80040396<br />**Número**:<br />-2147220586|No se pudo cargar el archivo porque contiene caracteres no válidos|
> |**Nombre**:<br />InvalidFileRangeRequested<br />**Hex**:<br />80090000<br />**Número**:<br />-2146893824|El intervalo de fragmentos utilizado en esta llamada no es válido o es mayor de los {0} MB permitidos.|
> |**Nombre**:<br />InvalidFileType<br />**Hex**:<br />800608CC<br />**Número**:<br />-2147088180|Tipo de archivo no válido.|
> |**Nombre**:<br />InvalidFilterCriteriaForVisualization<br />**Hex**:<br />8004E01E<br />**Número**:<br />-2147164130|No se pudo representar la visualización para los criterios de filtro indicados.|
> |**Nombre**:<br />InvalidFiscalPeriod<br />**Hex**:<br />80044814<br />**Número**:<br />-2147203052|El período fiscal {0} no se encuentra en el intervalo permitido de períodos fiscales según la configuración fiscal de la organización.|
> |**Nombre**:<br />InvalidFlowProcessClientData<br />**Hex**:<br />80060468<br />**Número**:<br />-2147089304|Los datos del cliente de flujo no tienen un formato válido. Detalles: "{0}".|
> |**Nombre**:<br />InvalidFormatForControl<br />**Hex**:<br />80060875<br />**Número**:<br />-2147088267|Parámetro de precisión no válido especificado para control {0}. No contiene el valor previsto|
> |**Nombre**:<br />InvalidFormatForDataDelimiter<br />**Hex**:<br />80040355<br />**Número**:<br />-2147220651|El delimitador de datos no coincide: sólo se encontró un delimitador.|
> |**Nombre**:<br />InvalidFormatForUpdateMode<br />**Hex**:<br />8004F601<br />**Número**:<br />-2147158527|El archivo que cargó no es válido y no puede usarse para actualizar registros.|
> |**Nombre**:<br />InvalidFormatParameters<br />**Hex**:<br />80047101<br />**Número**:<br />-2147192575|El número de parámetros de formato pasado a la cadena de entrada es incorrecto|
> |**Nombre**:<br />InvalidFormType<br />**Hex**:<br />8004E306<br />**Número**:<br />-2147163386|El tipo de formulario se debe establecer en {0} en el formulario XML.|
> |**Nombre**:<br />InvalidFormTypeCalledThroughSdk<br />**Hex**:<br />80060874<br />**Número**:<br />-2147088268|"Se ha usado un Formtype no válido en llamada de creación|
> |**Nombre**:<br />InvalidForOfficeGraph<br />**Hex**:<br />80044231<br />**Número**:<br />-2147204559|Una o ambas entidades de no están habilitadas para officegraph y no se pueden usar para officegraph.|
> |**Nombre**:<br />InvalidGoalAttribute<br />**Hex**:<br />8004480b<br />**Número**:<br />-2147203061|El atributo objetivo no coincide con el tipo de métrica especificado.|
> |**Nombre**:<br />InvalidGoalManager<br />**Hex**:<br />8004F684<br />**Número**:<br />-2147158396|El administrador de un objetivo solo puede ser un usuario y no un equipo.|
> |**Nombre**:<br />InvalidGranularityValue<br />**Hex**:<br />8004B038<br />**Número**:<br />-2147176392|El valor de la columna Granularidad es incorrecto. Cada parte de la regla debe ser un par de nombre-valor separado por un signo igual (=). Por ejemplo: frecuencia = minutos; intervalo = 15|
> |**Nombre**:<br />InvalidGroupByAlias<br />**Hex**:<br />8004E00F<br />**Número**:<br />-2147164145|Descripción de datos no válida El mismo grupo por alias no se puede usar para diferentes atributos.|
> |**Nombre**:<br />InvalidGroupByColumn<br />**Hex**:<br />8004E01D<br />**Número**:<br />-2147164131|Grupo no permitido en el atributo.|
> |**Nombre**:<br />InvalidGuid<br />**Hex**:<br />80040363<br />**Número**:<br />-2147220637|El identificador único global (GUID) de esta fila no es válido|
> |**Nombre**:<br />InvalidGuidInXaml<br />**Hex**:<br />80060407<br />**Número**:<br />-2147089401|GUID - {0} en el Xaml no es válido|
> |**Nombre**:<br />InvalidHeaderColumn<br />**Hex**:<br />80040344<br />**Número**:<br />-2147220668|El encabezado de columna contiene una combinación no válida de delimitadores de datos.|
> |**Nombre**:<br />InvalidHexColorValue<br />**Hex**:<br />800608D0<br />**Número**:<br />-2147088176|Solo se permiten valores hexadecimales.|
> |**Nombre**:<br />InvalidHierarchicalRelationship<br />**Hex**:<br />8004701F<br />**Número**:<br />-2147192801|Esta relación no se hace referencia a sí misma y por ello no puede ser jerárquica.|
> |**Nombre**:<br />InvalidHierarchicalRelationshipChange<br />**Hex**:<br />8004701a<br />**Número**:<br />-2147192806|No puede cambiar esta jerarquía de la entidad porque la relación jerárquica {0} no se puede personalizar.|
> |**Nombre**:<br />InvalidIconFileFormatForConnector<br />**Hex**:<br />80072603<br />**Número**:<br />-2147015165|Formato de archivo de icono no válido. Los formatos admitidos son PNG y JPG.|
> |**Nombre**:<br />InvalidImportFileContent<br />**Hex**:<br />80040374<br />**Número**:<br />-2147220620|El contenido del archivo de importación no es válido. Debe seleccionar un archivo de texto.|
> |**Nombre**:<br />InvalidImportFileData<br />**Hex**:<br />80040351<br />**Número**:<br />-2147220655|Los datos no tienen el formato necesario|
> |**Nombre**:<br />InvalidImportFileParseData<br />**Hex**:<br />80040349<br />**Número**:<br />-2147220663|No se especificaron los delimitadores de campo y de datos de este archivo.|
> |**Nombre**:<br />InvalidImportJobId<br />**Hex**:<br />80044252<br />**Número**:<br />-2147204526|El importjob solicitado no existe.|
> |**Nombre**:<br />InvalidImportJobTemplateFile<br />**Hex**:<br />80044251<br />**Número**:<br />-2147204527|El archivo ImportJobTemplate.xml no es válido.|
> |**Nombre**:<br />InvalidIncomingDeliveryExpectingEmailConnector<br />**Hex**:<br />8005E224<br />**Número**:<br />-2147098076|El método de entrega entrante no es conector de correo electrónico. Para recibir mensajes, su método de entrega entrante debe ser Conector de correo electrónico.|
> |**Nombre**:<br />InvalidInputArgumentForModernFlowExecute<br />**Hex**:<br />80060480<br />**Número**:<br />-2147089280|No se puede ejecutar Modern Flow '{0}' porque '{1}' no es un argumento de entrada compatible.|
> |**Nombre**:<br />InvalidInstanceEntityName<br />**Hex**:<br />8004E10D<br />**Número**:<br />-2147163891|Nombre de instancia de entidad no válido.|
> |**Nombre**:<br />InvalidInstanceTypeCode<br />**Hex**:<br />8004E107<br />**Número**:<br />-2147163897|Código de tipo de instancia no válido.|
> |**Nombre**:<br />InvalidInteractiveUserQuota<br />**Hex**:<br />8004B049<br />**Número**:<br />-2147176375|Ha alcanzado el número máximo de usuarios inactivos/completos.|
> |**Nombre**:<br />InvalidIntersectEntity<br />**Hex**:<br />80072540<br />**Número**:<br />-2147015360|No puede usar una entidad existente que no se cruza {0} como una entidad de intersección para definir relaciones de varios a varios.|
> |**Nombre**:<br />InvalidInvitationLiveId<br />**Hex**:<br />8004D20E<br />**Número**:<br />-2147167730|No se encontró un usuario con esta dirección de correo electrónico. Inicie sesión en Windows Live ID con la misma dirección de correo electrónico en la que recibió la invitación.  Si no tiene un Windows Live ID, cree uno con la dirección de correo electrónico.|
> |**Nombre**:<br />InvalidInvitationToken<br />**Hex**:<br />8004D20D<br />**Número**:<br />-2147167731|El token invitación {0} no tiene el formato correcto.|
> |**Nombre**:<br />InvalidIsFirstRowHeaderForUseSystemMap<br />**Hex**:<br />80040364<br />**Número**:<br />-2147220636|La primera fila del archivo no contiene encabezados de columna.|
> |**Nombre**:<br />InvalidIsoCurrencyCode<br />**Hex**:<br />80048cf2<br />**Número**:<br />-2147185422|Código de divisa ISO no válido.|
> |**Nombre**:<br />InvalidKeyQuery<br />**Hex**:<br />80072529<br />**Número**:<br />-2147015383|Las claves deben ser parte de las propiedades de EntityMetadata solicitadas cuando se especifica una KeyQuery. Propiedad esperada = {0} en lista de propiedades de entidad solicitada.|
> |**Nombre**:<br />InvalidKit<br />**Hex**:<br />80043afd<br />**Número**:<br />-2147206403|El producto no es un kit.|
> |**Nombre**:<br />InvalidKitProduct<br />**Hex**:<br />80043afe<br />**Número**:<br />-2147206402|No puede agregar un kit de productos a él mismo. Seleccione un producto diferente o kit de productos.|
> |**Nombre**:<br />InvalidLanguageCode<br />**Hex**:<br />80044195<br />**Número**:<br />-2147204715|El código de idioma especificado no es válido para esta organización.|
> |**Nombre**:<br />InvalidLanguageForCreate<br />**Hex**:<br />80060750<br />**Número**:<br />-2147088560|Las filas con atributos localizables solo se pueden crear cuando el idioma de la interfaz de usuario (UI) para el usuario actual se establece en el idioma base de la organización.|
> |**Nombre**:<br />InvalidLanguageForProcessConfiguration<br />**Hex**:<br />8005E102<br />**Número**:<br />-2147098366|La configuración del proceso no está disponibles porque el idioma no coincide con el idioma base del sistema.|
> |**Nombre**:<br />InvalidLanguageForSolution<br />**Hex**:<br />80047019<br />**Número**:<br />-2147192807|Las opciones de la solución y el publicador no están disponibles porque el idioma no coincide con el idioma base del sistema.|
> |**Nombre**:<br />InvalidLanguageForUpdate<br />**Hex**:<br />80060751<br />**Número**:<br />-2147088559|Los atributos localizables solo se pueden actualizar vía propieda de cadena cuando el idioma de la interfaz de usuario (UI) para el usuario actual se establece en el idioma base de la organización. Utilice SetLocLabels para actualizar los valores localizados para los siguientes atributos: [{0}].|
> |**Nombre**:<br />InvalidLicenseCannotReadMpcFile<br />**Hex**:<br />8004D245<br />**Número**:<br />-2147167675|Licencia no válida. No se puede leer el código MPC del archivo MPC.txt con esta ruta {0}.|
> |**Nombre**:<br />InvalidLicenseKey<br />**Hex**:<br />8004D240<br />**Número**:<br />-2147167680|Tipo de clave de licencia ({0}) no válido.|
> |**Nombre**:<br />InvalidLicenseMpcCode<br />**Hex**:<br />8004D246<br />**Número**:<br />-2147167674|Licencia no válida. Código MPC ({0}) no válido.|
> |**Nombre**:<br />InvalidLicensePid<br />**Hex**:<br />8004D242<br />**Número**:<br />-2147167678|Licencia no válida. Id del producto no válido ({0}).|
> |**Nombre**:<br />InvalidLicensePidGenCannotLoad<br />**Hex**:<br />8004D243<br />**Número**:<br />-2147167677|Licencia no válida. PidGen.dll no se puede cargar desde esta ruta {0}|
> |**Nombre**:<br />InvalidLicensePidGenOtherError<br />**Hex**:<br />8004D244<br />**Número**:<br />-2147167676|Licencia no válida. No se puede generar PID (Id. del producto) de clave de licencia. Código de error de PidGen ({0}).|
> |**Nombre**:<br />InvalidLocaleIdForKnowledgeArticle<br />**Hex**:<br />80061400<br />**Número**:<br />-2147085312|Idioma con ID local {0}, no existe|
> |**Nombre**:<br />InvalidLogoImageId<br />**Hex**:<br />800608D3<br />**Número**:<br />-2147088173|Id. no válido de recurso web de imagen de logotipo.|
> |**Nombre**:<br />InvalidLogoImageWebResourceType<br />**Hex**:<br />800608D9<br />**Número**:<br />-2147088167|Tipo WebResource no válido para imagen de logotipo.|
> |**Nombre**:<br />InvalidLookupMapNode<br />**Hex**:<br />80048481<br />**Número**:<br />-2147187583|La entidad de búsqueda suministrada no es válida para el atributo de destino indicado.|
> |**Nombre**:<br />InvalidMailbox<br />**Hex**:<br />8005E217<br />**Número**:<br />-2147098089|El mailboxId introducido no es válido. Compruebe el mailboxid.|
> |**Nombre**:<br />InvalidManagedPropertyException<br />**Hex**:<br />8004F030<br />**Número**:<br />-2147160016|La propiedad administrada {0} no contiene suficiente información para ser creada.  Proporcione (conjunto, clase), o (entidad, atributo) o establezca la propiedad administrada para personalizar.|
> |**Nombre**:<br />InvalidManifestFilePath<br />**Hex**:<br />80048533<br />**Número**:<br />-2147187405|No puede encontrar el archivo de manifiesto en la ubicación especificada|
> |**Nombre**:<br />InvalidMatchingAttributeError<br />**Hex**:<br />80044244<br />**Número**:<br />-2147204540|Atributo coincidente no válido.|
> |**Nombre**:<br />InvalidMaximumResourceLimit<br />**Hex**:<br />8004B02B<br />**Número**:<br />-2147176405|El tipo de recurso {0} no puede tener un límite máximo de {1}.|
> |**Nombre**:<br />InvalidMaxLengthForControl<br />**Hex**:<br />80060879<br />**Número**:<br />-2147088263|Se ha especificado un parámetro MaxLength no válido para el control {0}. Maxlength debe encontrarse entre {1} y {2}.|
> |**Nombre**:<br />InvalidMaxSizeInKB<br />**Hex**:<br />80090009<br />**Número**:<br />-2146893815|Tamaño no válido para el atributo de tipo de archivo. El tamaño válido debe estar entre [0-{0}] KB|
> |**Nombre**:<br />InvalidMaxValueForControl<br />**Hex**:<br />8006087B<br />**Número**:<br />-2147088261|Se ha especificado un parámetro MaxValue no válido para el control {0}. MaxValue debe encontrarse entre {1} y {2}.|
> |**Nombre**:<br />InvalidMeasureCollection<br />**Hex**:<br />8004E00A<br />**Número**:<br />-2147164150|La colección de medida no es válida. No todas las medidas de la colección de medidas deben tener el mismo group bys.|
> |**Nombre**:<br />InvalidMetadata<br />**Hex**:<br />8004023a<br />**Número**:<br />-2147220934|Metadatos no válidos.|
> |**Nombre**:<br />InvalidMetadataSqlOperation<br />**Hex**:<br />80072343<br />**Número**:<br />-2147015869|Se ha lanzado una excepción SQL en la operación actual de metadatos. Compruebe la excepción para obtener más detalles.|
> |**Nombre**:<br />InvalidMigrationFileContent<br />**Hex**:<br />8005F033<br />**Número**:<br />-2147094477|El contenido del archivo de importación no es válido. Debe seleccionar un archivo de texto.|
> |**Nombre**:<br />InvalidMinAndMaxValueForControl<br />**Hex**:<br />8006087C<br />**Número**:<br />-2147088260|Se han especificado unos parámetros MinValue y MaxValue no válidos para el control {0}. MinValue debe ser inferior a MaxValue.|
> |**Nombre**:<br />InvalidMinimumResourceLimit<br />**Hex**:<br />8004B02A<br />**Número**:<br />-2147176406|El tipo de recurso {0} no puede tener un límite mínimo de {1}.|
> |**Nombre**:<br />InvalidMinValueForControl<br />**Hex**:<br />8006087A<br />**Número**:<br />-2147088262|Se ha especificado un parámetro MinValue no válido para el control {0}. MinValue debe encontrarse entre {1} y {2}.|
> |**Nombre**:<br />InvalidMobileOfflineFiltersFetchXml<br />**Hex**:<br />80071113<br />**Número**:<br />-2147020525|No coincide el formato XML. Compruebe la exactitud de XML.|
> |**Nombre**:<br />InvalidMultipleMapping<br />**Hex**:<br />80048498<br />**Número**:<br />-2147187560|Un campo de origen está asignado a más de un campo de Dynamics 365 del tipo de búsqueda o lista desplegable.|
> |**Nombre**:<br />InvalidMultipleSiteMapReferenceSingleAppModule<br />**Hex**:<br />80050111<br />**Número**:<br />-2147155695|Una aplicación no puede tener varios mapas del sitio.|
> |**Nombre**:<br />InvalidNamePrefix<br />**Hex**:<br />80044366<br />**Número**:<br />-2147204250|El nombre de eseuqme {0} para el tipo {2} no es válido o falta. Los nombres personalizados de atributo, entidad, entitykey, conjunto de opciones y relación deben empezar por un prefijo de personalización válido. El prefijo para un componente de la solución debe coincidir con el prefijo especificado para el publicador de la solución.|
> |**Nombre**:<br />InvalidNetPrice<br />**Hex**:<br />800404f3<br />**Número**:<br />-2147220237|El precio neto no es válido|
> |**Nombre**:<br />InvalidNonInteractiveUserQuota<br />**Hex**:<br />8004B050<br />**Número**:<br />-2147176368|Ha alcanzado el número máximo de usuarios no inactivos/|
> |**Nombre**:<br />InvalidNumberGroupFormat<br />**Hex**:<br />80043700<br />**Número**:<br />-2147207424|Cadena de entrada no válida para numbergroupformat. La cadena de entrada debe contener una matriz de enteros. Cada elemento de la matriz de valor debe estar entre uno y nueve, excepto el último elemento, que puede ser cero.|
> |**Nombre**:<br />InvalidNumberOfCardFormSections<br />**Hex**:<br />80061505<br />**Número**:<br />-2147085051|El número de secciones de un formulario de tarjeta debe ser 4. Encontrado {0}.|
> |**Nombre**:<br />InvalidNumberOfParametersForFileUpload<br />**Hex**:<br />80090002<br />**Número**:<br />-2146893822|Número de parámetros no válido [{0}] proporcionado en la URL de solicitud.|
> |**Nombre**:<br />InvalidNumberOfPartitions<br />**Hex**:<br />8004E200<br />**Número**:<br />-2147163648|No se pueden eliminar datos de auditoría en las particiones que estén actualmente en uso ni eliminar las particiones que se han creado para almacenar datos de auditoría futuros.|
> |**Nombre**:<br />InvalidNumberOfReferencePanelSections<br />**Hex**:<br />80061504<br />**Número**:<br />-2147085052|El formulario MainInteractionCentric solo puede tener una sección de panel de referencia. Encontrado {0}.|
> |**Nombre**:<br />InvalidNumberOfSectionsInTab<br />**Hex**:<br />80060872<br />**Número**:<br />-2147088270|Un XML de formulario de diálogo no puede contener más de una sección.|
> |**Nombre**:<br />InvalidNumberOfTabsInDialog<br />**Hex**:<br />80060871<br />**Número**:<br />-2147088271|Un XML de formulario de diálogo no puede contener más de una pestaña.|
> |**Nombre**:<br />InvalidOAuthToken<br />**Hex**:<br />80041d50<br />**Número**:<br />-2147214000|El token OAuth no es válido|
> |**Nombre**:<br />InvalidObjectTypeCode<br />**Hex**:<br />80072005<br />**Número**:<br />-2147016699|No se encuentra el código de tipo de objeto {0}. Son metadatos: {1}|
> |**Nombre**:<br />InvalidObjectTypes<br />**Hex**:<br />8004021f<br />**Número**:<br />-2147220961|Tipo de objeto no válido.|
> |**Nombre**:<br />InvalidOccurrenceNumber<br />**Hex**:<br />8004E125<br />**Número**:<br />-2147163867|La fecha de finalización efectiva de la serie no puede ser anterior a la actual. Seleccione un número de incidencia válido.|
> |**Nombre**:<br />InvalidOfflineOperation<br />**Hex**:<br />8004410e<br />**Número**:<br />-2147204850|Operación no válida sin conexión.|
> |**Nombre**:<br />InvalidOneToManyRelationship<br />**Hex**:<br />80072500<br />**Número**:<br />-2147015424|La relación entre entidades OneToMany con EntityRelationshipId '{0}' tiene ReferencingEntityRole nulo|
> |**Nombre**:<br />InvalidOneToManyRelationshipForRelatedEntitiesQuery<br />**Hex**:<br />8004430F<br />**Número**:<br />-2147204337|Se ha especificado un OneToManyRelationship no válido para RelatedEntitiesQuery. La entidad a la que se hace referencia {0} debe tener el mismo que la entidad principal {1}|
> |**Nombre**:<br />InvalidOperandOnLeftHandSide<br />**Hex**:<br />80072501<br />**Número**:<br />-2147015423|El lateral izquierdo del operador '{0}' debe ser una propiedad de la entidad.|
> |**Nombre**:<br />InvalidOperation<br />**Hex**:<br />8004023b<br />**Número**:<br />-2147220933|Se realizó una operación no válida.|
> |**Nombre**:<br />InvalidOperationForClosedOrCancelledCampaignActivity<br />**Hex**:<br />80040314<br />**Número**:<br />-2147220716|No se pueden agregar elementos a la campaignactivity cerrada (cancelada).|
> |**Nombre**:<br />InvalidOperationForDynamicList<br />**Hex**:<br />8004F701<br />**Número**:<br />-2147158271|Esta acción no está disponible para una lista de marketing dinámica.|
> |**Nombre**:<br />InvalidOperationWhenBusinessRuleIsActive<br />**Hex**:<br />80060015<br />**Número**:<br />-2147090411|Operación no válida: no puede activar o desactivar esta regla empresarial|
> |**Nombre**:<br />InvalidOperationWhenListIsNotActive<br />**Hex**:<br />8004033a<br />**Número**:<br />-2147220678|La lista no está activa. No se puede realizar esta operación.|
> |**Nombre**:<br />InvalidOperationWhenListLocked<br />**Hex**:<br />80040302<br />**Número**:<br />-2147220734|La lista está bloqueada. No se puede realizar esta acción.|
> |**Nombre**:<br />InvalidOperationWhenPartyIsNotActive<br />**Hex**:<br />8004033b<br />**Número**:<br />-2147220677|La parte no está activa. No se puede realizar esta operación.|
> |**Nombre**:<br />InvalidOperatorCode<br />**Hex**:<br />80048415<br />**Número**:<br />-2147187691|El operador no es válido o no se admite.|
> |**Nombre**:<br />InvalidOperatorCodeError<br />**Hex**:<br />80044253<br />**Número**:<br />-2147204525|Código de operador no válido.|
> |**Nombre**:<br />InvalidOptionSetIdForControl<br />**Hex**:<br />80060876<br />**Número**:<br />-2147088266|Se ha especificado un OptionSetld no válido para el control {0}. OptionSetId es un GUID no vacío.|
> |**Nombre**:<br />InvalidOptionSetNameChange<br />**Hex**:<br />80048409<br />**Número**:<br />-2147187703|No se puede actualizar el nombre de OptionSet {0}, Id.: {1} porque el valor proporcionado de nombre de OptionSet ({2}) está en uso por otro OptionSet existente (Id.: {3})|
> |**Nombre**:<br />InvalidOptionSetOperation<br />**Hex**:<br />80048403<br />**Número**:<br />-2147187709|OptionSet no válido|
> |**Nombre**:<br />InvalidOptionSetSchemaName<br />**Hex**:<br />80044345<br />**Número**:<br />-2147204283|Ya existe un OptionSet con el nombre especificado. Especifique un nombre exclusivo.|
> |**Nombre**:<br />InvalidOrEmptyRelationshipId<br />**Hex**:<br />80071122<br />**Número**:<br />-2147020510|El id. de relación de la asociación del elemento de perfil móvil no es válido o está vacío.|
> |**Nombre**:<br />InvalidOrganizationFriendlyName<br />**Hex**:<br />8004D252<br />**Número**:<br />-2147167662|El nombre descriptivo de la organización ({0}) no es válido. Motivo: ({1})|
> |**Nombre**:<br />InvalidOrganizationId<br />**Hex**:<br />80044248<br />**Número**:<br />-2147204536|El Id. de organización presente en el archivo de transacciones no coincide con el identificador de la organización actual.|
> |**Nombre**:<br />InvalidOrganizationSettings<br />**Hex**:<br />8006110D<br />**Número**:<br />-2147086067|La configuración de la organización no se ha configurado correctamente para los proveedores externos.|
> |**Nombre**:<br />InvalidOrganizationUniqueName<br />**Hex**:<br />8004D251<br />**Número**:<br />-2147167663|Nombre único de la organización no válido ({0}). Motivo: ({1})|
> |**Nombre**:<br />InvalidOrgDBOrgSetting<br />**Hex**:<br />80048514<br />**Número**:<br />-2147187436|La configuración introducida de la organización no es válida. Compruebe el tipo de datos introduzca un valor correspondiente.|
> |**Nombre**:<br />InvalidOrgOwnedCascadeLinkType<br />**Hex**:<br />80044156<br />**Número**:<br />-2147204778|La propiedad del usuario de cascada no es un tipo de vínculo de cascada válido para relaciones entre entidades propiedad de la organización.|
> |**Nombre**:<br />InvalidOtherDataFilterOptions<br />**Hex**:<br />8006098D<br />**Número**:<br />-2147087987|Debe seleccionar al menos una opción en Descargar mis registros, Descargar los registros de mi equipo o Descargar los registros de mi unidad de negocio en Otro filtro de datos|
> |**Nombre**:<br />InvalidOutgoingDeliveryExpectingEmailConnector<br />**Hex**:<br />8005E226<br />**Número**:<br />-2147098074|El método de entrega saliente no es conector de correo electrónico. Para enviar mensajes, su método de entrega saliente debe ser Conector de correo electrónico.|
> |**Nombre**:<br />InvalidOwnerID<br />**Hex**:<br />80040229<br />**Número**:<br />-2147220951|El identificador de propietario falta o no es válido.|
> |**Nombre**:<br />InvalidOwnershipTypeMask<br />**Hex**:<br />8004700d<br />**Número**:<br />-2147192819|La máscara de tipo de propiedad especificada no es válida para esta operación|
> |**Nombre**:<br />InvalidPageResponse<br />**Hex**:<br />8004E00D<br />**Número**:<br />-2147164147|Respuesta de página no válida generada.|
> |**Nombre**:<br />InvalidParameterForFileOperation<br />**Hex**:<br />80090003<br />**Número**:<br />-2146893821|Parámetro no válido [{0}] proporcionado en la URL de solicitud.|
> |**Nombre**:<br />InvalidParent<br />**Hex**:<br />80040205<br />**Número**:<br />-2147220987|El objeto primario falta o no es válido.|
> |**Nombre**:<br />InvalidParentChildCascadeBehavior<br />**Hex**:<br />8007200D<br />**Número**:<br />-2147016691|Relación Primario-Elemento secundario {0} requiere un comportamiento jerárquico en cascada.|
> |**Nombre**:<br />InvalidParentChildRelationshipUpdate<br />**Hex**:<br />8007200B<br />**Número**:<br />-2147016693|No puede actualizar la relación de tipo ParentChild.|
> |**Nombre**:<br />InvalidParentId<br />**Hex**:<br />80040206<br />**Número**:<br />-2147220986|El identificador primario falta o no es válido.|
> |**Nombre**:<br />InvalidPartnerSolutionCustomizationProvider<br />**Hex**:<br />8004A109<br />**Número**:<br />-2147180279|Tipo de proveedor de personalización de solución asociada no válido|
> |**Nombre**:<br />InvalidPartyMapping<br />**Hex**:<br />80043515<br />**Número**:<br />-2147207915|La asignación de entidad no es válida.|
> |**Nombre**:<br />InvalidPluginAssemblyContent<br />**Hex**:<br />8004418b<br />**Número**:<br />-2147204725|El ensamblado de complementos no contiene los tipos necesarios o no se puede actualizar el contenido del ensamblado.|
> |**Nombre**:<br />InvalidPluginAssemblyVersion<br />**Hex**:<br />8004417B<br />**Número**:<br />-2147204741|Los nombres completos del ensamblado de complemento deben ser únicos (omitir la compilación de la versión y el número de revisión).|
> |**Nombre**:<br />InvalidPluginRegistrationConfiguration<br />**Hex**:<br />80044170<br />**Número**:<br />-2147204752|La configuración de registro del ensamblado de complementos no es válida.|
> |**Nombre**:<br />InvalidPluginStrongNameRequired<br />**Hex**:<br />80081114<br />**Número**:<br />-2146954988|El ensamblado de complemento no está indicado como nombre de alta seguridad.|
> |**Nombre**:<br />InvalidPluginTypeImplementation<br />**Hex**:<br />8004418c<br />**Número**:<br />-2147204724|El tipo de complemento debe implementar exactamente uno de las siguientes clases o la interfaces: Microsoft.Crm.Sdk.IPlugin, Microsoft.Xrm.Sdk.IPlugin, System.Activities.Activity y System.Workflow.ComponentModel.Activity.|
> |**Nombre**:<br />InvalidPointer<br />**Hex**:<br />80040218<br />**Número**:<br />-2147220968|Se desecha el objeto.|
> |**Nombre**:<br />InvalidPostponeUntilTimeForModernFlowExecute<br />**Hex**:<br />80060478<br />**Número**:<br />-2147089288|No se puede ejecutar Modern Flow '{0}' porque '{1}' no está en un formato DateTimeOffset admitido.|
> |**Nombre**:<br />InvalidPrecisionForControl<br />**Hex**:<br />8006087D<br />**Número**:<br />-2147088259|Se ha especificado un parámetro Precision no válido para el control {0}. Precision debe encontrarse entre {1} y {2}.|
> |**Nombre**:<br />InvalidPrefixInConnectorName<br />**Hex**:<br />80072605<br />**Número**:<br />-2147015163|El nombre del conector debe comenzar con un prefijo alfanumérico con una longitud entre 2~8 y seguido de '_' y nombre alfanumérico.|
> |**Nombre**:<br />InvalidPresentationDescription<br />**Hex**:<br />8004E002<br />**Número**:<br />-2147164158|La descripción de la presentación no es válida.|
> |**Nombre**:<br />InvalidPreviewModeOperation<br />**Hex**:<br />8005f219<br />**Número**:<br />-2147093991|No puede hacer esta operación en modo de vista previa.|
> |**Nombre**:<br />InvalidPriceLevelCurrencyForPricingMethod<br />**Hex**:<br />80048cf9<br />**Número**:<br />-2147185415|La divisa de la lista de precios debe coincidir con la divisa del producto para el porcentaje del método de cálculo de precios.|
> |**Nombre**:<br />InvalidPricePerUnit<br />**Hex**:<br />80043b10<br />**Número**:<br />-2147206384|El precio unitario no es válido.|
> |**Nombre**:<br />InvalidPrimaryContactBasedOnAccount<br />**Hex**:<br />8004F864<br />**Número**:<br />-2147157916|El contacto especificado no pertenece a la cuenta seleccionada como cliente. Especifique un contacto que pertenezca a la cuenta seleccionada e inténtelo de nuevo.|
> |**Nombre**:<br />InvalidPrimaryContactBasedOnContact<br />**Hex**:<br />8004F865<br />**Número**:<br />-2147157915|El contacto especificado no pertenece al contacto que se especificó en el campo de cliente. Quite el valor del campo de contacto o seleccione un contacto asociado al cliente seleccionado e inténtelo de nuevo.|
> |**Nombre**:<br />InvalidPrimaryFieldForActivity<br />**Hex**:<br />8004F127<br />**Número**:<br />-2147159769|Una entidad personalizada que se define como una actividad no puede tener atributo principal distintos del tema.|
> |**Nombre**:<br />InvalidPrimaryFieldType<br />**Hex**:<br />8004700e<br />**Número**:<br />-2147192818|El atributo principal de la interfaz de usuario debe ser del tipo String|
> |**Nombre**:<br />InvalidPrimaryKey<br />**Hex**:<br />80040266<br />**Número**:<br />-2147220890|Clave principal no válida.|
> |**Nombre**:<br />InvalidPrincipalId<br />**Hex**:<br />80048348<br />**Número**:<br />-2147187896|El GUID pasado está vacío.|
> |**Nombre**:<br />InvalidPrincipalType<br />**Hex**:<br />80048346<br />**Número**:<br />-2147187898|Pasado tipo principal no válido.|
> |**Nombre**:<br />InvalidPriv<br />**Hex**:<br />8004024b<br />**Número**:<br />-2147220917|Tipo de privilegios no válido.|
> |**Nombre**:<br />InvalidPrivilegeDepth<br />**Hex**:<br />8004140b<br />**Número**:<br />-2147216373|Profundidad de privilegios no válida.|
> |**Nombre**:<br />InvalidProcessControlAttribute<br />**Hex**:<br />8005E105<br />**Número**:<br />-2147098363|La definición de control de proceso contiene un atributo no válido.|
> |**Nombre**:<br />InvalidProcessControlEntity<br />**Hex**:<br />8005E104<br />**Número**:<br />-2147098364|La definición de control de proceso contiene una entidad u orden de entidad no válidos.|
> |**Nombre**:<br />InvalidProcessIdOperation<br />**Hex**:<br />80092001<br />**Número**:<br />-2146885631|Operación no válida. No se puede modificar el identificador de proceso.|
> |**Nombre**:<br />InvalidProcessStateData<br />**Hex**:<br />80045049<br />**Número**:<br />-2147200951|ProcessState no es válido para la instancia ProcessSession indicada.|
> |**Nombre**:<br />InvalidProduct<br />**Hex**:<br />80060623<br />**Número**:<br />-2147088861|No puede agregar una familia de productos.|
> |**Nombre**:<br />InvalidPublisherUniqueName<br />**Hex**:<br />8004F01C<br />**Número**:<br />-2147160036|Es necesario el nombre único del publicador.|
> |**Nombre**:<br />InvalidPublishOnProtectedComponent<br />**Hex**:<br />8004F014<br />**Número**:<br />-2147160044|No se puede publicar {0} {1}. La publicación no se puede realizar cuando {0} se administra.|
> |**Nombre**:<br />InvalidQuantityDecimalCode<br />**Hex**:<br />80043afc<br />**Número**:<br />-2147206404|El código decimal de cantidad no es válido.|
> |**Nombre**:<br />InvalidQuery<br />**Hex**:<br />80044183<br />**Número**:<br />-2147204733|La consulta especificada para esta operación no es válida|
> |**Nombre**:<br />InvalidQueryForVirtualEntity<br />**Hex**:<br />80044822<br />**Número**:<br />-2147203038|La consulta especificada no es compatible con una entidad virtual.|
> |**Nombre**:<br />InvalidRecurrenceInterval<br />**Hex**:<br />8004D2A1<br />**Número**:<br />-2147167583|Para establecer la periodicidad, debe especificar un intervalo comprendido entre 1 y 365.|
> |**Nombre**:<br />InvalidRecurrenceIntervalForRollupJobs<br />**Hex**:<br />8004D2A2<br />**Número**:<br />-2147167582|Para establecer la periodicidad, debe especificar un intervalo que sea superior a 1 hora.|
> |**Nombre**:<br />InvalidRecurrencePattern<br />**Hex**:<br />8004E100<br />**Número**:<br />-2147163904|Patrón de periodicidad no válido.|
> |**Nombre**:<br />InvalidRecurrenceRule<br />**Hex**:<br />80040246<br />**Número**:<br />-2147220922|Error en RecurrencePatternFactory.|
> |**Nombre**:<br />InvalidRecurrenceRuleForBulkDeleteAndDuplicateDetection<br />**Hex**:<br />8004D2A0<br />**Número**:<br />-2147167584|Debe especificar como diaria la frecuencia de eliminación en masa y detección de duplicados.|
> |**Nombre**:<br />InvalidReferencesFound<br />**Hex**:<br />80072032<br />**Número**:<br />-2147016654|Referencias no válidas encontradas: {0}|
> |**Nombre**:<br />InvalidRegardingObjectTypeCode<br />**Hex**:<br />80040319<br />**Número**:<br />-2147220711|El código de tipo de objeto referente no es válido para la operación masiva.|
> |**Nombre**:<br />InvalidRegistryKey<br />**Hex**:<br />8004024c<br />**Número**:<br />-2147220916|Clave de registro especificada no válida.|
> |**Nombre**:<br />InvalidRelationshipDescription<br />**Hex**:<br />80047003<br />**Número**:<br />-2147192829|La relación especificada no se puede crear|
> |**Nombre**:<br />InvalidRelationshipInMOPIAssociation<br />**Hex**:<br />80060999<br />**Número**:<br />-2147087975|No existe esta relación con la entidad seleccionada en el elemento de perfil primario.|
> |**Nombre**:<br />InvalidRelationshipNameForControl<br />**Hex**:<br />80060877<br />**Número**:<br />-2147088265|No se ha especificado Nombre de relación para el control {0}. Nombre de relación es un campo obligatorio.|
> |**Nombre**:<br />InvalidRelationshipQuery<br />**Hex**:<br />80072528<br />**Número**:<br />-2147015384|Al menos una de las propiedades de relación debe ser parte de las propiedades de EntityMetadata solicitadas cuando se especifica una RelationshipQuery. Deberá esperar por lo menos una propiedad = {0}, {1} o {2} en la lista de propiedades de la entidad solicitada.|
> |**Nombre**:<br />InvalidRelationshipType<br />**Hex**:<br />8004700f<br />**Número**:<br />-2147192817|El tipo de relación especificada no es válido para esta operación|
> |**Nombre**:<br />InvalidRelationshipTypeForAccessory<br />**Hex**:<br />8004F989<br />**Número**:<br />-2147157623|Una relación de accesorio siempre es unidireccional y no se puede cambiar.|
> |**Nombre**:<br />InvalidRelationshipTypeForUpSell<br />**Hex**:<br />8004F988<br />**Número**:<br />-2147157624|Una relación de incremento de ventas siempre es unidireccional y no se puede cambiar.|
> |**Nombre**:<br />InvalidRelativeUrlFormat<br />**Hex**:<br />80048054<br />**Número**:<br />-2147188652|La URL relativa contiene caracteres no válidos. Utilice un nombre diferente. Los nombres de dirección URL relativa válidos no pueden terminar con las siguientes cadenas: .aspx, .ashx, .asmx, .svc, no pueden comenzar o terminar con un punto, no pueden contener puntos consecutivos y no pueden contener ninguno de los siguientes caracteres: ~ " # % & * : < > ? / \ { | }.|
> |**Nombre**:<br />InvalidRequestBody<br />**Hex**:<br />80072530<br />**Número**:<br />-2147015376|El objeto de entidad pasado no puede ser nulo o estar vacío.|
> |**Nombre**:<br />InvalidRequestDataFormat<br />**Hex**:<br />80044271<br />**Número**:<br />-2147204495|La configuración actualizada incluye datos no válidos.|
> |**Nombre**:<br />InvalidRequestParameter<br />**Hex**:<br />80044828<br />**Número**:<br />-2147203032|Se deben especificar el nombre y el valor del parámetro de solicitud.|
> |**Nombre**:<br />InvalidRequestParameters<br />**Hex**:<br />8006110E<br />**Número**:<br />-2147086066|Los parámetros de la solicitud no son válidos para la parte externa del servidor.|
> |**Nombre**:<br />InvalidResourceType<br />**Hex**:<br />8004B029<br />**Número**:<br />-2147176407|La acción solicitada no es válida para el tipo de recurso {0}.|
> |**Nombre**:<br />InvalidRestore<br />**Hex**:<br />80040258<br />**Número**:<br />-2147220904|Debe llamarse RestoreCaller después de SwitchToSystemUser.|
> |**Nombre**:<br />InvalidRoboticProcessAutomationFlowProcessClientData<br />**Hex**:<br />80060473<br />**Número**:<br />-2147089293|Clientdata no tiene un formato válido. Detalles: "{0}".|
> |**Nombre**:<br />InvalidRole<br />**Hex**:<br />8004B012<br />**Número**:<br />-2147176430|No ha asignado roles de a este usuario|
> |**Nombre**:<br />InvalidRoleOccurrencesForOneToManyRelationship<br />**Hex**:<br />8006089A<br />**Número**:<br />-2147088230|No puede haber más de dos roles de relación de entidad para una relación de uno a varios {0}.|
> |**Nombre**:<br />InvalidRoleTypeForOneToManyRelationship<br />**Hex**:<br />80060899<br />**Número**:<br />-2147088231|Este tipo de rol de relación no es válido para una relación de uno a varios {0}.|
> |**Nombre**:<br />InvalidRollupQueryAttributeSet<br />**Hex**:<br />8004F683<br />**Número**:<br />-2147158397|No se puede establecer una consulta consolidada para un campo consolidado que no esté definida en la métrica del objetivo.|
> |**Nombre**:<br />InvalidRollupType<br />**Hex**:<br />80040234<br />**Número**:<br />-2147220940|El tipo consolidado no es válido.|
> |**Nombre**:<br />InvalidS2SAuthentication<br />**Hex**:<br />8005E245<br />**Número**:<br />-2147098043|Puede usar la autenticación de servidor a servidor solo para los perfiles de servidor de correo electrónico creados para una organización de Microsoft Dynamics 365 Online que se haya configurado a través del entorno de Microsoft Online Services (Office 365).|
> |**Nombre**:<br />InvalidSchemaName<br />**Hex**:<br />8004700b<br />**Número**:<br />-2147192821|Ya existe una entidad de con el nombre especificado. Especifique un nombre exclusivo.|
> |**Nombre**:<br />InvalidSearchEntities<br />**Hex**:<br />80060202<br />**Número**:<br />-2147089918|Búsqueda - {0} no se ha encontrado ninguna entidad válida.|
> |**Nombre**:<br />InvalidSearchEntity<br />**Hex**:<br />80060201<br />**Número**:<br />-2147089919|Entidad de búsqueda no válida - {0}.|
> |**Nombre**:<br />InvalidSearchName<br />**Hex**:<br />80060204<br />**Número**:<br />-2147089916|Nombre de búsqueda no válido - {0}.|
> |**Nombre**:<br />InvalidSeriesId<br />**Hex**:<br />8004E105<br />**Número**:<br />-2147163899|SeriesId es nulo o no es válido.|
> |**Nombre**:<br />InvalidSeriesIdOriginalStart<br />**Hex**:<br />8004E109<br />**Número**:<br />-2147163895|Seriesid o la fecha de inicio original no válida.|
> |**Nombre**:<br />InvalidSeriesStatus<br />**Hex**:<br />8004E10F<br />**Número**:<br />-2147163889|Estado de series no válido.|
> |**Nombre**:<br />InvalidSharee<br />**Hex**:<br />8004020c<br />**Número**:<br />-2147220980|Identificador de compartir no es válido.|
> |**Nombre**:<br />InvalidSharePointSiteCollectionUrl<br />**Hex**:<br />80048052<br />**Número**:<br />-2147188654|La dirección URL debe cumplir el esquema http o https.|
> |**Nombre**:<br />InvalidSimilarityRuleStateError<br />**Hex**:<br />80044254<br />**Número**:<br />-2147204524|Estado de la regla de similitud no válido.|
> |**Nombre**:<br />InvalidSingletonResults<br />**Hex**:<br />8004024f<br />**Número**:<br />-2147220913|Excepciones internas de CRM: Consulta de recuperación de Singleton no debería devolver más de 1 registro.|
> |**Nombre**:<br />InvalidSiteRelativeUrlFormat<br />**Hex**:<br />80048053<br />**Número**:<br />-2147188653|La URL relativa contiene caracteres no válidos. Utilice un nombre diferente. Los nombres de dirección URL relativa válidos no pueden terminar con las siguientes cadenas: .aspx, .ashx, .asmx, .svc, no pueden comenzar o terminar con un punto ni /, no pueden contener puntos consecutivos ni / y no pueden contener ninguno de los siguientes caracteres: ~ " # % & * : < > ? \ { | }.|
> |**Nombre**:<br />InvalidSolutionAwarenessDeclaration<br />**Hex**:<br />80072000<br />**Número**:<br />-2147016704|Una entidad no puede ser declarada como compatible con la solución en una operación de actualización. Entidad: {0}|
> |**Nombre**:<br />InvalidSolutionComponentKey<br />**Hex**:<br />8007200E<br />**Número**:<br />-2147016690|El atributo {0} de la clave {1} y entidad {2} debe ser exportable para ser una clave de exportación.|
> |**Nombre**:<br />InvalidSolutionConfigurationPage<br />**Hex**:<br />8004701B<br />**Número**:<br />-2147192805|La página de configuración especificada para esta solución no es válida.|
> |**Nombre**:<br />InvalidSolutionDependencies<br />**Hex**:<br />80072006<br />**Número**:<br />-2147016698|Todos los componentes presentes en esta solución tienen dependencias. Esto no está permitido ya que la desinstalación de esta solución sería inaccesible.|
> |**Nombre**:<br />InvalidSolutionUniqueName<br />**Hex**:<br />8004F002<br />**Número**:<br />-2147160062|Carácter no válido especificado para el nombre único de la solución. Solo están permitidos caracteres dentro de los rangos [A-Z] [a-z], [0-9] o _. El primer carácter solo puede estar en los intervalos [A-z] [a-z] o _.|
> |**Nombre**:<br />InvalidSolutionVersion<br />**Hex**:<br />8004F01E<br />**Número**:<br />-2147160034|Se especificó una versión de la solución no válida.|
> |**Nombre**:<br />InvalidSourceAttributeType<br />**Hex**:<br />80044808<br />**Número**:<br />-2147203064|El tipo de atributo de origen no coincide con el tipo de datos de importe especificado.|
> |**Nombre**:<br />InvalidSourceEntityAttribute<br />**Hex**:<br />80044806<br />**Número**:<br />-2147203066|El atributo {0} no es un atributo de entidad {1}.|
> |**Nombre**:<br />InvalidSourceStateValue<br />**Hex**:<br />80044810<br />**Número**:<br />-2147203056|El estado de origen especificado para la entidad no es válido.|
> |**Nombre**:<br />InvalidSourceStatusValue<br />**Hex**:<br />80044811<br />**Número**:<br />-2147203055|El estado de origen especificado para la entidad no es válido.|
> |**Nombre**:<br />InvalidSourceType<br />**Hex**:<br />80060437<br />**Número**:<br />-2147089353|El tipo de origen {0} no es válido para el tipo de datos {1}.|
> |**Nombre**:<br />InvalidSourceTypeCode<br />**Hex**:<br />800608EA<br />**Número**:<br />-2147088150|Seleccione el contenedor de propiedades válido para el tipo de origen seleccionado.|
> |**Nombre**:<br />InvalidStage<br />**Hex**:<br />80060452<br />**Número**:<br />-2147089326|Error de validación: fase no válida.|
> |**Nombre**:<br />InvalidStageTransition<br />**Hex**:<br />80092003<br />**Número**:<br />-2146885629|Transición de fase no válida. La transición a escenario {0} no está en la ruta activa del proceso.|
> |**Nombre**:<br />InvalidStageTransitionOnInactiveInstance<br />**Hex**:<br />80060377<br />**Número**:<br />-2147089545|Transición de fase no válida. La transición de fase no está permitida en procesos inactivos.|
> |**Nombre**:<br />InvalidState<br />**Hex**:<br />80040233<br />**Número**:<br />-2147220941|El objeto no está en un estado válido para realizar esta operación.|
> |**Nombre**:<br />InvalidStateCodeStatusCode<br />**Hex**:<br />80048408<br />**Número**:<br />-2147187704|El código de estado no es válido, o es válido pero el código de estatus no es válido para un código de estado especificado.|
> |**Nombre**:<br />InvalidStateForPublish<br />**Hex**:<br />8004F90A<br />**Número**:<br />-2147157750|La ProductFamily, el producto o la agrupación especificados solo se pueden publicar del estado de borrador o ActiveDraft|
> |**Nombre**:<br />InvalidStateTransition<br />**Hex**:<br />8004F00E<br />**Número**:<br />-2147160050|La entidad o el componente {0} (Id.={1}) ha intentado hacer la transición de un estado no válido: {2}.|
> |**Nombre**:<br />InvalidSubmitFromPublishedArticle<br />**Hex**:<br />80048dfa<br />**Número**:<br />-2147185158|Está intentando enviar un artículo que tiene un estado de publicado. Solo puede enviar un artículo con el estado de borrador.|
> |**Nombre**:<br />InvalidSubmitFromUnapprovedArticle<br />**Hex**:<br />80048dff<br />**Número**:<br />-2147185153|Está intentando enviar un artículo que tiene un estado de no aprobado. Solo puede enviar un artículo con el estado de borrador.|
> |**Nombre**:<br />InvalidSubstituteProduct<br />**Hex**:<br />80043aff<br />**Número**:<br />-2147206401|Un producto no puede estar relacionado consigo mismo.|
> |**Nombre**:<br />InvalidSyncDirectionValueForUpdate<br />**Hex**:<br />80060742<br />**Número**:<br />-2147088574|La dirección de sincronización no es válida según la dirección de sincronización permitida para una o varias asignaciones de atributos.|
> |**Nombre**:<br />InvalidSyncToken<br />**Hex**:<br />80072515<br />**Número**:<br />-2147015403|Token de sincronización no válido|
> |**Nombre**:<br />InvalidTargetEntity<br />**Hex**:<br />80040369<br />**Número**:<br />-2147220631|El tipo de registro de destino especificado no existe.|
> |**Nombre**:<br />InvalidTargetEntityTypeForControl<br />**Hex**:<br />80060878<br />**Número**:<br />-2147088264|No se ha especificado Tipo de entidad de destino para el control {0}. Entidad de destino es un campo obligatorio.|
> |**Nombre**:<br />InvalidTargetFrameworkVersion<br />**Hex**:<br />8004420b<br />**Número**:<br />-2147204597|El ensamblado de complemento tiene como destino una versión de .NET Framework que no es compatible.|
> |**Nombre**:<br />InvalidTaskFlow<br />**Hex**:<br />80060392<br />**Número**:<br />-2147089518|El flujo de tarea no es válido.|
> |**Nombre**:<br />InvalidTemplate<br />**Hex**:<br />8004B010<br />**Número**:<br />-2147176432|La plantilla del correo electrónico de invitación no es válida|
> |**Nombre**:<br />InvalidTemplateContent<br />**Hex**:<br />800609B2<br />**Número**:<br />-2147087950|El contenido de la plantilla no es válido.|
> |**Nombre**:<br />InvalidTemplateId<br />**Hex**:<br />80050019<br />**Número**:<br />-2147155943|No es una plantilla válida.|
> |**Nombre**:<br />InvalidTenantIDValue<br />**Hex**:<br />8005E25B<br />**Número**:<br />-2147098021|El valor de ID inquilino en línea de Exchange Online no es válido. El valor del campo debe ser una cadena en la estructura de GUID.|
> |**Nombre**:<br />InvalidThemeDeleteOperation<br />**Hex**:<br />800608D7<br />**Número**:<br />-2147088169|No puede eliminar temas del sistema o predeterminados.|
> |**Nombre**:<br />InvalidThemeId<br />**Hex**:<br />800608D4<br />**Número**:<br />-2147088172|Identificador de tema no válido.|
> |**Nombre**:<br />InvalidTimeZoneCode<br />**Hex**:<br />800608F7<br />**Número**:<br />-2147088137|El código de zona horaria {0} especificado no se reconoce. Especifique un valor de código de zona horaria válido.|
> |**Nombre**:<br />InvalidToDeleteFileAttachmentBulkDelete<br />**Hex**:<br />8009000A<br />**Número**:<br />-2146893814|Los trabajos de eliminación masiva de archivos adjuntos no se pueden eliminar.|
> |**Nombre**:<br />InvalidToken<br />**Hex**:<br />8004B061<br />**Número**:<br />-2147176351|El token no es válido.|
> |**Nombre**:<br />InvalidTotalDiscount<br />**Hex**:<br />800404f4<br />**Número**:<br />-2147220236|El descuento total no es válido|
> |**Nombre**:<br />InvalidTotalPrice<br />**Hex**:<br />800404f5<br />**Número**:<br />-2147220235|El precio total no es válido|
> |**Nombre**:<br />InvalidTransformationParameter<br />**Hex**:<br />80040389<br />**Número**:<br />-2147220599|Falta el parámetro de transformación o no es válido.|
> |**Nombre**:<br />InvalidTransformationParameterDataType<br />**Hex**:<br />80040380<br />**Número**:<br />-2147220608|No se admite el tipo de datos de uno o varios de los parámetros de transformación.|
> |**Nombre**:<br />InvalidTransformationParameterEmptyCollection<br />**Hex**:<br />80048511<br />**Número**:<br />-2147187439|El parámetro de transformación {0} tiene una longitud de valor de entrada no válida: {1}. La longitud del parámetro no puede ser una colección vacía.|
> |**Nombre**:<br />InvalidTransformationParameterMapping<br />**Hex**:<br />80040382<br />**Número**:<br />-2147220606|La asignación de parámetros de transformación definida no es válida. Compruebe que existe el nombre del atributo de destino.|
> |**Nombre**:<br />InvalidTransformationParameterMappings<br />**Hex**:<br />8004037c<br />**Número**:<br />-2147220612|Una o varias asignaciones de parámetros de transformación no son válidas o no coinciden con la descripción del parámetro de transformación.|
> |**Nombre**:<br />InvalidTransformationParameterOutsideRange<br />**Hex**:<br />80048510<br />**Número**:<br />-2147187440|El parámetro de transformación {0} tiene un valor de entrada no válido: {1}. El parámetro está fuera del intervalo válido: {2}. |
> |**Nombre**:<br />InvalidTransformationParameterOutsideRangeGeneric<br />**Hex**:<br />80048512<br />**Número**:<br />-2147187438|Uno o más valores de parámetros de transformación de entrada están fuera del rango permitido {0}.|
> |**Nombre**:<br />InvalidTransformationParametersGeneric<br />**Hex**:<br />80048507<br />**Número**:<br />-2147187449|El parámetro de transformación {0} tiene un valor de entrada no válido: {1}. El parámetro debe ser de tipo: {2}.|
> |**Nombre**:<br />InvalidTransformationParameterString<br />**Hex**:<br />80048508<br />**Número**:<br />-2147187448|El parámetro de transformación {0} tiene un valor de entrada no válido: {1}. El parámetro debe ser una cadena que no está vacía.|
> |**Nombre**:<br />InvalidTransformationParameterZeroToRange<br />**Hex**:<br />80048509<br />**Número**:<br />-2147187447|El parámetro de transformación {0} tiene un valor de entrada no válido: {1}. El valor del parámetro debe ser mayor que 0 y menor que la longitud del parámetro 1.|
> |**Nombre**:<br />InvalidTransformationType<br />**Hex**:<br />8004037a<br />**Número**:<br />-2147220614|No se admite el tipo de transformación especificado.|
> |**Nombre**:<br />InvalidTranslationsFile<br />**Hex**:<br />80044249<br />**Número**:<br />-2147204535|El archivo de traducciones no es válido o no se confirma con el esquema requerido.|
> |**Nombre**:<br />InvalidTraversedPath<br />**Hex**:<br />80092007<br />**Número**:<br />-2146885625|Ruta recorrida no válida.|
> |**Nombre**:<br />InvalidUniqueName<br />**Hex**:<br />80060386<br />**Número**:<br />-2147089530|Nombre único no válido para la acción.|
> |**Nombre**:<br />InvalidUnpublishFromDraftArticle<br />**Hex**:<br />80048dfc<br />**Número**:<br />-2147185156|Está intentando eliminar la publicación de un artículo que tiene un estado de borrador. Solo puede eliminar la publicación de un artículo con el estado de publicado.|
> |**Nombre**:<br />InvalidUnpublishFromUnapprovedArticle<br />**Hex**:<br />80048dfe<br />**Número**:<br />-2147185154|Está intentando eliminar la publicación de un artículo que tiene un estado de no aprobado. Solo puede eliminar la publicación de un artículo con el estado de publicar.|
> |**Nombre**:<br />InvalidUpdateOnProtectedComponent<br />**Hex**:<br />8004F012<br />**Número**:<br />-2147160046|No puede actualizar {0} {1}. La actualización no se puede realizar cuando {0} está administrada.|
> |**Nombre**:<br />InvalidUrlConsecutiveSlashes<br />**Hex**:<br />80048056<br />**Número**:<br />-2147188650|La dirección Url contiene barras consecutivas que no se permiten.|
> |**Nombre**:<br />InvalidUrlProtocol<br />**Hex**:<br />8004E30F<br />**Número**:<br />-2147163377|La URL especificada no es válida.|
> |**Nombre**:<br />InvalidUserAuth<br />**Hex**:<br />80040204<br />**Número**:<br />-2147220988|El usuario no tiene privilegios para realizar esta acción.|
> |**Nombre**:<br />InvalidUserLicenseCount<br />**Hex**:<br />8004B027<br />**Número**:<br />-2147176409|No puede adquirir {0} licencias de usuario para la oferta {1}.|
> |**Nombre**:<br />InvalidUserName<br />**Hex**:<br />80048095<br />**Número**:<br />-2147188587|Debe escribir el nombre de usuario con el formato <name>@<domain>. Solucione el formato e inténtelo de nuevo.|
> |**Nombre**:<br />InvalidUserQuota<br />**Hex**:<br />8004B011<br />**Número**:<br />-2147176431|Ha alcanzado el número máximo de cuota de usuario|
> |**Nombre**:<br />InvalidUserToImportExcelOnlineFile<br />**Hex**:<br />80060807<br />**Número**:<br />-2147088377|No tiene permiso para importar este archivo. Solo el usuario que exporta estos datos puede importar este archivo.|
> |**Nombre**:<br />InvalidUserToViewExcelOnlineFile<br />**Hex**:<br />80060806<br />**Número**:<br />-2147088378|No tiene permiso para ver este archivo. Solo el usuario que exporta estos datos puede visualizar este archivo.|
> |**Nombre**:<br />InvalidValueForCountryCode<br />**Hex**:<br />8004B022<br />**Número**:<br />-2147176414|La cuenta de código de país o región no puede ser {0}|
> |**Nombre**:<br />InvalidValueForCurrency<br />**Hex**:<br />8004B023<br />**Número**:<br />-2147176413|La cuenta de código de divisa no puede ser {0}|
> |**Nombre**:<br />InvalidValueForDataDelimiter<br />**Hex**:<br />80040341<br />**Número**:<br />-2147220671|El delimitador de datos no es válido.|
> |**Nombre**:<br />InvalidValueForFieldDelimiter<br />**Hex**:<br />80040340<br />**Número**:<br />-2147220672|El delimitador de campo no es válido.|
> |**Nombre**:<br />InvalidValueForFileType<br />**Hex**:<br />80040348<br />**Número**:<br />-2147220664|El tipo de archivo no es válido.|
> |**Nombre**:<br />InvalidValueForLocale<br />**Hex**:<br />8004B024<br />**Número**:<br />-2147176412|La cuenta de código local no puede ser {0}|
> |**Nombre**:<br />InvalidValueProcessEmailAfter<br />**Hex**:<br />8005E244<br />**Número**:<br />-2147098044|La fecha en el campo Procesar correo electrónico desde es anterior a la que se permite para su organización. Especifique una fecha posterior a la especificada e inténtelo de nuevo.|
> |**Nombre**:<br />InvalidVersion<br />**Hex**:<br />8004023c<br />**Número**:<br />-2147220932|Se encontró un error de coincidencia de versión no controlada.|
> |**Nombre**:<br />InvalidViewReference<br />**Hex**:<br />800609B3<br />**Número**:<br />-2147087949|La vista no se ha especificado o no es válida.|
> |**Nombre**:<br />InvalidWebResourceForVisualization<br />**Hex**:<br />8004E017<br />**Número**:<br />-2147164137|El tipo de recurso web {0} no se admite para visualizaciones.|
> |**Nombre**:<br />InvalidWebresourceId<br />**Hex**:<br />8005012B<br />**Número**:<br />-2147155669|El identificador del recurso web no es válido.|
> |**Nombre**:<br />InvalidWebresourceType<br />**Hex**:<br />8005012D<br />**Número**:<br />-2147155667|El recurso web proporcionado para el icono de la aplicación no es válido.|
> |**Nombre**:<br />InvalidWebToLeadRedirect<br />**Hex**:<br />80048476<br />**Número**:<br />-2147187594|El redirectto no es válido para el redireccionamiento web2lead.|
> |**Nombre**:<br />InvalidWelcomePageId<br />**Hex**:<br />8005012C<br />**Número**:<br />-2147155668|El identificador de la página principal no es válido.|
> |**Nombre**:<br />InvalidWelcomePageType<br />**Hex**:<br />8005012E<br />**Número**:<br />-2147155666|El recurso web proporcionado para la página principal de la aplicación no es válido.|
> |**Nombre**:<br />InvalidWordDocumentTemplate<br />**Hex**:<br />800608EF<br />**Número**:<br />-2147088145|La plantilla del documento no es válida.|
> |**Nombre**:<br />InvalidWordFileType<br />**Hex**:<br />800608EE<br />**Número**:<br />-2147088146|El tipo de archivo no se admite.|
> |**Nombre**:<br />InvalidWordTemplateContent<br />**Hex**:<br />800608FB<br />**Número**:<br />-2147088133|El contenido de la plantilla no es válido.|
> |**Nombre**:<br />InvalidWordXmlFile<br />**Hex**:<br />80048441<br />**Número**:<br />-2147187647|Solo se pueden cargar archivos en formato de Microsoft Word xml.|
> |**Nombre**:<br />InvalidWorkflowOrWorkflowDoesNotExist<br />**Hex**:<br />8006040a<br />**Número**:<br />-2147089398|Flujo de trabajo no es válido o no existe.|
> |**Nombre**:<br />InvalidXaml<br />**Hex**:<br />80060417<br />**Número**:<br />-2147089385|XAML para flujo de trabajo es NULO o está vacío|
> |**Nombre**:<br />InvalidXml<br />**Hex**:<br />80040201<br />**Número**:<br />-2147220991|XML no válido.|
> |**Nombre**:<br />InvalidXmlCollectionNameException<br />**Hex**:<br />80040247<br />**Número**:<br />-2147220921|Nombre de colección Xml no válido.|
> |**Nombre**:<br />InvalidXmlEntityNameException<br />**Hex**:<br />80040248<br />**Número**:<br />-2147220920|Nombre de entidad Xml no válido.|
> |**Nombre**:<br />InvalidXmlForParameters<br />**Hex**:<br />80060410<br />**Número**:<br />-2147089392|El nodo parámetros para ControlStep tiene XML no válido|
> |**Nombre**:<br />InvalidXmlSSContent<br />**Hex**:<br />80040350<br />**Número**:<br />-2147220656|No se puede importar el archivo de datos porque contiene datos de la entidad no válidos o está en un formato incorrecto. Asegúrese de que el archivo contiene datos correctos y de que se encuentra en el formato de hoja de cálculo XML 2003 y, después, intente cargar de nuevo.|
> |**Nombre**:<br />InvalidXrmSdkReference<br />**Hex**:<br />8004419b<br />**Número**:<br />-2147204709|El ensamblado de complemento hace referencia a una versión de Microsoft.Xrm.Sdk que es superior a la versión del servidor|
> |**Nombre**:<br />InvalidZipFileForImport<br />**Hex**:<br />80048482<br />**Número**:<br />-2147187582|El archivo comprimido (.zip) seleccionado contiene archivos que no se pueden importar. Un archivo .zip puede contener solo archivos .xlsx, .csv o XML.|
> |**Nombre**:<br />InvalidZipFileFormat<br />**Hex**:<br />80048488<br />**Número**:<br />-2147187576|El archivo que está intentando cargar no es un archivo válido. Compruebe el archivo e inténtelo de nuevo.|
> |**Nombre**:<br />InvitationBillingAdminUnknown<br />**Hex**:<br />8004D213<br />**Número**:<br />-2147167725|No es un administrador de facturación de la organización y por tanto, no puede enviar invitaciones.  Puede ponerse en contacto con su administrador de facturación y pedirle que envíe la invitación, o el Administrador de facturación puede visitar https://billing.microsoft.com y hacerle administrador de facturación delegado. A continuación, puede enviar las invitaciones.|
> |**Nombre**:<br />InvitationCannotBeReset<br />**Hex**:<br />8004D210<br />**Número**:<br />-2147167728|No se puede restablecer la invitación para el usuario.|
> |**Nombre**:<br />InvitationIsAccepted<br />**Hex**:<br />8004D208<br />**Número**:<br />-2147167736|{0} -- La invitación ya se ha aceptado -- Token={1} Puid={2} Id={3} estado={4}|
> |**Nombre**:<br />InvitationIsExpired<br />**Hex**:<br />8004D207<br />**Número**:<br />-2147167737|{0} -- La invitación ha expirado --Token={1} Puid={2} Id={3} estado={4}|
> |**Nombre**:<br />InvitationIsRejected<br />**Hex**:<br />8004D209<br />**Número**:<br />-2147167735|{0} -- El usuario nuevo ya ha rechazado la invitación-- Token={1} Puid={2} Id={3} estado={4}|
> |**Nombre**:<br />InvitationIsRevoked<br />**Hex**:<br />8004D20A<br />**Número**:<br />-2147167734|{0} -- La invitación ha sido revocada por la organización -- Token={1} Puid={2} Id={3} estado={4}|
> |**Nombre**:<br />InvitationNotFound<br />**Hex**:<br />8004D204<br />**Número**:<br />-2147167740|{0} -- No se ha encontrado la invitación o el estado no está abierto: Token={1} Puid={2} Id={3} estado={4}|
> |**Nombre**:<br />InvitationOrganizationNotEnabled<br />**Hex**:<br />8004D217<br />**Número**:<br />-2147167721|La organización para la invitación no está habilitada.|
> |**Nombre**:<br />InvitationSendToSelf<br />**Hex**:<br />8004D20F<br />**Número**:<br />-2147167729|No se puede enviar la invitación a usted mismo.|
> |**Nombre**:<br />InvitationStatusError<br />**Hex**:<br />8004D20C<br />**Número**:<br />-2147167732|"La invitación tiene estado {0}."|
> |**Nombre**:<br />InvitationWrongUserOrgRelation<br />**Hex**:<br />8004D206<br />**Número**:<br />-2147167738|{0}-- La relación de userorg creada previamente {1} es incorrecta.  La autenticación {2} ya está en uso por otro usuario|
> |**Nombre**:<br />InvitedUserAlreadyAdded<br />**Hex**:<br />8004D205<br />**Número**:<br />-2147167739|{0}-- El usuario de crm {1} ya se ha agregado, pero a la organización {2} en lugar de a la organización que invita {3}|
> |**Nombre**:<br />InvitedUserAlreadyExists<br />**Hex**:<br />8004D202<br />**Número**:<br />-2147167742|{0} -- El usuario invitado ya está en una organización -- {1}|
> |**Nombre**:<br />InvitedUserIsOrganization<br />**Hex**:<br />8004D203<br />**Número**:<br />-2147167741|{0} -- El usuario {1} tiene la autenticación {2} y ya está relacionado con la organización {3} con identificador de relación {4}|
> |**Nombre**:<br />InvitedUserMultipleTimes<br />**Hex**:<br />8004D20B<br />**Número**:<br />-2147167733|Se ha invitado al usuario de Dynamics 365 {0} varias veces.|
> |**Nombre**:<br />InvitingOrganizationNotFound<br />**Hex**:<br />8004D200<br />**Número**:<br />-2147167744|{0} -- No se encontró la organización -- {1}|
> |**Nombre**:<br />InvitingUserNotInOrganization<br />**Hex**:<br />8004D201<br />**Número**:<br />-2147167743|{0} -- El usuario invitado no está en la organización -- {1}|
> |**Nombre**:<br />IsKitCannotBeNull<br />**Hex**:<br />80044158<br />**Número**:<br />-2147204776|El atributo iskit no puede ser null.|
> |**Nombre**:<br />IsNotLiveToSendInvitation<br />**Hex**:<br />8004B009<br />**Número**:<br />-2147176439|No se admite esta funcionalidad, solo está disponible para la solución en línea.|
> |**Nombre**:<br />IsvAborted<br />**Hex**:<br />80040265<br />**Número**:<br />-2147220891|El código ISV anuló la operación.|
> |**Nombre**:<br />IsvExtensionsPrivilegeNotPresent<br />**Hex**:<br />80048029<br />**Número**:<br />-2147188695|Para importar ISV.Config, la cuenta de usuario debe estar asociada a un rol de seguridad que incluya el privilegio Extensiones ISV.|
> |**Nombre**:<br />IsvTransactionCount<br />**Hex**:<br />8009000C<br />**Número**:<br />-2146893812|El código ISV redujo el recuento de transacciones abiertas. Los complementos personalizados no deben detectar excepciones de llamadas de OrganizationService y continuar el procesamiento.|
> |**Nombre**:<br />IsvUnExpected<br />**Hex**:<br />80040224<br />**Número**:<br />-2147220956|Error inesperado del código ISV.|
> |**Nombre**:<br />JobNameIsEmptyOrNull<br />**Hex**:<br />80048457<br />**Número**:<br />-2147187625|El nombre del trabajo no puede ser nulo o estar vacío.|
> |**Nombre**:<br />KBInvalidCreateAssociation<br />**Hex**:<br />80060861<br />**Número**:<br />-2147088287|Este artículo de KB ya está vinculado a {0}.|
> |**Nombre**:<br />KnowledgeSearchActiveModelsAlreadyExist<br />**Hex**:<br />80061680<br />**Número**:<br />-2147084672|Ya existe una configuración activa para entidad de origen {0}. Solo se permite una configuración activa por entidad de origen.|
> |**Nombre**:<br />LabelIdDoesNotMatchStepId<br />**Hex**:<br />80060419<br />**Número**:<br />-2147089383|El identificador de la etiqueta {0} no coincide con el identificador del paso {1}.|
> |**Nombre**:<br />LanguageProvisioningSrsDataConnectorNotInstalled<br />**Hex**:<br />8004F710<br />**Número**:<br />-2147158256|Microsoft Dynamics 365 Reporting Extensions tiene que instalarse antes de que se pueda proporcionar el idioma para esta organización.|
> |**Nombre**:<br />LayerDesiredOrderFCBIsOff<br />**Hex**:<br />8004F057<br />**Número**:<br />-2147159977|La cláusula LayerDesiredOrder está presente en el mensaje de importación pero el FCB no está habilitado. Para evitar capas incorrectas, el proceso finaliza.|
> |**Nombre**:<br />LayerDesiredOrderHintDiffFormOnBase<br />**Hex**:<br />8004F055<br />**Número**:<br />-2147159979|La cláusula LayerDesiredOrder contiene un valor que causará el formulario [{0}] se convierta en la base, pero el Formulario en la solución entrante es un dif. Esto es un error terminal, volver a intentarlo no ayudará.|
> |**Nombre**:<br />LayerDesiredOrderHintTypeNotAvailable<br />**Hex**:<br />8004F054<br />**Número**:<br />-2147159980|La cláusula LayerDesiredOrder contiene un tipo [{0}] que no está disponible para su uso. Esto es un error terminal, volver a intentarlo no ayudará.|
> |**Nombre**:<br />LayerDesiredOrderInvalidLayerState<br />**Hex**:<br />8004F051<br />**Número**:<br />-2147159983|Hubo una coincidencia para una solución en la cláusula LayerDesiredOrder, pero no es posible honrarla debido a una corrupción en las capas del componente [{0}], identificado [{1}]. Esto es un error terminal, volver a intentarlo no ayudará. Llame al soporte al cliente. El estado de la capa es: [{2}].|
> |**Nombre**:<br />LayerDesiredOrderInvalidXML<br />**Hex**:<br />8004F049<br />**Número**:<br />-2147159991|La cláusula LayerDesiredOrder contiene un esquema XML no válido.|
> |**Nombre**:<br />LayerDesiredOrderInvalidXMLDetail<br />**Hex**:<br />8004F050<br />**Número**:<br />-2147159984|La cláusula LayerDesiredOrder contiene un esquema XML no válido. Verifique la propiedad [{0}].|
> |**Nombre**:<br />LayerDesiredOrderNotAllowedOnPatch<br />**Hex**:<br />8004F052<br />**Número**:<br />-2147159982|La cláusula LayerDesiredOrder no se puede utilizar al importar un parche. Elimine la cláusula y vuelva a intentar la operación.|
> |**Nombre**:<br />LayerDesiredOrderNotSamePublisher<br />**Hex**:<br />8004F048<br />**Número**:<br />-2147159992|La solución [{0}] se usó en una cláusula LayerDesiredOrder, pero su editor [{1}] no coincide con el editor de la solución que se está instalando: [{2}]. No se admite esta operación.|
> |**Nombre**:<br />LayerDesiredOrderPendingUpgrade<br />**Hex**:<br />8004F047<br />**Número**:<br />-2147159993|La solución [{0}] se usó en una cláusula LayerDesiredOrder, pero tiene una actualización pendiente. Complete la actualización e intente la operación nuevamente.|
> |**Nombre**:<br />LayerDesiredOrderPublisherNotAllowed<br />**Hex**:<br />8004F056<br />**Número**:<br />-2147159978|El editor [{0}] no está permitido usar la cláusula LayerDesiredOrder.|
> |**Nombre**:<br />LayerDesiredOrderRestrictedSolution<br />**Hex**:<br />8004F058<br />**Número**:<br />-2147159976|La cláusula LayerDesiredOrder no se puede usar en [{0}]. Esto es un error terminal, volver a intentarlo no ayudará.|
> |**Nombre**:<br />LeadAlreadyInClosedState<br />**Hex**:<br />80040519<br />**Número**:<br />-2147220199|El cliente potencial ya está cerrado.|
> |**Nombre**:<br />LeadAlreadyInOpenState<br />**Hex**:<br />80040518<br />**Número**:<br />-2147220200|El cliente potencial se encuentra en estado abierto.|
> |**Nombre**:<br />LegacyXlsxFileNotSupported<br />**Hex**:<br />800608CF<br />**Número**:<br />-2147088177|Los archivos .xlsx heredados no se pueden usar para plantillas de Excel.|
> |**Nombre**:<br />LicenseConfigFileInvalid<br />**Hex**:<br />8004D250<br />**Número**:<br />-2147167664|El archivo de configuración proporcionado {0} tiene un formato no válido.|
> |**Nombre**:<br />LicenseNotEnoughToActivate<br />**Hex**:<br />80042f14<br />**Número**:<br />-2147209452|No hay suficientes licencias disponibles para el número de usuarios que se activa.|
> |**Nombre**:<br />LicenseRegistrationExpired<br />**Hex**:<br />8004415d<br />**Número**:<br />-2147204771|Ha expirado el período de registro de Microsoft Dynamics 365.|
> |**Nombre**:<br />LicenseTampered<br />**Hex**:<br />8004415f<br />**Número**:<br />-2147204769|La licencia de esta instalación de Microsoft Dynamics 365 se ha manipulado. El sistema es no se puede usar. Póngase en contacto con el servicio de soporte técnico de Microsoft.|
> |**Nombre**:<br />LicenseTrialExpired<br />**Hex**:<br />8004415c<br />**Número**:<br />-2147204772|La instalación de prueba de Microsoft Dynamics 365 ha expirado.|
> |**Nombre**:<br />LicenseUpgradePathNotAllowed<br />**Hex**:<br />8004D247<br />**Número**:<br />-2147167673|No puede actualizar el tipo de licencia especificado.|
> |**Nombre**:<br />LinkedEntitiesAreNotAllowed<br />**Hex**:<br />80071120<br />**Número**:<br />-2147020512|No se permiten entidades vinculadas en el filtro|
> |**Nombre**:<br />LiveAdminUnknownCommand<br />**Hex**:<br />8004D239<br />**Número**:<br />-2147167687|Comando de administración desconocido {0}|
> |**Nombre**:<br />LiveAdminUnknownObject<br />**Hex**:<br />8004D238<br />**Número**:<br />-2147167688|Destino de administración desconocido {0}|
> |**Nombre**:<br />LivePlatformEmailInvalidBody<br />**Hex**:<br />8004B524<br />**Número**:<br />-2147175132|El parámetro "Cuerpo" está en blanco o es nulo|
> |**Nombre**:<br />LivePlatformEmailInvalidFrom<br />**Hex**:<br />8004B522<br />**Número**:<br />-2147175134|El parámetro "De" está en blanco o es nulo|
> |**Nombre**:<br />LivePlatformEmailInvalidSubject<br />**Hex**:<br />8004B523<br />**Número**:<br />-2147175133|El parámetro "Asunto" está en blanco o es nulo|
> |**Nombre**:<br />LivePlatformEmailInvalidTo<br />**Hex**:<br />8004B521<br />**Número**:<br />-2147175135|El parámetro "Para" está en blanco o es nulo|
> |**Nombre**:<br />LivePlatformGeneralEmailError<br />**Hex**:<br />8005B520<br />**Número**:<br />-2147109600|Se ha producido un error de correo electrónico.|
> |**Nombre**:<br />LocalDataSourceAbortError<br />**Hex**:<br />80072453<br />**Número**:<br />-2147015597|La operación del explorador se detuvo. Inténtelo de nuevo.|
> |**Nombre**:<br />LocalDataSourceDatabaseError<br />**Hex**:<br />80072455<br />**Número**:<br />-2147015595|La operación del explorador falló debido a errores de base de datos del explorador. Inténtelo de nuevo. Si no funciona, pruebe la misma operación de nuevo asegurándose de que el dispositivo permanece desbloqueado hasta que la operación se complete.|
> |**Nombre**:<br />LocalDataSourceError<br />**Hex**:<br />80072451<br />**Número**:<br />-2147015599|Error en la operación. Inténtelo de nuevo.|
> |**Nombre**:<br />LocalDataSourceQuotaExceededError<br />**Hex**:<br />80072452<br />**Número**:<br />-2147015598|La operación falló porque no había suficiente espacio en la cuota de almacenamiento del explorador o se alcanzó la cuota de almacenamiento del explorador y el usuario rechazó proporcionar más espacio a la base de datos del explorador.|
> |**Nombre**:<br />LocalDataSourceTimeOutError<br />**Hex**:<br />80072454<br />**Número**:<br />-2147015596|Se ha agotado el tiempo de espera de la operación. Vuelva a intentarlo más tarde.|
> |**Nombre**:<br />LockStatusNotValidForDynamicList<br />**Hex**:<br />8004F703<br />**Número**:<br />-2147158269|No se puede especificar el estado de bloqueo para una lista dinámica.|
> |**Nombre**:<br />LogoImageNodeDoesNotExist<br />**Hex**:<br />800608D2<br />**Número**:<br />-2147088174|No existe el nodo de imagen de logotipo en los datos de tema de la caché de la organización.|
> |**Nombre**:<br />LongParseRow<br />**Hex**:<br />80040372<br />**Número**:<br />-2147220622|Esta fila es demasiado larga para importarla|
> |**Nombre**:<br />LookupNotFound<br />**Hex**:<br />80040353<br />**Número**:<br />-2147220653|No se pudo resolver la referencia de búsqueda|
> |**Nombre**:<br />LowerVersionUpgrade<br />**Hex**:<br />80048541<br />**Número**:<br />-2147187391|La solución de importación debe tener una versión superior a la solución existente que está actualizando.|
> |**Nombre**:<br />LowQuantityGreaterThanHighQuantity<br />**Hex**:<br />80043b01<br />**Número**:<br />-2147206399|Una cantidad baja debe ser menor que la cantidad alta.|
> |**Nombre**:<br />LowQuantityLessThanZero<br />**Hex**:<br />80043b00<br />**Número**:<br />-2147206400|Una baja cantidad debe ser superior a cero.|
> |**Nombre**:<br />MailApp_AppModuleDashboardFormInactive<br />**Hex**:<br />80061227<br />**Número**:<br />-2147085785|La aplicación para el formulario de Outlook Dashboard está inactiva.|
> |**Nombre**:<br />MailApp_AppModuleDashboardFormMissing<br />**Hex**:<br />80061223<br />**Número**:<br />-2147085789|No se encuentra la aplicación para el formulario de Outlook Dashboard.|
> |**Nombre**:<br />MailApp_AppModuleDashboardFormRoleNotAssigned<br />**Hex**:<br />80061228<br />**Número**:<br />-2147085784|El usuario no tiene acceso a la aplicación para Outlook Dashboard.|
> |**Nombre**:<br />MailApp_AppModulePermission<br />**Hex**:<br />80070004<br />**Número**:<br />-2147024892|El rol del usuario actual no tiene los permisos necesarios para acceder a la aplicación para Outlook|
> |**Nombre**:<br />MailApp_AppModuleSitemapDashboardMissing<br />**Hex**:<br />80061224<br />**Número**:<br />-2147085788|No se encuentra la aplicación para Outlook Dashboard en el mapa del sitio.|
> |**Nombre**:<br />MailApp_AppModuleSitemapDashboardNotDefault<br />**Hex**:<br />80061225<br />**Número**:<br />-2147085787|El panel de la aplicación para Outlook no está configurado como predeterminado en el Mapa del sitio.|
> |**Nombre**:<br />MailApp_AppModuleSitemapMissing<br />**Hex**:<br />80061226<br />**Número**:<br />-2147085786|No se encuentra el mapa del sitio de la aplicación para Outlook AppModule|
> |**Nombre**:<br />MailApp_AppointmentFeatureNotEnabled<br />**Hex**:<br />80061218<br />**Número**:<br />-2147085800|No ha sido habilitado el acceso a la aplicación para citas para esta organización de Microsoft Dynamics 365. Póngase en contacto con el administrador del sistema para habilitar el acceso a citas.|
> |**Nombre**:<br />MailApp_DifferentSecurityZoneError<br />**Hex**:<br />80061210<br />**Número**:<br />-2147085808|Intente agregar las direcciones URL siguientes a los sitios de confianza:{0} {1} {2}|
> |**Nombre**:<br />MailApp_EmailAddressMismatch<br />**Hex**:<br />80061211<br />**Número**:<br />-2147085807|Parece que intenta acceder a la aplicación de CRM para Outlook desde una dirección de correo electrónico que se no reconoce. Cierre e inicie sesión con la dirección de correo electrónico que utiliza para Dynamics CRM o bien haga que su administrador del sistema actualice la configuración de su correo electrónico para que refleje esta dirección de correo electrónico.|
> |**Nombre**:<br />MailApp_FeatureControlBitDisabled<br />**Hex**:<br />80061204<br />**Número**:<br />-2147085820|No ha sido habilitado el acceso a la aplicación para esta organización de Dynamics 365. Póngase en contacto con el administrador del sistema para habilitar el acceso a esta aplicación.|
> |**Nombre**:<br />MailApp_MailboxNotConfiguredWithServerSideSync<br />**Hex**:<br />80061202<br />**Número**:<br />-2147085822|La cuenta de correo electrónico no está configurada con la sincronización del lado del servidor para el correo electrónico entrante|
> |**Nombre**:<br />MailApp_MailboxNotConfiguredWithServerSideSyncForACT<br />**Hex**:<br />80061217<br />**Número**:<br />-2147085801|La cuenta de correo electrónico no está configurada con la sincronización del lado del servidor para citas, contactos y tareas|
> |**Nombre**:<br />MailApp_MailboxServerSideSyncConfigurationFailure<br />**Hex**:<br />80061220<br />**Número**:<br />-2147085792|La sincronización del lado del servidor de Microsoft Dynamics 365 ha fallado para correos electrónicos entrantes.|
> |**Nombre**:<br />MailApp_MailboxServerSideSyncConfigurationFailureForACT<br />**Hex**:<br />80061221<br />**Número**:<br />-2147085791|La sincronización del lado del servidor de Microsoft Dynamics 365 ha fallado para las citas.|
> |**Nombre**:<br />MailApp_MobileBrowserIsNotSupported<br />**Hex**:<br />80061208<br />**Número**:<br />-2147085816|La versión móvil del explorador de Outlook no se admite actualmente. Inténtelo de nuevo desde la aplicación de escritorio de Outlook.|
> |**Nombre**:<br />MailApp_PermissionsToReadContactRequired<br />**Hex**:<br />80061219<br />**Número**:<br />-2147085799|No podemos comprobar si los destinatarios están en Dynamics 365 porque el usuario no dispone de los privilegios necesarios|
> |**Nombre**:<br />MailApp_PermissionToUseCrmForOfficeAppsRequired<br />**Hex**:<br />80061205<br />**Número**:<br />-2147085819|El usuario no tiene permiso para acceder a la aplicación.|
> |**Nombre**:<br />MailApp_ReadWriteAccessRequired<br />**Hex**:<br />80061203<br />**Número**:<br />-2147085821|El usuario solo tiene acceso administrativo a Dynamics 365|
> |**Nombre**:<br />MailApp_TrackingIsNotSupported<br />**Hex**:<br />80061207<br />**Número**:<br />-2147085817|Esta versión de Outlook no admite el seguimiento de correos electrónicos nuevos.|
> |**Nombre**:<br />MailApp_UnsupportedBrowser<br />**Hex**:<br />80061201<br />**Número**:<br />-2147085823|Su explorador no es compatible.|
> |**Nombre**:<br />MailApp_UnsupportedDevice<br />**Hex**:<br />80061200<br />**Número**:<br />-2147085824|Su dispositivo no es compatible.|
> |**Nombre**:<br />MailApp_UserMailboxInactive<br />**Hex**:<br />80061216<br />**Número**:<br />-2147085802|El buzón de correo del usuario está inactivo|
> |**Nombre**:<br />MailAppLimitedMode<br />**Hex**:<br />80061222<br />**Número**:<br />-2147085790|El error genérico cuando la sincronización del lado del servidor no está configurada correctamente y MailApp solo puede cargarse en LimitedMode|
> |**Nombre**:<br />MailboxCannotDeleteEmails<br />**Hex**:<br />8005E233<br />**Número**:<br />-2147098061|La opción Eliminar correo electrónico después del procesamiento no se puede establecer en Sí en buzones de usuario.|
> |**Nombre**:<br />MailboxCannotModifyEmailAddress<br />**Hex**:<br />8005E208<br />**Número**:<br />-2147098104|No se puede actualizar la dirección de correo electrónico de un buzón cuando está asociada a una usuario o cola.|
> |**Nombre**:<br />MailboxCredentialNotSpecified<br />**Hex**:<br />8005E209<br />**Número**:<br />-2147098103|No se ha especificado el nombre del usuario.|
> |**Nombre**:<br />MailboxTrackingFolderMappingCannotBeUpdated<br />**Hex**:<br />8006088C<br />**Número**:<br />-2147088244|No se puede actualizar la asignación de carpeta de seguimiento de buzón.|
> |**Nombre**:<br />MailboxUnsupportedEmailServerType<br />**Hex**:<br />8005E247<br />**Número**:<br />-2147098041|La sincronización del lado del servidor para citas, contactos y tareas no son compatibles con los servidores POP3 o SMTP. Seleccione un tipo de correo electrónico admitido o cambie el método de sincronización para citas, contactos y tareas a Ninguno.|
> |**Nombre**:<br />ManagedBpfDeletionInvalid<br />**Hex**:<br />80060383<br />**Número**:<br />-2147089533| El flujo de proceso de negocio forma parte de una solución administrada y no se puede eliminar individualmente. Desinstale la solución primaria para quitar el flujo de proceso de negocio.|
> |**Nombre**:<br />ManagedProcessDeletionError<br />**Hex**:<br />80072457<br />**Número**:<br />-2147015593|El flujo de proceso de negocio forma parte de una solución administrada y no se puede eliminar individualmente. Desinstale la solución primaria para quitar el proceso.|
> |**Nombre**:<br />ManifestParsingFailure<br />**Hex**:<br />80048534<br />**Número**:<br />-2147187404|No se puede analizar el archivo de manifiesto especificado para recuperar OrganizationId|
> |**Nombre**:<br />ManifestXsdValidationError<br />**Hex**:<br />80160001<br />**Número**:<br />-2146041855|El archivo de manifiesto de importación no es válido. Se produjo el siguiente error en la validación XSD: '{0}'."|
> |**Nombre**:<br />ManyToManyVirtualEntityNotSupported<br />**Hex**:<br />80044820<br />**Número**:<br />-2147203040|Las relaciones de N:N entre entidades virtuales no se admiten.|
> |**Nombre**:<br />MappingExistsForTargetAttribute<br />**Hex**:<br />8004033e<br />**Número**:<br />-2147220674|Este atributo se ha asignado más de una vez. Quite las asignaciones duplicadas y, a continuación, vuelva a importar esta asignación de datos.|
> |**Nombre**:<br />MarsConnectorDisableFailure<br />**Hex**:<br />80071108<br />**Número**:<br />-2147020536|Error producido al deshabilitar el conector Mars.|
> |**Nombre**:<br />MarsConnectorEnableFailure<br />**Hex**:<br />80071107<br />**Número**:<br />-2147020537|Error producido al habilitar el conector Mars.|
> |**Nombre**:<br />MatchingAttributeNameNotNullError<br />**Hex**:<br />80044243<br />**Número**:<br />-2147204541|El nombre del atributo coincidente debe ser una sola regla de entidad nula.|
> |**Nombre**:<br />MaxActiveSLAError<br />**Hex**:<br />8004F897<br />**Número**:<br />-2147157865|No puede activar este SLA porque ha superado el número máximo de entidades que pueden tener SLA activos para su organización.|
> |**Nombre**:<br />MaxActiveSLAKPIError<br />**Hex**:<br />8004F898<br />**Número**:<br />-2147157864|No puede activar este SLA porque ha superado el número máximo de KPI del SLA permitidos por entidad para su organización.|
> |**Nombre**:<br />MaxChildCasesLimitExceeded<br />**Hex**:<br />8003F454<br />**Número**:<br />-2147224492|Un caso principal no puede tener más casos secundarios del máximo permitido. Póngase en contacto con el administrador para conocer más detalles|
> |**Nombre**:<br />MaxConditionsMobileOfflineFilters<br />**Hex**:<br />80071114<br />**Número**:<br />-2147020524|Solo puede definir 3 filtros de la org. de Mobile offline para cada entidad.|
> |**Nombre**:<br />MaxIconSizeExceededForConnector<br />**Hex**:<br />80072602<br />**Número**:<br />-2147015166|El archivo de icono del conector es demasiado grande, el tamaño no puede exceder 1 MB.|
> |**Nombre**:<br />MaximumControlsLimitExceeded<br />**Hex**:<br />8004E301<br />**Número**:<br />-2147163391|El panel formulario XML contiene más del número máximo de elementos de control: {0}.|
> |**Nombre**:<br />MaximumCountForUpdateModeExceeded<br />**Hex**:<br />8004F602<br />**Número**:<br />-2147158526|En una operación de actualización, solo se puede importar un archivo a la vez.|
> |**Nombre**:<br />MaximumNumberHandlersExceeded<br />**Hex**:<br />80048505<br />**Número**:<br />-2147187451|Esta solución agrega controladores de eventos de formulario y, por consiguiente, se excede el número máximo de controladores de eventos para un formulario.|
> |**Nombre**:<br />MaximumNumberOfAttributesForEntityReached<br />**Hex**:<br />8004841A<br />**Número**:<br />-2147187686|Se ha alcanzado el número máximo de atributos permitido para una entidad. El atributo no se puede crear.|
> |**Nombre**:<br />MaxLimitForRollupAttribute<br />**Hex**:<br />8004480a<br />**Número**:<br />-2147203062|Se pueden crear solo tres detalles métricos por métrica.|
> |**Nombre**:<br />MaxMatchCodeLengthExceeded<br />**Hex**:<br />80048429<br />**Número**:<br />-2147187671|La condición de la regla no se puede crear ni actualizar porque se superaría el límite máximo de la longitud del código de correspondencia.|
> |**Nombre**:<br />MaxProductsAllowed<br />**Hex**:<br />80071020<br />**Número**:<br />-2147020768|No puede crear más de {0} productos.|
> |**Nombre**:<br />MaxprofileItemFilterConditionsAllowed<br />**Hex**:<br />80071116<br />**Número**:<br />-2147020522|Solo puede definir 6 condiciones de filtro de entidad de Mobile Offline para cada entidad.|
> |**Nombre**:<br />MaxUnzipFolderSizeExceeded<br />**Hex**:<br />80048499<br />**Número**:<br />-2147187559|El archivo comprimido (.zip) seleccionado no se puede descomprimir porque es demasiado grande.|
> |**Nombre**:<br />MeasureDataTypeInvalid<br />**Hex**:<br />8004E010<br />**Número**:<br />-2147164144|La descripción de datos para la visualización no es válida. El tipo de atributo de una de las medidas no agregadas no es válido. Solucione la descripción de datos.|
> |**Nombre**:<br />MemberHasAlreadyBeenContacted<br />**Hex**:<br />8004140e<br />**Número**:<br />-2147216370|No se estableció contacto con este integrante de la lista de marketing porque el integrante ya recibió esta comunicación con anterioridad.|
> |**Nombre**:<br />MergeActiveQuoteError<br />**Hex**:<br />80045302<br />**Número**:<br />-2147200254|La combinación no se puede realizar en una subentidad que tenga ofertas activas.|
> |**Nombre**:<br />MergeCyclicalParentingError<br />**Hex**:<br />80045300<br />**Número**:<br />-2147200256|La combinación podría crear una asociación cíclica.|
> |**Nombre**:<br />MergeDifferentlyParentedWarning<br />**Hex**:<br />80045316<br />**Número**:<br />-2147200234|Advertencia de combinación: la subentidad tendrá una jerarquía diferente.|
> |**Nombre**:<br />MergeEntitiesIdenticalError<br />**Hex**:<br />80045305<br />**Número**:<br />-2147200251|La combinación no se puede realizar en entidades maestras y subentidades que sean idénticas.|
> |**Nombre**:<br />MergeEntityNotActiveError<br />**Hex**:<br />80045304<br />**Número**:<br />-2147200252|La combinación no se puede realizar en una entidad que esté inactiva.|
> |**Nombre**:<br />MergeLossOfParentingWarning<br />**Hex**:<br />80045317<br />**Número**:<br />-2147200233|Advertencia de combinación: la subentidad podría perder relación jerárquica|
> |**Nombre**:<br />MergeSecurityError<br />**Hex**:<br />80045301<br />**Número**:<br />-2147200255|No se permite combinar: el autor de la llamada no tiene acceso o privilegios.|
> |**Nombre**:<br />MetadataNoMapping<br />**Hex**:<br />80040e01<br />**Número**:<br />-2147217919|La asignación entre las entidades especificadas no existe|
> |**Nombre**:<br />MetadataNotFound<br />**Hex**:<br />8004024a<br />**Número**:<br />-2147220918|Metadatos no encontrados.|
> |**Nombre**:<br />MetadataNotSerializable<br />**Hex**:<br />80040e03<br />**Número**:<br />-2147217917|La entidad de metadatos determinada no es serializable|
> |**Nombre**:<br />MetadataRecordNotDeletable<br />**Hex**:<br />80044250<br />**Número**:<br />-2147204528|El usuario final no puede eliminar el registro de metadatos que se está eliminando|
> |**Nombre**:<br />MetadataSyncRequired<br />**Hex**:<br />80072510<br />**Número**:<br />-2147015408|Se requiere sincronización de metadatos|
> |**Nombre**:<br />MetricEntityOrFieldDeleted<br />**Hex**:<br />8004F687<br />**Número**:<br />-2147158393|La entidad o cambo al que se hace referencia en el indicador de objetivos no es válido|
> |**Nombre**:<br />MetricNameAlreadyExists<br />**Hex**:<br />80044802<br />**Número**:<br />-2147203070|Ya existe una métrica del objetivo con el mismo nombre. Especifique un nombre diferente e inténtelo de nuevo.|
> |**Nombre**:<br />MinMaxValidationFailed<br />**Hex**:<br />80061004<br />**Número**:<br />-2147086332|Valor fuera del intervalo.|
> |**Nombre**:<br />MissingBOWFRules<br />**Hex**:<br />80040329<br />**Número**:<br />-2147220695|Falta operación masiva relacionada con reglas de flujo de trabajo.|
> |**Nombre**:<br />MissingBusinessId<br />**Hex**:<br />8004021a<br />**Número**:<br />-2147220966|El identificador de negocio falta o no es válido.|
> |**Nombre**:<br />MissingColumn<br />**Hex**:<br />8004B028<br />**Número**:<br />-2147176408|Al contenedor de propiedades le falta una entrada para {0}.|
> |**Nombre**:<br />MissingControlStep<br />**Hex**:<br />80060385<br />**Número**:<br />-2147089531|Falta un paso de control necesario.|
> |**Nombre**:<br />MissingCrmAuthenticationToken<br />**Hex**:<br />80044300<br />**Número**:<br />-2147204352|CrmAuthenticationToken no existe.|
> |**Nombre**:<br />MissingCrmAuthenticationTokenOrganizationName<br />**Hex**:<br />80044308<br />**Número**:<br />-2147204344|El nombre de la organización debe especificarse en CrmAuthenticationToken.|
> |**Nombre**:<br />MissingDependentConnectorsForModernFlow<br />**Hex**:<br />80060474<br />**Número**:<br />-2147089292|Faltan conectores personalizados para el flujo actual, recuento esperado: {0} con nombre: {1}, recuento real: {2}|
> |**Nombre**:<br />MissingHierarchicalRelationshipForOperator<br />**Hex**:<br />80047020<br />**Número**:<br />-2147192800|Esta consulta utiliza un operador jerárquico, pero la entidad {0} no tiene una relación jerárquica.|
> |**Nombre**:<br />MissingKeyValue<br />**Hex**:<br />80072034<br />**Número**:<br />-2147016652|Entidad {0} no contiene el valor clave para el atributo {1}.|
> |**Nombre**:<br />MissingOpportunityId<br />**Hex**:<br />80043b15<br />**Número**:<br />-2147206379|El identificador de oportunidad falta o no es válido.|
> |**Nombre**:<br />MissingOrganizationFriendlyName<br />**Hex**:<br />8004B00A<br />**Número**:<br />-2147176438|No se puede instalar Dynamics 365 sin un nombre descriptivo de la organización.|
> |**Nombre**:<br />MissingOrganizationUniqueName<br />**Hex**:<br />8004B00B<br />**Número**:<br />-2147176437|No se puede instalar Dynamics 365 sin un nombre único de la organización.|
> |**Nombre**:<br />MissingOrInvalidRedirectId<br />**Hex**:<br />80048473<br />**Número**:<br />-2147187597|El parámetro de RedirId falta para el rideccionamiento asociado.|
> |**Nombre**:<br />MissingOwner<br />**Hex**:<br />80040215<br />**Número**:<br />-2147220971|El elemento no tiene propietario.|
> |**Nombre**:<br />MissingParameter<br />**Hex**:<br />8004031f<br />**Número**:<br />-2147220705|No existe un parámetro requerido para la operación masiva|
> |**Nombre**:<br />MissingParameterToMethod<br />**Hex**:<br />8004B021<br />**Número**:<br />-2147176415|Falta el parámetro {0} método {1}|
> |**Nombre**:<br />MissingParameterToStoredProcedure<br />**Hex**:<br />8004C000<br />**Número**:<br />-2147172352|Falta parámetro de procedimiento almacenado: {0}|
> |**Nombre**:<br />MissingPriceLevelId<br />**Hex**:<br />80043b12<br />**Número**:<br />-2147206382|Falta el identificador del nivel de precios.|
> |**Nombre**:<br />MissingPrimaryKey<br />**Hex**:<br />80072033<br />**Número**:<br />-2147016653|A la Entidad {0} le falta la clave principal {1}.|
> |**Nombre**:<br />MissingProductId<br />**Hex**:<br />80043b11<br />**Número**:<br />-2147206383|Falta el identificador del producto.|
> |**Nombre**:<br />MissingQuantity<br />**Hex**:<br />80081012<br />**Número**:<br />-2146955246|Falta la cantidad.|
> |**Nombre**:<br />MissingQueryType<br />**Hex**:<br />80040235<br />**Número**:<br />-2147220939|Falta el tipo de consulta.|
> |**Nombre**:<br />MissingRecipient<br />**Hex**:<br />8004350d<br />**Número**:<br />-2147207923|El fax debe tener un destinatario para poder enviarlo.|
> |**Nombre**:<br />MissingRelationshipInSolution<br />**Hex**:<br />80048548<br />**Número**:<br />-2147187384|A los siguientes atributos {0} de entidad {1} les faltan sus relaciones asociadas.|
> |**Nombre**:<br />MissingRequiredAttributes<br />**Hex**:<br />80061037<br />**Número**:<br />-2147086281|La propiedad no se puede ser creada ni actualizada porque falta el regardingobjectid, el tipo de datos o el atributo de nombre.|
> |**Nombre**:<br />MissingRequiredComponentAttributes<br />**Hex**:<br />80072002<br />**Número**:<br />-2147016702|El atributo necesario no debe ser nulo. Atributo: {0}|
> |**Nombre**:<br />MissingTeamName<br />**Hex**:<br />80041d0b<br />**Número**:<br />-2147214069|El nombre de equipo falta inesperadamente.|
> |**Nombre**:<br />MissingTransactionCurrencyId<br />**Hex**:<br />80048546<br />**Número**:<br />-2147187386|Se necesita suministrar TransactionCurrencyId para dar formato al campo de dinero (Id: {0}, Nombre: {1}, Valor: {2}, Entidad: {3}).|
> |**Nombre**:<br />MissingUomId<br />**Hex**:<br />80043b0d<br />**Número**:<br />-2147206387|Falta el identificador de unidad.|
> |**Nombre**:<br />MissingUomScheduleId<br />**Hex**:<br />80043b0a<br />**Número**:<br />-2147206390|Falta el identificador de programación de unidad.|
> |**Nombre**:<br />MissingUserId<br />**Hex**:<br />8004021b<br />**Número**:<br />-2147220965|El identificador de usuario o de equipo falta o no es válido.|
> |**Nombre**:<br />MissingWebToLeadRedirect<br />**Hex**:<br />80048477<br />**Número**:<br />-2147187593|Falta el redirectto para el redireccionamiento web2lead.|
> |**Nombre**:<br />MobileClientLanguageNotSupported<br />**Hex**:<br />8005F201<br />**Número**:<br />-2147094015|La aplicación no encontró un idioma admitido en el servidor. Póngase en contacto con el administrador para habilitar un idioma admitido|
> |**Nombre**:<br />MobileClientNotConfiguredForCurrentUser<br />**Hex**:<br />8005F20E<br />**Número**:<br />-2147094002|Vuelva a intentarlo. Si el problema persiste, busque alguna solución en {0} o póngase en contacto con el administrador de {#Brand_CRM} de su organización. Finalmente, puede contactar {1}.|
> |**Nombre**:<br />MobileClientVersionNotSupported<br />**Hex**:<br />8005F202<br />**Número**:<br />-2147094014|No se admite la versión de cliente móviles|
> |**Nombre**:<br />MobileExcelFeatureNotEnabled<br />**Hex**:<br />800608CA<br />**Número**:<br />-2147088182|La exportación móvil a la función de Excel no está habilitada.|
> |**Nombre**:<br />MobileOfflineDaysSinceRecordLastModifiedZero<br />**Hex**:<br />80060990<br />**Número**:<br />-2147087984|No habrá registros disponibles en el modo sin conexión móvil si el valor del número de días es 0.|
> |**Nombre**:<br />MobileOfflineProfileItemNameAlreadyExists<br />**Hex**:<br />800609A8<br />**Número**:<br />-2147087960|Ya existe un elemento de perfil de Mobile Offline con este nombre para este perfil de Mobile Offline. Especifique un nombre único.|
> |**Nombre**:<br />MobileOfflineProfileItemNameCanNotBeNullOrEmpty<br />**Hex**:<br />800609AA<br />**Número**:<br />-2147087958|El nombre del elemento de perfil de Mobile Offline no puede ser nulo ni estar vacío. Escriba un nombre para el elemento de perfil.|
> |**Nombre**:<br />MobileOfflineProfileNameAlreadyExists<br />**Hex**:<br />800609A7<br />**Número**:<br />-2147087961|Ya existe un perfil de Mobile Offline con este nombre. Especifique un nombre único.|
> |**Nombre**:<br />MobileOfflineProfileNameCanNotBeNullOrEmpty<br />**Hex**:<br />800609A9<br />**Número**:<br />-2147087959|El nombre del perfil de Mobile Offline no puede ser nulo ni estar vacío. Escriba un nombre para el perfil.|
> |**Nombre**:<br />MobileOfflineRuleEnhancementFeatureNotAvailaible<br />**Hex**:<br />80071117<br />**Número**:<br />-2147020521|Esta característica no está habilitada para su organización. Póngase en contacto con el administrador del sistema para obtener ayuda.|
> |**Nombre**:<br />MobileServiceError<br />**Hex**:<br />8004B070<br />**Número**:<br />-2147176336|Error de comunicación con el servicio móvil.|
> |**Nombre**:<br />ModernFlowMustBeMarkedAsOnDemandForExecuteWorkflow<br />**Hex**:<br />80060479<br />**Número**:<br />-2147089287|No se puede ejecutar Modern Flow '{0}' porque no está marcado como bajo demanda.|
> |**Nombre**:<br />ModernFlowProcessesNotEnabled<br />**Hex**:<br />80060464<br />**Número**:<br />-2147089308|La creación de procesos de flujo modernos no está habilitada.|
> |**Nombre**:<br />ModernFlowProcessesOnlyAvailableOnline<br />**Hex**:<br />80060465<br />**Número**:<br />-2147089307|La creación de procesos de flujo modernos solo es accesible en línea.|
> |**Nombre**:<br />MoneySizeExceeded<br />**Hex**:<br />80040317<br />**Número**:<br />-2147220713|El valor proporcionado superaba el valor mínimo o máximo del campo de tipo dinero.|
> |**Nombre**:<br />MOPIAssociationNameCannotBeEmptyOrSpace<br />**Hex**:<br />80060997<br />**Número**:<br />-2147087977|El nombre de la asociación del elemento de perfil de Mobile Offline no puede ser un espacio en blanco ni una cadena vacía.|
> |**Nombre**:<br />MoveBothToPrimary<br />**Hex**:<br />8004D234<br />**Número**:<br />-2147167692|La operación de movimiento pone dos instancias en el mismo servidor: base de datos = {0} anterior principal = {1} anterior secundaria = {2} nueva secundaria = {3}|
> |**Nombre**:<br />MoveBothToSecondary<br />**Hex**:<br />8004D235<br />**Número**:<br />-2147167691|La operación de movimiento pone dos instancias en el mismo servidor: base de datos = {0} anterior principal = {1} anterior secundaria = {2} nueva secundaria = {3}|
> |**Nombre**:<br />MoveOrganizationFailedNotDisabled<br />**Hex**:<br />8004D236<br />**Número**:<br />-2147167690|La operación de movimiento ha dado error porque la organización {0} no está deshabilitada|
> |**Nombre**:<br />MultilevelParentChildRelationshipNotAllowed<br />**Hex**:<br />8003F453<br />**Número**:<br />-2147224493|No se permite asociar casos secundarios a los casos secundarios existentes.|
> |**Nombre**:<br />MultipleChartAreasFound<br />**Hex**:<br />8004E008<br />**Número**:<br />-2147164152|No se admiten varias áreas de gráficos.|
> |**Nombre**:<br />MultipleChildPicklist<br />**Hex**:<br />80040250<br />**Número**:<br />-2147220912|Excepciones internas de CRM: No se admiten listas desplegables con más de un childAttribute.|
> |**Nombre**:<br />MultipleExportKeyNotSupported<br />**Hex**:<br />800608A9<br />**Número**:<br />-2147088215|No se puede crear la clave de exportación para la entidad {0} porque la entidad ya tiene definida una clave de exportación|
> |**Nombre**:<br />MultipleFilesFound<br />**Hex**:<br />80048439<br />**Número**:<br />-2147187655|El nombre del archivo adjunto no es único.|
> |**Nombre**:<br />MultipleFormElementsFound<br />**Hex**:<br />8004E304<br />**Número**:<br />-2147163388|Un panel formulario XML puede contener solo un elemento de formulario.|
> |**Nombre**:<br />MultipleImportFilesFound<br />**Hex**:<br />80072036<br />**Número**:<br />-2147016650|Múltiples archivos para atributo {0} fueron encontrados para la entidad {1}.|
> |**Nombre**:<br />MultipleInstancesOnEntity<br />**Hex**:<br />80060373<br />**Número**:<br />-2147089549|Múltiples instancias de proceso '{0}' existen para '{1}':'{2}'. Utilice las API flujo de proceso de negocio para realizar acciones relacionadas con el proceso.|
> |**Nombre**:<br />MultipleLabelsInUserDashboard<br />**Hex**:<br />8004E30D<br />**Número**:<br />-2147163379|Un panel de usuario puede tener como máximo una etiqueta para un elemento de formulario.|
> |**Nombre**:<br />MultipleMeasureCollectionsFound<br />**Hex**:<br />8004E01C<br />**Número**:<br />-2147164132|Más de una colección de medidas no es admitida para los gráficos con subcategoría, como por ejemplo los gráficos de comparación|
> |**Nombre**:<br />MultipleMeasuresFound<br />**Hex**:<br />8004E007<br />**Número**:<br />-2147164153|Más de una medida no es admitida para los gráficos con subcategoría, como por ejemplo los gráficos de comparación|
> |**Nombre**:<br />MultipleOrganizationsNotAllowed<br />**Hex**:<br />80041d35<br />**Número**:<br />-2147214027|Solo se permite una organización y un negocio de raíz.|
> |**Nombre**:<br />MultipleParentEntitiesFoundByEntity<br />**Hex**:<br />8006089E<br />**Número**:<br />-2147088226|Existe más de un primario para {0} Una entidad solo puede tener una entidad primaria.|
> |**Nombre**:<br />MultipleParentReportsFound<br />**Hex**:<br />80040485<br />**Número**:<br />-2147220347|Se encontró más de un enlace de informes. Cada informe puede tener sólo un primario.|
> |**Nombre**:<br />MultipleParentsNotSupported<br />**Hex**:<br />80047007<br />**Número**:<br />-2147192825|Una entidad puede tener únicamente una relación jerárquica|
> |**Nombre**:<br />MultiplePartnerSecurityRoleWithSameInformation<br />**Hex**:<br />8004A10a<br />**Número**:<br />-2147180278|Más de un rol de seguridad encontrado para el usuario asociado|
> |**Nombre**:<br />MultiplePartnerUserWithSameInformation<br />**Hex**:<br />8004A10b<br />**Número**:<br />-2147180277|Se ha encontrado más de un usuario de asociado con la misma información|
> |**Nombre**:<br />MultipleQueueItemsFound<br />**Hex**:<br />80040525<br />**Número**:<br />-2147220187|Este artículo se produce en más de una cola y no se pueden enrutar de esta lista. Busque el elemento en una cola e intente distribuirlo de nuevo.|
> |**Nombre**:<br />MultipleRecordsFoundByEntityKey<br />**Hex**:<br />8006089D<br />**Número**:<br />-2147088227|Más de un registro existe para la entidad {0} con clave de entidad con atributos {1}|
> |**Nombre**:<br />MultipleRelationshipsNotSupported<br />**Hex**:<br />80048200<br />**Número**:<br />-2147188224|No se admiten varias relaciones|
> |**Nombre**:<br />MultipleRootBusinessUnit<br />**Hex**:<br />8004A10c<br />**Número**:<br />-2147180276|Más de una unidad de negocio raíz encontrada|
> |**Nombre**:<br />MultipleSitemapsFound<br />**Hex**:<br />80050120<br />**Número**:<br />-2147155680|Encontrados {0} mapas de sitios no publicados pero se esperaba solo 1|
> |**Nombre**:<br />MultipleSubcategoriesFound<br />**Hex**:<br />8004E006<br />**Número**:<br />-2147164154|El XML de datos para la visualización no puede contener más de dos cláusulas Agrupar por.|
> |**Nombre**:<br />MultiValueParameterFound<br />**Hex**:<br />8005E00A<br />**Número**:<br />-2147098614|Parámetro Fetch xml {0} no puede obtener varios valores. Cambie el parámetro de informe {0} a un único parámetro de valor e inténtelo de nuevo.|
> |**Nombre**:<br />MustContainAtLeastACharInMention<br />**Hex**:<br />8004F6A4<br />**Número**:<br />-2147158364|El nombre para mostrar debe contener al menos un carácter que no sea un espacio en blanco.|
> |**Nombre**:<br />NavigationPropertyAlreadyExists<br />**Hex**:<br />80072551<br />**Número**:<br />-2147015343|NavigationPropertyName {0} no es único en una entidad|
> |**Nombre**:<br />NavigationPropertyNameCannotBeTheSameOnBothSidesOfRel<br />**Hex**:<br />80072550<br />**Número**:<br />-2147015344|El nombre de la propiedad de navegación no puede ser el mismo en ambos lados de una relación que hace referencia a sí misma. SchemaName - {0}|
> |**Nombre**:<br />NavigationPropertyNameNodeMissing<br />**Hex**:<br />80048452<br />**Número**:<br />-2147187630|Falta el nodo NavigationPropertyName para la relación de entidad {0}.|
> |**Nombre**:<br />NavigationPropertyNameValueMissing<br />**Hex**:<br />80048836<br />**Número**:<br />-2147186634|Falta el valor NavigationPropertyName para la relación de entidad {0}.|
> |**Nombre**:<br />NavPaneNotCustomizable<br />**Hex**:<br />80044329<br />**Número**:<br />-2147204311|Las propiedades del panel de navegación de esta relación no son personalizables|
> |**Nombre**:<br />NavPaneOrderValueNotAllowed<br />**Hex**:<br />80044327<br />**Número**:<br />-2147204313|No se permite el valor de orden del panel de navegación proporcionado|
> |**Nombre**:<br />NegativeAutoNumberSeed<br />**Hex**:<br />80060886<br />**Número**:<br />-2147088250|No se puede establecer la semilla de número automático para el atributo {0} de entidad {1} con valor {2} ya que es menor de 0.|
> |**Nombre**:<br />NetworkIssue<br />**Hex**:<br />8005F104<br />**Número**:<br />-2147094268|Error en la solicitud debido a problemas de red desconocidos o problemas de GateWay o servidor.|
> |**Nombre**:<br />NewStatusHasInvalidState<br />**Hex**:<br />80044322<br />**Número**:<br />-2147204318|El valor de estado suministrado para esta opción de estado nueva no existe.|
> |**Nombre**:<br />NewStatusRequiresAssociatedState<br />**Hex**:<br />80044321<br />**Número**:<br />-2147204319|La nueva opción de estado debe tener un valor de estado asociado.|
> |**Nombre**:<br />NoActiveLocation<br />**Hex**:<br />80060900<br />**Número**:<br />-2147088128|No se encontraron ubicaciones activas.|
> |**Nombre**:<br />NoAddressFoundForRecipient<br />**Hex**:<br />80040b0a<br />**Número**:<br />-2147218678|No se pudo encontrar la dirección de correo electrónico para el destinatario de tipo '{0}' con el identificador '{1}'|
> |**Nombre**:<br />NoAppModuleComponentReferred<br />**Hex**:<br />8005011B<br />**Número**:<br />-2147155685|No se hace referencia a ningún componente|
> |**Nombre**:<br />NoAttributesForEntityCreate<br />**Hex**:<br />80047014<br />**Número**:<br />-2147192812|No hay atributos para la acción de creación de una entidad.|
> |**Nombre**:<br />NoConditionRuleCreationNotAllowedForSetValueShowError<br />**Hex**:<br />80060013<br />**Número**:<br />-2147090413|Las acciones "Mostrar mensaje de error" y "Establecer un valor" no se pueden usar en una regla de negocio que no tenga una condición.|
> |**Nombre**:<br />NoConnectionRoleAndObjectTypeCodePairPresent<br />**Hex**:<br />8004F222<br />**Número**:<br />-2147159518|No hay pares ConnectionRoleId y AssociatedObjectTypeCode presentes. Entidades que se están conectando: ({0},{1}); Registros de entidad que se están conectando: ({2},{3}); Record1ConnectionRoleName: {4}, Record2ConnectionRoleName: {5}. ConnectionRoleIds: {6};|
> |**Nombre**:<br />NoConversionRule<br />**Hex**:<br />800608F5<br />**Número**:<br />-2147088139|Se requiere una ConversionRule para que se ejecute la herramienta.|
> |**Nombre**:<br />NoDataFilterSelectedForOtherDataFilter<br />**Hex**:<br />80071138<br />**Número**:<br />-2147020488|La entidad '{0}' del perfil '{1}' contenía el filtro de descarga de datos 'Otro filtro de datos'; sin embargo, no se había seleccionado ninguna opción de filtro de datos. La entidad debe especificar una opción de filtro de datos.|
> |**Nombre**:<br />NoDataForVisualization<br />**Hex**:<br />8004E011<br />**Número**:<br />-2147164143|No hay ningún dato para crear esta visualización.|
> |**Nombre**:<br />NoDefaultValueForOptionSetArgument<br />**Hex**:<br />80060396<br />**Número**:<br />-2147089514|Los argumentos de tipo OptionSet deben tener un conjunto de valores predeterminado.|
> |**Nombre**:<br />NoDefinedRelationshipsForMOPIAssociation<br />**Hex**:<br />80060998<br />**Número**:<br />-2147087976|La entidad Asociación del elemento de perfil no tiene ninguna relación definida.|
> |**Nombre**:<br />NoDialNumber<br />**Hex**:<br />8004350f<br />**Número**:<br />-2147207921|No se ha especificado ningún número de fax en el fax ni para el destinatario.|
> |**Nombre**:<br />NoEntitiesForBulkDelete<br />**Hex**:<br />80048442<br />**Número**:<br />-2147187646|El Asistente para eliminación en masa no se puede abrir porque no hay entidades válidas para eliminación.|
> |**Nombre**:<br />NoEntitySpecified<br />**Hex**:<br />800608FA<br />**Número**:<br />-2147088134|La herramienta espera una Entidad como mínimo para procesar.|
> |**Nombre**:<br />NoFilesSelected<br />**Hex**:<br />80071021<br />**Número**:<br />-2147020767|No hay documentos seleccionados para copiar. Seleccione un documento e inténtelo de nuevo.|
> |**Nombre**:<br />NoHeaderColumnFound<br />**Hex**:<br />80040368<br />**Número**:<br />-2147220632|Falta un encabezado de columna.|
> |**Nombre**:<br />NoIncidentMergeHavingSameParent<br />**Hex**:<br />8003F450<br />**Número**:<br />-2147224496|Los casos secundarios que tienen casos primarios diferentes asociados no se pueden combinar.|
> |**Nombre**:<br />NoLabelsAssociatedWithStep<br />**Hex**:<br />80060408<br />**Número**:<br />-2147089400|{0} no tiene etiquetas asociadas.|
> |**Nombre**:<br />NoLanguageProvisioned<br />**Hex**:<br />80044199<br />**Número**:<br />-2147204711|No se ha aprovisionado ningún idioma para la organización.|
> |**Nombre**:<br />NoLicenseInConfigDB<br />**Hex**:<br />8004D241<br />**Número**:<br />-2147167679|No existe licencia en la base de datos MSCRM_CONFIG.|
> |**Nombre**:<br />NoMinimumRequiredPrivilegesForTabletApp<br />**Hex**:<br />8005F20F<br />**Número**:<br />-2147094001|No tiene permisos suficientes en el servidor para cargar la aplicación.\nPóngase en contacto con el administrador para actualizar sus permisos.|
> |**Nombre**:<br />NoMoreCustomOptionValuesExist<br />**Hex**:<br />8004431F<br />**Número**:<br />-2147204321|Se han usado todos los valores de opciones personalizadas disponibles.|
> |**Nombre**:<br />NonAutoNumberAttributeSpecified<br />**Hex**:<br />80060884<br />**Número**:<br />-2147088252|El atributo {0} de entidad {1} no es un atributo de número automático. Confirme que las entradas para Atributo y Entidad se asignen correctamente a un atributo de Número automático.|
> |**Nombre**:<br />NoncompliantXml<br />**Hex**:<br />80048425<br />**Número**:<br />-2147187675|El XML de entrada no cumple el esquema XML.|
> |**Nombre**:<br />NonCrmUIInteractiveWorkflowNotSupported<br />**Hex**:<br />80045044<br />**Número**:<br />-2147200956|No se puede crear, actualizar o publicar el flujo de trabajo interactivo porque se creó fuera de la aplicación web de Microsoft Dynamics 365.|
> |**Nombre**:<br />NonCrmUIWorkflowsNotSupported<br />**Hex**:<br />80045040<br />**Número**:<br />-2147200960|No se puede crear, actualizar o publicar el flujo de trabajo porque se creó fuera de la aplicación web de Microsoft Dynamics 365. Su organización no admite este tipo de flujo de trabajo.|
> |**Nombre**:<br />NonDraftBundleUpdate<br />**Hex**:<br />80061039<br />**Número**:<br />-2147086279|La asociación de producto no se puede actualizar cuando la agrupación se encuentra en un estado no válido.|
> |**Nombre**:<br />NonInteractiveUserCannotAccessUI<br />**Hex**:<br />80044160<br />**Número**:<br />-2147204768|Los usuarios no interactivo no pueden acceder a la interfaz de usuario de la web. Póngase en contacto con el administrador del sistema de la organización.|
> |**Nombre**:<br />NonMappableEntity<br />**Hex**:<br />80046200<br />**Número**:<br />-2147196416|Se produjo un error en NonMappableEntity|
> |**Nombre**:<br />NonPrimaryEntityDataDescriptionFound<br />**Hex**:<br />8004E001<br />**Número**:<br />-2147164159|La descripción de datos para la visualización no es válida. La descripción de datos para la visualización solo puede tener atributos de la entidad principal de la vista o las entidades vinculadas.|
> |**Nombre**:<br />NoOutputTransformationParameterMappingFound<br />**Hex**:<br />80040384<br />**Número**:<br />-2147220604|No hay ninguna asignación de parámetros de transformación de salida definida. Una asignación de transformación debe tener al menos un asignación de parámetros de transformación de salida.|
> |**Nombre**:<br />NoPreviewForCustomWebResource<br />**Hex**:<br />8004E020<br />**Número**:<br />-2147164128|Este gráfico utiliza un recurso web personalizado. No se puede obtener una vista previa de este gráfico.|
> |**Nombre**:<br />NoPrivilegeToApplyManualSLA<br />**Hex**:<br />80055002<br />**Número**:<br />-2147135486|No tiene los permisos adecuados para aplicar el contrato de nivel de servicio (SLA) a este registro de caso.|
> |**Nombre**:<br />NoPrivilegeToPublishWorkflow<br />**Hex**:<br />80045016<br />**Número**:<br />-2147201002|El usuario no tiene suficientes privilegios para publicar flujos de trabajo.|
> |**Nombre**:<br />NoPrivilegeToWorker<br />**Hex**:<br />80040521<br />**Número**:<br />-2147220191|No puede agregar elementos a una cola inactiva. Seleccione otra cola e inténtelo de nuevo.|
> |**Nombre**:<br />NoPublishedDuplicateDetectionRules<br />**Hex**:<br />80048436<br />**Número**:<br />-2147187658|No hay ninguna regla de detección de duplicados publicada en el sistema. Para ejecutar la detección de duplicados, debe crear y publicar una o varias reglas.|
> |**Nombre**:<br />NoQuickFindFound<br />**Hex**:<br />80060203<br />**Número**:<br />-2147089917|Entidad - {0} no tiene una consulta de búsqueda rápida válida.|
> |**Nombre**:<br />NoRollupAttributesDefined<br />**Hex**:<br />8004F681<br />**Número**:<br />-2147158399|Para un informe correcto al menos un atributo consolidado debe estar asociado con la métrica del objetivo|
> |**Nombre**:<br />NoSettingError<br />**Hex**:<br />8004Ed46<br />**Número**:<br />-2147160762|No se encontró configuración de configdb [{0}].|
> |**Nombre**:<br />NoSiteMapReferenceInAppModule<br />**Hex**:<br />8005011C<br />**Número**:<br />-2147155684|La aplicación Module no contiene un Mapa del sitio|
> |**Nombre**:<br />NotAWellFormedXml<br />**Hex**:<br />80048426<br />**Número**:<br />-2147187674|El XML de entrada no tiene el formato XML correcto.|
> |**Nombre**:<br />NotEnoughPrivilegesForXamlWorkflows<br />**Hex**:<br />80045041<br />**Número**:<br />-2147200959|No hay suficientes privilegios para completar la operación. Solo el administrador de implementación puede crear o actualizar los flujos de trabajo que se crean fuera de la aplicación web de Microsoft Dynamics 365.|
> |**Nombre**:<br />NoTestEmailAccessPrivilege<br />**Hex**:<br />8005E232<br />**Número**:<br />-2147098062|No hay suficientes privilegios para probar el acceso.|
> |**Nombre**:<br />NotExistArgumentInAction<br />**Hex**:<br />80060393<br />**Número**:<br />-2147089517|El argumento {0} no existe en el parámetro Acción.|
> |**Nombre**:<br />NotExistBusinessProcess<br />**Hex**:<br />80060391<br />**Número**:<br />-2147089519|El proceso de negocio no existe.|
> |**Nombre**:<br />NoTimeZoneCodeForConversionRule<br />**Hex**:<br />800608F9<br />**Número**:<br />-2147088135|Se requiere la propiedad TimeZoneCode cuando el valor de la propiedad ConversionRule es SpecificTimeZone.|
> |**Nombre**:<br />NotImplemented<br />**Hex**:<br />80040219<br />**Número**:<br />-2147220967|La funcionalidad solicitada no se ha implementado aún.|
> |**Nombre**:<br />NotMobileEnabled<br />**Hex**:<br />8005F215<br />**Número**:<br />-2147093995|No puede ver este tipo de registro en su tableta. Póngase en contacto con el administrador del sistema.|
> |**Nombre**:<br />NotMobileWriteEnabled<br />**Hex**:<br />8005F21c<br />**Número**:<br />-2147093988|No puede crear este tipo de registro en su dispositivo. Póngase en contacto con el administrador del sistema.|
> |**Nombre**:<br />NotSupported<br />**Hex**:<br />80040315<br />**Número**:<br />-2147220715|No se admite esta acción.|
> |**Nombre**:<br />NotVerifiedAdmin<br />**Hex**:<br />8005F106<br />**Número**:<br />-2147094266|Necesita una cuenta de empresa con Yammer para realizar esta configuración. Inicie sesión con una cuenta de administrador Yammer o póngase en contacto con un administrador de Yammer para obtener ayuda.|
> |**Nombre**:<br />NoUserPrivilege<br />**Hex**:<br />80154B50<br />**Número**:<br />-2146088112|No tiene permisos suficientes.|
> |**Nombre**:<br />NoValidModernFlowTriggerForExecute<br />**Hex**:<br />80060476<br />**Número**:<br />-2147089290|Modern Flow '{0}' no es válido para ExecuteWorkflow.  Seleccione un Flow que se active siempre que se crea, actualiza o elimina una entidad Common Data Service.|
> |**Nombre**:<br />NoWritePermission<br />**Hex**:<br />80071023<br />**Número**:<br />-2147020765|No tiene permisos de escritura para copiar los documentos.|
> |**Nombre**:<br />NoYammerNetworksFound<br />**Hex**:<br />8005F108<br />**Número**:<br />-2147094264|No está autorizado para ninguna red Yammer. Vuelva a autorizar la configuración de Yammer con una cuenta de administrador Yammer o póngase en contacto con un administrador de Yammer para obtener ayuda.|
> |**Nombre**:<br />NullArticleTemplateFormatXml<br />**Hex**:<br />800404f8<br />**Número**:<br />-2147220232|El formato de plantilla de artículo XML no puede ser NULO|
> |**Nombre**:<br />NullArticleTemplateStructureXml<br />**Hex**:<br />800404f9<br />**Número**:<br />-2147220231|La estructura de plantilla de artículo XML no puede ser NULO|
> |**Nombre**:<br />NullArticleXml<br />**Hex**:<br />800404f7<br />**Número**:<br />-2147220233|El xml del artículo no puede ser NULO|
> |**Nombre**:<br />NullAutoNumberParameterSpecfied<br />**Hex**:<br />80060887<br />**Número**:<br />-2147088249|El atributo de número automático o los parámetros de entidad no pueden ser una cadena nula o vacía.|
> |**Nombre**:<br />NullDashboardName<br />**Hex**:<br />8004E305<br />**Número**:<br />-2147163387|El nombre de un panel no puede ser nulo.|
> |**Nombre**:<br />NullKBArticleTemplateId<br />**Hex**:<br />800404fa<br />**Número**:<br />-2147220230|kbarticletemplateidno puede ser NULO|
> |**Nombre**:<br />NullOrEmptyAttributeInXaml<br />**Hex**:<br />80060406<br />**Número**:<br />-2147089402|El atributo {0} de {1} no puede ser nulo o estar vacío|
> |**Nombre**:<br />NumberFormatFailed<br />**Hex**:<br />80040259<br />**Número**:<br />-2147220903|No se puede generar un valor con formato numérico.|
> |**Nombre**:<br />O365RoleUnsupportedForEmailApproval<br />**Hex**:<br />8009000B<br />**Número**:<br />-2146893813|La dirección de correo electrónico solo puede ser aprobada por un Administrador Global de Office 365 o por un Administrador de Exchange. Para obtener más información, póngase en contacto con el administrador del sistema.|
> |**Nombre**:<br />OAuthTokenNotFound<br />**Hex**:<br />8005F109<br />**Número**:<br />-2147094263|No se ha encontrado el token OAuth de Yammer. Debe configurar Yammer antes de acceder a cualquier función relacionada.|
> |**Nombre**:<br />ObjectAlreadyExists<br />**Hex**:<br />8004E30A<br />**Número**:<br />-2147163382|Un objeto con el identificador {0} ya existe. Cambie el identificador e inténtelo de nuevo.|
> |**Nombre**:<br />ObjectDoesNotExist<br />**Hex**:<br />80040217<br />**Número**:<br />-2147220969|No se encontró el objeto especificado.|
> |**Nombre**:<br />ObjectNotFoundInAD<br />**Hex**:<br />80041d2a<br />**Número**:<br />-2147214038|El objeto no existe en Active Directory.|
> |**Nombre**:<br />ObjectNotRelatedToCampaign<br />**Hex**:<br />8004030e<br />**Número**:<br />-2147220722|El objeto especificado no está relacionado con la campaña principal|
> |**Nombre**:<br />OccurrenceCrossingBoundary<br />**Hex**:<br />8004E120<br />**Número**:<br />-2147163872|No se pueden superponer dos repeticiones.|
> |**Nombre**:<br />OccurrenceSkipsOverBackward<br />**Hex**:<br />8004E123<br />**Número**:<br />-2147163869|No se puede reprogramar una repetición de la cita periódica si esta omite una repetición anterior de la misma cita.|
> |**Nombre**:<br />OccurrenceSkipsOverForward<br />**Hex**:<br />8004E122<br />**Número**:<br />-2147163870|No se puede reprogramar una repetición de la cita periódica si esta omite una repetición posterior de la misma cita.|
> |**Nombre**:<br />OccurrenceTimeSpanTooBig<br />**Hex**:<br />8004E121<br />**Número**:<br />-2147163871|No se puede realizar la operación. Una instancia está fuera series de rango de expansión efectiva.|
> |**Nombre**:<br />OfferingCategoryAndTokenNull<br />**Hex**:<br />8004B00C<br />**Número**:<br />-2147176436|Tanto la categoría de oferta como el token de facturación faltan, pero al menos uno es necesario.|
> |**Nombre**:<br />OfferingIdNotSupported<br />**Hex**:<br />8004B00D<br />**Número**:<br />-2147176435|Esta versión no admite la búsqueda de Id. de oferta.|
> |**Nombre**:<br />OfficeGraphDisabledError<br />**Hex**:<br />80044239<br />**Número**:<br />-2147204551|Se deshabilitaron las recomendaciones de documentos de esta organización.|
> |**Nombre**:<br />OfficeGraphSiteNotConfigured<br />**Hex**:<br />80044257<br />**Número**:<br />-2147204521|No se ha configurado ningún sitio de SharePoint de forma predeterminada.|
> |**Nombre**:<br />OfficeGroupsExceptionRetrieveSetting<br />**Hex**:<br />800610EB<br />**Número**:<br />-2147086101|Se han producido excepciones de grupos de Office en RetrieveOfficeGroupsSetting: {0}.|
> |**Nombre**:<br />OfficeGroupsFeatureNotEnabled<br />**Hex**:<br />800610EA<br />**Número**:<br />-2147086102|La característica grupos de Office no está habilitada.|
> |**Nombre**:<br />OfficeGroupsInvalidSettingType<br />**Hex**:<br />800610EC<br />**Número**:<br />-2147086100|Tipo de valor no válido para la característica de grupos de Office: {0}.|
> |**Nombre**:<br />OfficeGroupsNoAuthServersFound<br />**Hex**:<br />800610EE<br />**Número**:<br />-2147086098|La característica de grupos de Office no pudo encontrar ningún servidor de autorización.|
> |**Nombre**:<br />OfficeGroupsNotSupportedCall<br />**Hex**:<br />800610ED<br />**Número**:<br />-2147086099|La característica de grupos de Office ha intentado una solicitud incompatible.|
> |**Nombre**:<br />OfflineFilterNestedDateTimeOR<br />**Hex**:<br />80048450<br />**Número**:<br />-2147187632|No puede usar condiciones de tiempo de fecha anidados en un cláusulas o en un grupo de datos local.|
> |**Nombre**:<br />OfflineFilterParentDownloaded<br />**Hex**:<br />80048451<br />**Número**:<br />-2147187631|No puede usar la condición Primario descargado en un grupo de datos local.|
> |**Nombre**:<br />OneDriveForBusinessDisabled<br />**Hex**:<br />80050004<br />**Número**:<br />-2147155964|Los siguientes datos adjuntos requieren OneDrive para la Empresa. Póngase en contacto con el administrador para habilitar OneDrive para la Empresa en la organización.|
> |**Nombre**:<br />OneDriveForBusinessLocationNotFound<br />**Hex**:<br />80050009<br />**Número**:<br />-2147155959|No se encuentra una ubicación activa de OneDrive para la Empresa.|
> |**Nombre**:<br />OneNoteCreationFailed<br />**Hex**:<br />80060902<br />**Número**:<br />-2147088126|Error de creación de OneNote.|
> |**Nombre**:<br />OneNoteLocationDeactivated<br />**Hex**:<br />80060907<br />**Número**:<br />-2147088121|La asignación de la ubicación de OneNote está inactiva. Póngase en contacto con su administrador para activar el registro de la ubicación de OneNote de este registro de Dynamics 365.|
> |**Nombre**:<br />OneNoteLocationNotCreated<br />**Hex**:<br />80060906<br />**Número**:<br />-2147088122|No se ha creado la ubicación de OneNote.|
> |**Nombre**:<br />OneNoteRenderFailed<br />**Hex**:<br />80060903<br />**Número**:<br />-2147088125|Error de generación de OneNote.|
> |**Nombre**:<br />OnlyDisabledOrganizationCanBeDeleted<br />**Hex**:<br />8004B02F<br />**Número**:<br />-2147176401|No se puede eliminar la organización habilitada. La organización debe estar deshabilitada antes de poder ser eliminada.|
> |**Nombre**:<br />OnlyOneSearchParameterMustBeProvided<br />**Hex**:<br />80060206<br />**Número**:<br />-2147089914|Parámetros adicionales. Solo es necesario proporcionar EntityGroupName o EntityNames, no ambos.|
> |**Nombre**:<br />OnlyOwnerCanRevoke<br />**Hex**:<br />80040223<br />**Número**:<br />-2147220957|Solo el propietario de un objeto puede revocar el acceso del propietario a ese objeto.|
> |**Nombre**:<br />OnlyOwnerCanSetManagedProperties<br />**Hex**:<br />8004F031<br />**Número**:<br />-2147160015|No se puede importar el componente {0}: {1} puesto que la propiedad administrada {2} con valor {3} es diferente al valor actual {4} y el editor de la solución que se está siendo importada no coincide con el editor de la solución que instaló este componente.|
> |**Nombre**:<br />OnlyProductCanBeConvertedToKit<br />**Hex**:<br />80061017<br />**Número**:<br />-2147086313|Solo los productos pueden convertirse en kits.|
> |**Nombre**:<br />OnlyStepInPredefinedStagesCanBeModified<br />**Hex**:<br />80044184<br />**Número**:<br />-2147204732|Fase de registro de complementos no válida. Los pasos sólo se pueden modificar en las fases Transacción exterior antes de operación principal, Transacción interior antes de operación principal, Transacción interior tras operación principal y Transacción exterior tras operación principal.|
> |**Nombre**:<br />OnlyStepInServerOnlyCanHaveSecureConfiguration<br />**Hex**:<br />80044185<br />**Número**:<br />-2147204731|Solo la implementación admitida de SdkMessageProcessingStep con ServerOnly puede tener configuración segura.|
> |**Nombre**:<br />OnlyStepOutsideTransactionCanCreateCrmService<br />**Hex**:<br />80044186<br />**Número**:<br />-2147204730|Solo SdkMessageProcessingStep en canalización principal y en fases fuera de transacciones puede crear CrmService para evitar un interbloqueo.|
> |**Nombre**:<br />OnlyWorkflowDefinitionOrTemplateCanBePublished<br />**Hex**:<br />8004500D<br />**Número**:<br />-2147201011|Solo se puede publicar definición de flujo de trabajo o borrador de plantilla de flujo de trabajo.|
> |**Nombre**:<br />OnlyWorkflowDefinitionOrTemplateCanBeUnpublished<br />**Hex**:<br />8004500E<br />**Número**:<br />-2147201010|Solo se puede cancelar la publicación de definición de flujo de trabajo o borrador de plantilla de flujo de trabajo.|
> |**Nombre**:<br />OnPremiseRestoreOrganizationManifestFailed<br />**Hex**:<br />80048532<br />**Número**:<br />-2147187406|No se puede restaurar el estado configdb de la organización del manifiesto|
> |**Nombre**:<br />OpenCrmDBConnection<br />**Hex**:<br />8004023e<br />**Número**:<br />-2147220930|La conexión de la base de datos está abierta, cuando se debería estar cerrada.|
> |**Nombre**:<br />OpenDocumentErrorCodeGeneric<br />**Hex**:<br />8005F20C<br />**Número**:<br />-2147094004|Vuelva a intentarlo. Si el problema persiste, busque alguna solución en {0} o póngase en contacto con el administrador de {#Brand_CRM} de su organización. Finalmente, puede contactar {1}.|
> |**Nombre**:<br />OpenDocumentErrorCodeUnableToFindAnActivity<br />**Hex**:<br />8005F20A<br />**Número**:<br />-2147094006|Vuelva a intentarlo. Si el problema persiste, busque alguna solución en {0} o póngase en contacto con el administrador de {#Brand_CRM} de su organización. Finalmente, puede contactar {1}.|
> |**Nombre**:<br />OpenDocumentErrorCodeUnableToFindTheDataId<br />**Hex**:<br />8005F20B<br />**Número**:<br />-2147094005|Vuelva a intentarlo. Si el problema persiste, busque alguna solución en {0} o póngase en contacto con el administrador de {#Brand_CRM} de su organización. Finalmente, puede contactar {1}.|
> |**Nombre**:<br />OpenMailboxException<br />**Hex**:<br />8005E216<br />**Número**:<br />-2147098090|Se produce una excepción al abrir el buzón del servidor de correo de Exchange.|
> |**Nombre**:<br />OperationCanBeCalledOnlyOnce<br />**Hex**:<br />80040334<br />**Número**:<br />-2147220684|La acción especificada sólo se puede realizar una vez.|
> |**Nombre**:<br />OperationCanceled<br />**Hex**:<br />80060912<br />**Número**:<br />-2147088110|El usuario canceló la actualización.|
> |**Nombre**:<br />OperationFailedTryAgain<br />**Hex**:<br />80154B53<br />**Número**:<br />-2146088109|No se puede realizar la operación en el momento. Inténtelo de nuevo.|
> |**Nombre**:<br />OperationOrganizationNotFullyDisabled<br />**Hex**:<br />8004D23a<br />**Número**:<br />-2147167686|La operación {1} ha dado error porque la organización {0} no está completamente deshabilitada aún.  Utilice FORCE para reemplazar|
> |**Nombre**:<br />OperationReservedForSolutionAwareEntities<br />**Hex**:<br />80072008<br />**Número**:<br />-2147016696|Esta operación está reservada solo para entidades conscientes de la solución.|
> |**Nombre**:<br />OperatorCodeNotPresentError<br />**Hex**:<br />80044241<br />**Número**:<br />-2147204543|OperatorCode debería estar en condición XML.|
> |**Nombre**:<br />OperatorsInViewNotSupportedOffline<br />**Hex**:<br />80071127<br />**Número**:<br />-2147020505|Uno o varios operadores de esta vista no se admiten sin conexión.|
> |**Nombre**:<br />OpportunityAlreadyInOpenState<br />**Hex**:<br />8004051a<br />**Número**:<br />-2147220198|La oportunidad se encuentra en estado abierto.|
> |**Nombre**:<br />OpportunityCannotBeClosed<br />**Hex**:<br />80040516<br />**Número**:<br />-2147220202|No se puede cerrar la oportunidad.|
> |**Nombre**:<br />OpportunityCurrencyComparisonNotPossible<br />**Hex**:<br />80100004<br />**Número**:<br />-2146435068|No se puede actualizar la oportunidad; la comparación de divisas no se pudo realizar.|
> |**Nombre**:<br />OpportunityIsAlreadyClosed<br />**Hex**:<br />80040515<br />**Número**:<br />-2147220203|La oportunidad ya está cerrada.|
> |**Nombre**:<br />OpportunityNotFound<br />**Hex**:<br />80100006<br />**Número**:<br />-2146435066|No se puede obtener la entidad oportunidad para actualizar.|
> |**Nombre**:<br />OpportunityPreImageNotFound<br />**Hex**:<br />80100007<br />**Número**:<br />-2146435065|No se puede encontrar la imagen previa de la oportunidad antes de la actualización.|
> |**Nombre**:<br />OptimisticConcurrencyNotEnabled<br />**Hex**:<br />8006088D<br />**Número**:<br />-2147088243|La simultaneidad optimista no está habilitada para el tipo de entidad {0}. Solo puede usar el valor IfVersionMatches de ConcurrencyBehavior si está habilitada la simultaneidad optimista.|
> |**Nombre**:<br />OptionReorderArrayIncorrectLength<br />**Hex**:<br />80044324<br />**Número**:<br />-2147204316|La matriz de valores opcionales que se proporcionaron para reordenar no coincide con el número de opciones para el atributo.|
> |**Nombre**:<br />OptionSetValidationFailed<br />**Hex**:<br />80061005<br />**Número**:<br />-2147086331|Valor fuera del intervalo.|
> |**Nombre**:<br />OptionValuePrefixOutOfRange<br />**Hex**:<br />80048402<br />**Número**:<br />-2147187710|CustomizationOptionValuePrefix debe ser un número comprendido entre {0} y {1}|
> |**Nombre**:<br />OrganizationDisabled<br />**Hex**:<br />8004A104<br />**Número**:<br />-2147180284|La organización de Dynamics 365 a la que intenta acceder está deshabilitada en este momento.  Póngase en contacto con el administrador del sistema|
> |**Nombre**:<br />OrganizationMigrationUnderway<br />**Hex**:<br />8004B044<br />**Número**:<br />-2147176380|La migración de la organización ya está en curso.|
> |**Nombre**:<br />OrganizationNotConfigured<br />**Hex**:<br />8004D253<br />**Número**:<br />-2147167661|La organización aún no está configurada|
> |**Nombre**:<br />OrganizationTakenBySomeoneElse<br />**Hex**:<br />8004B00F<br />**Número**:<br />-2147176433|La organización {0} ya ha sido adquirida por otro cliente.|
> |**Nombre**:<br />OrganizationTakenByYou<br />**Hex**:<br />8004B00E<br />**Número**:<br />-2147176434|La organización {0} ya ha sido adquirida por usted.|
> |**Nombre**:<br />OrganizationUIDeprecated<br />**Hex**:<br />80044159<br />**Número**:<br />-2147204775|La entidad OrganizationUI está obsoleta. Se ha reemplazando por la entidad SystemForm.|
> |**Nombre**:<br />OrgDoesNotExistInDiscoveryService<br />**Hex**:<br />8004B067<br />**Número**:<br />-2147176345|No se encuentra la organización en el servicio de detección de clientes|
> |**Nombre**:<br />OrgIdNotDetermined<br />**Hex**:<br />80044353<br />**Número**:<br />-2147204269|Error. No se pudo determinar el id. de organización actual|
> |**Nombre**:<br />OrgsInaccessible<br />**Hex**:<br />8004D24A<br />**Número**:<br />-2147167670|No se devolvieron resultados de la licencia de acceso de cliente (CAL) porque no se puede tener acceso a una o más organizaciones en la implementación.|
> |**Nombre**:<br />OutgoingNotAllowedForForwardMailbox<br />**Hex**:<br />8005E225<br />**Número**:<br />-2147098075|El buzón es un buzón de enrutamiento. Un buzón de enrutamiento no puede enviar los mensajes.|
> |**Nombre**:<br />OutgoingServerLocationAndSslSetToNo<br />**Hex**:<br />8005E23F<br />**Número**:<br />-2147098049|La dirección URL especificada para Ubicación de servidor saliente utiliza HTTPS, pero la opción Usar SSL para conexión saliente se ha establecido en No. Establezca esta opción en Sí e inténtelo de nuevo.|
> |**Nombre**:<br />OutgoingServerLocationAndSslSetToYes<br />**Hex**:<br />8005E241<br />**Número**:<br />-2147098047|La dirección URL especificada para Ubicación de servidor saliente utiliza HTTP, pero la opción Usar SSL para conexión saliente se ha establecido en Sí. Especifique una ubicación de servidor que utilice HTTPS e inténtelo de nuevo.|
> |**Nombre**:<br />OutgoingSettingsUpdateNotAllowed<br />**Hex**:<br />8005E238<br />**Número**:<br />-2147098056|No se pueden especificar diferentes configuraciones de conexión de salida porque la marca "Usar misma configuración para conexiones de salida" está establecida en True.|
> |**Nombre**:<br />OutlookClientConfigActionFailed<br />**Hex**:<br />80044509<br />**Número**:<br />-2147203831|Acción de configuración de cliente de Outlook de Dynamics 365 da error.|
> |**Nombre**:<br />OutOfScopeSlug<br />**Hex**:<br />80045050<br />**Número**:<br />-2147200944|No se pueden encontrar los datos necesarios para mostrar la siguiente página del diálogo. Para solucionar este problema, póngase en contacto con el propietario del diálogo o el administrador del sistema.|
> |**Nombre**:<br />OverlappingInstances<br />**Hex**:<br />8004E108<br />**Número**:<br />-2147163896|No se pueden superponer dos instancias de la serie.|
> |**Nombre**:<br />OverRetrievalUpperLimitWithoutPagingCookie<br />**Hex**:<br />8004430A<br />**Número**:<br />-2147204342|Por encia del límite máximo de registros que se pueden solicitar sin cookies de paginación. Cookies de paginación son necesarias al recuperar un número alto de página.|
> |**Nombre**:<br />OwnerAttributeMissing<br />**Hex**:<br />8006110C<br />**Número**:<br />-2147086068|El atributo propietario no está presente en la solicitud.|
> |**Nombre**:<br />OwnerMappingExistsWithSourceSystemUserName<br />**Hex**:<br />80040343<br />**Número**:<br />-2147220669|La asignación de datos ya contiene esta asignación de propietario.|
> |**Nombre**:<br />OwnerValueNotMapped<br />**Hex**:<br />80040361<br />**Número**:<br />-2147220639|El valor de propietario no está asignado|
> |**Nombre**:<br />PageNotFound<br />**Hex**:<br />8005F21A<br />**Número**:<br />-2147093990|Página no encontrada. Puede que el registro no exista o es posible que el vínculo sea incorrecto.|
> |**Nombre**:<br />ParentBusinessDoesNotExist<br />**Hex**:<br />80041d23<br />**Número**:<br />-2147214045|El id. de empresa primaria no es válido.|
> |**Nombre**:<br />ParentCaseNotAllowedAsAChildCase<br />**Hex**:<br />8003F455<br />**Número**:<br />-2147224491|No puede agregar un caso principal como caso secundario|
> |**Nombre**:<br />ParentChildMetricIdDiffers<br />**Hex**:<br />80044905<br />**Número**:<br />-2147202811|El metricid del objetivo secundario debe ser igual que el objetivo primario.|
> |**Nombre**:<br />ParentChildPeriodAttributesDiffer<br />**Hex**:<br />80044906<br />**Número**:<br />-2147202810|La configuración de periodo del objetivo secundario debe ser igual que el objetivo primario.|
> |**Nombre**:<br />ParentHierarchyExistProperty<br />**Hex**:<br />8004F888<br />**Número**:<br />-2147157880|Debe existir un elemento principal para cada nodo en la jerarquía excepto para el nodo raíz.|
> |**Nombre**:<br />ParentReadOnly<br />**Hex**:<br />80043b09<br />**Número**:<br />-2147206391|El primario es de solo lectura y no se puede editar.|
> |**Nombre**:<br />ParentRecordAlreadyExists<br />**Hex**:<br />80048478<br />**Número**:<br />-2147187592|No se puede agregar este registro porque ya tiene un registro primario.|
> |**Nombre**:<br />ParentReportDoesNotReferenceChild<br />**Hex**:<br />80040486<br />**Número**:<br />-2147220346|El informe primario especificado no hace referencia al actual. Solo los informes de SQL Reporting Services pueden tener informes primarios.|
> |**Nombre**:<br />ParentReportLinksToSameNameChild<br />**Hex**:<br />80040496<br />**Número**:<br />-2147220330|El informe primario ya está vinculado con otro informe con el mismo nombre.|
> |**Nombre**:<br />ParentReportNotSupported<br />**Hex**:<br />80040487<br />**Número**:<br />-2147220345|El informe primario no se admite para el tipo de informe especificado. Solo los informes de SQL Reporting Services pueden tener informes primarios.|
> |**Nombre**:<br />ParentUserDoesNotExist<br />**Hex**:<br />80041d27<br />**Número**:<br />-2147214041|El usuario primario no es válido.|
> |**Nombre**:<br />ParseMustBeCalledBeforeTransform<br />**Hex**:<br />80040371<br />**Número**:<br />-2147220623|No se puede llamar transformación antes analizar.|
> |**Nombre**:<br />ParsingMetadataNotFound<br />**Hex**:<br />80040367<br />**Número**:<br />-2147220633|No se encontraron los datos necesarios para analizar el archivo, como el delimitador de datos, el delimitador de campo o los encabezados de columna.|
> |**Nombre**:<br />PartialExpansionSettingLoadError<br />**Hex**:<br />8004E102<br />**Número**:<br />-2147163902|Error al recuperar la configuración de expansión parcial de la base de datos de configuración.|
> |**Nombre**:<br />PartialHolidayScheduleCreation<br />**Hex**:<br />8004F873<br />**Número**:<br />-2147157901|No se puede crear una programación de vacaciones parcial.|
> |**Nombre**:<br />ParticipatingEntityDoesNotAppearInTraversedPath<br />**Hex**:<br />80060441<br />**Número**:<br />-2147089343|El registro de la entidad '{0}' no está en la ruta recorrida '{1}'. Póngase en contacto con el administrador del sistema.|
> |**Nombre**:<br />ParticipatingQueryEntityMismatch<br />**Hex**:<br />80044909<br />**Número**:<br />-2147202807|El entitytype de consulta de participación debe ser el mismo que la entidad especificada en fetchxml.|
> |**Nombre**:<br />PasswordRequiredForImpersonation<br />**Hex**:<br />8005E24E<br />**Número**:<br />-2147098034|Escriba una contraseña y vuelva a guardar|
> |**Nombre**:<br />PatchMissingBase<br />**Hex**:<br />80048540<br />**Número**:<br />-2147187392|No se puede importar la revisión ({0}) para la solución ({1}) debido a que la solución no está presente. La operación se ha cancelado.|
> |**Nombre**:<br />PercentageDiscountCannotHaveCurrency<br />**Hex**:<br />80048cf1<br />**Número**:<br />-2147185423|No se puede establecer divisa cuando el tipo de descuento es porcentaje.|
> |**Nombre**:<br />PersonalReportFound<br />**Hex**:<br />8004E309<br />**Número**:<br />-2147163383|Un panel de sistema no puede contener informes personales.|
> |**Nombre**:<br />PickListMappingExistsForTargetValue<br />**Hex**:<br />8004033f<br />**Número**:<br />-2147220673|Este valor de lista se ha asignado más de una vez. Quite las asignaciones duplicadas y, a continuación, vuelva a importar esta asignación de datos.|
> |**Nombre**:<br />PickListMappingExistsWithSourceValue<br />**Hex**:<br />80040342<br />**Número**:<br />-2147220670|La asignación de datos ya contiene esta asignación de valor de lista.|
> |**Nombre**:<br />PicklistValueNotFound<br />**Hex**:<br />80040393<br />**Número**:<br />-2147220589|El archivo especifica una lista de valores que no existe en Microsoft Dynamics 365.|
> |**Nombre**:<br />PicklistValueNotMapped<br />**Hex**:<br />80040360<br />**Número**:<br />-2147220640|El registro no se pudo procesar ya que no se pudo asignar el valor establecido Opción.|
> |**Nombre**:<br />PicklistValueNotUnique<br />**Hex**:<br />80044310<br />**Número**:<br />-2147204336|El valor de lista desplegable ya existe.  Los valores de la lista desplegable deben ser únicos.|
> |**Nombre**:<br />PicklistValueOutOfRange<br />**Hex**:<br />8004431A<br />**Número**:<br />-2147204326|El valor de la lista desplegable está fuera del intervalo.|
> |**Nombre**:<br />PingFailureErrorCode<br />**Hex**:<br />8005F212<br />**Número**:<br />-2147093998|El sistema no puede volver a conectar con el servidor de {#Brand_CRM}.|
> |**Nombre**:<br />PluginAssemblyContentSizeExceeded<br />**Hex**:<br />8004418f<br />**Número**:<br />-2147204721|"El tamaño del conjunto de contenido '{0} bytes' ha superado el valor máximo permitido para complementos aislados '{1} bytes'."|
> |**Nombre**:<br />PluginAssemblyMustHavePublicKeyToken<br />**Hex**:<br />8004416c<br />**Número**:<br />-2147204756|El ensamblado público debe tener el token de clave pública.|
> |**Nombre**:<br />PluginDoesNotImplementCorrectInterface<br />**Hex**:<br />8004A200<br />**Número**:<br />-2147180032|El complemento especificado no implementa la interfaz necesaria Microsoft.Xrm.Sdk.IPlugin o Microsoft.Crm.Sdk.IPlugin.|
> |**Nombre**:<br />PluginSecureStoreAdalAcquireToken<br />**Hex**:<br />80091005<br />**Número**:<br />-2146889723|No se puede adquirir el token para el recurso|
> |**Nombre**:<br />PluginSecureStoreKeyVaultClient<br />**Hex**:<br />80091000<br />**Número**:<br />-2146889728|No se puede iniciar KeyVaultClientProvider en el Sandbox WorkerProcess|
> |**Nombre**:<br />PluginSecureStoreKeyVaultClientDecrypt<br />**Hex**:<br />80091003<br />**Número**:<br />-2146889725|No se puede descifrar mediante KeyVault|
> |**Nombre**:<br />PluginSecureStoreKeyVaultClientDeleteSecret<br />**Hex**:<br />80091010<br />**Número**:<br />-2146889712|No se puede obtener DeleteSecret para Key Vault|
> |**Nombre**:<br />PluginSecureStoreKeyVaultClientEncrypt<br />**Hex**:<br />80091004<br />**Número**:<br />-2146889724|No se puede cifrar mediante KeyVault|
> |**Nombre**:<br />PluginSecureStoreKeyVaultClientGetSecret<br />**Hex**:<br />80091001<br />**Número**:<br />-2146889727|No se puede obtener secreto de KeyVault|
> |**Nombre**:<br />PluginSecureStoreKeyVaultClientSetSecret<br />**Hex**:<br />80091002<br />**Número**:<br />-2146889726|No se puede obtener secreto para KeyVault|
> |**Nombre**:<br />PluginSecureStoreKeyVaultServiceCertFormat<br />**Hex**:<br />8009100D<br />**Número**:<br />-2146889715|Certificado no almacenado como Base64String en KeyVault|
> |**Nombre**:<br />PluginSecureStoreKeyVaultServiceProviderGetData<br />**Hex**:<br />8009100C<br />**Número**:<br />-2146889716|Faltan AppId o secretos en KeyVault|
> |**Nombre**:<br />PluginSecureStoreLocalConfigStoreGetData<br />**Hex**:<br />8009100A<br />**Número**:<br />-2146889718|No se pueden obtener los datos de LocalConfigStore|
> |**Nombre**:<br />PluginSecureStoreLocalConfigStoreSetData<br />**Hex**:<br />8009100B<br />**Número**:<br />-2146889717|No se pueden definir datos en LocalConfigStore|
> |**Nombre**:<br />PluginSecureStoreNoFullySigned<br />**Hex**:<br />8009100F<br />**Número**:<br />-2146889713|El ensamblado no se ha iniciado completamente|
> |**Nombre**:<br />PluginSecureStoreS2SMissing<br />**Hex**:<br />80091008<br />**Número**:<br />-2146889720|Faltan credenciales S2S|
> |**Nombre**:<br />PluginSecureStoreTPSAssemblyNotRegistered<br />**Hex**:<br />80091007<br />**Número**:<br />-2146889721|El ensamblado no está registrado en TPS|
> |**Nombre**:<br />PluginSecureStoreTPSClient<br />**Hex**:<br />80091009<br />**Número**:<br />-2146889719|No se puede crear el cliente TPS|
> |**Nombre**:<br />PluginSecureStoreTPSKeyVaultUnconfigured<br />**Hex**:<br />80091006<br />**Número**:<br />-2146889722|No se ha configurado KeyVaultURI para un conjunto de TPS|
> |**Nombre**:<br />PluginTypeMustBeUnique<br />**Hex**:<br />8004417C<br />**Número**:<br />-2147204740|No se admiten varios tipos de complementos en el mismo conjunto y con el mismo typename.|
> |**Nombre**:<br />Pop3UnexpectedException<br />**Hex**:<br />8005E215<br />**Número**:<br />-2147098091|Excepciones se producen mientras el sondeo mensajes utiliza protocolos Pop3.|
> |**Nombre**:<br />PowerBICannotBeSystemDashboard<br />**Hex**:<br />800608FC<br />**Número**:<br />-2147088132|Un panel de Power BI no puede ser un panel del sistema.|
> |**Nombre**:<br />PowerBIDashboardControlLimitation<br />**Hex**:<br />800608FD<br />**Número**:<br />-2147088131|Un panel de Power BI solo puede contener un control y ese control debe ser un control de Power BI.|
> |**Nombre**:<br />PresentParentAccountAndParentContact<br />**Hex**:<br />80040508<br />**Número**:<br />-2147220216|Puede especificar un contacto primario del contacto o su cuenta, pero no ambos.|
> |**Nombre**:<br />PreviousOperationNotComplete<br />**Hex**:<br />80048464<br />**Número**:<br />-2147187612|No se ha completado correctamente una operación de la que depende esta operación.|
> |**Nombre**:<br />PriceLevelNameExists<br />**Hex**:<br />80043b0f<br />**Número**:<br />-2147206385|El nombre ya existe.|
> |**Nombre**:<br />PriceLevelNoName<br />**Hex**:<br />80043b0e<br />**Número**:<br />-2147206386|El nombre no puede ser nulo.|
> |**Nombre**:<br />PriceListIsMandatory<br />**Hex**:<br />80100010<br />**Número**:<br />-2146435056|PriceList es obligatorio para crear la entidad.|
> |**Nombre**:<br />PrimaryEntityInvalid<br />**Hex**:<br />8004501E<br />**Número**:<br />-2147200994|Entidad principal no válida.|
> |**Nombre**:<br />PrimaryEntityIsNull<br />**Hex**:<br />80060401<br />**Número**:<br />-2147089407|La entidad principal no puede ser NULO al crear la categoría de flujo de proceso de negocio|
> |**Nombre**:<br />PrimaryNameAttributeNotFound<br />**Hex**:<br />80044355<br />**Número**:<br />-2147204267|No se encontró el atributo PrimaryName para la Entidad: {0}|
> |**Nombre**:<br />PrimaryParticipatingEntityIsNotPresent<br />**Hex**:<br />80060453<br />**Número**:<br />-2147089325|Error de validación: la entidad participante principal no está presente y se necesita para cada registro de entidad del proceso de negocio.|
> |**Nombre**:<br />PrincipalPrivilegeDenied<br />**Hex**:<br />80040231<br />**Número**:<br />-2147220943|El usuario de destino o el equipo no tiene los privilegios necesarios.|
> |**Nombre**:<br />PrivilegeCreateIsDisabledForOrganization<br />**Hex**:<br />80040276<br />**Número**:<br />-2147220874|Crear privilegios está deshabilitada para la organización.|
> |**Nombre**:<br />PrivilegeDenied<br />**Hex**:<br />80040220<br />**Número**:<br />-2147220960|El usuario no tiene los privilegios necesarios.|
> |**Nombre**:<br />ProcessActionDoesNotExist<br />**Hex**:<br />80045054<br />**Número**:<br />-2147200940|La accesión de proceso no existe.|
> |**Nombre**:<br />ProcessActionIsNotActive<br />**Hex**:<br />80045053<br />**Número**:<br />-2147200941|La acción de proceso debe estar activa para utilizarse en paso de acción.|
> |**Nombre**:<br />ProcessActionNameIncorrect<br />**Hex**:<br />80060379<br />**Número**:<br />-2147089543|La acción de proceso “{0}” no coincide con el nombre configurado: “{1}”. Póngase en contacto con el administrador del sistema para comprobar los metadatos de configuración si persiste el error.|
> |**Nombre**:<br />ProcessActionWithInvalidInputOutputParam<br />**Hex**:<br />80045058<br />**Número**:<br />-2147200936|La acción de proceso contiene un parámetro que no es compatible. Nombre: {0}, tipo: {1}, dirección: {2}.|
> |**Nombre**:<br />ProcessActionWithInvalidInputParam<br />**Hex**:<br />80045057<br />**Número**:<br />-2147200937|La acción de proceso contiene un campo en parámetro de entrada que no es compatible en Pasos de acción. Referencia a {0} |
> |**Nombre**:<br />ProcessActionWithInvalidOutputParam<br />**Hex**:<br />80045056<br />**Número**:<br />-2147200938|La acción de proceso contiene un campo en parámetro de salida que no es compatible en Pasos de acción. Referencia a {0}.|
> |**Nombre**:<br />ProcessActionWorkflowNotEnabledForOnDemand<br />**Hex**:<br />80060380<br />**Número**:<br />-2147089536|La acción de proceso o el flujo de trabajo debe estar habilitado para que la ejecución a petición esté disponible para pasos de acción.|
> |**Nombre**:<br />ProcessControlDoesNotExistOnForm<br />**Hex**:<br />80060372<br />**Número**:<br />-2147089550|El control de proceso no existe en el formulario|
> |**Nombre**:<br />ProcessEmptyBranches<br />**Hex**:<br />80060399<br />**Número**:<br />-2147089511|Este proceso contiene ramas vacías. Defina o elimine estas ramas e inténtelo de nuevo.|
> |**Nombre**:<br />ProcessFileFailure<br />**Hex**:<br />80072554<br />**Número**:<br />-2147015340|Se ha producido un error al procesar el archivo. Razón: {0}|
> |**Nombre**:<br />ProcessIdDoesNotMatchBusinessProcessDefinition<br />**Hex**:<br />80060460<br />**Número**:<br />-2147089312|Error de validación: El identificador del proceso no coincide con la definición de proceso de negocio.|
> |**Nombre**:<br />ProcessIdIsEmpty<br />**Hex**:<br />80060459<br />**Número**:<br />-2147089319|Error de validación: El identificador del proceso no puede estar vacío.|
> |**Nombre**:<br />ProcessImageFailure<br />**Hex**:<br />80072553<br />**Número**:<br />-2147015341|Se ha producido un error al procesar imagen. Razón: {0}|
> |**Nombre**:<br />ProcessInstanceNotFound<br />**Hex**:<br />80060370<br />**Número**:<br />-2147089552|Instancia de proceso suministrada {0} no coincide con ninguna instancia existente en esta entidad {1}|
> |**Nombre**:<br />ProcessNameContainsInvalidCharacters<br />**Hex**:<br />80060398<br />**Número**:<br />-2147089512|El nombre de proceso de negocio contiene caracteres no válidos.|
> |**Nombre**:<br />ProcessNameIsNullOrEmpty<br />**Hex**:<br />80060418<br />**Número**:<br />-2147089384|El flujo de proceso de negocio es NULO o está vacío. |
> |**Nombre**:<br />ProcessStageIdIsEmpty<br />**Hex**:<br />80060461<br />**Número**:<br />-2147089311|Error de validación: El identificador principal de la fase no puede estar vacío.|
> |**Nombre**:<br />ProductCanOnlyBeUpdatedInDraft<br />**Hex**:<br />8004F995<br />**Número**:<br />-2147157611|Los productos, las familias de productos y las agrupaciones solo se pueden actualizar en el estado de borrador.|
> |**Nombre**:<br />ProductCloneFailed<br />**Hex**:<br />80061006<br />**Número**:<br />-2147086330|No puede clonar un registro secundario de una familia de productos retirada.|
> |**Nombre**:<br />ProductDoesNotExist<br />**Hex**:<br />80043b24<br />**Número**:<br />-2147206364|El producto no existe.|
> |**Nombre**:<br />ProductFamilyCanCreateDynamicProperty<br />**Hex**:<br />80081007<br />**Número**:<br />-2146955257|Solo se puede crear una propiedad para una familia de productos.|
> |**Nombre**:<br />ProductFamilyRootParentisLocked<br />**Hex**:<br />8008101F<br />**Número**:<br />-2146955233|El registro primario de la raíz de familia de productos está bloqueado por otros procesos.|
> |**Nombre**:<br />ProductFromActiveToActiveState<br />**Hex**:<br />8004F982<br />**Número**:<br />-2147157630|El producto ya está en estado Activo.|
> |**Nombre**:<br />ProductFromActiveToDraftState<br />**Hex**:<br />8004F912<br />**Número**:<br />-2147157742|No puede establecer en estado Borrador un producto publicado..|
> |**Nombre**:<br />ProductFromDraftToDraftState<br />**Hex**:<br />8004F981<br />**Número**:<br />-2147157631|El producto ya está en estado Borrador.|
> |**Nombre**:<br />ProductFromDraftToRetiredState<br />**Hex**:<br />8004F978<br />**Número**:<br />-2147157640|No se puede retirar un producto que tiene el estado Borrador.|
> |**Nombre**:<br />ProductFromDraftToRevisedState<br />**Hex**:<br />8004F913<br />**Número**:<br />-2147157741|No puede revisar un borrador o un producto retirado.|
> |**Nombre**:<br />ProductFromRetiredToActiveState<br />**Hex**:<br />8004F977<br />**Número**:<br />-2147157641|No puede establecer un producto retirado en un estado Activo.|
> |**Nombre**:<br />ProductFromRetiredToDraftState<br />**Hex**:<br />8004F979<br />**Número**:<br />-2147157639|No es posible mover productos del estado Retirado a Borrador.|
> |**Nombre**:<br />ProductFromRetiredToRetiredState<br />**Hex**:<br />8004F980<br />**Número**:<br />-2147157632|El producto ya está en estado Retirado.|
> |**Nombre**:<br />ProductHasUnretiredChild<br />**Hex**:<br />8004F910<br />**Número**:<br />-2147157744|No puede retirar esta familia de productos porque uno o más de sus registros secundarios no están retirados.|
> |**Nombre**:<br />ProductInvalidPriceLevelPercentage<br />**Hex**:<br />80043b0c<br />**Número**:<br />-2147206388|El porcentaje de cálculo de precios debe ser mayor o igual que cero y menor que 100000.|
> |**Nombre**:<br />ProductInvalidQuantityDecimal<br />**Hex**:<br />80043b07<br />**Número**:<br />-2147206393|El número de espacios decimales en la cantidad no es válido.|
> |**Nombre**:<br />ProductInvalidUnit<br />**Hex**:<br />80043b14<br />**Número**:<br />-2147206380|La unidad especificada no es válida para este producto.|
> |**Nombre**:<br />ProductKitLoopBeingCreated<br />**Hex**:<br />80043b23<br />**Número**:<br />-2147206365|No se puede agregar un kit a sí mismo.|
> |**Nombre**:<br />ProductKitLoopExists<br />**Hex**:<br />80043b22<br />**Número**:<br />-2147206366|Existe un bucle en la jerarquía del kit.|
> |**Nombre**:<br />ProductMaxPropertyLimitExceeded<br />**Hex**:<br />8008100D<br />**Número**:<br />-2146955251|Este producto no se puede publicar porque tiene demasiadas propiedades. Un producto en su organización no puede tener más de {0} propiedades.|
> |**Nombre**:<br />ProductMissingUomSheduleId<br />**Hex**:<br />80043b13<br />**Número**:<br />-2147206381|Falta el identificador de programación de unidad del producto.|
> |**Nombre**:<br />ProductNoProductNumber<br />**Hex**:<br />80043b05<br />**Número**:<br />-2147206395|El número de producto no puede ser nulo.|
> |**Nombre**:<br />ProductNoSubstitutedProductNumber<br />**Hex**:<br />8004F990<br />**Número**:<br />-2147157616|El número de producto sustituido no puede ser NULO.|
> |**Nombre**:<br />ProductOrBundleCannotBeAsParent<br />**Hex**:<br />8004F973<br />**Número**:<br />-2147157645|Solo Familias de productos pueden ser elementos primarios de productos.|
> |**Nombre**:<br />ProductProductNumberExists<br />**Hex**:<br />80043b06<br />**Número**:<br />-2147206394|El id. del producto especificado está en conflicto con el id. del producto de un registro existente. Especifique un Id. de producto e inténtelo de nuevo.|
> |**Nombre**:<br />ProductRecommendationsFeatureNotEnabled<br />**Hex**:<br />80061600<br />**Número**:<br />-2147084800|La característica Recomendaciones de producto no está habilitada.|
> |**Nombre**:<br />ProfileContainsCircularReference<br />**Hex**:<br />80071141<br />**Número**:<br />-2147020479|El perfil '{0}' tiene una referencia circular que evitará la descarga de datos. Compruebe la cadena de referencia circular: {1} y elimine la asociación del elemento de perfil que produce la referencia circular.|
> |**Nombre**:<br />ProfileContainsRelationshipWithoutEntity<br />**Hex**:<br />80071142<br />**Número**:<br />-2147020478|El perfil '{0}' tiene un elemento de perfil {1} que contiene una asociación de elemento de perfil para {2}; sin embargo no existe un elemento de perfil para {2}. Incluya el elemento del perfil y publíquelo.|
> |**Nombre**:<br />ProfileCountUserLimitExceeded<br />**Hex**:<br />80071134<br />**Número**:<br />-2147020492|El número total de usuarios ('{0}') en este perfil supera el límite permitido ('{1}'). Limite el número total de usuarios que deben estar en el límite admitido.|
> |**Nombre**:<br />ProfileRuleActivateDeactivateByNonOwner<br />**Hex**:<br />80061102<br />**Número**:<br />-2147086078|Esta regla de perfil la puede activar o desactivar sólo su propietario.|
> |**Nombre**:<br />ProfileRuleMissingRuleCriteria<br />**Hex**:<br />80061100<br />**Número**:<br />-2147086080|No puede activar esta regla hasta que no resuelva la información que falta de criterios de regla en los elementos de regla.|
> |**Nombre**:<br />ProfileRulePublishedByOwner<br />**Hex**:<br />80061103<br />**Número**:<br />-2147086077|No se puede activar la regla hasta que la regla activa actual esté desactivada. Solo se puede desactivar la regla activa por el propietario de la regla.|
> |**Nombre**:<br />ProfileRuleWorkflowAuthorGenericError<br />**Hex**:<br />80061101<br />**Número**:<br />-2147086079|Se ha producido un error durante el flujo de trabajo de creación. Solucione la definición de flujo de trabajo e inténtelo de nuevo.|
> |**Nombre**:<br />ProvisioningNotCompleted<br />**Hex**:<br />80091044<br />**Número**:<br />-2146889660|Para habilitar la captura automática, debe configurar Cortana Intelligence Customer Insights en la configuración de información de relaciones.|
> |**Nombre**:<br />ProvisionRIAccessNotAllowed<br />**Hex**:<br />80044270<br />**Número**:<br />-2147204496|Necesita privilegios de administrador del sistema para ejecutar Información de relaciones en su organización.|
> |**Nombre**:<br />PublishArticle_TranslationWithMoreThanOneApprovedVersion<br />**Hex**:<br />80061401<br />**Número**:<br />-2147085311|Hay más de una versión autorizada del idioma {0}. Solo puede publicar una versión de cada idioma.|
> |**Nombre**:<br />PublishedWorkflowLimitForSkuReached<br />**Hex**:<br />80045015<br />**Número**:<br />-2147201003|No se puede publicar este flujo de trabajo porque su organización ha llegado a su límite de número de flujos de trabajo que se pueden publicar al mismo tiempo. (No hay ningún límite en el número de flujos de trabajo de borrador). Puede publicar el flujo de trabajo anulando la publicación de un flujo de trabajo diferente, o bien actualizando su licencia a una licencia que admita más flujos de trabajo.|
> |**Nombre**:<br />PublishedWorkflowOwnershipChange<br />**Hex**:<br />8004500C<br />**Número**:<br />-2147201012|Solo se le puede asignar un flujo de trabajo publicado al llamador.|
> |**Nombre**:<br />PublishWorkflowWhileActingOnBehalfOfAnotherUserError<br />**Hex**:<br />80045032<br />**Número**:<br />-2147200974|No se permite la publicación de flujos de trabajo si se actúa en nombre de otro usuario.|
> |**Nombre**:<br />PublishWorkflowWhileImpersonatingError<br />**Hex**:<br />80045039<br />**Número**:<br />-2147200967|No se permite la publicación de flujos de trabajo si no se admite la suplantación de otro usuario.|
> |**Nombre**:<br />QuantityReadonly<br />**Hex**:<br />80043b18<br />**Número**:<br />-2147206376|No modifique el campo Cantidad al actualizar la unidad principal.|
> |**Nombre**:<br />QueriesForDifferentEntities<br />**Hex**:<br />8004D2B0<br />**Número**:<br />-2147167568|Las consultas externas e internas deben ser de la misma entidad.|
> |**Nombre**:<br />QueryBuilderAlias_Does_Not_Exist<br />**Hex**:<br />8004110a<br />**Número**:<br />-2147217142|El alias especificado para la entidad determinada en la condición no existe.|
> |**Nombre**:<br />QueryBuilderAliasNotAllowedForNonAggregateOrderBy<br />**Hex**:<br />80041132<br />**Número**:<br />-2147217102|No se puede especificar un alias para una cláusula de orden para una consulta no agregada. Utilice un atributo.|
> |**Nombre**:<br />QueryBuilderAliasRequiredForAggregateOrderBy<br />**Hex**:<br />80041134<br />**Número**:<br />-2147217100|Se requiere un alias para una cláusula de orden para una consulta agregada.|
> |**Nombre**:<br />QueryBuilderAttribute_With_Aggregate<br />**Hex**:<br />80041107<br />**Número**:<br />-2147217145|Cuando se especifica la operación de agregado no se pueden devolver los atributos.|
> |**Nombre**:<br />QueryBuilderAttributeCannotBeGroupByAndAggregate<br />**Hex**:<br />80041137<br />**Número**:<br />-2147217097|Un atributo puede ser un agregado o un grupo, pero no ambos|
> |**Nombre**:<br />QueryBuilderAttributeNotAllowedForAggregateOrderBy<br />**Hex**:<br />80041131<br />**Número**:<br />-2147217103|No se puede especificar un atributo para una cláusula de orden para una consulta agregada. Utilice un alias.|
> |**Nombre**:<br />QueryBuilderAttributeNotFound<br />**Hex**:<br />8004111e<br />**Número**:<br />-2147217122|No se especificó un atributo requerido.|
> |**Nombre**:<br />QueryBuilderAttributePairMismatch<br />**Hex**:<br />80041111<br />**Número**:<br />-2147217135|AttributeFrom y AttributeTo deben estar ambos especificados o ambos omitidos.|
> |**Nombre**:<br />QueryBuilderAttributeRequiredForNonAggregateOrderBy<br />**Hex**:<br />80041133<br />**Número**:<br />-2147217101|Se requiere un atributo para una cláusula de orden para una consulta no agregada.|
> |**Nombre**:<br />QueryBuilderBad_Condition<br />**Hex**:<br />80041106<br />**Número**:<br />-2147217146|Condición o condiciones de filtro incorrectas.|
> |**Nombre**:<br />QueryBuilderByAttributeMismatch<br />**Hex**:<br />8004110f<br />**Número**:<br />-2147217137|QueryByAttribute debe especificar una matriz de valores no vacía con el mismo número de elementos que en la matriz de atributos.|
> |**Nombre**:<br />QueryBuilderByAttributeNonEmpty<br />**Hex**:<br />80041110<br />**Número**:<br />-2147217136|QueryByAttribute debe especificar una matriz de atributos no vacía.|
> |**Nombre**:<br />QueryBuilderColumnSetVersionMissing<br />**Hex**:<br />80041113<br />**Número**:<br />-2147217133|La versión de columnset especificada no es válida.|
> |**Nombre**:<br />QueryBuilderDeserializeEmptyXml<br />**Hex**:<br />80041124<br />**Número**:<br />-2147217116|La cadena XML no puede ser nula.|
> |**Nombre**:<br />QueryBuilderDeserializeInvalidAggregate<br />**Hex**:<br />8004111a<br />**Número**:<br />-2147217126|Se ha producido un error al procesar los agregados en consulta|
> |**Nombre**:<br />QueryBuilderDeserializeInvalidDescending<br />**Hex**:<br />80041119<br />**Número**:<br />-2147217127|Los únicos valores válidos para el atributo descendente son 'true', 'false', '1' y '0'.|
> |**Nombre**:<br />QueryBuilderDeserializeInvalidDistinct<br />**Hex**:<br />80041115<br />**Número**:<br />-2147217131|Los únicos valores válidos para el atributo Distinct son 'true', 'false', '1' y '0'.|
> |**Nombre**:<br />QueryBuilderDeserializeInvalidGetMinActiveRowVersion<br />**Hex**:<br />8004111b<br />**Número**:<br />-2147217125|Los únicos valores válidos para el atributo GetMinActiveRowVersion son 'true', 'false', '1' y '0'.|
> |**Nombre**:<br />QueryBuilderDeserializeInvalidGroupBy<br />**Hex**:<br />8004112E<br />**Número**:<br />-2147217106|Los únicos valores válidos para el atributo groupby son 'true', 'false', '1' y '0'.|
> |**Nombre**:<br />QueryBuilderDeserializeInvalidLinkType<br />**Hex**:<br />80041117<br />**Número**:<br />-2147217129|Los únicos valores solo válidos para atributo de tipo de vínculo son 'natural', 'inner','in','exists','matchfirstrowusingcrossapply' y 'outer'.|
> |**Nombre**:<br />QueryBuilderDeserializeInvalidMapping<br />**Hex**:<br />80041116<br />**Número**:<br />-2147217130|Los únicos valores válidos para la asignación son 'lógico' o 'interno' que está obsoleto.|
> |**Nombre**:<br />QueryBuilderDeserializeInvalidNode<br />**Hex**:<br />8004111c<br />**Número**:<br />-2147217124|El nodo de elemento encontrado no es válido.|
> |**Nombre**:<br />QueryBuilderDeserializeInvalidNoLock<br />**Hex**:<br />80041118<br />**Número**:<br />-2147217128|Los únicos valores válidos para el atributo no-lock son 'true', 'false', '1' y '0'.|
> |**Nombre**:<br />QueryBuilderDeserializeInvalidUseRawOrderBy<br />**Hex**:<br />800410fd<br />**Número**:<br />-2147217155|Los únicos valores válidos para el atributo useraworderby son 'true', 'false', '1' y '0'.|
> |**Nombre**:<br />QueryBuilderDeserializeInvalidUtcOffset<br />**Hex**:<br />8004111d<br />**Número**:<br />-2147217123|No se admite el atributo utc-offset para la deserialización.|
> |**Nombre**:<br />QueryBuilderDeserializeNoDocElemXml<br />**Hex**:<br />80041125<br />**Número**:<br />-2147217115|Elemento de documento no puede ser null.|
> |**Nombre**:<br />QueryBuilderDuplicateAlias<br />**Hex**:<br />80041130<br />**Número**:<br />-2147217104|FetchXML debe tener un alias único.|
> |**Nombre**:<br />QueryBuilderElementNotFound<br />**Hex**:<br />80041123<br />**Número**:<br />-2147217117|No se especificó un elemento requerido.|
> |**Nombre**:<br />QueryBuilderEntitiesDontMatch<br />**Hex**:<br />80041128<br />**Número**:<br />-2147217112|El nombre de la entidad especificado en fetchxml no coincide con el nombre de la entidad especificado en la entidad o expresión de consulta.|
> |**Nombre**:<br />QueryBuilderInvalid_Alias<br />**Hex**:<br />80041109<br />**Número**:<br />-2147217143|Alias no válido para la operación de agregado.|
> |**Nombre**:<br />QueryBuilderInvalid_Value<br />**Hex**:<br />80041108<br />**Número**:<br />-2147217144|El valor especificado para el tipo no es válido.|
> |**Nombre**:<br />QueryBuilderInvalidAggregateAttribute<br />**Hex**:<br />8004112F<br />**Número**:<br />-2147217105|Agregado {0} no se admite para atributo de tipo {1}.|
> |**Nombre**:<br />QueryBuilderInvalidAttributeValue<br />**Hex**:<br />80041139<br />**Número**:<br />-2147217095|El valor del atributo proporcionado no es válido.|
> |**Nombre**:<br />QueryBuilderInvalidColumnSetVersion<br />**Hex**:<br />80041112<br />**Número**:<br />-2147217134|La versión de columnset especificada no es válida.|
> |**Nombre**:<br />QueryBuilderInvalidConditionOperator<br />**Hex**:<br />80041120<br />**Número**:<br />-2147217120|Operador de condición no admitido.|
> |**Nombre**:<br />QueryBuilderInvalidDateGrouping<br />**Hex**:<br />80041135<br />**Número**:<br />-2147217099|Se pasó un valor no válido para un dategrouping especifiado.|
> |**Nombre**:<br />QueryBuilderInvalidFilterType<br />**Hex**:<br />80041122<br />**Número**:<br />-2147217118|Tipo de filtro no compatible Los valores válidos son "y" u "o".|
> |**Nombre**:<br />QueryBuilderInvalidJoinOperator<br />**Hex**:<br />80041121<br />**Número**:<br />-2147217119|Operador conjunto no admitido.|
> |**Nombre**:<br />QueryBuilderInvalidLogicalOperator<br />**Hex**:<br />800410fe<br />**Número**:<br />-2147217154|Operador lógico no admitido: {0}.  Los valores aceptados son ('y', 'o').|
> |**Nombre**:<br />QueryBuilderInvalidOrderType<br />**Hex**:<br />8004111f<br />**Número**:<br />-2147217121|Un tipo de pedido válido debe establecerse en el pedido antes de llamar a este método.|
> |**Nombre**:<br />QueryBuilderInvalidPagingCookie<br />**Hex**:<br />8004112A<br />**Número**:<br />-2147217110|Número de página no válida en cookies de paginación.|
> |**Nombre**:<br />QueryBuilderInvalidUpdate<br />**Hex**:<br />80041100<br />**Número**:<br />-2147217152|Se ha intentado actualizar un campo no se puede actualizar.|
> |**Nombre**:<br />QueryBuilderLinkNodeForOrderNotFound<br />**Hex**:<br />80041126<br />**Número**:<br />-2147217114|No se puede convertir la consulta en EntityExpression. No se encontró el vínculo nodo para el pedido.|
> |**Nombre**:<br />QueryBuilderMultipleIntersectEntities<br />**Hex**:<br />8004110e<br />**Número**:<br />-2147217138|Existe más de una entidad de intersección entre las dos entidades especificadas.|
> |**Nombre**:<br />QueryBuilderNoAlias<br />**Hex**:<br />8004110b<br />**Número**:<br />-2147217141|No se ha encontrado ningún alias para la entidad determinada en la condición.|
> |**Nombre**:<br />QueryBuilderNoAttribute<br />**Hex**:<br />80041103<br />**Número**:<br />-2147217149|El atributo especificado no existe en esta entidad.|
> |**Nombre**:<br />QueryBuilderNoAttrsDistinctConflict<br />**Hex**:<br />8004112C<br />**Número**:<br />-2147217108|La etiqueta no-attrs no se puede utilizar junto con Distinct establecido en true.|
> |**Nombre**:<br />QueryBuilderNoEntity<br />**Hex**:<br />80041102<br />**Número**:<br />-2147217150|No se encontró la entidad especificada.|
> |**Nombre**:<br />QueryBuilderNoEntityKey<br />**Hex**:<br />80041140<br />**Número**:<br />-2147217088|No se encontró la entitykey especificada.|
> |**Nombre**:<br />QueryBuilderPagingOrderBy<br />**Hex**:<br />80041129<br />**Número**:<br />-2147217111|El orden por columnas no coincide con el de cookies de paginación.|
> |**Nombre**:<br />QueryBuilderReportView_Does_Not_Exist<br />**Hex**:<br />8004110d<br />**Número**:<br />-2147217139|No existe una vista de informe para la entidad especificada.|
> |**Nombre**:<br />QueryBuilderSerializationInvalidIsQuickFindFilter<br />**Hex**:<br />80041138<br />**Número**:<br />-2147217096|Los únicos valores válidos para el atributo isquickfindfields son 'true', 'false', '1' y '0'.|
> |**Nombre**:<br />QueryBuilderSerialzeLinkTopCriteria<br />**Hex**:<br />80041114<br />**Número**:<br />-2147217132|Fetch no admite donde hay cláusulas con las condiciones de linkentity.|
> |**Nombre**:<br />QueryBuilderUnexpected<br />**Hex**:<br />80041101<br />**Número**:<br />-2147217151|Se produjo un error inesperado.|
> |**Nombre**:<br />QueryBuilderValue_GreaterThanZero<br />**Hex**:<br />8004110c<br />**Número**:<br />-2147217140|Debe especificarse un valor mayor que cero.|
> |**Nombre**:<br />QueryContainedSecuredAttributeWithoutAccess<br />**Hex**:<br />8004F506<br />**Número**:<br />-2147158778|La consulta incluye un atributo protegido al que el autor de la llamada no tiene acceso|
> |**Nombre**:<br />QueryFilterConditionAttributeNotPresentInExpressionEntity<br />**Hex**:<br />80071119<br />**Número**:<br />-2147020519|La consulta hace referencia a un campo que no existe en Dynamics 365: "{0}"|
> |**Nombre**:<br />QueryNotValidForStaticList<br />**Hex**:<br />8004F702<br />**Número**:<br />-2147158270|No se puede especificar una consulta para una lista estática.|
> |**Nombre**:<br />QueryParameterNotUnique<br />**Hex**:<br />8005E00B<br />**Número**:<br />-2147098613|El parámetro de consulta {0} debe definirse solo una vez en el conjunto de datos.|
> |**Nombre**:<br />QueueIdNotPresent<br />**Hex**:<br />80040528<br />**Número**:<br />-2147220184|Debe especificar la cola de destino. Especifique un valor válido en el campo de cola e inténtelo de nuevo.|
> |**Nombre**:<br />QueueItemNotPresent<br />**Hex**:<br />80040529<br />**Número**:<br />-2147220183|Debe escribir el nombre del registro que le gustaría pone en cola. Especifique un valor válido en el campo de elemento de cola e inténtelo de nuevo.|
> |**Nombre**:<br />QueueMailboxUnexpectedDeliveryMethod<br />**Hex**:<br />8005E210<br />**Número**:<br />-2147098096|Método de entrega para buzón asociado con una cola no puede ser cliente de outlook.|
> |**Nombre**:<br />QuickCreateDisabledOnEntity<br />**Hex**:<br />80060911<br />**Número**:<br />-2147088111|La entidad {0} no dispone de formulario de creación rápida o el número de formularios de creación rápida anidados superó el máximo permitido.|
> |**Nombre**:<br />QuickCreateInvalidEntityName<br />**Hex**:<br />80060910<br />**Número**:<br />-2147088112|El entityLogicalName no es válido. Este valor no puede ser nulo ni estar vacío, y debe representar una entidad de la organización.|
> |**Nombre**:<br />QuickFindQueryRecordLimitExceeded<br />**Hex**:<br />8004E024<br />**Número**:<br />-2147164124|El número de registros para esta búsqueda excede el límite de registro de Búsqueda rápida. Restrinja la consulta e inténtelo de nuevo.|
> |**Nombre**:<br />QuickFindSavedQueryAlreadyExists<br />**Hex**:<br />8004853A<br />**Número**:<br />-2147187398|"Solo una consulta de búsqueda rápida guardada puede existir para una entidad. Ya hay una consulta guardada de búsqueda rápida para la entidad con objecttypecode: {0}"|
> |**Nombre**:<br />QuickFormNotCustomizableThroughSdk<br />**Hex**:<br />8004F659<br />**Número**:<br />-2147158439|El SDK no admite la creación de un formulario del tipo "rápido". Este tipo de formulario está reservado para uso interno.|
> |**Nombre**:<br />QuoteAndSalesOrderCurrencyNotEqual<br />**Hex**:<br />80048cee<br />**Número**:<br />-2147185426|La divisa del registro no coincide con la divisa de la lista de precios.|
> |**Nombre**:<br />QuoteReviseExistingActiveQuote<br />**Hex**:<br />80048d00<br />**Número**:<br />-2147185408|La oferta no se puede revisar porque ya existe otra oferta en estado de borrador o activa y que tiene el mismo número de oferta.|
> |**Nombre**:<br />ReactivateEntityKeyOnlyForFailedJobs<br />**Hex**:<br />80060897<br />**Número**:<br />-2147088233|La reactivación de la clave de entidad solo se admite para el trabajo con error|
> |**Nombre**:<br />ReadIntentIncompatible<br />**Hex**:<br />80060881<br />**Número**:<br />-2147088255|Complemento intención de ejecución de contexto de ejecución actual no es compatible con su contexto principal|
> |**Nombre**:<br />ReadOnlyCreateValidationFailed<br />**Hex**:<br />80061002<br />**Número**:<br />-2147086334|No puede crear y asignar un valor a una instancia de propiedad para una propiedad de solo lectura.|
> |**Nombre**:<br />ReadOnlyUpdateValidationFailed<br />**Hex**:<br />80061003<br />**Número**:<br />-2147086333|No puede actualizar la instancia de propiedad para una propiedad de solo lectura.|
> |**Nombre**:<br />ReadOnlyUserNotSupported<br />**Hex**:<br />80041d40<br />**Número**:<br />-2147214016|No se admite el modo de acceso de solo lectura|
> |**Nombre**:<br />RecalculateNotSupportedOnNonRollupField<br />**Hex**:<br />80060554<br />**Número**:<br />-2147089068|Campo {0} de tipo {1} no admite recalcular acción. La acción de recalcular solo se puede llamar para el campo consolidado.|
> |**Nombre**:<br />RecipientMarkedDoNotEmail<br />**Hex**:<br />80040b09<br />**Número**:<br />-2147218679|El destinatario de tipo '{0}' con el identificador '{1}' está marcado como que no puede recibir correos|
> |**Nombre**:<br />RecommendationAzureConnectionCascadeActivateFailed<br />**Hex**:<br />80061633<br />**Número**:<br />-2147084749|No se puede activar uno o varios modelos de recomendación. Intente activar los modelos de recomendaciones existentes por sepadado de la conexión del servicio de Azure.|
> |**Nombre**:<br />RecommendationAzureConnectionFailed<br />**Hex**:<br />80061631<br />**Número**:<br />-2147084751|Error al conectar con el servicio de recomendaciones de Azure. Compruebe que la dirección URL del servicio y la cuenta de Azure son válidos y la suscripción de servicio está activa.|
> |**Nombre**:<br />RecommendationModelActivateConnectionMustBeActive<br />**Hex**:<br />80061607<br />**Número**:<br />-2147084793|La conexión del servicio de recomendaciones de Aprendizaje automático de Microsoft Azure se debe activar antes de poder activar el modelo. Active la conexión del servicio de recomendaciones e inténtelo de nuevo.|
> |**Nombre**:<br />RecommendationModelActiveVersionInvalidStatus<br />**Hex**:<br />80061602<br />**Número**:<br />-2147084798|La versión del modelo utilizada debe generarse correctamente para poder activar el modelo.|
> |**Nombre**:<br />RecommendationModelActiveVersionNotSet<br />**Hex**:<br />80061601<br />**Número**:<br />-2147084799|La versión del modelo utilizada está vacía. Para activar el modelo, especifique la versión del modelo.|
> |**Nombre**:<br />RecommendationModelBuildConnectionMustBeActive<br />**Hex**:<br />80061606<br />**Número**:<br />-2147084794|La conexión del servicio de recomendaciones de Aprendizaje automático de Microsoft Azure se debe activar antes de crear el modelo de recomendación. Active la conexión del servicio de recomendaciones e inténtelo de nuevo.|
> |**Nombre**:<br />RecommendationModelExpired<br />**Hex**:<br />80061608<br />**Número**:<br />-2147084792|El modelo de recomendaciones ha expirado. Cambie la fecha de válidez y pruebe activar el modelo de nuevo.|
> |**Nombre**:<br />RecommendationModelMappingDuplicateRecord<br />**Hex**:<br />80061610<br />**Número**:<br />-2147084784|Los valores de asignación del modelo de recomendaciones para entidad, tipo de asignación y versión deben ser únicos.|
> |**Nombre**:<br />RecommendationModelMappingReadOnly<br />**Hex**:<br />80061611<br />**Número**:<br />-2147084783|No se puede modificar una entidad de recomendación si tiene una entidad de cesta correspondiente.|
> |**Nombre**:<br />RecommendationModelVersionActive<br />**Hex**:<br />80061620<br />**Número**:<br />-2147084768|La versión de RecommendationModel está seleccionada como la versión activa en un modelo y no se puede eliminar.|
> |**Nombre**:<br />RecommendationModelVersionBuildInProgress<br />**Hex**:<br />80061621<br />**Número**:<br />-2147084767|Un flujo de trabajo para crear un modelo ya está en curso. No puede iniciar otro flujo de trabajo de compilación hasta que finalice el flujo de trabajo actual.|
> |**Nombre**:<br />RecommendationModelVersionDuplicateName<br />**Hex**:<br />80061622<br />**Número**:<br />-2147084766|Ya existe una versión modelo con el mismo nombre. Especifique un nombre diferente.|
> |**Nombre**:<br />RecommendationsUnavailable<br />**Hex**:<br />80061605<br />**Número**:<br />-2147084795|Las recomendaciones de producto de Azure Machine Learning no están disponibles temporalmente. Solo las recomendaciones de catálogo están disponibles.|
> |**Nombre**:<br />RecommendedDocumentsRetrievalFailure<br />**Hex**:<br />80071015<br />**Número**:<br />-2147020779|No se pueden recuperar sugerencias del documento del origen del documento.|
> |**Nombre**:<br />RecommendedDocumentsRetrievalFailureWhenSPSiteNotConfigured<br />**Hex**:<br />80071028<br />**Número**:<br />-2147020760|No se pueden recuperar sugerencias del documento del origen del documento.|
> |**Nombre**:<br />RecordAndOpportunityCurrencyNotEqual<br />**Hex**:<br />80048cef<br />**Número**:<br />-2147185425|La divisa del registro no coincide con la divisa de la lista de precios.|
> |**Nombre**:<br />RecordAndPricelistCurrencyNotEqual<br />**Hex**:<br />80048cf6<br />**Número**:<br />-2147185418|La divisa del registro no coincide con la divisa de la lista de precios.|
> |**Nombre**:<br />RecordCanOnlyBeRevisedFromActiveState<br />**Hex**:<br />8004F883<br />**Número**:<br />-2147157885|Solo puede revisar un producto activo.|
> |**Nombre**:<br />RecordCountExceededForExcelOnlineError<br />**Hex**:<br />80072456<br />**Número**:<br />-2147015594|El número de registros esperado es {0}. El número de registros actual es:{1}|
> |**Nombre**:<br />RecordNotFoundByEntityKey<br />**Hex**:<br />80060891<br />**Número**:<br />-2147088239|No existe en la entidad {0} un registro con los valores clave especificados|
> |**Nombre**:<br />RecordResolutionFailed<br />**Hex**:<br />8004F603<br />**Número**:<br />-2147158525|No se tiene que actualizar el registro porque el registro original ya no existe en Microsoft Dynamics 365.|
> |**Nombre**:<br />RecurrenceCalendarTypeNotSupported<br />**Hex**:<br />8004E116<br />**Número**:<br />-2147163882|No se admite el tipo de calendario.|
> |**Nombre**:<br />RecurrenceEndDateTooBig<br />**Hex**:<br />8004E119<br />**Número**:<br />-2147163879|La fecha de finalización del patrón de periodicidad no es válida.|
> |**Nombre**:<br />RecurrenceHasNoOccurrence<br />**Hex**:<br />8004E117<br />**Número**:<br />-2147163881|No hay resultados para el patrón de periodicidad.|
> |**Nombre**:<br />RecurrenceRuleDeleteFailure<br />**Hex**:<br />8004E111<br />**Número**:<br />-2147163887|No se puede eliminar una regla que esté vinculada a una regla maestra existente. Elimine la regla mediante la entidad primaria.|
> |**Nombre**:<br />RecurrenceRuleUpdateFailure<br />**Hex**:<br />8004E110<br />**Número**:<br />-2147163888|No se puede actualizar una regla que esté vinculada a una regla maestra existente. Actualice la regla mediante la entidad primaria.|
> |**Nombre**:<br />RecurrenceStartDateTooSmall<br />**Hex**:<br />8004E118<br />**Número**:<br />-2147163880|La fecha de inicio del patrón de periodicidad no es válida.|
> |**Nombre**:<br />RecurringSeriesCompleted<br />**Hex**:<br />8004E10B<br />**Número**:<br />-2147163893|La serie tiene un ExpansionStateCode no válido.|
> |**Nombre**:<br />RecurringSeriesMasterIsLocked<br />**Hex**:<br />8004E113<br />**Número**:<br />-2147163885|El registro maestro de series periódicas está bloqueado por otro proceso.|
> |**Nombre**:<br />RefEntityRelationshipRoleRequired<br />**Hex**:<br />80048470<br />**Número**:<br />-2147187600|El rol de relación de entidad de la entidad de referencia es necesario para crear una nueva relación de entidad de uno a varios.|
> |**Nombre**:<br />ReferencedEntityHasLogicalPrimaryNameField<br />**Hex**:<br />8004432E<br />**Número**:<br />-2147204306|Esta entidad tiene un campo principal que es lógico y, por tanto, no puede ser la entidad de referencia en una relación de uno a varios|
> |**Nombre**:<br />ReferencedEntityMustHaveLookupView<br />**Hex**:<br />80044337<br />**Número**:<br />-2147204297|Las entidades a las que se hace referencia de una relación deben tener una vista de búsqueda|
> |**Nombre**:<br />ReferencingEntityCannotBeSolutionAware<br />**Hex**:<br />80044350<br />**Número**:<br />-2147204272|Las entidades de referencia de una relación no puede ser un componente de una solución.|
> |**Nombre**:<br />ReferencingEntityMustHaveAssociationView<br />**Hex**:<br />80044338<br />**Número**:<br />-2147204296|Las entidades de referencia de una relación deben tener una vista de asociación|
> |**Nombre**:<br />RefferedSolutionIsDifferent<br />**Hex**:<br />80050122<br />**Número**:<br />-2147155678|Fila no publicada encontrada fuera de la solución activa: SiteMapId = {0}, SolutionId = {1}|
> |**Nombre**:<br />ReflexiveEntityParentOrChildDoesNotExist<br />**Hex**:<br />80040388<br />**Número**:<br />-2147220600|La entidad primaria o la entidad secundaria no existe|
> |**Nombre**:<br />RefRoleNavPaneDisplayOptionRequired<br />**Hex**:<br />80060898<br />**Número**:<br />-2147088232|El atributo NavPaneDisplayOption es necesario para el rol de referencia a de una relación de uno a varios {0}.|
> |**Nombre**:<br />RegardingObjectValuesRetrievalFailure<br />**Hex**:<br />80071012<br />**Número**:<br />-2147020782|No se pudieron recuperar valores de objetos referente a.|
> |**Nombre**:<br />RelatedEntityAlreadyExistsInProfile<br />**Hex**:<br />8005F21e<br />**Número**:<br />-2147093986|La entidad relacionada ya existe en este perfil.|
> |**Nombre**:<br />RelatedEntityDoesNotExistInProfileItem<br />**Hex**:<br />8006098E<br />**Número**:<br />-2147087986|La entidad relacionada {0} de la asociación {1} del elemento de perfil de Mobile Offline {2} no existe en los elementos del perfil {3}.|
> |**Nombre**:<br />RelatedEntityDoesNotExistsInProfile<br />**Hex**:<br />8005F21f<br />**Número**:<br />-2147093985|La entidad relacionada no existe en los elementos del perfil.|
> |**Nombre**:<br />RelatedEntityGenericError<br />**Hex**:<br />8005F220<br />**Número**:<br />-2147093984|Se ha producido un error inesperado al crear la asociación del perfil. Inténtelo de nuevo.|
> |**Nombre**:<br />RelatedRecordsFailure<br />**Hex**:<br />80071013<br />**Número**:<br />-2147020781|Error al recuperar registros relacionados.|
> |**Nombre**:<br />RelationshipGraphLimitExceeded<br />**Hex**:<br />80071139<br />**Número**:<br />-2147020487|Ha especificado una o varias asociaciones de elementos de perfil para las entidades definidas en el perfil de '{0}'. Compruebe las asociaciones del elemento de perfil que afectan a la entidad de '{1}' que tiene un recuento de asociación de {2} y supera el límite admitido de {3}.|
> |**Nombre**:<br />RelationshipGraphLimitExceededForIntersectEntity<br />**Hex**:<br />80071135<br />**Número**:<br />-2147020491|Ha especificado una o varias asociaciones de elementos de perfil para las entidades definidas en el perfil de '{0}' y relacionado con la entidad interseccionada '{1}'. Compruebe las asociaciones del elemento de perfil que afectan a las entidades '{2}' y '{3}' que tienen un recuento total de asociación de {4} y superan el límite admitido de {5}.|
> |**Nombre**:<br />RelationshipInsightsFeatureDisableError<br />**Hex**:<br />80044292<br />**Número**:<br />-2147204462|La característica Información de relaciones no se puede deshabilitar|
> |**Nombre**:<br />RelationshipInsightsFeatureNotEnabledError<br />**Hex**:<br />80044293<br />**Número**:<br />-2147204461|La característica Información de relaciones no está habilitada o el paquete RI no está instalado|
> |**Nombre**:<br />RelationshipIntelligenceSDKInvocationError<br />**Hex**:<br />80044276<br />**Número**:<br />-2147204490|Necesita Dynamics 365 (online) para poder utilizar el SDK de Información de relaciones.|
> |**Nombre**:<br />RelationshipIsNotCustomRelationship<br />**Hex**:<br />8004700a<br />**Número**:<br />-2147192822|La relaación especificada no es una relación personalizada|
> |**Nombre**:<br />RelationshipNameLengthExceedsLimit<br />**Hex**:<br />8004802A<br />**Número**:<br />-2147188694|Los identificadores no pueden tener más de {1} caracteres. El nombre proporcionado: {0} la longitud es mayor que la longitud máxima de {1} caracteres.|
> |**Nombre**:<br />RelationshipNotCreatedForOfficeGraphError<br />**Hex**:<br />80044235<br />**Número**:<br />-2147204555|Esta relación no se puede crear porque ninguna de las entidades está habilitada para Office Graph.|
> |**Nombre**:<br />RelationshipNotUpdatedForOfficeGraphError<br />**Hex**:<br />80044236<br />**Número**:<br />-2147204554|Esta relación no se puede actualizar para Office Graph porque ninguna de las entidades está habilitada para Office Graph.|
> |**Nombre**:<br />RelationshipRoleMismatch<br />**Hex**:<br />80048467<br />**Número**:<br />-2147187609|El nombre del rol de relación {0} no coincide con el nombre de entidad esperado de {1} o {2}.|
> |**Nombre**:<br />RelationshipRoleNodeNumberInvalid<br />**Hex**:<br />80048469<br />**Número**:<br />-2147187607|Debe haber dos nodos del rol de relación de entidad cuando se crea una nueva relación de entidad de muchos a muchos.|
> |**Nombre**:<br />RelationshipSchemaNameConflictWithFieldNameOnReferencedEntity<br />**Hex**:<br />80048835<br />**Número**:<br />-2147186635|RelationshipName {0} tiene un conflicto con el nombre del atributo en la entidad {1} (entityid={2}). Utilice un nombre único para la relación.|
> |**Nombre**:<br />RelatioshipAlreadyExists<br />**Hex**:<br />8005F221<br />**Número**:<br />-2147093983|La relación relacionada para la entidad ya existe en este perfil. |
> |**Nombre**:<br />RemoveActiveCustomizationsNotSupported<br />**Hex**:<br />8004F059<br />**Número**:<br />-2147159975|RemoveActiveCustomizations no es compatible con componentes de tipo {0}|
> |**Nombre**:<br />ReportDoesNotExist<br />**Hex**:<br />80040499<br />**Número**:<br />-2147220327|El informe no existe. ReportId:{0}|
> |**Nombre**:<br />ReportFileTooBig<br />**Hex**:<br />80048297<br />**Número**:<br />-2147188073|El archivo es demasiado grande y no se puede cargar. Reduzca el tamaño del archivo e inténtelo de nuevo.|
> |**Nombre**:<br />ReportFileZeroLength<br />**Hex**:<br />80048296<br />**Número**:<br />-2147188074|Ha cargado un archivo vacío.  Seleccione un nuevo archivo e inténtelo de nuevo.|
> |**Nombre**:<br />ReportImportCategoryOptionNotFound<br />**Hex**:<br />8004F028<br />**Número**:<br />-2147160024|No se encontró una opción de categoría para los informes.|
> |**Nombre**:<br />ReportingServicesReportExpected<br />**Hex**:<br />80040484<br />**Número**:<br />-2147220348|El informe no es un informe de Reporting Services.|
> |**Nombre**:<br />ReportLocalProcessingError<br />**Hex**:<br />80048310<br />**Número**:<br />-2147187952|Error al visualizar un informe procesado localmente. ReportId:{0}|
> |**Nombre**:<br />ReportLoopBeingCreated<br />**Hex**:<br />80040498<br />**Número**:<br />-2147220328|La creación de esta asociación jerárquica crearía un bucle en la jerarquía de informes.|
> |**Nombre**:<br />ReportLoopExists<br />**Hex**:<br />80040497<br />**Número**:<br />-2147220329|Existe un bucle en la jerarquía de los informes.|
> |**Nombre**:<br />ReportMissingDataSourceCredentialsError<br />**Hex**:<br />80048311<br />**Número**:<br />-2147187951|No se proporcionaron las credenciales para un origen de datos usado por el informe.  ReportId:{0}|
> |**Nombre**:<br />ReportMissingDataSourceError<br />**Hex**:<br />80048312<br />**Número**:<br />-2147187950|No se proporcionó un origen de datos esperado por el informe.  ReportId:{0}|
> |**Nombre**:<br />ReportMissingEndpointError<br />**Hex**:<br />80048313<br />**Número**:<br />-2147187949|No se tuvo acceso al extremo SOAP usado por el control ReportViewer. |
> |**Nombre**:<br />ReportMissingParameterError<br />**Hex**:<br />80048314<br />**Número**:<br />-2147187948|No se proporcionó el parámetro esperado para el informe. ReportId:{0}|
> |**Nombre**:<br />ReportMissingReportSourceError<br />**Hex**:<br />80048315<br />**Número**:<br />-2147187947|No se especificó un origen para el informe.  ReportId:{0}|
> |**Nombre**:<br />ReportNotAvailable<br />**Hex**:<br />80048299<br />**Número**:<br />-2147188071|Informe no disponible|
> |**Nombre**:<br />ReportParentChildNotCustomizable<br />**Hex**:<br />8004832f<br />**Número**:<br />-2147187921|No se pudo actualizar el informe porque el informe primario o el informe secundario no se pueden personalizar.|
> |**Nombre**:<br />ReportRdlSandboxing<br />**Hex**:<br />80048293<br />**Número**:<br />-2147188077|Fallo al cargar el informe a causa de limitaciones en el espacio seguro para RDL en el servidor de informes.|
> |**Nombre**:<br />ReportRenderError<br />**Hex**:<br />80040494<br />**Número**:<br />-2147220332|Se ha producido un error durante el informe de representación.|
> |**Nombre**:<br />ReportSecurityError<br />**Hex**:<br />80048316<br />**Número**:<br />-2147187946|El informe tiene una infracción de seguridad. ReportId:{0}|
> |**Nombre**:<br />ReportServerInvalidUrl<br />**Hex**:<br />80048301<br />**Número**:<br />-2147187967|No puede ponerse en contacto con el servidor de informes desde la dirección URL específicada|
> |**Nombre**:<br />ReportServerNoPrivilege<br />**Hex**:<br />80048302<br />**Número**:<br />-2147187966|No hay suficientes privilegios para configurar el servidor de informes|
> |**Nombre**:<br />ReportServerSP2HotFixNotApplied<br />**Hex**:<br />80048309<br />**Número**:<br />-2147187959|El servidor de informes SP2 Workgroup no tiene la revisión para la creación de roles|
> |**Nombre**:<br />ReportServerUnknownException<br />**Hex**:<br />80048300<br />**Número**:<br />-2147187968|Excepción desconocida emitida por el servidor de informes|
> |**Nombre**:<br />ReportServerVersionLow<br />**Hex**:<br />80048303<br />**Número**:<br />-2147187965|El servidor de informes no cumple los requisitos mínimos de la versión|
> |**Nombre**:<br />ReportTypeBlocked<br />**Hex**:<br />80048295<br />**Número**:<br />-2147188075|El informe no es de un tipo válido.  No pueden cargarse o descargarse.|
> |**Nombre**:<br />ReportUploadDisabled<br />**Hex**:<br />80048294<br />**Número**:<br />-2147188076|No se pueden cargar los informes de los servicios de informes. Si desea crear un nuevo informe, utilice Asistente para informes.|
> |**Nombre**:<br />ReportViewerError<br />**Hex**:<br />8004832c<br />**Número**:<br />-2147187924|Se ha producido un error durante el informe de representación. ReportId:{0}|
> |**Nombre**:<br />RequestIsNotAuthenticated<br />**Hex**:<br />80044302<br />**Número**:<br />-2147204350|No se ha autentificado la solicitud.|
> |**Nombre**:<br />RequestLengthTooLarge<br />**Hex**:<br />8004418a<br />**Número**:<br />-2147204726|La longitud del mensaje de solicitud es excesiva.|
> |**Nombre**:<br />RequiredBundleItemCannotBeUpdated<br />**Hex**:<br />80081009<br />**Número**:<br />-2146955255|No puede eliminar este elemento de agrupación porque es un producto necesario en la agrupación.|
> |**Nombre**:<br />RequiredBundleProductCannotBeDeleted<br />**Hex**:<br />80081008<br />**Número**:<br />-2146955256|No puede eliminar este registro del producto porque es un producto necesario en una agrupación.|
> |**Nombre**:<br />RequiredChildReportHasOtherParent<br />**Hex**:<br />8004F029<br />**Número**:<br />-2147160023|No se encontró una opción de categoría para los informes.|
> |**Nombre**:<br />RequiredColumnsNotFoundInImportFile<br />**Hex**:<br />80040383<br />**Número**:<br />-2147220605|Una o varias columnas de origen que se utilizan en la transformación no existe en el archivo de origen.|
> |**Nombre**:<br />RequiredFieldMissing<br />**Hex**:<br />80040200<br />**Número**:<br />-2147220992|Falta un campo necesario.|
> |**Nombre**:<br />RequiredProcessFlowStepIsNotComplete<br />**Hex**:<br />8006041d<br />**Número**:<br />-2147089379|No puede pasar a la siguiente etapa o completar el proceso hasta que se complete el paso de Flow o paso de aprobación requerido en la etapa actual.|
> |**Nombre**:<br />RequiredProcessFlowStepIsNotStarted<br />**Hex**:<br />8006041e<br />**Número**:<br />-2147089378|Para pasar a la siguiente etapa o completar el proceso, haga clic en el paso de Flow requerido o el paso de aprobación en la etapa actual. No puede pasar a las siguientes etapas o completar el proceso hasta que se complete el paso de Flow o paso de aprobación requerido en la etapa actual.|
> |**Nombre**:<br />RequiredProcessStepIsNull<br />**Hex**:<br />8006041a<br />**Número**:<br />-2147089382|Para desplazarse a la fase siguiente, complete los pasos requeridos.|
> |**Nombre**:<br />RequireValidImportMapForUpdate<br />**Hex**:<br />8004F600<br />**Número**:<br />-2147158528|No se puede completar la operación de actualización porque la asignación de importación usada para la importación no es válida.|
> |**Nombre**:<br />RestrictedSolutionName<br />**Hex**:<br />8004F022<br />**Número**:<br />-2147160030|El nombre único de la solución '{0}' está restringido y solo lo pueden usar soluciones internas.|
> |**Nombre**:<br />RestrictInheritedRole<br />**Hex**:<br />80044152<br />**Número**:<br />-2147204782|Los roles heredado no se pueden modificar.|
> |**Nombre**:<br />RetiredProductToBundle<br />**Hex**:<br />8004F993<br />**Número**:<br />-2147157613|No puede agregar un producto retirado a una agrupación.|
> |**Nombre**:<br />RetrieveImagePropertiesFail<br />**Hex**:<br />80072552<br />**Número**:<br />-2147015342|No se pueden recuperar propiedades para la imagen proporcionada de la entidad|
> |**Nombre**:<br />RetrieveOrganizationInfoUnexpectedError<br />**Hex**:<br />80072301<br />**Número**:<br />-2147015935|Error inesperado durante recuperación de información de la organización. Los servicios dependientes es posible que no estén disponibles en este momento. Vuelva a intentarlo más adelante.|
> |**Nombre**:<br />RetrieveRecordOfflineErrorCode<br />**Hex**:<br />8005F213<br />**Número**:<br />-2147093997|Este registro no está disponible mientras está sin conexión.  Vuelva a conectarse e inténtelo de nuevo.|
> |**Nombre**:<br />RetrieveUserLicenseUnexpectedError<br />**Hex**:<br />80072300<br />**Número**:<br />-2147015936|Error inesperado durante recuperación de información de licencias de usuario Los servicios dependientes es posible que no estén disponibles en este momento. Vuelva a intentarlo más adelante.|
> |**Nombre**:<br />RetryFailed<br />**Hex**:<br />8004F045<br />**Número**:<br />-2147159995|La acción falló después de {0} reintentos. InnerException es: {1}.|
> |**Nombre**:<br />RibbonImportDependencyMissingEntity<br />**Hex**:<br />8004F104<br />**Número**:<br />-2147159804|El elemento de la cinta de opciones '{0}' depende de la entidad {1}.|
> |**Nombre**:<br />RibbonImportDependencyMissingRibbonControl<br />**Hex**:<br />8004F107<br />**Número**:<br />-2147159801|El elemento de la cinta de opciones '{0}' depende del control de la cinta de opciones id='{1}'.|
> |**Nombre**:<br />RibbonImportDependencyMissingRibbonElement<br />**Hex**:<br />8004F105<br />**Número**:<br />-2147159803|El elemento de la cinta de opciones '{0}' depende de <{1} Id="{2}" />.|
> |**Nombre**:<br />RibbonImportDependencyMissingWebResource<br />**Hex**:<br />8004F106<br />**Número**:<br />-2147159802|El elemento de la cinta de opciones '{0}' depende del recurso web id='{1}'.|
> |**Nombre**:<br />RibbonImportDuplicateElementId<br />**Hex**:<br />8004F10B<br />**Número**:<br />-2147159797|El elemento de la cinta de opciones con Id:{0} no se puede importar porque ya existe un elemento de la cinta de opciones con el mismo identificador.|
> |**Nombre**:<br />RibbonImportEntityNotSupported<br />**Hex**:<br />8004F103<br />**Número**:<br />-2147159805|La solución no se puede importar porque la entidad {0} contiene una definición de cinta de opciones que no se admite para dicha entidad. Quite el nodo RibbonDiffXml de la definición de entidad e intente importar de nuevo.|
> |**Nombre**:<br />RibbonImportHidingBasicHomeTab<br />**Hex**:<br />8004F101<br />**Número**:<br />-2147159807|La definición de la cinta de opciones que se va a importar quitará la pestaña de inicio de Microsoft Dynamics 365. Si no incluye ninguna definición de la pestaña de inicio, la cinta de opciones no se mostrará en las áreas de la aplicación en las que se muestra la pestaña de inicio.|
> |**Nombre**:<br />RibbonImportHidingJewel<br />**Hex**:<br />8004F10A<br />**Número**:<br />-2147159798|Las personalizaciones de cinta de opciones no se pueden ocultar en el nodo <Jewel>. Cualquier personalización de la cinta que oculte este nodo se omitirá durante la importación y no se exportará.|
> |**Nombre**:<br />RibbonImportInvalidPrivilegeName<br />**Hex**:<br />8004F102<br />**Número**:<br />-2147159806|RibbonDiffXml en esta solución contiene una referencia a un privilegios no válido: {0}. Actualice RibbonDiffXml para que haga referencia a un privilegio válido e intente importar de nuevo.|
> |**Nombre**:<br />RibbonImportLocationAndIdDoNotMatch<br />**Hex**:<br />8004F109<br />**Número**:<br />-2147159799|El identificador de CustomAction '{0}' no puede reemplazar '{1}' porque '{2}' no coincide con el valor de ubicación de CustomAction.|
> |**Nombre**:<br />RibbonImportModifyingTopLevelNode<br />**Hex**:<br />8004F108<br />**Número**:<br />-2147159800|No se pueden realizar personalizaciones de la cinta de opciones en los siguientes nodos de nivel superior de la cinta de opciones: <Ribbon>, <ContextualGroups>, y <Tabs>.|
> |**Nombre**:<br />RibbonImportRibbonDiffIdInvalidLength<br />**Hex**:<br />8004F10C<br />**Número**:<br />-2147159796|No se puede importar este elemento de la cinta de opciones porque la duración del identificador supera la longitud máxima de 128 caracteres: {0}|
> |**Nombre**:<br />RINotProvisioned<br />**Hex**:<br />80044281<br />**Número**:<br />-2147204479|Información de relaciones no se ha activado para su organización {0}.|
> |**Nombre**:<br />RoboticProcessAutomationFlowProcessesNotEnabled<br />**Hex**:<br />80060471<br />**Número**:<br />-2147089295|La creación de procesos reservados no está habilitada.|
> |**Nombre**:<br />RoboticProcessAutomationFlowProcessesOnlyAvailableOnline<br />**Hex**:<br />80060472<br />**Número**:<br />-2147089294|La creación de procesos de reservados solo es accesible en línea.|
> |**Nombre**:<br />RoleAlreadyExists<br />**Hex**:<br />80041403<br />**Número**:<br />-2147216381|Un rol con el nombre especificado '{0}' ya existe en la unidad de negocio {1} y el Id. de solución {3}. Id de rol: {2}|
> |**Nombre**:<br />RoleNotEnabledForTabletApp<br />**Hex**:<br />8005F203<br />**Número**:<br />-2147094013|No está autorizado para utilizar esta aplicación.\nConsulte con el administrador del sistema para actualizar su configuración.|
> |**Nombre**:<br />RollupAggregateQueryRecordLimitExceeded<br />**Hex**:<br />8004E025<br />**Número**:<br />-2147164123|Los cálculos no se pueden llevar a cabo en línea porque se ha alcanzado el límite de cálculo de {0} registros relacionados.|
> |**Nombre**:<br />RollupCalculationLimitReached<br />**Hex**:<br />80060561<br />**Número**:<br />-2147089055|Los cálculos no se pueden realizar en este momento porque se ha alcanzado el límite de cálculo. Espere e inténtelo de nuevo.|
> |**Nombre**:<br />RollupDependentFieldNameAlreadyExists<br />**Hex**:<br />80060556<br />**Número**:<br />-2147089066|El campo dependiente obligatorio {0} para el campo consolidado no se puede crear, ya que existe otro campo con el mismo nombre. Utilice un nombre alternativo para crear el campo consolidado.|
> |**Nombre**:<br />RollupFieldAggregateFunctionNotAllowed<br />**Hex**:<br />80060546<br />**Número**:<br />-2147089082|No se permite la función agregada {0}.|
> |**Nombre**:<br />RollupFieldAggregateFunctionNotAllowedForRollupFieldDataType<br />**Hex**:<br />80060545<br />**Número**:<br />-2147089083|No se permite la función agregada {0} si el campo consolidado es un tipo de datos {1}.|
> |**Nombre**:<br />RollupFieldAndAggregateFieldDataTypeFormatMismatch<br />**Hex**:<br />80060544<br />**Número**:<br />-2147089084|No se permite el tipo de datos {0} con el formato {1} para el campo agregado si el campo consolidado es un tipo de datos {2} con el formato {3}.|
> |**Nombre**:<br />RollupFieldDefinitionNotValid<br />**Hex**:<br />80060553<br />**Número**:<br />-2147089069|El cálculo ha fallado porque la definición del campo consolidado no es válida. Póngase en contacto con el administrador del sistema.|
> |**Nombre**:<br />RollupFieldDependentFieldCannotDeleted<br />**Hex**:<br />80060541<br />**Número**:<br />-2147089087|El campo consolidado {0} depende de este campo. Solo se puede eliminar si se elimina el campo consolidado correspondiente {0}.|
> |**Nombre**:<br />RollupFieldNoWriteAccess<br />**Hex**:<br />8004E027<br />**Número**:<br />-2147164121|El usuario no tiene permiso de escritura en el registro {0} {1} con el identificador:{2} para calcular el campo consolidado.|
> |**Nombre**:<br />RollupFieldsAggregateFieldDataTypeNotAllowedSimilarRollupFieldDataType<br />**Hex**:<br />8006053d<br />**Número**:<br />-2147089091|No se permite el tipo de datos {0} para el campo agregado si el campo consolidado es un tipo de datos {1}.|
> |**Nombre**:<br />RollupFieldsAggregateFieldNotBelongToRelatedEntity<br />**Hex**:<br />80060540<br />**Número**:<br />-2147089088|El campo agregado {0} no pertenece a la entidad relacionada {1}.|
> |**Nombre**:<br />RollupFieldsAggregateFieldNotBelongToSourceEntity<br />**Hex**:<br />8006053f<br />**Número**:<br />-2147089089|El campo agregado {0} no pertenece a la entidad de origen {1}.|
> |**Nombre**:<br />RollupFieldsAggregateFieldNotPartOfEntity<br />**Hex**:<br />80060537<br />**Número**:<br />-2147089097|El campo agregado {0} no pertenece a la entidad {1}|
> |**Nombre**:<br />RollupFieldsAggregateFunctionTypeMismatch<br />**Hex**:<br />8006053a<br />**Número**:<br />-2147089094|No se permite el tipo de datos {0} para el campo agregado si la función agregada es {1}.|
> |**Nombre**:<br />RollupFieldsAggregateNotDefined<br />**Hex**:<br />80060536<br />**Número**:<br />-2147089098|Se deben proporcionar una función agregada y un campo agregado para el informe.|
> |**Nombre**:<br />RollupFieldsAggregateOnRollupFieldOrComplexCalcFieldNotAllowed<br />**Hex**:<br />8006053c<br />**Número**:<br />-2147089092|El campo de agregado debe ser un campo simple o un campo calculado básico.|
> |**Nombre**:<br />RollupFieldsDataTypeNotValid<br />**Hex**:<br />8006053e<br />**Número**:<br />-2147089090|El tipo de datos {0} no es válido para el campo de informe.|
> |**Nombre**:<br />RollupFieldsGeneric<br />**Hex**:<br />8006053b<br />**Número**:<br />-2147089093|La definición de campo de informe no es válida.|
> |**Nombre**:<br />RollupFieldSourceFilterFieldNotAllowed<br />**Hex**:<br />80060548<br />**Número**:<br />-2147089080|El filtro de la entidad de origen debe usar un campo simple o un campo calculado básico. No puede usar un campo consolidado o un campo calculado que esté usando un campo consolidado.|
> |**Nombre**:<br />RollupFieldsSourceEntityNotHierarchical<br />**Hex**:<br />80060535<br />**Número**:<br />-2147089099|La jerarquía de la entidad de origen {0} no existe.|
> |**Nombre**:<br />RollupFieldsSourceFilterConditionInvalid<br />**Hex**:<br />80060538<br />**Número**:<br />-2147089096|La condición de filtro {1} de la entidad de origen {0} no es válida.|
> |**Nombre**:<br />RollupFieldsTargetEntityNotValid<br />**Hex**:<br />80060552<br />**Número**:<br />-2147089070|No se permite la entidad relacionada {0} para los informes.|
> |**Nombre**:<br />RollupFieldsTargetFilterConditionInvalid<br />**Hex**:<br />80060539<br />**Número**:<br />-2147089095|La condición de filtro {1} de la entidad relacionada {0} no es válida.|
> |**Nombre**:<br />RollupFieldsTargetRelationshipNotPartOfOneToNRelationship<br />**Hex**:<br />80060534<br />**Número**:<br />-2147089100|No existe una relación de 1:N {0} entre la entidad de origen {1} y la entidad relacionada {2}.|
> |**Nombre**:<br />RollupFieldsTargetRelationshipNull<br />**Hex**:<br />80060533<br />**Número**:<br />-2147089101|La entidad relacionada está vacía. Se debe proporcionar cuando la jerarquía de entidad de origen no se usa para la consolidación.|
> |**Nombre**:<br />RollupFieldsTargetSameAsSourceEntity<br />**Hex**:<br />80060551<br />**Número**:<br />-2147089071|No se permiten las relaciones de 1:N que se hacen referencia a sí mismas para el campo consolidado.|
> |**Nombre**:<br />RollupFieldsV2FeatureNotEnabled<br />**Hex**:<br />80060565<br />**Número**:<br />-2147089051|La característica no es compatible con la versión actual del producto|
> |**Nombre**:<br />RollupFieldTargetFilterFieldNotAllowed<br />**Hex**:<br />80060549<br />**Número**:<br />-2147089079|El filtro de la entidad de destino debe usar un campo simple o un campo calculado básico. No puede usar un campo consolidado o un campo calculado que esté usando un campo consolidado.|
> |**Nombre**:<br />RollupFormulaFieldInvalid<br />**Hex**:<br />80060560<br />**Número**:<br />-2147089056|El campo de fórmula no es válido.|
> |**Nombre**:<br />RollupInvalidAttributeForFilterCondition<br />**Hex**:<br />80060564<br />**Número**:<br />-2147089052|El atributo {0} no se admite para la condición de filtro.|
> |**Nombre**:<br />RollupOrCalcNotAllowedInWorkflowWaitCondition<br />**Hex**:<br />80060557<br />**Número**:<br />-2147089065|El campo {0} es un campo consolidado o un campo a dependiente consolidado o un campo calculado. Estos campos no se admiten en la condición de espera de flujo de trabajo.|
> |**Nombre**:<br />RollupTargetLinkedEntityCanOnlyUsedForActivityPartyEntities<br />**Hex**:<br />80060563<br />**Número**:<br />-2147089053|La entidad relacionada del destino solo puede usar para la entidad {0} para consolidarla sobre {1} entidades de tipo.|
> |**Nombre**:<br />RollupTargetLinkedEntityOnlySupportedForActivityEntities<br />**Hex**:<br />80060562<br />**Número**:<br />-2147089054|La entidad relacionada del destino no se admite para consolidarla sobre {0} entidades de tipo.|
> |**Nombre**:<br />RollupTargetLinkedRelationshipNotValid<br />**Hex**:<br />80060566<br />**Número**:<br />-2147089050|La relación vinculada del destino {0} no es válida.|
> |**Nombre**:<br />RootBusinessUnitCannotBeDisabled<br />**Hex**:<br />80041d63<br />**Número**:<br />-2147213981|No se puede deshabilitar la unidad de negocio raíz.|
> |**Nombre**:<br />RouterIsDisabled<br />**Hex**:<br />8005E246<br />**Número**:<br />-2147098042|Microsoft Dynamics 365 se ha configurado para utilizar sincronización del lado del servidor para procesar el correo electrónico. Este error ocurre porque algunos clientes aún están configurados para usar el antiguo E-mail Router. Debe desinstalar la aplicación cliente E-mail Router en cualquier servidor en que esté instalada.|
> |**Nombre**:<br />RouteTypeUnsupported<br />**Hex**:<br />800404e9<br />**Número**:<br />-2147220247|No se admite el tipo de ruta|
> |**Nombre**:<br />RoutingNotAllowed<br />**Hex**:<br />800404e7<br />**Número**:<br />-2147220249|No se puede enrutar este tipo de objeto.|
> |**Nombre**:<br />RoutingRuleActivateDeactivateByNonOwner<br />**Hex**:<br />8004F885<br />**Número**:<br />-2147157883|Solo el propietario puede activar o desactivar este conjunto de reglas de enrutamiento.|
> |**Nombre**:<br />RoutingRuleMissingRuleCriteria<br />**Hex**:<br />8004F877<br />**Número**:<br />-2147157897|No puede activar esta regla hasta que no resuelva la información que falta de criterios de regla en los elementos de regla.|
> |**Nombre**:<br />RoutingRulePublishedByNonOwner<br />**Hex**:<br />8004F878<br />**Número**:<br />-2147157896|El propietario no puede publicar ni dejar sin anular la publicación de este conjunto de reglas de enrutamiento.|
> |**Nombre**:<br />RoutingRulePublishedByOwner<br />**Hex**:<br />8004F876<br />**Número**:<br />-2147157898|No se puede activar la regla hasta que la regla activa actual esté desactivada. Solo se puede desactivar la regla activa por el propietario de la regla.|
> |**Nombre**:<br />RowGuidIsNotValidName<br />**Hex**:<br />80047001<br />**Número**:<br />-2147192831|rowguid es un nombre reservado y no se puede usar como identificador|
> |**Nombre**:<br />RSCancelBatchError<br />**Hex**:<br />8004831c<br />**Número**:<br />-2147187940|Error al cancelar la operación en masa. |
> |**Nombre**:<br />RSCreateBatchError<br />**Hex**:<br />80048320<br />**Número**:<br />-2147187936|Error al crear una operación en masa. |
> |**Nombre**:<br />RSDeleteItemError<br />**Hex**:<br />80048317<br />**Número**:<br />-2147187945|Error al eliminar un elemento del report server.|
> |**Nombre**:<br />RSExecuteBatchError<br />**Hex**:<br />8004831d<br />**Número**:<br />-2147187939|Error al realizar la operación en masa. |
> |**Nombre**:<br />RSFindItemsError<br />**Hex**:<br />80048318<br />**Número**:<br />-2147187944|Error al buscar el elemento en report server.|
> |**Nombre**:<br />RSGetDataSourceContentsError<br />**Hex**:<br />8004831a<br />**Número**:<br />-2147187942|Error al obtener los contenidos de origen de datos.|
> |**Nombre**:<br />RSGetItemDataSourcesError<br />**Hex**:<br />80048321<br />**Número**:<br />-2147187935|Error al capturar los orígenes de datos actuales.|
> |**Nombre**:<br />RSGetItemTypeError<br />**Hex**:<br />8004832b<br />**Número**:<br />-2147187925|Error al capturar el informe. |
> |**Nombre**:<br />RSGetReportHistoryLimitError<br />**Hex**:<br />8004831e<br />**Número**:<br />-2147187938|Error al capturar la cantidad de instantáneas almacenadas para el informe. |
> |**Nombre**:<br />RSGetReportParametersError<br />**Hex**:<br />80048323<br />**Número**:<br />-2147187933|Error al obtener los parámetros para el informe.|
> |**Nombre**:<br />RSListExtensionsError<br />**Hex**:<br />8004831b<br />**Número**:<br />-2147187941|Error al obtener la lista de extensiones de datos instalada en report server.|
> |**Nombre**:<br />RSListReportHistoryError<br />**Hex**:<br />8004831f<br />**Número**:<br />-2147187937|Error al capturar instantáneas del historial de informes.|
> |**Nombre**:<br />RSMoveItemError<br />**Hex**:<br />80048330<br />**Número**:<br />-2147187920|No se puede mover elemento de informe {0} a {1}|
> |**Nombre**:<br />RSReportParameterTypeMismatchError<br />**Hex**:<br />80048329<br />**Número**:<br />-2147187927|El tipo de parámetro del informe no es válido.|
> |**Nombre**:<br />RSSetDataSourceContentsError<br />**Hex**:<br />80048319<br />**Número**:<br />-2147187943|Error al configurar los contenidos de origen de datos. |
> |**Nombre**:<br />RSSetExecutionOptionsError<br />**Hex**:<br />80048325<br />**Número**:<br />-2147187931|Error al configurar las opciones de ejecución.|
> |**Nombre**:<br />RSSetItemDataSourcesError<br />**Hex**:<br />80048322<br />**Número**:<br />-2147187934|Error al configurar el origen de datos.|
> |**Nombre**:<br />RSSetPropertiesError<br />**Hex**:<br />8004832a<br />**Número**:<br />-2147187926|Error al configurar los valores de las propiedades para el informe. |
> |**Nombre**:<br />RSSetReportHistoryLimitError<br />**Hex**:<br />80048327<br />**Número**:<br />-2147187929|Error al configurar el límite de las instantáneas del historial del informe.|
> |**Nombre**:<br />RSSetReportHistoryOptionsError<br />**Hex**:<br />80048326<br />**Número**:<br />-2147187930|Error al configurar las opciones de las instantáneas para el historial del informe.|
> |**Nombre**:<br />RSSetReportParametersError<br />**Hex**:<br />80048324<br />**Número**:<br />-2147187932|Error al configurar los parámetros para el informe.|
> |**Nombre**:<br />RSUpdateReportExecutionSnapshotError<br />**Hex**:<br />80048328<br />**Número**:<br />-2147187928|Error al tomar una instantánea de un informe.|
> |**Nombre**:<br />RuleActivationNotAllowedWithDeletedStages<br />**Hex**:<br />80060014<br />**Número**:<br />-2147090412|No puede activar esta regla porque contiene una fase eliminada o una categoría de fase. Solucione la regla e inténtelo de nuevo.|
> |**Nombre**:<br />RuleAlreadyExistsWithSameQueueAndChannel<br />**Hex**:<br />8004F884<br />**Número**:<br />-2147157884|La regla de creación de registro ya existe para el canal especificado y la cola. No puede crear otra.|
> |**Nombre**:<br />RuleAlreadyInactiveState<br />**Hex**:<br />8004F852<br />**Número**:<br />-2147157934|La regla de enrutamiento ya tiene el estado activo.|
> |**Nombre**:<br />RuleAlreadyInDraftState<br />**Hex**:<br />8004F853<br />**Número**:<br />-2147157933|No se puede desactivar un borrador de regla de enrutamiento.|
> |**Nombre**:<br />RuleAlreadyPublishing<br />**Hex**:<br />80048434<br />**Número**:<br />-2147187660|La regla de detección de duplicados seleccionada ya se está publicando.|
> |**Nombre**:<br />RuleCreationNotAllowedForCyclicReferences<br />**Hex**:<br />80060012<br />**Número**:<br />-2147090414|No puede crear esta regla porque contiene una referencia cíclica. Solucione la regla e inténtelo de nuevo.|
> |**Nombre**:<br />RuleNotFound<br />**Hex**:<br />80048433<br />**Número**:<br />-2147187661|No se encontraron reglas que coincidan con los criterios.|
> |**Nombre**:<br />RuleNotSupportedForEditor<br />**Hex**:<br />80060007<br />**Número**:<br />-2147090425|La definición de la regla actual no se puede editar en el editor de reglas de negocio.|
> |**Nombre**:<br />RulesInInconsistentStateFound<br />**Hex**:<br />80048423<br />**Número**:<br />-2147187677|Una o varias reglas no pueden ser no publicadas, porque están en proceso de publicación o están en un estado donde no pueden ser no publicados.|
> |**Nombre**:<br />RuntimeRibbonXmlValidation<br />**Hex**:<br />8004F671<br />**Número**:<br />-2147158415|No se puede generar la cinta de opciones personalizada más reciente para la pestaña en esta página. En su lugar se muestra la versión predefinida de la cinta de opciones.|
> |**Nombre**:<br />S2SAccessTokenCannotBeAcquired<br />**Hex**:<br />8005E243<br />**Número**:<br />-2147098045|No se puede adquirir el token de acceso S2S del servidor de autorización.|
> |**Nombre**:<br />S2SNotConfigured<br />**Hex**:<br />80044259<br />**Número**:<br />-2147204519|La integración de Office Graph usa en la integración de SharePoint basada en servidor. Para usar esta característica, habilite integración basada en servidor y tenga al menos un sitio de SharePoint activo.|
> |**Nombre**:<br />SalesOrderAndInvoiceCurrencyNotEqual<br />**Hex**:<br />80048ced<br />**Número**:<br />-2147185427|La divisa del registro no coincide con la divisa de la lista de precios.|
> |**Nombre**:<br />SalesPeopleDuplicateCalendarNotAllowed<br />**Hex**:<br />80043803<br />**Número**:<br />-2147207165|Ya exiten calendarios fiscales para este comercial/año|
> |**Nombre**:<br />SalesPeopleEmptyEffectiveDate<br />**Hex**:<br />80043801<br />**Número**:<br />-2147207167|La fecha de vigencia fiscal en vigor no puede estar vacía|
> |**Nombre**:<br />SalesPeopleEmptySalesPerson<br />**Hex**:<br />80043800<br />**Número**:<br />-2147207168|El comercial primario no puede estar vacío|
> |**Nombre**:<br />SalesPeopleManagerNotAllowed<br />**Hex**:<br />80043805<br />**Número**:<br />-2147207163|El administrador de la zona de ventas no puede pertenecer a otra zona de ventas|
> |**Nombre**:<br />SameSolutionCircularDependenciesIdentified<br />**Hex**:<br />80072007<br />**Número**:<br />-2147016697|Se identificaron dependencias circulares para esta solución.|
> |**Nombre**:<br />SandboxClientPluginTimeout<br />**Hex**:<br />80044171<br />**Número**:<br />-2147204751|La ejecución complemento da error porque la operación ha superado el tiempo de espera en el cliente de espacio aislado.|
> |**Nombre**:<br />SandboxHostNotAvailable<br />**Hex**:<br />8004418e<br />**Número**:<br />-2147204722|La ejecución del complemento da error porque no está disponible ahora ningún host de espacio aislado. Compruebe que tiene un servidor en espacio aislado configurado y que se está ejecutando.|
> |**Nombre**:<br />SandboxHostPluginTimeout<br />**Hex**:<br />80044172<br />**Número**:<br />-2147204750|La ejecución complemento da error porque la operación ha superado el tiempo de espera en el host de espacio aislado.|
> |**Nombre**:<br />SandboxPluginDisabled<br />**Hex**:<br />80081115<br />**Número**:<br />-2146954987|La ejecución de complemento de espacio aislado está deshabilitada.|
> |**Nombre**:<br />SandboxSdkListenerStartFailed<br />**Hex**:<br />80044174<br />**Número**:<br />-2147204748|La ejecución complemento da error porque se ha producido un error en el cliente de espacio aislado durante la inicialización.|
> |**Nombre**:<br />SandboxWorkerNotAvailable<br />**Hex**:<br />8004418d<br />**Número**:<br />-2147204723|La ejecución del complemento da error porque no está disponible ahora ningún proceso de trabajo de espacio aislado. Inténtelo de nuevo.|
> |**Nombre**:<br />SandboxWorkerPluginExecuteTimeout<br />**Hex**:<br />80081111<br />**Número**:<br />-2146954991|No se recibió una respuesta del complemento {0} dentro del límite de 2:20 minutos.|
> |**Nombre**:<br />SandboxWorkerPluginTimeout<br />**Hex**:<br />80044173<br />**Número**:<br />-2147204749|La ejecución complemento da error porque la operación ha superado el tiempo de espera en el trabajo de espacio aislado.|
> |**Nombre**:<br />SandboxWorkerThrottleLimit<br />**Hex**:<br />80081116<br />**Número**:<br />-2146954986|Se superaron los procesos máximos asignados para lógica de negocios de complementos. Se han producido errores irrecuperables en complementos para este entorno {0} veces en los últimos {1} minutos. Cada error requiere un proceso adicional para recuperar. Los procesos de los complementos se están reciclando. Todos los complementos para este entorno fallarán durante este período. Más información: https://go.microsoft.com/fwlink/?linkid=2038718 |
> |**Nombre**:<br />SaveAsDraftAppointmentNotAllowed<br />**Hex**:<br />8004026b<br />**Número**:<br />-2147220885|Se desactivado AllowSaveAsDraftAppointment.|
> |**Nombre**:<br />SaveDataFileErrorOutOfSpace<br />**Hex**:<br />8005F209<br />**Número**:<br />-2147094007|Vuelva a intentarlo. Si el problema persiste, busque alguna solución en {0} o póngase en contacto con el administrador de {#Brand_CRM} de su organización. Finalmente, puede contactar {1}.|
> |**Nombre**:<br />SavedQueryIsNotCustomizable<br />**Hex**:<br />80047017<br />**Número**:<br />-2147192809|La vista especificada no se puede personalizar|
> |**Nombre**:<br />SavedQueryValidationError<br />**Hex**:<br />800609A0<br />**Número**:<br />-2147087968|No puede publicar el perfil {0} porque uno de sus elementos de perfil {1} tiene una entidad {2} en la consulta guardada {3} que no forma parte de este perfil.|
> |**Nombre**:<br />SavePending<br />**Hex**:<br />80060913<br />**Número**:<br />-2147088109|La operación de guardar ya se está ejecutando en segundo plano.|
> |**Nombre**:<br />SaveRecordBeforeAddingBundle<br />**Hex**:<br />8004F983<br />**Número**:<br />-2147157629|Tras seleccionar una lista de precios, deberá guardar el registro para poder agregar una agrupación con productos opcionales.|
> |**Nombre**:<br />ScaleGroupDisabled<br />**Hex**:<br />8004A107<br />**Número**:<br />-2147180281|El scalegroup especificado está deshabilitado. No se admite acceso a organizaciones en este scalegroup.|
> |**Nombre**:<br />SchedulingFailedForBookingValidation<br />**Hex**:<br />80060915<br />**Número**:<br />-2147088107|La operación de reserva o reprogramación da error debido a una validación reserva.|
> |**Nombre**:<br />SchedulingFailedForInvalidData<br />**Hex**:<br />80060914<br />**Número**:<br />-2147088108|La operación de reserva o reprogramación da error debido a datos no válidos.|
> |**Nombre**:<br />SchemaNameContainsNonAlphaNumericCharacters<br />**Hex**:<br />80044364<br />**Número**:<br />-2147204252|El identificador {0} para el tipo {2} solo puede contener caracteres alfanuméricos y de subrayado.|
> |**Nombre**:<br />SchemaNameisNotUnique<br />**Hex**:<br />80044363<br />**Número**:<br />-2147204253|El nombre de esquema {0} para el tipo {1} no es único. Ya existe un {0} con el mismo nombre.|
> |**Nombre**:<br />SchemaNameLengthExceedsLimit<br />**Hex**:<br />80044367<br />**Número**:<br />-2147204249|Los identificadores no pueden tener más de {1} caracteres. La longitud del nombre de esquema proporcionada {0} para el tipo {2} es mayor que la longitud máxima de {1} caracteres.|
> |**Nombre**:<br />SchemaNameMatchesExistingIdentifier<br />**Hex**:<br />80044361<br />**Número**:<br />-2147204255|Los identificadores no pueden coincidir con los nombres de objeto existentes. Ya existe un objeto de tipo {1} con el mismo nombre {0}.|
> |**Nombre**:<br />SchemaNameMatchesReservedSqlKeywords<br />**Hex**:<br />80044362<br />**Número**:<br />-2147204254|Los identificadores no pueden coincidir con palabras clave SQL reservadas. El nombre proporcionado: {0} para el tipo {1} coincide con la palabra clave:{2}|
> |**Nombre**:<br />SchemaNameNotStartwithLetter<br />**Hex**:<br />80044365<br />**Número**:<br />-2147204251|Los identificadores debe empezar por una letra. El nombre de esquema {0} del tipo {2} no empieza con una letra.|
> |**Nombre**:<br />ScopeNotSetToGlobal<br />**Hex**:<br />80060403<br />**Número**:<br />-2147089405|Se debe definir el ámbito en Global al crear la categoría de flujo de proceso de negocio|
> |**Nombre**:<br />SdkCorrelationTokenDepthTooHigh<br />**Hex**:<br />80044182<br />**Número**:<br />-2147204734|Esta tarea de flujo de trabajo se ha cancelado porque el flujo de trabajo que había iniciado incluía un bucle infinito. Corrija la lógica del flujo de trabajo e inténtelo de nuevo. Para obtener información sobre la lógica de flujo de trabajo, consulte la Ayuda.|
> |**Nombre**:<br />SdkCustomProcessingStepIsNotAllowed<br />**Hex**:<br />80044187<br />**Número**:<br />-2147204729|No se permite la SdkMessageProcessingStep personalizada en el mensaje especificado y entidad.|
> |**Nombre**:<br />SdkEntityDoesNotSupportMessage<br />**Hex**:<br />80040800<br />**Número**:<br />-2147219456|El método que se está invocando no admite el tipo de entidad proporcionado.|
> |**Nombre**:<br />SdkEntityOfflineQueuePlaybackIsNotAllowed<br />**Hex**:<br />80044188<br />**Número**:<br />-2147204728|La entidad '{0}' no se admite en reproducción de cola sin conexión.|
> |**Nombre**:<br />SdkInvalidMessagePropertyName<br />**Hex**:<br />8004416b<br />**Número**:<br />-2147204757|El nombre de la propiedad del mensaje '{0}' no es válido en el mensaje {1}.|
> |**Nombre**:<br />SdkMessageDoesNotSupportImageRegistration<br />**Hex**:<br />80044189<br />**Número**:<br />-2147204727|Mensaje '{0}' no admite registro de imágenes.|
> |**Nombre**:<br />SdkMessageDoesNotSupportPostImageRegistration<br />**Hex**:<br />8004416e<br />**Número**:<br />-2147204754|Registro de paso preEvent no admite la imagen posterior.|
> |**Nombre**:<br />SdkMessageInvalidImageTypeRegistration<br />**Hex**:<br />8004416d<br />**Número**:<br />-2147204755|Mensaje {0} no admite este tipo de imágenes.|
> |**Nombre**:<br />SdkMessageNotImplemented<br />**Hex**:<br />80044824<br />**Número**:<br />-2147203036|Mensaje de SDK no implementado.|
> |**Nombre**:<br />SdkMessageNotSupportedOnClient<br />**Hex**:<br />80044181<br />**Número**:<br />-2147204735|El mensaje solicitado no se admite en el cliente.|
> |**Nombre**:<br />SdkMessageNotSupportedOnServer<br />**Hex**:<br />80044180<br />**Número**:<br />-2147204736|El mensaje solicitado no se admite en el servidor.|
> |**Nombre**:<br />SdkMessagesDeprecatedError<br />**Hex**:<br />8004F903<br />**Número**:<br />-2147157757|Este mensaje ya no está disponible. Consulte el SDK para mensajes alternativos.|
> |**Nombre**:<br />SdkNotEnoughPrivilegeToSetCallerOriginToken<br />**Hex**:<br />80044309<br />**Número**:<br />-2147204343|Llamador no tiene privilegios suficientes para establecer CallerOriginToken con el valor especificado.|
> |**Nombre**:<br />SearchTextLenExceeded<br />**Hex**:<br />800401ff<br />**Número**:<br />-2147220993|Se ha superado la longitud de texto de búsqueda.|
> |**Nombre**:<br />SelectedFileNotFound<br />**Hex**:<br />80071025<br />**Número**:<br />-2147020763|No se pueden copiar los documentos. Ya no existe el archivo de origen.|
> |**Nombre**:<br />SeriesMeasureCollectionMismatch<br />**Hex**:<br />8004E003<br />**Número**:<br />-2147164157|El número de serie para el área del gráfico y el número de colecciones de medida de categoría deben ser iguales.|
> |**Nombre**:<br />ServerLocationAndSSLSetToYes<br />**Hex**:<br />8005E255<br />**Número**:<br />-2147098027|La dirección URL especificada para la ubicación del servidor usa HTTP, pero se requiere la Capa de sockets seguros (SSL) para Exchange Online.|
> |**Nombre**:<br />ServerLocationIsEmpty<br />**Hex**:<br />8005E250<br />**Número**:<br />-2147098032|El campo de ubicación del servidor no puede estar vacío|
> |**Nombre**:<br />ServiceAccountMailboxesCountIsGreaterThanOne<br />**Hex**:<br />8005E24A<br />**Número**:<br />-2147098038|Más buzones de la cuenta de servicio están asociados al perfil de emailserver|
> |**Nombre**:<br />ServiceAccountMailboxesCountIsZero<br />**Hex**:<br />8005E249<br />**Número**:<br />-2147098039|No hay buzones de la cuenta de servicio asociados al perfil de servidor de correo electrónico.|
> |**Nombre**:<br />ServiceBusEndpointNotConfigured<br />**Hex**:<br />80081112<br />**Número**:<br />-2146954990|La configuración de las credenciales necesarias debe completarse para que se pueden enviar mensajes.|
> |**Nombre**:<br />ServiceBusExtendedTokenFailed<br />**Hex**:<br />80044178<br />**Número**:<br />-2147204744|Error al recuperar el token adicional para la publicación de service bus.|
> |**Nombre**:<br />ServiceBusIssuerCertificateError<br />**Hex**:<br />80044177<br />**Número**:<br />-2147204745|Error de certificado del emisor de integración del servicio.|
> |**Nombre**:<br />ServiceBusIssuerNotFound<br />**Hex**:<br />80044176<br />**Número**:<br />-2147204746|No se encontró la información del emisor de integración de servicio.|
> |**Nombre**:<br />ServiceBusMaxSizeExceeded<br />**Hex**:<br />80050208<br />**Número**:<br />-2147155448|La llamada de bus de servicio ha fallado porque la carga de la solicitud ha excedido el tamaño permitido máximo. Reduzca el tamaño de la solicitud y vuelva a intentarlo.|
> |**Nombre**:<br />ServiceBusPostDisabled<br />**Hex**:<br />8004417A<br />**Número**:<br />-2147204742|La publicación de bus de servicio está deshabilitada para la organización.|
> |**Nombre**:<br />ServiceBusPostFailed<br />**Hex**:<br />80044175<br />**Número**:<br />-2147204747|Fallo al publicar el bus de servicio.|
> |**Nombre**:<br />ServiceBusPostPostponed<br />**Hex**:<br />80044179<br />**Número**:<br />-2147204743|La publicación de bus de servicio se está posponiendo.|
> |**Nombre**:<br />ServiceEndpointAcsAuthNotSupported<br />**Hex**:<br />80050209<br />**Número**:<br />-2147155447|La extremo de servicio con tipo de autenticación ACS ya no se admite. Cambie la configuración del extremo para usar un tipo de autenticación admitido|
> |**Nombre**:<br />ServiceInstantiationFailed<br />**Hex**:<br />80040244<br />**Número**:<br />-2147220924|No se pudo crear una instancia de una entidad.|
> |**Nombre**:<br />SessionTokenUnavailable<br />**Hex**:<br />80040253<br />**Número**:<br />-2147220909|El token de sesión no está disponible, a menos que hay una transacción existente.|
> |**Nombre**:<br />SetActiveNotSupportedOnNewRecords<br />**Hex**:<br />80060374<br />**Número**:<br />-2147089548|SetActiveProcess no se admite en registros nuevos.|
> |**Nombre**:<br />SharePointAbsoluteAndRelativeUrlEmpty<br />**Hex**:<br />80048149<br />**Número**:<br />-2147188407|La dirección URL absoluta y la relativa no pueden ser null.|
> |**Nombre**:<br />SharePointAuthenticationFailure<br />**Hex**:<br />800608B3<br />**Número**:<br />-2147088205|Microsoft Dynamics 365 no puede autenticar este usuario {0}. Compruebe que la información para este usuario es correcta e inténtelo de nuevo.|
> |**Nombre**:<br />SharePointAuthorizationFailure<br />**Hex**:<br />800608B4<br />**Número**:<br />-2147088204|Microsoft Dynamics 365 no puede autorizar este usuario {0}. Compruebe que la información para este usuario es correcta e inténtelo de nuevo.|
> |**Nombre**:<br />SharePointCertificateExpired<br />**Hex**:<br />800608B1<br />**Número**:<br />-2147088207|El certificado usado para validación de Sharepoint ha expirado|
> |**Nombre**:<br />SharePointConnectionFailure<br />**Hex**:<br />800608B5<br />**Número**:<br />-2147088203|Microsoft Dynamics 365 no puede conectar este usuario {0} con SharePoint. Compruebe que la información para este usuario es correcta y existe en SharePoint e inténtelo de nuevo.|
> |**Nombre**:<br />SharePointCrmDomainValidator<br />**Hex**:<br />8004F302<br />**Número**:<br />-2147159294|SharePoint y Microsoft Dynamics 365 Server se encuentran en dominios diferentes. Asegúre una relación de confianza entre los dos dominios.|
> |**Nombre**:<br />SharePointCrmGridIsInstalledValidator<br />**Hex**:<br />8004F309<br />**Número**:<br />-2147159287|Se debe instalar el componente de cuadrícula de Microsoft Dynamics 365 en el SharePoint server. Este componente es necesario para que la integración de SharePoint funcione correctamente.|
> |**Nombre**:<br />SharePointErrorAbsoluteUrlClipped<br />**Hex**:<br />8004F314<br />**Número**:<br />-2147159276|La URL supera el número máximo de 256 caracteres. Utilice nombres más cortos para los sitios y carpetas e inténtelo de nuevo.|
> |**Nombre**:<br />SharePointErrorRetrieveAbsoluteUrl<br />**Hex**:<br />8004F310<br />**Número**:<br />-2147159280|Se ha producido un error al recuperar la dirección url absoluta y de colección de sitios para un objeto de SharePoint.|
> |**Nombre**:<br />SharePointInvalidEntityForValidation<br />**Hex**:<br />8004F311<br />**Número**:<br />-2147159279|La entidad no admite validación de dirección Url de SharePoint.|
> |**Nombre**:<br />SharePointRealmMismatch<br />**Hex**:<br />800608B2<br />**Número**:<br />-2147088206|El id. de dominio de SharePoint especificado no coincide con el dominio registrado en Sharepoint.|
> |**Nombre**:<br />SharePointRecordWithDuplicateUrl<br />**Hex**:<br />80048057<br />**Número**:<br />-2147188649|Ya hay un registro con la misma dirección Url.|
> |**Nombre**:<br />SharePointRoleProvisionJobAlreadyExists<br />**Hex**:<br />8004F0FA<br />**Número**:<br />-2147159814|Un trabajo del sistema para proporcionar el rol de seguridad seleccionado está pendiente. Los cambios realizados en el registro del rol de seguridad antes de que inicie el trabajo del sistema se aplicarán a este trabajo del sistema.|
> |**Nombre**:<br />SharePointS2SIsDisabled<br />**Hex**:<br />80071017<br />**Número**:<br />-2147020777|La integración de SharePoint basada en servidor de SharePoint no está habilitada.|
> |**Nombre**:<br />SharePointServerDiscoveryValidator<br />**Hex**:<br />8004F303<br />**Número**:<br />-2147159293|La dirección URL es incorrecta o el sitio no está en ejecución.|
> |**Nombre**:<br />SharePointServerLanguageValidator<br />**Hex**:<br />8004F308<br />**Número**:<br />-2147159288|Microsoft Dynamics 365 y Microsoft Office SharePoint Server deben tener el mismo idioma base.|
> |**Nombre**:<br />SharePointServerVersionValidator<br />**Hex**:<br />8004F304<br />**Número**:<br />-2147159292|La colección de sitios SharePoint debe estar ejecutándose en una versión compatible de Microsoft Office SharePoint Server o Microsoft Windows SharePoint Services. Consulte a la Guía de implementación.|
> |**Nombre**:<br />SharePointSiteCollectionIsAccessibleValidator<br />**Hex**:<br />8004F305<br />**Número**:<br />-2147159291|La dirección URL es incorrecta o el sitio no está en ejecución.|
> |**Nombre**:<br />SharePointSiteCreationFailure<br />**Hex**:<br />8004F0F8<br />**Número**:<br />-2147159816|No se puede crear el sitio {0} en SharePoint.|
> |**Nombre**:<br />SharePointSiteNotConfigured<br />**Hex**:<br />80071014<br />**Número**:<br />-2147020780|SharePointSite no está configurado; es necesario configurarlo.|
> |**Nombre**:<br />SharePointSiteNotPresentInSharePoint<br />**Hex**:<br />8004F0F3<br />**Número**:<br />-2147159821|El sitio {0} no existe en SharePoint.|
> |**Nombre**:<br />SharePointSitePermissionsValidator<br />**Hex**:<br />8004F307<br />**Número**:<br />-2147159289|El usuario actual no tiene los privilegios adecuados. Debe ser administrador del sitio de SharePoint en el sitio de SharePoint.|
> |**Nombre**:<br />SharePointSiteWideProvisioningJobFailed<br />**Hex**:<br />8004F0FB<br />**Número**:<br />-2147159813|Fallo en el trabajo de aprovisionamiento de SharePoint.|
> |**Nombre**:<br />SharePointTeamProvisionJobAlreadyExists<br />**Hex**:<br />8004F0F9<br />**Número**:<br />-2147159815|Un trabajo del sistema para proporcionar el equipo seleccionado está pendiente. Los cambios realizados en el registro del equipo antes de que inicie el trabajo del sistema se aplicarán a este trabajo del sistema.|
> |**Nombre**:<br />SharePointUnableToAclSite<br />**Hex**:<br />8004F0F6<br />**Número**:<br />-2147159818|Imposible sitio ACL {0} en SharePoint.|
> |**Nombre**:<br />SharePointUnableToAclSiteWithPrivilege<br />**Hex**:<br />8004F0F5<br />**Número**:<br />-2147159819|Imposible sitio ACL {0} con el privilegio {1} en SharePoint.|
> |**Nombre**:<br />SharePointUnableToAddUserToGroup<br />**Hex**:<br />8004F0F1<br />**Número**:<br />-2147159823|Microsoft Dynamics 365 no puede agregar este usuario {0} al grupo de {1} en SharePoint. Compruebe que la información para este usuario o grupo es correcta y que el grupo existe en SharePoint e inténtelo de nuevo.|
> |**Nombre**:<br />SharePointUnableToCreateSiteGroup<br />**Hex**:<br />8004F0F7<br />**Número**:<br />-2147159817|No se puede crear el grupo de sitios {0} en SharePoint.|
> |**Nombre**:<br />SharePointUnableToRemoveUserFromGroup<br />**Hex**:<br />8004F0F2<br />**Número**:<br />-2147159822|No se puede quitar el usuario {0} del grupo {1} en SharePoint.|
> |**Nombre**:<br />SharePointUnableToRetrieveGroup<br />**Hex**:<br />8004F0F4<br />**Número**:<br />-2147159820|No se puede recuperar el grupo {0} de SharePoint.|
> |**Nombre**:<br />SharePointUrlHostValidator<br />**Hex**:<br />8004F301<br />**Número**:<br />-2147159295|No se puede resolver la dirección URL en una dirección IP.|
> |**Nombre**:<br />SharePointUrlIsRootWebValidator<br />**Hex**:<br />8004F306<br />**Número**:<br />-2147159290|La URL no es válida. La dirección URL debe ser una colección de sitios válidos y no puede incluir un subsitio. La dirección URL debe tener una forma válida, como http://SharePointServer/sites/CrmSite.|
> |**Nombre**:<br />SharePointVersionUnsupported<br />**Hex**:<br />800608B6<br />**Número**:<br />-2147088202|Microsoft Dynamics 365 no puede conectarse a Sharepoint porque la versión Sharepoint no está admitida. Instale la versión correcta y, después, inténtelo de nuevo. |
> |**Nombre**:<br />SimilarityRuleDisabled<br />**Hex**:<br />80071016<br />**Número**:<br />-2147020778|No hay ninguna regla de similitud activa para esta entidad.|
> |**Nombre**:<br />SimilarityRuleFCBOff<br />**Hex**:<br />80071018<br />**Número**:<br />-2147020776|Las reglas de similitud no están habilitadas.|
> |**Nombre**:<br />SingletonMappingFoundForArrayParameter<br />**Hex**:<br />8004037e<br />**Número**:<br />-2147220610|La asignación de parámetros de una sola transformación se define para un parámetro de la matriz.|
> |**Nombre**:<br />SiteMapMissing<br />**Hex**:<br />80050016<br />**Número**:<br />-2147155946|No tiene permisos para estos registros o hay algún problema con el mapa del sitio. Contacte con el adminstrador del sistema. Si es usted el administrador, puede ir a la página de soluciones e importar otra solución.|
> |**Nombre**:<br />SiteMapXsdValidationError<br />**Hex**:<br />8004F401<br />**Número**:<br />-2147159039|El xml del mapa del sitio no ha superado la validación XSD con el siguiente error: "{0}" en línea {1} posición {2}.|
> |**Nombre**:<br />SkipValidDateTimeBehavior<br />**Hex**:<br />800608A3<br />**Número**:<br />-2147088221|El valor de comportamiento de este campo se ha ignorado. Un personalizador del sistema tendrá que configurar el valor de comportamiento para este campo directamente.|
> |**Nombre**:<br />SlaActivateDeactivateByNonOwner<br />**Hex**:<br />8004F872<br />**Número**:<br />-2147157902|Esta SLA la puede activar o desactivar sólo su propietario.|
> |**Nombre**:<br />SlaAlreadyInactiveState<br />**Hex**:<br />8004F861<br />**Número**:<br />-2147157919|No puede activar este registro porque ya está activo.|
> |**Nombre**:<br />SlaAlreadyInDraftState<br />**Hex**:<br />8004F862<br />**Número**:<br />-2147157918|No puede desactivar este registro porque no está en un estado de borrador.|
> |**Nombre**:<br />SlaNotEnabledEntity<br />**Hex**:<br />80055003<br />**Número**:<br />-2147135485|No se ha habilitado el SLA para esta entidad.|
> |**Nombre**:<br />SlaPermissionToPerformAction<br />**Hex**:<br />8004F875<br />**Número**:<br />-2147157899|No tiene los permisos necesarios sobre los SLA y los procesos para realizar esta acción.|
> |**Nombre**:<br />SnapshotReportNotReady<br />**Hex**:<br />80040489<br />**Número**:<br />-2147220343|El informe seleccionado no está listo para ver. El informe se sigue creando o no está disponible ninguna instantánea del informe. ReportId:{0}|
> |**Nombre**:<br />SocialCareDisabledError<br />**Hex**:<br />80060621<br />**Número**:<br />-2147088863|Hay un problema en la comunicación con la organización Dynamics 365. Puede ser la organización no está disponible o qie la característica esté establecida de forma que no puede recibir datos sociales. Vuelva a intentarlo más tarde. Si el problema persiste, póngase en contacto con el administrador de Microsoft Dynamics 365.|
> |**Nombre**:<br />SolutionComponentDefinitionNotAvailable<br />**Hex**:<br />8007200A<br />**Número**:<br />-2147016694|No se puede crear la definición de componente para la entidad que reconoce la solución {0}.|
> |**Nombre**:<br />SolutionConcurrencyFailure<br />**Hex**:<br />80071151<br />**Número**:<br />-2147020463|La instalación o la desinstalación de la solución no se ha podido realizar porque se estaba instalando o desinstalando otra solución al mismo tiempo. Inténtelo de nuevo más tarde.|
> |**Nombre**:<br />SolutionConfigurationPageMustBeHtmlWebResource<br />**Hex**:<br />8004701C<br />**Número**:<br />-2147192804|La página de configuración de la solución debe existir dentro de la solución que representa.|
> |**Nombre**:<br />SolutionImportCauseTimeout<br />**Hex**:<br />80048543<br />**Número**:<br />-2147187389|La operación agotó el tiempo de espera. Esto puede ser debido a que una solución se está importando actualmente en este entorno. Vuelva a intentarlo una vez finalizada la importación de la solución. Las soluciones se deberían importar fuera del horario laboral si es posible.|
> |**Nombre**:<br />SolutionRestrictedAttributes<br />**Hex**:<br />80072003<br />**Número**:<br />-2147016701|El componente no se pueden crear porque ya tiene columnas compatibles con soluciones. Entidad: {0}, atributo existente: {1}|
> |**Nombre**:<br />SolutionUniqueNameViolation<br />**Hex**:<br />8004F023<br />**Número**:<br />-2147160029|El nombre único de la solución '{0}' ya se está usando y no se puede usar de nuevo.|
> |**Nombre**:<br />SolutionUpgradeFailed<br />**Hex**:<br />8004F046<br />**Número**:<br />-2147159994|La acción de la actualización de solución falló después de importar como retenida. InnerException es: {1}.|
> |**Nombre**:<br />SolutionUpgradeNotAvailable<br />**Hex**:<br />8004853B<br />**Número**:<br />-2147187397|"La solución {0} no dispone de ninguna actualización lista para aplicarse".|
> |**Nombre**:<br />SolutionUpgradeOfApiManagedSolutionError<br />**Hex**:<br />8004803C<br />**Número**:<br />-2147188676|La importación ha fallado porque una solución ApiManaged no se puede actualizar.|
> |**Nombre**:<br />SolutionUpgradeWrongSolutionSelected<br />**Hex**:<br />8004853C<br />**Número**:<br />-2147187396|"Para usar esta acción, primero deberá seleccionar la solución anterior y, a continuación, intentarlo de nuevo."|
> |**Nombre**:<br />SourceAttributeHeaderTooBig<br />**Hex**:<br />80044340<br />**Número**:<br />-2147204288|Encabezados de columna deben tener 160 o menos caracteres. Solucione los encabezados de columna y, después, vuelva a ejecutar el administrador de migración de datos.|
> |**Nombre**:<br />SourceEntityMappedToMultipleTargets<br />**Hex**:<br />8004033d<br />**Número**:<br />-2147220675|Esta entidad de origen está asignada a más de una entidad de Microsoft Dynamics 365. Quite las asignaciones duplicadas y, a continuación, vuelva a importar esta asignación de datos.|
> |**Nombre**:<br />SPAccountNameFetchFailure<br />**Hex**:<br />8006072A<br />**Número**:<br />-2147088598|Excepciones se producen durante la obtención de nombre de la cuenta de Sharepoint.|
> |**Nombre**:<br />SPAllFilesErrorScenario<br />**Hex**:<br />80060760<br />**Número**:<br />-2147088544|Uno o varios sitios en la vista de todos los archivos de SharePointDocument da error.|
> |**Nombre**:<br />SPBadLockInFileCollectionErrorCode<br />**Hex**:<br />8006070A<br />**Número**:<br />-2147088630|El archivo de la colección tiene un bloqueo incorrecto |
> |**Nombre**:<br />SPCertificationError<br />**Hex**:<br />80060767<br />**Número**:<br />-2147088537|No se encuentra el certificado S2STokenIssuer.|
> |**Nombre**:<br />SPConnectionFailure<br />**Hex**:<br />80060761<br />**Número**:<br />-2147088543|No se pudo establecer conexión con SharePointSite.|
> |**Nombre**:<br />SPCurrentDocumentLocationDisabledErrorCode<br />**Hex**:<br />80060720<br />**Número**:<br />-2147088608|La ubicación del documento actual está deshabilitada por el administrador|
> |**Nombre**:<br />SPCurrentFolderAlreadyExistErrorCode<br />**Hex**:<br />80060721<br />**Número**:<br />-2147088607|Registro ya presente en la base de datos|
> |**Nombre**:<br />SPDataValidationFiledOnFieldAndListErrorCode<br />**Hex**:<br />80060713<br />**Número**:<br />-2147088621|Error en la validación de datos del campo y la lista|
> |**Nombre**:<br />SPDataValidationFiledOnFieldErrorCode<br />**Hex**:<br />80060711<br />**Número**:<br />-2147088623|Error en la validación de datos del campo|
> |**Nombre**:<br />SPDataValidationFiledOnListErrorCode<br />**Hex**:<br />80060712<br />**Número**:<br />-2147088622|Error en la validación de datos de la lista|
> |**Nombre**:<br />SPDefaultSiteNotPresent<br />**Hex**:<br />80060739<br />**Número**:<br />-2147088583|La activación de OneDrive necesita de un sitio de SharePoint de forma predeterminada.|
> |**Nombre**:<br />SPDocumentMappingFailure<br />**Hex**:<br />80060734<br />**Número**:<br />-2147088588|No se pueden asignar documentos a su ubicación.|
> |**Nombre**:<br />SPDuplicateValuesFoundErrorCode<br />**Hex**:<br />80060708<br />**Número**:<br />-2147088632|No se pudo actualizar el elemento de lista porque se encontraron valores duplicados en uno o más campos de la lista|
> |**Nombre**:<br />SpecifyIncomingPassword<br />**Hex**:<br />8005E253<br />**Número**:<br />-2147098029|Especifique una contraseña para la conexión entrante|
> |**Nombre**:<br />SpecifyInComingPort<br />**Hex**:<br />8005E24F<br />**Número**:<br />-2147098033|Especifique el puerto entrante y vuelva a guardar|
> |**Nombre**:<br />SpecifyIncomingServerLocation<br />**Hex**:<br />8005E24B<br />**Número**:<br />-2147098037|Especifique la dirección URL de la ubicación de servidor entrante|
> |**Nombre**:<br />SpecifyIncomingUserName<br />**Hex**:<br />8005E251<br />**Número**:<br />-2147098031|Especifique un nombre de usuario para la conexión entrante|
> |**Nombre**:<br />SpecifyOutgoingPassword<br />**Hex**:<br />8005E254<br />**Número**:<br />-2147098028|Especifique una contraseña para la conexión saliente|
> |**Nombre**:<br />SpecifyOutgoingPort<br />**Hex**:<br />8005E256<br />**Número**:<br />-2147098026|Especifique el puerto saliente y vuelva a guardar|
> |**Nombre**:<br />SpecifyOutgoingServerLocation<br />**Hex**:<br />8005E24C<br />**Número**:<br />-2147098036|Especifique la dirección URL de la ubicación de servidor saliente.|
> |**Nombre**:<br />SpecifyOutgoingUserName<br />**Hex**:<br />8005E252<br />**Número**:<br />-2147098030|Especifique un nombre de usuario para la conexión saliente|
> |**Nombre**:<br />SPExclusiveLockOnFileErrorCode<br />**Hex**:<br />80060705<br />**Número**:<br />-2147088635|Bloqueo exclusivo en el archivo|
> |**Nombre**:<br />SPFileAlreadyCheckedOutErrorCode<br />**Hex**:<br />80060702<br />**Número**:<br />-2147088638|El archivo ya está desprotegido.|
> |**Nombre**:<br />SPFileCheckedOutInvalidArgsErrorCode<br />**Hex**:<br />80060703<br />**Número**:<br />-2147088637|Los argumentos de desprotección no son válidos|
> |**Nombre**:<br />SPFileContentNullErrorCode<br />**Hex**:<br />8006070D<br />**Número**:<br />-2147088627|El contenido de la información de creación del archivo no puede ser nulo|
> |**Nombre**:<br />SPFileIsCheckedOutByOtherUser<br />**Hex**:<br />80060728<br />**Número**:<br />-2147088600|El archivo está desprotegido para un usuario distinto del usuario actual|
> |**Nombre**:<br />SPFileIsReadOnlyErrorCode<br />**Hex**:<br />8006070F<br />**Número**:<br />-2147088625|El campo es de solo lectura|
> |**Nombre**:<br />SPFileNameModifiedErrorCode<br />**Hex**:<br />80060729<br />**Número**:<br />-2147088599|No se encuentra la carpeta. Si ha cambiado el nombre de carpeta generado automáticamente para esta ubicación de documento directamente en SharePoint, debe cambiar el nombre de la carpeta en Dynamics 365 para que coincida con la carpeta que ha cambiado de nombre. Para ello, seleccione Editar ubicación y escriba el nombre coincidente en el campo de nombre de la carpeta.|
> |**Nombre**:<br />SPFileNotCheckedOutErrorCode<br />**Hex**:<br />80060700<br />**Número**:<br />-2147088640|El archivo no está desprotegido|
> |**Nombre**:<br />SPFileNotFoundErrorCode<br />**Hex**:<br />80060706<br />**Número**:<br />-2147088634|No se encuentra el archivo|
> |**Nombre**:<br />SPFileNotLockedErrorCode<br />**Hex**:<br />80060707<br />**Número**:<br />-2147088633|El archivo de la colección no está bloqueado|
> |**Nombre**:<br />SPFileSizeMismatchErrorCode<br />**Hex**:<br />8006070E<br />**Número**:<br />-2147088626|El tamaño de la secuencia del documento escrita y el tamaño de la secuencia del documento de entrada no coinciden.|
> |**Nombre**:<br />SPFileTooLargeOrInfectedErrorCode<br />**Hex**:<br />80060709<br />**Número**:<br />-2147088631|La comprobación de virus indica que el archivo está infectado con un virus o que el archivo es demasiado grande|
> |**Nombre**:<br />SPFolderCreationFailure<br />**Hex**:<br />8004F0F0<br />**Número**:<br />-2147159824|No se puede crear carpeta con este nombre|
> |**Nombre**:<br />SPFolderNotFoundErrorCode<br />**Hex**:<br />8006071B<br />**Número**:<br />-2147088613|Carpeta no encontrada|
> |**Nombre**:<br />SPFolderRenameFailure<br />**Hex**:<br />8006072C<br />**Número**:<br />-2147088596|Excepciones durante la edición las propiedades de documentos en Sharepoint.|
> |**Nombre**:<br />SPGenericErrorCode<br />**Hex**:<br />80060719<br />**Número**:<br />-2147088615|Error al realizar esta operación en SharePoint|
> |**Nombre**:<br />SPIllegalCharactersInFileNameErrorCode<br />**Hex**:<br />8006071F<br />**Número**:<br />-2147088609|Caracteres no válidos en el nombre de archivo|
> |**Nombre**:<br />SPIllegalFileTypeErrorCode<br />**Hex**:<br />8006071D<br />**Número**:<br />-2147088611|Tipo de archivo no válido|
> |**Nombre**:<br />SPInstanceOfRecurringEventErrorCode<br />**Hex**:<br />80060716<br />**Número**:<br />-2147088618|El elemento de lista es una instancia de un evento periódico que no es una excepción de repetición, el elemento de lista es una tarea de flujo de trabajo cuyo flujo de trabajo principal se encuentra en la papelera de reciclaje, o la lista principal es una biblioteca de documentos|
> |**Nombre**:<br />SPIntermittentError<br />**Hex**:<br />80060764<br />**Número**:<br />-2147088540|Se ha producido un error intermitente. Actualice la cuadrícula y vuelva a intentarlo.|
> |**Nombre**:<br />SPInvalidDocumentLocation<br />**Hex**:<br />80060762<br />**Número**:<br />-2147088542|Tipo de ubicación de documento de Sharepoint no válido.|
> |**Nombre**:<br />SPInvalidFieldValueErrorCode<br />**Hex**:<br />8006071E<br />**Número**:<br />-2147088610|Valor de campo no válido|
> |**Nombre**:<br />SPInvalidLookupValuesErrorCode<br />**Hex**:<br />8006070B<br />**Número**:<br />-2147088629|No se pudo actualizar el elemento de lista porque se encontraron valores de búsqueda no válidos en uno o más campos de la lista|
> |**Nombre**:<br />SPInvalidSavedQueryErrorCode<br />**Hex**:<br />80060718<br />**Número**:<br />-2147088616|Error al realizar esta operación en SharePoint|
> |**Nombre**:<br />SPInvalidSubSite<br />**Hex**:<br />80060763<br />**Número**:<br />-2147088541|Dirección url de SubSite formada incorrectamente|
> |**Nombre**:<br />SPItemNotExistErrorCode<br />**Hex**:<br />80060717<br />**Número**:<br />-2147088617|El elemento de lista no existe|
> |**Nombre**:<br />SPMalFormedRelativeUrl<br />**Hex**:<br />80060766<br />**Número**:<br />-2147088538|La dirección URL relativa no debe tener espacios anteriores o finales.|
> |**Nombre**:<br />SPModifiedOnServerErrorCode<br />**Hex**:<br />80060710<br />**Número**:<br />-2147088624|El elemento de lista se ha modificado en el servidor, por lo que no se pueden confirmar los cambios|
> |**Nombre**:<br />SPMultipleOdbSitesError<br />**Hex**:<br />8006072D<br />**Número**:<br />-2147088595|No se permite más de un sitio con OneDrive habilitado.|
> |**Nombre**:<br />SPNoActiveDocumentLocationErrorCode<br />**Hex**:<br />8006071C<br />**Número**:<br />-2147088612|No hay ubicaciones de documentos activos|
> |**Nombre**:<br />SPNotAdminError<br />**Hex**:<br />80060765<br />**Número**:<br />-2147088539|Solo el administrador de crm que es administrador de inquilinos puede realizar la operación de creación|
> |**Nombre**:<br />SPNotEnabledError<br />**Hex**:<br />8006073A<br />**Número**:<br />-2147088582|La integración de SharePoint no está habilitada en Entidad|
> |**Nombre**:<br />SPNotEnabledForEntity<br />**Hex**:<br />8006073B<br />**Número**:<br />-2147088581|La integración de SharePoint y la integración de Microsoft Teams no está habilitada en Entidad|
> |**Nombre**:<br />SPNullFileUrlErrorCode<br />**Hex**:<br />8006070C<br />**Número**:<br />-2147088628|La dirección URL de la información de la creación del archivo no puede ser nula y debe ser válida|
> |**Nombre**:<br />SPNullRegardingObjectErrorCode<br />**Hex**:<br />80060723<br />**Número**:<br />-2147088605|Id. de objeto referente nulo|
> |**Nombre**:<br />SPOdbDisabledError<br />**Hex**:<br />8006072E<br />**Número**:<br />-2147088594|Habilite la característica ODB (OneDrive para la Empresa) para crear el sitio ODB.|
> |**Nombre**:<br />SPOdbDuplicateLocationError<br />**Hex**:<br />80060735<br />**Número**:<br />-2147088587|No se permite más de una ubicación ODB (OneDrive para la Empresa).|
> |**Nombre**:<br />SPOdbUpdateDeleteError<br />**Hex**:<br />8006072F<br />**Número**:<br />-2147088593|No puede actualizar ni eliminar el sitio ODB (OneDrive para la Empresa).|
> |**Nombre**:<br />SPOdbUpdateDeleteLocationError<br />**Hex**:<br />80060736<br />**Número**:<br />-2147088586|No puede actualizar ni eliminar la ubicación de documento de SharePoint de tipo ODB (OneDrive para la Empresa).|
> |**Nombre**:<br />SPOperationNotSupportedErrorCode<br />**Hex**:<br />80060715<br />**Número**:<br />-2147088619|La lista no admite esta operación|
> |**Nombre**:<br />SPOperatorNotSupportedErrorCode<br />**Hex**:<br />80060724<br />**Número**:<br />-2147088604|{0} no admite el operador seleccionado|
> |**Nombre**:<br />SPPersonalSiteNotFound<br />**Hex**:<br />8006072B<br />**Número**:<br />-2147088597|No se encontró el sitio personal que para el usuario.|
> |**Nombre**:<br />SPRequiredColCheckInErrorCode<br />**Hex**:<br />80060725<br />**Número**:<br />-2147088603|Excepciones se producen durante el check-in de documentos porque algunas columnas se hacen obligatorias en SharePoint|
> |**Nombre**:<br />SPSearchOneDriveNotCreated<br />**Hex**:<br />80060737<br />**Número**:<br />-2147088585|La ubicación de OneDrive todavía no se ha creado. Cree la ubicación antes de buscarla.|
> |**Nombre**:<br />SPSharedLockOnFileErrorCode<br />**Hex**:<br />80060704<br />**Número**:<br />-2147088636|Bloqueo compartido en el archivo|
> |**Nombre**:<br />SPSiteNotFoundErrorCode<br />**Hex**:<br />8006071A<br />**Número**:<br />-2147088614|Sitio no encontrado|
> |**Nombre**:<br />SPSiteProtocolError<br />**Hex**:<br />80060738<br />**Número**:<br />-2147088584|Error de protocolos en el acceso a SharePoint|
> |**Nombre**:<br />SPThrottlingLimitExceededErrorCode<br />**Hex**:<br />80060714<br />**Número**:<br />-2147088620|La operación supera el límite|
> |**Nombre**:<br />SPUnauthorizedAccessErrorCode<br />**Hex**:<br />80060701<br />**Número**:<br />-2147088639|El usuario actual no dispone de privilegios suficientes|
> |**Nombre**:<br />SPUploadFailure<br />**Hex**:<br />80060740<br />**Número**:<br />-2147088576|Error de la carga en SharePoint por motivos desconocidos. Probablemente el archivo sea demasiado grande|
> |**Nombre**:<br />SqlArithmeticOverflowError<br />**Hex**:<br />80041136<br />**Número**:<br />-2147217098|Se ha producido un error de desbordamiento aritmético de SQL|
> |**Nombre**:<br />SqlEncryption<br />**Hex**:<br />80048518<br />**Número**:<br />-2147187432|Se produjo un error en el cifrado de datos.|
> |**Nombre**:<br />SqlEncryptionCannotOpenSymmetricKeyBecauseDatabaseMasterKeyDoesNotExistOrIsNotOpened<br />**Hex**:<br />8004851A<br />**Número**:<br />-2147187430|No se puede abrir clave simétrica porque la clave maestra de la base de datos no existe en la base de datos o no está abierta.|
> |**Nombre**:<br />SqlEncryptionCertificateDoesNotExist<br />**Hex**:<br />8004851D<br />**Número**:<br />-2147187427|El certificado con nombre ='{0}' no existe en la base de datos.|
> |**Nombre**:<br />SqlEncryptionChangeEncryptionKeyExceededQuotaForTheInterval<br />**Hex**:<br />80048529<br />**Número**:<br />-2147187415|Ya se ha ejecutado el 'Cambio' de clave de cifrado {0} veces en los últimos {1} minutos. Espere unos minutos e inténtelo de nuevo.|
> |**Nombre**:<br />SqlEncryptionCreateCertificateError<br />**Hex**:<br />8004851E<br />**Número**:<br />-2147187426|No se puede crear certificado con nombre ='{0}' porque ya existe.|
> |**Nombre**:<br />SqlEncryptionCreateDatabaseMasterKeyError<br />**Hex**:<br />8004851B<br />**Número**:<br />-2147187429|No se puede crear clave maestra de la base de datos porque ya existe.|
> |**Nombre**:<br />SqlEncryptionCreateSymmetricKeyError<br />**Hex**:<br />80048521<br />**Número**:<br />-2147187423|No se puede crear clave simétrica con nombre ='{0}' porque ya existe.|
> |**Nombre**:<br />SqlEncryptionDatabaseMasterKeyDoesNotExist<br />**Hex**:<br />80048519<br />**Número**:<br />-2147187431|La clave maestra de base de tados no existe en la base de datos.|
> |**Nombre**:<br />SqlEncryptionDeleteCertificateError<br />**Hex**:<br />8004851F<br />**Número**:<br />-2147187425|No se puede eliminar el certificado con nombre ='{0}' porque no existe.|
> |**Nombre**:<br />SqlEncryptionDeleteDatabaseMasterKeyError<br />**Hex**:<br />8004851C<br />**Número**:<br />-2147187428|No se puede eliminar clave maestra de la base de datos porque no existe.|
> |**Nombre**:<br />SqlEncryptionDeleteEncryptionKeyError<br />**Hex**:<br />80048526<br />**Número**:<br />-2147187418|No se puede eliminar la clave de cifrado.|
> |**Nombre**:<br />SqlEncryptionDeleteSymmetricKeyError<br />**Hex**:<br />80048522<br />**Número**:<br />-2147187422|No se puede eliminar la clave simétrica con nombre ='{0}' porque no existe.|
> |**Nombre**:<br />SqlEncryptionEncryptionDecryptionTestError<br />**Hex**:<br />80048523<br />**Número**:<br />-2147187421|Error al probar el cifrado y descifrado de datos.|
> |**Nombre**:<br />SqlEncryptionEncryptionKeyValidationError<br />**Hex**:<br />80048528<br />**Número**:<br />-2147187416|La nueva clave de cifrado no cumple los estrictos requisitos de clave de cifrado. La clave debe tener una longitud de 10 a 100 caracteres y debe contener al menos un número, al menos una letra y un símbolo o carácter especial. {0}|
> |**Nombre**:<br />SqlEncryptionIsActiveCannotRestoreEncryptionKey<br />**Hex**:<br />80048525<br />**Número**:<br />-2147187419|No puede 'activar' clave de cifrado porque la clave de cifrado ya está establecida y está en uso. Utilice en su lugar la clave de cifrado 'cambiar'.|
> |**Nombre**:<br />SqlEncryptionIsInactiveCannotChangeEncryptionKey<br />**Hex**:<br />80048527<br />**Número**:<br />-2147187417|No puede 'cambiar' clave de cifrado porque la clave de cifrado no está establecida y no está en uso. Utilice primero 'Activar' clave de cifrado para establecer la clave de cifrado actual correcta y, después, utilice 'cambiar' cifrado si quiere volver a cifrar datos mediante una clave de cifrado nueva.|
> |**Nombre**:<br />SqlEncryptionKeyCannotDecryptExistingData<br />**Hex**:<br />80048524<br />**Número**:<br />-2147187420|No se pueden descifrar los datos cifrados (entidad ='{0}', atributo ='{1}') con la clave de cifrado actual. Utilice la clave de encriptación 'Activar' para establecer la clave de cifrado correcta.|
> |**Nombre**:<br />SqlEncryptionRestoreEncryptionKeyCannotDecryptExistingData<br />**Hex**:<br />8004852B<br />**Número**:<br />-2147187413|No se puede 'activar' porque la clave de cifrado no coincide con la clave de cifrado original que se usó para cifrar los datos.|
> |**Nombre**:<br />SqlEncryptionSetEncryptionKeyIsAlreadyRunningCannotRunItInParallel<br />**Hex**:<br />8004852A<br />**Número**:<br />-2147187414|El sistema está ejecutando una solicitud para cambiar o activar la clave de cifrado. Espera antes de realizar otra solicitud.|
> |**Nombre**:<br />SqlEncryptionSymmetricKeyCannotOpenBecauseWrongPassword<br />**Hex**:<br />80048530<br />**Número**:<br />-2147187408|No se pueden abrir clave simétrica de cifrado porque la contraseña es incorrecta.|
> |**Nombre**:<br />SqlEncryptionSymmetricKeyDoesNotExist<br />**Hex**:<br />80048520<br />**Número**:<br />-2147187424|Clave simétrica con nombre ={0} no existe en la base de datos.|
> |**Nombre**:<br />SqlEncryptionSymmetricKeyDoesNotExistOrNoPermission<br />**Hex**:<br />8004852F<br />**Número**:<br />-2147187409|No se puede abrir clave simétrica de cifrado porque no existe en la base de datos o el usuario no tiene permiso.|
> |**Nombre**:<br />SqlEncryptionSymmetricKeyPasswordDoesNotExistInConfigDB<br />**Hex**:<br />8004852E<br />**Número**:<br />-2147187410|Contraseña de clave simétrica de cifrado no existe en la base de datos de configuración.|
> |**Nombre**:<br />SqlEncryptionSymmetricKeySourceDoesNotExistInConfigDB<br />**Hex**:<br />8004852D<br />**Número**:<br />-2147187411|Origen de clave simétrica de cifrado no existe en la base de datos de configuración.|
> |**Nombre**:<br />SqlErrorInStoredProcedure<br />**Hex**:<br />8004C001<br />**Número**:<br />-2147172351|Error SQL {0} en procedimiento almacenado {1}|
> |**Nombre**:<br />SqlMaxRecursionExceeded<br />**Hex**:<br />80044157<br />**Número**:<br />-2147204777|se ha alcanzado la recursión máxima antes de completar la declaración.|
> |**Nombre**:<br />SrsDataConnectorNotInstalled<br />**Hex**:<br />80040492<br />**Número**:<br />-2147220334|Conector de datos MSCRM no instalado|
> |**Nombre**:<br />SrsDataConnectorNotInstalledUpload<br />**Hex**:<br />80048292<br />**Número**:<br />-2147188078|Este informe no se puede cargar porque Dynamics 365 Reporting Extensions, que incluye componentes necesarios para los informes, no están instalados en el servidor que ejecuta Microsoft SQL Server Reporting Services.|
> |**Nombre**:<br />SSM_MaxPCI_Exceeded<br />**Hex**:<br />80072570<br />**Número**:<br />-2147015312|Vuelva a iniciar sesión para actualizar su sesión.|
> |**Nombre**:<br />SSM_RefreshToken_Failed<br />**Hex**:<br />80072571<br />**Número**:<br />-2147015311|No se pudo actualizar la sesión de inicio de sesión.|
> |**Nombre**:<br />StageEntityIsNull<br />**Hex**:<br />80060451<br />**Número**:<br />-2147089327|Error de validación: la entidad de fase no puede ser null.|
> |**Nombre**:<br />StageIdIsEmpty<br />**Hex**:<br />80060454<br />**Número**:<br />-2147089324|Error de validación: El identificador de la fase no puede estar vacío.|
> |**Nombre**:<br />StageIdIsNotPresentInBusinessProcess<br />**Hex**:<br />80060450<br />**Número**:<br />-2147089328|Error de validación: El identificador de la fase '{0}' no está presente en el proceso de negocio. Póngase en contacto con el administrador del sistema.|
> |**Nombre**:<br />StageIdIsNotValid<br />**Hex**:<br />80060458<br />**Número**:<br />-2147089320|Error de validación: El identificador de la fase no es válido para el proceso de negocio.|
> |**Nombre**:<br />StandAloneBpfNotActivated<br />**Hex**:<br />80060470<br />**Número**:<br />-2147089296|StandAlone BPF debe activarse en la página de Flujos.|
> |**Nombre**:<br />StateTransitionActivateNewStatus<br />**Hex**:<br />8004F857<br />**Número**:<br />-2147157929|No puede activar este registro debido al estado de las reglas de transición.Póngase en contacto con el administrador del sistema.|
> |**Nombre**:<br />StateTransitionActiveToCanceled<br />**Hex**:<br />8004F855<br />**Número**:<br />-2147157931|Debido a las reglas de transición del estado, no puede cancelar el caso en el estado actual. Cambie el estado del caso e intente cancelarlo o póngase en contacto con el administrador del sistema.|
> |**Nombre**:<br />StateTransitionActiveToResolve<br />**Hex**:<br />8004F854<br />**Número**:<br />-2147157932|Debido a las reglas de transición de estado, no puede resolver un caso en el estado actual. Cambie el estado del caso e intente resolverlo o póngase en contacto con el administrador del sistema.|
> |**Nombre**:<br />StateTransitionDeactivateNewStatus<br />**Hex**:<br />8004F858<br />**Número**:<br />-2147157928|No puede desactivar este registro debido al estado de las reglas de transición.Póngase en contacto con el administrador del sistema.|
> |**Nombre**:<br />StateTransitionResolvedOrCanceledToActive<br />**Hex**:<br />8004F856<br />**Número**:<br />-2147157930|Debido a las reglas de transición de estado, no puede activar el caso desde el estado actual. Póngase en contacto con el administrador del sistema.|
> |**Nombre**:<br />StepAutomaticallyDisabled<br />**Hex**:<br />80045043<br />**Número**:<br />-2147200957|El sdkmessageprocessingstep original se ha deshabilitado y sustituido.|
> |**Nombre**:<br />StepCountInXamlExceedsMaxAllowed<br />**Hex**:<br />80060414<br />**Número**:<br />-2147089388|Hay {0} {1} en el Xaml. El número máximo permitido es {2}.|
> |**Nombre**:<br />StepDoesNotHaveAnyChildInXaml<br />**Hex**:<br />80060416<br />**Número**:<br />-2147089386|{0} no tiene al menos una {1} como secundaria.|
> |**Nombre**:<br />StepNotSupportedForClientBusinessRule<br />**Hex**:<br />80060000<br />**Número**:<br />-2147090432|El paso {0} no se admite para la regla de negocio del cliente.|
> |**Nombre**:<br />StepStepDoesNotHaveAnyControlStepAsItsChildren<br />**Hex**:<br />80060409<br />**Número**:<br />-2147089399|StepStep no tiene ningún ControlStep como actividad secundaria|
> |**Nombre**:<br />StoredProcedureContext<br />**Hex**:<br />8004C002<br />**Número**:<br />-2147172350|Error de Dynamics 365 {0} en {1}:{2}|
> |**Nombre**:<br />StringAttributeIndexError<br />**Hex**:<br />8004D292<br />**Número**:<br />-2147167598|Uno de los atributos de la entidad seleccionada es una parte del índice de base de datos y, por lo tanto, no puede ser mayor que 900 bytes.|
> |**Nombre**:<br />StringLengthTooLong<br />**Hex**:<br />80044331<br />**Número**:<br />-2147204303|Se ha producido un error de validación. Un valor de cadena proporcionado es demasiado largo.|
> |**Nombre**:<br />SubcomponentDoesNotExist<br />**Hex**:<br />80048537<br />**Número**:<br />-2147187401|El subcomponente {0} de tipo {1} no se encuentra en la organización y no se puede agregar a los SolutionComponents.|
> |**Nombre**:<br />SubcomponentMissingARoot<br />**Hex**:<br />80048536<br />**Número**:<br />-2147187402|El subcomponente {0} no se puede agregar a la solución porque falta el componente raíz {1}.|
> |**Nombre**:<br />SubjectDoesNotExist<br />**Hex**:<br />80043e02<br />**Número**:<br />-2147205630|El asunto no existe.|
> |**Nombre**:<br />SubjectLoopBeingCreated<br />**Hex**:<br />80043e01<br />**Número**:<br />-2147205631|La creación de esta asociación jerárquica crearía un bucle en la jerarquía de temas.|
> |**Nombre**:<br />SubjectLoopExists<br />**Hex**:<br />80043e00<br />**Número**:<br />-2147205632|Existe un bucle en la jerarquía de los asuntos.|
> |**Nombre**:<br />SubReportDoesNotExist<br />**Hex**:<br />80040493<br />**Número**:<br />-2147220333|El subinforme no existe. ReportId:{0}|
> |**Nombre**:<br />SubscriptionGone<br />**Hex**:<br />80072513<br />**Número**:<br />-2147015405|Suscripción agotada|
> |**Nombre**:<br />SupportLogOnExpired<br />**Hex**:<br />8004A108<br />**Número**:<br />-2147180280|El inicio de sesión de soporte técnico ha expirado|
> |**Nombre**:<br />SupportUserCannotBeCreateNorUpdated<br />**Hex**:<br />80041d41<br />**Número**:<br />-2147214015|El usuario de soporte no se puede actualizar.|
> |**Nombre**:<br />SyncAttributeMappingCannotBeUpdated<br />**Hex**:<br />80060741<br />**Número**:<br />-2147088575|La asignación del atributo de sincronización no se puede actualizar.|
> |**Nombre**:<br />SyncToMsdeFailure<br />**Hex**:<br />80048407<br />**Número**:<br />-2147187705|Se produjo un error al iniciar o conectarse a la base de datos de Microsoft MSDE en modo sin conexión.|
> |**Nombre**:<br />SystemAttributeMap<br />**Hex**:<br />80046205<br />**Número**:<br />-2147196411|No se puede crear o eliminar el mapa de atributos del sistema que tiene ID {0} desde {1} a {2} perteneciente a un mapa de entidad con id {3} desde {4} a {5}.|
> |**Nombre**:<br />SystemEntityMap<br />**Hex**:<br />80046202<br />**Número**:<br />-2147196414|Se produjo un error de SystemEntityMap|
> |**Nombre**:<br />SystemFormCopyUnmatchedEntity<br />**Hex**:<br />8004F656<br />**Número**:<br />-2147158442|La entidad para Target y SourceId debe coincidir.|
> |**Nombre**:<br />SystemFormCopyUnmatchedFormType<br />**Hex**:<br />8004F657<br />**Número**:<br />-2147158441|El tipo de formulario de SourceId no es válido para la entidad Target.|
> |**Nombre**:<br />SystemFormCreateWithExistingLabel<br />**Hex**:<br />8004F658<br />**Número**:<br />-2147158440|La etiqueta '{0}', id: '{1}' ya existe. Proporcione valores de labelid únicos.|
> |**Nombre**:<br />SystemFormImportMissingRoles<br />**Hex**:<br />8004F655<br />**Número**:<br />-2147158443|La solución no administrada que está importando tiene atributos XML de condición de visualización que hacen referencia a roles de seguridad que el sistema objetivo no tiene. Se quitarán los atributos que hacen referencia a estos roles de seguridad.|
> |**Nombre**:<br />SystemUserDisabled<br />**Hex**:<br />8004A112<br />**Número**:<br />-2147180270|Se ha deshabilitado el usuario del sistema, por tanto, el vale expirado.|
> |**Nombre**:<br />TamperedAuthTicket<br />**Hex**:<br />8004A105<br />**Número**:<br />-2147180283|El vale especificado para la autenticación se ha manipulado o invalidado.|
> |**Nombre**:<br />TargetAttributeInvalidForIgnore<br />**Hex**:<br />80048500<br />**Número**:<br />-2147187456|El nombre de atributo de destino debe estar vacío si se ignora el código de proceso.|
> |**Nombre**:<br />TargetAttributeInvalidForMap<br />**Hex**:<br />80040394<br />**Número**:<br />-2147220588|Este atributo no es válido para la asignación.|
> |**Nombre**:<br />TargetAttributeNotFound<br />**Hex**:<br />80040392<br />**Número**:<br />-2147220590|El archivo especifica un atributo que no existe en Microsoft Dynamics 365.|
> |**Nombre**:<br />TargetEntityInvalidForMap<br />**Hex**:<br />80040395<br />**Número**:<br />-2147220587|El archivo especifica una entidad que no es válida para la migración de datos.|
> |**Nombre**:<br />TargetEntityNotFound<br />**Hex**:<br />80040391<br />**Número**:<br />-2147220591|El archivo especifica una entidad que no existe en Microsoft Dynamics 365.|
> |**Nombre**:<br />TargetEntityNotMapped<br />**Hex**:<br />80048460<br />**Número**:<br />-2147187616|Nombre de la entidad de destino no definido para origen:{0} archivo.|
> |**Nombre**:<br />TargetUserInsufficientPrivileges<br />**Hex**:<br />80048342<br />**Número**:<br />-2147187902|No se puede agregar el usuario al equipo porque aquel no tiene el privilegio "{0}".|
> |**Nombre**:<br />TaskFlowEmptyName<br />**Hex**:<br />80061712<br />**Número**:<br />-2147084526|El campo de nombre no puede estar vacío. Escriba un nombre.|
> |**Nombre**:<br />TaskFlowEntityAttributeIsNotValid<br />**Hex**:<br />80061717<br />**Número**:<br />-2147084521|Tipo de atributo no válido: {0}.{1}.|
> |**Nombre**:<br />TaskFlowEntityRelationshipIsNotValid<br />**Hex**:<br />80061716<br />**Número**:<br />-2147084522|Tipo de relación no válido: {0}.|
> |**Nombre**:<br />TaskFlowFormXmlNotFound<br />**Hex**:<br />80061713<br />**Número**:<br />-2147084525|No se encontró el formulario del sistema {0} para el flujo de tareas {1}.|
> |**Nombre**:<br />TaskFlowInvalidCharactersInName<br />**Hex**:<br />80061711<br />**Número**:<br />-2147084527|El campo del nombre solo puede contener caracteres alfanuméricos.|
> |**Nombre**:<br />TaskFlowMaxNumberControls<br />**Hex**:<br />80061719<br />**Número**:<br />-2147084519|El flujo de tareas ha superado el número máximo de controles permitidos ({0}). Para continuar, debe quitar algunos controles.|
> |**Nombre**:<br />TaskFlowMaxNumberPages<br />**Hex**:<br />80061718<br />**Número**:<br />-2147084520|El flujo de tareas ha superado el número máximo de páginas permitidas ({0}). Para continuar, debe quitar algunas páginas.|
> |**Nombre**:<br />TaskFlowNameIsNotUnique<br />**Hex**:<br />80061710<br />**Número**:<br />-2147084528|Ya existe un flujo de tareas con el nombre especificado.  Especifique un nombre exclusivo.|
> |**Nombre**:<br />TaskFlowNotFound<br />**Hex**:<br />80061720<br />**Número**:<br />-2147084512|Un flujo de tareas que intenta iniciar no está disponible en este dispositivo. No tiene permiso para acceder a ella o puede que no esté disponible en su organización. Póngase en contacto con el administrador del sistema.|
> |**Nombre**:<br />TaskFlowNotValid<br />**Hex**:<br />8006172F<br />**Número**:<br />-2147084497|La definición del flujo de tareas no es válida.|
> |**Nombre**:<br />TaskFlowPageMissingFormXmlTab<br />**Hex**:<br />80061714<br />**Número**:<br />-2147084524|No se encontraron las páginas {0} para el flujo de tareas {1} Paso {2}.|
> |**Nombre**:<br />TaskFlowUnsupportedEntities<br />**Hex**:<br />80061715<br />**Número**:<br />-2147084523|Las siguientes entidades no están habilitadas para los flujos de tareas: {0}.|
> |**Nombre**:<br />TeamAdministratorMissedPrivilege<br />**Hex**:<br />80041d0a<br />**Número**:<br />-2147214070|El administrador de equipo no tiene privilegios para leer el equipo.|
> |**Nombre**:<br />TeamInWrongBusiness<br />**Hex**:<br />8004140d<br />**Número**:<br />-2147216371|El equipo con el id={0} pertenece a otra unidad de negocio={1} que el rol con el roleId={2} y el roleBusinessUnit={3}.|
> |**Nombre**:<br />TeamNameTooLong<br />**Hex**:<br />80048305<br />**Número**:<br />-2147187963|El nombre especificado para el equipo es demasiado largo.|
> |**Nombre**:<br />TeamNotAssignedRoles<br />**Hex**:<br />80042f0a<br />**Número**:<br />-2147209462|No se han asignado roles al equipo.|
> |**Nombre**:<br />TemplateNotAllowedForInternetMarketing<br />**Hex**:<br />80048475<br />**Número**:<br />-2147187595|No se permite la creación de plantillas con actividades de campañas de Marketing de Internet|
> |**Nombre**:<br />TemplateTypeNotSupportedForUnsubscribeAcknowledgement<br />**Hex**:<br />80040324<br />**Número**:<br />-2147220700|Este tipo de plantilla no se admite para la confirmación de cancelación de suscripción.|
> |**Nombre**:<br />TenantIDIsEmpty<br />**Hex**:<br />8005E25A<br />**Número**:<br />-2147098022|El campo ID de inquilino de Exchange Online no puede estar vacío.|
> |**Nombre**:<br />TenantIDValueChanged<br />**Hex**:<br />8005E25C<br />**Número**:<br />-2147098020|El tenantId detectado para el intercambio es diferente del que guardó.|
> |**Nombre**:<br />TestEmailConfigurationScheduledInProgress<br />**Hex**:<br />8005E248<br />**Número**:<br />-2147098040|La prueba de la configuración de correo electrónico de prueba está en curso. Guarde tras finalizar la prueba.|
> |**Nombre**:<br />TextAnalyticsAPIActiveConfigurationDoesNotExist<br />**Hex**:<br />80061690<br />**Número**:<br />-2147084656|No existe ninguna configuración activa para la entidad.|
> |**Nombre**:<br />TextAnalyticsAPIActiveSimilarityConfigurationDoesNotExist<br />**Hex**:<br />80061695<br />**Número**:<br />-2147084651|No existe ninguna regla de similitud activa. El administrador del sistema debe realizar una configuración de la regla de similitud.|
> |**Nombre**:<br />TextAnalyticsAPIAllowedOnlyForEnglishLanguage<br />**Hex**:<br />80061691<br />**Número**:<br />-2147084655|La característica de análisis de textos está disponible para las organizaciones cuyo idioma base es el inglés.|
> |**Nombre**:<br />TextAnalyticsAPIAzureUnableToConnectWithBuild<br />**Hex**:<br />80061692<br />**Número**:<br />-2147084654|Falló la conexión de Dynamics 365 con el servicio de análisis de textos de Azure. Verifique que la dirección URI del servicio y la cuenta son válidas y que la suscripción de Azure está activa.|
> |**Nombre**:<br />TextAnalyticsAzureConnectionCascadeActivateFailed<br />**Hex**:<br />80061634<br />**Número**:<br />-2147084748|No se pueden activar uno o varios modelos de análisis de textos. Intente activar los modelos de análisis de textos existentes por separado de la conexión del servicio de Azure.|
> |**Nombre**:<br />TextAnalyticsAzureConnectionFailed<br />**Hex**:<br />80061650<br />**Número**:<br />-2147084720|No se puede conectar a la API de análisis de textos.|
> |**Nombre**:<br />TextAnalyticsAzureSchedulerError<br />**Hex**:<br />80061693<br />**Número**:<br />-2147084653|Falló la conexión de Dynamics 365 con el servicio de análisis de textos de Azure. Inténtelo de nuevo. Si el problema continúa, póngase en contacto con el administrador del sistema.|
> |**Nombre**:<br />TextAnalyticsAzureTestConnectionFailed<br />**Hex**:<br />80061632<br />**Número**:<br />-2147084750|Error al conectar con el servicio de análisis de texto de Azure. Compruebe que la dirección URL del servicio y la cuenta de Azure son válidos y la suscripción de servicio está activa.|
> |**Nombre**:<br />TextAnalyticsAzureUnableToConnectWithBuild<br />**Hex**:<br />80061655<br />**Número**:<br />-2147084715|Falló la conexión de Dynamics 365 con el servicio de análisis de textos de Azure. Verifique que la dirección URI del servicio y la cuenta son válidas y que la suscripción de Azure está activa.|
> |**Nombre**:<br />TextAnalyticsFeatureNotEnabled<br />**Hex**:<br />80061652<br />**Número**:<br />-2147084718|La característica de análisis de textos de Azure no está activada. El administrador del sistema debe activar esta característica y realizar la configuración necesaria.|
> |**Nombre**:<br />TextAnalyticsMappingUsedForActiveConfiguration<br />**Hex**:<br />80061667<br />**Número**:<br />-2147084697|Esta asignación de entidad de análisis de texto se usa como una configuración activa. No puede modificar o eliminar mientras que se usa en una configuración activa.|
> |**Nombre**:<br />TextAnalyticsMaxLimitForTopicModelReached<br />**Hex**:<br />80061694<br />**Número**:<br />-2147084652|Se ha alcanzado el número máximo de modelos de tema permitidos para su organización.|
> |**Nombre**:<br />TextAnalyticsModelActivateConnectionMustBeActive<br />**Hex**:<br />80061657<br />**Número**:<br />-2147084713|La conexión del servicio de análisis de textos de Aprendizaje automático de Microsoft Azure se debe activar antes de poder activar el modelo. Active la conexión del servicio de análisis de textos e inténtelo de nuevo.|
> |**Nombre**:<br />ThemeIdOrUpdateTimestampIsNull<br />**Hex**:<br />800608D1<br />**Número**:<br />-2147088175|El Id. del tema o el id. de marca de tiempo de la actualización no están presentes en los datos del tema.|
> |**Nombre**:<br />Límite<br />**Hex**:<br />8005F103<br />**Número**:<br />-2147094269|Demasiadas solcitudes.|
> |**Nombre**:<br />ThrottlingBurstRequestLimitExceededError<br />**Hex**:<br />80072322<br />**Número**:<br />-2147015902|El número de solicitudes ha superado el límite de {0} respecto a la ventana de tiempo de {1} segundos.|
> |**Nombre**:<br />ThrottlingConcurrencyLimitExceededError<br />**Hex**:<br />80072326<br />**Número**:<br />-2147015898|El número de solicitudes simultáneas ha superado el límite de {0}.|
> |**Nombre**:<br />ThrottlingTimeExceededError<br />**Hex**:<br />80072321<br />**Número**:<br />-2147015903|El tiempo de ejecución combinado de solicitudes entrantes ha superado el límite de {0} milisegundos sobre la ventana de tiempo de {1} segundos. Reduzca el número de solicitudes simultáneas o disminuya la duración de las solicitudes e inténtelo más tarde.|
> |**Nombre**:<br />TooManyBytesInInputStream<br />**Hex**:<br />8004F901<br />**Número**:<br />-2147157759|La secuencia de la que se está leyendo tiene demasiados bytes.|
> |**Nombre**:<br />TooManyCalculatedFieldsInQuery<br />**Hex**:<br />80060429<br />**Número**:<br />-2147089367|El número de campos calculados en la consulta superó el límite máximo de {0}.|
> |**Nombre**:<br />TooManyConditionParametersInQuery<br />**Hex**:<br />8004430E<br />**Número**:<br />-2147204338|El número de parámetros de una condición superó el límite máximo.|
> |**Nombre**:<br />TooManyConditionsInQuery<br />**Hex**:<br />8004430C<br />**Número**:<br />-2147204340|El número de condiciones en la consulta superó el límite máximo.|
> |**Nombre**:<br />TooManyEntitiesEnabledForAutoCreatedAccessTeams<br />**Hex**:<br />80048332<br />**Número**:<br />-2147187918|Demasiadas entidades habilitadas para crear automáticamente equipos de acceso.|
> |**Nombre**:<br />TooManyLinkEntitiesInQuery<br />**Hex**:<br />8004430D<br />**Número**:<br />-2147204339|El número de entidades de vínculos en la consulta superó el límite máximo.|
> |**Nombre**:<br />TooManyModernFlowTriggersForExecute<br />**Hex**:<br />80060477<br />**Número**:<br />-2147089289|No se puede ejecutar Modern Flow '{0}' porque hay más de una devolución de llamada registrada.|
> |**Nombre**:<br />TooManyMultiSelectConditionParametersInQuery<br />**Hex**:<br />80050223<br />**Número**:<br />-2147155421|El número de parámetros de condición de selección múltiple en la consulta superó el límite máximo: {0}.|
> |**Nombre**:<br />TooManyPicklistValues<br />**Hex**:<br />80048492<br />**Número**:<br />-2147187566|El número de valores de la lista desplegable diferenciada superará el límite.|
> |**Nombre**:<br />TooManyRecipients<br />**Hex**:<br />8004350e<br />**Número**:<br />-2147207922|No se admite el envío a varios destinatarios.|
> |**Nombre**:<br />TooManySelectionsForAttributeType<br />**Hex**:<br />80050222<br />**Número**:<br />-2147155422|El número de selecciones para el tipo de atributo MultiSelectPicklist superó límite máximo: {0}.|
> |**Nombre**:<br />TooManyTeamTemplatesForEntityAccessTeams<br />**Hex**:<br />80048333<br />**Número**:<br />-2147187917|El número actual de equipos: {0} es mayor que el límite de equipos: {1} para la entidad con ObjectTypeCode {2}|
> |**Nombre**:<br />TopicModelActivateWithInvalidConfiguration<br />**Hex**:<br />80061656<br />**Número**:<br />-2147084714|La configuración usada para la compilación no es válida. Los campos de determinación de temas son necesarios para la configuración usada para el análisis de temas.|
> |**Nombre**:<br />TopicModelConfigurationAssociatedModelAlreadyActive<br />**Hex**:<br />80061670<br />**Número**:<br />-2147084688|No se puede actualizar ni eliminar la configuración del modelo de tema porque está asociada a un modelo de tema activo.|
> |**Nombre**:<br />TopicModelConfigurationUsedEmpty<br />**Hex**:<br />80061653<br />**Número**:<br />-2147084717|La activación requiere especificar la configuración de compilación. Especifique la configuración usada para la compilación antes de la activación.|
> |**Nombre**:<br />TopicModelScheduleBuildSettingsEmpty<br />**Hex**:<br />80061651<br />**Número**:<br />-2147084719|La activación requiere establecer la programación de compilación. Especifique la configuración de generación de programación antes de la activación.|
> |**Nombre**:<br />TopicModelTestWithoutConfiguration<br />**Hex**:<br />80061654<br />**Número**:<br />-2147084716|Especifique la configuración usada para la compilación.|
> |**Nombre**:<br />TraceMessageConstructionError<br />**Hex**:<br />8004F900<br />**Número**:<br />-2147157760|El registro de seguimiento tiene un código de seguimiento no válido o un número suficiente de parámetros de seguimiento.|
> |**Nombre**:<br />TransactionAborted<br />**Hex**:<br />80040255<br />**Número**:<br />-2147220907|Transacción anulada.|
> |**Nombre**:<br />TransactionAbortedByIsvException<br />**Hex**:<br />80048550<br />**Número**:<br />-2147187376|Transacción cancelada por la excepción del código ISV en la etapa previa a la confirmación. Para obtener información detallada, consulte excepción interna.|
> |**Nombre**:<br />TransactionNotCommited<br />**Hex**:<br />80040252<br />**Número**:<br />-2147220910|Transacciones no confirmadas.|
> |**Nombre**:<br />TransactionNotStarted<br />**Hex**:<br />80040251<br />**Número**:<br />-2147220911|Transacción sin iniciar.|
> |**Nombre**:<br />TransactionNotSupported<br />**Hex**:<br />8005E007<br />**Número**:<br />-2147098617|La operación que está intentando realizar no admite transacciones.|
> |**Nombre**:<br />TransformationResumeNotSupported<br />**Hex**:<br />80048463<br />**Número**:<br />-2147187613|No se admite reanudar o reintentar el trabajo de transformación de la importación.|
> |**Nombre**:<br />TransformMustBeCalledBeforeImport<br />**Hex**:<br />80040335<br />**Número**:<br />-2147220683|No se puede llamar importación antes de la transformación.|
> |**Nombre**:<br />TranslateArticle_OnlyPrimaryArticlesCanBeTranslated<br />**Hex**:<br />80061402<br />**Número**:<br />-2147085310|Este artículo es una traducción del artículo original. No se puede traducir de nuevo. Si quiere que otra traducción, comience con el artículo original en lugar de este.|
> |**Nombre**:<br />TranslateArticle_TranslationCanNotBeCreatedForTheSameLanguage<br />**Hex**:<br />80061403<br />**Número**:<br />-2147085309|Ya existe una traducción en este idioma de esta versión del artículo|
> |**Nombre**:<br />TrendingDocumentsDataRetrievalFailure<br />**Hex**:<br />80044234<br />**Número**:<br />-2147204556|No podemos acceder a los Trending Documents. Vuelva a intentarlo más tarde.|
> |**Nombre**:<br />TrendingDocumentsIntegrationDisabledError<br />**Hex**:<br />80044233<br />**Número**:<br />-2147204557|Trending Documents está deshabilitado para su cuenta de Microsoft Dynamics 365.|
> |**Nombre**:<br />TrendingDocumentsIntegrationTurnedOffError<br />**Hex**:<br />80044255<br />**Número**:<br />-2147204523|Trending Documents desactivado. Póngase en contacto con el administrador del sistema para activar esta función en la Configuración del sistema.|
> |**Nombre**:<br />TrendingDocumentsOfflineModeError<br />**Hex**:<br />80044258<br />**Número**:<br />-2147204520|Trending Documents no está disponible en el modo sin conexión.|
> |**Nombre**:<br />TrendingDocumentsOnpremiseDeploymentError<br />**Hex**:<br />80044232<br />**Número**:<br />-2147204558|El servicio de Microsoft Office de su compañía no admite el componente del panel Trending Documents.|
> |**Nombre**:<br />TriggerFlowFailure<br />**Hex**:<br />80050261<br />**Número**:<br />-2147155359|Error al intentar ejecutar este flujo.|
> |**Nombre**:<br />TypeNotSetToDefinition<br />**Hex**:<br />80060402<br />**Número**:<br />-2147089406|Se debe definir el tipo Definición al crear la categoría de flujo de proceso de negocio|
> |**Nombre**:<br />UIDataGenerationFailed<br />**Hex**:<br />80045037<br />**Número**:<br />-2147200969|Error al generar el recuperar UIData de XAML.|
> |**Nombre**:<br />UIDataMissingInWorkflow<br />**Hex**:<br />80048471<br />**Número**:<br />-2147187599|El flujo de trabajo no contiene UIData.|
> |**Nombre**:<br />UIScriptIdentifierDuplicate<br />**Hex**:<br />8004F217<br />**Número**:<br />-2147159529|Ya existe una variable o argumento de entrada con el mismo nombre. Elija un nombre diferente e inténtelo de nuevo.|
> |**Nombre**:<br />UIScriptIdentifierInvalid<br />**Hex**:<br />8004F218<br />**Número**:<br />-2147159528|La variable o el nombre de argumento de entrada no es válido. El nombre sólo puede contener '_', caracteres numéricos y alfanuméricos. Elija un nombre diferente e inténtelo de nuevo.|
> |**Nombre**:<br />UIScriptIdentifierInvalidLength<br />**Hex**:<br />8004F219<br />**Número**:<br />-2147159527|La variable o el nombre de argumento de entrada es demasiado largo. Elija un nombre más pequeño e inténtelo de nuevo.|
> |**Nombre**:<br />UnableToActivateQuoteNotInDraft<br />**Hex**:<br />80100003<br />**Número**:<br />-2146435069|La oferta no se puede activar porque no se encuentra en estado de borrador.|
> |**Nombre**:<br />UnableToLoadCustomActivity<br />**Hex**:<br />8004505A<br />**Número**:<br />-2147200934|No se puede cargar la actividad personalizada.|
> |**Nombre**:<br />UnableToLoadPluginAssembly<br />**Hex**:<br />80044191<br />**Número**:<br />-2147204719|No se puede cargar el ensamblado de complemento.|
> |**Nombre**:<br />UnableToLoadPluginType<br />**Hex**:<br />80044190<br />**Número**:<br />-2147204720|No se puede cargar el tipo de complemento.|
> |**Nombre**:<br />UnableToLoadTransformationAssembly<br />**Hex**:<br />80040378<br />**Número**:<br />-2147220616|No se puede cargar el ensamblado de transformación.|
> |**Nombre**:<br />UnableToLoadTransformationType<br />**Hex**:<br />80040379<br />**Número**:<br />-2147220615|No se puede cargar el tipo de transformación.|
> |**Nombre**:<br />UnableToLogOnUserFromUserNameAndPassword<br />**Hex**:<br />80044311<br />**Número**:<br />-2147204335|No se puede iniciar sesión con el nombre de usuario y contraseña especificados.|
> |**Nombre**:<br />UnableToSendEmail<br />**Hex**:<br />8004B015<br />**Número**:<br />-2147176427|Error interno al enviar la invitación. Inténtelo más tarde.|
> |**Nombre**:<br />UnapprovedMailbox<br />**Hex**:<br />8005E220<br />**Número**:<br />-2147098080|El buzón no se encuentra en estado aprobado. Enviar y recibir mensajes se permite solo para los buzones aprobados.|
> |**Nombre**:<br />UnauthorizedAccess<br />**Hex**:<br />80040277<br />**Número**:<br />-2147220873|Se ha intentado realizar una operación no autorizada.|
> |**Nombre**:<br />UnExpected<br />**Hex**:<br />80040216<br />**Número**:<br />-2147220970|Se produjo un error inesperado.|
> |**Nombre**:<br />UnexpectedErrorInMailMerge<br />**Hex**:<br />80040330<br />**Número**:<br />-2147220688|Error inesperado durante la combinación de correspondencia.|
> |**Nombre**:<br />UnexpectedNullReferenceError<br />**Hex**:<br />8004F044<br />**Número**:<br />-2147159996|Error inesperado de referencia nula: {0}.|
> |**Nombre**:<br />UnexpectedRightOperandCount<br />**Hex**:<br />80060006<br />**Número**:<br />-2147090426|La matriz de operandos correcta de la expresión contiene un número inesperado. de operando.|
> |**Nombre**:<br />UnitDoesNotExist<br />**Hex**:<br />80043b1b<br />**Número**:<br />-2147206373|La unidad no existe.|
> |**Nombre**:<br />UnitLoopBeingCreated<br />**Hex**:<br />80043b1a<br />**Número**:<br />-2147206374|El uso de esta unidad base crearía un bucle en la jerarquía de la unidad.|
> |**Nombre**:<br />UnitLoopExists<br />**Hex**:<br />80043b19<br />**Número**:<br />-2147206375|Existe un bucle en la jerarquía de la unidad.|
> |**Nombre**:<br />UnitNoName<br />**Hex**:<br />80043b26<br />**Número**:<br />-2147206362|El nombre de unidad no puede ser nulo.|
> |**Nombre**:<br />UnitNotInSchedule<br />**Hex**:<br />80043b16<br />**Número**:<br />-2147206378|La unidad no existe en la programación de unidad especificada.|
> |**Nombre**:<br />UnknownInvalidTransformationParameterGeneric<br />**Hex**:<br />80048513<br />**Número**:<br />-2147187437|Uno o más valores de parámetros de transformación de entrada no son válidos {0}.|
> |**Nombre**:<br />unManagedchildentityisnotchild<br />**Hex**:<br />800404e6<br />**Número**:<br />-2147220250|La entidad secundaria suministrada no es secundaria.|
> |**Nombre**:<br />unManagedcihldofconditionforoffilefilters<br />**Hex**:<br />800404a9<br />**Número**:<br />-2147220311|La condición secundaria solo se permite en filtros sin conexión.|
> |**Nombre**:<br />UnmanagedComponentParentsManagedComponent<br />**Hex**:<br />8004803B<br />**Número**:<br />-2147188677|Encontrados {0} registros de dependencia donde un componente no administrado es el elemento primario de un componente administrado. Primer registro (dependentcomponentobjectid = {1}, tipo = {2}, requiredcomponentobjectid = {3}, tipo = {4}, solución = {5}).|
> |**Nombre**:<br />unManagedemptyprocessliteralcondition<br />**Hex**:<br />800404b0<br />**Número**:<br />-2147220304|No hay datos especificados para ProcessLiteralCondition.|
> |**Nombre**:<br />unManagedentityisnotintersect<br />**Hex**:<br />800404aa<br />**Número**:<br />-2147220310|La entidad no es una entidad de intersección.|
> |**Nombre**:<br />unManagederroraddingfiltertoqueryplan<br />**Hex**:<br />800404ca<br />**Número**:<br />-2147220278|Se ha produido un error al agregar un filtro para el plan de consulta.|
> |**Nombre**:<br />unManagederrorprocessingfilternodes<br />**Hex**:<br />800404c4<br />**Número**:<br />-2147220284|Se ha producido un error inesperado al procesar los nodos de filtro.|
> |**Nombre**:<br />unManagedfieldnotvalidatedbyplatform<br />**Hex**:<br />800404ae<br />**Número**:<br />-2147220306|Un campo no ha sido validado por la plataforma.|
> |**Nombre**:<br />unManagedfilterindexoutofrange<br />**Hex**:<br />800404ab<br />**Número**:<br />-2147220309|El índice de filtro está fuera del intervalo.|
> |**Nombre**:<br />unManagedIdsAccessDenied<br />**Hex**:<br />80048306<br />**Número**:<br />-2147187962|No hay suficientes privilegios de acceso al objeto de Microsoft Dynamics 365 o para realizar la operación solicitada.|
> |**Nombre**:<br />unManagedidsaccounthaschildopportunities<br />**Hex**:<br />80040511<br />**Número**:<br />-2147220207|La cuenta tiene oportunidades secundarias.|
> |**Nombre**:<br />unManagedidsactivitydurationdoesnotmatch<br />**Hex**:<br />8004350a<br />**Número**:<br />-2147207926|La duración de actividad no coincide con el tiempo de inicio y fin|
> |**Nombre**:<br />unManagedidsactivityinvalidduration<br />**Hex**:<br />80043509<br />**Número**:<br />-2147207927|Duración de la actividad no válida|
> |**Nombre**:<br />unManagedidsactivityinvalidobjecttype<br />**Hex**:<br />80043503<br />**Número**:<br />-2147207933|La actividad correspondiente al tipo de objeto no es válida.|
> |**Nombre**:<br />unManagedidsactivityinvalidpartyobjecttype<br />**Hex**:<br />80043505<br />**Número**:<br />-2147207931|El tipo de objeto del grupo de actividad no es válido.|
> |**Nombre**:<br />unManagedidsactivityinvalidregardingobject<br />**Hex**:<br />80043507<br />**Número**:<br />-2147207929|Actividad no válida respecto del objeto, probablemente no existe|
> |**Nombre**:<br />unManagedidsactivityinvalidstate<br />**Hex**:<br />80043500<br />**Número**:<br />-2147207936|Estado de actividad no válido|
> |**Nombre**:<br />unManagedidsactivityinvalidtimeformat<br />**Hex**:<br />80043508<br />**Número**:<br />-2147207928|Tiempo de actividad no válido, verifique el formato|
> |**Nombre**:<br />unManagedidsactivityinvalidtype<br />**Hex**:<br />80043501<br />**Número**:<br />-2147207935|Código de tipo de actividad no válido|
> |**Nombre**:<br />unManagedidsactivitynotroutable<br />**Hex**:<br />8004350b<br />**Número**:<br />-2147207925|No se puede enrutar este tipo de actividad|
> |**Nombre**:<br />unManagedidsactivityobjectidortypemissing<br />**Hex**:<br />80043502<br />**Número**:<br />-2147207934|Falta la actividad correspondiente al id. o tipo de objeto.|
> |**Nombre**:<br />unManagedidsactivitypartyobjectidortypemissing<br />**Hex**:<br />80043504<br />**Número**:<br />-2147207932|Falta el id. o tipo de objeto del grupo de actividad.|
> |**Nombre**:<br />unManagedidsanonymousenabled<br />**Hex**:<br />80040226<br />**Número**:<br />-2147220954|El usuario que ha iniciado sesión no se ha encontrado en Active Directory.|
> |**Nombre**:<br />unManagedidsarticletemplatecontainsarticles<br />**Hex**:<br />80043e05<br />**Número**:<br />-2147205627|No puede cambiar la plantilla de artículo porque hay artículo de knowledge base utilizándolo.|
> |**Nombre**:<br />unManagedidsarticletemplateisnotactive<br />**Hex**:<br />80043e07<br />**Número**:<br />-2147205625|La plantilla del artículo KB está inactiva.|
> |**Nombre**:<br />unManagedidsattachmentcannotcreatetempfile<br />**Hex**:<br />80044a05<br />**Número**:<br />-2147202555|No se puede crear archivo adjunto temporal.|
> |**Nombre**:<br />unManagedidsattachmentcannotgetfilesize<br />**Hex**:<br />80044a01<br />**Número**:<br />-2147202559|No se puede obtener el tamaño del archivo adjunto temporal.|
> |**Nombre**:<br />unManagedidsattachmentcannotopentempfile<br />**Hex**:<br />80044a00<br />**Número**:<br />-2147202560|No se puede abrir archivo adjunto temporal.|
> |**Nombre**:<br />unManagedidsattachmentcannotreadtempfile<br />**Hex**:<br />80044a03<br />**Número**:<br />-2147202557|No se puede leer el archivo adjunto temporal.|
> |**Nombre**:<br />unManagedidsattachmentcannottruncatetempfile<br />**Hex**:<br />80044a07<br />**Número**:<br />-2147202553|No se puede truncar un archivo adjunto temporal.|
> |**Nombre**:<br />unManagedidsattachmentcannotunmaptempfile<br />**Hex**:<br />80044a06<br />**Número**:<br />-2147202554|No se puede anular la asignación de un archivo adjunto temporal.|
> |**Nombre**:<br />unManagedidsattachmentinvalidfilesize<br />**Hex**:<br />80044a02<br />**Número**:<br />-2147202558|El tamaño del archivo adjunto es demasiado grande.|
> |**Nombre**:<br />unManagedidsattachmentisempty<br />**Hex**:<br />80044a04<br />**Número**:<br />-2147202556|El adjunto está vacío.|
> |**Nombre**:<br />unManagedidsbizmgmtbusinessparentdiffmerchant<br />**Hex**:<br />80041d04<br />**Número**:<br />-2147214076|El negocio no está en el mismo comerciante que el negocio principal.|
> |**Nombre**:<br />unManagedidsbizmgmtcallernotinpartnerbusiness<br />**Hex**:<br />80041d14<br />**Número**:<br />-2147214060|El autor de la llamada no es de la empresa asociada.|
> |**Nombre**:<br />unManagedidsbizmgmtcallernotinprimarybusiness<br />**Hex**:<br />80041d12<br />**Número**:<br />-2147214062|El autor de la llamada no es de la empresa principal.|
> |**Nombre**:<br />unManagedidsbizmgmtcannotaddlocaluser<br />**Hex**:<br />80041d32<br />**Número**:<br />-2147214030|Un usuario local no se puede agregar a Dynamics 365.|
> |**Nombre**:<br />unManagedidsbizmgmtcannotdeletebusiness<br />**Hex**:<br />80041d18<br />**Número**:<br />-2147214056|Este es un subconjunto de negocio. Utilice IBizMerchant::Delete para eliminar este subconjunto de negocio.|
> |**Nombre**:<br />unManagedidsbizmgmtcannotdeleteprovision<br />**Hex**:<br />80041d19<br />**Número**:<br />-2147214055|Se trata de una empresa raíz aprovisionada. Utilice IBizProvision::Delete para eliminar esta empresa raíz.|
> |**Nombre**:<br />unManagedidsbizmgmtcannotdisablebusiness<br />**Hex**:<br />80041d1a<br />**Número**:<br />-2147214054|No se puede deshabilitar esta unidad de negocio.|
> |**Nombre**:<br />unManagedidsbizmgmtcannotdisableprovision<br />**Hex**:<br />80041d1b<br />**Número**:<br />-2147214053|Se trata de una empresa raíz aprovisionada. Utilice IBizProvision::Disable para deshabilitar esta empresa raíz.|
> |**Nombre**:<br />unManagedidsbizmgmtcannotenablebusiness<br />**Hex**:<br />80041d1c<br />**Número**:<br />-2147214052|Este es un subconjunto de negocio. Utilice IBizMerchant::Enable para habilitar este subconjunto de negocio.|
> |**Nombre**:<br />unManagedidsbizmgmtcannotenableprovision<br />**Hex**:<br />80041d1d<br />**Número**:<br />-2147214051|Se trata de una empresa raíz aprovisionada. Utilice IBizProvision::Enable para habilitar esta empresa raíz.|
> |**Nombre**:<br />unManagedidsbizmgmtcannotmovedefaultuser<br />**Hex**:<br />80041d05<br />**Número**:<br />-2147214075|unManagedidsbizmgmtcannotmovedefaultuser|
> |**Nombre**:<br />unManagedidsbizmgmtcannotreadaccountcontrol<br />**Hex**:<br />80041d2d<br />**Número**:<br />-2147214035|Permisos insuficientes para el usuario especificado de Active Directory. Póngase en contacto con el administrador del sistema.|
> |**Nombre**:<br />unManagedidsbizmgmtcannotremovepartnershipdefaultuser<br />**Hex**:<br />80041d17<br />**Número**:<br />-2147214057|No se pudo quitar el usuario predeterminado de una sociedad.|
> |**Nombre**:<br />unManagedidsbizmgmtcantchangeorgname<br />**Hex**:<br />80041d36<br />**Número**:<br />-2147214026|El nombre de organización no se puede cambiar.|
> |**Nombre**:<br />unManagedidsbizmgmtdefaultusernotinbusiness<br />**Hex**:<br />80041d03<br />**Número**:<br />-2147214077|El usuario predeterminado no está en la empresa.|
> |**Nombre**:<br />unManagedidsbizmgmtdefaultusernotinpartnerbusiness<br />**Hex**:<br />80041d15<br />**Número**:<br />-2147214059|El usuario predeterminado no es de la empresa asociada.|
> |**Nombre**:<br />unManagedidsbizmgmtdefaultusernotinprimarybusiness<br />**Hex**:<br />80041d13<br />**Número**:<br />-2147214061|El usuario predeterminado no es de la empresa principal.|
> |**Nombre**:<br />unManagedidsbizmgmtmissbusinessname<br />**Hex**:<br />80041d00<br />**Número**:<br />-2147214080|Falta inesperadamente el nombre de unidad de negocio.|
> |**Nombre**:<br />unManagedidsbizmgmtmissparentbusiness<br />**Hex**:<br />80041d02<br />**Número**:<br />-2147214078|Falta inesperadamente la empresa primaria.|
> |**Nombre**:<br />unManagedidsbizmgmtmisspartnerbusiness<br />**Hex**:<br />80041d0f<br />**Número**:<br />-2147214065|Falta inesperadamente la empresa asociada de la sociedad.|
> |**Nombre**:<br />unManagedidsbizmgmtmissprimarybusiness<br />**Hex**:<br />80041d0e<br />**Número**:<br />-2147214066|Falta inesperadamente la empresa principal de la sociedad.|
> |**Nombre**:<br />unManagedidsbizmgmtmissuserdomainname<br />**Hex**:<br />80041d01<br />**Número**:<br />-2147214079|Falta de forma inesperada el nombre de dominio del usuario.|
> |**Nombre**:<br />unManagedidsbizmgmtnoparentbusiness<br />**Hex**:<br />80041d29<br />**Número**:<br />-2147214039|La empresa especificada no tiene una empresa primaria.|
> |**Nombre**:<br />unManagedidsbizmgmtpartnershipalreadyexists<br />**Hex**:<br />80041d11<br />**Número**:<br />-2147214063|Ya existe una asociación entre una empresa principal especificada y una empresa asociada.|
> |**Nombre**:<br />unManagedidsbizmgmtpartnershipnotinpendingstatus<br />**Hex**:<br />80041d16<br />**Número**:<br />-2147214058|La asociación se ha aceptado o rechazado.|
> |**Nombre**:<br />unManagedidsbizmgmtprimarysameaspartner<br />**Hex**:<br />80041d10<br />**Número**:<br />-2147214064|La empresa principal es la misma que la empresa asociada.|
> |**Nombre**:<br />unManagedidsbizmgmtusercannotbeownparent<br />**Hex**:<br />80041d06<br />**Número**:<br />-2147214074|El usuario no puede ser su propio usuario primario.|
> |**Nombre**:<br />unManagedidsbizmgmtuserdoesnothaveparent<br />**Hex**:<br />80041d1e<br />**Número**:<br />-2147214050|Este usuario no tiene un usuario principal.|
> |**Nombre**:<br />unManagedidsbizmgmtusersettingsnotcreated<br />**Hex**:<br />80041d2b<br />**Número**:<br />-2147214037|Aún no se ha creado la configuración del usuario especificado.|
> |**Nombre**:<br />unManagedidscalendarinvalidcalendar<br />**Hex**:<br />80044d00<br />**Número**:<br />-2147201792|El calendario no es válido.|
> |**Nombre**:<br />unManagedidscalendarruledoesnotexist<br />**Hex**:<br />80045100<br />**Número**:<br />-2147200768|La regla de calendario no existe.|
> |**Nombre**:<br />unManagedidsCalloutException<br />**Hex**:<br />80045f05<br />**Número**:<br />-2147197179|El código de llamada produce excepciones|
> |**Nombre**:<br />unManagedidscalloutinvalidconfig<br />**Hex**:<br />80045f03<br />**Número**:<br />-2147197181|Configuración de llamada no válida|
> |**Nombre**:<br />unManagedidscalloutinvalidevent<br />**Hex**:<br />80045f04<br />**Número**:<br />-2147197180|Tipo de evento de llamada no válido|
> |**Nombre**:<br />unManagedidscalloutisvabort<br />**Hex**:<br />80045f01<br />**Número**:<br />-2147197183|El código ISV de llamada anuló la operación|
> |**Nombre**:<br />unManagedidscalloutisvexception<br />**Hex**:<br />80045f00<br />**Número**:<br />-2147197184|El código de llamada ISV produce excepciones|
> |**Nombre**:<br />unManagedidscalloutisvstop<br />**Hex**:<br />80045f02<br />**Número**:<br />-2147197182|El código ISV de llamada detuvo la operación|
> |**Nombre**:<br />unManagedidscannotassigntobusiness<br />**Hex**:<br />80040221<br />**Número**:<br />-2147220959|No se puede asignar un objeto a un comerciante.|
> |**Nombre**:<br />unManagedidscannotdeactivatepricelevel<br />**Hex**:<br />80043b04<br />**Número**:<br />-2147206396|El nivel de precio no se puede desactivar porque es el nivel de precio predeterminado de una cuenta, contacto o producto.|
> |**Nombre**:<br />unManagedidscannotdefaultprivateview<br />**Hex**:<br />80040238<br />**Número**:<br />-2147220936|Las vistas privadas no pueden ser predeterminadas.|
> |**Nombre**:<br />unManagedidscannotgrantorrevokeaccesstobusiness<br />**Hex**:<br />8004021e<br />**Número**:<br />-2147220962|No se pueden conceder o revocar derechos de acceso a un vendedor.|
> |**Nombre**:<br />unManagedidscantdisable<br />**Hex**:<br />80044154<br />**Número**:<br />-2147204780|El usuario no se puede deshabilitar porque tiene reglas de flujo de trabajo ejecutándose en su contexto.|
> |**Nombre**:<br />unManagedidscascadeemptylinkerror<br />**Hex**:<br />80045602<br />**Número**:<br />-2147199486|El vínculo de relación está vacío|
> |**Nombre**:<br />unManagedidscascadeinconsistencyerror<br />**Hex**:<br />80045600<br />**Número**:<br />-2147199488|La información del mapa cascada es incoherente.|
> |**Nombre**:<br />unManagedidscascadeundefinedrelationerror<br />**Hex**:<br />80045601<br />**Número**:<br />-2147199487|El tipo de relación no se admite|
> |**Nombre**:<br />unManagedidscascadeunexpectederror<br />**Hex**:<br />80045603<br />**Número**:<br />-2147199485|Error inesperado en la operación en cascada|
> |**Nombre**:<br />unManagedidscommunicationsbadsender<br />**Hex**:<br />80040b01<br />**Número**:<br />-2147218687|Se ha especificado más de un remitente|
> |**Nombre**:<br />unManagedidscommunicationsnoparticipationmask<br />**Hex**:<br />80040b06<br />**Número**:<br />-2147218682|Falta el tipo de participación de una actividad|
> |**Nombre**:<br />unManagedidscommunicationsnopartyaddress<br />**Hex**:<br />80040b00<br />**Número**:<br />-2147218688|La dirección del objeto no se encuentra en la entidad o la entidad está marcada como no apta para recibir correos electrónicos|
> |**Nombre**:<br />unManagedidscommunicationsnorecipients<br />**Hex**:<br />80040b05<br />**Número**:<br />-2147218683|Al menos un usuario del sistema o cola de la organización debe ser un destinatario|
> |**Nombre**:<br />unManagedidscommunicationsnosender<br />**Hex**:<br />80040b02<br />**Número**:<br />-2147218686|No se especificó ninguna dirección de correo electrónico y el usuario autor de la llamada no tiene una dirección de correo electrónico establecida|
> |**Nombre**:<br />unManagedidscommunicationsnosenderaddress<br />**Hex**:<br />80040b08<br />**Número**:<br />-2147218680|El remitente no tiene una dirección de correo electrónico en el registro de la parte|
> |**Nombre**:<br />unManagedidscommunicationstemplateinvalidtemplate<br />**Hex**:<br />80040b07<br />**Número**:<br />-2147218681|La cuerpo de plantilla no es válido.|
> |**Nombre**:<br />unManagedidscontacthaschildopportunities<br />**Hex**:<br />80040512<br />**Número**:<br />-2147220206|El contacto tiene oportunidades secundarias.|
> |**Nombre**:<br />unManagedidscontractaccountmissing<br />**Hex**:<br />80043201<br />**Número**:<br />-2147208703|Es necesaria una uenta para guardar un contrato.|
> |**Nombre**:<br />unManagedidscontractdoesnotexist<br />**Hex**:<br />80043207<br />**Número**:<br />-2147208697|El contrato no existe.|
> |**Nombre**:<br />unManagedidscontractinvalidowner<br />**Hex**:<br />80043212<br />**Número**:<br />-2147208686|El propietario del contrato no es válido.|
> |**Nombre**:<br />unManagedidscontractinvalidstartdateforrenewedcontract<br />**Hex**:<br />80043217<br />**Número**:<br />-2147208681|La fecha de inicio del contrato renovado no puede ser anterior a la fecha de finalización del contrato original.|
> |**Nombre**:<br />unManagedidscontractinvalidtotalallotments<br />**Hex**:<br />80043214<br />**Número**:<br />-2147208684|Totalallotments no es válido.|
> |**Nombre**:<br />unManagedidscontractlineitemdoesnotexist<br />**Hex**:<br />80043208<br />**Número**:<br />-2147208696|El elemento de línea de contrato no existe.|
> |**Nombre**:<br />unManagedidscontractopencasesexist<br />**Hex**:<br />8004320a<br />**Número**:<br />-2147208694|Hay casos abiertos para este elemento de línea de contrato.|
> |**Nombre**:<br />unManagedidscontracttemplateabbreviationexists<br />**Hex**:<br />80043216<br />**Número**:<br />-2147208682|El valor de la abreviatura ya existe.|
> |**Nombre**:<br />unManagedidscontractunexpected<br />**Hex**:<br />80043200<br />**Número**:<br />-2147208704|Se ha producido un error inesperado en contratos.|
> |**Nombre**:<br />unManagedidscpbadpassword<br />**Hex**:<br />80042901<br />**Número**:<br />-2147211007|Contraseña incorrecta para el usuario portal de cliente especificado.|
> |**Nombre**:<br />unManagedidscpdecryptfailed<br />**Hex**:<br />80042903<br />**Número**:<br />-2147211005|Error de descifrado de la contraseña.|
> |**Nombre**:<br />unManagedidscpencryptfailed<br />**Hex**:<br />80042902<br />**Número**:<br />-2147211006|Error de cifrado de la contraseña suministrada.|
> |**Nombre**:<br />unManagedidscpuserdoesnotexist<br />**Hex**:<br />80042900<br />**Número**:<br />-2147211008|El usuario del portal del cliente no existe o la contraseña es incorrecta.|
> |**Nombre**:<br />unManagedidscustomentityalreadyinitialized<br />**Hex**:<br />80045901<br />**Número**:<br />-2147198719|La interfaz de entidad personalizada ya inicializada en este hilo.|
> |**Nombre**:<br />unManagedidscustomentityambiguousrelationship<br />**Hex**:<br />8004590d<br />**Número**:<br />-2147198707|Existe más de una relación entre las entidades solicitadas.|
> |**Nombre**:<br />unManagedidscustomentityexistingloop<br />**Hex**:<br />80045907<br />**Número**:<br />-2147198713|Hay un bucle existente en la base de datos.|
> |**Nombre**:<br />unManagedidscustomentityinvalidchild<br />**Hex**:<br />80045909<br />**Número**:<br />-2147198711|La entidad secundaria suministrada pasada no es válida.|
> |**Nombre**:<br />unManagedidscustomentityinvalidownership<br />**Hex**:<br />80045903<br />**Número**:<br />-2147198717|Máscara de tipo de propiedad de entidad personalizada está establecida incorrectamente.|
> |**Nombre**:<br />unManagedidscustomentityinvalidparent<br />**Hex**:<br />8004590a<br />**Número**:<br />-2147198710|La entidad primaria suministrada pasada no es válida.|
> |**Nombre**:<br />unManagedidscustomentitynameviolation<br />**Hex**:<br />80045900<br />**Número**:<br />-2147198720|Se ha encontrado la entidad suministrada pero no es una entidad personalizada.|
> |**Nombre**:<br />unManagedidscustomentitynorelationship<br />**Hex**:<br />8004590c<br />**Número**:<br />-2147198708|No existe relación entre las entidades solicitadas.|
> |**Nombre**:<br />unManagedidscustomentitynotinitialized<br />**Hex**:<br />80045902<br />**Número**:<br />-2147198718|La interfaz de la entidad personalizada no se inicializó correctamente.|
> |**Nombre**:<br />unManagedidscustomentityparentchildidentical<br />**Hex**:<br />8004590b<br />**Número**:<br />-2147198709|Las entidades primarias y secundarias proporcionadas son iguales.|
> |**Nombre**:<br />unManagedidscustomentitystackoverflow<br />**Hex**:<br />80045905<br />**Número**:<br />-2147198715|Desbordamiento de pila de entidad personalizada MD.|
> |**Nombre**:<br />unManagedidscustomentitystackunderflow<br />**Hex**:<br />80045906<br />**Número**:<br />-2147198714|Subdesbordamiento de pila de entidad personalizada MD.|
> |**Nombre**:<br />unManagedidscustomentitytlsfailure<br />**Hex**:<br />80045904<br />**Número**:<br />-2147198716|Entidad personalizada TLS MD no inicializada.|
> |**Nombre**:<br />unManagedidscustomentitywouldcreateloop<br />**Hex**:<br />80045908<br />**Número**:<br />-2147198712|Esta asociación crearía un bucle en la base de datos.|
> |**Nombre**:<br />unManagedidscustomeraddresstypeinvalid<br />**Hex**:<br />80040514<br />**Número**:<br />-2147220204|Tipo de dirección del cliente no válido.|
> |**Nombre**:<br />unManagedidscustomizationtransformationnotsupported<br />**Hex**:<br />80044700<br />**Número**:<br />-2147203328|No se admite la transformación para este objeto.|
> |**Nombre**:<br />unManagedidsdataaccessunexpected<br />**Hex**:<br />80042300<br />**Número**:<br />-2147212544|Error inesperado al acceder a los datos.  La conexión de la base de datos podría no haberse abierto correctamente.|
> |**Nombre**:<br />unManagedidsdataoutofrange<br />**Hex**:<br />8004022c<br />**Número**:<br />-2147220948|Datos fuera de rango|
> |**Nombre**:<br />unManagedidsevalaborted<br />**Hex**:<br />80042c03<br />**Número**:<br />-2147210237|Evaluación anulada.|
> |**Nombre**:<br />unManagedidsevalallaborted<br />**Hex**:<br />80042c02<br />**Número**:<br />-2147210238|Evaluación anulada y detiene de su posterior procesamiento.|
> |**Nombre**:<br />unManagedidsevalallcompleted<br />**Hex**:<br />80042c0c<br />**Número**:<br />-2147210228|Evaluación completada y detiene de su posterior procesamiento.|
> |**Nombre**:<br />unManagedidsevalassignshouldhave4parameters<br />**Hex**:<br />80042c01<br />**Número**:<br />-2147210239|La acción de asignar debería tener 4 parámetros.|
> |**Nombre**:<br />unManagedidsevalchangetypeerror<br />**Hex**:<br />80042c0d<br />**Número**:<br />-2147210227|Cambie tipo de error.|
> |**Nombre**:<br />unManagedidsevalcompleted<br />**Hex**:<br />80042c04<br />**Número**:<br />-2147210236|Evaluación completada.|
> |**Nombre**:<br />unManagedidsevalcreateshouldhave2parameters<br />**Hex**:<br />80042c3c<br />**Número**:<br />-2147210180|La acción de crear debería tener 2 parámetros.|
> |**Nombre**:<br />unManagedidsevalerrorabsparameter<br />**Hex**:<br />80042c2c<br />**Número**:<br />-2147210196|Error al evaluar un parámetro WFPM_ABS.|
> |**Nombre**:<br />unManagedidsevalerroractivityattachment<br />**Hex**:<br />80042c18<br />**Número**:<br />-2147210216|Error en la conexión de la actividad de acción.|
> |**Nombre**:<br />unManagedidsevalerroraddparameter<br />**Hex**:<br />80042c0f<br />**Número**:<br />-2147210225|Error al evaluar un parámetro WFPM_ADD.|
> |**Nombre**:<br />unManagedidsevalerrorappendtoactivityparty<br />**Hex**:<br />80042c3f<br />**Número**:<br />-2147210177|unManagedidsevalerrorappendtoactivityparty|
> |**Nombre**:<br />unManagedidsevalerrorassign<br />**Hex**:<br />80042c22<br />**Número**:<br />-2147210206|Error en asignación de acción.|
> |**Nombre**:<br />unManagedidsevalerrorbeginwithparameter<br />**Hex**:<br />80042c38<br />**Número**:<br />-2147210184|Error al evaluar un parámetro WFPM_BEGIN_WITH.|
> |**Nombre**:<br />unManagedidsevalerrorbetweenparameter<br />**Hex**:<br />80042c33<br />**Número**:<br />-2147210189|Error al evaluar un parámetro WFPM_BETWEEN.|
> |**Nombre**:<br />unManagedidsevalerrorcontainparameter<br />**Hex**:<br />80042c3a<br />**Número**:<br />-2147210182|Error al evaluar un parámetro WFPM_CONTAIN.|
> |**Nombre**:<br />unManagedidsevalerrorcreate<br />**Hex**:<br />80042c3b<br />**Número**:<br />-2147210181|Error en creación de actualización.|
> |**Nombre**:<br />unManagedidsevalerrorcreateactivity<br />**Hex**:<br />80042c17<br />**Número**:<br />-2147210217|Error en la creación de actividad.|
> |**Nombre**:<br />unManagedidsevalerrorcreateincident<br />**Hex**:<br />80042c1d<br />**Número**:<br />-2147210211|Error en la creación de un incidente.|
> |**Nombre**:<br />unManagedidsevalerrorcreatenote<br />**Hex**:<br />80042c1b<br />**Número**:<br />-2147210213|Error en la creación de una nota.|
> |**Nombre**:<br />unManagedidsevalerrordividedbyzero<br />**Hex**:<br />80042c16<br />**Número**:<br />-2147210218|Dividido por cero.|
> |**Nombre**:<br />unManagedidsevalerrordivisionparameter<br />**Hex**:<br />80042c13<br />**Número**:<br />-2147210221|Error al evaluar un parámetro WFPM_DIVISION.|
> |**Nombre**:<br />unManagedidsevalerrordivisionparameters<br />**Hex**:<br />80042c12<br />**Número**:<br />-2147210222|Los parámetros de división solo pueden tener dos subparámetros.|
> |**Nombre**:<br />unManagedidsevalerroremailtemplate<br />**Hex**:<br />80042c21<br />**Número**:<br />-2147210207|Error en la acción de plantilla de correo electrónico.|
> |**Nombre**:<br />unManagedidsevalerrorendwithparameter<br />**Hex**:<br />80042c39<br />**Número**:<br />-2147210183|Error al evaluar un parámetro WFPM_END_WITH.|
> |**Nombre**:<br />unManagedidsevalerroreqparameter<br />**Hex**:<br />80042c31<br />**Número**:<br />-2147210191|Error al evaluar un parámetro WFPM_EQ.|
> |**Nombre**:<br />unManagedidsevalerrorexec<br />**Hex**:<br />80042c27<br />**Número**:<br />-2147210201|Error en la acción exec.|
> |**Nombre**:<br />unManagedidsevalerrorformatbooleanparameter<br />**Hex**:<br />80042c45<br />**Número**:<br />-2147210171|Se produce un error cuando se evalúa el parámetro WFPM_FORMAT_BOOLEAN.|
> |**Nombre**:<br />unManagedidsevalerrorformatdatetimeparameter<br />**Hex**:<br />80042c44<br />**Número**:<br />-2147210172|Se produce un error cuando se evalúa el parámetro WFPM_FORMAT_DATETIME.|
> |**Nombre**:<br />unManagedidsevalerrorformatdecimalparameter<br />**Hex**:<br />80042c4a<br />**Número**:<br />-2147210166|Se produce un error cuando se evalúa el parámetro WFPM_FORMAT_DECIMAL.|
> |**Nombre**:<br />unManagedidsevalerrorformatintegerparameter<br />**Hex**:<br />80042c49<br />**Número**:<br />-2147210167|Se produce un error cuando se evalúa el parámetro WFPM_FORMAT_INTEGER.|
> |**Nombre**:<br />unManagedidsevalerrorformatlookupparameter<br />**Hex**:<br />80042c4c<br />**Número**:<br />-2147210164|Se produce un error cuando se evalúa el parámetro WFPM_FORMAT_LOOKUP.|
> |**Nombre**:<br />unManagedidsevalerrorformatpicklistparameter<br />**Hex**:<br />80042c46<br />**Número**:<br />-2147210170|Se produce un error cuando se evalúa el parámetro WFPM_FORMAT_PICKLIST.|
> |**Nombre**:<br />unManagedidsevalerrorformattimezonecodeparameter<br />**Hex**:<br />80042c4b<br />**Número**:<br />-2147210165|unManagedidsevalerrorformattimezonecodeparameter|
> |**Nombre**:<br />unManagedidsevalerrorgeqparameter<br />**Hex**:<br />80042c2e<br />**Número**:<br />-2147210194|Error al evaluar un parámetro WFPM_GEQ.|
> |**Nombre**:<br />unManagedidsevalerrorgtparameter<br />**Hex**:<br />80042c2d<br />**Número**:<br />-2147210195|Error al evaluar un parámetro WFPM_GT.|
> |**Nombre**:<br />unManagedidsevalerrorhalt<br />**Hex**:<br />80042c28<br />**Número**:<br />-2147210200|Error en la acción de detención.|
> |**Nombre**:<br />unManagedidsevalerrorhandleactivity<br />**Hex**:<br />80042c19<br />**Número**:<br />-2147210215|Error en la acción de controlar una actividad.|
> |**Nombre**:<br />unManagedidsevalerrorhandleincident<br />**Hex**:<br />80042c1e<br />**Número**:<br />-2147210210|Error en la acción de controlar un incidente.|
> |**Nombre**:<br />unManagedidsevalerrorincidentqueue<br />**Hex**:<br />80042c29<br />**Número**:<br />-2147210199|Error en la evaluación de INCIDENT_QUEUE.|
> |**Nombre**:<br />unManagedidsevalerrorinlistparameter<br />**Hex**:<br />80042c42<br />**Número**:<br />-2147210174|unManagedidsevalerrorinlistparameter|
> |**Nombre**:<br />unManagedidsevalerrorinparameter<br />**Hex**:<br />80042c34<br />**Número**:<br />-2147210188|Error al evaluar un parámetro WFPM_IN.|
> |**Nombre**:<br />unManagedidsevalerrorinvalidparameter<br />**Hex**:<br />80042c2b<br />**Número**:<br />-2147210197|Parámetro no válido.|
> |**Nombre**:<br />unManagedidsevalerrorinvalidrecipient<br />**Hex**:<br />80042c35<br />**Número**:<br />-2147210187|Destinatario de correo electrónico no válido.|
> |**Nombre**:<br />unManagedidsevalerrorisnulllistparameter<br />**Hex**:<br />80042c43<br />**Número**:<br />-2147210173|unManagedidsevalerrorisnulllistparameter|
> |**Nombre**:<br />unManagedidsevalerrorleqparameter<br />**Hex**:<br />80042c30<br />**Número**:<br />-2147210192|Error al evaluar un parámetro WFPM_LEQ.|
> |**Nombre**:<br />unManagedidsevalerrorltparameter<br />**Hex**:<br />80042c2f<br />**Número**:<br />-2147210193|Error al evaluar un parámetro WFPM_LT.|
> |**Nombre**:<br />unManagedidsevalerrormodulusparameter<br />**Hex**:<br />80042c15<br />**Número**:<br />-2147210219|Error al evaluar un parámetro WFPM_MODULUR.|
> |**Nombre**:<br />unManagedidsevalerrormodulusparameters<br />**Hex**:<br />80042c14<br />**Número**:<br />-2147210220|Los parámetros de Modulus solo pueden tener dos subparámetros.|
> |**Nombre**:<br />unManagedidsevalerrormultiplicationparameter<br />**Hex**:<br />80042c11<br />**Número**:<br />-2147210223|Error al evaluar un parámetro WFPM_MULTIPLICATION.|
> |**Nombre**:<br />unManagedidsevalerrorneqparameter<br />**Hex**:<br />80042c32<br />**Número**:<br />-2147210190|Error al evaluar un parámetro WFPM_NEQ.|
> |**Nombre**:<br />unManagedidsevalerrornoteattachment<br />**Hex**:<br />80042c1c<br />**Número**:<br />-2147210212|Error en la creación de adjuntar una nota.|
> |**Nombre**:<br />unManagedidsevalerrorobjecttype<br />**Hex**:<br />80042c48<br />**Número**:<br />-2147210168|Se produce un error cuando se evalúa el parámetro WFPM_GetObjectType.|
> |**Nombre**:<br />unManagedidsevalerrorposturl<br />**Hex**:<br />80042c26<br />**Número**:<br />-2147210202|Error en acción de posturl.|
> |**Nombre**:<br />unManagedidsevalerrorqueueidparameter<br />**Hex**:<br />80042c47<br />**Número**:<br />-2147210169|unManagedidsevalerrorqueueidparameter|
> |**Nombre**:<br />unManagedidsevalerrorremovefromactivityparty<br />**Hex**:<br />80042c40<br />**Número**:<br />-2147210176|unManagedidsevalerrorremovefromactivityparty|
> |**Nombre**:<br />unManagedidsevalerrorroute<br />**Hex**:<br />80042c24<br />**Número**:<br />-2147210204|Error en la acción de ruta.|
> |**Nombre**:<br />unManagedidsevalerrorsendemail<br />**Hex**:<br />80042c20<br />**Número**:<br />-2147210208|Error en la acción envío de correo electrónico.|
> |**Nombre**:<br />unManagedidsevalerrorsetactivityparty<br />**Hex**:<br />80042c41<br />**Número**:<br />-2147210175|unManagedidsevalerrorsetactivityparty|
> |**Nombre**:<br />unManagedidsevalerrorsetstate<br />**Hex**:<br />80042c25<br />**Número**:<br />-2147210203|Error en acción de establecer estado.|
> |**Nombre**:<br />unManagedidsevalerrorstrlenparameter<br />**Hex**:<br />80042c37<br />**Número**:<br />-2147210185|Error al evaluar un parámetro WFPM_STRLEN.|
> |**Nombre**:<br />unManagedidsevalerrorsubstrparameter<br />**Hex**:<br />80042c36<br />**Número**:<br />-2147210186|Error al evaluar un parámetro WFPM_SUBSTR.|
> |**Nombre**:<br />unManagedidsevalerrorsubtractionparameter<br />**Hex**:<br />80042c10<br />**Número**:<br />-2147210224|Error al evaluar un parámetro WFPM_SUBTRACTION.|
> |**Nombre**:<br />unManagedidsevalerrorunhandleactivity<br />**Hex**:<br />80042c1a<br />**Número**:<br />-2147210214|Error en la acción de una actividad no controlada.|
> |**Nombre**:<br />unManagedidsevalerrorunhandleincident<br />**Hex**:<br />80042c1f<br />**Número**:<br />-2147210209|Error en la acción de un incidente no controlado.|
> |**Nombre**:<br />unManagedidsevalerrorupdate<br />**Hex**:<br />80042c23<br />**Número**:<br />-2147210205|Error en acción actualización.|
> |**Nombre**:<br />unManagedidsevalgenericerror<br />**Hex**:<br />80042c2a<br />**Número**:<br />-2147210198|Error de evaluación.|
> |**Nombre**:<br />unManagedidsevalmetabaseattributenotfound<br />**Hex**:<br />80042c08<br />**Número**:<br />-2147210232|El atributo metabase especificado no existe.|
> |**Nombre**:<br />unManagedidsevalmetabaseattributenotmatchquery<br />**Hex**:<br />80042c0b<br />**Número**:<br />-2147210229|El refattributeid especificado no coincide con la consulta para un parámetro WFPM_SELECT.|
> |**Nombre**:<br />unManagedidsevalmetabaseentitycompoundkeys<br />**Hex**:<br />80042c07<br />**Número**:<br />-2147210233|El objeto metabase especificado tiene claves compuestas. No admitimos entidades de claves compuestas aún.|
> |**Nombre**:<br />unManagedidsevalmetabaseentitynotmatchquery<br />**Hex**:<br />80042c0a<br />**Número**:<br />-2147210230|El refentityid especificado no coincide con la consulta para un parámetro WFPM_SELECT.|
> |**Nombre**:<br />unManagedidsevalmissselectquery<br />**Hex**:<br />80042c0e<br />**Número**:<br />-2147210226|Falta la consulta de subparámetro en un parámetro seleccionado.|
> |**Nombre**:<br />unManagedidsevalobjectnotfound<br />**Hex**:<br />80042c05<br />**Número**:<br />-2147210235|El objeto solicitado no existe.|
> |**Nombre**:<br />unManagedidsevalpropertyisnull<br />**Hex**:<br />80042c09<br />**Número**:<br />-2147210231|No se ha establecido la propiedad necesaria del objeto.|
> |**Nombre**:<br />unManagedidsevalpropertynotfound<br />**Hex**:<br />80042c06<br />**Número**:<br />-2147210234|No se encontró la propiedad necesaria del objeto.|
> |**Nombre**:<br />unManagedidsevaltimererrorcalculatescheduletime<br />**Hex**:<br />80042c3e<br />**Número**:<br />-2147210178|No se puede calcular el tiempo de programación para la acción de temporizador.|
> |**Nombre**:<br />unManagedidsevaltimerinvalidparameternumber<br />**Hex**:<br />80042c3d<br />**Número**:<br />-2147210179|Parámetros no válidos para la acción de temporizador.|
> |**Nombre**:<br />unManagedidsevalupdateshouldhave3parameters<br />**Hex**:<br />80042c00<br />**Número**:<br />-2147210240|La acción de actalizar debería tener 3 parámetros.|
> |**Nombre**:<br />unManagedidsfailureinittoken<br />**Hex**:<br />8004020f<br />**Número**:<br />-2147220977|Error en la obtención de token de usuario.|
> |**Nombre**:<br />unManagedidsfetchbetweentext<br />**Hex**:<br />80044153<br />**Número**:<br />-2147204781|Los operadores entre, no-entre, en y no no se admiten en los atributos de tipo texto o ntext.|
> |**Nombre**:<br />unManagedidsfulltextoperationfailed<br />**Hex**:<br />80043e06<br />**Número**:<br />-2147205626|Operación de texto completo da error.|
> |**Nombre**:<br />unManagedidsincidentassociatedactivitycorrupted<br />**Hex**:<br />80044405<br />**Número**:<br />-2147204091|La actividad asociada a este caso está dañada.|
> |**Nombre**:<br />unManagedidsincidentcannotclose<br />**Hex**:<br />8004440a<br />**Número**:<br />-2147204086|No se puede cerrar el incidente porque hay actividades abiertas para este incidente.|
> |**Nombre**:<br />unManagedidsincidentcontractdetaildoesnotmatchcontract<br />**Hex**:<br />80044402<br />**Número**:<br />-2147204094|El elemento de línea de contrato no figura en el contrato especificado.|
> |**Nombre**:<br />unManagedidsincidentinvalidactivitytypecode<br />**Hex**:<br />80044406<br />**Número**:<br />-2147204090|El activitytypecode es incorrecto.|
> |**Nombre**:<br />unManagedidsincidentinvalidstate<br />**Hex**:<br />80044404<br />**Número**:<br />-2147204092|El estado de incidente no es válido.|
> |**Nombre**:<br />unManagedidsincidentmissingactivityobjecttype<br />**Hex**:<br />80044408<br />**Número**:<br />-2147204088|Falta el código de tipo de objeto.|
> |**Nombre**:<br />unManagedidsincidentnullactivitytypecode<br />**Hex**:<br />80044407<br />**Número**:<br />-2147204089|El activitytypecode no puede ser NULO.|
> |**Nombre**:<br />unManagedidsincidentparentaccountandparentcontactnotpresent<br />**Hex**:<br />80044410<br />**Número**:<br />-2147204080|Debe especificar una cuenta primaria o un contacto primario.|
> |**Nombre**:<br />unManagedidsincidentparentaccountandparentcontactpresent<br />**Hex**:<br />8004440f<br />**Número**:<br />-2147204081|Puede especificar un contacto primario o cuenta, pero no ambos.|
> |**Nombre**:<br />unManagedidsinvalidassociation<br />**Hex**:<br />80040211<br />**Número**:<br />-2147220975|Asociación no válida|
> |**Nombre**:<br />unManagedidsinvalidbusinessid<br />**Hex**:<br />80040209<br />**Número**:<br />-2147220983|Id. de empresa no válido.|
> |**Nombre**:<br />unManagedidsinvaliditemid<br />**Hex**:<br />8004020b<br />**Número**:<br />-2147220981|Id. de elemento no válido|
> |**Nombre**:<br />unManagedidsinvalidorgid<br />**Hex**:<br />8004020a<br />**Número**:<br />-2147220982|Id. de organización no válido|
> |**Nombre**:<br />unManagedidsinvalidowninguser<br />**Hex**:<br />80040212<br />**Número**:<br />-2147220974|El elemento no tiene usuario propietario.|
> |**Nombre**:<br />unManagedidsinvalidteamid<br />**Hex**:<br />80040208<br />**Número**:<br />-2147220984|Id. de equipo no válido|
> |**Nombre**:<br />unManagedidsinvaliduserid<br />**Hex**:<br />80040207<br />**Número**:<br />-2147220985|El identificador de usuario falta o no es válido.|
> |**Nombre**:<br />unManagedidsinvaliduseridorbusinessidorusersbusinessinvalid<br />**Hex**:<br />8004021d<br />**Número**:<br />-2147220963|Uno de los siguientes casos se ha producido: Id. de usuario no válido, Id. de empresa no válido o el usuario no pertenece a la empresa.|
> |**Nombre**:<br />unManagedidsinvalidvisibility<br />**Hex**:<br />8004020e<br />**Número**:<br />-2147220978|Visibilidad no válida.|
> |**Nombre**:<br />unManagedidsinvalidvisibilitymodificationaccess<br />**Hex**:<br />80040213<br />**Número**:<br />-2147220973|El usuario no tiene acceso para modificar la visibilidad de este elemento.|
> |**Nombre**:<br />unManagedidsinvoicecloseapideprecated<br />**Hex**:<br />80043b25<br />**Número**:<br />-2147206363|La API de cierre de factura está obsoleta. Se ha reemplazado por el pago y cancelado la API.|
> |**Nombre**:<br />unManagedidsjournalinginvalideventtype<br />**Hex**:<br />80040803<br />**Número**:<br />-2147219453|Tipo de evento no válido.|
> |**Nombre**:<br />unManagedidsjournalingmissingaccountid<br />**Hex**:<br />80040806<br />**Número**:<br />-2147219450|Falta el id. de cuenta.|
> |**Nombre**:<br />unManagedidsjournalingmissingcontactid<br />**Hex**:<br />80040808<br />**Número**:<br />-2147219448|Falta el id. de contacto|
> |**Nombre**:<br />unManagedidsjournalingmissingeventdirection<br />**Hex**:<br />80040802<br />**Número**:<br />-2147219454|Falta el código de dirección del evento.|
> |**Nombre**:<br />unManagedidsjournalingmissingeventtype<br />**Hex**:<br />80040804<br />**Número**:<br />-2147219452|Falta el tipo de evento.|
> |**Nombre**:<br />unManagedidsjournalingmissingincidentid<br />**Hex**:<br />80040809<br />**Número**:<br />-2147219447|Falta el Id. de incidente|
> |**Nombre**:<br />unManagedidsjournalingmissingleadid<br />**Hex**:<br />80040805<br />**Número**:<br />-2147219451|Falta el id. de cliente potencial.|
> |**Nombre**:<br />unManagedidsjournalingmissingopportunityid<br />**Hex**:<br />80040807<br />**Número**:<br />-2147219449|Falta el identificador de oportunidad.|
> |**Nombre**:<br />unManagedidsjournalingunsupportedobjecttype<br />**Hex**:<br />80040801<br />**Número**:<br />-2147219455|Se ha pasado un tipo de objeto no admitido en la operación.|
> |**Nombre**:<br />unManagedidsleaddoesnotexist<br />**Hex**:<br />80040501<br />**Número**:<br />-2147220223|El cliente potencial no existe.|
> |**Nombre**:<br />unManagedidsleadnoparent<br />**Hex**:<br />8004050b<br />**Número**:<br />-2147220213|El cliente potencial no tiene un primario.|
> |**Nombre**:<br />unManagedidsleadnotassigned<br />**Hex**:<br />8004050c<br />**Número**:<br />-2147220212|No se ha asignado el cliente potencial.|
> |**Nombre**:<br />unManagedidsleadnotassignedtocaller<br />**Hex**:<br />80040513<br />**Número**:<br />-2147220205|El cliente potencial no se está asignando al autor de la llamada para su aceptación.|
> |**Nombre**:<br />unManagedidsleadoneaccount<br />**Hex**:<br />80040510<br />**Número**:<br />-2147220208|Un cliente potencial se puede asociar únicamente con una cuenta.|
> |**Nombre**:<br />unManagedidsleadusercannotreject<br />**Hex**:<br />8004050d<br />**Número**:<br />-2147220211|El usuario no tiene permiso para rechazar un cliente potencial, por lo que no se puede asignar a los clientes potenciales para su aceptación.|
> |**Nombre**:<br />unManagedidsmergedifferentbizorgerror<br />**Hex**:<br />80045303<br />**Número**:<br />-2147200253|La combinación no se puede realizar en las entidades de distitna entidad de negocios.|
> |**Nombre**:<br />unManagedidsmetadatanoentity<br />**Hex**:<br />80040e00<br />**Número**:<br />-2147217920|La entidad especificada no existe|
> |**Nombre**:<br />unManagedidsmetadatanorelationship<br />**Hex**:<br />80040e02<br />**Número**:<br />-2147217918|La relación no existe|
> |**Nombre**:<br />unManagedidsnorelationship<br />**Hex**:<br />80040236<br />**Número**:<br />-2147220938|No hay relación entre los objetos especificados.|
> |**Nombre**:<br />unManagedidsnotesalreadyattached<br />**Hex**:<br />80041701<br />**Número**:<br />-2147215615|La nota especificada ya está asociada a un objeto.|
> |**Nombre**:<br />unManagedidsnotesloopbeingcreated<br />**Hex**:<br />80041703<br />**Número**:<br />-2147215613|La creación de esta asociación jerárquica crearía un bucle en la jerarquía de anotaciones.|
> |**Nombre**:<br />unManagedidsnotesloopexists<br />**Hex**:<br />80041702<br />**Número**:<br />-2147215614|Existe un bucle en la jerarquía de la anotación.|
> |**Nombre**:<br />unManagedidsnotesnoattachment<br />**Hex**:<br />80041704<br />**Número**:<br />-2147215612|La nota especificada no tiene anexos.|
> |**Nombre**:<br />unManagedidsnotesnotedoesnotexist<br />**Hex**:<br />80041700<br />**Número**:<br />-2147215616|La nota especificada no existe.|
> |**Nombre**:<br />unManagedidsopportunitydoesnotexist<br />**Hex**:<br />80040500<br />**Número**:<br />-2147220224|La oportunidad no existe.|
> |**Nombre**:<br />unManagedidsopportunityinvalidparent<br />**Hex**:<br />80040504<br />**Número**:<br />-2147220220|El primario de una oportunidad debe ser una cuenta o contacto.|
> |**Nombre**:<br />unManagedidsopportunitymissingparent<br />**Hex**:<br />80040505<br />**Número**:<br />-2147220219|Falta la oportunidad primaria.|
> |**Nombre**:<br />unManagedidsopportunityoneaccount<br />**Hex**:<br />8004050e<br />**Número**:<br />-2147220210|Una oportunidad se puede asociar únicamente con una cuenta.|
> |**Nombre**:<br />unManagedidsopportunityorphan<br />**Hex**:<br />8004050f<br />**Número**:<br />-2147220209|Al quitar esta asociación la oportunidad pasará a ser huérfana.|
> |**Nombre**:<br />unManagedidsoutofmemory<br />**Hex**:<br />80040222<br />**Número**:<br />-2147220958|Memoria insuficiente.|
> |**Nombre**:<br />unManagedidsownernotenabled<br />**Hex**:<br />8004022b<br />**Número**:<br />-2147220949|Se ha deshabilitado el propietario especificado.|
> |**Nombre**:<br />unManagedidspresentuseridandteamid<br />**Hex**:<br />8004021c<br />**Número**:<br />-2147220964|El Id. de usuario y el identificador de equipo están presentes. Solo una debe estar presente.|
> |**Nombre**:<br />unManagedidspropbagattributealreadyset<br />**Hex**:<br />8004203f<br />**Número**:<br />-2147213249|Ya se ha configurado uno de los atributos pasados|
> |**Nombre**:<br />unManagedidspropbagattributenotnullable<br />**Hex**:<br />8004203e<br />**Número**:<br />-2147213250|Uno de los atributos pasados no puede ser NULL|
> |**Nombre**:<br />unManagedidspropbagcolloutofrange<br />**Hex**:<br />8004201e<br />**Número**:<br />-2147213282|El índice de contenedores de la recopilación estaba fuera del intervalo.|
> |**Nombre**:<br />unManagedidspropbagnointerface<br />**Hex**:<br />80042001<br />**Número**:<br />-2147213311|No se encontró la interfaz de contenedor de propiedades.|
> |**Nombre**:<br />unManagedidspropbagnullproperty<br />**Hex**:<br />80042002<br />**Número**:<br />-2147213310|La propiedad especificada fue nula en el contenedor de propiedades.|
> |**Nombre**:<br />unManagedidspropbagpropertynotfound<br />**Hex**:<br />80042000<br />**Número**:<br />-2147213312|No se encontró la propiedad especificada en el contenedor de propiedades.|
> |**Nombre**:<br />unManagedidsqueuemissingbusinessunitid<br />**Hex**:<br />80043e03<br />**Número**:<br />-2147205629|Falta el businessunitid.|
> |**Nombre**:<br />unManagedidsqueueorganizationidnotmatch<br />**Hex**:<br />80043e04<br />**Número**:<br />-2147205628|Identificador de la organización del llamador no coincide con el Identificador de la organización de unidad de negocio.|
> |**Nombre**:<br />unManagedidsrcsyncfilternoaccess<br />**Hex**:<br />8004410f<br />**Número**:<br />-2147204849|No se puede desconectar: faltan derechos de acceso la entidad requerida.|
> |**Nombre**:<br />unManagedidsrcsyncinvalidfiltererror<br />**Hex**:<br />8004410d<br />**Número**:<br />-2147204851|Filtro especificado no válido.|
> |**Nombre**:<br />unManagedidsrcsyncinvalidsubscription<br />**Hex**:<br />80044109<br />**Número**:<br />-2147204855|La suscripción especificada no existe.|
> |**Nombre**:<br />unManagedidsrcsyncinvalidsynctime<br />**Hex**:<br />80044100<br />**Número**:<br />-2147204864|El tiempo de sincronización especificado no es válido.  Los tiempos de sincronización no deben ser anteriores a los que devueltos por la sincronización anterior. Reinicialice la suscripción.|
> |**Nombre**:<br />unManagedidsrcsyncmethodnone<br />**Hex**:<br />80044114<br />**Número**:<br />-2147204844|Las tareas de sincronización no se pueden realizar en este equipo porque el método de sincronización se estableció en Ninguno.|
> |**Nombre**:<br />unManagedidsrcsyncmsxmlfailed<br />**Hex**:<br />80044101<br />**Número**:<br />-2147204863|unManagedidsrcsyncmsxmlfailed|
> |**Nombre**:<br />unManagedidsrcsyncnoclient<br />**Hex**:<br />80044113<br />**Número**:<br />-2147204845|El cliente no existe.|
> |**Nombre**:<br />unManagedidsrcsyncnoprimary<br />**Hex**:<br />80044112<br />**Número**:<br />-2147204846|No existe cliente principal.|
> |**Nombre**:<br />unManagedidsrcsyncnotprimary<br />**Hex**:<br />80044111<br />**Número**:<br />-2147204847|No se puede sincronizar: no es el cliente OutlookSync principal.|
> |**Nombre**:<br />unManagedidsrcsyncsoapconnfailed<br />**Hex**:<br />80044103<br />**Número**:<br />-2147204861|unManagedidsrcsyncsoapconnfailed|
> |**Nombre**:<br />unManagedidsrcsyncsoapfaulterror<br />**Hex**:<br />80044106<br />**Número**:<br />-2147204858|unManagedidsrcsyncsoapfaulterror|
> |**Nombre**:<br />unManagedidsrcsyncsoapgenfailed<br />**Hex**:<br />80044102<br />**Número**:<br />-2147204862|unManagedidsrcsyncsoapgenfailed|
> |**Nombre**:<br />unManagedidsrcsyncsoapparseerror<br />**Hex**:<br />80044108<br />**Número**:<br />-2147204856|unManagedidsrcsyncsoapparseerror|
> |**Nombre**:<br />unManagedidsrcsyncsoapreaderror<br />**Hex**:<br />80044107<br />**Número**:<br />-2147204857|unManagedidsrcsyncsoapreaderror|
> |**Nombre**:<br />unManagedidsrcsyncsoapsendfailed<br />**Hex**:<br />80044104<br />**Número**:<br />-2147204860|unManagedidsrcsyncsoapsendfailed|
> |**Nombre**:<br />unManagedidsrcsyncsoapservererror<br />**Hex**:<br />80044105<br />**Número**:<br />-2147204859|unManagedidsrcsyncsoapservererror|
> |**Nombre**:<br />unManagedidsrcsyncsqlgenericerror<br />**Hex**:<br />80044110<br />**Número**:<br />-2147204848|unManagedidsrcsyncsqlgenericerror|
> |**Nombre**:<br />unManagedidsrcsyncsqlpausederror<br />**Hex**:<br />8004410c<br />**Número**:<br />-2147204852|unManagedidsrcsyncsqlpausederror|
> |**Nombre**:<br />unManagedidsrcsyncsqlstoppederror<br />**Hex**:<br />8004410b<br />**Número**:<br />-2147204853|unManagedidsrcsyncsqlstoppederror|
> |**Nombre**:<br />unManagedidsrcsyncsubscriptionowner<br />**Hex**:<br />8004410a<br />**Número**:<br />-2147204854|El id. del autor de la llamada no coincide con el id. del propietario de la suscripción. Sólo los propietarios de las suscripciones pueden realizar operaciones en ellas.|
> |**Nombre**:<br />unManagedidsrolesdeletenonparentrole<br />**Hex**:<br />8004140c<br />**Número**:<br />-2147216372|No se puede eliminar un rol que se hereda de una empresa primaria.|
> |**Nombre**:<br />unManagedidsrolesinvalidroledata<br />**Hex**:<br />80041400<br />**Número**:<br />-2147216384|Los datos de rol no son válidos.|
> |**Nombre**:<br />unManagedidsrolesinvalidroleid<br />**Hex**:<br />80041401<br />**Número**:<br />-2147216383|Identificador de rol no válido.|
> |**Nombre**:<br />unManagedidsrolesinvalidrolename<br />**Hex**:<br />8004140a<br />**Número**:<br />-2147216374|El nombre de rol no es válido.|
> |**Nombre**:<br />unManagedidsrolesinvalidtemplateid<br />**Hex**:<br />80041404<br />**Número**:<br />-2147216380|Id. de plantilla de rol no válido.|
> |**Nombre**:<br />unManagedidsrolesmissbusinessid<br />**Hex**:<br />80041406<br />**Número**:<br />-2147216378|Falta inesperadamente el identificador de la unidad de negocio del rol.|
> |**Nombre**:<br />unManagedidsrolesmissprivid<br />**Hex**:<br />80041408<br />**Número**:<br />-2147216376|El identificador de privilegio falta inesperadamente.|
> |**Nombre**:<br />unManagedidsrolesmissroleid<br />**Hex**:<br />80041405<br />**Número**:<br />-2147216379|El identificador de rol falta inesperadamente.|
> |**Nombre**:<br />unManagedidsrolesmissrolename<br />**Hex**:<br />80041407<br />**Número**:<br />-2147216377|El nombre de rol falta inesperadamente.|
> |**Nombre**:<br />unManagedidsrolesroledoesnotexist<br />**Hex**:<br />80041402<br />**Número**:<br />-2147216382|El rol especificado no existe.|
> |**Nombre**:<br />unManagedidsrspropbagdbinfoalreadyset<br />**Hex**:<br />8004203d<br />**Número**:<br />-2147213251|La información de la base de datos para el contenedor de propiedades del conjunto de registro ya se ha establecido.|
> |**Nombre**:<br />unManagedidsrspropbagdbinfonotset<br />**Hex**:<br />8004203c<br />**Número**:<br />-2147213252|La información de la base de datos para el contenedor de propiedades del conjunto de registro no se ha establecido.|
> |**Nombre**:<br />unManagedidssalespeopleduplicatecalendarfound<br />**Hex**:<br />80043802<br />**Número**:<br />-2147207166|Calendarios fiscales duplicados encontrados para este comercial/año|
> |**Nombre**:<br />unManagedidssalespeopleinvalidfiscalcalendartype<br />**Hex**:<br />80043808<br />**Número**:<br />-2147207160|Tipo de calendario fiscal no válido|
> |**Nombre**:<br />unManagedidssalespeopleinvalidfiscalperiodindex<br />**Hex**:<br />80043807<br />**Número**:<br />-2147207161|Índice de período fiscal no válido|
> |**Nombre**:<br />unManagedidssalespeopleinvalidterritoryobjecttype<br />**Hex**:<br />80043804<br />**Número**:<br />-2147207164|No se pueden recuperar zonas de ventas por este tipo de objeto|
> |**Nombre**:<br />unManagedidssqlerror<br />**Hex**:<br />80044150<br />**Número**:<br />-2147204784|Error genérico de SQL.|
> |**Nombre**:<br />unManagedidssqltimeouterror<br />**Hex**:<br />80044151<br />**Número**:<br />-2147204783|Tiempo de espera SQL agotado.|
> |**Nombre**:<br />unManagedidsstatedoesnotexist<br />**Hex**:<br />80043af9<br />**Número**:<br />-2147206407|El estado no es válido para este objeto.|
> |**Nombre**:<br />unManagedidsusernotenabled<br />**Hex**:<br />80040225<br />**Número**:<br />-2147220955|El usuario especificado está deshabilitado o no es un miembro de ninguna unidad de negocio.|
> |**Nombre**:<br />unManagedidsviewisnotsharable<br />**Hex**:<br />80040232<br />**Número**:<br />-2147220942|La vista no se puede compartir.|
> |**Nombre**:<br />unManagedidsxmlinvalidcollectionname<br />**Hex**:<br />80041a03<br />**Número**:<br />-2147214845|El nombre de colección especificado es incorrecto|
> |**Nombre**:<br />unManagedidsxmlinvalidcreate<br />**Hex**:<br />80041a01<br />**Número**:<br />-2147214847|Se especificó un campo no válido para una operación de creación.|
> |**Nombre**:<br />unManagedidsxmlinvalidentityattributes<br />**Hex**:<br />80041a06<br />**Número**:<br />-2147214842|Atributos no válidos|
> |**Nombre**:<br />unManagedidsxmlinvalidentityname<br />**Hex**:<br />80041a00<br />**Número**:<br />-2147214848|El nombre de entidad especificado no es correcto|
> |**Nombre**:<br />unManagedidsxmlinvalidfield<br />**Hex**:<br />80041a07<br />**Número**:<br />-2147214841|Se pasó un valor no válido para un campo|
> |**Nombre**:<br />unManagedidsxmlinvalidread<br />**Hex**:<br />80041a08<br />**Número**:<br />-2147214840|Se especificó un campo no válido para lectura.|
> |**Nombre**:<br />unManagedidsxmlinvalidupdate<br />**Hex**:<br />80041a02<br />**Número**:<br />-2147214846|Se especificó un campo no válido para una actualización.|
> |**Nombre**:<br />unManagedidsxmlparseerror<br />**Hex**:<br />80041a04<br />**Número**:<br />-2147214844|Se encontró un error de análisis en el código XML.|
> |**Nombre**:<br />unManagedidsxmlunexpected<br />**Hex**:<br />80041a05<br />**Número**:<br />-2147214843|Se ha producido un error inesperado|
> |**Nombre**:<br />unManagedinvalddbtimefield<br />**Hex**:<br />800404d9<br />**Número**:<br />-2147220263|La plataforma no puede administrar los campos dbtime.|
> |**Nombre**:<br />unManagedinvalidargumentsforcondition<br />**Hex**:<br />800404b7<br />**Número**:<br />-2147220297|Se ha proporcionado un número no válido de argumentos a una condición.|
> |**Nombre**:<br />unManagedinvalidbinaryfield<br />**Hex**:<br />800404dc<br />**Número**:<br />-2147220260|La plataforma no puede administrar los campos binarios.|
> |**Nombre**:<br />unManagedinvalidbusinessunitid<br />**Hex**:<br />800404a7<br />**Número**:<br />-2147220313|El businessunitid falta o no es válido.|
> |**Nombre**:<br />unManagedinvalidcharacterdataforaggregate<br />**Hex**:<br />800404de<br />**Número**:<br />-2147220258|Los datos de caracteres no son válidos al borrar un agregado.|
> |**Nombre**:<br />unManagedinvalidcountvalue<br />**Hex**:<br />800404c1<br />**Número**:<br />-2147220287|El valor de recuento falta o no es válido.|
> |**Nombre**:<br />unManagedinvaliddbdatefield<br />**Hex**:<br />800404da<br />**Número**:<br />-2147220262|La plataforma no puede administrar los campos dbdate.|
> |**Nombre**:<br />unManagedinvaliddynamicparameteraccessor<br />**Hex**:<br />800404d5<br />**Número**:<br />-2147220267|SetParam no ha podido procesar el parámetro DynamicParameterAccessor.|
> |**Nombre**:<br />unManagedinvalidequalityoperand<br />**Hex**:<br />800404ac<br />**Número**:<br />-2147220308|QB_LITERAL solo se admite para operadores de igualdad.|
> |**Nombre**:<br />unManagedinvalidescapedxml<br />**Hex**:<br />800404a1<br />**Número**:<br />-2147220319|Tamaño de escape xml no es como se esperaba.|
> |**Nombre**:<br />unManagedinvalidfieldtype<br />**Hex**:<br />800404d8<br />**Número**:<br />-2147220264|La plataforma no puede controlar el tipo de campo especificado.|
> |**Nombre**:<br />unManagedinvalidlinkobjects<br />**Hex**:<br />800404ba<br />**Número**:<br />-2147220294|Entidad de vínculo no válida, vínculo al atributo o vínculo desde el atributo.|
> |**Nombre**:<br />unManagedinvalidoperator<br />**Hex**:<br />800404c7<br />**Número**:<br />-2147220281|El operador especificado no es válido.|
> |**Nombre**:<br />unManagedinvalidorganizationid<br />**Hex**:<br />800404be<br />**Número**:<br />-2147220290|El organizationid falta o no es válido.|
> |**Nombre**:<br />unManagedinvalidowningbusinessunit<br />**Hex**:<br />800404a8<br />**Número**:<br />-2147220312|El owningbusinessunit falta o no es válido.|
> |**Nombre**:<br />unManagedinvalidowningbusinessunitorbusinessunitid<br />**Hex**:<br />800404bc<br />**Número**:<br />-2147220292|El owningbusinessunit falta o businessunitid no es válido o falta.|
> |**Nombre**:<br />unManagedinvalidowninguser<br />**Hex**:<br />800404bd<br />**Número**:<br />-2147220291|El owninguser falta o no es válido.|
> |**Nombre**:<br />unManagedinvalidpagevalue<br />**Hex**:<br />800404c2<br />**Número**:<br />-2147220286|El valor de página falta o no es válido.|
> |**Nombre**:<br />unManagedinvalidparametertypeforparameterizedquery<br />**Hex**:<br />800404d6<br />**Número**:<br />-2147220266|No se admite una consulta con parámetros para el tipo de parámetro proporcionado.|
> |**Nombre**:<br />unManagedinvalidprincipal<br />**Hex**:<br />8004049e<br />**Número**:<br />-2147220322|El identificador principal falta o no es válido.|
> |**Nombre**:<br />unManagedinvalidprivilegeedepth<br />**Hex**:<br />800404bb<br />**Número**:<br />-2147220293|Profundidad de privilegios no válida para el usuario.|
> |**Nombre**:<br />unManagedinvalidprivilegeid<br />**Hex**:<br />800404ce<br />**Número**:<br />-2147220274|El pivilegio falta o no es válido.|
> |**Nombre**:<br />unManagedinvalidprivilegeusergroup<br />**Hex**:<br />800404cd<br />**Número**:<br />-2147220275|El grupo de usuarios del privilegio no es válido o falta.|
> |**Nombre**:<br />unManagedinvalidprocesschildofcondition<br />**Hex**:<br />800404b4<br />**Número**:<br />-2147220300|Se ha llamado a ProcessChildOfCondition con condición de no secundario de.|
> |**Nombre**:<br />unManagedinvalidprocessliternalcondition<br />**Hex**:<br />800404b1<br />**Número**:<br />-2147220303|ProcessLiteralCondition solo es válido para su uso con las consultas de informe.|
> |**Nombre**:<br />unManagedinvalidsecurityprincipal<br />**Hex**:<br />800404d2<br />**Número**:<br />-2147220270|La entidad de seguridad falta o no es válida.|
> |**Nombre**:<br />unManagedinvalidstreamfield<br />**Hex**:<br />800404d7<br />**Número**:<br />-2147220265|La plataforma no puede administrar los campos de secuencia.|
> |**Nombre**:<br />unManagedinvalidtlsmananger<br />**Hex**:<br />800404a2<br />**Número**:<br />-2147220318|No se pudo recuperar el administrador de TLS.|
> |**Nombre**:<br />unManagedinvalidtrxcountforcommit<br />**Hex**:<br />800404e2<br />**Número**:<br />-2147220254|Se esperaba que el número de transacciones fuera 1 para confirmar.|
> |**Nombre**:<br />unManagedinvalidtrxcountforrollback<br />**Hex**:<br />800404e1<br />**Número**:<br />-2147220255|Se esperaba que el número de transacciones fuera 1 para revisar.|
> |**Nombre**:<br />unManagedinvalidvaluettagoutsideconditiontag<br />**Hex**:<br />800404bf<br />**Número**:<br />-2147220289|Una etiqueta de valor no válido se encontró fuera de su etiqueta de condición.|
> |**Nombre**:<br />unManagedinvalidversionvalue<br />**Hex**:<br />800404c0<br />**Número**:<br />-2147220288|El valor de versión falta o no es válido.|
> |**Nombre**:<br />unManagedinvaludidispatchfield<br />**Hex**:<br />800404db<br />**Número**:<br />-2147220261|La plataforma no puede administrar los campos idispatch.|
> |**Nombre**:<br />unManagedmissingaddressentity<br />**Hex**:<br />800404cb<br />**Número**:<br />-2147220277|No se encontró la entidad de dirección.|
> |**Nombre**:<br />unManagedmissingattributefortag<br />**Hex**:<br />800404c5<br />**Número**:<br />-2147220283|No se encontró el atributo esperado para la etiqueta especificada.|
> |**Nombre**:<br />unManagedmissingdataaccess<br />**Hex**:<br />800404df<br />**Número**:<br />-2147220257|No se ha podido recuperar el acceso a los datos de ExecutionContext.|
> |**Nombre**:<br />unManagedmissingfilterattribute<br />**Hex**:<br />800404ad<br />**Número**:<br />-2147220307|Falta el atributo de filtro.|
> |**Nombre**:<br />unManagedmissinglinkentity<br />**Hex**:<br />800404b2<br />**Número**:<br />-2147220302|Error inesperado al localizar la entidad de enlace.|
> |**Nombre**:<br />unManagedMissingObjectType<br />**Hex**:<br />80042003<br />**Número**:<br />-2147213309|Debe especificar el tipo de objeto de uno de los atributos.|
> |**Nombre**:<br />unManagedmissingparentattributeonentity<br />**Hex**:<br />800404b5<br />**Número**:<br />-2147220299|No se encontró el atributo principal en la entidad esperada.|
> |**Nombre**:<br />unManagedmissingparententity<br />**Hex**:<br />800404e5<br />**Número**:<br />-2147220251|No se encontró la entidad primaria.|
> |**Nombre**:<br />unManagedmissingpreviousownertype<br />**Hex**:<br />800404d0<br />**Número**:<br />-2147220272|No se puede determinar el tipo del propietario anterior.|
> |**Nombre**:<br />unManagedmissingreferencesfromrelationship<br />**Hex**:<br />800404c9<br />**Número**:<br />-2147220279|No se puede acceder a una relación en el conjunto de ReferencesFrom de la entidad.|
> |**Nombre**:<br />unManagedmissingreferencingattribute<br />**Hex**:<br />800404c8<br />**Número**:<br />-2147220280|El ReferencingAttribute de la relación falta o no es válido.|
> |**Nombre**:<br />unManagedmorethanonesortattribute<br />**Hex**:<br />800404a6<br />**Número**:<br />-2147220314|Se ha definido más de un atributo de ordenación.|
> |**Nombre**:<br />unManagedObjectTypeUnexpected<br />**Hex**:<br />80042004<br />**Número**:<br />-2147213308|Se especificó el tipo de objeto de uno de los atributos que no lo permite.|
> |**Nombre**:<br />unManagedparentattributenotfound<br />**Hex**:<br />800404a4<br />**Número**:<br />-2147220316|No se encontró el atributo principal para el atributo secundario.|
> |**Nombre**:<br />unManagedpartylistattributenotsupported<br />**Hex**:<br />800404b8<br />**Número**:<br />-2147220296|No se admiten los atributos de tipo partylist.|
> |**Nombre**:<br />unManagedpendingtrxexists<br />**Hex**:<br />800404e3<br />**Número**:<br />-2147220253|Ya existe una transacción pendiente.|
> |**Nombre**:<br />unManagedproxycreationfailed<br />**Hex**:<br />8004049f<br />**Número**:<br />-2147220321|No se puede crear una instancia de proxy administrado.|
> |**Nombre**:<br />unManagedtrxinterophandlerset<br />**Hex**:<br />800404dd<br />**Número**:<br />-2147220259|TrxInteropHandler ya se ha establecido.|
> |**Nombre**:<br />unManagedunablegetexecutioncontext<br />**Hex**:<br />800404e4<br />**Número**:<br />-2147220252|No se pudo recuperar el contexto de ejecución (TLS).|
> |**Nombre**:<br />unManagedunablegetsessiontoken<br />**Hex**:<br />800404d3<br />**Número**:<br />-2147220269|No se puede recuperar el token de sesión.|
> |**Nombre**:<br />unManagedunablegetsessiontokennotrx<br />**Hex**:<br />800404d4<br />**Número**:<br />-2147220268|No se puede recuperar el token de sesión porque no existen transacciones pendientes.|
> |**Nombre**:<br />unManagedunableswitchusercontext<br />**Hex**:<br />800404e0<br />**Número**:<br />-2147220256|No se puede establecer un contexto de usuario diferente.|
> |**Nombre**:<br />unManagedunabletoaccessqueryplan<br />**Hex**:<br />800404a5<br />**Número**:<br />-2147220315|No se puede acceder al plan de la consulta.|
> |**Nombre**:<br />unManagedunabletoaccessqueryplanfilter<br />**Hex**:<br />800404c6<br />**Número**:<br />-2147220282|No se puede acceder a un filtro en el plan de la consulta.|
> |**Nombre**:<br />unManagedunabletolocateconditionfilter<br />**Hex**:<br />800404c3<br />**Número**:<br />-2147220285|Error inesperado al localizar el filtro para la condición.|
> |**Nombre**:<br />unManagedunabletoretrieveprivileges<br />**Hex**:<br />800404a0<br />**Número**:<br />-2147220320|No se pudieron recuperar privilegios.|
> |**Nombre**:<br />unManagedunexpectedpropertytype<br />**Hex**:<br />800404cc<br />**Número**:<br />-2147220276|Tipo inesperado de propiedad.|
> |**Nombre**:<br />unManagedunexpectedrimarykey<br />**Hex**:<br />800404b3<br />**Número**:<br />-2147220301|El atributo de clave principal no fue como espera.|
> |**Nombre**:<br />unManagedunknownaggregateoperation<br />**Hex**:<br />800404b6<br />**Número**:<br />-2147220298|Se ha proporcionado una operación agregada desconocida.|
> |**Nombre**:<br />unManagedunusablevariantdata<br />**Hex**:<br />800404af<br />**Número**:<br />-2147220305|La variante proporcionada contiene datos en un formato que no se puede usar.|
> |**Nombre**:<br />UnmappedTransformationOutputDataFound<br />**Hex**:<br />80040381<br />**Número**:<br />-2147220607|Uno o varios de los resultados devueltos por la transformación no está asignado a los campos de destino.|
> |**Nombre**:<br />UnpopulatedPrimaryKey<br />**Hex**:<br />8004023d<br />**Número**:<br />-2147220931|La clave principal debe rellenarse para llamadas a plataforma en cliente rico en modo sin conexión.|
> |**Nombre**:<br />UnrelatedConnectionRoles<br />**Hex**:<br />80048216<br />**Número**:<br />-2147188202|Los roles de conexión no están relacionados.|
> |**Nombre**:<br />UnrestrictedIFrameInUserDashboard<br />**Hex**:<br />8004E30C<br />**Número**:<br />-2147163380|Un formulario XML de panel de usuario no puede tener seguridad = false.|
> |**Nombre**:<br />UnspecifiedActivityXmlForCampaignActivityPropagate<br />**Hex**:<br />80040318<br />**Número**:<br />-2147220712|Especifique un Xml de actividad para CampaignActivity ejecutar o distribuir|
> |**Nombre**:<br />UnsupportedActionType<br />**Hex**:<br />80060390<br />**Número**:<br />-2147089520|Falta el paso de control.|
> |**Nombre**:<br />UnsupportedArgumentsMarkedRequired<br />**Hex**:<br />80060394<br />**Número**:<br />-2147089516|Los argumentos no compatible no se deben marcar como necesarios.|
> |**Nombre**:<br />UnsupportedAttributeForEditor<br />**Hex**:<br />80060010<br />**Número**:<br />-2147090416|La regla incluye un atributo que no se admite.|
> |**Nombre**:<br />UnsupportedAttributeInInProfileItemEntityFilters<br />**Hex**:<br />80071123<br />**Número**:<br />-2147020509|El atributo {0} no es compatible con la opción de consulta de filtro.|
> |**Nombre**:<br />UnsupportedAttributeOrOperatorMobileOfflineFilters<br />**Hex**:<br />80071115<br />**Número**:<br />-2147020523|El operador o atributo "{0}" no se admite para el filtro de la org. de Mobile offline.|
> |**Nombre**:<br />UnsupportedAttributeType<br />**Hex**:<br />8005E00D<br />**Número**:<br />-2147098611|El tipo de atributo {0} no se admite. Quite el atributo {1} de la consulta e inténtelo de nuevo.|
> |**Nombre**:<br />UnsupportedComponentOperation<br />**Hex**:<br />8004F010<br />**Número**:<br />-2147160048|{0} no se reconoce como una operación admitida.|
> |**Nombre**:<br />UnsupportedCudOperationForDynamicProperties<br />**Hex**:<br />80061019<br />**Número**:<br />-2147086311|No se puede crear una propiedad para un kit.|
> |**Nombre**:<br />UnsupportedDashboardInEditor<br />**Hex**:<br />8004E30E<br />**Número**:<br />-2147163378|No se pudo abrir el panel. |
> |**Nombre**:<br />UnsupportedEmailServer<br />**Hex**:<br />8005E242<br />**Número**:<br />-2147098046|No se admite el servidor de correo electrónico.|
> |**Nombre**:<br />UnsupportedImportComponent<br />**Hex**:<br />80061302<br />**Número**:<br />-2147085566|Error en la importación porque el componente {0} no es compatible con la importación y la exportación.|
> |**Nombre**:<br />UnsupportedListMemberType<br />**Hex**:<br />80040301<br />**Número**:<br />-2147220735|Tipo de miembro de lista no admitido.|
> |**Nombre**:<br />UnsupportedOperatorForAttributeInProfileItemEntityFilters<br />**Hex**:<br />80071121<br />**Número**:<br />-2147020511|El operador {0} no es compatible con el atributo {1} en la opción de consulta de filtro.|
> |**Nombre**:<br />UnsupportedParameter<br />**Hex**:<br />80040320<br />**Número**:<br />-2147220704|Un parámetro especificado no se admite en la operación masiva|
> |**Nombre**:<br />UnsupportedProcessCode<br />**Hex**:<br />80040385<br />**Número**:<br />-2147220603|El código de proceso no se admite en esta entidad.|
> |**Nombre**:<br />UnsupportedSdkMessageForBundles<br />**Hex**:<br />80061025<br />**Número**:<br />-2147086299|No se admite este mensaje para productos del tipo agrupación.|
> |**Nombre**:<br />UnsupportedStepForBusinessRuleEditor<br />**Hex**:<br />80060009<br />**Número**:<br />-2147090423|La regla contiene un paso que no admite el editor.|
> |**Nombre**:<br />UnsupportedZipFileForImport<br />**Hex**:<br />80048495<br />**Número**:<br />-2147187563|No se pudo cargar el archivo comprimido (.zip) o .cab debido a que está dañado o no contiene archivos importables válidos.|
> |**Nombre**:<br />UnzipProcessCountLimitReached<br />**Hex**:<br />80048494<br />**Número**:<br />-2147187564|No se puede iniciar un nuevo proceso para descomprimir.|
> |**Nombre**:<br />UnzipTimeout<br />**Hex**:<br />80048496<br />**Número**:<br />-2147187562|El tiempo de espera ha sucedido al descomprimir el archivo zip cargado para la importación.|
> |**Nombre**:<br />UpdateAttributeMap<br />**Hex**:<br />80046204<br />**Número**:<br />-2147196412|Se ha producido un error UpdateAttributeMap|
> |**Nombre**:<br />UpdateEntityMap<br />**Hex**:<br />80046201<br />**Número**:<br />-2147196415|Se ha producido un error UpdateEntityMap|
> |**Nombre**:<br />UpdateNonCustomReportFromTemplate<br />**Hex**:<br />80040490<br />**Número**:<br />-2147220336|No se puede actualizar un informe desde una plantilla si no se creó el informe desde una plantilla|
> |**Nombre**:<br />UpdatePublishedWorkflowDefinition<br />**Hex**:<br />80045002<br />**Número**:<br />-2147201022|No se puede actualizar una definición de flujo de trabajo publicada.|
> |**Nombre**:<br />UpdatePublishedWorkflowDefinitionWorkflowDependency<br />**Hex**:<br />80045008<br />**Número**:<br />-2147201016|No se puede actualizar una dependencia de flujo de trabajo para una definición de un flujo de trabajo publicada.|
> |**Nombre**:<br />UpdatePublishedWorkflowTemplate<br />**Hex**:<br />8004501B<br />**Número**:<br />-2147200997|No se puede actualizar una plantilla de flujo de trabajo publicada.|
> |**Nombre**:<br />UpdateRecurrenceRuleFailed<br />**Hex**:<br />8004E114<br />**Número**:<br />-2147163884|No se pudo actualizar la regla de periodicidad. No se puede encontrar una regla de periodicidad correspondiente.|
> |**Nombre**:<br />UpdateRIOrganizationDataAccessNotAllowed<br />**Hex**:<br />80044273<br />**Número**:<br />-2147204493|Solo un administrador del sistema puede actualizar esta configuración.|
> |**Nombre**:<br />UpdateWorkflowActivation<br />**Hex**:<br />80045003<br />**Número**:<br />-2147201021|No se puede actualizar la activación de un flujo de trabajo.|
> |**Nombre**:<br />UpdateWorkflowActivationWorkflowDependency<br />**Hex**:<br />80045007<br />**Número**:<br />-2147201017|No se puede actualizar una dependencia de flujo de trabajo asociada con la activación de un flujo de trabajo.|
> |**Nombre**:<br />UserAlreadyExists<br />**Hex**:<br />80041d2c<br />**Número**:<br />-2147214036|El usuario especificado de Active Directory ya existe como usuario de Dynamics 365.|
> |**Nombre**:<br />UserCancelledMailMerge<br />**Hex**:<br />8004032f<br />**Número**:<br />-2147220689|El usuario ha cancelado la operación de combinación de correspondencia.|
> |**Nombre**:<br />UserCannotEnableWithoutLicense<br />**Hex**:<br />8004D24C<br />**Número**:<br />-2147167668|No se puede habilitar un usuario sin licencia|
> |**Nombre**:<br />UserDataNotFound<br />**Hex**:<br />8004D211<br />**Número**:<br />-2147167727|No se encontraron los datos de usuario.|
> |**Nombre**:<br />UserDoesNotHaveAccessToTheTenant<br />**Hex**:<br />80044507<br />**Número**:<br />-2147203833|El usuario no tiene acceso al inquilino.|
> |**Nombre**:<br />UserDoesNotHaveAdminOnlyModePermissions<br />**Hex**:<br />8004A113<br />**Número**:<br />-2147180269|El usuario no tiene los privilegios necesarios (o la pertenencia a un rol) para acceder a la organización cuando se encuentra en el modo solo de administración.|
> |**Nombre**:<br />UserDoesNotHavePrivilegesToRunTheTool<br />**Hex**:<br />800608F8<br />**Número**:<br />-2147088136|Debe ser administrador del sistema para ejecutar esta solicitud.|
> |**Nombre**:<br />UserDoesNotHaveSendAsAllowed<br />**Hex**:<br />8004480d<br />**Número**:<br />-2147203059|El usuario no tiene el privilegio de enviar como.|
> |**Nombre**:<br />UserDoesNotHaveSendAsForQueue<br />**Hex**:<br />8004480f<br />**Número**:<br />-2147203057|No tiene privilegios suficientes para enviar un correo electrónico como la cola seleccionada. Póngase en contacto con el administrador del sistema para obtener asistencia.|
> |**Nombre**:<br />UserIdOrQueueNotSet<br />**Hex**:<br />800404e8<br />**Número**:<br />-2147220248|Id. de usuario principal o tipo de cola de destino no establecido|
> |**Nombre**:<br />UserInviteDisabled<br />**Hex**:<br />8004D216<br />**Número**:<br />-2147167722|No se puede enviar invitación porque están deshabilitadas las invitaciones de usuario.|
> |**Nombre**:<br />UserInWrongBusiness<br />**Hex**:<br />80041409<br />**Número**:<br />-2147216375|El usuario con el id={0} pertenece a otra unidad de negocio={1} que el rol con el roleId={2} y el rolebusinessUnit={3}.|
> |**Nombre**:<br />UserIsNotSystemAdminInOrganization<br />**Hex**:<br />8004B069<br />**Número**:<br />-2147176343|El usuario actual no es un administrador del sistema en la organización del cliente|
> |**Nombre**:<br />UserLoopBeingCreated<br />**Hex**:<br />80041d25<br />**Número**:<br />-2147214043|No se puede establecer el usuario seleccionado como administrador de este usuario porque el usuario seleccionado ya es el administrador o está en la jerarquía de administración inmediata del usuario.  Seleccione otro usuario para que sea el administrador o no actualice el registro.|
> |**Nombre**:<br />UserLoopExists<br />**Hex**:<br />80041d24<br />**Número**:<br />-2147214044|No se puede establecer un administrador para este usuario porque una relación existente en la jerarquía de administración causa una relación circular.  Normalmente, esto se debe a una edición manual de la base de datos de Microsoft Dynamics 365. Para solucionar esto, se debe cambiar la jerarquía en la base de datos para quitar la relación circular.|
> |**Nombre**:<br />UserNameRequiredForImpersonation<br />**Hex**:<br />8005E24D<br />**Número**:<br />-2147098035|Escriba un nombre de usuario y vuelva a guardar|
> |**Nombre**:<br />UserNeverLoggedIntoYammer<br />**Hex**:<br />8005F111<br />**Número**:<br />-2147094255|Para seguir a otros usuarios, debe iniciar sesión en Yammer. Inicie sesión en su cuenta de Yammer e inténtelo de nuevo.|
> |**Nombre**:<br />UserNotAssignedLicense<br />**Hex**:<br />8004D24B<br />**Número**:<br />-2147167669|No se han asignado licencias al usuario|
> |**Nombre**:<br />UserNotAssignedRoles<br />**Hex**:<br />80042f09<br />**Número**:<br />-2147209463|No se ha asignado ningún rol al usuario (Id = {0}).|
> |**Nombre**:<br />UserNotInParentHierarchy<br />**Hex**:<br />80041d07<br />**Número**:<br />-2147214073|El usuario no se encuentra en la jerarquía de negocio del usuario primario.|
> |**Nombre**:<br />UserNotMemberOfOrg<br />**Hex**:<br />80072560<br />**Número**:<br />-2147015328|El usuario no es miembro de la organización.|
> |**Nombre**:<br />UserSettingsInvalidAdvancedFindStartupMode<br />**Hex**:<br />80041d34<br />**Número**:<br />-2147214028|El modo de inicio de búsqueda avanzada no es válido.|
> |**Nombre**:<br />UserSettingsInvalidSearchExperienceValue<br />**Hex**:<br />80041d53<br />**Número**:<br />-2147213997|Valor de la experiencia de búsqueda no válido.|
> |**Nombre**:<br />UserSettingsOverMaxPagingLimit<br />**Hex**:<br />80044305<br />**Número**:<br />-2147204347|Límite de paginación por encima del valor máximo configurado.|
> |**Nombre**:<br />UserTimeConvertException<br />**Hex**:<br />80040241<br />**Número**:<br />-2147220927|No se puede convertir la información de zona horaria del usuario.|
> |**Nombre**:<br />UserTimeZoneException<br />**Hex**:<br />80040240<br />**Número**:<br />-2147220928|No se puede recuperar la información de zona horaria del usuario.|
> |**Nombre**:<br />UserViewsOrVisualizationsFound<br />**Hex**:<br />8004E302<br />**Número**:<br />-2147163390|Un panel del sistema no puede contener vistas y visualizaciónes de usuario.|
> |**Nombre**:<br />ValidateNotSupported<br />**Hex**:<br />8004E10A<br />**Número**:<br />-2147163894|El método de validación no se admite para la cita periódica maestra.|
> |**Nombre**:<br />ValidationContextIsNull<br />**Hex**:<br />80060442<br />**Número**:<br />-2147089342|Error al crear o actualizar proceso de negocios: contexto de validación no puede ser nulo.|
> |**Nombre**:<br />ValidationFailedForDynamicProperty<br />**Hex**:<br />80061021<br />**Número**:<br />-2147086303|Error al guardar la propiedad {0}.|
> |**Nombre**:<br />ValidDateTimeBehaviorExportAsWarning<br />**Hex**:<br />800608A5<br />**Número**:<br />-2147088219|El campo {0} será una fecha y hora local de usuario puesto que los comportamientos de Solo fecha e Independiente de la zona horaria no funcionarán en versiones anteriores de Dynamics 365.|
> |**Nombre**:<br />ValidDateTimeBehaviorWarning<br />**Hex**:<br />800608A4<br />**Número**:<br />-2147088220|Se ha cambiado el comportamiento de este campo. Debe revisar todas las dependencias de este campo, como las reglas de negocio, los flujos de trabajo, y los campos consolidados y calculados, para asegurar que no se producirán problemas. Atributo: {0}|
> |**Nombre**:<br />ValidOnlyForDynamicsOnline<br />**Hex**:<br />80072302<br />**Número**:<br />-2147015934|Esta API solo es válida para Dynamics 365 en línea.|
> |**Nombre**:<br />ValueMissingInOptionOrderArray<br />**Hex**:<br />80044325<br />**Número**:<br />-2147204315|Falta un valor en la matriz de opciones.|
> |**Nombre**:<br />ValueParsingError<br />**Hex**:<br />8004B037<br />**Número**:<br />-2147176393|Error de análisis de parámetro {0} de tipo {1} con un valor {2}|
> |**Nombre**:<br />VersionedRowNotFoundInTempDB<br />**Hex**:<br />80048542<br />**Número**:<br />-2147187390|La fila de versión necesaria no se encontró en TempDB; TempDB es probable que esté sin espacio; vuelva a intentarlo más adelante.|
> |**Nombre**:<br />VersionMismatch<br />**Hex**:<br />8004B020<br />**Número**:<br />-2147176416|Versión no admitida - esta es la versión {0} {1}, pero se ha solicitado la versión {2}.|
> |**Nombre**:<br />VeryLargeFileInZipImport<br />**Hex**:<br />80048491<br />**Número**:<br />-2147187567|Uno de los archivos del archivo comprimido (.zip) o .cab que está intentando importar excede el límite de tamaño.|
> |**Nombre**:<br />ViewConditionTypeNotSupportedOffline<br />**Hex**:<br />80071130<br />**Número**:<br />-2147020496|La condición {0} no es compatible.|
> |**Nombre**:<br />ViewForDuplicateDetectionNotDefined<br />**Hex**:<br />80048838<br />**Número**:<br />-2147186632|Vista necesaria para ver duplicados de una entidad no definida.|
> |**Nombre**:<br />ViewNotAvailableForMobileOffline<br />**Hex**:<br />8005F21b<br />**Número**:<br />-2147093989|La vista actual no está disponible sin conexión. Intente cambiar de vista o póngase en contacto con el administrador.|
> |**Nombre**:<br />ViewNotAvailableOnMobile<br />**Hex**:<br />80071126<br />**Número**:<br />-2147020506|Esta vista no está disponible en dispositivos móviles.|
> |**Nombre**:<br />ViewNotSupportedInCalendarModeOffline<br />**Hex**:<br />80071128<br />**Número**:<br />-2147020504|Esta vista solo se admite en el modo de cuadrícula sin conexión. No se admite en el calendario en modo sin conexión.|
> |**Nombre**:<br />VirtualEntitiesNotSupported<br />**Hex**:<br />80073020<br />**Número**:<br />-2147012576|No se admiten entidades virtuales.|
> |**Nombre**:<br />VirtualEntityFailure<br />**Hex**:<br />80050263<br />**Número**:<br />-2147155357|La operación de entidad virtual generó error.|
> |**Nombre**:<br />VirtualEntityFCBOFF<br />**Hex**:<br />80081113<br />**Número**:<br />-2146954989|Bit de característica para EntidadVirtual no habilitada.|
> |**Nombre**:<br />VirtualEntityNotSupportedInMobileOffline<br />**Hex**:<br />80044821<br />**Número**:<br />-2147203039|La entidad {0} es una entidad virtual que no está disponible en Mobile offline.|
> |**Nombre**:<br />VisualizationModuleNotFound<br />**Hex**:<br />8004E012<br />**Número**:<br />-2147164142|No se ha encontrado ningún módulo de visualización con el nombre dado.|
> |**Nombre**:<br />VisualizationOtcNotFoundError<br />**Hex**:<br />8004E015<br />**Número**:<br />-2147164139|No se especifica el código de tipo de objeto para la visualización.|
> |**Nombre**:<br />VisualizationRenderingError<br />**Hex**:<br />8004E00E<br />**Número**:<br />-2147164146|Error en la representación del gráfico|
> |**Nombre**:<br />WebhooksHttpRequestTimedOut<br />**Hex**:<br />80050202<br />**Número**:<br />-2147155454|La llamada webhook ha fallado porque la solicitud Http agotaró el tiempo de espera en el lado cliente. Compruebe al controlador de solicitud de webhook.|
> |**Nombre**:<br />WebhooksInvalidHttpHeaders<br />**Hex**:<br />80050203<br />**Número**:<br />-2147155453|La llamada de webhook ha fallado debido a los encabezados http no válidos en authValue. Compruebe si el formato, los nombres de encabezado y los valores de authValue son válidos para la entidad del extremo de servicio.|
> |**Nombre**:<br />WebhooksInvalidHttpQueryParams<br />**Hex**:<br />80050204<br />**Número**:<br />-2147155452|La llamada de webhook ha fallado debido a los parámetros de consulta http no válidos en authValue. Compruebe si el formato, los nombres de parámetro de consulta y los valores de authValue son válidos para la entidad del extremo de servicio.|
> |**Nombre**:<br />WebhooksMaxSizeExceeded<br />**Hex**:<br />80050207<br />**Número**:<br />-2147155449|La llamada webhook ha fallado porque la carga de la solicitud http ha excedido el tamaño permitido máximo. Reduzca el tamaño de la solicitud y vuelva a intentarlo.|
> |**Nombre**:<br />WebhooksNonSuccessHttpResponse<br />**Hex**:<br />80050201<br />**Número**:<br />-2147155455|La llamada webhook ha fallado porque la solicitud http recibió un código httpStatus incorrecto. Compruebe al controlador de solicitud de webhook.|
> |**Nombre**:<br />WebhooksPostDisabled<br />**Hex**:<br />80050206<br />**Número**:<br />-2147155450|La publicación webhook está deshabilitada para la organización.|
> |**Nombre**:<br />WebhooksPostRequestFailed<br />**Hex**:<br />80050205<br />**Número**:<br />-2147155451|La llamada webhook ha fallado durante la publicación de http. Compruebe la excepción para obtener más detalles.|
> |**Nombre**:<br />WebResourceContentSizeExceeded<br />**Hex**:<br />8004F114<br />**Número**:<br />-2147159788|El tamaño del contenido de recursos web es excesivo.|
> |**Nombre**:<br />WebResourceDuplicateName<br />**Hex**:<br />8004F115<br />**Número**:<br />-2147159787|Ya existe una recurso Web con el mismo nombre. Use un nombre diferente.|
> |**Nombre**:<br />WebResourceEmptyName<br />**Hex**:<br />8004F116<br />**Número**:<br />-2147159786|El nombre del recurso de web no puede ser nulo ni estar vacío.|
> |**Nombre**:<br />WebResourceEmptySilverlightVersion<br />**Hex**:<br />8004F112<br />**Número**:<br />-2147159790|La versión de Silverlight no puede estar vacía para los recursos web de Silverlight.|
> |**Nombre**:<br />WebResourceImportError<br />**Hex**:<br />8004F11B<br />**Número**:<br />-2147159781|Se ha producido un error al importar un recurso Web. Intente importar de nuevo esta solución. Para obtener más ayuda, póngase en contacto con el servicio de soporte técnico de Microsoft Dynamics 365.|
> |**Nombre**:<br />WebResourceImportMissingFile<br />**Hex**:<br />8004F11A<br />**Número**:<br />-2147159782|El archivo para este recurso web no existe en el archivo de solución.|
> |**Nombre**:<br />WebResourceInvalidSilverlightVersion<br />**Hex**:<br />8004F113<br />**Número**:<br />-2147159789|La versión de Silverlight solo puede tener el formato xx.xx[.xx.xx].|
> |**Nombre**:<br />WebResourceInvalidType<br />**Hex**:<br />8004F111<br />**Número**:<br />-2147159791|Tipo de recurso web especificado no válido.|
> |**Nombre**:<br />WebResourceNameInvalidCharacters<br />**Hex**:<br />8004F117<br />**Número**:<br />-2147159785|Los nombres de recursos web solo pueden incluir letras, números, puntos y caracteres de barra diagonal no consecutivos.|
> |**Nombre**:<br />WebResourceNameInvalidFileExtension<br />**Hex**:<br />8004F119<br />**Número**:<br />-2147159783|Los recursos Web no pueden tener las siguientes extensiones de archivo: .aspx, .ascx, .asmx o .ashx.|
> |**Nombre**:<br />WebResourceNameInvalidPrefix<br />**Hex**:<br />8004F118<br />**Número**:<br />-2147159784|El nombre del recurso web no contiene un prefijo válido.|
> |**Nombre**:<br />WebResourcePreventingFormSave<br />**Hex**:<br />80060369<br />**Número**:<br />-2147089559|No se pueden guardar los datos del formulario porque el recurso web registró onSave al invocar preventDefault.|
> |**Nombre**:<br />WopiApplicationUrl<br />**Hex**:<br />80060802<br />**Número**:<br />-2147088382|Error al recuperar la información de la dirección url de la aplicación WOPI.|
> |**Nombre**:<br />WopiDiscoveryFailed<br />**Hex**:<br />80060800<br />**Número**:<br />-2147088384|Fallo en la solicitud de recuperar el XML de detección de WOPI.|
> |**Nombre**:<br />WopiMaxFileSizeExceeded<br />**Hex**:<br />80060803<br />**Número**:<br />-2147088381|{0} el archivo ha superado límite de tamaño de {1}.|
> |**Nombre**:<br />WordTemplateFeatureNotEnabled<br />**Hex**:<br />800608DB<br />**Número**:<br />-2147088165|La característica de documento de Word no está habilitada.|
> |**Nombre**:<br />WorkerProcessCrashFailure<br />**Hex**:<br />80072031<br />**Número**:<br />-2147016655|Esta operación falló debido a un bloqueo del proceso de trabajo.|
> |**Nombre**:<br />WorkflowActivityNotSupported<br />**Hex**:<br />80045045<br />**Número**:<br />-2147200955|No se puede crear, actualizar o publicar el flujo de trabajo porque hace referencia un paso del flujo de trabajo no compatible.|
> |**Nombre**:<br />WorkflowAutomaticallyDeactivated<br />**Hex**:<br />80045042<br />**Número**:<br />-2147200958|La definición de flujo de trabajo original se ha desactivado y sustituido.|
> |**Nombre**:<br />WorkflowCompileFailure<br />**Hex**:<br />80045001<br />**Número**:<br />-2147201023|Se ha producido un error durante la recopilación del flujo de trabajo.|
> |**Nombre**:<br />WorkflowConditionIncorrectBinaryOperatorFormation<br />**Hex**:<br />80045011<br />**Número**:<br />-2147201007|Formación incorrecta de operador binario.|
> |**Nombre**:<br />WorkflowConditionIncorrectUnaryOperatorFormation<br />**Hex**:<br />80045010<br />**Número**:<br />-2147201008|Formación incorrecta de operador unario.|
> |**Nombre**:<br />WorkflowConditionOperatorNotSupported<br />**Hex**:<br />80045012<br />**Número**:<br />-2147201006|Operador de condición admitido para tipo especificado.|
> |**Nombre**:<br />WorkflowConditionTypeNotSupport<br />**Hex**:<br />80045013<br />**Número**:<br />-2147201005|Tipo especificado en condición no válido.|
> |**Nombre**:<br />WorkflowDoesNotExist<br />**Hex**:<br />8006040b<br />**Número**:<br />-2147089397|El flujo de trabajo no existe.|
> |**Nombre**:<br />WorkflowExpressionOperatorNotSupported<br />**Hex**:<br />8004502E<br />**Número**:<br />-2147200978|Operador de expresión admitido para tipo especificado.|
> |**Nombre**:<br />WorkflowIdIsNull<br />**Hex**:<br />80060400<br />**Número**:<br />-2147089408|El id. de flujo de trabajo no puede ser NULO al crear la categoría de flujo de proceso de negocio|
> |**Nombre**:<br />WorkflowIsNotActive<br />**Hex**:<br />80045055<br />**Número**:<br />-2147200939|El flujo de trabajo debe estar activo para utilizarse en un paso de acción.|
> |**Nombre**:<br />WorkflowIsNotOnDemand<br />**Hex**:<br />80045059<br />**Número**:<br />-2147200935|El flujo de trabajo debe marcarse como a petición.|
> |**Nombre**:<br />WorkflowPublishedByNonOwner<br />**Hex**:<br />8004500B<br />**Número**:<br />-2147201013|El propietario no puede publicar ni dejar sin anular la publicación del flujo de trabajo.|
> |**Nombre**:<br />WorkflowPublishNoActivationParameters<br />**Hex**:<br />80045018<br />**Número**:<br />-2147201000|No se puede publicar el flujo de trabajo automático si no se han especificado parámetros de activación.|
> |**Nombre**:<br />WorkflowReferencesInvalidActivity<br />**Hex**:<br />80045038<br />**Número**:<br />-2147200968|La definición de flujo de trabajo contiene un paso que hace referencia a una actividad personalizada no válida. Quite las referencias no válidas e inténtelo de nuevo.|
> |**Nombre**:<br />WorkflowSystemPaused<br />**Hex**:<br />80045017<br />**Número**:<br />-2147201001|El sistema debe pausar el flujo de trabajo.|
> |**Nombre**:<br />WorkflowValidationFailure<br />**Hex**:<br />80045014<br />**Número**:<br />-2147201004|Error en la validación del flujo de trabajo especificado.|
> |**Nombre**:<br />WrongNumberOfBooleanOptions<br />**Hex**:<br />8004431B<br />**Número**:<br />-2147204325|Atributos booleano deben tener exactamente dos opciones de valores.|
> |**Nombre**:<br />XamlNotFound<br />**Hex**:<br />80154B4F<br />**Número**:<br />-2146088113|Esta característica no está disponible en modo sin conexión.|
> |**Nombre**:<br />XlsxExportGeneratingExcelFailed<br />**Hex**:<br />800608C7<br />**Número**:<br />-2147088185|Error de generación de Excel.|
> |**Nombre**:<br />XlsxImportColumnHeadersInvalid<br />**Hex**:<br />800608C6<br />**Número**:<br />-2147088186|Columnas no válidas.|
> |**Nombre**:<br />XlsxImportExcelFailed<br />**Hex**:<br />800608C8<br />**Número**:<br />-2147088184|Error de importación de datos.|
> |**Nombre**:<br />XlsxImportHiddenColumnAbsent<br />**Hex**:<br />800608C4<br />**Número**:<br />-2147088188|Falta la columna necesaria.|
> |**Nombre**:<br />XlsxImportInvalidColumnCount<br />**Hex**:<br />800608C5<br />**Número**:<br />-2147088187|Error de coincidencia de las columnas|
> |**Nombre**:<br />XlsxImportInvalidExcelDocument<br />**Hex**:<br />800608C2<br />**Número**:<br />-2147088190|Archivo para importación no válido.|
> |**Nombre**:<br />XlsxImportInvalidFileData<br />**Hex**:<br />800608C3<br />**Número**:<br />-2147088189|Formato no válido en el archivo de importación.|
> |**Nombre**:<br />YammerAuthTimedOut<br />**Hex**:<br />8005F107<br />**Número**:<br />-2147094265|Ha esperado demasiado tiempo para completar la autorización de Yammer. Inténtelo de nuevo.|
> |**Nombre**:<br />YValuesPerPointMeasureMismatch<br />**Hex**:<br />8004E004<br />**Número**:<br />-2147164156|El número de YValuesPerPoint para series y el número de medidas para colección de medidas para categorías debe ser el mismo.|
> |**Nombre**:<br />ZeroEmailReceived<br />**Hex**:<br />8005E231<br />**Número**:<br />-2147098063|No hay ningún correo electrónico disponible en el buzón o no se puede recuperar.|
> |**Nombre**:<br />ZipFileHasMixOfCsvAndXmlFiles<br />**Hex**:<br />80048485<br />**Número**:<br />-2147187579|El archivo comprimido (.zip) que está intentando cargar contiene más de un tipo de archivo. El archivo puede contener archivos de Excel (.xlsx), archivos separados por comas (.csv) o archivos de hoja de cálculo XML 2003 (.xml), pero no una combinación de los tipos de archivo.|
> |**Nombre**:<br />ZipInsideZip<br />**Hex**:<br />80048489<br />**Número**:<br />-2147187575|El archivo comprimido (.zip) que está intentando cargar contiene otro archivo .zip.|

### <a name="see-also"></a>Vea también

[Administrar las excepciones en su código](handle-exceptions-code.md)