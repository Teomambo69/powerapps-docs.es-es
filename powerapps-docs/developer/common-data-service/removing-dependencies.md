---
title: Eliminar dependencias (Common Data Service) | Microsoft Docs
description: Las dependencias a veces pueden bloquear las operaciones. Este artículo describe cómo se pueden eliminar las dependencias.
ms.custom: ''
ms.date: 04/28/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: ccdietrich
ms.author: cdietric
manager: shmcarth
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3c0227ac41dce2fe28f27d1ac92401fa4d6f476d
ms.sourcegitcommit: 94d66a2e1bc7f45f1a8ae97cc5ec4fce89aefdee
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2020
ms.locfileid: "3325708"
---
# <a name="removing-dependencies"></a>Eliminar dependencias

Las dependencias son registros creados automáticamente por el marco de soluciones para evitar acciones que, si se ejecutan sin control, podrían causar problemas. A medida que se modifican y amplían los componentes, se crean dependencias para indicar, por ejemplo, que se requiere un campo para que un formulario funcione.
Si alguna vez intenta ejecutar una acción que dará como resultado la eliminación de ese campo, el formulario dejará de funcionar.

Existen dependencias para evitar que los componentes requeridos se eliminen mientras que uno o más componentes dependientes aún tienen una referencia.

> [!NOTE]
> La palabra *eliminar*, tal como se utiliza en el contexto de este documento, debe entenderse como la eliminación completa del componente del sistema.

En este artículo discutiremos cómo manejar estas dependencias y las estrategias que se pueden usar para eliminar las dependencias que ya no se necesitan.

Primero, es importante aclarar que las dependencias solo evitan las operaciones que causarían la eliminación de un componente requerido y las acciones que pueden eliminar un componente son diferentes dependiendo de su estado:

- **No gestionado**: los componentes en este estado están representados por una sola capa en la solución activa. Ninguna operación **Eliminar** para el componente da como resultado su eliminación completa.

 - **Gestionado**: la eliminación de componentes administrados depende de múltiples factores: número de capas de solución, posición relativa de la capa que se está desinstalando y los editores de componentes. Por ejemplo, cuando se elimina un componente, considere los siguientes escenarios y lo que se espera cuando se desinstala:

     ![Desinstalar con una sola capa](media/solution-managed-uninstall-scenario-01.png "Desinstalar con una sola capa")

    - Solución 1: provoca la eliminación de un componente, ya que es la única capa para el componente.

    ![Desinstalar con dos capas: editor diferente](media/solution-managed-uninstall-scenario-02.png "Desinstalar con dos capas: editor diferente")

    - Solución 2: no causa la eliminación de un componente. Solo se eliminará esa capa.
    - Solución 1: provoca la eliminación de un componente ya que la acción ocurre en la capa base. De hecho, la solución 1 no se puede desinstalar en este caso porque hay una solución de un editor diferente que extiende el componente.

    ![Desinstalar con múltiples capas: editor diferente](media/solution-managed-uninstall-scenario-03.png "Desinstalar con múltiples capas: editor diferente")
    
     - Solución 3: no causa la eliminación de un componente. Solo se eliminará esa capa.
     - Solución 2: no causa la eliminación de un componente. Solo se eliminará esa capa.
     - Solución 1: no causa la eliminación de un componente. En este caso, hay otra solución del mismo editor (solución 3). La plataforma elimina la capa de la solución 1 y la reemplaza con la capa de la solución 3.

    ![Desinstalar con dos capas: personalización no administrada](media/solution-managed-uninstall-scenario-04.png "Desinstalar con dos capas: personalización no administrada")

      - Activa: no causa la eliminación de un componente. Solo se eliminará esa capa. Observe que no puede desinstalar la solución activa, pero puede eliminar componentes utilizando la característica **Eliminar personalización activa**.
      - Solución 1: causa la eliminación de un componente. La acción ocurre en la capa base. A diferencia del escenario 2, puede desinstalar la solución 1. La solución activa no se considera una extensión y se eliminarán ambas filas.

## <a name="dependency-dialog"></a>Diálogo de dependencia

El diálogo de dependencia es donde puede enumerar las dependencias para la solución seleccionada. Puede ser invocado:

- Haciendo clic en el botón **Mostrar dependencias** en la página de la solución.
- Intentando desinstalar una solución, y la plataforma detecta que existen dependencias.

