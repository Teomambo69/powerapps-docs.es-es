---
title: Depurar complementos (Common Data Service) | Microsoft Docs
description: Aprenda a depurar complementos mediante la herramienta de registro de complementos.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
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
ms.openlocfilehash: 637ed40097ff29cc74cdfc671eb4e2f6cf7edf2b
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156276"
---
# <a name="debug-plug-ins"></a>Depuración de complementos

El proceso para escribir, registrar y depurar un complemento es:

1. Crear un proyecto de biblioteca de clases de .NET Framework en Visual Studio
1. Agregar el paquete `Microsoft.CrmSdk.CoreAssemblies` NuGet al proyecto
1. Implementar la interfaz <xref:Microsoft.Xrm.Sdk.IPlugin> en clases que se registrarán como pasos.
1. Agregar su código al método <xref:Microsoft.Xrm.Sdk.IPlugin.Execute*> requerido por la interfaz
    1. Obtener las referencias a los servicios que necesita
    1. Adición de lógica de negocios
1. Firmar y crear el ensamblado
1. Probar el ensamblado
    1. Registrar el ensamblado en un entorno de prueba
    1. Agregar el ensamblado registrado y pasos a una solución no administrada
    1. **Probar el comportamiento del ensamblado**
    1. **Comprobar que se escriben los registros de seguimiento esperados**
    1. **Depure el ensamblado según sea necesario**

El contenido de este tema convierte los pasos anteriores **en negrita** y ofrece los tutoriales siguientes:

- [Tutorial: Escribir y registrar un complemento](tutorial-write-plug-in.md)
- [Tutorial: Depurar un complemento](tutorial-debug-plug-in.md)
- [Tutorial: Actualizar un complemento](tutorial-update-plug-in.md)

## <a name="test-your-assembly"></a>Probar el ensamblado

La forma más sencilla de probar el ensamblado puede ser sencillamente realizar manualmente la operación con la aplicación. Pero también debe tener en cuenta que los eventos que hacen que los complementos se ejecuten se pueden iniciar de varias formas, como una entidad creada desde un flujo de trabajo, o desde servicios web.

Los valores de atributo u otra información de contexto de ejecución pueden ser diferentes en función de cómo se realiza la acción. Al escribir el complemento, es importante que realice prácticas de programación defensiva y que no suponga que cada valor que espere siempre estará ahí.

Es posible que desee escribir un programa que automatice la realización de operaciones que harán el complemento se desencadene e incluya varias variaciones posibles.

Si desea usar un marco de automatización de prueba, descubrirá que la comunidad ha creado algunas herramientas para este tipo de marco. Más información: [Herramientas de pruebas para el desarrollo de servidor](testing-tools-server.md)


## <a name="use-tracing"></a>Usar seguimiento

