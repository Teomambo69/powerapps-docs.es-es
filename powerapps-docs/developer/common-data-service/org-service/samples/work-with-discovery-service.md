---
title: 'Ejemplo: Trabajar con servicio de detección (Common Data Service) | Microsoft Docs'
description: Este código muestra cómo trabajar con el servicio de detección
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: samples
author: shmcarth
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 6099f304e62092dd63dd35472b80d3c22471de8e
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155484"
---
# <a name="work-with-discovery-service"></a>Trabajar con el servicio de detección

Este código de muestra enseña cómo usar los servicios de detección con ensamblados de SDK. Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/Nava_samplecode/cds/orgsvc/C%23/DiscoveryService).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

En este ejemplo no se abrirá un diálogo para pedirle información de conexión.

Primero debe configurar las variables `username` y `password` en el método `SampleProgram.Main` antes de construir este ejemplo.

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

Este ejemplo usa el ensamblado de SDK `DiscoveryServiceProxy` para ver el servicio de detección con las credenciales de un usuario para determinar con qué entornos se puede conectar.

Si se devuelven uno o varios entornos, el ejemplo le solicitará al usuario que seleccione uno y, a continuación, use un `WhoAmIRequest` para devolver el `SystemUser.UserId` de ese entorno.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

En este ejemplo no se necesita ninguna configuración especial salvo que haya un nombre de usuario y una contraseña de credenciales de usuario válidos para usarlos.

Si conoce el centro de datos regional donde están sus entornos, el ejemplo se ejecutará más rápido si se establece este valor en la línea 40 del archivo de SampleProgram.cs.

En SampleMethods.cs hay una enumeración `DataCenter` para cada uno de los centros de datos conocidos. Cada uno de los miembros de enumeración está acompañado de una notación `Description`. Todos estos integrantes excepto `Unknown` tienen la dirección URL del servicio de detección regional establecida como la descripción. 


### <a name="demonstrate"></a>Demostración

1. Con las credenciales de usuario y el valor `dataCenter`, el programa usa el método estático `GetAllOrganizations` para recuperar todos los entornos conocidos del usuario.
1. El método `GetAllOrganizations` detecta de si el valor `dataCenter` está establecido en `DataCenter.Unknown`. Si está establecido en este integrante, este método irá en bucle por el resto de integrantes de la enumeración de `DataCenter` y recuperará cualquier entorno que encuentre mediante el método estático `GetOrganizationsForDataCenter`.

    Si está establecido un centro de datos específico, `GetAllOrganizations` llamará simplemente a `GetOrganizationsForDataCenter` con estos valores.

1. El método `GetOrganizationsForDataCenter` extrae la dirección URL del servicio de detección del centro de datos de la decoración `Description` de integrantes y la usa así como las credenciales de usuario para ejecutar el mensaje de servicio de detección `RetrieveOrganizationsRequest`.

    Se espera un `System.ServiceModel.Security.SecurityAccessDeniedException` cuando el usuario no tiene ningún entorno en un centro de datos específico.

1. Si algún entorno es devuelto por el método `GetAllOrganizations`, será enumerado en la Consola y a usted se le solicitará que seleccione uno escribiendo un número. Si la decisión es válida, los datos del entorno seleccionados se usan para ejecutar una `WhoAmIRequest` y para devolver el `SystemUser.UserId` para el usuario de ese entorno.

### <a name="clean-up"></a>Limpiar

En este ejemplo no crea ningún registro. No es necesario ninguna limpieza.
