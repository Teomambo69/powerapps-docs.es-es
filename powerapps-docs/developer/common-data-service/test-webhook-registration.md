---
title: Probar el registro de webhook con un sitio de registro de solicitud (Common Data Service para aplicaciones) | Microsoft Docs
description: Para comprender los datos contextuales pasados con un webhook conviene usar un sitio de registro de solicitud para explorar los datos. En este tema se describirá cómo hacerlo.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="test-webhook-registration-with-request-logging-site"></a>Probar el registro de webhook con un sitio de registro de solicitud 

Antes de pasar a crear o configurar un servicio para consumir webhooks, debe probar el tipo de datos que recibirá el servicio para saber qué tipo de datos tendrá que procesar. Para ello, puede usar uno de distintos sitios de registro de solicitud. Para este ejemplo, vamos a usar [Webhook Tester](https://webhook.site) para configurar un destino para las solicitudes de webhook. Lleve a cabo los pasos siguientes:

1. Vaya a [https://webhook.site](https://webhook.site). En la esquina superior derecha verá un botón **Copiar** verde.
    ![Botón de copia de Webhook Tester](media/webhook-tester-copy-button.png)
1. Use el botón **Copiar** para copiar la dirección URL. Consulte esta página abierta.
1. Utilice la herramienta de registro de complementos para registrar un nueva webhook tal como se describe en [Registrar un webhook](register-web-hook.md). 
    1. Use la URL que copió en el paso 2 como la **URL de extremo**. 
    1. Defina un nombre y cualquier propiedad de autenticación que desee. Webhook Tester no evaluará estos valores de la forma que un sitio real procesaría los datos, pero puede ver cómo se transfirieron.
1. Utilice la herramienta de registro de complementos para registrar un paso mediante el webhook que creó en el paso 4 tal como se describe en [Registrar un paso para un webhook](register-web-hook.md#register-a-step-for-a-webhook). 
    1. Asegúrese de usar un evento que puede realizar fácilmente editando los datos en la aplicación de CDS para aplicaciones, como la actualización de una entidad de contacto.
1. Utilice la aplicación de CDS para aplicaciones para realizar la operación para desencadenar el evento.
1. Una vez que desencadene el evento, vuelva a la página de Webhook Tester del paso 2. Debe ver que la página se ha actualizado para mostrar los datos pasados en la solicitud:

    ![Un ejemplo de la solicitud registrada en el sitio web de Webhook Tester](media/webhook-tester-example.png)

    > [!TIP]
    > Use la opción **Formato JSON** para facilitar la lectura del JSON devuelto en el cuerpo de la solicitud.

## <a name="next-steps"></a>Pasos siguientes

[Utilice webhooks para crear controladores externos para eventos de servidor](use-webhooks.md)

### <a name="see-also"></a>Vea también
[Registrar un webhook](register-web-hook.md)