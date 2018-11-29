---
title: 'Exportación, preparación para editar e importación de la cinta de opciones (aplicaciones basadas en modelos) | Microsoft Docs'
description: 'Obtenga información sobre cómo exportar la cinta de opciones al incluirla en una solución y, a continuación, exportando la solución. Puede exportar todas las personalizaciones, pero esto puede representar una gran cantidad de datos. Se recomienda usar una solución no administrada existente o crear una solución nueva.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: shilpas
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="export-prepare-to-edit-and-import-the-ribbon"></a>Exportar, preparar para modificar e importar la cinta de opciones

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/customize-dev/export-prepare-edit-import-ribbon -->

Para editar la cinta de opciones, debe realizar los siguientes pasos:  
  
1.  [Exporte la cinta de opciones](export-prepare-edit-import-ribbon.md#BKMK_ExportTheRibbon)  
  
2.  [Prepararse para editar el archivo XML](export-prepare-edit-import-ribbon.md#BKMK_PrepareToEditTheXML)  
  
3.  Edite la `<RibbonDiffXml>`  
  
4.  [Importar la cinta de opciones](export-prepare-edit-import-ribbon.md#BKMK_ImportTheRibbon)  
  
<a name="BKMK_ExportTheRibbon"></a>   
## <a name="export-the-ribbon"></a>Exporte la cinta de opciones  
 La cinta de opciones se exporta al incluirla en una solución y luego se exporta la solución. Puede exportar todas las personalizaciones, pero esto puede representar una gran cantidad de datos. Se recomienda usar una solución no administrada existente o crear una solución nueva.  
  
#### <a name="create-a-new-solution"></a>Crear una solución nueva  
  
1. Vaya a **Configuración > Personalizaciones**.
1. Vaya a **Configuración > Soluciones**.
1. Haga clic o pulse en **Nuevo**.  
1. Escriba un **Nombre** significativo, **Nombre único** e ingrese un **Editor** y escriba un número **Versión**.  
  
   > [!NOTE]
   >  Puede usar normalmente el editor predeterminado para la organización.  
  
6. Haga clic en el icono **Guardar**.  
  
7. Si desea modificar la cinta de opciones de entidades específicas:  
  
   1.  Haga clic en **Agregar existente** y, a continuación, haga clic en **Entidad**.  
  
   2.  Seleccione las entidades que desea incluir en la Solución y, a continuación, haga clic en **Aceptar**.  
  
       > [!NOTE]
       >  Para editar las cintas de opciones de entidad, no tiene que incluir los componentes necesarios. Si trata de exportar esta solución y aplicarla en otro sistema, debe incluir los componentes necesarios.  
  
8. Si desea editar las cintas de opciones globales o agregar un grupo personalizado a todas las entidades, haga clic en **Agregar existente** y luego haga clic en **Cintas de opciones de la aplicación**.  
  
9. Haga clic en **Guardar y cerrar**.  
  
#### <a name="use-an-existing-solution"></a>Usar una solución existente  
  
1. Vaya a **Configuración > Personalizaciones**.
1. Vaya a **Configuración > Soluciones**. 
1. Haga doble clic en una solución para abrirla.  
  
5. Si desea modificar la cinta de opciones de entidades específicas:  
  
   1.  Haga clic en **Agregar existente** y, a continuación, haga clic en **Entidad**.  
  
   2.  Seleccione las entidades que desea incluir en la Solución y, a continuación, haga clic en **Aceptar**.  
  
       > [!NOTE]
       >  Para editar las cintas de opciones de entidad, no tiene que incluir los componentes necesarios. Si trata de exportar esta solución y aplicarla en otro sistema, debe incluir los componentes necesarios.  
  
6. Si desea editar las cintas de opciones globales o agregar un botón personalizado a todas las entidades: haga clic en **Agregar existente** y luego haga clic en **Cintas de opciones de la aplicación**.  
  
7. Haga clic en **Guardar y cerrar**.  
  
#### <a name="export-the-ribbon"></a>Exporte la cinta de opciones  
  
1. Vaya a **Configuración > Personalizaciones**.
1. Vaya a **Configuración > Soluciones**.
  
4. Seleccione la solución que desea y luego haga clic en **Exportar**.  
  
5. Si ha realizado cambios recientes que aún no se han publicado, haga clic en **Publicar todas las personalizaciones**. De lo contrario, haga clic en **Siguiente**.  
  
6. Con la opción **No administrado** seleccionada, haga clic en **Exportar**.  
  
7. Haga clic en **Guardar** en el cuadro de diálogo **Descarga de archivos** y luego haga clic en **Abrir carpeta** en el cuadro de diálogo **Descarga completa**.  
  
8. Haga clic con el botón secundario en el archivo .zip que descargó y seleccione **Extraer todo...**  
  
9. Seleccione una ubicación para extraer los archivos y luego haga clic en **Extraer**.  
  
10. El archivo customizations.xml es el archivo que se modificará.  
  
<a name="BKMK_PrepareToEditTheXML"></a>   
## <a name="prepare-to-edit-the-xml"></a>Prepararse para editar el archivo XML  
 Para una mejor experiencia, edite el archivo customizations.xml con una aplicación que pueda usar la validación de esquema para proporcionar soporte de IntelliSense. Para obtener más información, consulte [Editar el archivo de personalizaciones con la validación de esquema](edit-customizations-xml-file-schema-validation.md).  
  
<a name="BKMK_ImportTheRibbon"></a>   
## <a name="import-the-ribbon"></a>Importar la cinta de opciones  
  
1. Después de modificar el archivo customization.xml, en Visual Studio o Visual Web Developer 2010 Express, haga clic con el botón secundario en la pestaña customization.xml y seleccione **Abrir carpeta contenedora**.  
  
2. Seleccione todos los archivos o carpetas que se incluyeron cuando se extrajo la solución. Haga clic con el botón secundario en los archivos seleccionados, seleccione **Enviar a**y luego seleccione la carpeta **Carpeta comprimida (en zip)**.  
  
   > [!NOTE]
   >  Se creará un archivo comprimido .zip en la misma carpeta. El nombre del archivo puede variar, pero coincidirá con uno de los demás archivos en la carpeta, excepto por la extensión de nombre de archivo .zip.  
  
1. Vaya a **Configuración > Personalizaciones**.
1. Vaya a **Configuración > Soluciones**. 
  
6. Haga clic en **Importar**.  
  
7. Haga clic en **Examinar** y busque el archivo .zip comprimido que creó en el paso 2 de este procedimiento.  
  
8. Haga clic en **Siguiente** y, a continuación, haga clic en **Importar**.  
  
9. Cuando haya terminado la importación, verá el mensaje que indica que la importación se completó correctamente. Haga clic en Cerrar.  
  
10. Una vez que haya importado correctamente la solución, debe publicar las personalizaciones para poder ver los cambios. En la lista Soluciones, haga clic en **Publicar todas las personalizaciones**.  
  
<a name="BKMK_DealWithErrorsOnImport"></a>   
### <a name="dealing-with-errors-on-import"></a>Cómo gestionar los errores en la importación  
  
1.  Si recibe una notificación que se produjeron errores que causaron un problema en la importación, haga clic en **Exportar registro**.  
  
2.  Guarde el archivo de registro de exportación. Seleccione el archivo y haga clic con el botón secundario. Haga clic en **Abrir con** y luego seleccione **Microsoft Office Excel**.  
  
3.  Seleccione la hoja de cálculo **Componentes** y observe los mensajes en la columna **ErrorText**.  
  
    > [!TIP]
    >  El tipo de error más común es un error que hace referencia a un elemento dependiente en el RibbonDiffXml. Es posible que se haya olvidado de incluir una LocLabel a la que se hace referencia en alguna parte. Quizás haya un espacio en blanco adicional al final de un atributo XML que hace referencia a otro elemento. Todas las referencias deben coincidir exactamente.  
  
4.  Una vez que haya corregido el error, complete los pasos para importar la cinta de opciones nuevamente.  
  
### <a name="see-also"></a>Vea también  
 [Personalizar la cinta de opciones](customize-commands-ribbon.md)   
 [Exportar definiciones de cinta de opciones](export-ribbon-definitions.md)   
 [Usar etiquetas localizadas con cintas de opciones](use-localized-labels-ribbons.md)
