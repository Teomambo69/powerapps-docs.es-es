---
title: Definición de campos consolidados con PowerApps | Microsoft Docs
description: Obtenga información sobre cómo definir campos consolidados.
ms.custom: ''
ms.date: 05/23/2018
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
ms.assetid: ff0504a1-01bd-4f9b-b884-7f84911d86c3
caps.latest.revision: 58
ms.author: matp
manager: kvivek
ms.openlocfilehash: c76162747ac2bda27c46895290e5943b7f46739f
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39698709"
---
# <a name="define-rollup-fields-that-aggregate-values"></a>Definición de campos consolidados que agregan valores

Los campos consolidados ayudan a los usuarios a obtener información detallada de los datos mediante la supervisión de métricas empresariales clave. Un campo consolidado contiene un valor agregado calculado en función de los registros relacionados con un registro específico. Esto incluye entidades regulares y entidades de actividad como correos electrónicos y citas.

En escenarios más complejos, puede agregar datos en la jerarquía de registros. Como administrador o personalizador, puede definir campos consolidados mediante el uso de las herramientas de personalización de PowerApps, sin necesidad de escribir código.  
  
<a name="BKMK_benefitsandcapabilities"></a> 
 
## <a name="rollup-fields-benefits-and-capabilities"></a>Ventajas y funcionalidades de los campos consolidados  

Entre las ventajas y las funcionalidades de los campos consolidados se incluyen las siguientes:  
  
- Edición visual sencilla. Puede crear campos consolidados mediante el Editor de campos, al igual que cuando se crea un campo normal.  
- Amplia selección de funciones agregadas. Puede agregar datos utilizando las siguientes funciones: `SUM`, `COUNT`, `MIN`, `MAX` y `AVG`.  
- Soporte de filtro completo para la agregación. Puede definir varios filtros para la entidad de origen o la entidad relacionada al establecer varias condiciones.  
- Integración sin problemas con la interfaz de usuario. Puede incluir los campos consolidados en formularios, vistas, gráficos e informes.  
- Los campos consolidados son componentes de la solución. Fácilmente puede transportar los campos consolidados como componentes entre los entornos y distribuirlos en soluciones.  
- Los campos consolidados y los campos calculados son complementarios entre sí. Puede usar un campo consolidado como parte del campo calculado, y viceversa.  
- Puede configurar los campos consolidados para usar controles personalizados.  
  
 Algunos ejemplos de campos consolidados:  
  
- Total de ingresos estimados de oportunidades abiertas de una cuenta  
- Total de ingresos estimados de oportunidades abiertas de todas las cuentas de una jerarquía  
- Total de ingresos estimados de una oportunidad, incluidas las oportunidades secundarias  
- Valor total estimado de clientes potenciales cualificados generados por una campaña  
- Número de casos abiertos de alta prioridad en todas las cuentas de una jerarquía  
- Primera hora de creación de todos los casos abiertos de alta prioridad para una cuenta  
  
Cada campo consolidado crea dos campos accesorios con el patrón de sufijo *&lt;fieldname&gt;*`_date` y *&lt;fieldname&gt;*`_state`. El campo `_date` contiene datos datetime, y el campo `_state` contiene datos Integer. El campo `_state` tiene los siguientes valores:  
  
|Valor|Estado|Descripción|  
|-|-|-|  
|0|NotCalculated|El valor del campo aún se debe calcular.|  
|1|Calculado|El valor de campo se ha calculado según el campo in _date con la hora de la última actualización.|  
|2|OverflowError|El cálculo del valor de campo resultó en un error de desbordamiento.|  
|3|OtherError|Error en el cálculo del valor de campo debido a un error interno. La siguiente ejecución del trabajo de cálculo posiblemente lo corregirá.|  
|4|RetryLimitExceeded|Error en el cálculo del valor de campo porque se excedió el número máximo de reintentos de cálculo del valor debido a un número elevado de conflictos de simultaneidad y bloqueo.|  
|5|HierarchicalRecursionLimitReached|Error en el cálculo del valor de campo porque se alcanzó el límite máximo de profundidad de la jerarquía para el cálculo.|  
|6|LoopDetected|Error en el cálculo del valor de campo porque se detectó un bucle recursivo en la jerarquía del registro.|  
  
