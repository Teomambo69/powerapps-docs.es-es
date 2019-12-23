---
title: Espacio seguro para RDL  | MicrosoftDocs
ms.custom: ''
ms.date: 09/30/2017
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 for Customer Engagement (online)
ms.assetid: 8ec72014-9f0c-4964-ac67-24419b054e91
caps.latest.revision: 13
author: Mattp123
ms.author: matp
manager: amyla
tags:
- MigrationHO
search.audienceType:
- customizer
search.app:
- D365CE
ms.openlocfilehash: 557959f9bb561fcb138f15011bd8320dfa5c94ff
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "2862904"
---
# <a name="rdl-sandboxing"></a>Espacio seguro para RDL 

En Common Data Service, los informes se ejecutan en el modo de espacio seguro. Para hacerlo se habilita el espacio seguro del lenguaje RDL (Report Definition Language) en SQL Server Reporting Services. El espacio seguro para RDL permite detectar y limitar el uso de determinados tipos de recursos. Como resultado, determinadas características de aplicaciones basadas en modelos de Power Apps pueden no estar disponibles. Para obtener más información, vea [MSDN: Habilitar y deshabilitar el espacio aislado de RDL](https://msdn.microsoft.com/library/ee210591.aspx).  
  
 Las opciones de configuración del espacio seguro para RDL en Common Data Service se describen en las siguientes secciones en este tema.  
    
<a name="BKMK_Max"></a>   
## <a name="limits-of-the-array-result-length-and-string-result-length"></a>Limita la longitud de longitud del resultado de la matriz y la longitud del resultado de la cadena  
 El número máximo de elementos permitidos en un valor de devolución de matriz de una expresión RDL se aumenta de 250 a 102400. El número máximo de elementos permitidos en un valor de devolución de cadena de una expresión RDL también se aumenta de 250 a 102400. Esto le permite incluir imágenes y logotipos con tamaños de hasta 75 KB, que se almacenarán en una base de datos con codificación Base64.  
  
 MaxResourceSize se establece en 2000. Esto le permite incluir imágenes externas en un informe de hasta 1500 KB de tamaño. Más información: [TechNet: Agregar una imagen externa (Generador de informes y SSRS)](https://technet.microsoft.com/library/dd220527.aspx)  
  
<a name="BKMK_Allowed"></a>   
## <a name="allowed-types-and-denied-members"></a>Tipos permitidos e integrantes denegados  
 La característica de espacio seguro para RDL permite crear una lista de tipos aprobados y lista de integrantes denegados. La lista de tipos aprobados se denomina una lista de permiso. La lista de integrantes denegados que no se permiten en expresiones RDL se denomina lista de bloqueo.  
  
 La siguiente tabla contiene una lista de tipos permitidos y de integrantes denegados disponibles en el modo de espacio seguro en Common Data Service.  
  
|Tipos permitidos|Integrantes denegados|  
|-------------------|--------------------|  
|`System.Array`|CreateInstance|  
||Finalizar|  
||GetType|  
||MemberwiseClone|  
||Cambiar tamaño|  
|||  
|`System.DateTime`|FromBinary|  
||GetDateTimeFormats|  
||GreaterThan|  
||GreaterThanOrEqual|  
|||  
|||  
|`System.Object`|GetType|  
||MemberwiseClone|  
||ReferenceEquals|  
|||  
|`System.DbNull`|Finalizar|  
||MemberwiseClone|  
||GetObjectData|  
||GetTypeCode|  
|||  
|`System.Math`|BigMul|  
||DivRem|  
||IEEERemainder|  
||E|  
||PI|  
||Pow|  
|`System.String`||  
|`System.TimeSpan`|Horas|  
||TicksPerDay|  
||TicksPerHour|  
||TicksPerMillisecond|  
||TicksPerMinute|  
||TicksPerSecond|  
||Cero|  
||TryParse|  
||TryParseExact|  
|`System.Convert`|ChangeType|  
||IConvertible.ToBoolean|  
||IConvertible.ToByte|  
||IConvertible.ToChar|  
||IConvertible.ToDateTime|  
||IConvertible.ToDecimal|  
||IConvertible.ToDouble|  
||IConvertible.ToInt16|  
||IConvertible.ToInt32|  
||IConvertible.ToInt64|  
||IConvertible.ToSByte|  
||IConvertible.ToSingle|  
||IConvertible.ToType|  
||IConvertible.ToUInt16|  
||IConvertible.ToUInt32|  
||IConvertible.ToUInt64|  
|`System.StringComparer`|Crear|  
||Finalizar|  
|||  
|`System.TimeZone`|Finalizar|  
||GetType|  
||MemberwiseClone|  
|||  
|`System.Uri`|Eliminar escape|  
||Analizar|  
||Escape|  
||Finalizar|  
|||  
|`System.UriBuilder`|Finalizar|  
|||  
|`System.Globalization.CultureInfo`|ClearCachedData|  
|||  
|`System.Text.RegularExpressions.Match`|Vacío|  
||NextMatch|  
||Resultado|  
||Sincronizado|  
|||  
|||  
|`System.Text.RegularExpressions.Regex`|CacheSize|  
||CompileToAssembly|  
||GetGroupNames|  
||GetGroupNumbers|  
||GetHashCode|  
||Eliminar escape|  
||UseOptionC|  
||UseOptionR|  
||capnames|  
||mayús|  
||capsize|  
||capslist|  
||roptions|  
||patrón|  
||fábrica|  
||IsMatch|  
||Coincidencias|  
||Iserializable.GetObjectData|  
||InitializeReferences|  
||RightToLeft|  
||Opciones|  
|||  
|||  
|`Microsoft.VisualBasic.Constants`|vbAbort|  
||vbAbortRetryIgnore|  
||vbApplicationModal|  
||vbArchive|  
||vbBinaryCompare|  
||vbCancel|  
||vbCritical|  
||vbDefaultButton1|  
||vbDefaultButton2|  
||vbDefaultButton3|  
||vbExclamation|  
||vbFormFeed|  
||vbGet|  
||vbHidden|  
||vbHide|  
||vbHiragana|  
||vbIgnore|  
||vbInformation|  
||vbKatakana|  
||vbLet|  
||vbLinguisticCasing|  
||vbMaximizedFocus|  
||vbMinimizedFocus|  
||vbMinimizedNoFocus|  
||vbMsgBoxHelp|  
||vbMsgBoxRight|  
||vbMsgBoxRtlReading|  
||vbMsgBoxSetForeground|  
||vbNo|  
||vbNormal|  
||vbNormalFocus|  
||vbNormalNoFocus|  
||vbObjectError|  
||vbOK|  
||vbOKCancel|  
||vbOKOnly|  
||vbQuestion|  
||vbReadOnly|  
||vbRetry|  
||vbRetryCancel|  
||vbSet|  
||vbSystem|  
||vbSystemModal|  
||VbTypeName|  
||vbVolume|  
||Cero|  
|`Microsoft.VisualBasic.ControlChars`|Finalizar|  
||GetType|  
||MemberwiseClone|  
|||  
|`Microsoft.VisualBasic.Conversion`|Err|  
||ErrorToString|  
||Corregir|  
|||  
|`Microsoft.VisualBasic.DateInterval`|Finalizar|  
||GetType|  
||MemberwiseClone|  
|||  
|`Microsoft.VisualBasic.Financial`|Finalizar|  
||GetType|  
||MemberwiseClone|  
||IRR|  
||NPV|  
||MIRR|  
|||  
|||  
|`Microsoft.VisualBasic.Interaction`|AppActivate|  
||Bip|  
||CallByName|  
||Comando|  
||CreateObject|  
||Environ|  
||Finalizar|  
||GetAllSettings|  
||GetObject|  
||GetSetting|  
||GetType|  
||InputBox|  
||MemberwiseClone|  
||MsgBox|  
||SaveSetting|  
||Shell|  
||Elegir|  
||Modificador|  
|||  
|||  
|`Microsoft.VisualBasic.Information`|Erl|  
||Err|  
||IsError|  
||IsDBNull|  
||Lbound|  
||Ubound|  
||SystemTypeName|  
|||  
|`Microsoft.VisualBasic.Strings`|Finalizar|  
||GetType|  
||MemberwiseClone|  
||Lset|  
||Rset|  
|||  
|`Microsoft.Crm.Reporting.RdlHelper`||  
  
<a name="BKMK_Denied"></a>   
## <a name="common-denied-members"></a>Integrantes denegados comunes  
 La siguiente tabla contiene una lista de integrantes denegados comunes en los tipos permitidos:  
  
||  
|-|  
|DateString|  
|Duración|  
|Igualdad|  
|Es igual a|  
|Erl|  
|Filtro|  
|GetChar|  
|GroupNameFromNumber|  
|GroupNumberFromName|  
|Int|  
|MaxValue|  
|MinValue|  
|Negar|  
|Temporizador|  
|TimeString|  
|ToBinary|  
|Finalizar|  
|GetType|  
|MemberwiseClone|  
  

