---
title: Personalizar los paquetes de contenido de Dynamics 365 Power BI | MicrosoftDocs
description: Obtenga más información sobre cómo modificar los paquetes de contenido de Power BI disponibles para su uso con datos de Dynamics 365.
keywords: PBI
ms.date: 09/30/2017
ms.service: crm-online
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 for Customer Engagement (online)
ms.assetid: 424d7f29-de44-4ce0-94f1-be8777ad6485
author: Mattp123
ms.author: matp
manager: annbe
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: 16
topic-status: Drafting
tags: ''
search.audienceType:
- customizer
search.app:
- D365CE
ms.openlocfilehash: 1fb1c7289e287c96ce53474baba7632106ada79e
ms.sourcegitcommit: 5701e7a755fade6c3bac5c4a5774fcc74627e168
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/10/2020
ms.locfileid: "3115962"
---
# <a name="customize-dynamics-365-apps-power-bi-content-packs"></a>Personalizar los paquetes de contenido Power BI de aplicaciones Dynamics 365

Power BI es una colección completa de servicios y herramientas que se usa para visualizar los datos profesionales.  Hay paquetes de contenido disponibles que permiten visualizar y analizar fácilmente los datos de aplicaciones Dynamics 365 Sales, Service, y Marketing con Power BI basándose en un modelo de datos estándar. Los paquetes de contenido se crean con un conjunto de entidades y campos que son útiles para la mayoría de los escenarios de ventas, de servicio, o de informes de marketing.  
  
 Las instancias de aplicaciones Dynamics 365 se amplían con frecuencia con campos personalizados. Estos campos personalizados no aparecen automáticamente en el modelo de Power BI. En este tema se describen las distintas formas en que se pueden editar o ampliar los informes incluidos en un paquete de contenido para incluir campos personalizados en el modelo de Power BI.  
    
<a name="PBI_edit_first"></a>   
## <a name="do-this-before-you-customize-a-content-pack-for-power-bi-reports"></a>Hágalo antes de personalizar un paquete de contenido para informes de Power BI  
 
Para personalizar un paquete contenido, consulte esta información y realice cada tarea si es necesario.  
  
### <a name="meet-the-requirements"></a>Cumplir los requisitos  
  
