---
title: Agregar un nombre de dominio personalizado | MicrosoftDocs
description: Instrucciones para agregar un nombre de dominio personalizado.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: e354a3a784a984e070f5948b4b14c9eb4c32417b
ms.sourcegitcommit: 6cffa70358fd2e388d64a01f906c8c196fbbdefb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/17/2020
ms.locfileid: "3069559"
---
# <a name="add-a-custom-domain-name"></a>Agregue un nombre de dominio personalizado

Un dominio personalizado puede ayudar a sus clientes a encontrar los recursos de soporte más fácilmente y mejorar su marca. Solo un nombre de dominio personalizado se puede agregar a un portal. Después de aprovisionar el portal y adquirir el nombre de dominio, necesitará un certificado SSL para configurar un nombre de host personalizado. Puede usar el certificado SSL comprado para el dominio para vincular el portal a un dominio personalizado utilizando el asistente.

1. Abra [Centro de administración de Portales de Power Apps](admin-overview.md).

2. Vaya a **Acciones del portal** > **Agregar un nombre de dominio personalizado**. Se abrirá el asistente para elegir el certificado SSL.

3. En la página , **Escoger un certificado SSL**, seleccione una de las siguientes opciones:
   - **Cargar un nuevo certificado**: seleccione esta opción para cargar el archivo .pfx si aún no lo ha cargado a la organización. Seleccione el botón cargar bajo **Archivo** y seleccione el archivo .pfx. Una vez haya seleccionado el archivo, escriba la contraseña del certificado SSL en el campo **Contraseña**.
   - **Usar un certificado existente**: seleccione esta opción para escoger el certificado correcto en el menú desplegable.

     > [!Note]
     > El certificado SSL debe cumplir los siguientes requisitos:
     > - Debe estar firmado por una entidad de certificación de confianza.
     > - [Exportado](https://docs.microsoft.com/powershell/module/pkiclient/export-pfxcertificate?view=win10-ps) como un archivo PFX protegido con contraseña.
     > - Debe contener una clave privada de al menos 2048 bits de longitud.
     > - Debe contener todos los certificados intermedios de la cadena de certificados.
     > - Debe estar habilitado para SHA2; el soporte técnico de SHA1 ya no estará disponible en los exploradores más populares.
     > 
     > Los pasos para exportar el certificado SSL como un archivo PFX protegido con contraseña pueden variar según el proveedor de su certificado. Consulte con su proveedor de certificados para obtener recomendaciones. Por ejemplo, ciertos proveedores pueden sugerir utilizar la herramienta de terceros OpenSSL desde los sitios [OpenSSL](https://www.openssl.org/) o [Binarios de OpenSSL](https://wiki.openssl.org/index.php/Binaries). 

4. Seleccione **Siguiente**.

5. En la página **Escoger un nombre de host**, seleccione una de las siguientes opciones:
    - **Agregar un nuevo nombre de host**: Seleccione esta opción para crear un nuevo dominio personalizado. Escriba el nombre de dominio que quiera en el campo **Nombre de dominio**.
    - **Usar un nombre de host existente**: seleccione esta opción para escoger un nombre de host del menú desplegable. 
   
   > [!Note]
   > - Solo puede tener un nombre de dominio personalizado para un portal. 
   > - Para crear un nombre de host personalizado, deberá crear un CNAME con su proveedor de dominio que señale el dominio a la dirección URL del portal. Si acaba de agregar un CNAME con su proveedor de dominio, tardará algún tiempo en difundirse a todos los servidores DNS. Si el nombre no se difunde y lo agrega aquí, se mostrará el siguiente un mensaje de error: Agregue un registro CNAME a este nombre de dominio. Vuelva a intentarlo después de un tiempo.

6. Revise la información que ha especificado y haga clic en **Siguiente** para empezar a crear el enlace SSL. Debería ver el mensaje El nombre de dominio personalizado se ha configurado correctamente en este portal. Ahora puede ir a {Custom Domain Name} para obtener acceso a este portal. {Custom Domain Name} será un hipervínculo a la dirección URL del portal personalizada que acaba de configurar.

7. Para cerrar el asistente, elija **Finalizar**.

    > [!Note]
    > Si desea cambiar el nombre de dominio personalizado existente, debe cargar un nuevo certificado SSL y seguir los pasos del asistente de esta sección.
    

