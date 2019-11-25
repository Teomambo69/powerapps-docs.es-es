---
title: Solución de problemas de Power Query | Microsoft Docs
description: Puede resolver problemas usando Power Query para crear una entidad personalizada en Common Data Service.
author: mllopis
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 05/16/2018
ms.author: millopis
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5679d82d6ec53d579567a778043ac9542099a20e
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2706699"
---
# <a name="troubleshoot-power-query"></a>Solución de problemas de Power Query
Cuando usa Power Query for Excel para crear una entidad personalizada que contiene datos de orígenes externos, podría aparecer este error:

>“El administrador de Azure Active Directory ha establecido una política que le impide usar esta función. Póngase en contacto con al administrador, que puede conceder los permisos para esta función en su nombre”.

El error se produce si Power Query no puede acceder a los datos de la organización en PowerApps o Common Data Service. Esta situación surge bajo dos grupos de circunstancias:

* Un administrador de inquilinos de Azure Active Directory (Azure AD) ha deshabilitado la capacidad de los usuarios de consentir aplicaciones que acceden a datos de la compañía en su nombre.
* Uso de un inquilino de Active Directory no administrado. Un inquilino no administrado es un directorio sin un administrador global que se creó para completar una oferta de suscripción de autoservicio. Para corregir este escenario, los usuarios primero deben realizar la conversión a un inquilino administrado y después seguir una de las dos soluciones a este problema. Las soluciones se describen en la siguiente sección.

Para resolver este problema, el administrador de Azure Active Directory debe seguir cualquiera de los procedimientos que se presentan más adelante en este artículo.

## <a name="allow-users-to-consent-to-apps-that-access-company-data"></a>Permitir a los usuarios consentir aplicaciones que acceden a datos de la compañía
Este método es quizás más sencillo que el siguiente, pero permite permisos más amplios.

1. En el [portal de Azure](https://portal.azure.com), abra el panel **Azure Active Directory** y, a continuación, seleccione **Configuración de usuario**.
2. Junto a **Los usuarios pueden consentir aplicaciones que acceden a datos empresariales en su nombre**, seleccione **Sí** y, a continuación, seleccione **Guardar**.

## <a name="allow-power-query-to-access-company-data"></a>Permitir a Power Query acceder a datos de la compañía
Como alternativa, el administrador de inquilinos puede dar consentimiento a Power Query sin modificar los permisos de los inquilinos.

1. Instale [Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-azurerm-ps).
2. Ejecute los siguientes comandos de PowerShell:
   * Login-AzureRmAccount (e inicie sesión como el administrador de inquilinos)
   * New-AzureRmADServicePrincipal -ApplicationId f3b07414-6bf4-46e6-b63f-56941f3f4128

La ventaja de este método (respecto a la solución de inquilinos) es que esta solución está muy dirigida. Proporciona solo el servicio principal de **Power Query** y no se realiza ningún otro cambio en el inquilino.

## <a name="update-personal-data"></a>Actualizar datos personales

Los usuarios pueden actualizar los mashups y otra información (como nombres de consulta y metadatos de mashup) a través del editor de consultas y a través del cuadro **Opciones** al que se puede acceder desde el editor de consultas.

En PowerApps, puede acceder al editor de consultas mediante el procedimiento siguiente:
1. Vaya al panel **Datos**, expándalo y, a continuación, seleccione **Entidades**. 
2. Seleccione los puntos suspensivos (...) y, a continuación, seleccione **Editar consultas**.
3. En la cinta de opciones, seleccione el botón **Opciones** y después seleccione el botón **Diagnóstico de exportación**.


## <a name="delete-personal-data"></a>Eliminar datos personales

La mayoría de los datos se elimina automáticamente en 30 días. Para los datos y metadatos alrededor de los mashups, los usuarios deben quitar todos los mashups con PowerApps. Todos los datos y metadatos asociados se eliminarán en 30 días.

Para quitar mashups de Power Apps:
1. Quite los proyectos del integrador de datos, que se pueden quitar desde la ficha homónima.
2. Seleccione los puntos suspensivos (...) y después seleccione la opción **Eliminar**.

Si ha creado un mashup a través de la función "Nuevas entidades desde datos (vista previa técnica)", puede quitarlo mediante el procedimiento siguiente:
1. Seleccione los puntos suspensivos (...) y, a continuación, seleccione **Editar consultas**.
2. En la cinta de opciones, seleccione el botón **Opciones**.
3. Seleccione el botón **Quitar todas las consultas**.  
    Tras confirmar que desea eliminar las consultas, estas se eliminarán.

## <a name="export-personal-data"></a>Exportar datos personales

Para exportar datos personales, los usuarios pueden hacer lo siguiente:
1. Abrir el editor de consultas.
2. En la cinta de opciones, seleccione el botón **Opciones**.
3. Seleccionar el botón **Diagnóstico de exportación**.

En PowerApps, puede acceder al editor de consultas mediante el procedimiento siguiente:
1. Vaya al panel **Datos**, expándalo y, a continuación, seleccione **Entidades**.
2. Seleccione los puntos suspensivos (...) y, a continuación, seleccione **Editar consultas**. 
3. En la cinta de opciones, seleccione el botón **Opciones** y después seleccione el botón **Diagnóstico de exportación**.

Se puede acceder a los registros generados por el sistema sobre acciones del usuario en la interfaz de usuario (IU) en el portal de Azure.



