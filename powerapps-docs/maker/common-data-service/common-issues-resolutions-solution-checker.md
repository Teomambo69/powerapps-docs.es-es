---
title: Problemas y soluciones comunes para el Comprobador de soluciones | Microsoft Docs
description: ' Una lista de problemas y soluciones comunes en Comprobador de soluciones'
keywords: ''
ms.date: 02/11/2019
ms.service:
  - powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: caa4e3f2-9700-49b8-87ed-8a68e8878b02
author: jowells1
ms.author: jowells
manager: austinj
ms.reviewer: null
robots: 'noindex,nofollow'
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="common-issues-and-resolutions-for-solution-checker"></a>Problemas y soluciones comunes para el Comprobador de soluciones

En este artículo se enumeran algunos problemas comunes que puede encontrar mientras usa el Comprobador de soluciones. En los casos que correspondan, se proporcionan las soluciones alternativas.

## <a name="solution-checker-runs-fail-due-to-powerapps-checker-version-installed"></a>La ejecución del Comprobador de soluciones falla debido a la versión instalada del Comprobador de PowerApps
El Comprobador de soluciones es una característica que se incluye en la solución del Comprobador de PowerApps.  Si tiene una versión del Comprobador de PowerApps anterior a 1.0.0.47, las ejecuciones del Comprobador de soluciones no se completarán correctamente. Debe actualizar la versión del Comprobador de PowerApps desde [!INCLUDE [pn-dyn-365-admin-center](../../includes/pn-dyn-365-admin-center.md)]. 

Sin embargo, si tiene una versión del Comprobador de PowerApps anterior a 1.0.0.45 instalado, se recomienda eliminar la solución y volver a instalarla. Debido a los cambios recientes de esquema, la actualización del Comprobador de PowerApps de versiones anteriores a 1.0.0.45 puede provocar errores.

Si desea conservar los resultados anteriores del Comprobador de la solución, exporte los resultados de una ejecución anterior o exporte todos los datos del Comprobador de soluciones con [Exportar datos a Excel](../../user/export-data-excel.md) para exportar los datos de las siguientes entidades:

- Componente de análisis
- Trabajo de análisis
- Resultado de análisis
- Detalle de resultado de análisis

### <a name="delete-powerapps-checker"></a>Eliminar el Comprobador de PowerApps

Para eliminar la solución Comprobador de PowerApps:

1. Como administrador del sistema o como personalizador del sistema, abra el portal de PowerApps en https://web.powerapps.com/environments.
2. Seleccione **Solución**.
3. Seleccione **Comprobador de PowerApps** y, a continuación, en la barra de herramientas de soluciones seleccione **Eliminar**.

### <a name="add-powerapps-checker"></a>Agregar el Comprobador de PowerApps

Para volver a agregar el Comprobador de PowerApps a su entorno de Common Data Service:

1. Como administrador del sistema o como personalizador del sistema, abra el portal de PowerApps en https://web.powerapps.com/environments.
2. Seleccione **Solución**.
3. En la barra de herramientas de soluciones, seleccione **Comprobador de soluciones** y, a continuación, seleccione **Instalar**.

## <a name="runs-on-large-solutions-fail"></a>Error de la ejecución en soluciones pesadas

Hay un par de escenarios que puede suceder si una solución es demasiado grande. Estas escenarios se describen a continuación. La solución a cada escenario es crear soluciones más pequeñas con menos componentes para analizar. Si el gran tamaño del archivo de la solución se debe a componentes de ensamblado de complementos, consulte las instrucciones en [Optimizar el desarrollo de ensamblados personalizados](../../developer/common-data-service/best-practices/business-logic/optimize-assembly-development.md).

Comprobador de soluciones puede generar errores al comprobar una solución basada en estos escenarios:
- Limitación dura de un límite de tamaño de archivo de solución de 30 MB.  
- Tiempo de espera de 10 minutos para exportar una solución desde el entorno de Common Data Service. Las soluciones pesadas, como la solución predeterminada, puedan experimentar errores para poder exportarse en este intervalo y la comprobación no se completará correctamente. El Comprobador de soluciones lo volverá a intentar tres veces antes de que dé erro en el trabajo, por lo que pueden pasar más de 30 minutos antes de que reciba una notificación de error.

