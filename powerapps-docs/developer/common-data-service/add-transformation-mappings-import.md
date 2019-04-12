---
title: Agregar asignaciones de transformación para la importación (Common Data Service) | Microsoft Docs
description: La asignación de transformación permite la modificación opcional de los datos de origen antes de la importación.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="add-transformation-mappings-for-import"></a>Agregar asignaciones de transformación para la importación

Use la asignación de transformación para modificar los datos antes de importarlos. Por ejemplo, divida el nombre completo contenido en el archivo de origen en nombre y apellidos para que coincidan con los atributos de destino de una entidad.  
  
 Para implementar la asignación de transformación, use la entidad de asignación de transformaciones (`TransformationMapping`) y la entidad de asignación de parámetros de transformación (`TransformationParameterMapping`).  
  
 Los datos transformados deben ser compatibles con los tipos de atributos de entidad Common Data Service.  
  
 La propiedad `TransformationMapping.TransformationTypeName` describen el tipo de transformación. Los valores válidos para esta propiedad se muestran en la tabla siguiente:  
  
|Campo|Valor|  
|-----------|-----------|  
|AddToCurrentDate|"Microsoft.Crm.Transformations.AddToCurrentDate"|  
|AddToDate|"Microsoft.Crm.Transformations.AddToDate"|  
|AdvancedAddToCurrentDate|"Microsoft.Crm.Transformations.AdvancedAddToCurrentDate"|  
|AssignValue|"Microsoft.Crm.Transformations.AssignValue"|  
|Concatenación|"Microsoft.Crm.Transformations.Concatenate"|  
|Reemplazar|"Microsoft.Crm.Transformations.Replace"|  
|División|"Microsoft.Crm.Transformations.Split"|  
|Subcadena|"Microsoft.Crm.Transformations.Substring"|  
  
 En las siguientes secciones se describen las transformaciones disponibles.  
  
<a name="BKMK_Concatenation"></a>   
## <a name="concatenation"></a>Concatenación  
 Concatena cadenas y las separa con un delimitador.  
  
|Parámetros de entrada|Descripción|  
|----------------------|-----------------|  
|Prefijo|Cadena que se usa como prefijo en la cadena concatenada.|  
|Sufijo|Cadena que se usa como sufijo en la cadena concatenada.|  
|Delimitador|Un carácter o combinación de caracteres que separan las subcadenas dentro de la cadena concatenada. El delimitador no se usa entre el prefijo y la subcadena o entre el sufijo y la subcadena. No use los caracteres de retroceso (\b), nueva línea (\n) y retorno (\r) como delimitador.|  
|\<Variable>|Matriz de longitud variable que contiene subcadenas.|  
  
|Parámetros de salida|Descripción|  
|-----------------------|-----------------|  
|Cadena|Cadena concatenada.|  
  
<a name="BKMK_Split"></a>   
## <a name="split"></a>División  
 Separa una cadena que incluye un delimitador en subcadenas. Puede haber un máximo de diez subcadenas.  
  
|Parámetros de entrada|Descripción|  
|----------------------|-----------------|  
|Cadena de entrada|Cadena que contiene una o varias subcadenas que se separan con delimitadores.|  
|Delimitador|Un carácter o combinación de caracteres que separan las subcadenas dentro de la cadena. No use los caracteres de retroceso (\b), nueva línea (\n) y retorno (\r) o cadenas vacías como delimitador.|  
  
|Parámetros de salida|Descripción|  
|-----------------------|-----------------|  
|Variable|1 subcadena hasta un máximo de 10.|  
  
 Por ejemplo, si la cadena de entrada contiene once subcadenas, el resultado contiene diez subcadenas tal como se muestra en el siguiente ejemplo:  
  
 Cadena de entrada: a;b;c;d;e;f;g;h;i;j;k  
  
 Salida:  
  
 a  
  
 b.  
  
 c  
  
 d  
  
 e  
  
 f  
  
 g  
  
 h  
  
 i  
  
 j;k  
  
<a name="BKMK_Substring"></a>   
## <a name="substring"></a>Subcadena  
 Devuelve una subcadena de una longitud especificada, a partir de un punto especificado de la cadena.  
  
