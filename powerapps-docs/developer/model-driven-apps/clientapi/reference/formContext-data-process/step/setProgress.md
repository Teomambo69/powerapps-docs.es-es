---
title: setProgress (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 649fe7b0-016d-409f-ba3c-b14e0f1953e0
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="setprogress-client-api-reference"></a>setProgress (referencia de la API de cliente)



[!INCLUDE[./includes/setProgress-description.md](./includes/setProgress-description.md)]

## <a name="syntax"></a>Sintaxis

`stepObj.setProgress(stepProgress,message);`

## <a name="parameters"></a>Parámetros

<table style="width:100%">
<tr>
<th>Nombre</th>
<th>Tipo</th>
<th>Obligatoria</th>
<th>Descripción</th>
</tr>
<tr>
<td>stepProgress</td>
<td>Número</td>
<td>Sí</td>
<td>Especifique uno de los valores siguientes para indicar el progreso del paso:
<ul>
<li>0: Ninguno</li>
<li>1: Procesando</li>
<li>2: Finalizada</li>
<li>3: Error</li>
<li>4: No válido</li>
</ul>
</td>
</tr>
<tr>
<td>mensaje</td>
<td>String</td>
<td>No</td>
<td><p>Un mensaje opcional que se configura como texto Alt en el icono del paso.</td>
</tr>
</table>


## <a name="return-value"></a>Valor devuelto

**Tipo**: Cadena. 

**Descripción**: Devuelve "no válido" o "correcto", según se haya actualizado el progreso del paso.

## <a name="remarks"></a>Comentarios

Este método sólo se admite para los pasos de acción. Los pasos de acción son botones de las fases de proceso de negocio en los que los usuarios pueden hacer clic para desencadenar una acción o un flujo de trabajo a petición. Paso de acción es una característica en vista previa que se introdujo en la versión v9.0. Más información: consulte la sección **Automatización de flujos de proceso de negocio con pasos de acción** en [Blog: Nuevas características de automatización y visualización para flujos de proceso de negocio (vista previa pública)](https://blogs.msdn.microsoft.com/crm/2017/10/25/new-automation-and-visualization-features-for-business-process-flows-public-preview/).

### <a name="related-topics"></a>Temas relacionados

[getProgress](getprogress.md)
 
[formContext.data.process](../../formContext-data-process.md)

