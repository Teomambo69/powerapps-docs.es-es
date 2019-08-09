---
title: 'Tutorial: Actualizar un extremo de servicio importado de una solución (Common Data Service) | Microsoft Docs'
description: El tutorial demuestra cómo actualizar un extremo de servicio importado de una solución.
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: 66795838-3b15-bfb3-6f59-68cfe2fe988e
author: brandonsimons
ms.author: jdaly
manager: ryjones
ms.reviewer: null
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="tutorial-update-a-service-endpoint-imported-from-a-solution"></a>Tutorial: Actualizar un extremo de servicio importado de una solución

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/walkthrough-update-service-endpoint-imported-solution -->

Un paso adicional es necesario después de importar en una organización una solución que contiene uno o varios extremos de servicio configurados para autorización SAS. Si la solución que contiene los extremos de servicio se exporta, la solución exportada no contiene la clave SAS para cada extremo de servicio. Tras importar la solución en una organización, deberá dar un paso adicional para proporcionar la clave SAS para cada extremo de servicio.  
  
 Siga estos pasos para establecer la clave SAS para cada extremo de servicio después de la importación de la solución.  
  
### <a name="update-the-sas-key"></a>Actualizar la clave SAS  
  
1.  Ejecute la herramienta de registro de complementos, que se encuentra en la carpeta Tools de la descarga del SDK de Dynamics CRM 2016 Service Pack 1 On-Premises (o posterior). Las versiones anteriores de la herramienta no admiten autorización SAS.  
  
2.  Utilizando la herramienta, inicie sesión en la organización que contiene la solución importada.  
  
3.  Seleccione el extremo de servicio de destino en la vista de pestaña de la organización.  
  
4.  Seleccione **Actualizar**. Debe ver el siguiente formulario con campos ya completos.  
  
 ![Actualizar valor de clave SAS del extremo de servicio](media/sas-key.PNG "Actualizar valor de clave SAS del extremo de servicio")  
  
5.  El campo **Clave SAS** aparece con un valor de "*******".  Reemplace ese valor con el valor de SAS correcto. Puede obtener la clave SAS para su entidad de mensajería de Azure (cola, tema, etc.) desde el [portal clásico](http://manage.windowsazure.com) de Azure.  
  
6.  Seleccione **Guardar**.  
  
### <a name="see-also"></a>Vea también  
[Integration de Azure para Dynamics 365](azure-integration.md)

 [Autenticación y autorización del bus de servicio](https://azure.microsoft.com/documentation/articles/service-bus-authentication-and-authorization/)
