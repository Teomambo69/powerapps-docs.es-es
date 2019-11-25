---
title: Usar una clave alternativa para crear un registro (Common Data Service) | Microsoft Docs
description: Se pueden utilizar teclas alternativas para crear instancias de clases Entity y EntityReference. Este tema analiza los patrones de uso y las excepciones posibles que se pueden lanzar cuando se usan claves alternativas.
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
ms.openlocfilehash: 11c94bdecd7a2032ea17066280f2abddd61528ef
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749667"
---
# <a name="use-an-alternate-key-to-create-a-record"></a>Usar una clave alternativa para crear un registro

Ahora puede utilizar claves alternativas para crear instancias de clases <xref:Microsoft.Xrm.Sdk.Entity> y <xref:Microsoft.Xrm.Sdk.EntityReference>. Este tema analiza los patrones de uso y las excepciones posibles que se pueden lanzar cuando se usan claves alternativas. Para comprender cómo definir las claves alternativas para una entidad, consulte [Definir claves alternativas para una entidad](define-alternate-keys-entity.md).  

> [!NOTE]
> También puede actualizar registros usando las claves alternativas. Más información: [Actualización con clave alternativa](org-service/entity-operations-update-delete.md#update-with-alternate-key)
  
<a name="BKMK_entity"></a>

## <a name="using-alternate-keys-to-create-an-entity"></a>Uso de claves alternativas para crear una entidad

Ahora puede crear un <xref:Microsoft.Xrm.Sdk.Entity> con un Id. primario, con un solo `KeyAttribute` o una colección de atributos clave en una sola llamada utilizando estos constructores.  
  
```csharp  
public Entity (string logicalName, Guid id) {…}    
public Entity (string logicalName, string keyName, object keyValue) {…}  
public Entity (string logicalName, KeyAttributeCollection keyAttributes) {…}  
  
```  
  
 Un <xref:Microsoft.Xrm.Sdk.Entity> válido usado para operaciones de actualización incluye un nombre lógico de la entidad y uno de los siguientes:  
  
- Un valor para el Id. (valor de GUID de clave principal)
- Un par de valores clave especificados
- Un <xref:Microsoft.Xrm.Sdk.KeyAttributeCollection> con un conjunto válido de atributos que coincide con una clave definida para la entidad.  
  
<a name="BKMK_EntityReference"></a>

## <a name="using-alternate-keys-to-create-an-entityreference"></a>Uso de claves alternativas para crear una EntityReference

Ahora también puede crear un <xref:Microsoft.Xrm.Sdk.EntityReference> con un Id. primario, con un solo `KeyAttribute` o una colección de atributos clave en una sola llamada utilizando estos constructores.  
  
```csharp  
public EntityReference(string logicalName, Guid id) {…}    
public EntityReference(string logicalName, string keyName, object keyValue) {…}    
public EntityReference(string logicalName, KeyAttributeCollection keyAttributeCollection) {…}  
  
```  
  
 Un <xref:Microsoft.Xrm.Sdk.EntityReference> válido incluye un nombre lógico de la entidad y:  
  
- Un valor para el Id. (valor de GUID de clave principal)  
- Un par de valores clave especificados
- Una colección <xref:Microsoft.Xrm.Sdk.KeyAttributeCollection> con un conjunto válido de atributos que coincide con una clave definida para la entidad.  
  
<a name="BKMK_input"></a> 
  
## <a name="alternative-input-to-messages"></a>Entrada alternativa a mensajes

Al pasar las entidades a <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> y <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest>, los valores que se proporcionan para los atributos de búsqueda mediante una <xref:Microsoft.Xrm.Sdk.EntityReference> pueden utilizar ahora <xref:Microsoft.Xrm.Sdk.EntityReference> con claves alternativas definidas en el <xref:Microsoft.Xrm.Sdk.EntityReference.KeyAttributes> para especificar el registro relacionado.  Estos se resolverán y reemplazarán con las referencias de entidad basadas en Id. principal antes de que se procesen los mensajes.  
  
<a name="BKMK_Exceptions"></a>   

## <a name="exceptions-when-using-alternate-keys"></a>Excepciones al utilizar claves alternativas

Es necesario conocer las siguientes condiciones y excepciones posibles para utilizar claves alternativas:  
  
- El Id. principal se usa si se proporciona. Si no se proporciona, examinará el <xref:Microsoft.Xrm.Sdk.KeyAttributeCollection>.  Si no se proporciona el <xref:Microsoft.Xrm.Sdk.KeyAttributeCollection>, lanzará un error.  
  
- Si el <xref:Microsoft.Xrm.Sdk.KeyAttributeCollection> proporcionado incluye un atributo que es la clave principal de la entidad y el valor es válido, éste rellena la propiedad de Id. del <xref:Microsoft.Xrm.Sdk.Entity> o <xref:Microsoft.Xrm.Sdk.EntityReference> con el valor proporcionado.  
  
- Si se proporcionan los atributos de clave, el sistema trata de hacer coincidir el conjunto de atributos suministrado con las claves definidas para la <xref:Microsoft.Xrm.Sdk.Entity>.  Si no encuentra una coincidencia, lanzará un error.  Si encuentra una coincidencia, validará los valores proporcionados para esos atributos. Si es válido, recuperará el Id. del registro que coincidió con valores clave proporcionados, y rellena el valor de Id. de <xref:Microsoft.Xrm.Sdk.Entity> o <xref:Microsoft.Xrm.Sdk.EntityReference> con este valor.  
  
- Si especifica un atributo establecido que no está definido como única clave, se lanzará un error que indica que el uso de atributos de clave únicos es obligatorio.  
  
### <a name="see-also"></a>Vea también

[Defina claves alternativas para una entidad](define-alternate-keys-entity.md)   
[Uso del seguimiento de cambios para sincronizar los datos con sistemas externos](use-change-tracking-synchronize-data-external-systems.md)   
[Use Upsert para insertar o actualizar un registro](use-upsert-insert-update-record.md)
