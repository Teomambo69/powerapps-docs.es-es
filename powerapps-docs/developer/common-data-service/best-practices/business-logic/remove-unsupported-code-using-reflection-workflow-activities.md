---
title: Quitar código incompatible que usa reflexión en actividades de flujo de trabajo personalizadas | MicrosoftDocs
description: Debe quitar el fragmento de código mencionado en este tema si lo encuentra en actividades de flujo de trabajo personalizadas
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
ms.date: 18/15/2019
ms.author: jdaly
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="remove-unsupported-code-that-uses-reflection-in-custom-workflow-activities"></a>Quitar código no admitido que usa reflexión en actividades de flujo de trabajo personalizadas

**Categoría**: Fiabilidad

**Potencial de impacto**: alto

<a name='symptoms'></a>

## <a name="symptoms"></a>Síntomas

Las actividades de flujo de trabajo que contienen código no admitido que usa reflexión aparecerán en los próximos meses a menos que se quiten.

Las extensiones de flujo de trabajo fallarán lanzando el error `Could not load file or assembly 'Microsoft.Crm.Workflow, Version=`. El número de versión puede ser distinto pero normalmente es `6.0.0.0`.


<a name='guidance'></a>

## <a name="guidance"></a>Instrucciones

No debe incluir y debe buscar y quitar proactivamente código en actividades de flujo de trabajo personalizadas como las siguientes:

```
var type = Type.GetType("Microsoft.Crm.Workflow.SynchronousRuntime.WorkflowContext, Microsoft.Crm.Workflow, Version=6.0.0.0");
type.GetProperty("ProxyTypesAssembly").SetValue(serviceFactory, typeof(YourServiceContext).Assembly, null); 
```

Si encuentra código como este que está usando reflexión en una actividad de flujo de trabajo personalizada debe quitarlo, recompilarlo y actualizar el ensamblado que lo contiene.

<a name='problem'></a>

## <a name="problematic-patterns"></a>Patrones problemáticos

Hoy, este código no sirve a ningún objetivo. Parece que lo han agregado los desarrolladores que buscan una solución alternativa para un problema con tipos seguros (tiempo de compilación) hace unos 7 años. 

Los fragmentos que incluyen este código se encuentran en muchas entradas de foro no relacionadas con el problema. Se menciona como una solución en este mensaje en Desbordamiento de pila [¿Cómo aplicar EnableProxyTypes en un servicio al que se accede desde IWorkflowContext en CRM 2011?](https://stackoverflow.com/questions/9230117/how-to-enableproxytypes-on-a-service-accessed-from-the-iworkflowcontext-in-crm-2/45948206)

El problema subyacente sobre la compatibilidad de tipos seguros se ha corregido, pero este código se ha mantenido en la base de código para actividades de flujo de trabajo personalizadas. Este código nunca ha sido compatible, pero no afectaba a nada. En los próximos meses, comenzará a hacer que se interrumpa el flujo de trabajo personalizado que lo incluya.


<a name='additional'></a>

## <a name="additional-information"></a>Información adicional

Estamos en proceso de publicar cambios que permitirán el uso de la reflexión en actividades de flujo de trabajo personalizadas. Sin embargo, en el entorno de espacio aislado donde este código ejecutará llamadas mediante [Método Type.GetType](/dotnet/api/system.type.gettype) debe usar el nombre completo del ensamblado. Además de ser innecesario, este código no usa el nombre completo y esta es la razón por la que genera un error.

La reflexión no está permitida actualmente. Este código hace referencia a un ensamblado interno que se incluyó en una lista blanca de modo que el código interno pudiera tener reflexión sobre él. Esta es la razón por la que no genera actualmente un error. Pero cuando las restricciones generales se supriman en el futuro, hará que actividad de flujo de trabajo se interrumpa.

Para proporcionar más capacidades en actividades de flujo de trabajo personalizadas sin interrumpir la lógica de negocio de los usuarios, es necesario que todo el mundo revise su código base y quite referencias como ésta.

<a name='seealso'></a>

### <a name="see-also"></a>Vea también

[Extensiones de flujo de trabajo](../../workflow/workflow-extensions.md)