Por ejemplo:

![Diálogo de dependencia con dependencias](media/dependency-dialog-with-dependencies.png "Diálogo de dependencia con dependencias")

El diálogo **Detalles de dependencia** tiene 6 columnas, que se describen a continuación:

- **Nombre para mostrar**: nombre descriptivo del componente requerido. Cada componente puede mostrar datos ligeramente diferentes para facilitar la identificación. En la figura de ejemplo, puede ver que la entidad solo tiene su nombre, mientras que el campo tiene su nombre y el nombre de la entidad principal.
- **Nombre/id.**: nombre interno del componente requerido.
- **Tipo**: tipo del componente requerido.
- **Requerido por**: nombre descriptivo del componente que lo requiere (el componente dependiente). Si el componente tiene una página de personalización, se convierte en un enlace que abre esa página.
- **Tipo dependiente**: tipo del componente dependiente.
- **Capas de soluciones**: enlace donde puede ver más detalles sobre los componentes involucrados en la dependencia.

> [!NOTE]
> El componente requerido es el que desea eliminar. El componente dependiente es el que tiene referencias al componente requerido. Para eliminar una dependencia, debe realizar cambios que afecten al componente dependiente, no al componente requerido.

## <a name="diagnosing-dependencies"></a>Diagnóstico de dependencias

Tengamos en cuenta el escenario siguiente. La siguiente organización tiene dos soluciones: "Solución - Flujo de trabajo" y "Solución - Entidad personalizada".

![Lista de soluciones con dos soluciones](media/solution-list-custom-entity-workflow.png "Lista de soluciones con dos soluciones")

El propietario de la organización decidió que ya no necesitaban la "Solución - Entidad personalizada", trató de eliminarla y se le presentó el siguiente diálogo:

![Diálogo de dependencia con dependencias](media/dependency-dialog-with-dependencies.png "Diálogo de dependencia con dependencias")

Sin entrar en detalles, podemos concluir que la desinstalación de la solución está tratando de eliminar una entidad llamada "Entidad personalizada" y tres campos "Entidad personalizada", "Nombre" y "Campo de número" donde los 4 componentes tienen dependencias.

> [!NOTE]
> La solución puede estar eliminando más componentes, pero como no tienen dependencias, no aparecen en la lista.

El siguiente paso es verificar las Capas de solución (enlace en la columna de la derecha) para cada dependencia. Eso ayudará a definir cuál es la acción requerida para eliminar la dependencia.

Entidad (Entidad personalizada) y Proceso (Flujo de trabajo de prueba):

![Dependencia entre Entidad (Entidad personalizada) y Flujo de trabajo (Mi aplicación)](media/solution-dependency-solution-history-02.png "Dependencia entre Entidad (Entidad personalizada) y Mapa del sitio (Mi aplicación)")

Según los datos que se muestran, puede ver que el componente dependiente pertenece a una solución llamada SolutionWorkflow. Para eliminar esta dependencia, podemos:

- Actualizar la definición del flujo de trabajo de SolutionWorkflow eliminando cualquier referencia a la entidad o sus subcomponentes. Luego, **Actualizar** o **Mejorar** la solución.
- Desinstalar la solución SolutionWorkflow.
- Eliminar el flujo de trabajo de una nueva versión de la solución SolutionWorkflow y realizare una **Mejora**.

Como cualquier componente dependiente puede detener la eliminación de la solución, le recomendamos que verifique todas las dependencias y realice todos los cambios necesarios en una sola operación.

Entidad (Entidad personalizada) y Aplicación controlada por modelo (Mi aplicación):

![Dependencia entre Entidad (Entidad personalizada) y Mapa del sitio (Mi aplicación)](media/solution-dependency-solution-history-01.png "Dependencia entre Entidad (Entidad personalizada) y Mapa del sitio (Mi aplicación)")

Según los datos que se muestran, puede ver que el componente dependiente pertenece a una solución llamada Active. Esto indica que la dependencia se creó importando una solución no administrada o mediante una personalización no administrada ejecutada a través de la UI o API moderna.

Para eliminar esta dependencia, puede:

- Editar la definición de la aplicación basada en modelo para eliminar cualquier referencia a la entidad o sus subcomponentes. Dado que las aplicaciones basadas en modelo admiten la publicación, debe publicar sus cambios.
- Eliminar la aplicación basada en modelo.

