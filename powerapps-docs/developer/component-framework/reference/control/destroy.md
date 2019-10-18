---
title: destruir | MicrosoftDocs
ms.topic: reference
applies_to: ''
ms.assetid: ba66b513-2a7b-4ba6-b2d5-446ea2b42fdb
author: nkrb
ms.author: nabuthuk
manager: kvivek
ms.date: 10/01/2019
ms.openlocfilehash: 195a6b56ee440cebfdc46c3aa3bb3fc2b5ce3101
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345460"
---
# <a name="destroy"></a>destroy

[!INCLUDE[./includes/destroy-description.md](./includes/destroy-description.md)]

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental)

## <a name="syntax"></a>Sintaxis

`destroy()`

## <a name="example"></a>Ejemplo

```javascript
MyControl.prototype.destroy = function () {
 this.button.removeEventListener("click", this.onButtonClick);
};
```

### <a name="related-topics"></a>Temas relacionados

[Control](../control.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../../overview.md)