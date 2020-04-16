---
title: 'Diseño de la personalización escalable: información general (Common Data Service) | Microsoft Docs'
description: 'El primero de una serie de temas. Este tema presenta los síntomas que pueden ocurrir cuando las personalizaciones de código no se optimizan y las restricciones con que deben lidiar las personalizaciones de código para evitarlos. '
ms.custom: ''
ms.date: 1/15/2019
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: rogergilchrist
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 6dd7163c10e9b10dd7cdb91a6e1571ffef63f566
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155308"
---
# <a name="scalable-customization-design-in-common-data-service"></a>Diseño de personalización escalable en Common Data Service

> [!NOTE]
> Este es el primero de una serie de temas sobre el diseño de la personalización escalable. Aunque este contenido está dividido en temas separados, muestra una vista global de los conceptos, los problemas y las estrategias que rodean el diseño de las personalizaciones escalables. Cada tema se basa en conceptos establecidos en temas anteriores.
> Puede [descargar estos temas en un solo documento PDF](/powerapps/opbuildpdf/developer/common-data-service/scalable-customization-design/TOC.pdf?branch=live) si desea leerlo sin conexión.

Common Data Service se diseñó para protegerse a sí mismo y a los usuarios de las actividades prolongadas que podrían afectar los tiempos de respuesta para el usuario que crea una solicitud y a la estabilidad y la capacidad de respuesta del sistema para otros usuarios.

Un reto al que se enfrentaron algunas personas que implementaron soluciones Common Data Service son los errores que genera la plataforma o la base de datos de Microsoft SQL Server subyacente cuando estas acciones protectoras se hacen efectivas. Esto se interpreta a menudo como que la plataforma no se puede escalar o que se termina incorrectamente o que limita las solicitudes al sistema.

Este contenido se basa en la experiencia por la investigación y gestión de las causas subyacentes verdaderas de la mayoría de estos tipos de retos. Estos temas describen cómo la plataforma se protege de la repercusión de estas solicitudes impuestas al sistema y se explica por qué este comportamiento es con mayor frecuencia el resultado de implementaciones personalizadas que no consideran el impacto en los bloqueos y el uso de las transacciones en la plataforma.

Este contenido también describe cómo optimizar una implementación personalizada para evitar estos tipos de comportamientos no solo evitará errores de la plataforma, sino que también ofrecen un mejor rendimiento y la experiencia de usuario final como consecuencia. Proporciona buenas prácticas de diseño e identifica errores comunes a evitar.

## <a name="the-challenge"></a>La dificultad

La investigación y la gestión de las dificultades en esta área empieza normalmente determinados tipos de errores y de síntomas aparecen en el sistema. Se perciben con frecuencia como problemas en la plataforma y el paso necesario para remediarlos es aflojar las restricciones en la plataforma que normalmente desencadenan que una solicitud de ejecución lenta para pase notificarse como error.

En realidad, mientras que los errores se podían haber evitado a corto plazo suavizando algunas de las restricciones de la plataforma, estas restricciones existen por razones buenas para evitar que una acción de ejecución excesivamente prolongada afecte a los demás usuarios o al rendimiento del sistema. Mientras que se podrían suavizar las restricciones evitar errores, los usuarios seguirían experimentando tiempos lentos de respuesta y esto podría afectar la experiencia de otros usuarios del sistema también.

Por lo tanto, es preferible buscar las causas originales de por qué estas restricciones se están desencadenado y provocando errores y, a continuación, optimizar las personalizaciones de código para evitarlas. Esto le ofrecerá un sistema más uniforme y con más capacidad de respuesta para los usuarios. 

### <a name="common-symptoms"></a>Síntomas comunes

Estos tipos de problemas presentan normalmente una combinación de síntomas comunes como se muestra en la tabla siguiente.

