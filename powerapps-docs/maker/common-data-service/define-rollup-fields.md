---
title: Definir campos consolidados con Power Apps | MicrosoftDocs
description: Aprenda a definir campos consolidados
ms.custom: ''
ms.date: 05/23/2018
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
ms.assetid: ff0504a1-01bd-4f9b-b884-7f84911d86c3
caps.latest.revision: 58
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: e0c254635d6d51ee037ef7865f4b67b72710f319
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "2864012"
---
# <a name="define-rollup-fields-that-aggregate-values"></a>Definir campos consolidados que agregan valores

Los campos consolidados ayudan a los usuarios a obtener ideas sobre los datos supervisando indicadores clave de negocio. Un campo consolidado contiene un valor agregado calculado a través de los registros relacionados con un registro específico. Esto incluye entidades normales y entidades de actividad, como correos electrónicos y citas.

En situaciones más complejos, puede agregar datos a la jerarquía de registros. Como administrador o personalizador, puede definir campos consolidados mediante las herramientas de personalización de Power Apps, sin necesidad de escribir código.  
  
<a name="BKMK_benefitsandcapabilities"></a> 
 
## <a name="rollup-fields-benefits-and-capabilities"></a>Ventajas y funciones de los campos consolidados  

Las ventajas y funciones de los campos consolidados incluyen lo siguiente:  
  
- La edición visual es fácil. Puede crear campos consolidados utilizando el Editor de campos, como cuando crea un campo regular.  
- Amplia selección de las capacidades agregadas. Puede agregar datos mediante las siguientes funciones: `SUM`, `COUNT`, `MIN`, `MAX` y `AVG`.  
- Soporte de filtro completo para agregado. Puede configurar varios filtros para la entidad de origen o la entidad relacionada mientras establece varias condiciones.  
- Integración sin problemas con la interfaz de usuario. Puede incluir campos consolidados en formularios, vistas, gráficos e informes.  
- Los campos consolidados son componentes de la solución. Puede transportar fácilmente los campos consolidados como componentes entre los entornos y distribuirlos en soluciones.  
- Los campos consolidados y los campos calculados son complementarios entre sí. Puede usar un campo consolidado como parte del campo calculado, y viceversa.  
- Puede configurar campos consolidados para usar controles personalizados.  
  
 Algunos ejemplos de los campos consolidados:  
  
- Ingresos estimados totales de oportunidades abiertas de una cuenta  
- Ingresos estimados totales de oportunidades abiertas de todas las cuentas de una jerarquía  
- Ingresos estimados totales de una oportunidad incluidas oportunidades secundarias  
- Valor estimado total de clientes potenciales calificados generados por una campaña  
- Número de casos abiertos de alta prioridad en todas las cuentas de una jerarquía  
- Hora de creación más temprana de todos los casos abiertos de alta prioridad para una cuenta  
  
Cada campo consolidado crea dos campos accesorios con el patrón de sufijos *&lt;fieldname&gt;*`_date` y *&lt;fieldname&gt;*`_state`. El campo `_date` contiene datos de fecha y hora y el campo `_state` contiene datos de enteros. El campo `_state` tiene los siguientes valores:  
  
|Value|Estado|Descripción|  
|-|-|-|  
|0|NotCalculated|El valor del campo aún está por calcular.|  
|1|Calculado|El valor del campo se ha calculado de acuerdo con la última hora de actualización en el campo _date.|  
|2|OverflowError|El cálculo del valor del campo dio lugar a error de desbordamiento.|  
|3|OtherError|No se pudo calcular el valor del campo debido a un error interno. La siguiente ejecución del trabajo de cálculo lo corregirá probablemente.|  
|4|RetryLimitExceeded|El cálculo del valor del campo produjo un error porque el número máximo de reintentos de calcular el valor se ha excedido debido al número elevado de conflictos de la simultaneidad y bloqueo.|  
|5|HierarchicalRecursionLimitReached|El cálculo del valor del campo produjo un error porque se alcanzó el límite máximo de la profundidad de la jerarquía para el cálculo.|  
|6|LoopDetected|El cálculo del valor del campo produjo error porque se detectó un bucle recursivo en la jerarquía del registro.|  
  
