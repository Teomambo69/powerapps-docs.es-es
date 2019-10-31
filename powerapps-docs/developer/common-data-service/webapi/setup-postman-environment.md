---
title: Configurar un entorno Postman (Common Data Service para aplicaciones)| MicrosoftDocs
description: Aprenda a instalar y configurar un entorno Postman que se conecte con entornos de Common Data Service.
ms.custom: null
ms.date: 04/09/2019
ms.reviewer: null
ms.service: powerapps
ms.suite: null
ms.tgt_pltfrm: null
ms.topic: article
ms.assetid: 955BA444-A53D-4843-9429-833B1636E2B4
caps.latest.revision: 7
author: susikka
ms.author: susikka
manager: shujoshi
search.audienceType:
  - developer
search.app:
  - D365CE
---

# <a name="set-up-a-postman-environment"></a>Configure un entorno Postman

Puede usar Postman para conectarse a su instancia de Common Data Service y componer solicitudes wen API, enviarlas y ver respuestas. Administrar la autenticación un desafío para mucha gente. Este tema describe cómo configurar un entorno Postman para trabajar en entornos de Common Data Service.

Puede usar un entorno Postman para guardar un conjunto de variables que usará para conectarse. Estos valores se pueden agregar en Postman mediante esta sintaxis: `{{name}}`. Para obtener más información sobre variables Postman, consulte [Documentación de Postman > Variables](https://www.getpostman.com/docs/v6/postman/environments_and_globals/variables).

## <a name="prerequisites"></a>Requisitos previos

* Obtenga un entorno de PowerApps Common Data Service al que puede conectarse. 
* Descargue e instale el  [Aplicación de envío para ordenador](https://www.getpostman.com/apps).

<a name="bkmk_connectcds"></a> 

## <a name="connect-with-your-common-data-service-environment"></a>Conectar con su entorno de Common Data Service

Este entorno utiliza un ID de cliente para una aplicación que está registrada para todos los entornos de Common Data Service. 
 
Puede usar `clientid` y `callback`, los valores propuestos en estas instrucciones.  Sin embargo, al generar su propia aplicación, debe registrar su propia aplicación de Azure Active Directory (Azure AD).
 
Para registrar su propia aplicación de Azure AD, vea los pasos descritos en [Tutorial: Registrar una aplicación de Common Data Service con Azure Active Directory](../walkthrough-register-app-azure-active-directory.md).

Use estos pasos para crear un entorno de envío que puede usar para conectarse con su instancia de Common Data Service:

1. Inicie la aplicación de envío de escritorio.
1. Seleccione en el icono **Opciones de entorno** en la esquina superior derecha. 
1. En el cuadro **Administrar entornos**, seleccione el botón **Agregar** para agregar un nuevo entorno.
  
  ![Haga clic en Agregar el botón para agregar un nuevo entorno de envío](media/postman-manage-env.png "Haga clic en Agregar el botón para agregar un nuevo entorno de envío")<br>
  
1. En el cuadro de diálogo que se abre, escriba un nombre para el entorno. A continuación agregue los siguientes pares de clave-valor en el espacio de edición.<br>

    | Nombre de variable | Value |
    |----|---|
    |`url`|`https://<add your environment name, like ‘myorg.crm’>.dynamics.com`|
    |`clientid`|`51f81489-12ee-4a9e-aaae-a2591f45987d`|
    |`version`|`9.0`|
    |`webapiurl`|`{{url}}/api/data/v{{version}}/`|
    |`callback`|`https://callbackurl`|
    |`authurl`|`https://login.microsoftonline.com/common/oauth2/authorize?resource={{url}}`|

    ![Cree un nuevo entorno Postman para establecer la conexión con la instancia online](media/postman-add-online-env.png "Cree un nuevo entorno Postman para establecer la conexión con la instancia online")<br>
1. Reemplace el valor de marcador de posición de la URL de instancia de Common Data Service y seleccione **Agregar** para guardar el entorno.

1. Cierre el diálogo **Administrar entornos** .  

### <a name="generate-an-access-token-to-use-with-your-environment"></a>Genere un token de acceso para usar con su entorno

Para conectar con **OAuth 2.0**, debe tener un símbolo de acceso. Use los siguientes pasos para permitir el acceso a un nuevo token:

1. Asegúrese de que el nuevo entorno que ha creado está seleccionado.
1. Seleccione la ficha **Personalización**.
1. Establezca el **Tipo** **OAuth 2.0**.
1. Compruebe si ha seleccionado el entorno que ha creado.
1. Seleccione **Obtenga el nuevo símbolo de acceso**.

    ![En ficha de licencias, establezca el tipo a OAuth 2.0](media/postman-set-type.png)<br>
1. Establezca los siguientes valores en el cuadro de diálogo. Seleccione `Implicit` del menú desplegable **Grant Type** . Puede establecer **Nombre simbólico** a lo que quiera y deja otras claves en los valores predeterminados.<br>

    ![Obtenga el nuevo símbolo de acceso](media/postman-access-token.png "Obtenga el nuevo símbolo de acceso")<br>

    > [!NOTE]
    > Si está configurando entornos en envío para varias instancias de Common Data Service con credenciales de usuario diferentes, es posible que deba eliminar las cookies almacenadas en la caché de envío. Seleccione el vínculo **Cookies** , que se encuentra en el botón **Enviar** y quite las cookies guardadas del cuadro **Administrar las cookies** .<br>![Quitar Cookies](media/postman-cookies.png "Quitar Cookies")<br>
    > Algunas de estas cookies son muy persistentes. Puede eliminar algunas en grupos, pero otras puede que deba eliminarlas manualmente.   Es posible que tenga que hacer esto dos veces por asegurarse que no permanece ninguna cookies.

1. Seleccione **Solicitar token**. Cuando haga esto, aparecerá una página de inicio de sesión de Azure Active Directory. Compruebe el nombre de usuario y la contraseña.
1. Después de que se genere el símbolo, desplácese a la parte inferior y seleccione **Símbolo de uso**. Esto cerrará el cuadro de diálogo **Administrar símbolos de acceso** . 
1. Tras agregar un símbolo, puede seleccionar qué símbolo que aplicará a las solicitudes. En el menú desplegable **Símbolos disponibles** seleccione el símbolo que acaba de crear. El encabezado Authorization se agrega a la solicitud de la API web.

Vea [Pruebe la conexión](#test-your-connection) para los pasos para comprobar la conexión.

## <a name="test-your-connection"></a>Compruebe su conexión

Crear una nueva solicitud de API web para probar la conexión con su instancia de Common Data Service. Use el <xref href="Microsoft.Dynamics.CRM.WhoAmI?text=WhoAmI function" />:
1. Seleccione `GET` como el método de HTTP y agregan `{{webapiurl}}WhoAmI` en el espacio de edición.
  ![Solicitud del rol WhoAmI](media/postman-whoami-request.png "Solicitud del rol WhoAmI")
2. Seleccione **Enviar** para enviar esta solicitud.
3. Si su solicitud se realiza correctamente, debe ver los datos de <xref href="Microsoft.Dynamics.CRM.WhoAmIResponse?text=WhoAmIResponse ComplexType" /> que son devueltos por <xref href="Microsoft.Dynamics.CRM.WhoAmI?text=WhoAmI Function" />.

## <a name="see-also"></a>Vea también

[Use enviar para realizar operaciones](use-postman-perform-operations.md)<br>
[Tutorial: Registrar una aplicación de Common Data Service con Azure Active Directory](../walkthrough-register-app-azure-active-directory.md)
