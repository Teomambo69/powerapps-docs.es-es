---
title: Definir campos calculados en PowerApps | MicrosoftDocs
description: Aprenda a definir campos calculados
ms.custom: ''
ms.date: 05/25/2018
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
ms.assetid: 6d58a297-2ddf-4236-be3a-47249b49d5fa
caps.latest.revision: 67
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="define-calculated-fields-to-automate-manual-calculations"></a>Definir campos calculados para automatizar los cálculos manuales

Usar campos calculados para automatizar los cálculos manuales usados en los procesos de negocio. 

Por ejemplo, un comercial puede querer conocer los ingresos ponderados de una oportunidad que se basan en los ingresos estimados de una oportunidad multiplicados por la probabilidad. O bien, automáticamente desea aplicar un descuento, si un pedido es superior a $500. Un campo calculado puede que contenga valores resultado de simples operaciones matemáticas, u operaciones condicionales, por ejemplo, Mayor que o If-Else, y muchos otras. Puede llevar a cabo todo esto utilizando PowerApps, sin necesidad de escribir código.  
  
## <a name="capabilities"></a>Capacidades
  
- Los campos calculados usan campos de la entidad actual o de entidades principales relacionadas.  
- El soporte de expresión está disponible en los campos de la entidad actual y las entidades principal relacionadas en las secciones **Condición** y las secciones **Acción**. Las funciones integradas incluyen:  
 **ADDHOURS**, **ADDDAYS**, **ADDWEEKS**, **ADDMONTHS**, **ADDYEARS**, **SUBTRACTHOURS**, **SUBTRACTDAYS**, **SUBTRACTWEEKS**, **SUBTRACTMONTHS**, **SUBTRACTYEARS**, **DIFFINDAYS**, **DIFFINHOURS**, **DIFFINMINUTES**, **DIFFINMONTHS**, **DIFFINWEEKS**, **DIFFINYEARS**, **CONCAT**, **TRIMLEFT** y **TRIMRIGHT**.  
- Un soporte condicional rico proporciona bifurcación y condiciones múltiples. Las operaciones lógicas incluyen los operadores **AND** y **OR**.  
- Las funcionalidades de edición visual incluyen una moderna interfaz de usuario e intellisense en la sección **ACCIÓN**. 
- Una integración sin problemas de los campos calculados con formularios, vistas, gráficos e informes está disponible en tiempo real.  
- Puede configurar campos calculados para usar controles personalizados.  
  
  
## <a name="scenarios"></a>Escenarios
  
- **Ingresos ponderados**: Ingresos estimados multiplicados por probabilidad  
- **Valor neto**: Activos restados de los pasivos de una cuenta determinada  
- **Costo de mano de obra**: Tasa base hasta 40 horas, más horas extras adicionales  
- **Número de contacto**: Número de teléfono para una cuenta o contacto basados en una oportunidad  
- **Puntuación de cliente potencial**: Un campo que proporciona ideas sobre la calidad de un cliente potencial determinado  
- **Seguimiento por**: Seguimiento de una actividad por un número especificado de días en función de su prioridad  
  
> [!IMPORTANT]
>  Para crear un campo calculado debe tener el privilegio de Escritura en la [entidad Perfil de seguridad de campo](/powerapps/developer/common-data-service/reference/entities/fieldsecurityprofile). Si el campo calculado usa los campos protegidos en un cálculo, debe considerar proteger el campo calculado también, para evitar que los usuarios accedan a datos para los que no tienen suficientes permisos. El editor del campo calculado proporciona una advertencia, si usted está creando un campo calculado que usa campos protegidos en un cálculo, sugiriendo que proteja el campo calculado. Más información: [Seguridad de nivel de campo para controlar el acceso](/dynamics365/customer-engagement/admin/field-level-security).  

## <a name="create-a-calculated-field"></a>Crear un campo calculado

Use el editor de campos para especificar un campo calculado. En este ejemplo usaremos [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) pero los pasos son similares con el explorador de soluciones. Más información: [Crear y editar campos](create-edit-fields.md)
  
