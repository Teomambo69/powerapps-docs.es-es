---
title: Introducción a Power Platform ISV Studio | Microsoft Docs
description: Conozca cómo se administran las aplicaciones y son compatibles a través del portal de ISV Studio.
services: ''
suite: powerapps
documentationcenter: na
author: phecke
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.reviewer: pehecke
ms.workload: na
ms.date: 07/11/2019
ms.author: prkoduku
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="introduction-to-isv-studio-for-the-power-platform"></a>Introducción a ISV Studio para Power Platform

[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

ISV Studio está diseñado para convertirse en el destino de Power Platform al que recurrir para los fabricantes independientes de software (ISV) para supervisar y administrar sus aplicaciones. ISV Studio proporciona una vista consolidada entre inquilinos de todas las aplicaciones que un ISV distribuye a los clientes.

> [!IMPORTANT]
>
> - ISV Studio es una característica de vista previa.
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)]

ISV Studio admite aplicaciones creados en el Common Data Service que se publican e implementan a través de [AppSource](https://appsource.microsoft.com/). No se proporcionará telemetría en soluciones cargadas lateralmente no implementadas a través de AppSource.

Las aplicaciones disponibles actualmente en Common Data Service incluyen PowerApps así como Dynamics 365 for Sales, Marketing, Service y Talent.

Cuando un usuario final instala una aplicación desde AppSource, se mostrará un diálogo de consentimiento que solicita al usuario que confirme que la información de contacto, uso y transacción puede compartirse con el proveedor de la aplicación. Esta información la usa el proveedor para permitir la facturación y otras actividades transaccionales y para permitir telemetría en ISV Studio para que ISV aprenda y actúe.

Un cliente puede solicitar que los datos no se compartan con el proveedor, en cuyo caso Microsoft quitará todos los datos de ese inquilino determinado de ISV Studio.

Para obtener acceso a la vista previa pública de ISV Studio, vaya al explorador de [https://aka.ms/ISVStudio](https://aka.ms/ISVStudio/).

## <a name="pre-requisites"></a>Requisitos previos

1. El ISV debe estar asociado con una organización asociada registrada en Microsoft [ISV] que tenga una o varias aplicaciones admitidas publicadas en [AppSource](https://appsource.microsoft.com/). Las aplicaciones compatibles incluyen PowerApps y aplicaciones basadas en modelo en Dynamics 365 como Dynamics 365 Sales y Dynamics 365 Customer Service.

2. El ISV debe tener una cuenta [Azure Active Directory](https://azure.microsoft.com/services/active-directory/) (AAD) y la cuenta se debe estar configurada como colaborador o propietario de la aplicación en el Cloud Partner Portal (CPP) para ese ISV determinado.

Si desea que usuarios adicionales obtengan acceso a ISV Studio, se pueden agregar como colaboradores de la aplicación en CPP.  Las instrucciones se encuentran en [Administrar usuarios en el Cloud Partner Portal](https://docs.microsoft.com/en-us/azure/marketplace/cloud-partner-portal-orig/cloud-partner-portal-manage-users).

Siga leyendo los temas de la página “Aplicación” e “Inquilino” que aparecen a continuación para obtener información sobre las capacidades de ISV Studio.

Envíe un correo electrónico a [ISVFeedback@microsoft.com](mailto:ISVFeedback@microsoft.com) con comentarios o preguntas. Sus comentarios son importantes para que podamos dar forma a las nuevas experiencias móviles.

## <a name="in-this-section"></a>En esta sección

[Página principal](isv-app-management-homepage.md)  
[Página de aplicación](isv-app-management-apppage.md)  
[Página de inquilino](isv-app-management-tenantpage.md)

### <a name="see-also"></a>Vea también

[Introducción a soluciones](introduction-solutions.md)  
[Publicar la aplicación en AppSource](publish-app-appsource.md)
