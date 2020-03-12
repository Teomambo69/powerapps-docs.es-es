---
title: Función Trace | Microsoft Docs
description: Información de referencia sobre la función Trace en Power Apps, incluida la sintaxis
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/19/2018
ms.author: aheneay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 927b8dae59a4dc6fc55d74c1998b0d434eb8356c
ms.sourcegitcommit: d500f44e77747a3244b6691ad9b3528e131dbfa5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2020
ms.locfileid: "79133564"
---
# <a name="trace-function"></a>Función Trace 

Cuando se usa con Test Studio, Trace es una expresión opcional que se puede usar para proporcionar información adicional en los resultados de las pruebas del evento **OnTestCaseComplete**. Los mensajes de eventos de seguimiento, así como los mensajes de las aserciones superadas y con errores, se encuentran en la tabla Seguimientos, en el registro TestCaseResult. La tabla Seguimientos tiene dos propiedades, mensaje y marca de tiempo. 

También se pueden definir mensajes de seguimiento en la aplicación. Se pueden ver en la herramienta Monitor de Power apps junto con otras actividades de la aplicación para ayudar a depurar o identificar problemas con la información de diagnóstico en tiempo real de la aplicación. Si ha permitido que la aplicación envíe datos de telemetría a Azure Application Insights, la función Trace también se puede usar para enviar información de diagnóstico o eventos personalizados a su recurso de Application Insights. Puede inspeccionar estos datos en Application Insights para ayudar a diagnosticar problemas o comprender el uso de las aplicaciones y las características. La información de seguimiento utilizada en Pruebas también se registrará en Application Insights. La información de seguimiento de prueba no estará disponible en la herramienta de supervisión, ya que el monitor está conectado a la aplicación cuando se reproduce desde Canvas Studio. 

## <a name="syntax"></a>Sintaxis

*Seguimiento (mensaje, trace_severity, custom_record)*

- *Mensaje*: es necesario. Información de la que se realizará un seguimiento. En las pruebas, se crea un registro en la tabla Seguimientos, en el registro TestCaseResult. 
- *Trace_severity* : opcional. Nivel de gravedad del seguimiento registrado en Application Insights. Las opciones son TraceSeverity. Information, TraceSeverity. WARNING o TraceSeverity. error. 
- *Registro_personalizado*: opcional. Un registro que contiene los datos personalizados que se registrarán en Application Insights. 
  

### <a name="see-also"></a>Vea también

[Información general de Test Studio](../test-studio.md) <br>
[Trabajo con Test Studio](../working-with-test-studio.md)
