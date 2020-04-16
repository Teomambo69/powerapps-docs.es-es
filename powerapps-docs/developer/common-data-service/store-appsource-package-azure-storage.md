---
title: 'Paso 4: Almacenar el paquete AppSource en Azure Storage y generar una dirección URL con clave SAS (Common Data Service) | Microsoft Docs'
description: Para mantener la seguridad de los archivos, todos los desarrolladores de aplicaciones deben almacenar su archivo de paquete AppSource en una cuenta de almacenamiento del objeto binario de Microsoft Azure y usar una clave de firma de acceso compartido (SAS) para compartir el archivo de paquete. El archivo de paquete se recupera de la ubicación de Azure Storage para certificación y, después, para versiones de prueba de AppSource.
ms.custom: ''
ms.date: 12/20/2019
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: shmcarth
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: cb6436f85a9961bad403c3a6c97440f154877b00
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155276"
---
# <a name="step-4-store-your-appsource-package-on-azure-storage-and-generate-a-url-with-sas-key"></a>Paso 4: Almacenar el paquete AppSource en Azure Storage y generar una dirección URL con clave SAS

Microsoft Azure Storage es un servicio de nube administrado por Microsoft que proporciona almacenamiento de gran disponibilidad, seguridad, duración, escalabilidad y es redundante. Más información: [Introducción a Microsoft Azure Storage](https://docs.microsoft.com/azure/storage/common/storage-introduction).

Para mantener la seguridad de los archivos, todos los desarrolladores de aplicaciones deben almacenar su archivo de paquete AppSource en una cuenta de almacenamiento del objeto binario de Microsoft Azure y usar una clave de firma de acceso compartido (SAS) para compartir el archivo de paquete. El archivo de paquete se recupera de la ubicación de Azure Storage para certificación y, después, para versiones de prueba de AppSource.

## <a name="before-you-upload-your-package"></a>Antes de cargar el paquete

Descargar e instalar el Explorador de Microsoft Azure Storage desde [https://storageexplorer.com](https://storageexplorer.com).

Azure Storage Explorer le permite administrar fácilmente el contenido de su cuenta de almacenamiento.

## <a name="upload-your-package-and-generate-a-url-with-sas-key"></a>Cargar el paquete y generar una dirección URL con clave SAS

Para cargar el paquete en Azure blob Storage:

1. Cree una cuenta de Azure gratuita o de pago por uso en [https://azure.microsoft.com](https://azure.microsoft.com).
2. Inicie sesión en el Portal de administración de Azure en [https://portal.azure.com](https://portal.azure.com).
3. Cree una nueva cuenta de almacenamiento, haciendo clic en > **almacenamiento** > **cuenta de almacenamiento - blob, archivo, tabla, cola**.
    
   ![](media/appsource-storageaccount-pic1.png)

4. En la página **crear cuenta de almacenamiento**, especifique **nombre**, **grupo de recursos** y **ubicación** para su cuenta de almacenamiento. Deje el resto de los campos con las opciones predeterminadas. Haga clic en **Crear**. 

   ![](media/appsource-storageaccount-pic2.png)
 
  
5. Después de crear la cuenta de almacenamiento, vaya al grupo de recursos recién creado y cree un contenedor de blob nuevo. En **Blob Service**, seleccione **contenedores** y, después, **+ Contenedor**.

   ![](media/appsource-storageaccount-pic3.png)

6. Especifique un nombre para su contenedor y seleccione el **nivel de acceso público** como **Blob**. Haga clic en **Aceptar**.

   ![](media/appsource-storageaccount-pic4.png)

7. Inicie Azure Storage Explorer en su equipo y conéctese a su cuenta de Azure Storage iniciando sesión con la misma cuenta con la que ha creado su cuenta de Azure Storage.

8. En Azure Storage Explorer, seleccione el contenedor recién creado y seleccione **Cargar** > **Cargar archivos** para cargar el paquete de origen de la aplicación que ha creado en [paso 4: crear un paquete de AppSource para su aplicación](create-package-app-appsource.md). 

   ![](media/appsource-storageaccount-pic5.png)

9. Busque el archivo de paquete de AppSource en su equipo y selecciónelo para cargarlo.

10. Haga clic con el botón derecho del mouse en el archivo de paquete AppSource cargado y seleccione **Obtener firma de acceso compartido**.

    ![](media/appsource-storageaccount-pic6.png)

11. En la página **firma de acceso compartido**, modifique el valor de **tiempo de expiración** para activar la firma de acceso compartido (SAS) durante un mes desde la **hora de inicio**. Haga clic en **Crear**.

    ![](media/appsource-storageaccount-pic7.png)

12. La siguiente página muestra información sobre la información de SAS generada. Copie el valor de la **dirección URL** para más tarde. Deberá especificar esta dirección URL al crear una oferta en el Portal de Socio en la nube.

    ![](media/appsource-storageaccount-pic8.png)


> [!div class="nextstepaction"]
> [Pasos siguientes: enviar la aplicación al Centro de partners](next-steps-submit-app-cloud-partner-portal.md)
