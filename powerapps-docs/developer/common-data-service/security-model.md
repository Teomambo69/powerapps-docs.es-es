---
title: Modelo de seguridad (Common Data Service) | Microsoft Docs
description: Common Data Service ofrece un modelo de seguridad que protege la integridad y privacidad de los datos, y admite una colaboración y un acceso a los datos eficaces.
ms.custom: ''
ms.date: 10/19/2019
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
ms.openlocfilehash: 4305fca9d8a343421bc1128a4d4dcc8103d373be
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749795"
---
# <a name="security-model"></a>Modelo de seguridad

Common Data Service ofrece un modelo de seguridad que protege la integridad y privacidad de los datos, y admite una colaboración y un acceso a los datos eficaces. Los objetivos del modelo son los siguientes:
- Proporcione a los usuarios el acceso exclusivo a los niveles de información adecuados que necesitan para realizar su trabajo.
- Establecer categorías de usuarios por rol, y restringir el acceso de acuerdo con esos roles.
- Admitir el uso compartido de datos, de forma que los usuarios y equipos puedan obtener acceso a registros cuya propiedad no tienen para un trabajo en colaboración específico.
- Impedir el acceso de un usuario a registros que no son propiedad del usuario o no se comparten.

La **seguridad basada en roles** se centra en el agrupamiento de un conjunto de privilegios que describen las responsabilidades de un usuario (o las tareas que puede realizar). Common Data Service incluye un conjunto de roles de seguridad predefinidos. Cada uno agrega un conjunto de derechos de usuario para facilitar la administración de la seguridad de usuario. Además, cada implementación de la aplicación puede definir sus propios roles, adaptados a las necesidades de diferentes usuarios. Los roles de seguridad se asocian a [unidades de negocio](businessunit-entity.md).

La **seguridad basada en registros** se centra en los derechos de acceso a registros específicos.

La **seguridad de nivel de campo** restringe el acceso a los campos de alto impacto empresarial específicos de una entidad solo a los usuarios o equipos especificados.
Combine la seguridad basada en roles, la seguridad de nivel de registro y la seguridad de nivel de campo para definir los derechos de seguridad generales que los usuarios tienen en su aplicación de PowerApps.

Como programador, debe saber que las consultas en el código se ejecutan en el contexto de un usuario, y solo devolverán los registros a los que tiene derecho el usuario a leer.
Además, el código solo podrá realizar operaciones basadas en los privilegios asignados a la cuenta de usuario con los roles de seguridad o pertenencia al equipo.

Para obtener información detallada, consulte [Seguridad en Common Data Service](/power-platform/admin/wp-security)

