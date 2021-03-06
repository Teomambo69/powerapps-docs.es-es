---
title: 'Ejemplo: Creación de un rol de conexión (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo crear un rol de conexión.
ms.custom: ''
ms.date: 10/31/2018
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
ms.openlocfilehash: 8e67af447e8d43f14476dcb153798ff3ce7da673
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155896"
---
# <a name="sample-create-a-connection"></a>Ejemplo: crear una conexión

Este ejemplo muestra cómo crear una conexión entre una cuenta y una entidad de contacto que tengan roles de conexión coincidentes. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ConnectionEarlyBound). 
  
## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

Este ejemplo muestra cómo crear una conexión entre una cuenta y un contacto que tengan roles de conexión coincidentes.  

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
2. Crea un rol de conexión para la cuenta y la entidad de contacto.
3. Crea un código de tipo de objeto de rol de conexión relacionado con la cuenta y la entidad de contacto.
4. Asocia el role de conexión consigo mismo.

### <a name="demonstrate"></a>Demostración

1. Crea un rol de conexión entre la cuenta y la entidade de contacto. 
2. Asigna un rol de conexión a un registro.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los registros creados en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
