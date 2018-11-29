---
title: Distribuir una aplicación controlada por modelos usando una solución | MicrosoftDocs
description: Aprenda a distribuir una aplicación controlada por modelos usando soluciones
keywords: ''
ms.date: 08/06/2018
ms.service: crm-online
ms.custom: null
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.assetid: e82e7f64-37ad-41e5-acd7-16309881c6a2
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: null
ms.suite: null
ms.tgt_pltfrm: null
caps.latest.revision: 9
topic-status: Drafting
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="distribute-a-model-driven-app-using-a-solution"></a>Distribuir una aplicación controlada por modelos usando una solución

Las aplicaciones basadas en modelos se distribuyen como componentes de la solución. Una vez que haya creado una aplicación controlada por modelos, puede hacer que esté disponible para que otros entornos la usen empaquetando la aplicación en una solución y, después, se exportándola en un archivo zip. Después de que la solución (archivo .zip) se importa correctamente en el entorno de destino, la aplicación empaquetada está disponible para su uso. 
  
## <a name="add-an-app-to-a-solution"></a>Agregar una aplicación a una solución
Para distribuir su aplicación, debe crear una solución para que la aplicación se pueda empaquetar para la exportación.

1. Iniciar sesión en [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

2. Seleccione **Soluciones** y seleccione **Nueva solución**.
3. Complete los campos en la página **Nueva solución** y, a continuación, seleccione **Guardar**. Más información: [Crear una solución](../common-data-service/create-solution.md)
4. Se muestra la página **Solución**. Seleccione **Agregar existente**, seleccione **Aplicación**, seleccione la aplicación que desea agregar a la solución y, a continuación, seleccione **Aceptar**. 

    ![Seleccionar componentes de la solución](media/select-solution-components.png)

5. Si aparece una página **Faltan componentes necesarios** se recomienda seleccionar **Sí, incluir componentes necesarios** para agregar componentes necesarios como entidades, vistas, formularios, gráficos y mapa del sitio que formen parte de la aplicación. Seleccione **Aceptar**.
6. En la página **Solución**, seleccione **Guardar y cerrar**.

## <a name="export-a-solution"></a>Exportación de soluciones
Para distribuir la aplicación de modo que se pueda importar en otro entorno o ponerla a disposición en [Microsoft AppSource](https://appsource.microsoft.com/), debe exportar la solución a un archivo zip. A continuación, el archivo zip que contiene la aplicación y los componentes se puede importar en otros entornos.

1. Abra la [página Soluciones](advanced-navigation.md#solutions). 
2. Seleccione la solución que desea exportar y, después, en la barra de herramientas, seleccione **Exportar**. 
3. En la página **Publicar personalizaciones**, seleccione **Siguiente**.
4. Si aparece la página **Faltan componentes necesarios**, seleccione **Siguiente**. 
5. En la página **Exportar configuración del sistema**, seleccione las características opcionales que desee incluir y, a continuación, seleccione **Siguiente**. 
6. En la página **Tipo de paquete**, seleccione **No administrado** o **Administrado** y seleccione **Exportar**. Para obtener más información acerca de los tipos de paquetes de soluciones, consulte [Información general de soluciones](../common-data-service/solutions-overview.md).
7. En función del explorador y valores de configuración, se crea un archivo del paquete .zip y se copia en la carpeta de descargas predeterminada. El nombre de archivo del paquete se basa en el nombre único de la solución anexada con caracteres de subrayado y el número de versión de la solución.

    > [!NOTE]
    > Cuando exporta una aplicación mediante una solución, no se exporta la dirección URL de la aplicación.
  
## <a name="import-a-solution"></a>Importación de soluciones  
Cuando reciba un archivo zip de la solución que contiene la aplicación que desea importar, abra la página de componentes de soluciones e importe la solución. Cuando la solución se haya importado correctamente, la aplicación estará disponible en su entorno.

1. Iniciar sesión en [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

2. Seleccione **Soluciones** y en la barra de herramientas seleccione **Importar**.
3. Examine el archivo que desea importar y elija **Siguiente**.
4. Seleccione **importar**.

## <a name="see-also"></a>Vea también
[Cambiar el prefijo del editor de soluciones](../common-data-service/change-solution-publisher-prefix.md)
