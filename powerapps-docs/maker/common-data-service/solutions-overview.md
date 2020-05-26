---
title: Trabajar con soluciones en Power Apps | Microsoft Docs
description: Aprenda cómo se distribuyen las soluciones
ms.custom: ''
ms.date: 01/21/2020
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: ece68f5f-ad40-4bfa-975a-3e5bafb854aa
caps.latest.revision: 55
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 1838f1303d706ab7b9c2ec7356a4ad447a6d0d23
ms.sourcegitcommit: c6906775005aec98973b1f5c3dbe5924aff6d26e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "3341407"
---
# <a name="solutions-overview"></a>Información general de las soluciones  

En Power Apps, las soluciones se aprovechan para transportar aplicaciones y componentes desde un entorno a otro o para aplicar un conjunto de personalizaciones a aplicaciones existentes. Una solución puede contener una o varias aplicaciones así como otros componentes como mapas del sitio, entidades, procesos, recursos web, los conjuntos de opciones, etc.  Puede obtener una solución de [AppSource](https://appsource.microsoft.com/) o de un proveedor de software independiente (ISV).
  
Más información: [Conceptos de soluciones](/power-platform/alm/solution-concepts-alm)
  
> [!NOTE]
>  Si es un ISV que crea una aplicación que va a distribuir, deberá usar soluciones. Para obtener más información acerca del uso de soluciones, vea [Guía para desarrolladores: Introducción a soluciones](/powerapps/developer/common-data-service/introduction-solutions).  
  

<a name="BKMK_SolutionComponents"></a>   
## <a name="components"></a>Componentes  
 Un componente representa algo que puede personalizar. Todo lo que se puede incluir en una solución es un componente. Para ver los componentes incluidos en una solución, en el explorador de soluciones vaya a **Configuración** > **Soluciones** y luego abra la solución que desee. Los componentes se enumeran en la lista **Componentes**. Tenga en cuenta que no puede editar los componentes contenidos en un solución administrada. 

> [!div class="mx-imgBorder"] 
> ![Componentes de la solución](media/components-in-solution.png "Componentes de la solución") 

Para ver una lista de los tipos de componentes que se pueden agregar a cualquier solución, vea [Opciones de tipo de componente ](../../developer/common-data-service/reference/entities/solutioncomponent.md#componenttype-options). 

Para obtener más información sobre las soluciones, consulte estos artículos: 
- [Conceptos de soluciones](/power-platform/alm/solution-concepts-alm)
- [Capas de soluciones](/power-platform/alm/solution-layers-alm)
- [Comprender cómo se combinan soluciones administradas](/power-platform/alm/how-managed-solutions-merged)
- [Usar una solución para personalizar](/power-platform/alm/use-solutions-for-your-customizations)
- [Propiedades administradas](/power-platform/alm/managed-properties-alm)
- [Usar soluciones segmentadas](/power-platform/alm/segmented-solutions-alm)
- [Actualizar una solución](/power-platform/alm/update-solutions-alm)


<!-- The following is a list of components that you can view in a solution:  
  
-   AI Model

-   Application Ribbon  
  
-   Article Template  
  
-   Business Rule  

-   Canvas App 
  
-   Chart  
  
-   Connection Role  
  
-   Contract Template  

-   Custom Connector
 
-   Custom Control
  
-   Dashboard  
  
-   Email Template  
  
-   Entity  
  
-   Entity Relationship  

-   Environment variable
  
-   Field  
  
-   Field Security Profile  

-   Flow
  
-   Form  
  
-   Mail Merge Template  
  
-   Message  

-   Model-driven app
  
-   Option Set  
  
-   Plug-in Assembly  
  
-   Process  

-   Report  

-   Sdk Message Processing Step  
  
-   Security Role  
  
-   Service Endpoint  
  
-   Site Map  

-   Virtual Entity Data Provider

-   Virtual Entity Data Source
  
-   Web Resource  -->
  
 Algunos componentes se anidan en otros componentes. Por ejemplo, una entidad contiene formularios, vistas, gráficos, campos, relaciones de entidad, mensajes y reglas de negocio. Cada uno de los componentes necesita que exista una entidad. Un campo no puede existir fuera de una entidad. Decimos que el campo depende de la entidad. Existe el doble de tipos de componentes que se muestra en la lista anterior, pero la mayoría de ellos no se anidan en otros componentes y no son visibles en la aplicación.  
  
 El objetivo de tener componentes es mantener un seguimiento de las limitaciones sobre lo que se puede personalizar mediante propiedades administradas y todas las dependencias para que se pueda exportar, importar y (en las soluciones administradas) eliminar sin dejar nada atrás.  

<!--  
<a name="BKMK_ManagedAndUnmanagedSolutions"></a>   
## Managed and unmanaged solutions  
 There are **managed** and **unmanaged** solutions. A **managed** solution cannot be modified and can be uninstalled after it is imported. All the components of that solution are deleted by uninstalling the solution.  
  
 When you import an **unmanaged** solution, you add all the components of that solution into your environment. You can’t delete the components by uninstalling the solution.  
  
 When you import an **unmanaged** solution that contains components that you have already customized, your customizations will be overwritten by the customizations in the imported unmanaged solution. You can’t undo this.  
  
> [!IMPORTANT]
>  Install an unmanaged solution only if you want to add all the components to your environment and overwrite any existing customizations.  
  
 Even if you don’t plan on distributing your apps or customizations, you may want to create and use an unmanaged solution to have a separate view that only includes those parts of the application that you have customized. Whenever you customize something, just add it to the unmanaged solution that you created.  
  
 To create a **managed** solution, you choose the **As managed** option when you export the solution. If you create a managed solution, you can’t import it back into the same environment you used to create it. You can only import it into a different environment.  
  
<a name="BKMK_HowSolutionsAreApplied"></a>   
### How solutions are applied  
 All solutions are evaluated as layers to determine what your app will actually do. The following diagram shows how managed and unmanaged solutions are evaluated and how changes in them will appear in your environment.  
  
 ![Solution layering](media/solution-layering.png "Solution layering")  
  
 Starting from the bottom and working up to top:  
  
 **System Solution**  
 The system solution is like a managed solution that every environment has. The system solution is the definition of all the out-of-the box components in the system.  
  
 **Managed Solutions**  
 Managed solutions can modify the system solution components and add new components. If multiple managed solutions are installed, the first one installed is below the managed solution installed later. This means that the second solution installed can customize the one installed before it. When two managed solutions have conflicting definitions, the general rule is “Last one wins”. If you uninstall a managed solution, the managed solution below it takes effect. If you uninstall all managed solution, the default behavior defined within the system solution is applied.  
  
 **Unmanaged Customizations**  
 Unmanaged customizations are any change you have made to your environment through an unmanaged solution. The system solution defines what you can or can't customize by using managed properties. Publishers of managed solutions have the same ability to limit your ability to customize solution components that they add in their solution. You can customize any of the solution components that do not have managed properties that prevent you from customizing them.  
  
 **Application Behavior**  
 This is what you actually see in your environment. The default system solution plus any managed solutions, plus any unmanaged customizations you have applied.  
  
<a name="BKMK_ManagedProperties"></a>   
## Managed properties  
 Some components can’t be customized. These components in the system solution have metadata that prevents you from customizing them. These are called **managed properties**. The publisher of a managed solution can also set the managed properties to prevent you from customizing their solution in ways they don’t want you to.  
  
<a name="BKMK_Dependencies"></a>   
## Solution dependencies  
 Because of the way that managed solutions are layered, some managed solutions can be dependent on solution components in other managed solutions. Some solution publishers will take advantage of this to build solutions that are modular. You may need to install a “base” managed solution first and then you can install a second managed solution that will further customize the components in the base managed solution. The second managed solution depends on solution components that are part of the first solution.  
  
 The system tracks these dependencies between solutions. If you try to install a solution that requires a base solution that isn’t installed, you won’t be able to install the solution. You will get a message saying that the solution requires another solution to be installed first. Similarly, because of the dependencies, you can’t uninstall the base solution while a solution that depends on it is still installed. You have to uninstall the dependent solution before you can uninstall the base solution.  
 
## Solution publisher prefix 

By default, the solution you will work with in Power Apps will be the **Common Data Services Default Solution** which is associated with the **Common Data Service Default Publisher**. The default customization prefix will be randomly assigned for this publisher, for example it could be `cr8a3`. This means that the name of every new item of metadata created for your organization will have this prepended to the names used to uniquely identify the items. 

We recommend that you change the solution publisher prefix so that it will be more meaningful. More information: [Change the solution publisher prefix](change-solution-publisher-prefix.md) -->
  
### <a name="next-steps"></a>Pasos siguientes  
[Usar soluciones en Power Apps](use-solution-explorer.md) <br/>

 
