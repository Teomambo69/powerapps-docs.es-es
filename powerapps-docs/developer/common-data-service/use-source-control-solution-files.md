---
title: Control de código fuente con archivos de solución(Common Data Service) | Microsoft Docs
description: La herramienta SolutionPackager puede usarse con cualquier sistema de control de código fuente. Cuando un archivo .zip de solución se extrae a una carpeta, simplemente agregue y envíe los archivos al sistema de control de código fuente. Estos archivos se pueden sincronizar a continuación en otro equipo donde se pueden comprimir en un nuevo archivo .zip de solución idéntico.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: shmcarth
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 77e938315461948c5dc5507f68be290560e728d2
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749658"
---
# <a name="source-control-with-solution-files"></a>Control de código fuente con archivos de solución

La herramienta SolutionPackager puede usarse con cualquier sistema de control de código fuente. Cuando un archivo .zip de solución se extrae a una carpeta, simplemente agregue y envíe los archivos al sistema de control de código fuente. Estos archivos se pueden sincronizar a continuación en otro equipo donde se pueden comprimir en un nuevo archivo .zip de solución idéntico.  
  
 Un aspecto importante al usar los archivos componentes extraídos en el control de código fuente es que agregar todos los archivos al control de código fuente puede causar duplicación innecesaria. Consulte [Referencia de archivo de componente de la solución](solution-component-file-reference-solutionpackager.md) para ver qué archivos se generan para cada tipo de componente y qué archivos se recomiendan para su uso en el control de código fuente.  
  
 Cuando sean necesarias más personalizaciones y cambios para la solución, los desarrolladores deberán modificar o personalizar los componentes con los medios existentes, exportar de nuevo para crear un archivo .zip y extraer el archivo comprimido de solución en la misma carpeta.  
  
> [!IMPORTANT]
>  Excepto en las secciones que se describen en [al editar el archivo de personalización](../model-driven-apps/when-edit-customization-file.md), edición de manual de los archivos de componente extraídos y archivos .zip no se admiten.  
  
 Cuando la herramienta SolutionPackager extrae los archivos componentes no sobrescribe los archivos componentes existentes del mismo nombre si el contenido del archivo es idéntico. Además, la herramienta respeta el atributo de solo lectura en los archivos componentes generando una advertencia en la ventana de la consola indicando que determinados archivos no se escribirán. Esto permite al usuario comprobar, desde el control de código fuente, el conjunto de archivos mínimo que está modificando. El parámetro de `/clobber` se puede usar para reemplazar y para hacer que los archivos de solo lectura se escriban o eliminen. El parámetro de `/allowWrite` se puede usar para evaluar el impacto que tiene una operación de extracción sin hacer realmente que ningún archivo se escriba o elimine. El uso de parámetros de `/allowWrite` con registro detallado es válido.  
  
 Después de que la operación de extracción se complete con el conjunto de archivos mínimo desprotegido de control de código fuente, un desarrollador puede enviar los archivos cambiados de vuelta al control de código fuente, como se hace con cualquier otro tipo de archivo de código de fuente.  
  
<a name="team_dev"></a>   
## <a name="team-development"></a>Desarrollo de equipo  
 Cuando hay varios desarrolladores que trabajan en el mismo componente de la solución puede surgir un conflicto donde los cambios entre dos desarrolladores provoquen cambios a un archivo único. Esta instancia se minimiza descomponiendo cada componente o subcomponente individualmente editable en un archivo distinto. Tenga en cuenta el siguiente ejemplo.  
  
1. El desarrollador A y B trabajan en la misma solución.  
  
2. En equipos independientes, ambos obtienen los últimos orígenes de la solución del control de código fuente, empaquetan e importan un archivo .zip de solución no administrada en organizaciones de Common Data Service independientes.  
  
3. El desarrollador A personaliza la vista del sistema "Contactos activos" y el formulario principal para la entidad Contacto.  
  
4. El desarrollador B personaliza el formulario principal para la entidad Cuenta y cambia la "Vista de búsqueda de contactos".  
  
5. Ambos desarrolladores exportan un archivo .zip de solución no administrada y lo extraen.  
  
   1.  El desarrollador A necesitará desproteger un archivo para el formulario principal del contacto y otro archivo para la vista "Contactos activos".  
  
   2.  El desarrollador B necesitará desproteger un archivo para el formulario principal de cuenta y otro archivo para la "Vista de búsqueda de contactos".  
  
6. Los desarrolladores pueden enviar, en cualquier orden, porque los cambios respectivos tocan archivos independientes.  
  
7. Después de completarse ambos envíos, pueden repetir el paso #2 y después seguir realizando otros cambios en las organizaciones independientes. Cada uno tiene ambos conjuntos de cambios, sin sobrescritura de su propio trabajo.  
  
   El ejemplo anterior funciona únicamente cuando hay cambios en archivos separados. Es inevitable que las personalizaciones independientes requieran cambios en un archivo único. Según el ejemplo indicado anteriormente, tenga en cuenta que el desarrollador B ha personalizado la vista "Contactos activos" mientras el desarrollador A también la estaba personalizando. En este nuevo ejemplo, el orden de los eventos pasa a ser importante. El proceso correcto para solucionar este problema, indicado por completo, es el siguiente.  
  
8. El desarrollador A y B trabajan en la misma solución.  
  
9. En equipos independientes, ambos obtienen los últimos orígenes de la solución del control de código fuente, empaquetan e importan un archivo .zip de solución no administrada en organizaciones independientes.  
  
