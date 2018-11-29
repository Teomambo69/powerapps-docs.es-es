---
title: getEntityMetadata (referencia API de cliente) en aplicaciones basadas en modelo| Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 89123cde-7c66-4c7d-94e4-e287285019f8
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getentitymetadata"></a>getEntityMetadata



[!INCLUDE[./includes/getEntityMetadata-description.md](./includes/getEntityMetadata-description.md)] 

## <a name="syntax"></a>Sintaxis

`Xrm.Utility.getEntityMetadata(entityName,attributes).then(successCallback, errorCallback)`

## <a name="parameters"></a>Parámetros

|Nombre |Tipo |Obligatoria |Descripción |
|---|---|---|---|
|entityName|String|Sí|El nombre lógico de la entidad.|
|atributos|matriz de cadenas|No|Los atributos para los que se obtienen los metadatos.|
|successCallback|función|No|Una función para llamar cuando se devuelve el valor de los metadatos de la entidad.|
|errorCallback|función|No|Una función para llamar cuando la operación tiene error.|

## <a name="returns"></a>Devuelve

**Tipo**: Objeto

**Descripción**: un objeto que contiene la información de los metadatos de la entidad con los siguientes atributos.

<table>
<tr>
<th>Nombre de atributo</th>
<th>Tipo</th>
<th>Descripción</th>
</tr>
<tr>
<td>ActivityTypeMask</td>
<td>Número</td>
<td>Si una actividad personalizada debe aparecer en los menús de la actividad en la aplicación web. 0 indica que la actividad personalizada no aparece; 1 indica que aparece.</td>
</tr>
<tr>
<td>AutoRouteToOwnerQueue</td>
<td>Valor booleano</td>
<td>Indica si mover los registros de forma automática a la cola predeterminada del propietario cuando se cree o asigne un registro de este tipo. </td>
</tr>