1. Abra [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)
1. Expanda **Datos** > **Entidades**.  
1. Seleccione la entidad que desee y que elija **Campos**. Elija **Agregar campo**.  
1. Indique la información necesaria para el campo, incluidos el **Nombre para mostrar**, el **Nombre** y el **Tipo de datos**. 
1. Si el tipo de datos es uno de los tipos que admiten campos calculados, puede convertir el campo en un campo calculado seleccionando **Agregar** > **Cálculo**.

    ![Hacer que un campo sea calculado](media/make-field-calculated-maker.png)

    Estos son los tipos de campos que admiten cálculos:
    - Texto
    - Conjunto de opciones  
    - Dos opciones  
    - Número entero  
    - Número decimal  
    - Divisa  
    - Fecha y hora

1. Si selecciona **Cálculo**, debe guardar los cambios en la entidad. Haga clic en **Guardar** en el cuadro de diálogo **Cambios pendientes** para continuar.
1. Se abrirá el editor de definiciones del campo calculado, donde se ha creado el nuevo campo calculado, pero no se ha establecido ninguna fórmula. La definición del campo calculado consta de dos secciones: **CONDICIÓN** y **ACCIÓN**.  
  ![Formulario Nuevo cálculo de campo](media/empty-field-calculation.png)
- En la sección **Condición** puede especificar una entidad, un campo, un operador, tipo y un valor. En la lista desplegable para **Entidad**, puede seleccionar una entidad actual o una entidad relacionada. En el cuadro desplegable **Campo** tiene una selección de todos los campos disponibles para la entidad. Según el operador que elija, puede ser necesario proporcionar el tipo y el valor. Puede especificar varias condiciones mediante los operadores `AND` o `OR`  
- En la sección **Acción**, proporcione la fórmula para el campo calculado.  
  
> [!NOTE]
>  Puede usar datos de registros de búsqueda en la acción. Primero tiene que seleccionar el campo de búsqueda y después especificar un período. Después, puede seleccionar uno de los campos disponibles en la entidad relacionada. Por ejemplo, en el caso de *`<LookupFieldName>.<RelatedFieldName>`*, puede seleccionar: `ParentAccountId.AccountNumber`.  
>   
>  Tenga en cuenta que la seguridad de nivel de campo se omitirá en la entidad relacionada, por lo que si hay datos confidenciales en el campo al que se ha accedido le recomendamos que también proteja el campo calculado.  


<a name="BusinessScenarios"></a> 
  
## <a name="examples"></a>Ejemplos  

Veamos ejemplos de campos calculados con mayor detalle. 
  
### <a name="weighted-revenue-of-opportunity"></a>Ingresos ponderados de oportunidad

En este ejemplo usamos los campos de la entidad de oportunidad para calcular los ingresos ponderados basados en la probabilidad de la oportunidad. En el editor de campos para una entidad de oportunidad, creamos un campo denominado **Ingresos ponderados** y especificamos el tipo de campo como **Calculado** y el tipo de datos como **Divisa**.

En el editor de definición de campos calculados, en la sección **Condición**, especificamos la oportunidad con el Estado = Abierto. En la **ACCIÓN**, la fórmula calcula los ingresos ponderados a partir de los ingresos estimados de la oportunidad multiplicados por la probabilidad de la oportunidad.  Las siguientes capturas de pantalla muestran paso a paso cómo definir el campo calculado **Ingresos ponderados**.  
  
#### <a name="set-the-condition-on-the-opportunities"></a>Fije la condición de las oportunidades:
  
![Establecer ingresos ponderados en Dynamics 365](media/calc-field-open-opportunity.png)  
  
#### <a name="provide-the-formula-for-the-weighted-revenue"></a>Proporcione la fórmula para los ingresos ponderados: 
  
![Establecer el valor estimado de los ingresos ponderados en Dynamics 365](media/calc-field-open-opportunities-3.png)  
  
