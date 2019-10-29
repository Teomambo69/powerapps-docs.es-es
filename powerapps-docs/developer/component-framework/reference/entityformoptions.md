---
title: EntityFormOptions | Microsoft Docs
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 418871c0-59dc-4a7c-a8f9-9364a19f7662
ms.openlocfilehash: 0ed2d2b13fa084fe1521e90304b7e3ead4ccac27
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/29/2019
ms.locfileid: "73025464"
---
# <a name="entityformoptions"></a>EntityFormOptions

Proporciona acceso a toda la información sobre los formularios de la entidad.

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos

## <a name="properties"></a>Propiedades

### <a name="createfromentity"></a>createFromEntity

Designa un registro que proporcionará los valores predeterminados basados en el valor de atributo asignado. El objeto de búsqueda tiene las siguientes propiedades: tipo de entidad, identificador y nombre.

**Tipo**: [EntityReference](entityreference.md)

### <a name="entityid"></a>entityId

Identificador único del registro de entidad para el que se va a mostrar el formulario. 

**Tipo**: `string`

### <a name="entityname"></a>entityName

Nombre lógico de la entidad para la que se va a mostrar el formulario. 

**Tipo**: `string`

### <a name="formid"></a>formId

IDENTIFICADOR de la instancia del formulario que se va a mostrar.

**Tipo**: `string`

### <a name="height"></a>alto

Alto de la ventana del formulario que se va a mostrar en píxeles.

**Tipo**: `number`

### <a name="openinnewwindow"></a>openInNewWindow

Indica si se va a mostrar el formulario en una nueva ventana.

**Tipo**: `boolean`

### <a name="usequickcreateform"></a>useQuickCreateForm

Si se va a abrir un formulario de creación rápida. Si no se especifica, se pasa de forma predeterminada el valor false. 

**Tipo**: `boolean`

### <a name="width"></a>ancho

Ancho de la ventana del formulario que se va a mostrar en píxeles.

**Tipo**: `boolean`

### <a name="windowposition"></a>windowPosition

Especifica la posición de la ventana en la pantalla.

**Tipo**: `number`

El valor de windowPosition es un número con los siguientes valores posibles

|Value|Posición|
|---|---|
|1|Centro|
|2|Margen|


## <a name="example"></a>Ejemplo

```TypeScript
private onRowClick(event: Event): void {
    let rowRecordId = (event.currentTarget as HTMLTableRowElement).getAttribute(
      RowRecordId
    );
    if (rowRecordId) {
      let entityreference = this.contextObj.parameters.simpleTableGrid.records[
        rowRecordId
      ].getNamedreference();
      let entityFormOptions = {
        entityName: entityreference.entityType!,
        entityId: entityreference.id
      };
      this.contextObj.navigation.openForm(entityFormOptions);
    }
  }
```

### <a name="related-topics"></a>Temas relacionados

[Referencia de la API del marco de componentes de PowerApps](../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../overview.md)