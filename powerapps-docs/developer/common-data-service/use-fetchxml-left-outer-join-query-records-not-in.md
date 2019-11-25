---
title: Usar una combinación externa izquierda en FetchXML para consultar registros &bdquo;no en&bdquo; (Common Data Service) | Microsoft Docs
description: Aprenda a usar una combinación izquierda mediante la clase FetchXML para realizar una consulta que filtre en la tabla de combinación y cree una consulta para buscar registros "no incluidos en" un conjunto
ms.custom: ''
ms.date: 10/31/2018
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
ms.openlocfilehash: e50ff095affda6c976b838b1f368026640fcb2b2
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749659"
---
# <a name="use-a-left-outer-join-in-fetchxml-to-query-for-records-not-in"></a>Use una combinación externa izquierda en FetchXML para consultar los registros "no en"

Puede usar una combinación externa izquierda en FetchXML para realizar una consulta que aplica un filtro a la tabla combinada, por ejemplo, para buscar todos los contactos que no han tenido ninguna actividad de campaña en los últimos dos meses. Otro uso común de este tipo de una consulta es buscar los registros que "no están en" un conjunto, como en estos casos:  
  
- Buscar todos los clientes potenciales que no tienen ninguna tarea  
  
- Buscar todas las cuentas que no tienen ningún contacto  
  
- Buscar todos los clientes potenciales que tienen una o varias tareas  
  
  Una combinación externa izquierda devuelve todas las filas que satisfacen la combinación de la primera entrada con la segunda entrada. También devuelve las filas de la primera entrada que no tenían ninguna fila coincidente en la segunda entrada. Las filas no coincidentes de la segunda entrada se devuelven como valores nulos.  
  
  Puede realizar una combinación externa izquierda en FetchXML mediante el atributo `entityname` como un operador de condición. El atributo `entityname` es válido en condiciones, filtros y filtros anidados.  
  
  Puede crear una consulta con una combinación externa izquierda mediante programación y ejecutar las consultas mediante <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest> y puede guardar la consulta creando un registro de `SavedQuery`. Puede abrir una consulta guardada que contiene una combinación externa izquierda de los editores de búsqueda avanzada o consulta guardada y ejecutar y ver los resultados, pero parte de la funcionalidad del editor está deshabilitada. Los editores permitirán modificaciones de la consulta, como cambiar las columnas devueltas, pero el editor no admite cambiar la combinación externa izquierda.  
  
## <a name="example-find-all-accounts-that-have-no-leads"></a>Ejemplo: buscar todas las cuentas que no tienen ningún cliente potencial  
 A continuación se muestra cómo crear la consulta de FetchXML:  
  
```xml  
<fetch mapping='logical'>  
 <entity name='account'>  
  <attribute name='name'/>  
  <link-entity name='lead'  
               from='leadid'  
               to='originatingleadid'  
               link-type='outer'/>  
  <filter type='and'>  
   <condition entityname='lead'  
              attribute='leadid'  
              operator='null'/>  
  </filter>  
 </entity>  
</fetch>  
  
```  
  
## <a name="example-find-all-leads-that-have-no-tasks-using-an-alias"></a>Ejemplo: buscar todos los clientes potenciales que no tienen ninguna tarea, con un alias  
 A continuación se muestra cómo crear la consulta de FetchXML:  
  
```xml  
<fetch version="1.0" output-format="xml-platform" mapping="logical" distinct="true">  
  <entity name="lead">  
    <attribute name="fullname" />  
    <link-entity name="task" from="regardingobjectid" to="leadid" alias="ab" link-type="outer">  
       <attribute name="regardingobjectid" />  
    </link-entity>  
    <filter type="and">  
        <condition entityname="ab" attribute="regardingobjectid" operator="null" />  
    </filter>  
  </entity>  
<fetch/>  
  
```  
  
 Esto equivale al código SQL siguiente.  
  
```sql  
SELECT lead.FullName  
FROM Leads as lead  
LEFT OUTER JOIN Tasks as ab  
ON (lead.leadId  =  ab.RegardingObjectId)  
WHERE ab.RegardingObjectId is null  
  
```  
  
### <a name="see-also"></a>Vea también  
 [Crear consultas con FetchXML](/dynamics365/customer-engagement/developer/org-service/build-queries-fetchxml)   
 [Ejemplo: Usar agregación en FetchXML](org-service/samples/use-aggregation-fetchxml.md)   
 [Usar FetchXML para crear una consulta](use-fetchxml-construct-query.md)   
 [Ejemplo: Validar y ejecutar una consulta guardada](org-service/samples/validate-execute-saved-query.md)