Para solucionar estos problemas, seleccione o cree soluciones más pequeñas para el análisis. Para reducir los falsos positivos, asegúrese de agregar las personalizaciones dependientes. Cuando cree una solución y agregue estos componentes, incluya lo siguiente:

- Cuando agregue complementos, incluya las Pasos de procesamiento de mensajes de SDK para el complemento.
- Cuando agregue formularios de entidades, incluya los recursos web de JavaScript que se adjuntan a los eventos de formulario.  
- Cuando agregue recursos web de JavaScript, incluya cualquier recurso web de JavaScript dependiente.
- Cuando agregue recursos web de HTML, incluya cualquier dependiente script que esté definido en el recurso web HTML.
- Cuando agregue flujos de trabajo personalizados, incluya el ensamblado que se usa en el flujo de trabajo.

## <a name="solution-checker-run-or-download-results-dont-complete"></a>No se completa la creación de los resultados de la ejecución o descarga del Comprobador de soluciones 
Poco después ejecutar el Comprobador de soluciones, la operación no se completa y aparece el mensaje siguiente:<br />
“No pudimos ejecutar la comprobación en la solución *SOLUTIONNAME*. Intente ejecutarla de nuevo”. <br />
![No se pudo ejecutar](media/solution-checker-werent-able-to-run.png)

Este problema se produce porque la organización está en estado de **modo de administración** y el Comprobador de soluciones no puede validar los permisos del usuario que ejecuta la solicitud. Para resolver este problema, deshabilite el modo de administración. 

### <a name="disable-administration-mode-for-an-instance"></a>Deshabilitar el modo de administración en una instancia
1. Acceda al selector de instancias de Dynamics 365 for Customer Engagement: https://port.crm.dynamics.com/G/Instances/InstancePicker.aspx
2. Seleccione la instancia que tiene problemas de ejecución del Comprobador de soluciones.
3. Seleccione **ADMINISTRACIÓN**.<br />
![Instancia Admin](media/solution-checker-instance-admin.png)

4. Desmarque **Habilitar modo de administración**. <br />
![Deshabilitar el modo de administración](media/solution-checker-instance-disable-admin-mode.png)

5. Volver a ejecutar el Comprobador de soluciones

## <a name="solution-checker-will-not-process-patched-solutions"></a>El Comprobador de soluciones no procesa las soluciones con parches

Si a una solución se le han aplicado [parches](https://docs.microsoft.com/powerapps/developer/common-data-service/create-patches-simplify-solution-updates), el Comprobador de soluciones no podrá exportar la solución para analizarla. Cuando se aplicaron parches a una solución, la solución original pasa a bloquearse y no se puede cambiarla o exportarla mientras haya revisiones dependientes que existan en la organización que identifica la solución como solución primaria.

Para solucionar este problema, clone la solución para que todos los parches relacionados con la solución se implementen en una solución recién creada. Esto desbloquea la solución y permite exportarla desde el sistema. Más información: [Clonar una solución](use-segmented-solutions-patches-simplify-updates.md#clone-a-solution)

## <a name="line-number-references-for-issues-in-html-resources-with-embedded-javascript-are-not-correct"></a>Las referencias de número de línea para problemas en los recursos de HTML con JavaScript insertada no son correctas 

Cuando se procesan recursos web HTML en el Comprobador de soluciones, el recurso web HTML se procesa independientemente de JavaScript en el recurso de web HTML. Por este motivo, el número de número de línea de la infracción detectada en `<script>` del recurso web HTML no es correcto.

## <a name="web-unsupported-syntax-issue-for-web-resources"></a>Problema de sintaxis web no admitida para recursos web

ECMAScript 6 (2015) o las versiones posteriores no se admiten actualmente en el Comprobador de soluciones. Cuando el Comprobador de soluciones analiza JavaScript con ECMAScript 6 o versiones posteriores, se registra un problema de sintaxis web no admitida para el recurso web.  

## <a name="see-also"></a>Vea también
[Prácticas recomendadas e instrucciones para Common Data Service](../../developer/common-data-service/best-practices/index.md)<br />
[Prácticas recomendadas e instrucciones para aplicaciones basadas en modelos](../../developer/model-driven-apps/best-practices/index.md)<br />
