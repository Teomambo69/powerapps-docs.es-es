---
title: Limitar el registro de complementos para los mensajes Retrieve y de RetrieveMultiple | MicrosoftDocs
description: Si se agrega lógica de complementos síncrona a los eventos de mensaje Retrieve y de RetrieveMultiple, se puede producir lentitud.
services: ''
suite: powerapps
documentationcenter: na
author: jowells
manager: austinj
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 1/15/2019
ms.author: jowells
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: d17772aab805ae6d7969db19b888b3565926ca6c
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749396"
---
# <a name="limit-the-registration-of-plug-ins-for-retrieve-and-retrievemultiple-messages"></a>Limitar el registro de complementos para los mensajes Retrieve y de RetrieveMultiple

**Categoría**: rendimiento

**Potencial de impacto**: medio

<a name='symptoms'></a>

## <a name="symptoms"></a>Síntomas

Si se agrega lógica de complementos síncrona a los eventos de mensaje Retrieve y de RetrieveMultiple, puede provocar:

- Aplicaciones basadas en modelos que dejan de responder
- Interacciones lentas con el cliente
- El explorador deja de responder

<a name='guidance'></a>

## <a name="guidance"></a>Instrucciones

Evalúe el diseño de soluciones que incluyen complementos registrados para los mensajes Retrieve y RetrieveMultiple.  En general, no se recomienda registrar complementos para estos mensajes debido a los riesgos asociados con ralentizar las solicitudes para devolver un registro o registros de entidad desde varios puntos de entrada.  Sin embargo, puede ser adecuado para el diseño de su aplicación. Un ejemplo de una aplicación común sería la inyección de criterios de filtro adicionales a una consulta existente específica. Esto permite que las soluciones compensen por aquello que no se puede hacer en la interfaz de usuario para las vistas.  El diseñador de vistas solo puede admitir un grado de complejidad determinado y otras opciones deben utilizarse para aumentar los resultados o la consulta.

Si es una solución adecuada, siga estas sugerencias para minimizar el impacto en el entorno:

- Incluya las condiciones del código del complemento para comprobar rápidamente si debe implementarse a lógica de destino. Si no es así, vuelva rápidamente, sin ejecutar los pasos adicionales que no son necesarios y que retrasarán devolver los datos al autor de la llamada.

- Evite incluir las tareas prolongadas, especialmente las que pueden no ser deterministas, como la invocación de las llamadas de servicio externas o las consultas complejas a Dynamics 365.

- Limite o evite consultar datos adicionales de Common Data Service

### <a name="virtual-entities"></a>Entidades virtuales

Por lo general Retrieve y RetrieveMultiple se invocan en el complementos para recuperar datos de orígenes externos. Los datos de orígenes externos se generan en PowerApps o se usan trabajar con los datos existentes o gestionarlos. Dynamics 365 (online) versión 9.0 presenta una función denominada [Entidades virtuales](/dynamics365/customer-engagement/developer/virtual-entities/get-started-ve) que permiten la integración de los datos que se encuentran en sistemas externos y representan sin problemas esos datos como entidades en PowerApps, sin replicación de datos y a menudo sin código personalizado. Consulte la documentación de [Entidades virtuales](/dynamics365/customer-engagement/developer/virtual-entities/get-started-ve) para obtener más información acerca de las funcionalidades, las limitaciones y la configuración.

### <a name="retrieve-caution"></a>Precaución de Retrieve

Common Data Service activará al menos dos mensajes Retrieve para cada carga de formulario de entidad.  Una recuperación contiene atributos limitados, lo que puede variar en función de la entidad y las llamadas posteriores incluirán más atributos.  Si se espera que se produzca una sola acción durante la carga de un formulario, no confíe totalmente en el desencadenador de un mensaje Retrieve.

<a name='additional'></a>

## <a name="additional-information"></a>Información adicional

Los mensajes `Retrieve` y `RetrieveMultiple` son los dos mensajes procesados más frecuentes. El mensaje `Retrieve` se desencadena al abrir un formulario de entidad o si se va a obtener acceso a la entidad mediante la operación `Retrieve` en uno de los extremos de servicio. `RetrieveMultiple` se desencadena debido a la distintas acciones en los extremos de la aplicación y el servicio, por ejemplo, al rellenar una cuadrícula de la interfaz de usuario.  Si se agrega lógica de complementos síncrona a estos eventos de mensaje, se puede producir lentitud.

<a name='seealso'></a>

### <a name="see-also"></a>Vea también

[Optimizaciones del rendimiento para Microsoft Dynamics CRM Online](https://mbs.microsoft.com/customersource/northamerica/CRM/learning/documentation/user-guides/PerformanceOptimizationsCRMOnlineSuccess)<br />
[Crear y editar entidades virtuales que contienen datos desde un origen de datos externo](/powerapps/maker/common-data-service/create-edit-virtual-entities)<br />