<a name="BKMK_calculations"></a>  
 
## <a name="rollup-calculations"></a>Cálculos consolidados  

Las cálculos consolidados se realizan mediante trabajos del sistema programados que se ejecutan de forma asincrónica en segundo plano. Debe ser un administrador para ver y administrar los trabajos consolidados. 

### <a name="view-rollup-jobs"></a>Visualización de trabajos consolidados

Para ver los trabajos consolidados:

1. Mientras visualiza la **Solución predeterminada Common Data Services**, edite la dirección URL, quitando todo lo que aparece después de `dynamics.com`, y actualice la página.
2. En el área **Configuración**, seleccione **Sistema** > **Trabajos del sistema**.<br />![Navegar a los trabajos del sistema](media/navigate-system-jobs.png)
1. En el selector de vistas, elija **Trabajos del sistema periódicos**.
2. Para buscar rápidamente un trabajo importante, puede filtrar por el tipo de trabajo del sistema: **Cálculo masivo de campo consolidado** o **Calcular campo consolidado**.
 
### <a name="mass-calculate-rollup-field"></a>Cálculo masivo de campo consolidado

**Cálculo masivo de campo consolidado** es un trabajo periódico, creado por un campo consolidado. Se ejecuta una vez, después de haber creado o actualizado un campo consolidado. El trabajo recalcula el campo consolidado especificado en todos los registros existentes que contienen este campo. De forma predeterminada, el trabajo se ejecutará 12 horas después de haber creado o actualizado un campo. Una vez completado el trabajo, se programa automáticamente para ejecutarse en un futuro lejano, aproximadamente, en 10 años. Si se modifica el campo, se restablece el trabajo para volver a ejecutarse 12 horas después de la actualización. Se necesita un retraso de 12 horas para asegurarse de que el **Cálculo masivo de campo consolidado** se ejecuta durante las horas no operativas del entorno. Se recomienda que un administrador ajuste la hora de inicio de un trabajo de **Cálculo masivo de campo consolidado** una vez creado o modificado el campo consolidado, de tal forma que se ejecute durante el horario no operativo. Por ejemplo, medianoche sería un buen momento para ejecutar el trabajo a fin de garantizar un procesamiento eficaz de los campos consolidados.  

### <a name="calculate-rollup-field"></a>Calcular campo consolidado 

**Calcular campo consolidado** es un trabajo periódico que realiza cálculos incrementales de todos los campos consolidados en los registros existentes de una entidad especificada. Solo hay un trabajo **Calcular campo consolidado** por entidad. Los cálculos incrementales significan que el trabajo **Calcular campo consolidado** procesa los registros que se crearon, actualizaron o eliminaron después de que el último trabajo **Cálculo masivo de campo consolidado** terminara de ejecutarse. El valor de periodicidad máxima predeterminado es una hora. El trabajo se crea automáticamente cuando se crea el primer campo consolidado en una entidad, y se elimina cuando se elimina el último campo consolidado.  

## <a name="online-recalculation-option"></a>Opción de actualización en línea
Si mantiene el puntero sobre el campo consolidado del formulario, puede ver la hora de la última consolidación y puede actualizar el valor consolidado eligiendo el icono de actualización junto al campo, como se muestra a continuación:  

![Campo consolidado en el formulario de cuenta](media/rollup-field-on-account-form.png)
  

Hay algunas consideraciones que debe tener en cuenta al usar la opción de actualización en línea (actualización manual en el formulario):  
  
- Debe tener privilegios de escritura en la entidad y derechos de acceso de escritura en el registro de origen para el que solicita la actualización. Por ejemplo, si va a calcular los ingresos estimados de las oportunidades abiertas de una cuenta, no debe tener privilegios de escritura en la entidad de oportunidad, sino solo en la entidad de cuenta.  
- Esta opción solo está disponible en el modo en línea. No puede usarlo mientras trabaja sin conexión.  
- El número máximo de registros durante la actualización consolidada se limita a 50 000 registros. En caso de consolidaciones jerárquicas, esto se aplica a los registros relacionados en toda la jerarquía. Si se supera el límite, aparece un mensaje de error: *Los cálculos no pueden realizarse en línea porque se alcanzó el límite de cálculo de 50 000 registros relacionados.* Este límite no se aplica cuando se actualiza automáticamente la consolidación mediante los trabajos del sistema.  
- La profundidad máxima de la jerarquía está limitada a 10 para el registro de origen. Si se supera el límite, aparece un mensaje de error: *Los cálculos no pueden realizarse en línea porque se alcanzó el límite de profundidad de la jerarquía de 10 para el registro de origen.* Este límite no se aplica cuando se actualiza automáticamente la consolidación mediante los trabajos del sistema.  

