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
ms.openlocfilehash: 86d28400e0eaea89b59286df173d0e67655bb7a5
ms.sourcegitcommit: 6b2961308c41867756ecdd55f55eccbebf70f7f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "76541253"
---
# <a name="trace-function"></a>Función Trace 

Cuando se usa con Test Studio, Trace es una expresión opcional que se puede usar para proporcionar información adicional en los resultados de las pruebas del evento **OnTestCaseComplete**. Los mensajes de eventos de seguimiento, así como los mensajes de las aserciones superadas y con errores, se encuentran en la tabla Seguimientos, en el registro TestCaseResult. La tabla Seguimientos tiene dos propiedades, mensaje y marca de tiempo. 

Si ha permitido que la aplicación envíe datos de telemetría a Azure Application Insights, la función Trace también se puede usar para enviar información de diagnóstico o eventos personalizados a su recurso de Application Insights. Puede inspeccionar estos datos en Application Insights para ayudar a diagnosticar problemas o comprender el uso de las aplicaciones y las características. La información de seguimiento utilizada en Pruebas también se registrará en Application Insights. También se pueden ver todos los mensajes de Seguimiento en la herramienta Power Apps Monitor, que le ayudará a depurar o identificar problemas en las sesiones de diagnóstico en tiempo real de la aplicación.   

## <a name="syntax"></a>Sintaxis

*Trace(mensaje, gravedad, registro_personalizado)*

- *Mensaje*: es necesario. Información de la que se realizará un seguimiento. En las pruebas, se crea un registro en la tabla Seguimientos, en el registro TestCaseResult. 
- *Gravedad*: opcional. Nivel de gravedad del seguimiento registrado en Application Insights. Las opciones son Información, Advertencia o Error. 
- *Registro_personalizado*: opcional. Un registro que contiene los datos personalizados que se registrarán en Application Insights. 
  

### <a name="see-also"></a>Vea también

[Información general de Test Studio](../test-studio.md) <br>
[Trabajo con Test Studio](../working-with-test-studio.md)
