---
title: Personalizaciones compatibles para Common Data Service (Common Data Service) | Microsoft Docs
description: Lea cómo puede personalizar Common Data Service mediante las herramientas disponibles en el portal Power Apps o las que aparecen descritas en documentos.
ms.custom: ''
ms.date: 01/25/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: shmcarth
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 38cf4a367c197649dde3e9f8737584f03c9b4a1a
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "2883514"
---
<!-- This is the portion of the old topic that applies to Common Data Service
https://docs.microsoft.com/dynamics365/customer-engagement/developer/supported-extensions
 -->


# <a name="supported-customizations-for-common-data-service"></a>Personalizaciones compatibles para Common Data Service

Puede personalizar Common Data Service con las herramientas disponibles en el portal Power Apps o con aquellas que se describen en la documentación oficial. Estas personalizaciones están admitidas y se pueden actualizar.

Las personalizaciones realizadas con otros métodos que no sean los que aquí se describen no están admitidas y podrían causar problemas durante la instalación de actualizaciones y mejoras de Common Data Service. Consulte [Personalizaciones no admitidas](#unsupported-customizations) para obtener más información.

Los temas cubiertos en los artículos técnicos publicados en sitios de Microsoft como docs.microsoft.com, msdn.microsoft.com o technet.microsoft.com, son compatibles pero quizá no se actualicen.


## <a name="customizations-using-power-apps-portal"></a>Personalizaciones utilizando el portal de Power Apps

Hay una variedad de herramientas que se incluyen con Common Data Service que puede utilizar para personalizarlo. Las personalizaciones realizadas con las herramientas y la aplicación web del portal de Power Apps son completamente compatibles y se pueden actualizar por completo.

Se pueden usar los siguientes métodos de personalización para generar personalizaciones completamente compatibles:

- Personalización en el portal de Power Apps o la solución del explorador. Para obtener más información, consulte [¿Qué es Common Data Service?](../../maker/common-data-service/data-platform-intro.md).

- Configuración en la aplicación web. Para obtener más información, vea [Administrar Power Apps](../../administrator/admin-guide.md).

- Reporting Services. Para obtener más información, consulte [Agregar informes a la aplicación basada en modelos](/powerapps/maker/model-driven-apps/add-reporting-to-app).

> [!NOTE]
> Completamente compatible significa que el soporte técnico para programadores puede proporcionar ayuda para las personalizaciones y que el soporte técnico para aplicaciones puede ayudar a los clientes a ejecutar dichas modificaciones.

Para obtener más información sobre el uso de las herramientas de personalización en la aplicación web, consulte [Qué es Common Data Service](../../maker/common-data-service/data-platform-intro.md).


## <a name="customizations-applied-using-code"></a>Personalizaciones aplicadas con código

La documentación de este sitio para desarrolladores, artículos técnicos y código de ejemplo publicados en este sitio, y la información publicada por el equipo de soporte técnico para programadores de Common Data Service se incluyen en el área de personalización aplicada utilizando código. Las acciones y niveles específicos de compatibilidad y capacidad de actualización se describen más adelante en este tema.

### <a name="common-data-service-web-services"></a>Servicios web de Common Data Service

El uso de los servicios web es completamente compatible. Esto incluye: API web, servicio de organización, servicio de detección y servicio de datos de la organización. Nos esforzamos por mantener las API compatibles con versiones anteriores, pero nos reservamos el derecho de cambiar las API para las características adicionales. Los atributos de entidad también pueden cambiar en versiones futuras.

### <a name="solution-file"></a>Archivo de solución

Se admite la modificación del archivo de una solución no administrada como se describe en esta documentación. Algunas tareas de personalización para las aplicaciones basadas en modelos pueden realizarse con estos pasos:

1. Exportar un componente de la solución como una solución no administrada.
2. Extraer el contenido del paquete de solución.
3. Editar el archivo customizations.xml.
4. Volver a empaquetar el archivo de solución.
5. Importar la solución modificada.

> [!NOTE]
> Los cambios en el archivo `Customizations.xml` deben cumplir el esquema de `CustomizationsSolution.xsd`. Para obtener más información, consulte [Esquema de archivo de soluciones de personalización](customization-solutions-file-schema.md).

Las tareas admitidas siguientes pueden realizarse con este procedimiento:

- Personalización de la cinta de opciones.
- Personalización de la navegación de la aplicación con el mapa del sitio.
- Personalización del formulario y el panel con FormXml.
- Personalización de la consulta guardada.

### <a name="plug-ins"></a>Complementos

La capacidad para crear la lógica de negocios personalizada con el mecanismo de complemento que se describe en esta documentación es completamente compatible y se puede actualizar. Los complementos solo se pueden registrar y ejecutar en el espacio aislado (modo aislado). Más información: [Complementos](plug-ins.md)

### <a name="workflow-extensions"></a>Extensiones de flujo de trabajo

La capacidad para crear las actividades de flujo de trabajo personalizadas (ensamblados) que se llamarán desde las reglas de flujo de trabajo es completamente compatible y se puede actualizar. Las actividades de flujo de trabajo personalizadas solo se pueden registrar y ejecutar en el espacio aislado (modo aislado). Más información: [Extensiones de flujo de trabajo](workflow/workflow-extensions.md)

## <a name="support-for-net-framework-versions"></a>Compatibilidad con las versiones de .NET Framework

A continuación se describen las consideraciones sobre compatibilidad del código personalizado escrito con Microsoft .NET Framework 4.6.2..

- Cualquier cliente de servicio web creado con Microsoft .NET Framework 4.6.2. o posterior que llama a los servicios web es completamente compatible en Common Data Service.

    > [!IMPORTANT]
    > Debe crear cualquier aplicación de cliente personalizada usando Microsoft .NET Framework 4.6.2 o posterior. Solo podrán conectar las aplicaciones que utilizan Seguridad de capa de transporte (TLS) 1.2 o superior. TLS 1.2 no es el protocolo predeterminado usado por .NET Framework 4.5.2, pero está en .NET Framework 4.6.2.


- Se admiten todos los ensamblados .NET creados con Microsoft .NET Framework 4.6.2. para usar en Common Data Service como un ensamblado de complemento o como una actividad de flujo de trabajo personalizada.

## <a name="unsupported-customizations"></a>Personalizaciones no admitidas

Las modificaciones en Common Data Service que se realizan sin usar los métodos descritos en esta documentación o las herramientas Common Data Service no se admiten ni se mantienen durante la instalación de actualizaciones o mejoras de Common Data Service. No se admite nada que no esté reflejado en esta documentación y en los documentos relacionados. Además, las modificaciones no admitidas podrían provocar problemas cuando se actualice a través de la instalación de revisiones, los Service Pack o mejoras de Common Data Service. 

La siguiente es una lista de los tipos de acciones no admitidas por los que recibimos preguntas frecuentes:

- Hacer referencia a cualquier biblioteca de vínculos dinámicos (DLL) de Common Data Service que no sean las siguientes:

    - Microsoft.Crm.Outlook.Sdk.dll
    - Microsoft.Crm.Sdk.Proxy.dll
    - Microsoft.Xrm.Sdk.dll
    - Microsoft.Xrm.Sdk.Data.dll
    - Microsoft.Xrm.Sdk.Deployment.dll
    - Microsoft.Xrm.Sdk.Workflow.dll
    - Microsoft.Xrm.Tooling.Connector.dll
    - Microsoft.Xrm.Tooling.CrmConnectControl.dll
    - Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.dll
    - Microsoft.Xrm.Tooling.WebResourceUtility.dll

- El uso de interfaces de programación de aplicaciones (API) que no sean las API documentadas en los servicios web: API web, servicio de organización, servicio de implementación, servicio de detección y servicio de datos de la organización.

- Los ensamblados de Workflow y de complemento deben contener toda la lógica necesaria dentro del dll respectivo. Los complementos pueden hacer referencia a algunos ensamblados .Net principales. Sin embargo, no se admiten las dependencias de ensamblados .Net que interactúen con las APIs de Windows de bajo nivel, como la interfaz de diseño gráfico. Anteriormente, Dynamics 365 permitía que los ensamblados hicieran referencia a estas interfaces, pero para cumplir nuestros estándares de seguridad, son necesarios cambios en este funcionamiento.

- No se admite la creación de un ensamblado de complementos para un ensamblado de Common Data Service estándar (Microsoft.Crm.*.dll) ni realizar una actualización o eliminar un `pluginassembly` creado en una plataforma.

- No se admite la edición de un archivo de solución para editar cualquiera de los componentes de la solución que no sean las cintas de opciones, los formularios, el mapa del sitio o las consultas guardadas. Para obtener más información, consulte [Cuándo editar personalizaciones](when-edit-customization-file.md). No se admite la definición de nuevos componentes de la solución mediante la edición del archivo de solución. No se admite la edición de los archivos de recursos web exportados con una solución. Excepto por los pasos que se documentan en [Mantener soluciones administradas](maintain-managed-solutions.md), no se admite la edición del contenido de una solución administrada.

### <a name="outlook-client"></a>Cliente de Outlook
- Las modificaciones a cualquiera de los formularios de Dynamics 365 o agregar nuevos formularios, como páginas .aspx personalizadas, directamente en Office Outlook o realizar cambios en archivos .pst. Estos cambios no se actualizarán.
- Crear personalizaciones mediante cualquier medios distintos de las herramientas compatibles.

### <a name="see-also"></a>Vea también

[Personalizaciones compatibles para aplicaciones basadas en modelos](../model-driven-apps/supported-customizations.md)




