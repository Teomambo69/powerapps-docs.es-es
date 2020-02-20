---
title: Importación de datos en aplicaciones controladas por modelos | MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 11/16/2018
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
- D365CE
ms.openlocfilehash: 8f1105fc88fe87aabceaa10160b96e2d7299cbe0
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74733211"
---
# <a name="import-data"></a>Importar datos

Si sus datos están almacenados en una hoja de cálculo, en el teléfono o en un programa de correo electrónico, en este artículo sabrá cómo importar los datos en su aplicación. Por ejemplo, importar su lista de contactos de clientes desde una hoja de cálculo de Excel en la aplicación para poder realizar un seguimiento de toda la información de los clientes en un mismo lugar.
  
## <a name="step-1-get-your-import-file-ready"></a>Paso 1: Prepárese el archivo de importación  
En primer lugar, exporte los datos a un archivo de Excel. Se admiten estos formatos de archivo:
 - Libro de Excel (.xlsx)
 - Valores separados por comas (.csv)
  
El tamaño máximo de archivo permitido para archivos .zip es de 32 MB. Para el resto de los formatos de archivo, el tamaño máximo de archivo permitido es de 8 MB.  
  
### <a name="export-data-from-an-email-program"></a>Exportación de datos desde un programa de correo electrónico  
  
1.  Exporte los datos a un archivo de valores separados por comas (.csv).  
  
     Para ver los pasos específicos sobre cómo exportar los contactos de su programa de correo electrónico, abra la Ayuda del programa y busque "exportar". Busque temas que incluyan "exportación de contactos", "exportación de la libreta de direcciones" o "Asistente para exportación" en el título.  
  
2.  Guarde el archivo en una ubicación donde pueda encontrarlo más fácilmente.  
  
### <a name="export-data-from-a-spreadsheet"></a>Exportación de datos desde una hoja de cálculo  
  
1.  Abra la hoja de cálculo.  
  
2.  Si es necesario, edite el nombre de cualquier columna de la hoja de cálculo para que coincida con el nombre correspondiente que se muestra a continuación.  
  
    > [!WARNING]
    > Si la hoja de cálculo no incluye todos los nombres de columna enumerados, es correcto. Sin embargo, si hay un nombre de columna, debe coincidir exactamente con el nombre correspondiente en la lista; si no, la importación no funcionará. Los espacios son obligatorios. Tenga en cuenta que la palabra "Email" no contiene un guión.  

    |**Nombre de columna en la hoja de cálculo (la ortografía debe coincidir exactamente)**|
    |---------|
    |Nombre|  
    |Segundo nombre|  
    |Apellidos|  
    |Teléfono del trabajo|  
    |Teléfono móvil|  
    |Puesto|  
    |Calle del trabajo|  
    |Ciudad de trabajo|  
    |Estado o provincia del trabajo|  
    |Código postal del trabajo|  
    |País o región del trabajo|  
    |Dirección de correo electrónico|  
  
3.  Guarde el archivo.  
  
### <a name="export-data-from-your-phone"></a>Exportación de datos desde el teléfono  

Utilice un cable USB o una aplicación para exportar datos, como los contactos, desde el teléfono a su equipo.
  
Para buscar los pasos específicos sobre cómo exportar los contactos de su marca de teléfono, busque "exportar contactos de mi teléfono" en su motor de búsqueda favorito (como Bing).  
  
Para buscar una aplicación, busque en la tienda en línea del teléfono.  
  
## <a name="step-2-import-the-file"></a>Paso 2: Importe el archivo. 
  
1. En la barra de comandos, seleccione **Importar desde Excel** o **Importar desde archivo CSV**.

   > [!div class="mx-imgBorder"]
   > ![Menú principal de Power Apps](media/import.png "Menú principal de Power Apps")
  
2. Vaya a la carpeta donde guardó el archivo que contiene la exportación de los contactos. Seleccione el archivo, elija **Abrir** y, a continuación, seleccione **Siguiente**.  
  
   > [!TIP]
   > Solo puede importar un archivo a la vez. Para importar más archivos, vuelva a ejecutar al asistente más tarde.
   
3. Revise el nombre de archivo y compruebe que los delimitadores de campos y datos son correctos mediante la opción **Revisar asignación**. Si todo parece correcto, seleccione **Finalizar importación**.  
 
## <a name="step-3-check-that-the-import-is-successful"></a>Paso 3: Compruebe que la importación es correcta

Cuando finalice el asistente, compruebe los datos (por ejemplo, la lista de contactos) para asegurarse de que se han importado correctamente.  
  
1. En el menú principal, vaya a **Contactos**.
  
2. Desplácese por la lista de contactos. Compruebe que aparece cada persona y verifique que el contenido de los campos es preciso.

## <a name="import-double-byte-characters"></a>Importación de caracteres de doble byte 

Si va a importar datos que incluyen caracteres de doble byte de idiomas de Este de Asia, asegúrese de que el archivo está codificado como UTF-8 BOM. La codificación UTF-8 estándar podría no ser suficiente.

1. Abra el archivo CSV utilizando Visual Studio Code.
2. En la barra inferior, haga clic en la etiqueta **UTF-8** (se abre una ventana emergente). 
3. Seleccione **Guardar con codificación**. 

Ahora puede seleccionar la codificación UTF-8 BOM para ese archivo.

