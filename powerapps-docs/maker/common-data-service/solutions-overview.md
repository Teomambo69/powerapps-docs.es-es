---
title: Trabajar con soluciones en PowerApps | Microsoft Docs
description: Obtenga información sobre cómo se distribuyen las soluciones.
ms.custom: ''
ms.date: 06/21/2018
ms.reviewer: ''
ms.service: crm-online
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
ms.openlocfilehash: 47fb64e650da2f3e1a9e0cf523060cf7d9f5a03b
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39699685"
---
<a name="BKMK_Solutions"></a>   
# <a name="solutions-overview"></a>Información general sobre soluciones  

 Existen soluciones para poder adquirir, compartir o transportar entre organizaciones una aplicación basada en modelos. Puede obtener soluciones de [AppSource](https://appsource.microsoft.com/) o de un fabricante de software independiente (ISV). Una solución es un archivo que se puede importar en un entorno como una aplicación o para aplicar una serie de personalizaciones a una aplicación existente.  
  
Más información: [Whitepaper: Patterns and Principles for Solution Builders](http://go.microsoft.com/fwlink/p/?LinkID=533946) (Notas del producto: patrones y principios para los creadores de soluciones)  
  
> [!NOTE]
>  Si es un ISV que quiere crear una aplicación para distribuirla, deberá usar soluciones. Para más información sobre el uso de soluciones, vea [Empaquetar y distribuir las extensiones con soluciones](https://msdn.microsoft.com/library/gg334530.aspx).  
  
 Si le interesa simplemente crear aplicaciones de PowerApps para uso corporativo o personalizar Dynamics 365, aquí está lo que necesita saber sobre las soluciones:  
  
-   La creación de soluciones es opcional. Puede crear o personalizar las aplicaciones en su entorno de PowerApps directamente sin crear jamás una solución.  
  
-   Al personalizar el entorno de PowerApps directamente, se trabaja con una solución especial denominada **solución predeterminada Common Data Services**. Esta solución contiene todos los componentes del sistema.  
  
-   Puede exportar la solución predeterminada para crear una copia de seguridad de las personalizaciones que haya definido en su organización. Esto es conveniente para tener un escenario del peor caso.  
  
<a name="BKMK_SolutionComponents"></a>   
### <a name="solution-components"></a>Componentes de la solución  
 El componente de una solución representa algo que potencialmente se puede personalizar. Todo lo que puede incluirse en una solución es un componente de la solución. A continuación, se ofrece una lista de componentes de la solución que puede ver en una solución:  
  
-   Cinta de la aplicación  

-   App 
  
-   Plantilla de artículo  
  
-   Regla de negocio  
  
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
  
-   Formulario  
  
-   Plantilla de combinación de correspondencia  
  
-   Mensaje  
  
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
  
 La mayoría de los componentes de una solución se anidan dentro de otros componentes de la solución. Por ejemplo, una entidad contiene formularios, vistas, gráficos, campos, relaciones entre entidades, mensajes y reglas de negocios. Cada uno de esos componentes de la solución requiere la existencia de una entidad. No puede existir un campo fuera de una entidad. Se dice que el campo depende de la entidad. Realmente hay dos veces más tipos de componentes de la solución de los que se muestran en la lista anterior, pero la mayoría de ellos no están visibles en la aplicación.  
  
 El propósito de tener componentes de la solución es realizar un seguimiento de las limitaciones de lo que se puede personalizar con propiedades administradas y todas las dependencias de la solución, para que se pueda exportar, importar y (en las soluciones administradas) eliminar sin dejar nada atrás.  
  
<a name="BKMK_ManagedAndUnmanagedSolutions"></a>   
### <a name="managed-and-unmanaged-solutions"></a>Soluciones administradas y no administradas  
 Una solución **administrada** se puede desinstalar una vez importada. Todos los componentes de la solución se quitan al desinstalar la solución.  
  
 Al importar una solución **no administrada**, agregue todos los componentes de esa solución a la solución predeterminada. No se pueden quitar los componentes mediante la desinstalación de la solución.  
  
 Al importar una solución **no administrada** que contiene los componentes de la solución que ya ha personalizado, las personalizaciones se sobrescribirán con las personalizaciones de la solución no administrada. No se puede deshacer esta operación.  
  
> [!IMPORTANT]
>  Instale una solución no administrada solo si desea agregar todos los componentes a la solución predeterminada y sobrescribir las personalizaciones existentes.  
  
 Incluso si no pretende distribuir la solución, es posible que desee crear y utilizar una solución no administrada para tener una vista independiente que solo incluya las partes de la aplicación que ha personalizado. Cada vez que personalice algo, agréguelo sin más a la solución no administrada que se ha creado.  
  
 La solución predeterminada solo se puede exportar como una solución no administrada.  
  
 Para crear una solución **administrada**, elija la opción de la solución administrada al exportar la solución. Si crea una solución administrada, no puede importarla de nuevo en la misma organización que usó para crearla. Solo se puede importar en una organización diferente.  
  
<a name="BKMK_HowSolutionsAreApplied"></a>   
### <a name="how-solutions-are-applied"></a>Cómo se aplican las soluciones  
 Todas las soluciones se evalúan como capas para determinar lo que la aplicación realmente hará. En el siguiente diagrama se muestra cómo las soluciones administradas y no administradas se evalúan y cómo los cambios realizados en ellas aparecerán en la organización.  
  
 ![Disposición en capas de la solución](media/solution-layering.png "Disposición en capas de la solución")  
  
 Desde la parte inferior y trabajando hacia arriba:  
  
 **Solución del sistema**  
 La solución del sistema es como una solución administrada que todas las organizaciones tienen. La solución del sistema es la definición de todos los componentes listos para usar del el sistema.  
  
 **Soluciones administradas**  
 Las soluciones administradas pueden modificar los componentes de la solución del sistema y agregar nuevos componentes. Si se instalan varias soluciones administradas, la primera que se instala aparece debajo de la solución administrada instalada después. Esto significa que la segunda solución instalada puede personalizar la que se ha instalado antes. Cuando dos soluciones administradas tienen definiciones en conflicto, la regla general es "La última gana". Si desinstala una solución administrada, se aplica la solución administrada debajo de ella. Si se desinstalan todas las soluciones administradas, se aplica el comportamiento predeterminado definido dentro de la solución del sistema.  
  
 **Personalizaciones no administradas**  
 Las personalizaciones no administradas son cualquier cambio que haya realizado en su organización mediante una solución no administrada. La solución del sistema define lo que se puede personalizar y lo que no con el uso de propiedades administradas. Los editores de soluciones administradas tienen la misma capacidad de limitar la posibilidad de personalizar los componentes de la solución que agregan en su solución. Puede personalizar cualquier de los componentes de la solución que no tengan propiedades administradas que impidan personalizarlos.  
  
 **Comportamiento de la aplicación**  
 Esto es lo que realmente se ve en su organización. La solución del sistema predeterminada más todas las soluciones administradas y más todas las personalizaciones no administradas aplicadas.  
  
<a name="BKMK_ManagedProperties"></a>   
### <a name="managed-properties"></a>Propiedades administradas  
 Algunos componentes no se pueden personalizar. Estos componentes de la solución del sistema tienen metadatos que impiden personalizarlos. Se denominan **propiedades administradas**. El editor de una solución administrada también puede establecer las propiedades administradas para evitar personalizar su solución de formas que no desean.  
  
<a name="BKMK_Dependencies"></a>   
### <a name="solution-dependencies"></a>Dependencias de la solución  
 Debido a la forma en que las soluciones administradas están dispuestas en capas, algunas soluciones administradas pueden depender de los componentes de otras soluciones administradas. Algunos editores de soluciones se beneficiarán de esta opción para crear soluciones que modular. Puede que deba instalar una solución administrada "base" en primer lugar y, a continuación, puede instalar una segunda solución administrada que personalizará aún más los componentes de la solución administrada base. La segunda solución administrada depende de los componentes que forman parte de la primera solución.  
  
 El sistema realiza un seguimiento de estas dependencias entre las soluciones. Si intenta instalar una solución que requiere una solución base que no está instalada, no podrá instalar la solución. Obtendrá un mensaje que indica que la solución requiere que se instale otra aplicación primero. De forma similar, debido a las dependencias, no se puede desinstalar la solución base mientras esté instalada una solución que depende de ella. Tendrá que desinstalar la solución dependiente antes de poder desinstalar la solución base.  
  
  
## <a name="next-steps"></a>Pasos siguientes  
[Importación, actualización y exportación de soluciones](import-update-export-solutions.md) <br/>
[Búsqueda de una solución específica](navigate-specific-solution.md)
 
