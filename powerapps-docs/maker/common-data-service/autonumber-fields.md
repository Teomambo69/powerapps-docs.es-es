---
title: Campos de numeración automática en Common Data Service | MicrosoftDocs
description: 'Comprender cómo crear, administrar y usar campos de numeración automática'
keywords: ''
ms.date: 02/26/2019
ms.service: powerapps
ms.custom: null
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: daemelia
ms.assetid: null
ms.author: daemelia
manager: kvivek
ms.reviewer: Mattp123
ms.suite: null
ms.tgt_pltfrm: null
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="autonumber-fields"></a>Campos de numeración automática

Los campos de numeración automática son campos que generan automáticamente cadenas alfanuméricas cuando se crean. Los fabricantes pueden personalizar el formato de estos campos según sus preferencias y, a continuación dejar que el sistema genere valores coincidentes que los completan automáticamente en tiempo de ejecución.

Si bien los campos de numeración automática son formalmente solo campos de texto con funcionalidad adicional agregada sobre ellos, [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) simplifica este concepto exponiendo simplemente **Numeración automática** como tipo de datos distinto en la categoría **Texto**. Cabe dejar constancia de que el [explorador de soluciones clásico](use-solution-explorer.md#classic-solution-explorer) no admite la creación o administración de campos de numeración automática.

Para crear un campo de numeración automática, siga los mismos pasos para [crear un campo](create-edit-field-portal.md#create-a-field) y simplemente seleccione **Numeración automática** en el cuadro de lista desplegable **Tipo de datos**. 

También puede activar funcionalidad de numeración automática en un campo de texto existente abriendo el campo y seleccionando **Numeración automática** del cuadro de lista desplegable **Tipo de datos**. De forma similar, la funcionalidad de numeración automática también puede ser deshabilitada en cualquier momento abriendo el campo y seleccionando otra opción en el cuadro de lista desplegable **Tipo de datos**.

## <a name="autonumber-types"></a>Tipos de numeración automática

Para facilitar la creación de los campos de numeración automática, hay algunos tipos predeterminados predefinidos de numeración automática para capturar los escenarios más comunes. 

### <a name="string-prefixed-number"></a>Número predefinido de cadena

El formato más común de numeración automática es un número predefinido de cadena sencilla. Cuando seleccione este tipo, la numeración automática consistirá en un número que se incrementa automáticamente con un prefijo constante de cadena opcional. Por ejemplo, un número predefinido de cadena con el prefijo *Contoso* generaría registros como *Contoso-1000*, *Contoso-1001*, *Contoso-1002*, etc.

### <a name="date-prefixed-number"></a>Número predefinido de fecha

Otro formato común de numeración automática es un número predefinido de fecha. Cuando seleccione este tipo, la numeración automática consistirá en un número que se incrementa automáticamente con un prefijo de fecha formateado. La parte de fecha del registro reflejará la fecha y hora actuales en la que se creó el registro en hora UTC. Hemos proporcionado varios formatos distintos de fecha que puede elegir.
Por ejemplo, un número predefinido de fecha generaría registros como *2019-26-02-1000*, *2019-27-02-1000*, *2019-28-02-1000*, etc., en función de la fecha actual y el formato de fecha seleccionado.

### <a name="custom"></a>Personalizada

Para creadores más avanzados con casos de uso específicos, proporcionamos la opción de personalizar completamente el formato deseado de un campo de numeración automática. El formato puede estar compuesto de constantes de cadena, incrementando automáticamente los números, fechas con formato o secuencias alfanuméricas aleatorias.
Para obtener información detallada sobre cómo definir formatos personalizados, consulte [Opciones de AutoNumberFormat](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/create-auto-number-attributes#autonumberformat-options).

## <a name="seed-values"></a>Valores de inicialización

El valor de inicialización de un campo de numeración automática es el número inicial que se usa para la parte numérica del formato. Por ejemplo, si desea que haya un campo de numeración automática para generar registros como *Contoso-1000*, *Contoso-1001*, *Contoso-1002*, etc., el valor de inicialización deseado es 1000 porque éste es el valor con el que se inicia la secuencia de número. Los campos de numeración automática tienen un valor de inicialización predeterminado de 1000, pero puede establecer un valor de inicialización personalizado si lo desea. 


> [!IMPORTANT]
> Designar una inicialización personalizada se admite actualmente únicamente al crear un nuevo campo de numeración automática. 
>
> Establecer el valor de inicialización sólo cambia el valor numérico actual para el atributo especificado en el entorno actual. No implica un valor de inicio común para el atributo. El valor de inicialización no se incluye en una solución cuando se importa en un entorno diferente. 

## <a name="create-an-autonumber-field"></a>Crear un campo de numeración automática
  
1.  Iniciar sesión en el [portal de PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).
  
2.  En el panel izquierdo, expanda **Datos**, y seleccione **Entidades**.
  
3.  Seleccione la entidad a la que desea agregar un campo de numeración automática y seleccione la pestaña **Campos** .
  
4.  En la barra de herramientas, seleccione **Agregar**.  
  
5.  En el panel derecho, escriba un **Nombre para mostrar** y seleccione **Numeración automática** para **Tipo de datos**.

    > [!div class="mx-imgBorder"] 
    > ![](media/create-autonumber-field.png "Crear un campo de numeración automática")
  
6. Establezca los campos opcionales según sea necesario. Más información: [Crear y editar campos](create-edit-field-portal.md#create-a-field)

7. Seleccione un tipo de numeración automática o mantenga la opción **Número predefinido de cadena** predeterminada.

8. Personalice un valor de inicialización o mantenga el valor predeterminado **1000**.

9. Seleccione **Listo**.

## <a name="see-also"></a>Vea también
 [Crear y editar campos para Common Data Service mediante el portal de PowerApps](create-edit-field-portal.md)
