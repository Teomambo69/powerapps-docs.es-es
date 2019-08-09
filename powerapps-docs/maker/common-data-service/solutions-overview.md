---
title: Trabajar con soluciones en PowerApps | MicrosoftDocs
description: Aprenda cómo se distribuyen las soluciones
ms.custom: ''
ms.date: 05/28/2019
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
---
   
# <a name="solutions-overview"></a>Información general de las soluciones  

  En PowerApps, las soluciones se aprovechan para transportar aplicaciones y componentes desde un entorno a otro o para aplicar un conjunto de personalizaciones a aplicaciones existentes. Una solución puede contener una o varias aplicaciones así como a otros componentes como entidades, conjuntos de opciones, etc. Puede obtener una solución de [AppSource](https://appsource.microsoft.com/) o de un proveedor independiente de software (ISV).
  
Más información: [Notas del producto: Administración del ciclo de vida de las soluciones](https://www.microsoft.com/en-us/download/details.aspx?id=57777)  
  
> [!NOTE]
>  Si es un ISV que crea una aplicación que va a distribuir, deberá usar soluciones. Para obtener más información acerca del uso de soluciones, vea [Guía para desarrolladores: Introducción a soluciones](/powerapps/developer/common-data-service/introduction-solutions).  
  
 Si solo está interesado en crear aplicaciones de PowerApps para el uso de la organización o en personalizar aplicaciones Dynamics 365 for Customer Engagement, esto es lo que necesita saber sobre las soluciones:  
  
-   Crear soluciones es opcional. Puede crear o personalizar aplicaciones en su entorno de PowerApps directamente sin tener que crear una solución.  
  
-   Al personalizar directamente el entorno de PowerApps sin crear ninguna solución, trabaja con una solución especial denominada **Solución predeterminada de Common Data Service**. Esta solución contiene todas las personalizaciones que realiza en el entorno de PowerApps.  
  
-   Hay otra solución especial llamada **Solución predeterminada**. Esta solución contiene todos los componentes en el sistema, es creados por usted o por otros. Puede exportar la **Solución predeterminada** para crear una copia de seguridad de las personalizaciones que ha definido en su organización. Esto es una buena práctica para realizar copia de seguridad de los cambios en un escenario de peor caso.  
  
<a name="BKMK_SolutionComponents"></a>   
### <a name="components"></a>Componentes  
 Un componente representa algo que puede personalizar. Todo lo que se puede incluir en una solución es un componente. La siguiente es una lista de componentes que puede ver en una solución:  
  
-   Cinta de la aplicación  
  
-   Plantilla de artículo  
  
-   Regla de negocio  

-   Aplicación de lienzo 
  
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
  
-   Paso de procesamiento del mensaje de SDK  
  
-   Rol de seguridad   
  
-   Extremo de servicio  
  
-   Mapa del sitio  

-   Proveedor de datos de entidad virtual

-   Origen de datos de entidad virtual
  
-   Recurso web  
  
 Algunos componentes se anidan en otros componentes. Por ejemplo, una entidad contiene formularios, vistas, gráficos, campos, relaciones de entidad, mensajes y reglas de negocio. Cada uno de los componentes necesita que exista una entidad. Un campo no puede existir fuera de una entidad. Decimos que el campo depende de la entidad. Existe el doble de tipos de componentes que se muestra en la lista anterior, pero la mayoría de ellos no se anidan en otros componentes y no son visibles en la aplicación.  
  
 El objetivo de tener componentes es mantener un seguimiento de las limitaciones sobre lo que se puede personalizar mediante propiedades administradas y todas las dependencias para que se pueda exportar, importar y (en las soluciones administradas) eliminar sin dejar nada atrás.  
  
<a name="BKMK_ManagedAndUnmanagedSolutions"></a>   
### <a name="managed-and-unmanaged-solutions"></a>Soluciones administradas y no administradas  
 Hay soluciones **administradas** y **no administradas**. Una solución **administrada** no se puede modificar y puede desinstalarse una vez importada. Todos los componentes de la solución se quitan al desinstalar la solución.  
  
 Cuando importa una solución **no administrada**, debe agregar todos los componentes de la solución a su entorno. No puede quitar componentes desinstalando la solución.  
  
 Cuando importa una solución **no administrada** que contiene componentes que ya personalizó, las personalizaciones se sobrescribirán por las personalizaciones de la solución no administrada importada. No se puede deshacer esto.  
  
> [!IMPORTANT]
>  Instale una solución no administrada si solo desea agregar todos los componentes del entorno y sobrescribir las personalizaciones existentes.  
  
 Incluso si no va a distribuir las aplicaciones o personalizaciones, es posible que desee crear y usar una solución no administrada para tener una vista diferente que solo incluya las partes de la aplicación que ha personalizado. Siempre que personalice algún elemento, agréguelo a la solución no administrada que ha creado.  
  
 Solo puede exportar la **Solución predeterminada** como una solución no administrada.  
  
 Para crear una solución **administrada**, puede elegir la opción **Como administrado** cuando se exporta la solución. Si crea una solución administrada, no puede importarla nuevamente al mismo entorno usado para crearla. Solo puede importarla en otro entorno.  
  
<a name="BKMK_HowSolutionsAreApplied"></a>   
### <a name="how-solutions-are-applied"></a>Cómo se aplican las soluciones  
 Todas las soluciones se evalúan como capas para determinar lo que hace la aplicación hará realmente. En el siguiente diagrama se muestra cómo las soluciones administradas y no administradas se evalúan y cómo los cambios que se realicen en ellas aparecerán en el entorno.  
  
 ![Disposición en capas de la solución](media/solution-layering.png "Disposición en capas de la solución")  
  
 Empezando por abajo y siguiendo hasta el principio:  
  
 **Solución del sistema**  
 La solución del sistema es como una solución administrada que todo entorno tiene. La solución del sistema es la definición de todos los componentes predefinidos del sistema.  
  
 **Soluciones administradas**  
 Las soluciones administradas pueden editar componentes de la solución del sistema y agregar nuevos componentes. Si se instalan varias soluciones administradas, la primera que se instala aparece debajo de la solución administrada instalada más tarde. Esto significa que la segunda solución instalada puede personalizar la que se ha instalado antes. Cuando dos soluciones administradas tienen definiciones en conflicto, la regla general es la "última gana". Si desinstala una solución administrada, la solución administrada siguiente toma efecto. Si desinstala todas las soluciones administradas, el comportamiento predeterminado definido en la solución del sistema se aplica.  
  
 **Personalizaciones no administradas**  
 Las personalizaciones no administradas son los cambios que haya realizado en su entorno a través de una solución no administrada. La solución del sistema define lo que se puede y no se puede personalizar mediante propiedades administradas. Los editores de soluciones administradas tienen la misma capacidad de restringir su capacidad de personalización de los componentes de la solución que agregan a su solución. Puede personalizar cualquier componente de la solución que no tenga propiedades administradas que le impidan personalizarlo.  
  
 **Comportamiento de aplicación**  
 Esto es lo que se ve realmente en su entorno. La solución predeterminada del sistema más todas las soluciones administradas, más todas las personalizaciones no administradas que ha aplicado.  
  
<a name="BKMK_ManagedProperties"></a>   
### <a name="managed-properties"></a>Propiedades administradas  
 Algunos componentes no se pueden personalizar. Estos componentes en la solución del sistema tienen metadatos que impiden personalizarlos. Se denominan **propiedades administradas**. El editor de una solución administrada también puede establecer las propiedades administradas para evitar que personalice su solución de formas que no desea.  
  
<a name="BKMK_Dependencies"></a>   
### <a name="solution-dependencies"></a>Dependencias de soluciones  
 Debido al modo en que las soluciones administradas se estructuran, algunas soluciones administradas pueden ser dependientes de los componentes de la solución en otras soluciones administradas. Algunos editores de soluciones aprovecharán esta característica para crear soluciones modulares. Es posible que tenga que instalar una solución administrada "base" primero y luego puede instalar una segunda solución administrada que personalice aún más los componentes de la solución administrada base. La segunda solución administrada depende de los componentes de la solución que forman parte de la primera solución.  
  
 El sistema sigue estas dependencias entre las soluciones. Si intenta instalar una solución que requiere una solución base que no está instalada, no podrá instalar la solución. Recibirá un mensaje que indica que la solución requiere que se instale otra solución primero. De forma similar, debido a las dependencias, no puede desinstalar la solución base mientras una solución que depende de esta aún está instalada. Es necesario desinstalar la solución dependiente antes de desinstalar la solución base.  
  
  
## <a name="next-steps"></a>Pasos siguientes  
[Importar, actualizar y exportar soluciones](import-update-export-solutions.md) <br/>
[Navegue a una solución específica](navigate-specific-solution.md)
 