<tr>
<td>CanEnableSyncToExternalSearchIndex</td>
<td>Valor booleano</td>
<td>Solo para uso interno.</td>
</tr>
<tr>
<td>CanTriggerWorkflow</td>
<td>Valor booleano</td>
<td>Indica si la entidad puede desencadenar un proceso de flujo de trabajo.</td>
</tr>
<tr>
<td>Descripción</td>
<td>String</td>
<td>Descripción de la entidad.</td>
</tr>
<tr>
<td>DisplayCollectionName</td>
<td>String</td>
<td>Nombre plural de la entidad.</td>
</tr>
<tr>
<td>DisplayName</td>
<td>String</td>
<td>Nombre de la entidad.</td>
</tr>
<tr>
<td>EnforceStateTransitions</td>
<td>Valor booleano</td>
<td>Indica si la entidad aplicará transiciones de estado personalizadas.</td>
</tr>
<tr>
<td>EntityColor</td>
<td>String</td>
<td>El código hexadecimal para representar el color que se usará para esta entidad en la aplicación.</td>
</tr>
<tr>
<td>EntitySetName</td>
<td>String</td>
<td>El nombre de la entidad de API web activada para esta entidad.</td>
</tr>
<tr>
<td>HasActivities</td>
<td>Valor booleano</td>
<td>Indica si las actividades están asociadas a esta entidad.</td>
</tr>
<tr>
<td>IsActivity</td>
<td>Valor booleano</td>
<td>Indica si la entidad es una actividad.</td>
</tr>
<tr>
<td>IsActivityParty</td>
<td>Valor booleano</td>
<td>Indica si los correos electrónicos se pueden enviar a una dirección de correo electrónico almacenada en un registro de este tipo.</td>
</tr>
<tr>
<td>IsBusinessProcessEnabled</td>
<td>Valor booleano</td>
<td>Indica si se ha habilitado la entidad para los flujos de proceso de negocio.</td>
</tr>
<tr>
<td>IsBPFEntity</td>
<td>Valor booleano</td>
<td>Indica si la entidad es una entidad de flujos de proceso de negocio.</td>
</tr>
<tr>
<td>IsChildEntity</td>
<td>Valor booleano</td>
<td>Indica si la entidad es una entidad secundaria.</td>
</tr>
<tr>
<td>IsConnectionsEnabled</td>
<td>Valor booleano</td>
<td>Indica si hay conexiones habilitadas para esta entidad.</td>
</tr>
<tr>
<td>IsCustomEntity</td>
<td>Valor booleano</td>
<td>Indica si la entidad es una entidad personalizada.</td>
</tr>
<tr>
<td>IsCustomizable</td>
<td>Valor booleano</td>
<td>Indica si la entidad se puede personalizar.</td>
</tr>
<tr>
<td>IsDocumentManagementEnabled</td>
<td>Valor booleano</td>
<td>Indica si está habilitada la administración de documentos.</td>
</tr>
<tr>
<td>IsDocumentRecommendationsEnabled</td>
<td>Valor booleano</td>
<td>Indica si las recomendaciones de documentos estás habilitadas.</td>
</tr>
<tr>
<td>IsDuplicateDetectionEnabled</td>
<td>Valor booleano</td>
<td>Indica si la detección de duplicados está habilitada.</td>
</tr>
<tr>
<td>IsEnabledForCharts</td>
<td>Valor booleano</td>
<td>Indica si los gráficos están habilitados.</td>
</tr>
<tr>
<td>IsImportable</td>
<td>Valor booleano</td>
<td>Indica si la entidad se puede importar mediante el Asistente para importación.</td>
</tr>
<tr>
<td>IsInteractionCentricEnabled</td>
<td>Valor booleano</td>
<td>Indica si la entidad está habilitada para la experiencia interactiva.</td>
</tr>
<tr>
<td>IsKnowledgeManagementEnabled</td>
<td>Valor booleano</td>
<td>Indica si la administración del conocimiento está habilitada para la entidad.</td>
</tr>
<tr>
<td>IsMailMergeEnabled</td>
<td>Valor booleano</td>
<td>Indica si combinar correspondencia está habilitada para esta entidad.</td>
</tr>
<tr>
<td>IsManaged</td>
<td>Valor booleano</td>
<td>Indica si la entidad forma parte de una solución administrada.</td>
</tr>
<tr>
<td>IsOneNoteIntegrationEnabled</td>
<td>Valor booleano</td>
<td>Indica si la Integración de OneNote está habilitada para la entidad.</td>
</tr>
<tr>
<td>IsOptimisticConcurrencyEnabled</td>
<td>Valor booleano</td>
<td>Indica si se ha habilitado la simultaneidad optimista se ha habilitado para la entidad.</td>
</tr>
<tr>
<td>IsQuickCreateEnabled</td>
<td>Valor booleano</td>
<td>Indica si la entidad está habilitada para crear formularios rápidamente.</td>
</tr>
<tr>
<td>IsStateModelAware</td>
<td>Valor booleano</td>
<td>Indica si la entidad admite la configuración de transiciones de estado personalizadas.</td>
</tr>
<tr>
<td>IsValidForAdvancedFind</td>
<td>Valor booleano</td>
<td>Indica si es la entidad aparecerá en Búsqueda avanzada.</td>
</tr>
<tr>
<td>IsVisibleInMobileClient</td>
<td>Valor booleano</td>
<td>Indica si los usuarios de Microsoft Dynamics 365 para tabletas pueden ver los datos para esta entidad.</td>
</tr>
<tr>
<td>IsEnabledInUnifiedInterface</td>
<td>Valor booleano</td>
<td>Indica si la entidad está habilitada para la interfaz unificada.</td>
</tr>
<tr>
<td>LogicalCollectionName</td>
<td>String</td>
<td>El nombre lógico de la colección.</td>
</tr>
<tr>
<td>LogicalName</td>
<td>String</td>
<td>El nombre lógico de la entidad.</td>
</tr>
<tr>
<td>CódigoDeTipoDeObjeto</td>
<td>Número</td>
<td>El código de tipo de entidad.</td>
</tr>
<tr>
<td>OwnershipType</td>
<td>String</td>
<td>El tipo de propiedad para la entidad: “UserOwned” u “OrganizationOwned”.</td>
</tr>
<tr>
<td>PrimaryIdAttribute</td>
<td>String</td>
<td>El nombre del atributo que es el identificador principal de la entidad.</td>
</tr>
<tr>
<td>PrimaryImageAttribute</td>
<td>String</td>
<td>El nombre del atributo de la imagen principal para una entidad.</td>
</tr>
<tr>
<td>PrimaryNameAttribute</td>
<td>String</td>
<td>El nombre del atributo principal para una entidad.</td>
</tr>
<tr>
<td>Privilegios</td>
<td>Matriz de objetos</td>
<td>Los metadatos de privilegios para la entidad cuando *cada* objeto contienen los siguientes atributos para definir el privilegio de seguridad para obtener acceso a una entidad:
<ul>
<li><b>CanBeBasic</b>: booleano. Si el privilegio puede ser un nivel de acceso básico.</li>
<li><b>CanBeDeep</b>: booleano. Si el privilegio puede ser un nivel de acceso exhaustivo.</li>
<li><b>CanBeEntityReference</b>: booleano. Si el privilegio para una parte externa puede ser un nivel de acceso básico.</li>
<li><b>CanBeGlobal</b>: booleano. Si el privilegio puede ser un nivel de acceso global.</li>
<li><b>CanBeLocal</b>: booleano. Si el privilegio puede ser un nivel de acceso local.</li>
<li><b>CanBeParentEntityReference</b>: booleano. Si el privilegio para una parte externa puede ser un nivel de acceso principal.</li>
<li><b>Nombre</b>: cadena. El nombre del privilegio.</li>
<li><b>PrivilegeId</b>: cadena. El identificador del privilegio.</li>
<li><b>PrivilegeType</b>: número. El tipo de privilegio, que es una de las alternativas siguientes:</li>
<ul>
<li>0: Ninguno</li>
<li>1: Crear</li>
<li>2: Leer</li>
<li>3: Escribir</li>
<li>4: Eliminar</li>
<li>5: Asignar</li>
<li>6: Compartir</li>
<li>7: Anexar</li>
<li>8: Anexar a</li>
</ul>
</ul></td>
</tr>
<tr>
<td>Atributos</td>
<td>Recogida</td>
<td>Una colección de objetos de metadatos de atributo. El objeto devuelto depende del tipo de metadatos de atributo.
<p><b>Metadatos de atributo para el <i>tipo</i> básico</b><br/>
Un objeto devuelto con las siguientes propiedades:</p>
<ul>
<li><b>AttributeType</b>: número. Tipo de un atributo. Para una lista de valores del tipo de atributo, consulte <a href="https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.metadata.attributetypecode">AttributeTypeCode</a></li>
<li><b>DisplayName</b>: cadena. Muestra el nombre del atributo.</li>
<li><b>EntityLogicalName</b>: cadena. Nombre lógico de la entidad que contiene el atributo.</li>
<li><b>LogicalName</b>: cadena. Nombre lógico del atributo.</li></ul>