Como se describe en [Usar el servicio de seguimiento](write-plug-in.md#use-the-tracing-service), puede escribir mensajes en la [entidad de PluginTraceLog](reference/entities/plugintracelog.md) en el código del complemento mediante el <xref:Microsoft.Xrm.Sdk.ITracingService>.<xref:Microsoft.Xrm.Sdk.ITracingService.Trace*> .

Para poder usar este servicio, debe habilitar el seguimiento en el entorno de Common Data Service. El proceso se describe en [Ver registros de seguimiento](tutorial-write-plug-in.md#view-trace-logs).

> [!NOTE]
> El registro de seguimiento ocupa espacio de almacenamiento de la organización, especialmente cuando se generan muchos seguimientos y excepciones. Solo debe activar el registro de seguimiento para depurar y solucionar problemas, y desactivarla después de que la investigación esté completa.

Mientras se realiza la depuración, puede fácilmente consultar los registros de seguimiento de una clase de complemento determinado usando la API web del explorador. Si el ensamblado se llama `BasicPlugin.FollowUpPlugin`, puede usar esta consulta en el campo de dirección del explorador:

`GET <your org uri>/api/data/v9.0/plugintracelogs?$select=messageblock&$filter=typename eq 'BasicPlugin.FollowUpPlugin'`

Los resultados de JSON se devolverán a su explorador como:


```json
{
    "@odata.context": "<your org uri>/api/data/v9.0/$metadata#plugintracelogs(messageblock)",
    "value": [{
        "messageblock": "FollowupPlugin: Creating the task activity.",
        "plugintracelogid": "f0c221d1-7f84-4f89-acdb-bbf8f7ce9f6c"
    }]
}
```

> [!TIP]
> Esto funciona mejor si instala un complemento del explorador que aplicará formato al JSON devuelto. O bien puede usar Postman. Más información: [Usar Postman con API web](/dynamics365/customer-engagement/developer/webapi/use-postman-web-api)
> 
> Puede preferir usar el [Visor de seguimiento de complementos XrmToolbox](https://www.xrmtoolbox.com/plugins/Cinteros.XrmToolBox.PluginTraceViewer/). Esta herramienta de la comunidad no se admite en Microsoft. Si tiene alguna duda relacionada con esta herramienta, póngase en contacto con el Editor.

Los mensajes de seguimiento también se pueden encontrar en el archivo de registro que puede ser descargado cuando un complemento sincrónico o un montaje de flujo de trabajo personalizado produce un error que da como resultado un diálogo de error que se muestra al usuario. El usuario puede seleccionar el botón **Descargar archivo de registro** para ver el registro que contiene los detalles de la excepción y la salida de seguimiento.

Para los complementos registrados asincrónicos o los ensamblados de flujo de trabajo que devuelven una excepción, la información de seguimiento aparece en el área de detalles del formulario **Trabajo del sistema** en la aplicación web.

> [!NOTE]
> Si el código personalizado se ejecuta en una transacción de la base de datos y se produce una excepción que provoca una reversión de la transacción, todos los cambios en los datos de la entidad realizados por el código se desharán. Sin embargo, los registros de entidad `PluginTraceLog` se mantendrán después de que la reversión se complete.

## <a name="use-plug-in-profiler"></a>Usar el generador de perfiles de complementos

El generador de perfiles de complementos es una solución que puede instalar en el entorno que le permite capturar el contexto de ejecución de un complemento y usar esos datos para reproducir el evento dentro de Visual Studio mientras se realiza la depuración.

Puede encontrar instrucciones para instalar y usar el generador de perfiles de complementos en el [Tutorial: Depurar un complemento](tutorial-debug-plug-in.md). Consulte [Instalar el generador de perfiles de complementos](tutorial-debug-plug-in.md#install-plug-in-profiler) y [Depurar el complemento](tutorial-debug-plug-in.md#debug-your-plug-in)

### <a name="view-plug-in-profile-data"></a>Ver los datos del generador de perfiles de complementos

Después de instalar el generador de perfiles de complementos y de capturar algunos perfiles, puede ver el contexto del evento y reproducir los datos que se usan cuando realiza la depuración. Ver estos datos puede ayudarle a comprender los datos del contexto de ejecución que el complemento puede usar.

Puede ver estos datos mediante la herramienta de registro de complementos seleccionando el comando **Ver perfil de complemento**. Se abrirá el diálogo de perfil de complementos.

![Abrir el perfil de complementos](media/view-plug-in-profile.png)

Seleccione el icono ![icono de descarga](media/prt-down-arrow-icon.png) y en el diálogo **Seleccionar perfil de CRM**, especifique el elemento de registro que usará.

![Seleccionar perfil de CRM](media/prt-select-profile-from-crm.png)

Y luego seleccione **Ver** en el cuadro de diálogo **Perfil de complemento**.

Esto descargará un archivo XML abierto con información del perfil. El elemento `Context` representa el contexto de ejecución que se pasa al complemento.

![ejemplo de datos de perfil](media/prt-example-profile-data.png)

### <a name="more-information"></a>Más información

[Herramientas de pruebas para el desarrollo de servidor](testing-tools-server.md)