|Síntoma|Descripción|
|--|--|
|**Solicitudes lentas**|Los usuarios aprecian tiempos de respuesta lentos para en áreas del sistema en particular, por ejemplo, determinados formularios y consultas.|
|**Errores de SQL genéricos**|Algunas acciones responden con un informe de errores de la plataforma un error genérico de SQL. <br />Esto se traduce a menudo en una capa de la plataforma para un tiempo de espera de SQL.|
|**Paradas**|Informes de errores de la plataforma que indican que se produjo una parada, que ha forzado que se terminara la acción y se revierte.|
|**Rendimiento limitado**|Particularmente en escenarios de carga por lotes, esto a menudo se traduce en un rendimiento muy lento, mucho más lento de lo que se debería poder.|
|**Errores intermitentes y rendimiento lento**|Un indicador importante de estos comportamientos es cuando la misma acción puede ser muy rápida o muy lenta, y al reintentarla va mucho más rápido o evita un error.|

En realidad una combinación de estos síntomas puede notificarse, y a menudo se hace, a la vez cuando se presentan estas dificultades. No es siempre el caso que estos síntomas sean un indicador de problemas en el diseño. Otros problemas, como limitaciones de E/S de disco en la base de datos o un error del producto, pueden causar síntomas similares. Pero la causa más común de estos tipos de síntomas y por lo tanto es útil comprobarlo, se relaciona directamente con el diseño de la implementación personalizada y cómo afecta al sistema. 

> *¿Por qué preocuparnos?, Common Data Service para aplicaciones se encarga de ello ¿no?*

Hace todo lo que puede… Pero usa el bloqueo y las transacciones para proteger el sistema contra conflictos cuando es necesario.

También proporcionamos opciones para que tome decisiones sobre el escenario específico y decida dónde es importante controlar el acceso a los datos. Pero estas decisiones pueden ser incorrectas y es posible introducir consecuencias involuntarias en código personalizado. Estos problemas suelen tener un impacto en la experiencia de usuario con tiempos de respuesta más lentos de modo que comprender las implicaciones de determinadas acciones puede traducirse en resultados más uniformes y mejores para los usuarios.

## <a name="understanding-causes"></a>Descripción de las causas

Los síntomas comunes hace que se fuercen solicitudes particulares para una ejecución lenta y desencadenan restricciones de la plataforma. En el siguiente diagrama muestra los síntomas típicos con algunas de las causas originales comunes de estos síntomas.

![causas subyacentes](media/understanding-causes.png)

El impacto subyacente de las transacciones prolongadas, el bloqueo de bases de datos y las consultas complejas pueden superponerse y amplificar los efectos para provocar estos síntomas. Por ejemplo, una serie de consultas prolongadas totalmente independientes entre sí puede producir tiempos de respuesta lentos para el usuario, pero solo cuando necesiten acceso a los mismos recursos los tiempos de respuesta serán más lentos y se convierten en errores. 

## <a name="design-for-platform-constraints"></a>Diseño de las restricciones de plataforma

La plataforma de Common Data Service tiene varias restricciones deliberadas que impone para evitar cualquier acción con un impacto demasiado perjudicial sobre el resto del sistema y, por tanto, los usuarios. Mientras que este comportamiento puede ser frustrante ya puede bloquear el que solicitudes específicas se completen y a menudo lleva a preguntas acerca de si las restricciones se pueden suavizar, se trata en raras ocasiones de un buen método cuando se consideran las implicaciones más generales.

Cuando se usa la plataforma como se tiene previsto y se optimiza una implementación, es muy raro encontrar escenarios donde se den estas restricciones. Toparse con la restricción es casi siempre un indicador de comportamientos que limitarán en exceso los recursos en el sistema. Esto significa que otras solicitudes del mismo usuario o de otros usuarios no se podrán procesar. Por lo tanto, mientras que es posible suavizar las restricciones de la solicitud que está bloqueada, lo que significa realmente es que los recursos que está consumiendo estarán limitados durante más tiempo aún lo que provocará repercusiones mayores en otros usuarios.