> [!NOTE]
> Desinstalar una solución no administrada no es una opción para eliminar esta dependencia, porque las soluciones no administradas son solo medios para agrupar componentes.

## <a name="actions-to-remove-a-managed-dependency"></a>Acciones para eliminar una dependencia administrada

Las dependencias administradas son aquellas en las que el componente dependiente está asociado a un solución administrada. Para resolver este tipo de dependencia, debe actuar sobre la solución donde se agregó el componente. Esa acción puede ser diferente según lo que intente hacer:

- Si está intentando desinstalar una solución:

    1. En la organización de destino, inspeccione el enlace Capas de solución para encontrar cuál es la solución más importante en la lista del componente dependiente.
    1. En la organización de origen, prepare una nueva versión de esa solución donde: la solución no contiene el componente dependiente, o tiene una versión actualizada del componente dependiente que no contiene referencias al componente requerido. Su objetivo es eliminar cualquier referencia a los componentes necesarios en la nueva versión de la solución.
    1. Exporte la nueva versión de la solución.
    1. En la organización de destino, **mejore** esa solución.

A continuación, vuelva a intentar la desinstalación.

- Si está intentando actualizar una solución: en este caso, debe confirmar que eliminar el componente requerido es una acción intencional (recuerde que las dependencias se aplican solo en los componentes que se eliminan).

  Si no fue intencional, el enfoque correcto es corregir la nueva versión de la solución agregando el componente nuevamente. Para ello, debe hacer lo siguiente:

    1. En la organización de destino, desinstale la solución por etapas (la solución que termina en _Upgrade).
    2. En la organización de origen, agregue los componentes necesarios de nuevo a la solución.
    3. Exporte la nueva versión.
    4. Reintente la mejora.

  Si la eliminación es intencional, debe eliminar la dependencia. Los posibles pasos son los mismos descritos en la viñeta anterior.

### <a name="layers-and-dependencies"></a>Capas y dependencias

Los componentes dependientes pueden estar dispuestos en capas, por lo que es posible que deba cambiar más de una solución para eliminar por completo una dependencia. El marco de dependencia solo calcula dependencias entre las capas superiores para los componentes necesarios y dependientes. Eso significa que debe trabajar desde la parte superior hasta la parte inferior de las soluciones del componente dependiente.

Tenga en cuenta el escenario siguiente:

![Dependencia entre Entidad (Entidad personalizada) y Mapa del sitio (Mi aplicación)](media/solution-dependency-multiple-layers.png "Dependencia entre Entidad (Entidad personalizada) y Mapa del sitio (Mi aplicación)")

Intenta desinstalar "Solución - Entidad personalizada" y la operación está bloqueada por dependencias:

![Dependencias que bloquean la desinstalación de la solución: entidad personalizada](media/solution-dependency-layers-and-dependencies-dependency-dialog-01.png "Dependencias que bloquean la desinstalación de "Solución: entidad personalizada"")

Comienza a diagnosticar la dependencia haciendo clic en "Capas de solución" en el Atributo (new_numberfield) y el Flujo de trabajo (flujo de trabajo de prueba). Ve la siguiente pantalla:

![Dependencia entre Atributo (new_numberfield) y Flujo de trabajo (flujo de trabajo de prueba)](media/solution-dependency-layers-and-dependencies-solution-history-01.png "Dependencia entre Atributo (new_numberfield) y Flujo de trabajo (flujo de trabajo de prueba)")

Dado que las dependencias se crean solo entre las capas superiores de cada componente, el primer paso es tratar la dependencia entre el Atributo (new_numberfield) en SolutionCustomEntity y el Flujo de trabajo (flujo de trabajo de prueba) en SolutionWorkflow3.

Para eliminar la dependencia, decidió desinstalar SolutionWorkflow3. Lo hizo, pero cuando intentó desinstalar la solución una vez más, se le presenta el mismo cuadro de diálogo:

![Dependencias que bloquean la desinstalación de la solución: entidad personalizada](media/solution-dependency-layers-and-dependencies-dependency-dialog-02.png "Dependencias que bloquean la desinstalación de "Solución: entidad personalizada"")

Pero el Atributo (new_numberfield) ya no aparece en la lista, incluso si tenía más capas.

## <a name="actions-to-remove-an-unmanaged-dependency"></a>Acciones para eliminar una dependencia no administrada

