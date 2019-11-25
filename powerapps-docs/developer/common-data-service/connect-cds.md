---
title: Crear aplicaciones cliente (Common Data Service) | Microsoft Docs
description: Introduce los conceptos necesarios para crear aplicaciones cliente personalizadas que se conecten a Common Data Service mediante código.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: paulliew
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 82616711b47a2f14d32e7ee327b21e27df919a9b
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749579"
---
# <a name="create-client-applications"></a>Crear aplicaciones cliente

Puede crear aplicaciones cliente sin escribir código mediante aplicaciones basadas en modelos y lienzos.
Más información: [Visión general de creación de aplicaciones en PowerApps](../../maker/index.md)

Si las opciones de PowerApps no cumplen los requisitos, puede crear una aplicación cliente con código.

## <a name="connecting-to-common-data-service"></a>Conectando a Common Data Service

Para conectarse a un entorno de Common Data Service necesita la dirección URL de la información de entorno y de credenciales de una cuenta de usuario con acceso al entorno. La estrategia que usará depende de si tiene esta información o necesita obtenerla del usuario de la aplicación. 

### <a name="discovery-service"></a>Servicio de detección

Los usuarios pueden tener acceso a varios entornos de Common Data Service. A menos que su aplicación se conecte únicamente a un entorno específico, puede permitir al usuario elegir a qué entorno desea conectarse usando sus credenciales para *detectar* los entornos que sus credenciales le permiten usar. 

Para usar el servicio de detección debe autenticar al usuario para el servicio de detección y recuperar los entornos que tiene a su disposición. Debe implementar por lo general alguna forma que le permita elegir a qué entorno desea conectarse. El siguiente paso es usar la información sobre ese entorno para autenticarlo otra vez para el acceso a ese entorno específico.

Más información: [Servicios de detección](discovery-service.md)

### <a name="authentication"></a>Autenticación

Cuando sepa a qué entorno conectar el usuario, debe autenticarlo en ese entorno.

Más información: [Autenticación con servicios web Common Data Service](authentication.md)