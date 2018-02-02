---
title: Desarrollo de un conector de API | Microsoft Docs
description: "Describa la API, especifique el tipo de autenticación, cree desencadenadores y acciones, y realice pruebas."
services: 
suite: powerapps
documentationcenter: na
author: asavaritayal
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/06/2017
ms.author: astay
ms.openlocfilehash: 68a0be6c6be91ff5b89b3e06aecc242f987a4cf4
ms.sourcegitcommit: 68eee592c351688e5d0bd458f33a70be507fa53f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/30/2018
---
# <a name="develop-an-api-connector-powerapps"></a>Desarrollar un conector de API (PowerApps)
La creación de un conector consta de varios pasos. Para empezar, en [PowerApps](https://web.powerapps.com/), pulse o haga clic en el botón **Configuración** (el icono de engranaje) en la parte superior derecha de la página. A continuación, pulse o haga clic en **Custom Connectors** (Conectores personalizados).

![Buscar conectores de API](./media/api-connectors-dev/finding-custom-apis.png)

## <a name="describe-your-api"></a>Describir la API
Los conectores de API se describen mediante el [estándar OpenAPI](https://swagger.io/) para definir la interfaz de una API de HTTP. Puede comenzar a crearla con un archivo de OpenAPI existente o puede importar una [colección Postman](https://www.getpostman.com/docs/collections), que genera automáticamente el archivo de OpenAPI. 

![Definir el diagrama de API](./media/api-connectors-dev/build-your-api-updated.png)

Si parte de cualquiera de estas descripciones de API, los campos de metadatos en el asistente se rellenan automáticamente. Puede editarlos en cualquier momento.  

## <a name="build-security"></a>Crear la seguridad
Elija el tipo de autenticación admitido por su servicio y proporcione más detalles para permitir que la identidad fluya de la forma adecuada entre su servicio y los clientes. 

![Diagrama de seguridad](./media/api-connectors-dev/security.png)

[Aprenda más](register-custom-api.md) sobre la seguridad de conectores.

## <a name="build-triggers-and-actions"></a>Crear desencadenadores y acciones
1. Para crear los desencadenadores y las acciones para el conector, cambie a la pestaña **Definición**. 
   
    ![Diagrama de definición](./media/api-connectors-dev/definition.png)
2. Con el asistente, puede agregar nuevas operaciones o editar el esquema y la respuesta para las existentes. Las propiedades **General** de cada operación le permiten controlar la experiencia del usuario final para el conector. Aprenda más sobre los diferentes tipos de operaciones mediante los vínculos siguientes:
   
   * [Desencadenadores](https://flow.microsoft.com/documentation/customapi-webhooks) (no visibles en PowerApps)
   * [Acciones](register-custom-api.md)
     
     Para implementar funcionalidad avanzada para Microsoft Flow, consulte [Extensiones de OpenAPI para conectores de API](https://flow.microsoft.com/documentation/customapi-how-to-swagger/). 
3. Por último, pulse o haga clic en **Crear conector** para registrar el conector de API.

Para características adicionales no disponibles en el asistente, póngase en contacto con [condevhelp@microsoft.com](mailto:condevhelp@microsoft.com).

## <a name="test-the-connector"></a>Probar el conector
Antes de enviarlo, pruebe el conector de API de una o varias maneras: 

* Mediante el [asistente para pruebas](https://flow.microsoft.com/blog/new-updates-custom-api/) del conector de API, puede llamar a cada operación para comprobar la funcionalidad y el esquema de respuesta.
* En el diseñador para Microsoft Flow, puede crear visualmente flujos mediante el conector de API. Este método de prueba permite observar la funcionalidad de la interfaz de usuario y las características de su conector.
* En PowerApps Studio, puede llamar a cada operación mediante la barra de fórmulas y enlazar la respuesta a los controles de la pantalla.

Este tema proporciona información general; para ampliarla, consulte [Registrar y usar un conector personalizado](register-custom-api.md).