<a name="BKMK_calculations"></a>  
 
## <a name="rollup-calculations"></a>Cálculos consolidados  

Las consolidaciones son calculadas por los trabajos del sistema programados que se ejecutan asincrónicamente en segundo plano. Usted tiene que ser administrador para ver y administrar los trabajos consolidados. 

### <a name="view-rollup-jobs"></a>Ver trabajos consolidados

Para ver los trabajos consolidados:

1. Mientras visualiza la **Solución predeterminada de Common Data Service**, edite la dirección URL, quitando todo lo que hay después de `dynamics.com` y actualizado la página.
2. En el área **Configuración** seleccione **Sistema** > **Trabajos del sistema**.<br />![Navegar a trabajos del sistema](media/navigate-system-jobs.png)
1. En el selector de vistas, elija **Trabajos del sistema periódicos**.
2. Para buscar rápidamente un trabajo relevante, puede filtrar por el tipo de trabajo del sistema: **Cálculo masivo de campos consolidados** o **Calcular campo consolidado**.
 
### <a name="mass-calculate-rollup-field"></a>Cálculo masivo de campos consolidados

El **Cálculo masivo de campos consolidados** es un trabajo periódico, creado por un campo consolidado. Se ejecuta una vez, después de crear o actualizar un campo consolidado. El trabajo recalcula el valor del campo consolidado especificado en todos los registros existentes que contienen este campo. De forma predeterminada, el trabajo se ejecutará 12 horas después de crear o actualizar un campo. Una vez que complete el trabajo, se programa automáticamente para ejecutarse en un futuro lejano, aproximadamente, en 10 años. Si se modifica el campo, el trabajo se reinicializa para ejecutarse de nuevo en 12 horas después de la actualización. El retraso de 12 horas es necesario para garantizar que el **Cálculo masivo de campos consolidados** se ejecuta durante las horas no operativas del entorno. Se recomienda que un administrador ajuste la hora de inicio de un trabajo de **Cálculo masivo de campos consolidados** después de que se cree o se edite el campo consolidado, de tal forma que se ejecute en horas no operativas. Por ejemplo, un buen momento para ejecutar el trabajo podría ser a medianoche, para garantizar un procesamiento eficaz de los campos consolidados.  

### <a name="calculate-rollup-field"></a>Calcular campo consolidado 

**Calcular campo consolidado** es un trabajo periódico que realiza cálculos incrementales de todos los campos consolidados en los registros existentes para una entidad especificada. Solo hay un trabajo de **Calcular campo consolidado** por entidad. Los cálculos incrementales suponen que el trabajo **Calcular campo consolidado** procesa los registros creados, actualizados o eliminados después de la última ejecución terminada del trabajo de **Cálculo masivo de campos consolidados**. El valor de periodicidad predeterminado máximo es una hora. El trabajo se crea automáticamente cuando el primer campo consolidado de una entidad se crea y elimina cuando se elimina el último campo consolidado.  

## <a name="online-recalculation-option"></a>Opción de recálculo en línea
Si coloca el mouse sobre el campo consolidados del formulario, puede ver la hora de la última consolidación y puede actualizar el valor de consolidación seleccionando el icono Actualizar junto al campo, como se muestra a continuación:  

![Campo consolidado en el formulario de cuenta](media/rollup-field-on-account-form.png)
  

Existen algunas consideraciones que debe tener presentes cuando usa la opción recálculo en línea (actualización manual en el formulario):  
  
- Debe tener privilegios de escritura sobre la entidad y derechos de acceso de escritura sobre el registro de origen en el que está solicitando la actualización. Por ejemplo, si está calculando los ingresos estimados de las oportunidades abiertas de una cuenta, no es necesario tener privilegios de escritura en la entidad de oportunidad, únicamente en la entidad de cuenta.  
- Esta opción solo está disponible en modo online. No puede usarla mientras trabaja sin conexión.  
- El número máximo de registros durante la actualización de consolidado se limita a 50.000 registros. En caso de la consolidación jerárquica, esto se aplica a los registros relacionados a través de la jerarquía. Si se supera el límite, recibe un mensaje de error: *Los cálculos no se pueden realizar en línea porque el límite de cálculo de 50.000 registros relacionados se ha alcanzado*. Este límite no se aplica cuando los trabajos del sistema recalculan la consolidación automáticamente.  
- La profundidad máxima de la jerarquía está limitada a 10 para el registro de origen. Si se supera el límite, recibe un mensaje de error: *Los cálculos no se pueden realizar en línea porque se ha alcanzado el límite de profundidad de jerarquía de 10 para el registro de origen*. Este límite no se aplica cuando los trabajos del sistema recalculan la consolidación automáticamente.  

