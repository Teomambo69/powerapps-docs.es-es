---
title: Registro y uso de conectores personalizados | Microsoft Docs
description: Registre y use conectores personalizados en PowerApps con OpenAPI y Postman.
services: 
suite: powerapps
documentationcenter: 
author: mgblythe
manager: anneta
editor: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/05/2017
ms.author: mblythe
ms.openlocfilehash: 80f56a849dca7488f5b38908a7ec87b3a0916187
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="register-and-use-custom-connectors-in-powerapps"></a>Registrar y usar conectores personalizados en PowerApps
PowerApps permite crear aplicaciones completas sin ningún código de aplicación tradicional. En algunos casos, necesitará ampliar las funcionalidades de PowerApps, y los servicios web son la solución natural para esto. La aplicación puede conectarse a un servicio, realizar operaciones y recuperar datos. Si tiene un servicio web al que desea conectarse con PowerApps, debe registrar el servicio como un conector personalizado. Este proceso permite a PowerApps comprender las características de su API web, incluida la autenticación que requiere, las operaciones que admite, y los parámetros y las salidas de cada una de esas operaciones.

En este tema, veremos los pasos necesarios para registrar y utilizar un conector personalizado, y vamos a usar [Text Analytics API](https://www.microsoft.com/cognitive-services/en-us/text-analytics-api) de Azure Cognitive Services como ejemplo. Esta API identifica el idioma, la opinión y las frases clave de un texto que se le pasa. La siguiente imagen muestra la interacción entre el servicio, el conector personalizado que se crea a partir de él y la aplicación que llama a la API.

![API, conector personalizado y aplicación](./media/register-custom-api/intro-graphic.png)

## <a name="prerequisites"></a>Requisitos previos
* Una [cuenta de PowerApps](https://powerapps.microsoft.com).
* Un archivo de OpenAPI en formato JSON, una dirección URL a una definición de OpenAPI o una colección Postman para la API. Si no tiene nada de esto, le proporcionaremos instrucciones.
* Una imagen para usar como icono del conector personalizado (opcional).

## <a name="steps-in-the-custom-connector-process"></a>Pasos del proceso de conector personalizado
El proceso de conector personalizado tiene varios pasos, que se describen brevemente a continuación. En este artículo se da por supuesto que ya tiene una API de REST con algún tipo de acceso autenticado, por lo que nos centraremos en los pasos 3 a 6 del resto del artículo. Para obtener un ejemplo de los pasos 1 y 2, consulte [Crear una API web personalizada para PowerApps](customapi-web-api-tutorial.md).

1. **Cree una API de RESTful** en el lenguaje y la plataforma que elija. Para las tecnologías de Microsoft, se recomienda uno de los siguientes.
   
   * Azure Functions
   * Azure Web Apps
   * Azure API Apps
2. **Proteja su API** con uno de los siguientes mecanismos de autenticación. Puede permitir el acceso no autenticado a las API, pero no es aconsejable.
   
   * Azure Active Directory. Para más información, consulte [Uso de Azure Active Directory con un conector personalizado en PowerApps](customapi-azure-resource-manager-tutorial.md).
   * OAuth 2.0 para servicios específicos como Dropbox, Facebook y SalesForce.
   * OAuth 2.0 genérico
   * Clave de API
   * Autenticación básica
3. **Describa la API** de una de las dos maneras estándar del sector, para que PowerApps pueda conectarse a ella.
   
   * Un archivo de OpenAPI (también conocido como un archivo Swagger)
   * Una colección Postman
     
     También puede crear un archivo OpenAPI en el paso 4 como parte del proceso de registro.
4. **Registre el conector personalizado** con un asistente en PowerApps, donde se especifican la descripción de la API, los detalles de seguridad y otra información.
5. **Use el conector personalizado** en una aplicación. Cree una conexión a la API de la aplicación y llame a las operaciones que proporciona la API, igual que llama a las funciones nativas de PowerApps.
6. **Comparta el conector personalizado** igual que hace con otras conexiones de datos en PowerApps. Este paso es opcional, pero suele tener sentido compartir conectores personalizados entre varios creadores de aplicaciones.

## <a name="describe-your-api"></a>Describir la API
Suponiendo que tiene una API con algún tipo de acceso autenticado, necesita una manera de describir la API para que PowerApps puedan conectarse a ella. Para ello, cree un archivo de OpenAPI o una colección Postman, lo que puede hacer desde *cualquier* punto de conexión de API de REST, entre otros:

* API disponibles públicamente. Estos son algunos ejemplos: [Spotify](https://developer.spotify.com/), [Uber](https://developer.uber.com/), [Slack](https://api.slack.com/), [Rackspace](http://docs.rackspace.com/), entre otros.
* Una API que se crea e implementa en cualquier proveedor de hospedaje en la nube, entre ellos Azure, Amazon Web Services (AWS), Heroku, Google Cloud, etc.
* Una API de línea de negocio personalizada implementada en la red, siempre que la API esté expuesta en Internet pública.

Los archivos de OpenAPI y las colecciones Postman utilizan distintos formatos, pero ambos son documentos legibles en máquina independientes del lenguaje que describen las operaciones y los parámetros de la API:

* Puede generar estos documentos con diversas herramientas según el lenguaje y la plataforma en los que se basa su API. Consulte la [documentación de Text Analytics API](https://westus.dev.cognitive.microsoft.com/docs/services/TextAnalytics.V2.0/export?DocumentFormat=Swagger&ApiName=Azure) para ver un ejemplo de un archivo de OpenAPI.
* Si aún no tiene un archivo de OpenAPI para su API y no desea crear uno, puede crear fácilmente un conector personalizado con una colección Postman. Consulte cómo [crear una colección Postman](postman-collection.md) para más información.
* En última instancia, PowerApps usa OpenAPI, por lo que la colección Postman se analiza y se traduce en un archivo de definición de OpenAPI.

**Nota**: el tamaño del archivo debe ser inferior a 1 MB.

### <a name="getting-started-with-openapi-and-postman"></a>Introducción a OpenAPI y Postman
* Si está familiarizado con OpenAPI, consulte [Getting Started with OpenAPI](http://swagger.io/getting-started/) (Introducción a OpenAPI) en el sitio swagger.io.
* Si no está familiarizado con Postman, instale la [aplicación Postman](https://www.getpostman.com/apps) desde su sitio.
* Si su API se ha creado con Azure App Service o Azure Functions, consulte [Exportación de una API hospedada en Azure a PowerApps y Microsoft Flow](https://docs.microsoft.com/azure/app-service/app-service-export-api-to-powerapps-and-flow) para más información.

## <a name="register-your-custom-connector"></a>Registrar el conector personalizado
Ahora, usará el archivo de OpenAPI o la colección Postman para registrar el conector personalizado en PowerApps.

1. En [powerapps.com](https://web.powerapps.com), en el menú de la izquierda, seleccione **Conexiones**. Seleccione los puntos suspensivos (**...** ) y **Manage custom connectors** (Administrar conectores personalizados) en la esquina superior derecha.
   
     **Sugerencia**: Si no encuentra dónde se administran los conectores personalizados en el explorador para dispositivos móviles, podría estar en un menú en la esquina superior izquierda.
   
    ![Create custom connector (Crear conector personalizado)](./media/register-custom-api/managecustomapi.png)  
2. Seleccione **Create custom connector** (Crear conector personalizado).
   
    ![Propiedades del conector personalizado](./media/register-custom-api/newcustomapi.png)
3. En la pestaña **General**, elija cómo desea crear el conector personalizado.
   
   * Upload an OpenAPI file (Cargar un archivo de OpenAPI)
   * Use una dirección URL OpenAPI (Usar una dirección URL de OpenAPI)
   * Upload Postman Collection V1 (Cargar una colección Postman V1)
     
     ![Cómo crear un conector personalizado](./media/register-custom-api/choosehowtocreate.png)
     
     Cargue un icono para el conector personalizado. Los campos de descripción, host y dirección URL base normalmente se rellenan automáticamente con la información del archivo de OpenAPI. Si no se rellenan automáticamente, puede agregar la información a esos campos. Seleccione **Continue** (Continuar).
4. Especifique las propiedades de la autenticación en la pestaña **Security** (Seguridad).
   
    ![Tipo de autenticación](./media/register-custom-api/authenticationtypes.png)
   
   * El tipo de autenticación se rellena automáticamente según lo definido en el objeto de OpenAPI `securityDefinitions`. El siguiente es un ejemplo de OAuth2.0.
     
       ```
       "securityDefinitions": {
           "AAD": {
           "type": "oauth2",
           "flow": "accessCode",
           "authorizationUrl": "https://login.windows.net/common/oauth2/authorize",
           "scopes": {}
           }
       },
       ```
   * Si el archivo de OpenAPI no usa el objeto `securityDefintions`, no se necesitan valores adicionales.
   * Cuando se utiliza una colección Postman, el tipo de autenticación se rellena automáticamente solo cuando se usan tipos de autenticación admitidos, por ejemplo, OAuth 2.0 o básica.
   * Para obtener un ejemplo de cómo configurar la autenticación de Azure Active Directory (AAD), consulte [Crear una API web personalizada para PowerApps](customapi-web-api-tutorial.md#set-up-azure-active-directory-authentication).
5. En la pestaña **Definiciones**, todas las operaciones definidas en el archivo de OpenAPI o en la colección Postman, además de los valores de solicitud y respuesta, se rellenan automáticamente. Si se han definido todas las operaciones necesarias, puede ir al paso 6 del proceso de registro sin realizar cambios en esta pantalla.
   
    ![Pestaña Definición](./media/register-custom-api/definitiontab.png)
   
    Si desea editar acciones existentes o agregar nuevas acciones al conector personalizado, siga leyendo.
   
   1. Si desea agregar una nueva acción que no se encontraba en el archivo de OpenAPI o en la colección Postman, seleccione **New action** (Nueva acción) en el panel izquierdo y rellene la sección **General** con el nombre, la descripción y la visibilidad de la operación.
   2. En la sección **Request** (Solicitar), seleccione **Import from sample** (Importar del ejemplo) en la parte superior derecha. En el formulario de la derecha, pegue los datos en una solicitud de ejemplo. Normalmente hay solicitudes de ejemplo en la documentación de la API, donde puede obtener información para rellenar los campos **Verbo**, **URL de solicitud**, **Encabezados** y **Cuerpo**. Consulte la [documentación de Text Analytics API](https://westus.dev.cognitive.microsoft.com/docs/services/TextAnalytics.V2.0/operations/56f30ceeeda5650db055a3c6) para ver un ejemplo.
      
       ![Importar del ejemplo](./media/register-custom-api/importfromsample.png)
   3. Seleccione **Importar** para completar la definición de la solicitud. Defina la respuesta de una manera similar.
6. Una vez que tenga todas las operaciones definidas, seleccione **Crear** para crear el conector personalizado.
7. Después de crear el conector personalizado, vaya a la pestaña **Probar** para probar las operaciones definidas en la API. Elija una conexión y especifique los parámetros de entrada para probar una operación.
   
    ![Probar un conector personalizado](./media/register-custom-api/testcustomapi.png)
   
    Si la llamada se realiza correctamente, obtendrá una respuesta válida.
   
    ![Probar la respuesta de la API](./media/register-custom-api/testapiresponse.png)

## <a name="use-your-custom-connector"></a>Usar el conector personalizado
Ahora que ha registrado su API, agregue el conector personalizado a la aplicación igual que haría con cualquier otro origen de datos. Analizaremos un breve ejemplo. Para más información acerca de las conexiones de datos, consulte [Agregar una conexión de datos en PowerApps](add-data-connection.md).

1. En PowerApps Studio, en el panel de la derecha, pulse o haga clic en **Agregar origen de datos**.
   
    ![](./media/register-custom-api/data-source.png)
2. Pulse o haga clic en el conector personalizado que ha creado.
   
    ![](./media/register-custom-api/connector.png)
3. Complete los pasos necesarios para iniciar sesión en el servicio al que se está conectando. Si la API usa la autenticación OAuth, es posible que aparezca una pantalla de inicio de sesión. Para la autenticación con clave de API, se le podría solicitar el valor de la clave.
4. Llame a la API en su aplicación. En nuestro ejemplo, hemos creado una aplicación que envía texto a Cognitive Services y devuelve una puntuación de opinión de 0 a 1, que se muestra en la aplicación como un porcentaje.
   
   * Con este conector, si comienza a escribir "Az" en la barra de fórmulas, verá la API y las operaciones que están disponibles.
     
       ![](./media/register-custom-api/formula.png)
   * La llamada completa tiene el siguiente aspecto; pasamos el texto del control `TextInput` y obtenemos una puntuación para mostrar en la aplicación:
     
       ```
       'AzureMachineLearning-TextAnalytics'.Sentiment({documents:Table({language:"en",id:"1",text:TextInput.Text})}).documents.score)
       ```
   * Elaboramos un poco más la aplicación para controlar los datos que se devuelven, pero no es demasiado complicado.

La aplicación finalizada es similar a la de la imagen siguiente. Es una aplicación sencilla, pero cuenta con una funcionalidad eficaz porque puede llamar a Cognitive Services a través de un conector personalizado.

![](./media/register-custom-api/finished-app.png)

### <a name="quota-and-throttling"></a>Cuota y limitación
* Consulte la página de [precios de PowerApps](https://powerapps.microsoft.com/pricing/) para más información acerca de las cuotas de la creación de conectores personalizados. Los conectores personalizados que se compartan con usted no cuentan en esta cuota.
* Para cada conexión que se crea en un conector personalizado, los usuarios pueden realizar hasta 500 solicitudes por minuto.

## <a name="share-your-custom-connector"></a>Compartir el conector personalizado
Ahora que tiene un conector personalizado, puede compartirlo con otros usuarios de su organización. Recuerde que, cuando se comparte una API, otros usuarios pueden empezar a depender de ella y, si elimina un conector personalizado, se eliminan todas las conexiones a la API. Si desea proporcionar un conector para usuarios ajenos a su organización, consulte [Información general de la certificación de conectores personalizados en PowerApps](api-connector-overview.md).

1. En [powerapps.com](https://web.powerapps.com), en el menú de la izquierda, seleccione **Conexiones**. Seleccione los puntos suspensivos (**...** ) y **Manage custom connectors** (Administrar conectores personalizados) en la esquina superior derecha.
   
    ![Nueva conexión](./media/register-custom-api/managecustomapi.png)
2. Seleccione los puntos suspensivos (**...** ) del conector y seleccione **Ver propiedades**.  
   
    ![Ver las propiedades del conector](./media/register-custom-api/view-properties.png)
3. Seleccione su API, seleccione **Compartir** y, después, especifique los usuarios o grupos a los que desea conceder acceso a la API.  
   
    ![Compartir el conector personalizado](./media/register-custom-api/sharecustomapi.png)
4. Seleccione **Guardar**.

## <a name="next-steps"></a>Pasos siguientes
[Vea cómo crear una colección Postman](postman-collection.md)

[Use una instancia de ASP.NET Web API](customapi-web-api-tutorial.md).

[Registre una API de Azure Resource Manager](customapi-azure-resource-manager-tutorial.md).

