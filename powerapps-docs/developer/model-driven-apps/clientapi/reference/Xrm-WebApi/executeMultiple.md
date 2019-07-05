---
title: Xrm.WebApi.online.executeMultiple (referencia de API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: reference
ms.assetid: d4e92999-3b79-4783-8cac-f656fc5f7fda
author: KumarVivek
ms.author: kvivek
manager: annbe
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="xrmwebapionlineexecutemultiple-client-api-reference"></a>Xrm.WebApi.online.executeMultiple (referencia de la API de cliente)

[!INCLUDE[./includes/executeMultiple-description.md](./includes/executeMultiple-description.md)]

> [!NOTE]
> Este método solo es compatible para el modo con conexión ([Xrm.WebApi.online](online.md)). 

Si desea ejecutar varias solicitudes en una transacción, debe pasar un conjunto de cambios como parámetro a este método. [Conjuntos de cambios](../../../../common-data-service/webapi/execute-batch-operations-using-web-api.md#change-sets) representan un conjunto de operaciones que se ejecuta en una transacción. También puede pasar solicitudes individuales y conjuntos de cambios conjuntamente como parámetros a este método.

> [!NOTE]
> No puede incluir operaciones de lectura (recuperar, recuperar varios y funciones de la API web) en un conjunto de cambios. Esto se debe a las especificaciones de OData v4.

## <a name="syntax"></a>Sintaxis

**Ejecutar varias solicitudes:**

```JavaScript
var requests = [req1, req2, req3];
Xrm.WebApi.online.executeMultiple(requests).then(successCallback, errorCallback);
```

**Ejecutar varias solicitudes en una transacción:**

En este caso, `req1`, `req2` y `req3` se ejecutarán en una transacción.

```JavaScript
var changeSet = [req1, req2, req3];
var requests = [changeSet];
Xrm.WebApi.online.executeMultiple(requests).then(successCallback, errorCallback);
```


**Ejecutar una combinación de solicitudes individuales y varias solicitudes en una transacción:**

En este caso, `req1`, `req2` y `req3` se ejecutarán en una transacción, pero `req4` y `req5` se ejecutarán individualmente.

```JavaScript
var changeSet = [req1, req2, req3];
var requests = [req4, req5, changeset];
Xrm.WebApi.online.executeMultiple(requests).then(successCallback, errorCallback);
```

## <a name="parameters"></a>Parámetros

<table style="width:100%">
<tr>
<th>Nombre</th>
<th>Tipo</th>
<th>Obligatoria</th>
<th>Descripción</th>
</tr>
<tr>
<td>Solicitudes</td>
<td>Matriz de objetos</td>
<td>Sí</td>
<td><p>Matriz de uno de los siguientes tipos:</p>
<ul>
<li>objetos donde cada objeto es una acción, función o solicitud CRUD que desea ejecutar en el extremo de la API web. Cada objeto muestra un método <b>getMetadata</b> que le permite definir los metadatos de la acción, la función o la solicitud CRUD que desea ejecutar. Este es el mismo objeto que se pasa en el método <code>execute</code>. Para obtener más información sobre el objeto, consulte <a href="execute.md">execute</a>.</li>
<li>Conjunto de cambios (matriz de objetos), donde cada objeto en el conjunto de cambios es tal como se ha definido anteriormente. En este caso, todos los objetos de solicitud especificados en el conjunto de cambios se ejecutará en una transacción.</li>
</ul>
<p>Vea ejemplos de las solicitudes anteriores en la sección **Sintaxis** para obtener más información.</p>
</td>
</tr>
<tr>
<td>successCallback</td>
<td>Función</td>
<td>No</td>
<td><p>Función para llamar cuando la operación se ejecuta correctamente. Se pasa una matriz de objetos de respuesta a la función donde el objeto de respuesta tiene los atributos siguientes:</p>
<ul>
<li><b>body</b>: (opcional). Objeto. Cuerpo de la respuesta.</li>
<li><b>headers</b>: objeto. Encabezados de la respuesta.</li>
<li><b>ok</b>: booleano. Indica si la solicitud se ha realizado correctamente.</li>
<li><b>status</b>: número. Valor numérico en el código de estado de la respuesta. Por ejemplo: <b>200</b></li>
<li><b>statusText</b>: cadena. Descripción del código del estado de la respuesta. Por ejemplo, <b>OK</b></li>
<li><b>type</b>: cadena. Tipo de respuesta. Los valores son: la cadena vacía (predeterminada), "arraybuffer", "blob", "document", "json" y "text".</b></li>
<li><b>url</b>: cadena. Dirección URL de la solicitud de la acción, de la función o de la solicitud CRUD que se envió al extremo de la API web.</b></li>
</ul>
</td>
</tr>
<tr>
<td>errorCallback</td>
<td>Función</td>
<td>No</td>
<td>Una función para llamar cuando la operación tiene error.</td>
</tr>
</table>

## <a name="return-value"></a>Valor devuelto

En caso de éxito, devuelve una promesa que contiene una matriz de objetos con los atributos especificados anteriormente en la descripción de la función **successCallback**.

### <a name="related-topics"></a>Temas relacionados

[Xrm.WebApi](../xrm-webapi.md)