## <a name="modify-rollup-job-recurrence"></a>Modificación de la periodicidad de trabajo consolidado

Como administrador del sistema, puede modificar el patrón de periodicidad del trabajo consolidado, posponer, pausar o reanudar el trabajo consolidado. Sin embargo, no puede cancelar o eliminar un trabajo consolidado. 

Para pausar, posponer, reanudar o editar el patrón de periodicidad, debe ver los trabajos del sistema. Más información [Ver trabajos consolidados](#view-rollup-jobs) 

En la barra de navegación, elija **Acciones** y seleccione la acción que desee. 

Para el trabajo **Cálculo masivo de campos consolidados**, las selecciones disponibles son: **Reanudar**, **Posponer** y **Pausa**. 

Para el trabajo **Calcular campo consolidado**, las selecciones disponibles son: **Modificar periodicidad**, **Reanudar**, **Posponer** y **Pausa**.  
  
<a name="BKMK_businessscenarios"></a>  
 
## <a name="examples"></a>Ejemplos 

Veamos varios ejemplos de campos consolidados. Agregaremos los datos para un registro de los registros relacionados, usando y sin usar una jerarquía. También agregaremos datos para un registro desde actividades relacionadas y actividades relacionadas indirectamente con un registro mediante la entidad ActivityParty. En cada ejemplo, definimos el campo consolidado mediante el Editor de campos. Para abrir el Editor de campo, abra el explorador de soluciones y expanda **Componentes** > **Entidades**. Seleccione la entidad que desee y seleccione **Campos**. Elija **Nuevo**. En el editor, proporcione la información necesaria para el campo, incluidos **Tipo de campo** y **Tipo de datos**. En **Tipo de campo**, seleccione **Consolidado**, después de seleccionar el tipo de datos. Los tipos de datos incluyen decimales o números enteros, divisa y fecha y hora. Elija el botón **Editar** junto a **Tipo de campo**. Esto le llevará al editor de definiciones de campos consolidados. La definición de campo consolidado consta de tres secciones: **Entidad de origen**, **Entidad relacionada** y **Agregado**.  
  
-   En la sección **Entidad de origen**, especifique la entidad para la que se define el campo consolidado y si agrega o no sobre una jerarquía. Puede agregar filtros con varias condiciones para especificar los registros de la jerarquía que desee usar para la consolidación.  
  
-   En la sección **Entidad relacionada**, especifique la entidad sobre la que desea agregar. Esta sección es opcional cuando selecciona consolidar sobre la jerarquía de la entidad de origen. Puede agregar filtros con varias condiciones para especificar qué registros relacionados desea usar en el cálculo. Por ejemplo, se incluyen los ingresos de las oportunidades abiertas con unos ingresos anuales mayores que $1000.  
  
-   En la sección **Agregado**, especifique la métrica que desea calcular. Puede elegir funciones de agregado disponibles, como SUM, COUNT, MIN, MAX o AVG.  
  
### <a name="aggregate-data-for-a-record-from-related-records"></a>Agregar datos para un registro desde registros relacionados  

En este ejemplo, no se usa una jerarquía. Los ingresos estimados totales se calculan para una cuenta, a partir de las oportunidades abiertas relacionadas.  

![Agregar los ingresos estimados para una cuenta](media/rollup-field-no-hierarchy.png)
  
### <a name="aggregate-data-for-a-record-from-the-child-records-over-the-hierarchy"></a>Agregar datos para un registro desde los registros secundarios sobre la jerarquía 
 
En este ejemplo, calculamos los ingresos estimados totales de una oportunidad incluidas las oportunidades secundarias sobre la jerarquía.  
  
![Ingresos estimados agregados, jerarquía de oportunidad](media/rollup-field-hierarchy-self.png)
  
### <a name="aggregate-data-for-a-record-from-the-related-records-over-the-hierarchy"></a>Agregar datos para un registro desde los registros relacionados sobre la jerarquía

En este ejemplo, calculamos los ingresos estimados totales de oportunidades abiertas en todas las cuentas sobre la jerarquía.  
  
![Ingresos estimados agregados sobre jerarquía de cuenta](media/rollup-field-hierarchy.png)  
  
### <a name="aggregate-data-for-a-record-from-all-related-activities"></a>Agregar datos para un registro desde todas las actividades relacionadas
  
En este ejemplo, calculamos el tiempo total invertido y facturado de todas las actividades relacionadas con una cuenta. Esto puede incluir el tiempo empleado en el teléfono, en citas o en actividades personalizadas.  
  
En versiones anteriores, podía definir un campo consolidado para una actividad individual, como una llamada de teléfono, fax, o una cita. Pero, para conseguir el resultado del ejemplo que se muestra a continuación, tenía que calcular el total de los datos mediante los campos calculados. Ahora, puede hacer todo en un paso definiendo un campo consolidado para la entidad Actividad.  
  
![Consolidar todas las actividades para una cuenta](media/rollup-enhancements-activities.png)  
  
### <a name="aggregate-data-for-a-record-from-all-related-activities-and-activities-indirectly-related-via-the-activity-party-entity"></a>Agregar datos para un registro desde todas las actividades relacionadas y actividades relacionadas indirectamente mediante la entidad Grupo de actividad  

En este ejemplo, contamos el número total de correos electrónicos enviados a una cuenta, donde cuenta aparece en la línea "Destinatario Para" o “Destinatario CC". Esto se realiza especificando el **Tipo de participación** en **FILTROS** para la entidad Grupo de actividad en la definición de campo consolidado. Si no usa filtros, todos los tipos de participación disponibles para una actividad se usan en el cálculo. 
 
Para obtener más información acerca de la entidad Grupo de actividad y los tipos de participación disponibles para una actividad determinada, vea [Entidad ActivityParty](/dynamics365/customer-engagement/developer/activityparty-entity).

  
![Actividades relacionadas consolidadas y grupo de actividad](media/rollup-enhancements-indirect-activities.png)  
  
### <a name="aggregate-data-for-a-record-from-related-records-using-the-avg-operator"></a>Agregar datos para un registro desde registros relacionados utilizando el operador AVG

En este ejemplo, calculamos ingresos estimados medios de todas las oportunidades relacionadas con una cuenta.  
  
![Ingresos estimados medios en Dynamics 365](media/rollup-enhancements-average.PNG)  
  
En el siguiente ejemplo se muestra cómo calcular los ingresos estimados medios de oportunidades relacionadas a través de una jerarquía de cuentas. Los ingresos estimados medios se pueden ver en cada nivel de la jerarquía.  
  
![Ingresos estimados medios en Dynamics 365](media/cust-rollup-enhancements-avg-over-hierarchy.png)  
  
<a name="BKMK_considerations"></a> 

## <a name="rollup-field-considerations"></a>Consideraciones sobre los campos consolidados 

Debe conocer determinadas condiciones y restricciones cuando trabaja con campos consolidados:  
  
- Puede definir un máximo de 100 campos consolidados para la organización y de hasta 10 campos consolidados por entidad.  
- Las actualizaciones de campos consolidados no pueden desencadenar un flujo de trabajo.  
- Una condición de espera de flujo de trabajo no puede usar un campo consolidado.  
- No se admite una consolidación sobre un campo consolidado.  
- Un consolidado no puede hacer referencia a un campo calculado que use otro campo calculado, incluso si todos los campos del otro campo calculado están en la entidad actual.  
- La consolidación sólo puede aplicar filtros a la entidad de origen o entidades relacionadas, campos sencillos o campos calculados no complejos.  
- Solo se puede realizar una consolidación sobre entidades relacionadas con la relación 1:N. No se puede realizar una consolidación sobre las relaciones N:N.  
- No se puede realizar una consolidación sobre la relación 1:N para la entidad Actividad o la entidad Grupo de actividad.  
- Las reglas de negocio, los flujos de trabajo o los campos calculados usan siempre el último valor calculado del campo consolidado.  
- Un campo consolidado se agrega en el contexto del usuario del sistema. Todos los usuarios pueden ver el mismo valor de campo consolidado. Puede controlar la visibilidad del campo consolidado con la seguridad de nivel de campo (FLS), limitando quién tiene acceso al campo consolidado. Más información [Seguridad de nivel de campo para controlar el acceso](/dynamics365/customer-engagement/admin/field-level-security). 

### <a name="precision-rounding"></a>Redondeo de precisión
 
Si la precisión del campo agregado es mayor que la precisión del campo consolidado, la precisión del campo agregado se redondea a la precisión del campo consolidado, antes de que se realice la agregación. Para ilustrar este comportamiento miremos un ejemplo específico. Digamos que el campo consolidado en la entidad de cuenta, para calcular los ingresos totales estimados de las oportunidades relacionadas, tiene una precisión de dos decimales. El campo Ingresos estimados de la entidad de oportunidad es el campo agregado con la precisión de cuatro decimales. En nuestro ejemplo, la cuenta tiene dos oportunidades relacionadas. La suma agregada de los ingresos estimados se calcula de este modo:  
  
1. Ingresos estimados para la primera oportunidad: $1000,0041  
1. Ingresos estimados para la segunda oportunidad: $2000,0044  
1. Suma agregada de ingresos Ingresos: 1000,00 $ + 2000,00 $ = 3000,00 $

Como puede ver, la precisión se redondea a dos decimales en el campo agregado antes de que se realice la agregación.  
  
### <a name="different-behavior-from-associated-grids"></a>Diferente comportamiento de cuadrículas asociadas
 
Algunos formularios de entidades, como Cuenta o Contacto, contienen las cuadrículas asociadas de forma predefinida. Por ejemplo, un formulario de cuenta incluye contratos, casos, oportunidades y otras cuadrículas. Algunos de los registros mostrados en las cuadrículas de formulario de cuenta están relacionados directamente con el registro de cuenta; otros, indirectamente, a través de relaciones con otros registros. En comparación, las aplicaciones de agregación de campo consolidado utilizan únicamente relaciones directas definidas forma explícita en la definición del campo consolidado. No se consideran otras relaciones. Para mostrar la diferencia de comportamiento, miremos el siguiente ejemplo.  
  
1. La cuenta A1 tiene un contacto principal, P1. El caso C1 está asociado a la cuenta A1 (C1.campo de cliente = A1) y el caso C2 está asociado al contacto P1 (C2.campo de cliente = P1).  
1. La cuadrícula **Casos** en el formulario **Cuenta** para el registro A1 muestra dos casos, C1 y C2.  
1. El campo consolidado en la entidad de cuenta, denominado Número total de casos, se usa para contar los casos asociados con la cuenta.  
1. En la definición de campo consolidado de cuenta, especificamos los casos que tienen la relación de cliente con la cuenta. Después de la agregación, el Número total de casos es igual a 1 (caso C1). El caso C2 no se incluye en el total, que se relaciona directamente con el contacto, no con la cuenta y no se puede definir explícitamente en la definición del campo consolidado de cuenta. Como resultado, el número total de casos devueltos por la operación consolidada no coincide con el número de casos que se muestra en la cuadrícula **Casos**.  
  
### <a name="see-also"></a>Vea también  

[Crear y editar campos](create-edit-fields.md)<br />
[Definir campos calculados](define-calculated-fields.md)<br />
[Comportamiento y formato del campo de fecha y hora](behavior-format-date-time-field.md)<br />
[Definir y consultar datos relacionados jerárquicamente](define-query-hierarchical-data.md)<br />
[Vídeo: Campos consolidados y calculados](https://www.youtube.com/watch?v=RoahCH1p3T8&list=PLC3591A8FE4ADBE07&index=8)<br />
[Vídeo: Usar Power BI](https://www.youtube.com/watch?v=PkQe4BFlBS8&list=PLC3591A8FE4ADBE07&index=3)