|Parámetros de entrada|Descripción|  
|----------------------|-----------------|  
|Cadena de entrada|Cadena que contiene una subcadena.|  
|Índice inicial|Posición de inicio de la subcadena.|  
|Duración|Longitud de la subcadena. Si la longitud es **null**, devuelve una cadena completa desde el índice de inicio.|  
  
|Parámetros de salida|Descripción|  
|-----------------------|-----------------|  
|Subcadena|Subcadena devuelta.|  
  
<a name="BKMK_Replace"></a>   
## <a name="replace"></a>Reemplazar  
 Sustituye todos los casos de una cadena especificada por otra cadena especificada.  
  
|Parámetros de entrada|Descripción|  
|----------------------|-----------------|  
|Cadena de entrada|Cadena que contiene una cadena de búsqueda.|  
|Cadena de búsqueda|Cadena de búsqueda. No use los caracteres de retroceso (\b), nueva línea (\n) y retorno (\r) como cadena de búsqueda.|  
|Reemplazar cadena|Cadena que reemplaza. Use una cadena vacía para quitar una cadena de búsqueda. No use los caracteres de retroceso (\b), nueva línea (\n) y retorno (\r) como cadena que reemplaza.|  
  
|Parámetros de salida|Descripción|  
|-----------------------|-----------------|  
|Valor|Valor de reemplazo (igual que el valor asignado).|  
  
<a name="BKMK_AssignValue"></a>   
## <a name="assign-value"></a>Asignar valor  
 Sustituye todos los valores por un valor especificado.  
  
|Parámetros de entrada|Descripción|  
|----------------------|-----------------|  
|Valor|Valor que desea asignar.|  
  
|Parámetros de salida|Descripción|  
|-----------------------|-----------------|  
|Valor|Valor de reemplazo (igual que el valor asignado).|  
  
> [!NOTE]
>  Las transformaciones de fecha solo se pueden usar para fechas con formato correcto. Para obtener información sobre cómo dar formato a las fechas, vea la Ayuda de Common Data Service.  
  
<a name="BKMK_AddToDate"></a>   
## <a name="add-to-date"></a>Agregar a fecha  
 Agrega un número determinado de días, meses y años a una fecha.  
  
|Parámetros de entrada|Descripción|  
|----------------------|-----------------|  
|Fecha|Cadena de fecha que se va a modificar.|  
|Desplazamiento de año|Valor positivo o negativo que se agrega al componente del año de una fecha de entrada.|  
|Desplazamiento de mes|Valor positivo o negativo que se agrega al componente del mes de una fecha de entrada.|  
|Desplazamiento de día|Valor positivo o negativo que se agrega al componente del día de una fecha de entrada.|  
  
|Parámetros de salida|Descripción|  
|-----------------------|-----------------|  
|Nueva fecha|Nueva cadena de datos que contiene el día, el mes y el año agregados en este orden.|  
  
<a name="BKMK_AdjustCurrentDate"></a>   
## <a name="adjust-current-date-and-set-time"></a>Ajustar fecha actual y establecer hora  
 Agrega un número determinado de días, meses y años a la fecha actual y establece la hora especificada. Los desplazamientos solo pueden ser números enteros.  
  