## <a name="modify-rollup-job-recurrence"></a>Modificación de la periodicidad del trabajo consolidado

Como administrador del sistema, puede modificar el patrón de periodicidad del trabajo consolidado, posponer, pausar o reanudar el trabajo consolidado. Sin embargo, no se puede cancelar o eliminar un trabajo consolidado. 

Para pausar, posponer, reanudar o modificar el patrón de periodicidad, debe ver los trabajos del sistema. Más información en [Visualización de trabajos consolidados](#view-rollup-jobs) 

En la barra de navegación, elija **Acciones** y seleccione la acción que desee. 

Para el trabajo **Cálculo masivo de campo consolidado**, las selecciones disponibles son: **Reanudar**, **Posponer** y **Pausar**. 

Para el trabajo **Calcular campo consolidado**, las selecciones disponibles son: **Modificar periodicidad**, **Reanudar**, **Posponer** y **Pausar**.  
  
<a name="BKMK_businessscenarios"></a>  
 
## <a name="examples"></a>Ejemplos 

Echemos un vistazo a varios ejemplos de campo consolidado. Se agregarán datos para un registro desde los registros relacionados con o sin el uso de una jerarquía. También se agregarán datos para un registro desde actividades relacionadas y actividades relacionadas indirectamente con un registro mediante la entidad ActivityParty. En cada ejemplo, definimos el campo consolidado mediante el Editor de campos. Para abrir el Editor de campos, abra el Explorador de soluciones y expanda **Componentes** > **Entidades**. Seleccione la entidad que desee y seleccione **Campos**. Elija **Nuevo**. En el editor, proporcione la información necesaria para el campo, incluidos el **Tipo de campo** y el **Tipo de datos**. En el **Tipo de campo**, seleccione **Consolidado**, después de haber seleccionado el tipo de datos. Los tipos de datos incluyen números entero o decimales, moneda y fecha y hora. Elija el botón **Editar** situado junto al **Tipo de campo**. Esto lo redirigirá al editor de definiciones de campos consolidados. La definición de campo consolidado consta de tres secciones: **Entidad de origen**, **Entidad relacionada** y **Agregación**.  
  
-   En la sección **Entidad de origen**, especifique la entidad para la que se define el campo consolidado y si agregarlo o no a la jerarquía. Puede agregar filtros con varias condiciones para especificar los registros de la jerarquía que desea usar para la consolidación.  
  
-   En la sección **Entidad relacionada**, especifique la entidad en la que agregar. Esta sección es opcional si se decide realizar la consolidación en la jerarquía de la entidad de origen. Puede agregar filtros con varias condiciones para especificar qué registros relacionados usar en el cálculo. Por ejemplo, se incluyen los ingresos de las oportunidades abiertas con unos ingresos anuales de más de 1000 USD.  
  
-   En la sección **Agregar**, especifique la métrica que desea calcular. Puede elegir las funciones de agregado disponibles, como SUM, COUNT, MIN, MAX o AVG.  
  
### <a name="aggregate-data-for-a-record-from-related-records"></a>Agregar datos para un registro desde registros relacionados  

En este ejemplo, no se utiliza una jerarquía. Los ingresos totales estimados se calculan para una cuenta a partir de las oportunidades abiertas relacionadas.  

![Agregar los ingresos estimados para una cuenta](media/rollup-field-no-hierarchy.png)
  
### <a name="aggregate-data-for-a-record-from-the-child-records-over-the-hierarchy"></a>Agregar datos para un registro a partir de los registros secundarios en la jerarquía 
 
En este ejemplo, se calculan los ingresos estimados totales de una oportunidad, incluidas las oportunidades secundarias, en la jerarquía  
  
![Agregar ingresos estimados, jerarquía de oportunidades](media/rollup-field-hierarchy-self.png)
  
### <a name="aggregate-data-for-a-record-from-the-related-records-over-the-hierarchy"></a>Agregar datos para un registro a partir de los registros relacionados en la jerarquía

En este ejemplo, se calculan los ingresos estimados totales de las oportunidades abiertas de todas las cuentas en la jerarquía.  
  
![Agregar ingresos estimados de la jerarquía de una cuenta](media/rollup-field-hierarchy.png)  
  
### <a name="aggregate-data-for-a-record-from-all-related-activities"></a>Agregar datos para un registro a partir de todas las actividades relacionadas
  
En este ejemplo, se calcula el tiempo total empleado y facturado de todas las actividades relacionadas con una cuenta. Esto puede incluir el tiempo invertido en el teléfono, en las citas, o en las actividades personalizadas.  
  
En versiones anteriores, podía definir un campo consolidado para una actividad individual, como una llamada de teléfono, fax o cita. Sin embargo, para lograr el resultado del ejemplo que se muestra a continuación, tenía que calcular el total de los datos con el uso de los campos calculados. Ahora, puede hacerlo todo en un solo paso mediante la definición de un campo consolidado para la entidad de actividad.  
  
![Consolidación de todas las actividades de una cuenta](media/rollup-enhancements-activities.png)  
  
### <a name="aggregate-data-for-a-record-from-all-related-activities-and-activities-indirectly-related-via-the-activity-party-entity"></a>Agregar datos para un registro a partir de todas las actividades relacionadas y actividades relacionadas indirectamente mediante la entidad Activity Party  

En este ejemplo, contamos el número total de correos electrónicos enviados a una cuenta, donde la cuenta aparece en la línea "To Recipient" o en la línea "Cc Recipient". Esto se hace especificando el valor **Participation Type** (Tipo de participación) en **FILTERS** (Filtros) para la entidad Activity Party en la definición del campo consolidado. Si no usa el filtrado, se usan todos los tipos de participación disponibles para una actividad en el cálculo. 
 
Para más información sobre la entidad Activity Party y los tipos de participación disponibles para una actividad particular, vea [Entidad ActivityParty](/dynamics365/customer-engagement/developer/activityparty-entity).

  
![Actividades relacionadas con la consolidación y Activity Party](media/rollup-enhancements-indirect-activities.png)  
  
### <a name="aggregate-data-for-a-record-from-related-records-using-the-avg-operator"></a>Agregar datos para un registro desde registros relacionados mediante el operador AVG

En este ejemplo, calculamos un ingreso medio estimado de todas las oportunidades relacionadas con una cuenta.  
  
![Promedio de los ingresos estimados en Dynamics 365](media/rollup-enhancements-average.PNG)  
  
El ejemplo siguiente muestra cómo calcular un promedio de ingresos estimados de oportunidades relacionadas en una jerarquía de cuentas. Se puede ver un promedio de ingresos estimados en cada nivel de la jerarquía.  
  
![Promedio de los ingresos estimados en Dynamics 365](media/cust-rollup-enhancements-avg-over-hierarchy.png)  
  
<a name="BKMK_considerations"></a> 

## <a name="rollup-field-considerations"></a>Consideraciones de campos consolidados 

Se deben tener en cuenta determinadas condiciones y restricciones al trabajar con campos consolidados:  
  
- Puede definir un máximo de 100 campos consolidados para la organización y un máximo de 10 campos consolidados por entidad.  
- Las actualizaciones de campos consolidados no pueden desencadenar un flujo de trabajo.  
- Una condición de espera del flujo de trabajo no puede usar un campo consolidado.  
- No se admite una consolidación de un campo consolidado.  
- Una consolidación no puede hacer referencia a un campo calculado que usa otro campo calculado, aunque todos los campos del otro campo calculado se encuentren en la entidad actual.  
- La acumulación solo puede aplicar filtros a la entidad de origen o a entidades relacionadas, campos simples o campos calculados no complejos.  
- Una consolidación solo puede realizarse mediante entidades relacionadas con la relación 1:N. Una acumulación no puede realizarse mediante relaciones N:N.  
- Una consolidación no puede realizarse mediante la relación 1:N para la entidad Activity o la entidad Activity Party.  
- Las reglas de negocio, los flujos de trabajo o los campos calculados siempre usan el último valor calculado del campo consolidado.  
- Se agrega un campo consolidado en el contexto de usuario del sistema. Todos los usuarios pueden ver el mismo valor de campo consolidado. Puede controlar la visibilidad del campo consolidado con la seguridad de nivel de campo (FLS) mediante la restricción de quién puede acceder al campo consolidado. Más información: [Seguridad de nivel de campo para controlar el acceso](/dynamics365/customer-engagement/admin/field-level-security). 

### <a name="precision-rounding"></a>Precisión de redondeo
 
Si la precisión del campo agregado es mayor que la precisión del campo consolidado, la precisión del campo agregado se redondea hacia abajo hasta la precisión del campo consolidado, antes de realizar la agregación. Para ilustrar este comportamiento, veamos un ejemplo concreto. Supongamos que el campo consolidado de la entidad de cuenta, para calcular el total de ingresos estimados de las oportunidades relacionados, tiene una precisión de dos puntos decimales. El campo de los ingresos estimados de la entidad de oportunidad es el campo agregado con la precisión de cuatro puntos decimales. En nuestro ejemplo, la cuenta tiene dos oportunidades relacionadas. La suma agregada de los ingresos estimados se calcula como sigue:  
  
1. Ingresos estimados para la primera oportunidad: 1000,0041 USD  
1. Ingresos estimados para la segunda oportunidad: 2000,0044 USD  
1. Suma agregada de ingresos estimados: 1000,00 USD + 2000,00 USD = 3000,00 USD

Como se puede observar, la precisión redondeada a dos puntos decimales en el campo agregado se realiza antes de completar la agregación.  
  
### <a name="different-behavior-from-associated-grids"></a>Comportamiento diferente de las cuadrículas asociadas
 
Determinados formularios de entidad, como cuenta o contacto, de forma preestablecida, contienen las cuadrículas asociadas. Por ejemplo, un formulario de cuenta incluye contactos, casos, oportunidades y otras cuadrículas. Algunos de los registros mostrados en las cuadrículas del formulario de cuenta están relacionados directamente con el registro de la cuenta; otros, de forma indirecta, están relacionados con otros registros mediante relaciones. En comparación, la agregación de campos consolidados usa solo relaciones directas definidas de forma explícita en la definición de campo consolidado. No se consideran otras relaciones. Para ilustrar la diferencia de comportamiento, veamos el ejemplo siguiente.  
  
1. La cuenta A1 tiene un contacto principal, P1. El caso C1 está asociado con la cuenta A1 (campo C1.Customer = A1), y el caso C2 está asociado con el contacto P1 (campo C2.Customer = P1).  
1. La cuadrícula **Casos** del formulario **Cuenta** para el registro A1 muestra dos casos, C1 y C2.  
1. El campo consolidado de la entidad de cuenta, denominado Número total de casos, se usa para calcular los casos asociados con la cuenta.  
1. En la definición de campo consolidado de la cuenta, se especifican los casos que tiene la relación de cliente con la cuenta. Después de la agregación, el número total de casos es igual a 1 (caso C1). El caso C2 no se incluye en el total, ya que está directamente relacionado con el contacto, no con la cuenta, y no se puede definir de forma explícita en la definición de campo consolidado de la cuenta. Como resultado, el número total de casos devuelto por la operación consolidada no coincide con el número de casos que se muestra en la cuadrícula **Casos**.  
  
### <a name="see-also"></a>Vea también  

[Crear y editar campos](create-edit-fields.md)<br />
[Definir campos calculados](define-calculated-fields.md)<br />
[Comportamiento y formato del campo de fecha y hora](behavior-format-date-time-field.md)<br />
[Definir y realizar consultas a datos relacionados jerárquicamente](define-query-hierarchical-data.md)<br />
[Vídeo: Campos consolidados y calculados](http://www.youtube.com/watch?v=RoahCH1p3T8&list=PLC3591A8FE4ADBE07&index=8)<br />
[Vídeo: Uso de Power BI](http://www.youtube.com/watch?v=PkQe4BFlBS8&list=PLC3591A8FE4ADBE07&index=3)
