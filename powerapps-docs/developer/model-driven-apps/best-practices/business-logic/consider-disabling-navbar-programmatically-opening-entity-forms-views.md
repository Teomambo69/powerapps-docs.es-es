---
title: Considere deshabilitar NavBar mediante programación abriendo formularios de entidad o vistas | MicrosoftDocs
description: 'Al abrir formularios o vistas de entidad con una dirección URL, podría producirse un rendimiento más lento de los clientes en redes de alta latencia cuando se habilita la barra de navegación (NavBar).'
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
ms.date: 3/04/2019
ms.author: jowells
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="consider-disabling-navbar-when-programmatically-opening-entity-forms-or-views"></a>Considere deshabilitar NavBar mediante programación abriendo formularios de entidad o vistas

**Categoría**: diseño, rendimiento

**Potencial de impacto**: medio

<a name='symptoms'></a>

## <a name="symptoms"></a>Síntomas

Al abrir formularios o vistas de entidad con una dirección URL, podría producirse un rendimiento más lento de los clientes en redes de alta latencia cuando se habilita la barra de navegación (NavBar).

<a name='guidance'></a>

## <a name="guidance"></a>Instrucciones

Establezca si los usuarios necestian tener la barra de navegación completa cuando crean personalizaciones que abren formularios o vistas de entidad a través de una dirección URL. En la mayoría de los casos, los usuarios hacen clic en un vínculo para abrir un formulario de entidad, realizan trabajo rápido y, a continuación cierran el registro.  Al deshabilitar la barra de navegación se reducirá la cantidad de recursos que se deben cargar, lo que reducirá el número de solicitudes de red que se realizan.  

Para generar direcciones URL para abrir formularios o vistas de entidad, implemente `navbar=off` en los parámetros de cadena de consulta para la página `main.aspx`. El ejemplo siguiente abre un formulario de entidad de Cuenta con la barra de navegación deshabilitada.

```JavaScript
function disableNavBar() {
    var globalContext = Xrm.Utility.getGlobalContext();
    return globalContext.getClientUrl() + "/main.aspx?appid=9411ee28-4310-e811-a839-000d3a33a7cb&etc=1&id={00000000-0000-0000-00AA-000010001004}&pagetype=entityrecord&navbar=off";
}
```

> [!IMPORTANT]
> El parámetro de cadena de consulta navbar=off sólo está disponible con la página `main.aspx`. 

<a name='problem'></a>

## <a name="problematic-patterns"></a>Patrones problemáticos

> [!WARNING] 
> Estos escenarios deben evitarse. 

Mantener la barra de navegación (NavBar) habilitada no significa que los usuarios tendrán problemas de rendimiento. Sin embargo, significa que deben cargarse recursos adicionales en el formulario o la vista de entidad, lo que requiere solicitudes adicionales de red.  Se ha observado en redes muy latentes que esto puede llevar a una experiencia pobre de usuario.

Un ejemplo de una dirección URL creada con NavBar habilitado es el siguiente

```JavaScript
function enabledNavBar() {
    var globalContext = Xrm.Utility.getGlobalContext();
    // By default, NavBar is set to true if you do not include the parameter in the query string:
    return globalContext.getClientUrl() + "/main.aspx?appid=9411ee28-4310-e811-a839-000d3a33a7cb&etc=1&id={00000000-0000-0000-00AA-000010001004}&pagetype=entityrecord";
}

function enabledNavBarExplicit() {
    var globalContext = Xrm.Utility.getGlobalContext();
    // Explicitly defining that the NavBar will be enabled
    return globalContext.getClientUrl() + "/main.aspx?appid=9411ee28-4310-e811-a839-000d3a33a7cb&etc=1&id={00000000-0000-0000-00AA-000010001004}&pagetype=entityrecord&navbar=on";
}
```

<a name='additional'></a>

## <a name="additional-information"></a>Información adicional

Al abrir otros registros desde aplicaciones basadas en modelos, la barra de navegación se está cargando con las áreas y subáreas definidas en el mapa del sitio.  Además, también genera el [Iniciador de aplicaciones de Office](https://support.office.com/article/Meet-the-Office-365-app-launcher-79f12104-6fed-442f-96a0-eb089a3f476a) que muestra las aplicaciones de Office 365 a las que el usuario tiene acceso.<br/>
![Comparación de NavBar habilitado y deshabilitado](../media/navbar_comparison_enabled_disabled.png)

<a name='seealso'></a>

### <a name="see-also"></a>Vea también

[Abrir formularios, vistas, diálogos e informes con una dirección URL](../../open-forms-views-dialogs-reports-url.md)