10. El desarrollador A personaliza la vista del sistema "Contactos activos" y el formulario principal para la entidad Contacto.  
  
11. El desarrollador B personaliza el formulario principal para la entidad Cuenta y cambia los "Contactos activos".  
  
12. Ambos desarrolladores exportan una solución no administrada. Archivo .zip y extracción.  
  
    1.  El desarrollador A necesitará desproteger un archivo para el formulario principal del contacto y otro archivo para la vista "Contactos activos".  
  
    2.  El desarrollador B necesitará desproteger un archivo para el formulario principal de cuenta y otro archivo para la vista "Contactos activos".  
  
13. El desarrollador Al está listo primero.  
  
    1.  Antes de que se envíe al control de código fuente debe obtener los últimos orígenes para garantizar que ninguna protección anterior entre en conflicto con sus cambios.  
  
    2.  No hay conflictos así que se puede enviar.  
  
14. El desarrollador B está listo siguiendo al desarrollador A.  
  
    1.  Antes de que se envíe debe obtener los últimos orígenes para garantizar que ninguna protección anterior entre en conflicto con sus cambios.  
  
    2.  Hay un conflicto porque el archivo para "Contactos activos" se ha modificado desde que se recuperaron los últimos orígenes.  
  
    3.  El desarrollador B debe solucionar el conflicto. Es posible que las capacidades del sistema de control de código fuente en uso puedan ayudar en este proceso; si no las siguientes opciones son viables.  
  
        1.  El desarrollador B, mediante el historial de control de código fuente, si procede, puede consultar si el desarrollador A realizó el cambio anterior. A través de la comunicación directa pueden discutir cada cambio. A continuación, el desarrollador B tiene que actualizar la organización con la resolución acordada. A continuación, exporta, extrae y sobrescribe el archivo en conflicto y lo envía.  
  
        2.  Permitir que el control de código fuente sobrescriba el archivo local. El desarrollador B empaqueta la solución y la importa a su organización, a continuación evalúa el estado de la vista y vuelve a personalizarla según sea necesario. A continuación, puede exportar, extraer y sobrescribir el archivo en conflicto.  
  
        3.  Si el cambio anterior se considera no necesario, el desarrollador B permite que su copia del archivo sobrescriba la versión en el control de código fuente y la envíe.  
  
    Si trabaja en una organización compartida o en organizaciones independientes, el desarrollo del equipo de soluciones de Common Data Service requiere que los que trabajan activamente con una solución común conozcan el trabajo de otros usuarios. La herramienta SolutionPackager no elimina completamente esta necesidad pero habilita la combinación fácil de cambios que no están en conflicto en el nivel de control de código fuente y resalta de forma proactiva los componentes concisos donde han surgido los conflictos.  
  
    Las secciones siguientes son procesos genéricos para usar eficazmente la herramienta SolutionPackager en el control de código fuente al desarrollar con equipos. Estos funcionan por igual con las organizaciones independientes o con las organizaciones compartidas de desarrollo, aunque con las organizaciones compartidas la exportación y el extracto incluirán naturalmente todos los cambios presentes en la solución, no solo los creados por el desarrollador que realiza la exportación. De forma similar, cuando se importa un archivo .zip de solución se producirá el comportamiento natural de sobrescribir todos los componentes.  
  
<a name="create_sol"></a>   
## <a name="create-a-solution"></a>Crear una solución  
 El siguiente procedimiento identifica los pasos típicos usados al crear una solución por primera vez.  
  
1. En una organización limpia, cree una solución en el servidor de Common Data Service y, a continuación, agregue o cree componentes como sea necesario.  
  
2. Cuando esté listo para proteger, siga estos pasos.  
  
   1.  Exporte la solución no administrada.  
  
   2.  Con la herramienta SolutionPackager, extraiga la solución exportada en los archivos componentes.  
  
   3.  De esos archivos componentes extraídos, agregue los archivos necesarios al control de código fuente.  
  
   4.  Envíe estos cambios al control de origen.  
  
<a name="modify_sol"></a>   

## <a name="modify-a-solution"></a>Modificar una solución  
 El siguiente procedimiento identifica los pasos típicos usados al modificar una solución existente.  
  
1. Sincronice u obtenga los últimos orígenes de archivo componente de la solución.  
  
2. Con la herramienta SolutionPackager, empaquete los archivos componentes en un archivo .zip de solución no administrada.  
  
3. Importe el archivo de la solución no administrada en una organización.  
  
4. Personalice y modifique la solución como sea necesario.  
  
5. Cuando esté listo para comprobar los cambios en el control de origen, haga lo siguiente.  
  
   1.  Exporte la solución no administrada.  
  
   2.  Con la herramienta SolutionPackager, extraiga la solución exportada en los archivos componentes.  
  
   3.  Sincronice u obtenga los últimos orígenes del control de código fuente.  
  
   4.  Solucione los conflictos si los hay.  
  
   5.  Envíe los cambios al control de código fuente.  
  
   Los pasos 2 y 3 deben realizarse antes de que se produzcan más personalizaciones en la organización del desarrollo. En el paso 5, el paso b se debe completar antes que el paso c.  
  
### <a name="see-also"></a>Vea también  
 [Referencia de archivo de componente de la solución (SolutionPackager)](solution-component-file-reference-solutionpackager.md)<br/>  
 [Use la herramienta SolutionPackager para comprimir y extraer un archivo de solución](compress-extract-solution-file-solutionpackager.md)
