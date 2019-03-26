---
title: Autenticación con las aplicaciones de .NET Framework (Common Data Service para aplicaciones) | Microsoft Docs
description: Cómo las aplicaciones de .NET Framework se pueden autenticar en Common Data Service para aplicaciones
ms.custom: ''
ms.date: 01/25/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: paulliew
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="authentication-with-net-framework-applications"></a>Autenticación con las aplicaciones de .NET Framework

Si usa .NET Framework puede usar clases en el espacio de nombre [Xrm.Tooling](/dotnet/api/?view=dynamics-xrmtooling-ce-9) para autenticarse y para conectarse al servicio de la organización y a la Api web.

Con las clases `Xrm.Tooling` puede usar los ensamblados de SDK que usen los métodos de interfaz <xref:Microsoft.Xrm.Sdk.IOrganizationService>. Este es el mismo estilo de programación que usan los complementos y las actividades de flujo de trabajo, convirtiéndolo en un estilo que puede usar por todas partes para las aplicaciones de .NET Framework.

Con las clases `Xrm.Tooling` use la clase <xref:Microsoft.Xrm.Tooling.Connector>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient> .

> [!NOTE]
> Puede encontrar un código o ejemplos más antiguos usando el <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy> de bajo nivel o las clases <xref:Microsoft.Xrm.Sdk.WebServiceClient.OrganizationWebProxyClient>. Estos siguen estando admitidos y no están obsoletos, pero le recomendamos usar <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient> para las nuevas aplicaciones cliente de .NET Framework.

Las clases `Xrm.Tooling` proporcionan varios beneficios que incluyen:
- Puede definir la información de conexión con una cadena de conexión.
- Admite la autenticación basada en notificaciones de OAuth y Office 365.
- Seguridad de subprocesos para las acciones realizadas en un entorno multiprocesos. 
- Un control de inicio de sesión común de Windows Presentation Foundation (WPF) para tener una experiencia de inicio de sesión coherente desde las aplicaciones cliente de Windows.
- Es compatible con almacenamiento seguro de credenciales de inicio de sesión y reutiliza las credenciales almacenadas para iniciar sesión automáticamente después del inicio de sesión inicial.
- Informes integrados de seguimiento de diagnósticos y de rendimiento de las acciones realizadas, que puede configurar según los requisitos de la organización.
- Soporte para la autenticación del certificado X.509.

Las clases `Xrm.Tooling` se optimizar para usar los métodos de interfaz <xref:Microsoft.Xrm.Sdk.IOrganizationService>. 

Si desea usar la API web, puede usar el método  <xref:Microsoft.Xrm.Tooling.Connector><xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.ExecuteCrmWebRequest*> para componer solicitudes mediante API web con el resto de las ventajas proporcionadas con las clases `Xrm.Tooling` siempre y cuando use OAuth.

Más información: [Crear aplicaciones cliente de Windows mediante las herramientas XRM](xrm-tooling/build-windows-client-applications-xrm-tools.md)


## <a name="net-framework-versions"></a>Versiones de .NET Framework

Use la versión 4.6.2 de .NET Framework o superior al crear aplicaciones cliente. Solo las aplicaciones que usan la seguridad de nivel de transporte (TLS) 1.2 o una mejor seguridad pueden conectarse. TLS 1.2 no es el protocolo predeterminado usado por .NET Framework 4.5.2, pero está en .NET Framework 4.6.2.

> [!NOTE]
> **Problema conocido con Visual Studio 2015**
> 
> Cuando se ejecuta el proyecto/solución en VS 2015 en modo de depuración, es posible que no pueda conectarse. Esto ocurre independientemente de si está usando un marco de destino de 4.6.2 o más alto. Esto puede producirse porque el proceso de hospedaje de Visual Studio se compila con .NET 4.5, lo que significa de forma predeterminada que no es compatible con TLS 1.2. Puede deshabilitar el proceso de hospedaje de Visual Studio como solución. 
>
> Haga clic con el botón derecho del mouse en el nombre del proyecto en Visual Studio y luego haga clic en **Propiedades**. En la pestaña **Depuración** puede desactivar la opción **Habilitar proceso de hospedaje de Visual Studio**. 
>
> Esto afecta solo a la experiencia de depuración en VS 2015. Esto no afecta a los archivos binarios o ejecutables que se crean. El mismo problema no se produce en Visual Studio 2017.

## <a name="net-framework-applications-without-sdk-assemblies"></a>Aplicaciones de .NET Framework sin ensamblados de SDK

Si prefiere no tener una dependencia en ningún ensamblado de SDK, puede usar también los patrones descritos en [Usar OAuth con Common Data Service para aplicaciones](authenticate-oauth.md) sin aceptar ninguna dependencia de cualquier montaje del SDK. Sin los ensamblados de SDK, puede usar solo los servicios web de OData Restful (API web y servicio de detección global de OData). Los [Ejemplos de las operaciones de datos de API web (C#)](webapi/web-api-samples-csharp.md) demuestran este método.

### <a name="see-also"></a>Vea también

[Autenticación con servicios web Common Data Service para aplicaciones](authentication.md)<br />
[Usar OAuth con Common Data Service para aplicaciones](authenticate-oauth.md)

