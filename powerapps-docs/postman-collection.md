---
title: "Descripción de un conector personalizado con Postman | Microsoft Docs"
description: "Crear una colección Postman para registrar conectores personalizados"
services: 
suite: powerapps
documentationcenter: 
author: archnair
manager: anneta
editor: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 04/28/2017
ms.author: archanan
ms.openlocfilehash: fd060ff873ee376b7ca886f721d360372c1d13ed
ms.sourcegitcommit: 68eee592c351688e5d0bd458f33a70be507fa53f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/30/2018
---
# <a name="describe-a-custom-connector-with-postman"></a>Describir un conector personalizado con Postman
[Postman](https://www.getpostman.com/) es una herramienta que agiliza y facilita el desarrollo de API. En este tutorial se muestra cómo crear una colección Postman, que puede usar para crear fácilmente [conectores personalizados](register-custom-api.md) en PowerApps.

## <a name="prerequisites"></a>Requisitos previos
* Instale la [aplicación Postman](https://www.getpostman.com/apps).

## <a name="create-a-postman-collection"></a>Crear una colección Postman
Se va a crear una colección Postman para [Text Analytics API](https://www.microsoft.com/cognitive-services/en-us/text-analytics-api) de Azure Cognitive Services. Esta API identifica el idioma, la opinión y las frases clave de un texto que se le pasa.

1. El primer paso para crear una colección Postman es crear una solicitud. Cuando cree la solicitud, puede establecer el verbo HTTP, la dirección URL de la solicitud, los parámetros de consulta o ruta de acceso, los encabezados y el cuerpo. Para más información, consulte [Sending Requests](https://www.getpostman.com/docs/requests) (Enviar solicitudes) en la documentación de Postman. Para el punto de conexión de API de detección de idioma, establezca los valores como se indica a continuación:
   
    ![Solicitud de Postman](./media/postman-collection/request.png)
   
    Detalles de los parámetros y valores utilizados:
   
   | Parámetro | Valor |
   | --- | --- |
   | Verb (Verbo) |POST |
   | Request URL (Dirección URL de solicitud) |https://westus.api.cognitive.microsoft.com/text/analytics/v2.0/languages |
   | Params (Parámetros) |numberOfLanguagesToDetect |
   | Autorización |"No Auth" (Sin autorización) |
   | Headers (Encabezados) |Ocp-Apim-Subscription-Key = <your subscription key> <br/>Content-Type = application/json |
   | Body (Cuerpo) |<code>{<br/>&nbsp;&nbsp;&nbsp;"documents": [<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"id": "1",<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"text": "Hello World"<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}<br/>&nbsp;&nbsp;]<br/>}<code> |
2. Haga clic en **Send** (Enviar) para realizar la solicitud y obtener la respuesta.
3. Haga clic en **Save** (Guardar) para guardar la solicitud en una colección Postman.
   
    ![Respuesta de Postman](./media/postman-collection/request-response-save.png)
4. Proporcione valores para **Request name** (Nombre de la solicitud) y **Request description** (Descripción de la solicitud) en el cuadro de diálogo **Save Request** (Guardar solicitud). Usará estos valores en el conector personalizado.
   
    ![Guardar colección en Postman](./media/postman-collection/save-request-note.png)
   
    También puede guardar la respuesta a la solicitud. Actualmente, los conectores personalizados solo admiten una respuesta para cada solicitud. Si guarda varias respuestas para cada solicitud, se usa solo la primera.
   
    ![Guardar respuesta en Postman](./media/postman-collection/save-response.png)
5. Siga creando la colección Postman creando y guardando otras solicitudes y respuestas.
6. Una vez que haya terminado de crear la colección Postman para todas las solicitudes y respuestas, expórtela.
   
    ![Exportar en Postman](./media/postman-collection/export.png)
7. Elija **Collection v1** (Colección v1) como formato de exportación.
   
    ![Exportar en Postman](./media/postman-collection/export2.png)

Ahora puede usar esta colección Postman para crear un conector personalizado en PowerApps. Para más información, consulte [Registrar y usar conectores personalizados en PowerApps](register-custom-api.md). 

