---
title: Xrm.WebApi.offline (referencia de API de cliente) en aplicaciones basadas en modelos | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 848c277b-bd44-4388-852a-0f59a3a15538
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="xrmwebapioffline-client-api-reference"></a>Xrm.WebApi.offline (referencia de la API de cliente)



[!INCLUDE[./includes/offline-description.md](./includes/offline-description.md)] 

Para obtener información sobre la característica sin conexión móvil, vea [configurar la sincronización sin conexión móvil para permitir a los usuarios trabajar en modo sin conexión en sus dispositivos móviles](/dynamics365/customer-engagement/mobile-app/configure-mobile-offline-synchronization-dynamics-365-phones-tablets)

`var offlineWebApi = Xrm.WebApi.offline;`

> [!NOTE]
> Use **Xrm.WebApi.offline** en lugar del espacio de nombres [en desuso](/dynamics365/get-started/whats-new/customer-engagement/important-changes-coming#some-client-apis-are-deprecated) **Xrm.Mobile.Offline** para crear y administrar registros en los clientes móviles mientras trabaja en el modo sin conexión.

El objeto **offlineWebApi** proporciona los siguientes métodos. En el modo sin conexión, estos métodos funcionan solo para las entidades que están habilitadas para la sincronización sin conexión móvil y están disponibles en el perfil sin conexión móvil del usuario actual.

- [createRecord](createRecord.md)
- [deleteRecord](deleteRecord.md)
- [isAvailableOffline](isAvailableOffline.md)
- [retrieveRecord](retrieveRecord.md)
- [retrieveMultipleRecords](retrieveMultipleRecords.md)
- [updateRecord](updateRecord.md)

> [!IMPORTANT]
> Mientras crea o actualiza registros en el modo sin conexión, solo se realiza validación básica en los datos de entrada. La validación básica incluye elementos como asegurarse de que el nombre de atributo de la entidad especificado está en minúscula y existe para una entidad, comprobar si existen discrepancias de tipo de datos para el valor de atributo especificado, evitar la creación de registros creados con el mismo valor GUID, comprobar si la entidad relacionada está habilitado sin conexión al recuperar registros de entidad relacionada y validar si el registro que desee recuperar, actualizar o eliminar realmente existe en el almacén de datos sin conexión. Las validaciones de nivel de negocio se producen solo cuando está conectado al servidor y se sincronizan los datos. Un registro se crea o se actualiza solo si los datos de entrada son completamente válidos.

### <a name="related-topics"></a>Temas relacionados

[Xrm.WebApi.online](online.md)

[Xrm.WebApi](../xrm-webapi.md)



