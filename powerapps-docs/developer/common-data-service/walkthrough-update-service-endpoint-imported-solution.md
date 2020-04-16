---
title: 'Tutorial: Actualizar un extremo de servicio importado de una solución (Common Data Service) | Microsoft Docs'
description: El tutorial demuestra cómo actualizar un extremo de servicio importado de una solución.
keywords: ''
ms.date: 10/06/2019
ms.service: powerapps
ms.topic: article
ms.assetid: 66795838-3b15-bfb3-6f59-68cfe2fe988e
author: JimDaly
ms.author: jdaly
manager: ryjones
ms.reviewer: pehecke
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 607f231260d606c9da5070914b50d4b2e4c0abb1
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155128"
---
# <a name="tutorial-update-a-service-endpoint-imported-from-a-solution"></a>Tutorial: Actualizar un extremo de servicio importado de una solución

Un paso adicional es necesario después de importar en una organización una solución que contiene uno o varios extremos de servicio configurados para autorización SAS. Si la solución que contiene los extremos de servicio se exporta, la solución exportada no contiene la clave SAS para cada extremo de servicio. Tras importar la solución en una organización, deberá dar un paso adicional para proporcionar la clave SAS para cada extremo de servicio.  
  
Siga estos pasos para establecer la clave SAS para cada extremo de servicio después de la importación de la solución.  
  
## <a name="update-the-sas-key"></a>Actualizar la clave SAS  
  
1. Ejecute Plug-in Registration Tool, que está disponible para descarga en NuGet. Más información: [Herramientas de descarga de NuGet](download-tools-nuget.md)
  
1. Utilizando Plug-in Registration Tool, inicie sesión en la organización que contiene la solución importada.  
  
1. Seleccione el extremo de servicio de destino en la vista de pestaña de la organización.  
  
1. Seleccione **Actualizar**. Debe ver el siguiente formulario con campos ya completos.  
  
    ![Actualizar valor de clave SAS del extremo de servicio](media/sas-key.PNG "Actualizar valor de clave SAS del extremo de servicio")  
  
1. El campo **Clave SAS** aparece con un valor de "*******".  Reemplace ese valor con el valor de SAS correcto. Puede obtener la clave SAS para su entidad de mensajería de Azure (cola, tema, etc.) desde el [portal de Azure](https://portal.azure.com).  
  
1. Seleccione **Guardar**.  
  
### <a name="see-also"></a>Vea también

[Integración de Azure](azure-integration.md)<br />
[Autenticación y autorización del bus de servicio](/azure/service-bus-messaging/service-bus-authentication-and-authorization)<br />
[Control de acceso al bus de servicio con las firmas de acceso compartido](/azure/service-bus-messaging/service-bus-sas)