#### <a name="altogether"></a>En conjunto:
  
![Ingresos ponderados para ingresos estimados en Dynamics 365](media/calculated-field-open-opportunity.png)  
  
### <a name="follow-up-date-of-opportunity"></a>Fecha de seguimiento de oportunidad 
 
En este ejemplo utilizamos los campos del cliente potencial que originó una oportunidad para calcular la fecha adecuada para realizar seguimiento de la oportunidad. 

En el editor de campos para una entidad de oportunidad, creamos un campo denominado **Fecha de seguimiento** y especificamos el tipo de campo como **Calculado** y el tipo de datos como **Fecha y hora**.  

En el editor de definiciones de campos calculados, en la sección **Condición**, especificamos dos condiciones: plazo de tiempo de la compra y valor estimado de cliente potencial. 

En **ACCIÓN**, proporcionamos dos fórmulas:
 - Seguimiento a una semana de la oportunidad inmediata
 - Seguimiento a un mes si no es probable que la oportunidad ocurra inmediatamente. 

Las siguientes capturas de pantalla muestran paso a paso cómo definir el campo calculado **Fecha de seguimiento**.  
  
#### <a name="set-the-two-conditions-on-the-originating-lead"></a>Fije las dos condiciones del cliente potencial original:
  
![Fecha de seguimiento sobre una oportunidad en Dynamics 365](media/calc-field-follow-update-2.PNG)  
  
![Fecha de seguimiento sobre una oportunidad en Dynamics 365](media/calc-field-follow-update-3.PNG)  
  
#### <a name="provide-the-formula-to-follow-up-in-one-week"></a>Proporcione la fórmula para seguimiento a una semana:
  
![Fecha de seguimiento sobre una oportunidad en Dynamics 365](media/calc-field-follow-update-4.PNG)  
  
#### <a name="provide-the-formula-to-follow-up-in-one-month"></a>Proporcione la fórmula para seguimiento a un mes:
  
![Establecer la fecha de seguimiento en Dynamics 365](media/calc-field-follow-update-5.PNG)  
  
#### <a name="altogether"></a>En conjunto:
  
 ![Establecer la fecha de seguimiento If-Then y Else en Dynamics 365](media/calc-field-follow-update-6.PNG)  
  
### <a name="days-from-a-record-creation"></a>Días desde la creación de un registro 
 
En este ejemplo, usamos la función **DIFFINDAYS** para calcular la diferencia en días desde la hora en que se creó un registro hasta la fecha actual. 

Cree un nuevo campo de número entero llamado **Diferencia calculada en días**.
  
#### <a name="provide-the-formula-for-computing-the-difference-in-days"></a>Proporcione la fórmula para calcular la diferencia en días
  
![Campo calculado, función DIFFINDAYS](media/custom-calc-field-diff-days.png)  
  
#### <a name="altogether"></a>En conjunto:
  
![Diferencia en días desde la creación de registros](media/calc-field-diff-days-complete.png)  
  
<a name="Syntax"></a> 
  
## <a name="functions-syntax"></a>Sintaxis de funciones  

La siguiente tabla contiene información acerca de la sintaxis de las funciones suministradas en la sección **ACCIÓN** del campo calculado.  
  
> [!TIP]
>  Los nombres de función se especifican en letras mayúsculas.  
  
