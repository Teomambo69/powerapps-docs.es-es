---
title: Agregar un nombre de dominio personalizado | MicrosoftDocs
description: Instrucciones para agregar un nombre de dominio personalizado.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/21/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 2e8cd720f4ad5d1ff285a6414e99f4322b60b7b0
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72978517"
---
# <a name="add-a-custom-domain-name"></a>Agregar un nombre de dominio personalizado

Un dominio personalizado puede ayudar a los clientes a encontrar más fácilmente los recursos de soporte técnico y mejorar su marca. Solo se puede Agregar un nombre de dominio personalizado a un portal. Después de aprovisionar el portal y adquirir el nombre de dominio, necesitará un certificado SSL para configurar un nombre de host personalizado. Puede usar el certificado SSL adquirido para el dominio con el fin de vincular el portal a un dominio personalizado mediante un asistente.

1. Abra el [centro de administración de portales de PowerApps](admin-overview.md).

2. Vaya a **acciones del Portal** > **Agregar un nombre de dominio personalizado**. Se abre un asistente para elegir el certificado SSL.

3. En la página **elegir un certificado SSL** , seleccione una de las siguientes opciones:
   - **Cargar un certificado nuevo**: Seleccione esta opción para cargar el archivo. pfx si todavía no lo ha cargado en la organización. Seleccione el botón cargar bajo **archivo** para seleccionar el archivo. pfx. Después de seleccionar el archivo, escriba la contraseña del certificado SSL en el campo **contraseña** .
   - **Usar un certificado existente**: Seleccione esta opción para elegir el certificado correcto en la lista desplegable.

     > [!Note]
     > El certificado SSL debe cumplir todos los requisitos siguientes:
     > - Firmado por una entidad de certificación de confianza
     > - Exportados como un archivo PFX protegido por contraseña
     > - Contiene una clave privada con una longitud mínima de 2048 bits
     > - Contiene todos los certificados intermedios de la cadena de certificados
     > - Debe ser SHA2 habilitado; La compatibilidad con SHA1 se quita de los exploradores más populares

4. Seleccione **Siguiente**.

5. En la página **elegir un nombre de host** , seleccione una de las siguientes opciones:
    - **Agregar un nuevo nombre de host**: Seleccione esta opción para crear un nuevo dominio personalizado. Escriba el nombre de dominio que desee en el campo **nombre de dominio** .
    - **Usar un nombre de host existente**: Seleccione esta opción para elegir un nombre de host de la lista desplegable. 
   
   > [!Note]
   > - Solo puede tener un nombre de dominio personalizado para un portal. 
   > - Para crear un nombre de host personalizado, debe crear un CNAME con el proveedor de dominios que apunte su dominio a la dirección URL de su portal. Si acaba de agregar un CNAME con el proveedor de dominios, se tardará un tiempo en propagarse a todos los servidores DNS. Si el nombre no se propaga y lo agrega aquí, aparecerá el siguiente mensaje de error: Agregue un registro CNAME a este nombre de dominio. Vuelva a intentarlo después de que transcurra un tiempo.

6. Revise la información que ha escrito y, a continuación, seleccione **siguiente** para empezar a crear el enlace SSL. Debería ver que el mensaje nombre de dominio personalizado se ha configurado correctamente para este portal. Ahora puede ir a {nombre de dominio personalizado} para acceder a este portal. {Nombre de dominio personalizado} será un hipervínculo a la dirección URL del portal personalizado que se acaba de configurar.

7. Seleccione **Finalizar** para cerrar el asistente.

    > [!Note]
    > Si desea cambiar el nombre de dominio personalizado existente, debe cargar un nuevo certificado SSL y seguir los pasos del asistente, tal como se mencionó [aquí](#link-your-portal-to-a-custom-domain).
    