<p><b>Metadatos de atributo para el <i>tipo</i> booleano</b><br/>
Un objeto devuelto con las siguientes propiedades además las propiedades de tipo de metadatos de atributo <i>base</i>:</p>
<ul>
<li><b>DefaultFormValue</b>: boolenao. Valor predeterminado para un conjunto de opciones booleanas.</li>
<li><b>OptionSet</b>: objeto. Opciones para el atributo booleano donde cada opción es un par clave-valor.</li></ul>

<p><b>Metadatos de atributo para el <i>tipo</i> enumeración</b><br/>
Un objeto devuelto con las siguientes propiedades además las propiedades de tipo de metadatos de atributo <i>base</i>:</p>
<ul>
<li><b>OptionSet</b>: objeto. Opciones para el atributo donde cada opción es un par clave-valor.</li></ul>

<p><b>Metadatos de atributo para el <i>tipo</i> lista desplegable</b><br/>
Un objeto devuelto con las siguientes propiedades además las propiedades de tipo de metadatos de atributo <i>base</i>:</p>
<ul>
<li><b>DefaultFormValue</b>: número. Valor predeterminado del formulario para el atributo.</li>
<li><b>OptionSet</b>: objeto. Opciones para el atributo donde cada opción es un par clave-valor.</li></ul>

<p><b>Metadatos de atributo para el <i>tipo</i> estado</b><br/>
Un objeto devuelto con las siguientes propiedades además las propiedades de tipo de metadatos de atributo <i>base</i>:</p>
<ul>
<li><b>OptionSet</b>: objeto. Opciones para el atributo donde cada opción es un par clave-valor.</li></ul>
<p>El objeto también contiene los siguientes métodos:</p>
<ul>
<li><b>getDefaultStatus(arg)</b>: devuelve el estado predeterminado (número) basado en valor de estado pasado para una entidad. Para los valores de estado predeterminados de una entidad, consulte la información de los metadatos de la entidad en <a href="https://docs.microsoft.com/powerapps/developer/common-data-service/reference/about-entity-reference">referencia de entidad</a>.</li>
<li><b>getStatusValuesForState(arg)</b>: devuelve los posibles valores del estado (matriz de números) para un valor especificado de estado. Para los valores de estado de una entidad, consulte la información de los metadatos de la entidad en <a href="https://docs.microsoft.com/powerapps/developer/common-data-service/reference/about-entity-reference">referencia de entidad</a>.</li></ul>

<p><b>Metadatos de atributo para el <i>tipo</i> estado</b><br/>
Un objeto devuelto con las siguientes propiedades además las propiedades de tipo de metadatos de atributo <i>base</i>:</p>
<ul>
<li><b>OptionSet</b>: objeto. Opciones para el atributo donde cada opción es un par clave-valor.</li></ul>
<p>El objeto también contiene el siguiente método:</p>
<ul>
<li><b>getState(arg)</b>: devuelve el valor de estado (número) por el valor de estado especificado (número). Para los valores de estado predeterminados de una entidad, consulte la información de los metadatos de la entidad en <a href="https://docs.microsoft.com/powerapps/developer/common-data-service/reference/about-entity-reference">referencia de entidad</a>.</li>
</ul>
</td>
</tr>
</table>

### <a name="related-topics"></a>Temas relacionados

[Xrm.Utility](../xrm-utility.md)

