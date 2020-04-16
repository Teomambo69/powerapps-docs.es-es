---
title: Agregar y quitar datos de ejemplo (Common Data Service) | Microsoft Docs
description: Cómo instalar o desinstalar datos de ejemplo usando la web API o el servicio de la organización
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
ms.openlocfilehash: 6448cc652e9135a1264f17d60af072a3ae206130
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155324"
---
# <a name="add-and-remove-sample-data"></a>Agregar y quitar datos de ejemplo

Puede instalar y desinstalar datos de ejemplo mediante programación para una organización mediante los mensajes `InstallSampleData` y `UninstallSampleData`: 

|Acción de API web |Clase de servicio de la organización|
|--|--|
|<xref href="Microsoft.Dynamics.CRM.InstallSampleData?text=InstallSampleData Action" /> |<xref:Microsoft.Crm.Sdk.Messages.InstallSampleDataRequest>|
|<xref href="Microsoft.Dynamics.CRM.UninstallSampleData?text=UninstallSampleData Action" />|<xref:Microsoft.Crm.Sdk.Messages.UninstallSampleDataRequest>|

## <a name="using-the-web-api"></a>Uso de la API web

Instalar datos de ejemplo mediante <xref href="Microsoft.Dynamics.CRM.InstallSampleData?text=InstallSampleData Action" />.

### <a name="request"></a>Solicitud

```http
POST [Organization URI]/api/data/v9.0/InstallSampleData HTTP/1.1
Accept: application/json
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0
```
### <a name="response"></a>Respuesta

```http
HTTP/1.1 204 No Content
OData-Version: 4.0
```

Desinstalar datos de ejemplo mediante <xref href="Microsoft.Dynamics.CRM.UninstallSampleData?text=UninstallSampleData Action" />.

### <a name="request"></a>Solicitud

```http
POST [Organization URI]/api/data/v9.0/UninstallSampleData HTTP/1.1
Accept: application/json
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0
```
### <a name="response"></a>Respuesta

```http
HTTP/1.1 204 No Content
OData-Version: 4.0
```

## <a name="using-the-organization-service"></a>Usar el servicio de la organización

Instalar datos de ejemplo mediante <xref:Microsoft.Crm.Sdk.Messages.InstallSampleDataRequest>

```csharp
var request = new InstallSampleDataRequest();
service.Execute(request);
```

Desinstalar datos de ejemplo mediante <xref:Microsoft.Crm.Sdk.Messages.UninstallSampleDataRequest>

```csharp
var request = new UninstallSampleDataRequest();
service.Execute(request);
```

> [!NOTE]
> Las clases <xref:Microsoft.Crm.Sdk.Messages.InstallSampleDataResponse> o <xref:Microsoft.Crm.Sdk.Messages.UninstallSampleDataResponse> devueltas por estas operaciones no incluyen ninguna propiedad para examinar.

### <a name="see-also"></a>Vea también

[Importar datos](import-data.md)