|Sintaxis de la función|Descripción|Tipo devuelto|  
|---------------------|-----------------|-----------------|  
|**ADDDAYS** (número entero, fecha y hora)|Devuelve una nueva fecha y hora que es igual a la fecha y hora dadas, más el número de días especificado.|Fecha y hora|  
|**ADDHOURS** (número entero, fecha y hora)|Devuelve una nueva fecha y hora que es igual a la fecha y hora dadas, más el número de horas especificado.|Fecha y hora|  
|**ADDMONTHS** (número entero, fecha y hora)|Devuelve una nueva fecha y hora que es igual a la fecha y hora dadas, más el número de meses especificado.|Fecha y hora|  
|**ADDWEEKS** (número entero, fecha y hora)|Devuelve una nueva fecha y hora que es igual a la fecha y hora dadas, más el número de semanas especificado.|Fecha y hora|  
|**ADDYEARS** (número entero, fecha y hora)|Devuelve una nueva fecha y hora que es igual a la fecha y hora dadas, más el número de años especificado.|Fecha y hora|  
|**SUBTRACTDAYS** (número entero, fecha y hora)|Devuelve una nueva fecha y hora que es igual a la fecha y hora dadas, menos el número de días especificado.|Fecha y hora|  
|**SUBTRACTHOURS** (número entero, fecha y hora)|Devuelve una nueva fecha y hora que es igual a la fecha y hora dadas, menos el número de horas especificado.|Fecha y hora|  
|**SUBTRACTMONTHS** (número entero, fecha y hora)|Devuelve una nueva fecha y hora que es igual a la fecha y hora dadas, menos el número de meses especificado.|Fecha y hora|  
|**SUBTRACTWEEKS** (número entero, fecha y hora)|Devuelve una nueva fecha y hora que es igual a la fecha y hora dadas, menos el número de semanas especificado.|Fecha y hora|  
|**SUBTRACTYEARS** (número entero, fecha y hora)|Devuelve una nueva fecha y hora que es igual a la fecha y hora dadas, menos el número de años especificado.|Fecha y hora|  
|**DIFFINDAYS** (fecha y hora, fecha y hora)|Devuelve la diferencia en días entre dos campos **Fecha y hora**. Si ambas fechas y horas coinciden en el mismo día, la diferencia es cero.|Número entero|  
|**DIFFINHOURS** (fecha y hora, fecha y hora)|Devuelve la diferencia en horas entre dos campos **Fecha y hora**.|Número entero|  
|**DIFFINMINUTES** (fecha y hora, fecha y hora)|Devuelve la diferencia en minutos entre dos campos **Fecha y hora**.|Número entero|  
|**DIFFINMONTHS** (fecha y hora, fecha y hora)|Devuelve la diferencia en meses entre dos campos **Fecha y hora**. Si ambas fechas y horas coinciden en el mismo mes, la diferencia es cero.|Número entero|  
|**DIFFINWEEKS** (fecha y hora, fecha y hora)|Devuelve la diferencia en semanas entre dos campos **Fecha y hora**. Si ambas fechas y horas coinciden en la mismo semana, la diferencia es cero.|Número entero|  
|**DIFFINYEARS** (fecha y hora, fecha y hora)|Devuelve la diferencia en años entre dos campos **Fecha y hora**. Si ambas fechas y horas coinciden en el mismo año, la diferencia es cero.|Número entero|  
|**CONCAT** (una línea de texto, una línea de texto, ... línea de texto única)|Devuelve una cadena que es el resultado de concatenar dos o más cadenas.|Cadena|  
|**TRIMLEFT** (una línea de texto, número entero)|Devuelve una cadena que contiene una copia de una cadena especificada sin los primeros N caracteres.|Cadena|  
|**TRIMRIGHT** (una línea de texto, número entero)|Devuelve una cadena que contiene una copia de una cadena especificada sin los últimos N caracteres.|Cadena|  
  
> [!NOTE]
>  Todas las funciones DIFF requieren que el primer campo de **Fecha y hora** y el segundo campo de **Fecha y hora** tengan el mismo comportamiento: **Local del usuario**, **Solo fecha** o **Independiente de zona horaria**. Si no coincide el comportamiento del segundo campo con el comportamiento del primer campo, el mensaje de error aparece, indicando que el segundo campo no se puede usar en la función actual. Más información: [Comportamiento y formato del campo de fecha y hora](behavior-format-date-time-field.md).  
  
> [!NOTE]
>  No puede especificar una fecha, como 01/01/2015, como el valor Fecha en un campo calculado. Los valores de Fecha y Fecha y hora solo se pueden configurar o comparar usando otros campos Fecha y hora.  
  
