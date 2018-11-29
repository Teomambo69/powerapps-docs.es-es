---
title: Visual Studio y .NET Framework (Common Data Service para aplicaciones) | Microsoft Docs
description: Obtenga más información sobre herramientas y requisitos de desarrollo de código administrado.
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
# <a name="visual-studio-and-the-net-framework"></a>Visual Studio y .NET Framework

Los ensamblados del SDK .NET para Common Data Service para aplicaciones se basan en .NET Framework 4.5.2. 

Puede usar Visual Studio para crear aplicaciones de código administrado mediante .NET Framework 4.5.2 o posterior. 

> [!IMPORTANT]
> Debe crear cualquier aplicación de cliente personalizada usando Microsoft .NET Framework 4.6.2 o posterior.
> Solo podrán conectar con CDS para aplicaciones las aplicaciones que utilizan Seguridad de capa de transporte (TLS) 1.2 o superior. TLS 1.2 no es el protocolo predeterminado usado por .NET Framework 4.5.2, pero está en .NET Framework 4.6.2.
> 
> Más información: [Entrada de blog: Próximas actualizaciones de seguridad de conexión de Dynamics 365 Customer Engagement](https://blogs.msdn.microsoft.com/crm/2017/09/28/updates-coming-to-dynamics-365-customer-engagement-connection-security/)
> 
> [!TIP]
> Al instalar .NET Framework 4.6.2 en el equipo de desarrollo, asegúrese de instalar el paquete de desarrollador y no sólo el tiempo de ejecución. Esto habilitará el marco 4.6.2 para elegirlo en el cuadro de diálogo **Nuevo proyecto** de Visual Studio y en el menú desplegable del marco de destino de las propiedades del proyecto.  

Puede usar una edición Community de Visual Studio para desarrollo. 

[comment]: <> (However, use of extensions isn’t supported in the Express edition so you won’t be able to install useful extensions in that version of Visual Studio)

Más información: [Compatibilidad de versiones de .NET Framework](/dynamics365/customer-engagement/developer/supported-extensions#SupportNET)

Para obtener una relación completa del desarrollo compatible y no compatible, consulte [Extensiones compatibles para Dynamics 365](/dynamics365/customer-engagement/developer/supported-extensions#SupportNET).

## <a name="see-also"></a>Vea también

 [Herramientas del desarrollador](/dynamics365/customer-engagement/developer/developer-tools)