- [Registro del servicio de Power BI](https://powerbi.com/).  
  
- [Power BI Desktop](https://powerbi.microsoft.com/desktop) aplicación para editar informes Power BI.  
  
- Archivo PBIX para el paquete de contenido que desea personalizar.  
  
  -   [Descargar el PBIX de Dynamics CRM Online Sales Manager](https://download.microsoft.com/download/9/2/B/92BCBDCE-CE01-4BC9-A306-2A92653B683E/Sales%20Manager.pbix)  
  
  -   [Descargar el PBIX del jefe de servicio de Dynamics CRM Online](https://download.microsoft.com/download/9/2/B/92BCBDCE-CE01-4BC9-A306-2A92653B683E/Customer%20Service%20Manager.pbix)  
  
  -   [Descargar el PBIX de Microsoft Dynamics 365 Process Analyzer](https://download.microsoft.com/download/9/2/B/92BCBDCE-CE01-4BC9-A306-2A92653B683E/Process%20Analyzer%20-1.34b.pbix)  
  
  Los paquetes de contenido de Dynamics 365 se admiten actualmente solo en el idioma inglés de Estados Unidos.  
  
### <a name="prepare-a-content-pack-for-customization"></a>Preparar un paquete de contenido para personalización  
  
> [!IMPORTANT]
>  Para conectar la fuente de OData a su instancia debe seguir los pasos descritos aquí antes de personalizar el paquete de contenido.  
> 
> Actualmente, el servicio Power BI no es compatible con el extremo OData de Dynamics 365 versión 9.0. Cuando intenta usar el extremo OData de la versión 9.0 con el servicio Power BI, aparece el mensaje de error “El documento de metadatos de la fuente no parece válido”. Para solucionar esta incompatibilidad, use el extremo OData de la versión 8.2 de Dynamics 365. Para obtener más información acerca de las distintas versiones de extremo, consulte [Componer solicitudes HTTP y administrar errores](../../developer/common-data-service/webapi/compose-http-requests-handle-errors.md).
  
1. Iniciar Power BI Desktop.  
  
    Seleccione **Archivo** > **Abrir**, abra un paquete de contenido, como Sales Manager.bpix y después seleccione **Abrir**.  
  
    Varias páginas de informes en el paquete de contenido se cargan y muestran enPower BI Desktop.  
  
2. En la cinta de opciones de Power BI Desktop, seleccione **Editar consultas**.  
  
3. En el panel de navegación de la izquierda de la ventana Editar consultas, en **Consultas**, seleccione la consulta **CRMServiceUrl** y en la cinta de opciones seleccione **Editor avanzado**. En la definición de origen, reemplace **base.crm.dynamics.com** con su dirección URL de la instancia de aplicaciones. Por ejemplo, si el nombre de la organización es *Contoso*, la dirección URL tiene esta apariencia:  
  
    Origen = "https://*contoso*.crm.dynamics.com/api/data/v8.0/"  
  
4. Seleccione **Hecho** y después seleccione **Cerrar y aplicar** en el editor de consultas.  
  
5. Cuando aparezca el cuadro de diálogo Acceso a una fuente OData, seleccione **Cuenta profesional** y, a continuación, seleccione **Iniciar sesión**.  
  
   ![Tener acceso a un diálogo Fuente de OData](media/pbi-odata-signin.PNG "Tener acceso a un diálogo Fuente de OData")  
  
6. Cuando aparezca la página de inicio de sesión, escriba sus credenciales para autenticarse en su instancia.  
  
7. En el diálogo Acceso a una fuente OData, seleccione **Conectar**.  
  
    Se actualizan las consultas del paquete de contenido. Esto puede llevar varios minutos.  
  
<a name="PBI_edit_report"></a>   
## <a name="customize-adynamics-365-content-pack"></a>Personalizar Dynamics 365 content pack  
 [Cambiar el formato de fecha que se muestra en un informe](#PBI_edit_date)  
  
 [Agregar un campo personalizado a un informe para una entidad que no sea Cuenta](#PBI_edit_field)  
  
 [Agregar un campo personalizado a un informe para la entidad Cuenta](#PBI_field_Account)  
  
 [Agregar un campo de conjunto de opciones a un informe](#PBI_optionset_field)  
  
 [Aumentar el número de filas consultadas](#BPI_increaserows)  
  
<a name="PBI_edit_date"></a>   
### <a name="convert-a-datetime-field-to-a-date-field-for-reporting"></a>Convertir un campo de fecha y hora en un campo de fecha para informes  
 En aplicaciones Dynamics 365, algunas fechas se guardan en un formato de fecha, hora y zona horaria, que quizá no sea el formato preferido para agregar datos en un informe. Puede convertir la fecha mostrada en informes para un campo de entidad. Por ejemplo, el campo Oportunidad creada el se puede convertir en una fecha para informar de las oportunidades creadas por día.  
  
1. En Power BI Desktop, seleccione **Editar consultas**.  
  
2. En el panel de navegación de la izquierda del editor de consultas en **Consultas**, seleccione la consulta que tiene el campo de fecha que desea cambiar, como **Fecha de cierre estimada** en la consulta de entidad **Oportunidad**.  
  
3. Haga clic con el botón secundario en el encabezado de columna, como *Fecha de cierre estimada*, señale a **Cambiar tipo** y seleccione otro tipo de fecha, como **Fecha**.  
  
   ![Cambiar tipo de datos en Power BI Desktop](media/pbi-changeformat.PNG "Cambiar tipo de datos en Power BI Desktop")  
  
4. Seleccione **Cerrar y aplicar** para cerrar el editor de consultas.  
  
5. En la página principal de Power BI, seleccione **Aplicar cambios** para actualizar los informes asociados.  
  
<a name="PBI_edit_field"></a>   
### <a name="add-a-custom-field-to-a-report"></a>Agregar un campo personalizado a un formulario  
 El siguiente procedimiento describe cómo agregar un campo personalizado que es una fecha, una cadena, o número a un informe para todas las entidades disponible excepto la entidad de cuenta.  
  
> [!NOTE]
>  Para agregar un campo a la entidad Cuenta, consulte [Agregar un campo personalizado a un informe para la entidad Cuenta](#PBI_field_Account). Para agregar un campo que sea un conjunto de opciones, consulte [Agregar un campo de conjunto de opciones a un informe](#PBI_optionset_field).  
  
1. En Power BI Desktop, seleccione **Editar consultas**.  
  
2. En el panel de navegación de la izquierda del editor de consultas, en **Consultas**, seleccione la consulta que tiene el campo personalizado que desea hacer disponible para informes, como la consulta de entidad **Oportunidad**.  
  
3. En el panel derecho, en **PASOS APLICADOS**, seleccione el botón de configuración ![Botón Configuración](media/mp-ua-r16-settings.png "Botón Configuración") junto a **Otras columnas quitadas**.  
  
4. La lista **Elegir columnas** muestra todos los campos para la entidad incluidos campos personalizados. Seleccione un campo personalizado que desea agregar y luego seleccione **Aceptar**.  
  
    Se actualizará la consulta de entidad y una columna se agrega en la tabla de entidad para el campo personalizado que seleccionó.  
  
5. En el panel derecho, en **PASOS APLICADOS**, seleccione **Lang – Columnas cambiadas de nombre** y después seleccione **Editor avanzado** para agregar la asignación para el campo a la consulta de entidad. Por ejemplo, si el nombre del campo personalizado para la entidad de oportunidad es *int_forecast* y el nombre para mostrar es *Previsiones*, la entrada debe aparecer como ésta.  
  
   ```  
   {"int_forecast","Forecast"}  
   ```  
  
   ![Agregar asignación para un campo personalizado en un informe](media/pbi-addfieldmapping.png "Agregar asignación para un campo personalizado en un informe")  
  
6. Después de agregar las asignaciones de campos asegúrese de que no haya errores de sintaxis en la parte inferior del editor avanzado. Además, asegúrese de que aparezca el nombre del campo exactamente del mismo modo que aparece en el encabezado de columna, incluido el uso de mayúsculas y minúsculas. Si no se detecta ningún error de sintaxis o de tabla, seleccione **Hecho**.  
  
7. Haga clic en **Cerrar y cargar** en el editor de consultas.  
  
    El campo personalizado está ahora disponible en el panel derecho en **Campos** para la entidad y se puede agregar a informes nuevos o existentes.  
  
<a name="PBI_field_Account"></a>   
## <a name="add-a-custom-field-to-a-report-for-the-account-entity"></a>Agregar un campo personalizado a un informe para la entidad Cuenta  
 Puesto que la consulta de cuenta utiliza Fetch XML para filtrar la consulta, los pasos para agregar un campo son distintas que para otras consultas de entidad que usan OData. Para agregar un campo personalizado a las entidades consultadas de OData, consulte [Agregar un campo personalizado a un formulario](#PBI_edit_field).  
  
1. Copie la consulta Fetch XML codificada para la entidad de cuenta. Para ello, siga estos pasos:  
  
   1.  En Power BI Desktop, seleccione **Editar consultas**.  
  
   2.  En el panel de navegación de la izquierda del editor de consultas, en **Consultas**, seleccione la consulta de entidad **Cuenta** y luego **Editor avanzado** en la cinta de opciones.  
  
   3.  Desde la primera línea, que empieza con %3Cfetch y termina con fetch%3E, copie todo el Fetch XML codificado.  
  
   4.  El Fetch XML codificado que copia debe ser similar al siguiente:  
  
        %3Cfetch%20version%3D%221.0%22%20output-format%3D%22xml-platform%22%20mapping%3D%22logical%22%20distinct%3D%22true%22%3E%3Centity%20name%3D%22account%22%3E%3Cattribute%20name%3D%22territorycode%22%20%2F%3E%3Cattribute%20name%3D%22customersizecode%22%20%2F%3E%3Cattribute%20name%3D%22owningbusinessunit%22%20%2F%3E%3Cattribute%20name%3D%22ownerid%22%20%2F%3E%3Cattribute%20name%3D%22originatingleadid%22%20%2F%3E%3Cattribute%20name%3D%22revenue%22%20%2F%3E%3Cattribute%20name%3D%22sic%22%20%2F%3E%3Cattribute%20name%3D%22marketcap%22%20%2F%3E%20%3Cattribute%20name%3D%22parentaccountid%22%20%2F%3E%3Cattribute%20name%3D%22owninguser%22%20%2F%3E%3Cattribute%20name%3D%22accountcategorycode%22%20%2F%3E%3Cattribute%20name%3D%22marketcap_base%22%20%2F%3E%3Cattribute%20name%3D%22customertypecode%22%20%2F%3E%3Cattribute%20name%3D%22address1_postalcode%22%20%2F%3E%3Cattribute%20name%3D%22numberofemployees%22%20%2F%3E%3Cattribute%20name%3D%22accountratingcode%22%20%2F%3E%3Cattribute%20name%3D%22address1_longitude%22%20%2F%3E%3Cattribute%20name%3D%22revenue_base%22%20%2F%3E%3Cattribute%20name%3D%22createdon%22%20%2F%3E%3Cattribute%20name%3D%22name%22%20%2F%3E%3Cattribute%20name%3D%22address1_stateorprovince%22%20%2F%3E%3Cattribute%20name%3D%22territoryid%22%20%2F%3E%3Cattribute%20name%3D%22accountclassificationcode%22%20%2F%3E%3Cattribute%20name%3D%22businesstypecode%22%20%2F%3E%3Cattribute%20name%3D%22address1_country%22%20%2F%3E%3Cattribute%20name%3D%22accountid%22%20%2F%3E%3Cattribute%20name%3D%22address1_latitude%22%20%2F%3E%3Cattribute%20name%3D%22modifiedon%22%20%2F%3E%3Cattribute%20name%3D%22industrycode%22%20%2F%3E%3Clink-entity%20name%3D%22opportunity%22%20from%3D%22parentaccountid%22%20to%3D%22accountid%22%20alias%3D%22ab%22%3E%3Cfilter%20type%3D%22and%22%3E%3Ccondition%20attribute%3D%22opportunityid%22%20operator%3D%22not-null%22%20%2F%3E%3Ccondition%20attribute%3D%22modifiedon%22%20operator%3D%22last-x-days%22%20value%3D%22365%22%20%2F%3E%3C%2Ffilter%3E%3C%2Flink-entity%3E%3C%2Fentity%3E%3C%2Ffetch%3E  
  
2. Descodifique el Fetch XML codificado. Debe ser Fetch XML codificado válido y, una vez codificado, debe ser similar a esto:  
  
    \<fetch version="1.0" output-format="xml-platform" mapping="logical" distinct="true"> \<entity name="account"> \<attribute name="territorycode" /> \<attribute name="customersizecode" /> \<attribute name="owningbusinessunit" /> \<attribute name="ownerid" /> \<attribute name="originatingleadid" /> \<attribute name="revenue" /> \<attribute name="sic" /> \<attribute name="marketcap" />  \<attribute name="parentaccountid" /> \<attribute name="owninguser" /> \<attribute name="accountcategorycode" /> \<attribute name="marketcap_base" /> \<attribute name="customertypecode" /> \<attribute name="address1_postalcode" /> \<attribute name="numberofemployees" /> \<attribute name="accountratingcode" /> \<attribute name="address1_longitude" /> \<attribute name="revenue_base" /> \<attribute name="createdon" /> \<attribute name="name" /> \<attribute name="address1_stateorprovince" /> \<attribute name="territoryid" /> \<attribute name="accountclassificationcode" /> \<attribute name="businesstypecode" /> \<attribute name="address1_country" /> \<attribute name="accountid" /> \<attribute name="address1_latitude" /> \<attribute name="modifiedon" /> \<attribute name="industrycode" /> \<link-entity name="opportunity" from="parentaccountid" to="accountid" alias="ab"> \<filter type="and"> \<condition attribute="opportunityid" operator="not-null" /> \<condition attribute="modifiedon" operator="last-x-days" value="365" /> \</filter> \</link-entity> \</entity> \</fetch>  
  
   > [!TIP]
   >  Muchas herramientas de codificador y descodificador de dirección URL se encuentran gratis en la web.  
  
3. En el Fetch XML, agregue la entidad personalizada como nodo de atributo entre los nodos \<entity>. Por ejemplo, para agregar un campo personalizado llamado *customclassificationcode*, agregue el nodo después de otro nodo de atributo, como **industrycode**.  
  
   ```  
  
   <attribute name="industrycode" />  
   <attribute name=" customclassificationcode "/>  
   <link-entity name="opportunity" from="parentaccountid" to="accountid" alias="ab">  
   ```  
  
4. Cifre la dirección URL del Fetch XML actualizado. El Fetch XML que incluye el nuevo atributo personalizado se debe codificar y después usar para reemplazar la consulta existente de la fuente OData que se suministra con el paquete de contenido. Para ello, copie el FetchXML actualizado al portapapeles y péguelo en un codificador de dirección URL.  
  
5. Pegue la dirección URL del Fetch XML codificado en la fuente OData. Para ello, pegue la dirección URL codificada entre comillas después del texto **Query=[fetchXml=**, reemplazando el FetchXML codificado existente. Después seleccione **Hecho**.  
  
    El captura de pantalla siguiente indica donde se encuentran las comillas izquierdas.  
  
   ![Pegar dirección URL codificada en fuente OData](media/pbi-acct-encoded-url.PNG "Pegar dirección URL codificada en fuente OData")  
  
6. En el panel derecho, en **PASOS APLICADOS**, seleccione el botón de configuración ![Botón Configuración](media/mp-ua-r16-settings.png "Botón Configuración") junto a **Otras columnas quitadas**.  
  
7. La lista Elegir columnas muestra todos los campos para la entidad incluidos campos personalizados. Seleccione el campo personalizado, como *customclassificationcode*, que agregó a la consulta Fetch XML anterior y, a continuación seleccione **Aceptar**.  
  
   > [!NOTE]
   >  El nombre del campo que seleccione en el Selector de columna y el nombre de campo que agrega a la consulta de FetchXML deben coincidir.  
  
    Se actualizará la consulta de entidad y una columna se agrega en la tabla de entidad para el campo personalizado que seleccionó.  
  
8. Seleccione **Cerrar y cargar** en el editor de consultas.  
  
    El campo personalizado está ahora disponible en el panel derecho en **Campos** para la entidad y se puede agregar a informes nuevos o existentes.  
  
<a name="PBI_optionset_field"></a>   
## <a name="add-a-custom-option-set-field-to-a-report"></a>Agregar un campo de conjunto de opciones personalizado a un informe  
 Los campos de conjunto de opciones le permiten elegir entre varios valores. Ejemplos de campos de conjunto de opciones predefinidos son los campos Nivel de interés y Fase de ventas para una oportunidad. Imagine que tiene un campo de conjunto de opciones personalizado en el formulario de oportunidad principal que tiene los valores y las etiquetas siguientes.  
  
 ![Ejemplo de conjunto de opciones personalizado](media/pbi-custom-option-set-example.PNG "Ejemplo de conjunto de opciones personalizado")  
  
 Para agregar el campo de conjunto de opciones personalizado a un informe, siga estos pasos.  
  
1. Agregue la columna de campo personalizado.  
  
   -   En el panel de navegación de la izquierda del editor de consultas, en **Consultas**, seleccione la entidad que tiene el conjunto de opciones personalizado asociado, como la entidad *Oportunidad*.  
  
   -   En el panel derecho, en **PASOS APLICADOS**, seleccione el botón de configuración ![Botón Configuración](media/mp-ua-r16-settings.png "Botón Configuración") junto a **Otras columnas quitadas**.  
  
   -   La lista Elegir columnas muestra todos los campos para la entidad incluidos campos personalizados. Seleccione el campo personalizado, como *new_customoptionset* y a continuación seleccione **Aceptar**.  
  
   -   Seleccione **Guardar** y después cuando se le solicite, seleccione **Aplicar**.  
  
        La columna para el campo personalizado aparece en la tabla de entidad.  
  
2. Cree la consulta del conjunto de opciones.  
  
   1.  En Power BI Desktop, seleccione **Editar consultas**.  
  
   2.  En el panel de navegación de la izquierda del editor de consultas, en **Consultas**, seleccione la consulta en el grupo **Crear tablas** que tiene el campo de conjunto de opciones que es más similar al conjunto de opciones que desea agregar a un informe. Para este ejemplo, la consulta **SalesStageOptionSet** tiene cuatro opciones, por lo que es una buena opción.  
  
   3.  Seleccione **Editor avanzado**.  
  
        Se muestra la consulta del conjunto de opciones.  
  
   ![Crear una consulta del conjunto de opciones](media/pbi-makeoptionsetquery.png "Crear una consulta del conjunto de opciones")  
  
   4.  Copie la consulta completa en el Portapapeles. Puede pegarlo en un editor de texto, como Bloc de notas, para usar como referencia más tarde.  
  
   5.  En el editor de consultas, haga clic con el botón secundario en el grupo **Crear tablas**, seleccione **Nueva consulta**, y después seleccione **Consulta en blanco**.  
  
   6.  En el panel derecho, en **Nombre**, escriba un nombre, como *CustomOptionSet* y presione Entrar.  
  
   7.  Seleccione **Editor avanzado**.  
  
   8.  En el editor avanzado, pegue la consulta que copió antes.  
  
   9. Reemplace los valores y las opciones existentes con sus valores y opciones personalizados. En este ejemplo, cambie esto.  
  
       ```  
       let  
           Source = #table({"Value","Option"},{{0,"Qualify"},{1,"Develop"},{2,"Propose"},{3,"Close"}})  
       in  
           Source  
  
       ```  
  
        Por esto.  
  
       ```  
       let  
           Source = #table({"Value","Option"},{{0,"A"},{1,"B"},{2,"C"},{3,"D"},{4,"E"}})  
       in  
           Source  
  
       ```  
  
   10. Asegúrese de que no hay errores de sintaxis y después seleccione **Hecho** para cerrar el editor avanzado. La tabla de valores y de opciones aparece en el editor de consultas.  
  
   ![Nueva consulta de conjunto de opciones](media/pbi-optionsetquerycreated.png "Nueva consulta de conjunto de opciones")  
  
   11. Seleccione **Guardar** y después cuando se le solicite, seleccione **Aplicar**.  
  
3. Inserte una consulta de combinación para las tablas del conjunto de opciones de la entidad y personalizadas.  
  
   1.  En el panel izquierdo del editor de consultas, en **Entidades**, seleccione la entidad que incluye el conjunto de opciones personalizadas. Para este ejemplo, se selecciona la consulta de entidad **Oportunidad**.  
  
   2.  En la cinta de opciones seleccione **Consultas de combinación** y, cuando se le solicite insertar un paso, seleccione **Insertar**.  
  
   3.  En el diálogo Combinar, seleccione el encabezado de columna del conjunto de opciones personalizado, como *new_optionset*. En la lista desplegable, seleccione la consulta del conjunto de opciones correspondiente que creó anteriormente.  Cuando aparezca la tabla del conjunto de opciones, seleccione el encabezado de columna **Valor** para seleccionarlo.  
  
   ![Combinar selecciones de tabla](media/pbi-merge-tables.png "Combinar selecciones de tabla")  
  
   4.  Deje el tipo de unión como **Externa izquierda (todas desde la primera, coincidiendo desde la segunda)**, y después seleccione **Aceptar**.  
  
       > [!TIP]
       >  Cambie el nombre de la consulta de combinación. En **PASOS APLICADOS**, haga clic con el botón secundario en la consulta de combinación que ha creado, seleccione **Cambiar nombre** y especifique un nuevo nombre descriptivo, como *Merge CustomOptionSet*.  
  
4. Defina la columna de modo que solo las etiquetas se muestren.  
  
   1.  En el panel izquierdo del editor de consultas, en Entidades, seleccione la entidad que incluye el conjunto de opciones personalizadas. Para este ejemplo, se selecciona la consulta de entidad **Oportunidad**.  
  
   2.  En el panel derecho, en **PASOS APLICADOS**, seleccione una de las consultas ampliadas para revelar las columnas combinadas, como **Expanded SalesStage**.  
  
   3.  Busque y seleccione el encabezado de columna para la nueva columna que se creó como parte del paso de consulta de combinación anterior.  
  
   4.  En la pestaña **Transformación**, seleccione **Expandir**.  
  
   5.  En el diálogo de la nueva columna Expandir, borre la columna que corresponda a los valores (porque solo las etiquetas deben aparecer en la columna). Seleccione **Listo**.  
  
   ![Elija la columna que representa la etiqueta](media/pbi-expand-column.png "Elija la columna que representa la etiqueta")  
  
   6.  Seleccione **Guardar** y después cuando se le solicite, seleccione **Aplicar**.  
  
5. Cambie el nombre de columna para generación de informes.  
  
   1.  En el panel izquierdo del editor de consultas, en **Entidades**, seleccione la entidad que incluye el conjunto de opciones personalizadas. Para este ejemplo, se selecciona la consulta de entidad **Oportunidad**.  
  
   2.  Seleccione **Editor avanzado**.  
  
   3.  Agregue un elemento de línea de columna con el nombre cambiado, asegúrese de que no hay errores de sintaxis, y seleccione **Hecho**. En este ejemplo, el nombre de columna del conjunto de opciones personalizado que creó anteriormente es **NewColumn**, cuyo nombre se cambia a *Conjunto de opciones personalizado*.  
  
   ![Cambiar un nombre para mostrar en los informes](media/pbi-rename-column.png "Cambiar un nombre para mostrar en los informes")  
  
   4.  Seleccione **Guardar** y después cuando se le solicite, seleccione **Aplicar**.  
  
6. Seleccione **Cerrar y aplicar** para cerrar el editor de consultas.  
  
    El conjunto de opciones personalizado se puede utilizar ahora para crear informes de Power BI.  
  
<a name="BPI_increaserows"></a>   
## <a name="increase-the-number-of-rows-queried"></a>Aumentar el número de filas consultadas  
 De forma predeterminada, todas las consultas de entidad de Power BI en los paquetes de contenido no pueden exceder las 100.000 filas. Para aumentar el número de filas que pueden ser consultadas, siga estos pasos.  
  
> [!IMPORTANT]
>  Aumentar el límite de recuento de filas puede afectar significativamente al tiempo que se tarda en actualizar un informe. Además, el servicio Power BI tiene un límite de 30 minutos para ejecutar consultas. Tenga cuidado al aumentar el límite de recuento de filas.  
  
1. En Power BI Desktop, seleccione **Editar consultas**.  
  
2. En el panel de navegación de la izquierda del editor de consultas, en **Consultas**, seleccione la consulta de entidad cuyo límite de recuento de filas desea aumentar, como la entidad **Cliente potencial**.  
  
3. En el panel derecho, en **PASOS APLICADOS**, seleccione **Mantener primeras filas**.  
  
4. Aumente el número de filas filtradas. Por ejemplo para aumentar a 150.000, cambie Table.FirstN(#"Filtered Rows",100001) a Table.FirstN(#"Filtered Rows",150000)  
  
5. En el panel derecho, en **PASOS APLICADOS**, seleccione **Comprobar recuento de filas**.  
  
6. Localice la parte **>100.000** del paso.  
  
   ![Incrementar valor de recuento de filas](media/pbi-increaserowcount.png "Incrementar valor de recuento de filas")  
  
7. Aumente el valor a un número mayor, como *150.000*.  
  
8. Seleccione **Cerrar y cargar** en el editor de consultas.  
  
<a name="BPI_publish"></a>   
## <a name="publish-your-report-to-the-power-bi-service"></a>Publicar el informe al servicio de Power BI  
 Publique el informe para compartirlo en la organización y para que esté accesible desde cualquier lugar en casi cualquier dispositivo.  
  
1. En la cinta de opciones de la pestaña **Inicio** de la página principal de Power BI Desktop, seleccione **Publicar**.  
  
2. Si se le solicita iniciar sesión en el servicio de Power BI, seleccione **Iniciar sesión**.  
  
3. Si hay múltiples destinos disponibles, seleccione el que desee y, a continuación seleccione **Publicar**.  
  
### <a name="see-also"></a>Vea también  
 [Usar Power BI con Dynamics 365 Customer Engagement (on-premises)](use-power-bi.md)