Para eliminar dependencias no administradas, debe actuar directamente sobre los componentes, no en las soluciones a las que pertenecen. Por ejemplo, si desea eliminar las dependencias entre un atributo y un formulario, debe editarlo en le Editor de formularios y eliminar el atributo del formulario. La dependencia se eliminará después de seleccionar **Guardar** y **Publicar**.

> [!NOTE]
> También puede eliminar el componente dependiente. Esa acción elimina todas las dependencias junto con el componente.

Para ver las dependencias de un componente, debe ubicarlo en la página de personalizaciones y hacer clic en **Mostrar dependencias**.

Por ejemplo, dado un campo:

![Mostrar dependencias](media/solution-dependency-layers-and-dependencies-component-show-dependencies.png "Mostrar dependencias")

El diálogo tiene dos partes distintas:

![Dependencias de componente](media/solution-dependency-layers-and-dependencies-component-dependency-dialog.png "Mostrar componente")

  - Componentes dependientes: lista de componentes que dependen del campo seleccionado. En otras palabras, los componentes que tendrán este campo F = como componente requerido.
  - Componentes requeridos: lista de componentes que este campo requiere para funcionar. En otras palabras, los componentes que tendrán este campo como componente dependiente.

Los escenarios más comunes: (requerido y dependiente)

## <a name="field-and-workflow"></a>Campo y flujo de trabajo

Para eliminar dependencias entre campos (atributos) y flujos de trabajo (procesos), debe ubicar el flujo de trabajo en la página **Personalizaciones**.

Con el flujo de trabajo abierto, necesita encontrar la referencia al componente del que ya no desea que dependa el flujo de trabajo. En este ejemplo, puede ver el campo (Campo de número) al que se hace referencia en un paso:

![Editar flujo de trabajo](media/solution-dependency-component-workflow.png "Editar flujo de trabajo")

Elimine (o cambie) el paso y luego guarde el flujo de trabajo.

## <a name="field-and-view"></a>Campo y vista

Para eliminar dependencias entre campos (atributos) y vistas (consultas guardadas), debe ubicar la vista en la página **Personalizaciones**.

En el editor de campo, busque la referencia al componente del que ya no desea que dependa la vista. En este ejemplo, verá que el campo (Campo de número) se utiliza como una columna de selección y un filtro.

![Editar vista](media/solution-dependency-component-view.png "Editar vista")

Elimine ambos, guarde y luego publique la vista.

## <a name="entity-and-model-driven-apps"></a>Entidad y aplicaciones basadas en modelo

Para eliminar dependencias entre entidades y aplicaciones basadas en modelo (Módulo de aplicaciones), debe ubicar la aplicación en la lista **Aplicaciones** de la interfaz de usuario moderna.

![Lista de aplicaciones](media/solution-dependency-component-appmodule-01.png "Lista de aplicaciones")

En el editor, busque la referencia al componente del que ya no desea que dependa la aplicación. En este ejemplo, verá la entidad (Entidad personalizada) en **Vista de entidad**.

![Editor de aplicaciones](media/solution-dependency-component-appmodule-02.png "Editor de aplicaciones")

También inspeccione el mapa del sitio asociado con la aplicación, porque es probable que encuentre referencias allí:

![Editor de mapas de sitios](media/solution-dependency-component-appmodule-03.png "Editor de mapa de aplicaciones")

Elimine todas las referencias, guarde y publique ambas (la aplicación y el mapa del sitio).

> [!NOTE]
> Después de ser editados, los componentes se pueden agregar a las soluciones administradas y transportarse a otras organizaciones para eliminar las dependencias administradas.
  
### <a name="see-also"></a>Vea también  
 [Empaquetar y distribuir extensiones con soluciones de Dynamics 365](/dynamics365/customer-engagement/developer/package-distribute-extensions-use-solutions)   
 [Introducción a las soluciones](introduction-solutions.md)   
 [Planear el desarrollo de la solución](/dynamics365/customer-engagement/developer/plan-solution-development)   
 [Crear, exportar o importar una solución no administrada](create-export-import-unmanaged-solution.md)   
 [Crear, instalar y actualizar una solución administrada](create-install-update-managed-solution.md)   
 [Crear, instalar y actualizar una solución administrada](create-install-update-managed-solution.md)   
 [Desinstalar o eliminar una solución](uninstall-delete-solution.md)   
 [Entidades de solución](/dynamics365/customer-engagement/developer/solution-entities)