|Parámetros de entrada|Descripción|  
|----------------------|-----------------|  
|Desplazamiento de año|Valor positivo o negativo que se agrega al componente del año de una fecha actual.|  
|Desplazamiento de mes|Valor positivo o negativo que se agrega al componente del mes de una fecha actual.|  
|Desplazamiento de día|Valor positivo o negativo que se agrega al componente del día de una fecha actual.|  
|horas|Valor que se usa para establecer el componente de las horas de una fecha actual.|  
|minutos|Valor que se usa para establecer el componente de los minutos de una fecha actual.|  
|Segundos|Valor que se usa para establecer el componente de los segundos de una fecha actual.|  
|Día de la semana|Día de la semana que puede ser lunes, martes, miércoles, jueves, viernes, sábado o domingo. Los días de la semana se representan en números enteros, empezando por el decimal 1 para lunes. Los valores por los días de la semana están incluidos en la enumeración `DayOfWeek`. Para obtener más información sobre esta enumeración, vea el tema de MSDN [DayOfWeekEnumeration](https://msdn.microsoft.com/library/system.dayofweek.aspx). <br />Si la fecha actual calculada no está en el día especificado de la semana, se ajusta a la fecha anterior más próxima que esté en el día especificado de la semana. La fecha actual se ajusta siempre a una fecha anterior. <br />Por ejemplo, si especifica miércoles como día de la semana y la fecha recién calculada es el martes 9 de marzo, entonces la fecha se ajusta al miércoles 3 de marzo.|  
  
|Parámetros de salida|Descripción|  
|-----------------------|-----------------|  
|Nueva fecha|Nueva cadena de datos que contiene el día, el mes y el año agregados en este orden.|  
  
<a name="BKMK_AdvancedAdd"></a>   
## <a name="advanced-add-to-current-date"></a>Adición avanzada a fecha actual.  
 Agrega un número especificado de días, meses y años a la fecha actual. Se puede especificar si los desplazamientos son valores relativos a la fecha actual o absolutos. Los desplazamientos solo pueden ser números enteros.  
  
 Por ejemplo, si usa un valor absoluto de 3 para un desplazamiento de mes, el mes recién calculado es marzo. Si establece un desplazamiento relativo al mes de la fecha actual en 3 y el mes actual es abril, el mes recién calculado será julio.  
  
|Parámetros de entrada|Descripción|  
|----------------------|-----------------|  
|Desplazamiento de año|Valor positivo o negativo que se agrega al componente del año de una fecha actual o un año absoluto.|  
|Modo de desplazamiento de año|Especifique si la navegación es relativa a la fecha actual o el valor absoluto mediante el atributo `TransformationParameterMapping.Data`. Si usa enlaces de tipo de compilación, puede usar la enumeración `TransformationOffsetMode` para especificar el desplazamiento absoluto o relativo. Para obtener una lista de valores de DataTypeCode, consulte los valores de lista desplegable para esta entidad. Para ver los metadatos de las entidades de su organización, instale la solución Explorador de metadatos que se describe en [Exploración de los metadatos de su organización](/dynamics365/customer-engagement/developer/browse-your-metadata). También puede examinar la documentación de referencia para las entidades en la [Referencia de entidad](/dynamics365/customer-engagement/developer/about-entity-reference).  
|Desplazamiento de mes|Valor positivo o negativo que se agrega al componente del mes de una fecha actual o un mes absoluto.|  
|Modo de desplazamiento de mes|Especifique si la navegación es relativa a la fecha actual o el valor absoluto mediante el atributo `TransformationParameterMapping.Data`. Si usa enlaces de tipo de compilación, puede usar la enumeración `TransformationOffsetMode` para especificar el desplazamiento absoluto o relativo. Para obtener una lista de valores de DataTypeCode, consulte los valores de lista desplegable para esta entidad.|  
|Desplazamiento de día|Valor positivo o negativo que se agrega al componente del día de una fecha actual o un día absoluto.|  
|Modo de desplazamiento de día|Especifique si la navegación es relativa a la fecha actual o el valor absoluto mediante el atributo `TransformationParameterMapping.Data`. Si usa enlaces de tipo de compilación, puede usar la enumeración `TransformationOffsetMode` para especificar el desplazamiento absoluto o relativo. Para obtener una lista de valores de DataTypeCode, consulte los valores de lista desplegable para esta entidad.|  
|Horas|Valor que establece el componente de las horas de una fecha actual.|  
|minutos|Valor que establece el componente de los minutos de una fecha actual.|  
|Segundos|Valor que establece el componente de los segundos de una fecha actual.|  
  
|Parámetros de salida|Descripción|  
|-----------------------|-----------------|  
|Nueva fecha|Nueva cadena de datos que contiene el día, el mes y el año, agregados en este orden. Primero, se agregan los componentes relativos y después se usan los valores absolutos para formar una fecha.|  

### <a name="see-also"></a>Vea también

[Importar datos](import-data.md)<br />
[Preparar archivos de origen para importar](prepare-source-files-import.md)<br />
[Crear asignaciones de datos para importar](create-data-maps-for-import.md)<br />
[Configurar la importación de datos](configure-data-import.md)<br />
[Ejecutar importación de datos](run-data-import.md)<br />
[Entidades de importación de datos](data-import-entities.md)<br />
[Ejemplo: exportar e importar una asignación de datos](org-service/samples/export-import-data-map.md)<br />
[Ejemplo: importar datos mediante la asignación de datos complejos](org-service/samples/import-data-complex-data-map.md)<br />