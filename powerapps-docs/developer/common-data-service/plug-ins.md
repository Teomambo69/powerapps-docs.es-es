---
title: Usar complementos para ampliar los procesos de negocio (Common Data Service) | Microsoft Docs
description: Un complemento es un montaje de .NET que puede cargar al Common Data Service. Las clases dentro del ensamblado pueden registrarse en los eventos específicos (pasos) dentro del marco de eventos. El código dentro de la clase ofrece una forma de responder al evento para poder aumentar o modificar el comportamiento predeterminado de la plataforma.
ms.custom: ''
ms.date: 03/27/2019
ms.reviewer: phecke
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 110a530c25c7f7e502c26da18bf2f473d53b6673
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749815"
---
# <a name="use-plug-ins-to-extend-business-processes"></a>Use complementos para ampliar los procesos de negocio

Un complemento es un montaje de .NET que puede cargar al Common Data Service. Las clases dentro del ensamblado pueden registrarse en los eventos específicos (pasos) dentro del marco de eventos. El código dentro de la clase ofrece una forma de responder al evento para poder aumentar o modificar el comportamiento predeterminado de la plataforma.

> [!IMPORTANT]
> Siempre que sea posible, primero debe considerar aplicar una de las opciones declarativas para definir la lógica de negocios. Más información: [Aplicar lógica de negocios en Common Data Service para aplicaciones](../../maker/common-data-service/cds-processes.md)<br/><br/>
> Use las extensiones cuando un proceso declarativo no cumpla su requisito.

Las clases en el ensamblado que puede registrar un paso debe implementar la interfaz <xref:Microsoft.Xrm.Sdk.IPlugin>. Esta interfaz expone un solo método: <xref:Microsoft.Xrm.Sdk.IPlugin.Execute*>. Cuando un evento aparece con una clase registrada a él, los datos contextuales se pasan al método `Execute`. En el método `Execute` puede:

- Cancelar el evento y mostrar un error al usuario
- Realizar cambios en los datos de la operación
- Emprender otras acciones con el servicio de organización para agregar la automatización

Los complementos se pueden configurar para ejecutarse de forma sincrónica o asincrónica. Un complemento sincrónico hará la operación espere hasta que se complete el código del complemento. Este tiene un impacto en el rendimiento percibido del sistema. Las operaciones en un complemento asincrónico se ubican en una cola y se ejecutan tras completar la operación, para que la operación puede completarse con una interrupción mínima.

## <a name="when-to-use-plug-ins"></a>Cuándo usar complementos

La gente a menudo compara flujos de trabajo y complementos como las opciones para aplicar lógica empresarial personalizada. Hay una superposición importante en las capacidades de flujos de trabajo y de complementos. Los complementos pueden hacer todos los flujos de trabajo pueden hacer lo contrario pero no es cierto. Sin embargo, esto no significa que debe usar solo complementos para cualquier cosa que no se puede hacer con un flujo de trabajo. Hay otras formas de cumplir los requisitos sin usar los complementos. 

- Los flujos de trabajo pueden usar las extensiones personalizadas del flujo de trabajo (actividades de flujo de trabajo) que le permiten crear condiciones y acciones que pueden reutilizarse con el código que puede usarse en múltiples flujos de trabajo. 

- Los campos calculados y de informes proporcionan las capacidades que antes solo podrían hacerse usando flujos de trabajo.

- Las acciones personalizadas son un tipo de similar de proceso para los flujos de trabajo que permiten crear mensajes que pueden reutilizarse y que se pueden invocar desde otros flujos de trabajo o de los extremos de servicios web.

- La integración de bus del servicio Azure y los vínculos web se pueden usar para insertar datos a los sistemas externos donde la lógica se puede aplicar con diferentes recursos.

- Microsoft Flow ofrece muchas capacidades que antes se ejecutaban usando complementos.

Puede tener numerosas opciones disponibles. Debería evaluar cada una de ellas para comprender la mejor forma que cumpla sus requisitos.

### <a name="advantages-of-plug-ins"></a>Ventajas de los complementos

Estas son las principales ventajas de los complementos:

- Los complementos rinden bien. Un complemento bien escriba proporciona la forma más eficaz de aplicar lógica de negocios.
- Los complementos son eficaces. Muchos desarrolladores preferirían usar los conocimientos y los conocimientos que poseen para definir lógicas y a usar las funcionalidades para trabajar directamente con los servicios de servicio o servicios externos de la organización en código. Un desarrollador de complementos experimentado puede ser muy productivo.

### <a name="disadvantages-of-plug-ins"></a>Desventajas de los complementos

- Los complementos requieren los conocimientos especiales de un programador que escriba y mantenga el código. Los programadores son costosos y mucho negocios no tiene acceso a uno cuando es necesario. Los procesos de negocio pueden cambiar rápidamente y proporcionar las opciones para habilitar el cambio sin requerir un programador puede permitir que el sistema se adapte más rápido.
- Se puede abusar de los complementos. Un complemento mal escrito puede producir un gran impacto de un el rendimiento del entorno. El gran potencial de los complementos debe aplicarse con cierta mesura y consideración con el impacto que tienen en todo el sistema.


## <a name="next-steps"></a>Pasos siguientes

Use el tutorial siguiente y temas prácticos para aprender a escribir complementos

### <a name="tutorials"></a>Tutoriales

Estos temas le guían por el proceso de creación de algunos complementos básicos.

- [Tutorial: Escribir y registrar un complemento](tutorial-write-plug-in.md)
- [Tutorial: Depurar un complemento](tutorial-debug-plug-in.md)
- [Tutorial: Actualizar un complemento](tutorial-update-plug-in.md)

### <a name="how-to-topics"></a>Temas de aprendizaje

Estos temas proporcionan los detalles que usará para crear complementos.

- [Escribir un complemento](write-plug-in.md)
- [Administrar excepciones](handle-exceptions.md)
- [Registro de un complemento](register-plug-in.md)
- [Depuración de complementos](debug-plug-in.md)
 
Estos temas proporcionan información adicional sobre la escritura o la depuración de complementos o sobre el análisis de su rendimiento.

- [Suplantar a un usuario](impersonate-a-user.md)
- [Registro y seguimiento](logging-tracing.md)
- [Analizar el rendimiento](analyze-performance.md)
- [Acceso a recursos web externos](access-web-services.md)