En el centro de estas restricciones está la idea de que la plataforma Common Data Service está diseñada para admitir una aplicación transaccional para múltiples usuarios donde la prioridad es dar una respuesta rápida a las demandas de los usuarios. No se pretende que sea una plataforma para ejecuciones prolongadas ni el procesamiento por lotes. Es posible generar una serie de breves solicitudes a Common Data Service, pero Common Data Service no está diseñado para administrar un procesamiento por lotes. Igualmente, si se trata de actividades que ejecuten procesamientos iterativos voluminosos, Common Data Service no está diseñado para administrar ese procesamiento iterativo.

En estas situaciones de ejemplo, un servicio independiente se puede usar para hospedar los procesos prolongados y generar solicitudes transaccionales más cortas a Common Data Service. Por ejemplo, si se usa Flow o se hospeda Microsoft SQL Server Integration Services (SSIS) en otro sitio, crear o generar solicitudes individuales para Common Data Service es un método mucho mejor que usar un complemento en recorrer miles de registros que se crearon en Common Data Service.

Vale la pena conocer y comprender las restricciones de la plataforma que existen para poder tenerlas en cuenta en el diseño de las aplicaciones. Además, si experimenta estos errores, podrán entender por qué se producen y sabrá lo que puede cambiar para evitarlos.

|Restricción|Descripción|
|--|--|
|**Tiempos de espera de complementos**|&bull; Los complementos agotan el tiempo de espera después de 2 minutos. <br />&bull; No realice operaciones prolongadas en los complementos. Protege la plataforma y el servicio de espacio aislado y, en definitiva, al usuario de experiencias deficientes.|
|**Tiempos de espera de SQL**|&bull; Las solicitudes a SQL Server agotan el tiempo de espera en 30 segundos.<br />&bull; Protege frente a solicitudes de ejecución prolongada.<br />&bull; Proporciona protección en una organización específica y su base de datos privada.<br />&bull; También ofrece protección en los servidores de base de datos frente a un uso excesivo de recursos compartidos como procesadores y memoria.|
|**Límites de flujos de trabajo**|&bull; Funciona bajo una directiva justa de uso.<br />&bull; No hay límites rígidos específicos, sino que lo que se hace es equilibrar los recursos en las organizaciones.<br />&bull; Donde la demanda es baja, la organización puede aprovechar la máximo la capacidad disponible. Donde la demanda es alta, se comparten los recursos y el rendimiento.|
|**Conexiones simultáneas máximas**|&bull; Hay una configuración predeterminada para la plataforma con un límite de grupo de conexiones máximas de 100 conexiones desde la conexión del servidor web en IIS a la base de datos. Common Data Service no cambia este valor<br />&bull; Si le ocurre esto, es una indicación de un error en el sistema; consulte por qué hay tantas conexiones bloqueadas.<br />&bull; Con múltiples servidores web, cada uno con 100 conexiones simultáneas a la base de datos de 10ms &lt;, que es lo normal, se espera un rendimiento de &gt; 10 000 solicitudes de base de datos para cada servidor web. Esto no debería solicitarse y originaría otras dificultades mucho antes de llegar a ese punto.|
|**ExecuteMultiple**|&bull; El mensaje `ExecuteMultiple` está diseñado para prestar ayuda con las colecciones de operaciones que se envían a Common Data Service desde un origen externo.<br />&bull; El procesamiento de grupos grandes de estas solicitudes puede bloquear recursos cruciales en Common Data Service en detrimento de que los usuarios puedan efectuar más solicitudes críticas de respuesta, por consiguiente esto está limitado a 2 solicitudes `ExecuteMultiple` simultáneas por organización.|

## <a name="next-steps"></a>Pasos siguientes

Para entender cómo se aplican las restricciones de la plataforma, es necesario comprender las transacciones de base de datos. Más información: [Diseño de personalización escalable: Transacciones de bases de datos](database-transactions.md)


