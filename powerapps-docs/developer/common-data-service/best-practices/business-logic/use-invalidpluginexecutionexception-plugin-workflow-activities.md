---
title: Utilizar InvalidPluginExecutionException en actividades de complementos y de flujo de trabajo | MicrosoftDocs
description: Use InvalidPluginExecutionException al publicar errores en el contexto de las actividades de complemento o de flujo de trabajo.
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: ryjones
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 3/5/2020
ms.author: JimDaly
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0657e9b39713f4f11d68daac1c60fa144dc6ab08
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "3109141"
---
# <a name="use-invalidpluginexecutionexception-in-plug-ins-and-workflow-activities"></a>Utilizar InvalidPluginExecutionException en actividades de complementos y de flujo de trabajo

**Categoría**: mantenimiento, uso

**Potencial de impacto**: medio

<a name='symptoms'></a>

## <a name="symptoms"></a>Síntomas

Si un complemento sincrónico devuelve a la plataforma una excepción que no sea <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException>, en un cliente de Power Apps se mostrará un error al usuario con el mensaje de la excepción <xref:System.Exception.Message> y el seguimiento de la pila. Esto proporciona una experiencia hostil de usuario ya que es probable que ya sea una situación de frustración.

Si está usando <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> para cancelar intencionalmente la operación debido a un problema de lógica de validación de datos, debe proporcionar orientación aplicable al usuario de la aplicación para que pueda corregir el problema y continuar.

Si el error es inesperado, aún se recomienda detectar el error y convertirlo en un <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> para que las aplicaciones puedan mostrar un mensaje de error amigable con orientación para ayudar a un usuario o personal técnico a identificar rápidamente el problema.

<a name='guidance'></a>

## <a name="guidance"></a>Instrucciones

Los complementos solo deben devolver un <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> por las siguientes razones:

- Mostrar un mensaje útil al usuario
- Se evita que aumente el archivo de seguimiento/registro de eventos

No convertir el mensaje en un <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> generará un error `IsvUnExpected` sin mensaje mostrado al usuario desde un cliente de Power Apps.

<a name='problem'></a>

## <a name="problematic-patterns"></a>Patrones problemáticos

> [!WARNING]
> Estos patrones deben evitarse.

No use HTML dentro del texto del mensaje de error. 

Las aplicaciones web que acceden a datos CDS deben codificar a HTML cualquier texto de mensaje de error antes de mostrarlo a un usuario. Esto evitará que se procese cualquier HTML en su mensaje como lo desea. Solo mostrará el código HTML.


<a name='seealso'></a>

### <a name="see-also"></a>Vea también

[Cancelación de una operación](../../handle-exceptions.md#cancelling-an-operation)<br/>
[Depurar actividades de flujo de trabajo personalizadas](../../workflow/workflow-extensions.md#debug-workflow-activities)<br/>