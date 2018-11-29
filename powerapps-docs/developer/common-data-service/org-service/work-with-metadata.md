---
title: Trabajar con metadatos con el servicio de organización (Common Data Service para aplicaciones) | Microsoft Docs
description: Describe cómo acceder y modificar mediante programación el modelo de metadatos mediante el Servicio de organización.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="work-with-metadata-using-the-organization-service"></a>Trabajar con metadatos usando el servicio de la organización

Los metadatos hacen referencia a la estructura de entidades que se usan para administrar datos en Common Data Service (CDS) para aplicaciones. <xref:Microsoft.Xrm.Sdk.Metadata.MetadataBase> es la clase base para clases que contienen información de metadatos. Esta sección describe cómo acceder y modificar mediante programación el modelo de metadatos mediante el Servicio de organización.

> [!IMPORTANT]
> Agregar, quitar o cambiar las entidades, claves alternativas, atributos o relaciones pueden interferir en el funcionamiento normal del sistema. Si está aplicando cambios a un sistema de producción, se recomienda programar estas operaciones cuando sea menos posible perturbador para los usuarios.

## <a name="see-also"></a>Vea también

[Usar la API web con metadatos](../webapi/use-web-api-metadata.md)

[Trabajar con metadatos con código](../metadata-services.md)