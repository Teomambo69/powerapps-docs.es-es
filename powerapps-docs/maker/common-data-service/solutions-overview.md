---
title: Trabajar con soluciones en PowerApps | Microsoft Docs
description: Obtenga información sobre cómo se distribuyen las soluciones.
ms.custom: ''
ms.date: 01/28/2019
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
ms.openlocfilehash: da6b44c4755fa42d6e946cfe5955bba0e78b91c2
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "65038614"
---
# <a name="solutions-overview"></a>Información general sobre soluciones  

  En PowerApps, se aprovechan soluciones para transportar aplicaciones y componentes de un entorno a otro o para aplicar un conjunto de personalizaciones a aplicaciones existentes. Una solución puede contener una o varias aplicaciones, así como otros componentes, como entidades, conjuntos de opciones, etc.  Puede obtener soluciones de [AppSource](https://appsource.microsoft.com/) o de fabricantes de software independientes (ISV).
  
Más información: [Notas del producto: Administración del ciclo de vida de la solución](https://www.microsoft.com/en-us/download/details.aspx?id=57777)  
  
> [!NOTE]
>  Si es un ISV que quiere crear una aplicación para distribuirla, deberá usar soluciones. Para más información sobre el uso de soluciones, consulte [Guía del desarrollador: Introducción a las soluciones](/powerapps/developer/common-data-service/introduction-solutions).  
  
 Si está interesado en crear aplicaciones de PowerApps para uso corporativo o en personalizar Dynamics 365 para aplicaciones de Customer Engagement, esto es lo que debe saber sobre las soluciones:  
  
-   La creación de soluciones es opcional. Puede crear o personalizar las aplicaciones en su entorno de PowerApps directamente sin crear jamás una solución.  
  
-   Al personalizar el entorno de PowerApps directamente sin crear una solución, se trabaja con una solución especial denominada **solución predeterminada de Common Data Services**. Esta solución contiene todas las personalizaciones realizadas en el entorno de PowerApps.  
  
-   Hay otra solución especial llamada **solución predeterminada**. Esta solución contiene todos los componentes del sistema, tanto los creados por usted como por otra persona. Puede exportar la **solución predeterminada** para crear una copia de seguridad de las personalizaciones que haya definido en su organización. Es una buena práctica realizar una copia de seguridad de los cambios en la peor situación posible.  
  
<a name="BKMK_SolutionComponents"></a>   
### <a name="components"></a>Componentes  
 Un componente representa algo que potencialmente se puede personalizar. Todo lo que puede incluirse en una solución es un componente. A continuación, se ofrece una lista de componentes que puede ver en una solución:  
  
-   Cinta de la aplicación  
  
-   Plantilla de artículo  
  
-   Regla de negocio  

-   Aplicaciones de lienzo 
  
-   Gráfico  
  
-   Rol de conexión  
  
-   Plantilla de contrato  
 
-   Control personalizado
  
-   Panel  
  
-   Plantilla de correo electrónico  
  
-   Entidad  
  
-   Relación de entidad  
  
-   Campo  
  
-   Perfil de seguridad de campo  

-   Flujo
  
-   Formulario  
  
-   Plantilla de combinación de correspondencia  
  
-   Mensaje  

-   Aplicación basada en modelo
  
-   Conjunto de opciones  
  
-   Ensamblado de complementos  
  
-   Proceso  
  
-   Paso de procesamiento de mensajes de SDK  
  
-   Rol de seguridad  
  
-   Punto de conexión de servicio  
  
-   Mapa del sitio  

-   Proveedor de datos de entidad virtual

-   Origen de datos de entidad virtual
  
-   Recurso web  
  
 Algunos componentes están anidados dentro de otros. Por ejemplo, una entidad contiene formularios, vistas, gráficos, campos, relaciones entre entidades, mensajes y reglas de negocios. Cada uno de esos componentes requiere la existencia de una entidad. No puede existir un campo fuera de una entidad. Se dice que el campo depende de la entidad. En realidad hay dos veces más tipos de componentes de los que se muestran en la lista anterior, pero la mayoría de ellos no están anidados dentro de otros y no son visibles en la aplicación.  
  
 El propósito de tener componentes es mantener el seguimiento de las limitaciones sobre lo que se puede personalizar con propiedades administradas y todas las dependencias, de forma que se pueda exportar, importar y eliminar (en soluciones administradas) sin que quede nada.  
  
<a name="BKMK_ManagedAndUnmanagedSolutions"></a>   
### <a name="managed-and-unmanaged-solutions"></a>Soluciones administradas y no administradas  
 Existen soluciones **administradas** y **no administradas**. Una solución **administrada** no se puede modificar y se puede desinstalar una vez importada. Todos los componentes de la solución se quitan al desinstalar la solución.  
  
 Al importar una solución **no administrada**, se agregan todos los componentes de esa solución al entorno. No se pueden quitar los componentes mediante la desinstalación de la solución.  
  
 Al importar una solución **no administrada** que contiene componentes que ya se han personalizado, las personalizaciones se sobrescribirán con las personalizaciones de la solución no administrada. No se puede deshacer esta operación.  
  
> [!IMPORTANT]
>  Instale una solución no administrada solo si quiere agregar todos los componentes al entorno y sobrescribir las personalizaciones existentes.  
  
 Incluso si no pretende distribuir las aplicaciones o personalizaciones, puede que quiera crear y usar una solución no administrada para tener una vista independiente que solo incluya esas partes de la aplicación que ha personalizado. Cada vez que personalice algo, agréguelo sin más a la solución no administrada que se ha creado.  
  
 La **solución predeterminada** solo se puede exportar como una solución no administrada.  
  
 Para crear una solución **administrada**, elija la opción **Como administrado** al exportar la solución. Si crea una solución administrada, no puede importarla de nuevo al mismo entorno que usó para crearla. Solo se puede importar en un entorno diferente.  
  
<a name="BKMK_HowSolutionsAreApplied"></a>   
### <a name="how-solutions-are-applied"></a>Cómo se aplican las soluciones  
 Todas las soluciones se evalúan como capas para determinar lo que la aplicación realmente hará. En el siguiente diagrama se muestra cómo se evalúan las soluciones administradas y no administradas y cómo aparecen en la organización los cambios realizados en ellas.  
  
 ![Disposición en capas de la solución](media/solution-layering.png "Disposición en capas de la solución")  
  
 Desde la parte inferior y trabajando hacia arriba:  
  
 **Solución del sistema**  
 La solución del sistema es como una solución administrada que tienen todos los entornos. La solución del sistema es la definición de todos los componentes listos para usar del el sistema.  
  
 **Soluciones administradas**  
 Las soluciones administradas pueden modificar los componentes de la solución del sistema y agregar nuevos componentes. Si se instalan varias soluciones administradas, la primera que se instala aparece debajo de la solución administrada instalada después. Esto significa que la segunda solución instalada puede personalizar la que se ha instalado antes. Cuando dos soluciones administradas tienen definiciones en conflicto, la regla general es "La última gana". Si desinstala una solución administrada, se aplica la solución administrada debajo de ella. Si se desinstalan todas las soluciones administradas, se aplica el comportamiento predeterminado definido dentro de la solución del sistema.  
  
 **Personalizaciones no administradas**  
 Las personalizaciones no administradas son cualquier cambio que haya realizado en su entorno mediante una solución no administrada. La solución del sistema define lo que se puede personalizar y lo que no con el uso de propiedades administradas. Los editores de soluciones administradas tienen la misma capacidad de limitar la posibilidad de personalizar los componentes de la solución que agregan en su solución. Puede personalizar cualquier de los componentes de la solución que no tengan propiedades administradas que impidan personalizarlos.  
  
 **Comportamiento de la aplicación**  
 Esto es lo que realmente se ve en su entorno. La solución del sistema predeterminada más todas las soluciones administradas y más todas las personalizaciones no administradas aplicadas.  
  
<a name="BKMK_ManagedProperties"></a>   
### <a name="managed-properties"></a>Propiedades administradas  
 Algunos componentes no se pueden personalizar. Estos componentes de la solución del sistema tienen metadatos que impiden personalizarlos. Se denominan **propiedades administradas**. El editor de una solución administrada también puede establecer las propiedades administradas para evitar personalizar su solución de formas que no desean.  
  
<a name="BKMK_Dependencies"></a>   
### <a name="solution-dependencies"></a>Dependencias de la solución  
 Debido a la forma en que las soluciones administradas están dispuestas en capas, algunas soluciones administradas pueden depender de los componentes de otras soluciones administradas. Algunos editores de soluciones se beneficiarán de esta opción para crear soluciones modulares. Puede que deba instalar una solución administrada "base" en primer lugar y, a continuación, puede instalar una segunda solución administrada que personalizará aún más los componentes de la solución administrada base. La segunda solución administrada depende de los componentes que forman parte de la primera solución.  
  
 El sistema realiza un seguimiento de estas dependencias entre las soluciones. Si intenta instalar una solución que requiere una solución base que no está instalada, no podrá instalar la solución. Obtendrá un mensaje que indica que la solución requiere que se instale otra aplicación primero. De forma similar, debido a las dependencias, no se puede desinstalar la solución base mientras esté instalada una solución que depende de ella. Tendrá que desinstalar la solución dependiente antes de poder desinstalar la solución base.  
  
  
## <a name="next-steps"></a>Pasos siguientes  
[Importación, actualización y exportación de soluciones](import-update-export-solutions.md) <br/>
[Búsqueda de una solución específica](navigate-specific-solution.md)
 