En la función **CONCAT** , puede usar cadenas literales como líneas individuales de texto, campos de entidad que contienen una sola línea de texto, o una combinación de ambos. Por ejemplo: **CONCAT** (FirstName, LastName, "es un jefe"). Si una cadena literal contiene comillas, preceda cada marca con el carácter de escape de barra diagonal inversa (\\), de este modo: `This string contains the \"quotation marks.\"`. Esto garantiza que las comillas dentro de cadena no se tratan como caracteres especiales que separan las cadenas.  
  
Los siguientes ejemplos muestran cómo usar las funciones **TRIMLEFT** y **TRIMRIGHT**. Contienen las cadenas iniciales y las cadenas resultantes, devueltas por las funciones **TRIMLEFT** y **TRIMRIGHT**:  
  
**TRIMLEFT** (“RXX10-3456789”, 3), devuelve la cadena `10-3456789`    
**TRIMRIGHT** (“20-3456789RXX”, 3), devuelve la cadena `20-3456789` 
  
<a name="Considerations"></a> 
  
## <a name="considerations"></a>Consideraciones 
 
Debe conocer determinadas condiciones y limitaciones cuando trabaja con campos calculados:  
  
- Las consultas, gráficos, y las visualizaciones guardados pueden tener un máximo de 10 campos calculados únicos.  
- Los valores de los campos calculados no se muestran en modo sin conexión del cliente de Outlook en las vistas de ventana o en los formularios principales de entidad.  
- El número máximo de los campos calculados encadenados es 5.  
- Un campo calculado no puede hacer referencia a sí mismo o tener cadenas cíclicas.  
- Si cambia uno de los operadores de condición en una cláusula de condición múltiple, todos los operadores de condición se actualizarán a esa condición. Por ejemplo, en la cláusula `IF (x > 50) OR (y ==10) OR (z < 5)`, si cambia el operador `OR` al operador `AND`, todos los operadores `OR` de la cláusula se convertirán en operadores `AND`.  
- Puede obtener acceso a campos primarios mediante el campo de búsqueda en la entidad primaria, como *`<LookupFieldName>.<FieldName>`*. Esto no es posible con los campos de búsqueda de varias entidades como Cliente, que puede ser Cuenta o Contacto. Sin embargo, algunas entidades tienen campos de búsqueda individuales para una entidad específica, como `ParentAccountid.`*`<FieldName>`* o `ParentContactid.`*`<FieldName>`*.  
- El orden está deshabilitado en:  
  - Un campo calculado que contiene un campo de un registro primario.  
  - Un campo calculado que contiene un campo lógico (por ejemplo, campo de dirección)
  - Un campo calculado que contiene otro campo calculado.  
- Los campos calculados pueden abarcar dos entidades sólo.  
  - Un campo calculado puede contener un campo de otra entidad (que abarca dos entidades - entidad actual y registro primario).  
  - Un campo calculado no puede contener un campo calculado procedente de otra entidad que también contenga otro campo de una entidad distinta (abarcando tres entidades):   
    (Entidad actual) Campo calculado &larr; (Registro primario) Campo calculado 1 &larr; (Registro primario) Campo calculado 2.  
- No se pueden desencadenar flujos de trabajo o complementos en los campos calculados.  
- No puede cambiar un campo simple existente en un campo calculado. Si la aplicación actual está usando JavaScript o complementos para calcular un campo, no podrá usar la característica de campos calculados sin crear un nuevo campo.  
- Las reglas de detección de duplicados no se activan en campos calculados.  
- Un consolidado no puede hacer referencia a un campo calculado que use otro campo calculado, incluso si todos los campos del otro campo calculado están en la entidad actual.  
  
### <a name="see-also"></a>Vea también
 
[Crear y editar campos](create-edit-fields.md)<br />
[Definir campos consolidados que agregan valores](define-rollup-fields.md)<br />
[Vídeo: Campos consolidados y calculados](http://go.microsoft.com/fwlink/p/?LinkId=517727)
