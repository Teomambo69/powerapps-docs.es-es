---
title: Atributos calculados y consolidados (Common Data Service) | Microsoft Docs
description: 'Obtenga información sobre elementos y características comunes, atributos calculados, atributos consolidados, recuperar un valor de campo consolidado calculado inmediatamente y enumeración de SourceTypeMasks.'
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
# <a name="calculated-and-rollup-attributes"></a>Atributos calculados y consolidados

Los atributos *calculados* y *consolidados* liberan al usuario de tener que realizar cálculos manualmente y le permiten centrarse en su trabajo. Los administradores del sistema pueden ahora definir con facilidad un campo para que contenga el valor de muchos cálculos comunes sin necesidad de trabajar con un desarrollador. Los programadores también pueden aprovechar las capacidades de la plataforma para realizar estos cálculos en vez de en su propio código.  
  
 [Vídeo: Campos consolidados y calculados en Microsoft Dynamics CRM 2015](http://youtu.be/RoahCH1p3T8)  
  
<a name="BKMK_CommonElements"></a>   
## <a name="common-elements-and-characteristics"></a>Elementos y características comunes  
 Los atributos calculados y consolidados comparten algunos elementos y características comunes, como:  
  
- Son de solo lectura.  
  
- No son específicos del usuario. El cálculo se realiza mediante una cuenta de usuario del sistema, por lo que los valores se pueden basar en registros que de otro modo el usuario no tiene privilegios para ver, como atributos que tienen seguridad de nivel de campo habilitada.  
  
  Todos los atributos que se heredan de <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata> tienen una propiedad <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.SourceType> que puede contener los valores que se muestran en la tabla siguiente.  
  
|                 Value                 |                                    Descripción                                     |
|---------------------------------------|------------------------------------------------------------------------------------|
| Null |       No es un tipo válido de atributo para ser un atributo calculado o consolidado.        |
|                   0                   | Atributo simple. El atributo no se define como atributo calculado o consolidado. |
|                   1                   |                                Atributo calculado                                |
|                   2                   |                                  Atributo consolidado                                  |
  
 Los atributos calculados y consolidados se basan en tipos de atributos existentes que se heredan de <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata>. Los siguientes tipos de atributos tienen propiedades nuevas:  
  
- <xref:Microsoft.Xrm.Sdk.Metadata.BooleanAttributeMetadata>  
  
- <xref:Microsoft.Xrm.Sdk.Metadata.DateTimeAttributeMetadata>  
  
- <xref:Microsoft.Xrm.Sdk.Metadata.DecimalAttributeMetadata>  
  
- <xref:Microsoft.Xrm.Sdk.Metadata.IntegerAttributeMetadata>  
  
- <xref:Microsoft.Xrm.Sdk.Metadata.MoneyAttributeMetadata>  
  
- <xref:Microsoft.Xrm.Sdk.Metadata.PicklistAttributeMetadata>  
  
- <xref:Microsoft.Xrm.Sdk.Metadata.StringAttributeMetadata>  
  
  Cada uno de estos tipos de atributos tiene las siguientes propiedades para permitir cálculos y consolidaciones.  
  
|      Propiedad       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        Definición                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|---------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `FormulaDefinition` |                                                                                                                                                                                                                                                                                                                                                                                                                                                                   Contiene la definición XAML de la fórmula usada para realizar el cálculo o la consolidación. La única forma admitida de cambiar este valor es a través del editor de fórmulas de la aplicación.<br /><br /> Para obtener información sobre las fórmulas para estos atributos vea los siguientes temas en el manual de personalización: [Definir campos de informe](https://technet.microsoft.com/library/dn832162.aspx) y [Definir campos calculados](https://technet.microsoft.com/library/dn832103.aspx).                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|  `SourceTypeMask`   | El valor de máscara de bits de esta propiedad de solo lectura describe los tipos de orígenes que se usan en la fórmula del atributo calculado o si la fórmula de un atributo calculado o consolidado no es válida.<br /><br /> -   0: **Indefinido**. El valor predeterminado para los atributos simples y consolidados.<br />-   1: **Simple**. El atributo calculado hace referencia a un atributo en el mismo registro.<br />-   2. **Relacionado**. El atributo calculado hace referencia a un atributo en un registro relacionado.<br />-   4: `Logical`. El atributo calculado hace referencia a un atributo en el mismo registro que realmente se almacena en otra tabla de base de datos. Más información: [Atributos lógicos](/dynamics365/customer-engagement/developer/introduction-to-entity-attributes#BKMK_LogicalAttributes)<br />-   8: `Calculated`. El atributo calculado hace referencia a otro atributo calculado.<br />-   16: `Rollup`. El atributo calculado hace referencia a un atributo consolidado.<br />-   32: `Invalid`. El campo calculado o consolidado no es válido.<br />     Aquí es donde normalmente un campo hace referencia a un atributo que ya no existe. **Nota:** Una o varias de estas condiciones pueden ser true para campos calculados o consolidados. Dado que este es un valor de máscara de bits, puede resultarle útil usar la [Enumeración de SourceTypeMasks](calculated-rollup-attributes.md#BKMK_SourceTypeMasks) al realizar operaciones bit a bit. |
  
<a name="BKMK_Calculated"></a>   
## <a name="calculated-attributes"></a>Atributos calculados  
 Los atributos calculados se calculan en tiempo real cuando se recuperan. Los atributos calculados pueden estar compuestos con diferentes tipos de datos. Por ejemplo, un atributo calculado entero puede hacer referencia a valores de atributos decimales o de divisa. Más información: [Definir campos calculados](https://technet.microsoft.com/library/dn832103.aspx).  
  
 Los valores de atributos calculados están disponibles en la canalización de complementos de recuperación. La imagen posterior de actualización o creación de registro de entidad contiene el valor de atributo calculado en la fase 40. Más información: [Canalización de ejecución de eventos](event-framework.md#event-execution-pipeline) e [Imágenes de la entidad](understand-the-data-context.md#entity-images)
  
### <a name="limitations"></a>Limitaciones  
 No puede usar valores en los atributos calculados que hacen referencia a una entidad relacionada, otro atributo calculado, o un *valor lógico* en la misma entidad para ordenar los datos devueltos por una consulta. Aunque la consulta pueda especificar que los resultados se deben ordenar mediante un atributo calculado, se ignorará la dirección del orden y no se lanzará un error. Si el atributo calculado hace referencia solo a valores simples en el mismo registro, el orden funciona normalmente. Puede determinar los orígenes usados en un campo calculado usando la propiedad `SourceTypeMask` en los metadatos del atributo. Más información: [Atributos lógicos](/dynamics365/customer-engagement/developer/introduction-to-entity-attributes.md#BKMK_LogicalAttributes)  
  
 Sólo los atributos de una entidad primaria inmediata se pueden usar en un atributo calculado.  
  
 Las consultas, gráficos, y las visualizaciones guardados pueden tener un máximo de 10 atributos calculados únicos.  
  
 Los atributos calculados pueden hacer referencia a otros atributos calculados en su fórmula, pero no pueden hacer referencia a sí mismos.  
  
 Los atributos calculados no tienen valores cuando un usuario con Dynamics 365 for Outlook está sin conexión.  
  
 Las propiedades de metadatos `MaxValue` y `MinValue` no se pueden definir en atributos calculados  
  
<a name="BKMK_Rollup"></a>   
## <a name="rollup-attributes"></a>Atributos consolidados  
 Dado que los atributos consolidados se mantienen en la base de datos, se pueden usar para filtrar u ordenar como atributos ordinarios. Cualquier tipo de proceso o de complemento usará el valor calculado más recientemente del atributo. Los valores de atributo consolidado son calculados asincrónicamente por trabajos del sistema programados. Los administradores establecen cuándo se ejecuta un trabajo o se pausa el trabajo. De forma predeterminada, cada atributo se actualiza cada hora. Más información: [Definir campos consolidados](https://technet.microsoft.com/library/dn832103.aspx).  
  
 Cuando un atributo consolidado se crea o se actualiza un trabajo de **Cálculo masivo de campos consolidados** programado para ejecutarse en 12 horas. El retraso de 12 horas está pensado para realizar esta operación de uso intensivo de recursos en un momento que afecte lo menos posible a los usuarios. Una vez que se complete el trabajo, la próxima vez que se programe para ejecutarse será dentro de 10 años. Si hay algún problema con el cálculo, este se transmitirá con el trabajo del sistema. Busque el trabajo del sistema en **Configuración** > **Trabajos del sistema** para buscar los errores con los campos consolidados.  
  
> [!TIP]
>  Como programador que prueba una solución en un entorno de desarrollo es posible que no desee esperar 12 horas. Puede hacer que suceda más rápidamente. En la lista **Trabajos del sistema**, use la vista **Trabajos del sistema periódicos** para filtrar la lista y busque el trabajo **Cálculo masivo de campos consolidados**. Con el trabajo seleccionado, use **Más acciones** > **Posponer** y establezca una hora anterior para que se produzca la acción.  
>   
>  Si desea desencadenar la creación de un nuevo trabajo **Cálculo masivo de campos consolidados**, recupere el <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata> para el atributo consolidado mediante <xref:Microsoft.Xrm.Sdk.Messages.RetrieveAttributeRequest> y use <xref:Microsoft.Xrm.Sdk.Messages.UpdateAttributeRequest> para actualizar el atributo sin realizar ningún cambio real.  
  
 El trabajo **Cálculo masivo de campos consolidados** se producirá inmediatamente cuando una solución que contiene un atributo consolidado se importe. Esto da por hecho que está instalando una solución durante una hora que no influirá negativamente en los usuarios.  
  
 Cada atributo consolidado para una entidad también incluirá dos atributos de apoyo para el atributo consolidado:  
  
- *\<attribute SchemaName>* `_Date`: DateTime - Cuando la consolidación se calculó por última vez.  
  
- *\<attribute SchemaName>* `_State`: Entero - El estado de cálculo consolidado. Más información: [Configuración de estados consolidados](calculated-rollup-attributes.md#BKMK_RollupStateValues)  
  
<a name="BKMK_RollupStateValues"></a>   
### <a name="rollup-state-values"></a>Valores de estado consolidado  
 El estado de un cálculo de campo consolidado está disponible en el correspondiente atributo *\<attribute SchemaName>*`_State` y en la propiedad <xref:Microsoft.Crm.Sdk.Messages.CalculateRollupFieldResponse>.`FieldState` . Los valores que indican el estado se muestran en la tabla siguiente.  
  
|Valor de estado|Descripción|  
|-----------------|-----------------|  
|0|`NotCalculated`: El valor de atributo aún está por calcular.|  
|1|`Calculated`: El valor de atributo se ha calculado de acuerdo la última hora de actualización en el atributo *\<attribute SchemaName>*`_Date`.|  
|2|`OverflowError`: El cálculo de valor de atributo produjo error de desbordamiento.|  
|3|`OtherError`: Error de cálculo de valor de atributo debido a un error interno, la próxima ejecución del trabajo cálculo lo corregirá probablemente.|  
|4|`RetryLimitExceeded`: El cálculo del valor del campo produjo un error porque el número máximo de reintentos de calcular el valor se ha excedido debido probablemente al número elevado de conflictos de la simultaneidad y bloqueo.|  
|5|`HierarchicalRecursionLimitReached`: El cálculo del valor de atributo produjo un error porque se alcanzó el límite máximo de la profundidad de la jerarquía para el cálculo.|  
|6|`LoopDetected`: El cálculo del valor de atributo produjo error porque se detectó un bucle recursivo en la jerarquía del registro.|  
  
### <a name="retrieve-a-calculated-rollup-field-value-immediately"></a>Recuperar un valor de campo consolidado calculado inmediatamente  
 Los atributos consolidados admiten un mensaje de `CalculateRollupField` que los desarrolladores pueden usar para calcular un valor de atributo consolidado a petición. La solicitud y respuesta, junto con los integrantes, se muestran en la tabla siguiente.  
  
|Solicitud/respuesta|Integrantes|  
|-----------------------|-------------|  
|<xref:Microsoft.Crm.Sdk.Messages.CalculateRollupFieldRequest>|`Target`: <xref:Microsoft.Xrm.Sdk.EntityReference> para el registro.<br /><br /> `FieldName`: Cadena que representa el nombre lógico del atributo.|  
|<xref:Microsoft.Crm.Sdk.Messages.CalculateRollupFieldResponse>|`Entity`: <xref:Microsoft.Xrm.Sdk.Entity> que contiene el atributo consolidado y los atributos *\<attribute SchemaName>*`_Date` y *\<attribute SchemaName>*`_State` de apoyo.|  
  
 Este mensaje es una operación sincrónica solo para el atributo identificado en la solicitud. Si el valor del registro se incluye como parte de otros campos consolidados, los valores de esos campos no tomarán en consideración el posible cambio de valor producido por la llamada a este método hasta que se produzcan los trabajos asincrónicos programados regularmente que realizan esos cálculos.  
  
### <a name="limitations"></a>Limitaciones  
 Los atributos consolidados no se pueden usar como un evento de flujo de trabajo o condición de espera. Estos atributos no provocan que el evento desencadene flujos de trabajo.  
  
 Los atributos ModifiedBy y ModifiedOn de la entidad no se actualizan cuando se actualiza el atributo consolidado.  
  
 Un máximo de 100 atributos consolidados se puede definir dentro de una organización. Cada entidad no puede tener más de 10 atributos consolidados.  
  
 Una fórmula de atributo consolidado no puede hacer referencia a otro atributo consolidado.  
  
 Una fórmula de atributo consolidado no puede hacer referencia a atributos calculados complejos. Solo los atributos calculados que hacen referencia atributos simples en el mismo registro pueden usarse con las consolidaciones.  
  
 Una fórmula de atributo consolidado no puede incluir registros en relaciones de varios a varios (N:N). Puede incluir solo registros en relaciones de uno a varios (1:N).  
  
 Las fórmulas de atributo consolidado no podrán usar relaciones de uno a varios (1:N) con la entidad `ActivityPointer` o `ActivityParty`.  
  
<a name="BKMK_SourceTypeMasks"></a>   
## <a name="sourcetypemasks-enumeration"></a>Enumeración de SourceTypeMasks  
 La propiedad `SourceTypeMask` para los atributos que permiten campos calculados y consolidados contiene un valor de máscara de bits. Para extraer la información del valor, ayuda tener una enumeración al realizar operaciones bit a bit. Use la siguiente enumeración de `SourceTypeMasks` al comparar el valor de propiedad de `SourceTypeMask`.  
  
```csharp  
 public enum SourceTypeMasks  
{  
    /// <summary>  
    /// Undefined: 0 - The default value for simple and rollup attributes.  
    /// </summary>  
    Undefined = 0,  
    /// <summary>  
    /// Simple: 1 - The calculated attribute refers to an attribute in the same record.  
    /// </summary>  
    Simple = 1,  
    /// <summary>  
    /// Related: 2 - The calculated attribute refers to an attribute in a related record.  
    /// </summary>  
    Related = 2,  
    /// <summary>  
    /// Logical: 4 - The calculated attribute refers to a logical attribute.  
    /// </summary>  
    Logical = 4,  
    /// <summary>  
    /// Calculated: 8 - The calculated attribute refers to another calculated attribute.  
    /// </summary>  
    Calculated = 8,  
    /// <summary>  
    /// Rollup: 16 - The calculated attribute refers a rollup attribute.   
    /// </summary>  
    Rollup = 16,  
    /// <summary>  
    /// Invalid: 32 - The calculated or rollup attribute is invalid.  
    /// Typically this would be where a field refers to an attribute that no longer exists.   
    /// </summary>  
    Invalid = 32  
}  
```  
  
### <a name="see-also"></a>Vea también  
 [Vídeo: Campos consolidados y calculados en Microsoft Dynamics CRM 2015](http://youtu.be/RoahCH1p3T8)   
 [Introducción a los atributos de entidad](/dynamics365/customer-engagement/developer/introduction-to-entity-attributes)   
 [Definir campos calculados](https://technet.microsoft.com/library/dn832103.aspx)   
 [Definir campos consolidados](https://technet.microsoft.com/library/dn832103.aspx)
