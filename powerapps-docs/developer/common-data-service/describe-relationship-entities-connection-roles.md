---
title: Describir una relación entre entidades con roles de conexión (Common Data Service) | Microsoft Docs
description: Descripción de una relación entre entidades que usan roles de creación de conexión y categorías de rol de conexión.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 07bd45625e0947ed7123f891aa9b33aac214869d
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749380"
---
# <a name="describe-a-relationship-between-entities-with-connection-roles"></a>Describir una relación entre entidades con roles de conexión

Puede describir la relación entre los registros mediante los roles que les asigna.  
  
 Existen varias formas de usar roles de conexión en una conexión:  
  
-   Aplique el mismo rol al registro de origen y al de destino. Un "amigo", un "miembro del equipo" o un "compañero" son ejemplos de los roles que se pueden aplicar a ambos registros en la conexión.  
  
-   Aplique un rol al registro de origen o al registro de destino, pero no a ambos. El rol "comercial" en un contacto con conexión de oportunidad es un ejemplo de dicho rol. Los registros, como oportunidad, factura, o pedido de venta, normalmente contienen suficiente información acerca de lo que representan y no necesitan que se les asigne un rol.  
  
-   Aplique dos roles coincidentes (designados a veces roles recíprocos). Un rol se aplica a un registro de origen y el otro rol se aplica a un registro de destino. Un “doctor” y un “paciente”, un "padre” y un “hijo” son ejemplos de roles que coinciden.  
  
## <a name="connection-role-categories"></a>Categorías del rol de conexión  
 Al crear roles de conexión, puede especificar a qué categoría pertenecen. Por ejemplo, puede usar las categorías siguientes:  
  
- Negocio (proveedor, comprador, competidor)  
  
- Familia (padre, hermana, primo)  
  
- Social (compañero de tenis, miembro de club, amigo)  
  
  La lista de categorías es personalizable. Puede agregar las categorías que mejor se adecúen a su modelo de negocio.  
  
## <a name="create-connection-roles"></a>Crear roles de conexión  
 Para crear un rol de conexión, debe especificar la siguiente información:  
  
- Utilice el atributo `ConnectionRole.Name` para especificar un nombre de rol.  
  
- Utilice el atributo `ConnectionRole.Description` para agregar una descripción de rol.  
  
- Utilice el atributo `ConnectionRole.Category` para especificar una categoría de rol. Los valores posibles para este atributo se definen en el conjunto de opciones globales de `connectionrole_category`.  
  
- Al crear un rol de conexión, puede especificar el tipo de entidad al que se aplicará el rol, como cliente potencial, cuenta o competidor. Si no especifica un tipo específico de la entidad, puede aplicar un rol de conexión a todas las entidades de Common Data Service. Para especificar el tipo de entidad, use el atributo `ConnectionRoleObjectTypeCode.AssociatedObjectTypeCode`. Para vincular el rol de conexión a un determinado tipo de entidad, use el atributo `ConnectionRoleObjectTypeCode.ConnectionRoleId`. Distintos registros de código de tipo de objeto de rol de conexión pueden hacer referencia a un registro de rol de conexión. Si quita todas las referencias al registro de rol de conexión, puede aplicar este rol de conexión a todas las entidades de Common Data Service.  
  
  > [!TIP]
  >  Para buscar los roles de conexión de una entidad de cuenta, especifique en la consulta todos los roles vinculados a la entidad de cuenta (código de tipo de entidad = 1) o a todas las entidades (código de tipo de entidad = 0).  
  
## <a name="associate-and-disassociate-connection-roles"></a>Asociar y anular asociación de roles de conexión  
 Para asociar los roles de la conexión, use el método de <xref:Microsoft.Xrm.Sdk.IOrganizationService.Associate*>. Para anular la asociación de roles, use el método de <xref:Microsoft.Xrm.Sdk.IOrganizationService.Disassociate*>. Para obtener más información sobre el mensaje `Associate` y el mensaje `Disassociate`, vea [Introducción a las entidades de Dynamics 365](/dynamics365/customer-engagement/developer/introduction-entities).  
  
### <a name="see-also"></a>Vea también  
 [Entidades de conexión](connection-entities.md)   
 [Código de ejemplo para entidades de conexión](/dynamics365/customer-engagement/developer/sample-code-connection-entities)   
 [Ejemplo: Crear un rol de conexión recíproca (enlace en tiempo de compilación)](/dynamics365/customer-engagement/developer/sample-create-reciprocal-connection-role-early-bound)   
 [Entidad de conexión](/reference/entities/connection.md)