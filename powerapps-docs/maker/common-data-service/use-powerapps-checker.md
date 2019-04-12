---
title: Usar comprobador de soluciones para validar sus aplicaciones en PowerApps | Microsoft Docs
description: Use el comprobador de soluciones para validar su solución.
author: Mattp123
manager: kvivek
ms.service: powerapps
ms.component: cds
ms.topic: article
ms.date: 03/20/2019
ms.author: matp
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="use-solution-checker-to-validate-your-model-driven-apps-in-powerapps"></a>Use el comprobador de soluciones para validar sus aplicaciones basadas en modelos en PowerApps

Para cumplir complejos requisitos de negocio, los fabricantes de aplicaciones basadas en modelos pueden terminar con frecuencia con soluciones muy avanzadas que personalizan y extienden la plataforma Common Data Service. Con implementaciones avanzadas aumenta el riesgo, pues se presentan problemas de rendimiento, estabilidad y fiabilidad que pueden afectar negativamente la experiencia de usuario. Identificar y comprender cómo resolver estos problemas puede ser complejo y laborioso. Con la característica del comprobador de soluciones puede realizar una completa verificación de análisis estático de sus soluciones con un conjunto de reglas de prácticas recomendadas e identificar rápidamente estos patrones problemáticos. Cuando la comprobación se completa, usted recibe un informe detallado que lista los problemas identificados, los componentes y el código afectados y vínculos a la documentación que describe cómo solucionar cada problema.

El comprobador de soluciones analiza estos componentes de la solución: 
- Complementos de Common Data Service
- Actividades personalizadas del flujo de trabajo de Common Data Service 
- Recursos web de Common Data Service (HTML y JavaScript)
- Configuraciones de Common Data Service, como pasos de mensaje del SDK 

El comprobador de soluciones trabaja con soluciones no administradas que se pueden exportar desde un entorno. 

> [!NOTE]
> El comprobador de soluciones no funciona con soluciones que contienen JavaScript que usa ECMAScript 6 (2015) o versioenes posteriores. Cuando se detecta JavaScript que usa una de estas versiones, se informará de un problema de la sintaxis JS001 para el recurso web.

## <a name="enable-the-solution-checker"></a>Habilitar el comprobador de soluciones
El comprobador de soluciones pasa a estar disponible en el área Soluciones de PowerApps después de instalar la solución del comprobador de PowerApps. Tenga en cuenta que no podrá encontrarla examinando o buscando en Microsoft AppSource. Para instalarlo, siga estos pasos:  

1. Inicie sesión en [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) y seleccione el entorno Common Data Service donde desea habilitar el comprobador de soluciones. 
2. En el panel de navegación izquierdo, seleccione **Soluciones**.
3. En la barra de herramientas, seleccione **Comprobador de soluciones** y después seleccione **Instalar** – esto abre la página de Microsoft AppSource. Debe permitir ventanas emergentes si el explorador bloquea la apertura de la página. 

   > [!div class="mx-imgBorder"]
   > ![Instalar el comprobador de soluciones](media/solution-checker-install.png "Instalar el comprobador de soluciones")

4. Seleccione **Prueba gratuita** en la página de AppSource. 


<!--from editor: Should it be "solution checker" rather than "checker solution" in the following step?

5. If you agree, accept the terms and conditions and select the environment to install the PowerApps checker solution. 
6. When the installation is complete, refresh the **Solution** list on the PowerApps site to verify that the solution checker is available.  
7. To check a solution, [Run the solution checker](#run-the-solution-checker).


<!-- ### Components created with the PowerApps checker
When you install the PowerApps checker these solution specific components are created. 
- Entities: The entities that are created are required to store the results of solution analysis and the status of analysis jobs in your environment.
   - Analysis Component
   - Analysis Job
   - Analysis Result
- System job: A system job is created so admins can remove solution analysis data from the environment. The job contains a configuration value, currently set to remove the solution analysis data after 60 days, which an administrator can override. 
- Security Roles: Two security roles, **Export Customizations**, and **Solution Checker** are created. These roles are required to export the solution for analysis, and storing the analysis results to the entities in your environment.
- User principle: The **PowerApps Advisor** user is created that allows the checker to authenticate with your Common Data Service environment and assign the two security roles, Export Customizations and Solution Checker. The PowerApps Advisor is an application user and does not consume a license.  -->

## <a name="run-the-solution-checker"></a>Ejecutar el comprobador de soluciones
Después de instalar el comprobador de PowerApps en el entorno, un elemento de menú **Comprobador de soluciones** está disponible cuando seleccione una solución no administrada en el área **Soluciones** de PowerApps. 

1. Iniciar sesión en [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc). 
2. En el panel izquierdo, seleccione **Soluciones**. 
3. Junto a la solución no administrada que desea analizar, seleccione **...**, señale a **Comprobador de soluciones** y, a continuación seleccione **Ejecutar**. 

   > [!div class="mx-imgBorder"]
   > ![Comando ejecutar comprobador de soluciones](media/solution-checker-run.png "Comando ejecutar comprobador de soluciones")

4.  El panel de estado situado en la parte superior derecha de la página **Soluciones** muestra **Comprobador de soluciones ejecutándose**. 

    > [!div class="mx-imgBorder"]
    > ![Estado del comprobador de soluciones](media/solution-checker-status.png "Estado del comprobador de soluciones")
   
    Tenga en cuenta lo siguiente:
    - El comprobador de soluciones puede tardar varios minutos en completar el análisis. 
    
    - Durante este tiempo observará el estado **Ejecutándose…** en la columna **Comprobación de solución** de la lista **Solución**. 
    
    - Usted recibirá un correo electrónico de notificación y una notificación en el área **Notificaciones** del sitio de PowerApps cuando finalice la comprobación.  

5.  [Vea el informe](#review-the-solution-checker-report) cuando finalice la comprobación.

## <a name="cancel-a-check"></a>Cancelar una comprobación

Después de enviar una comprobación de soluciones en el entorno, la comprobación se puede cancelar a través del panel de estado en el área superior derecha de la página **Soluciones**. 

Cuando usted cancela una comprobación, la comprobación de la solución deja de ejecutarse y la comprobación de la solución vuelve al estado anterior. 

## <a name="solution-checker-states"></a>Estados del comprobador de soluciones
Al instalar el comprobador de soluciones en el entorno, la columna **Comprobación de solución** pasa a estar disponible en la lista **Soluciones**. En esta columna se muestran los estados de análisis para una solución. 

|Estado  |Descripción  |
|---------|---------|
|No se ha ejecutado    | La solución no se ha analizado.        |
|En ejecución     | La solución se está analizando.       |
|No se pudo completar     |  El análisis de soluciones se ha solicitado pero no se ha completado correctamente.       |
|Resultados en la *fecha y hora*   | El análisis de soluciones se ha completado y los resultados están disponible para descarga.      |
|No se pudo completar. Resultado en la *fecha y hora*     | La última solicitud de análisis no se completó correctamente. Los últimos resultados correctos pueden descargarse.         |
|Comprobado por Microsoft     | Esta es una solución administrada de Microsoft. El análisis de soluciones no está permitido en estas soluciones.         |
|Comprobado por el editor     | Se trata de una solución administrada por terceros. Actualmente, los análisis de soluciones no está disponible para estas soluciones.        |


## <a name="review-the-solution-checker-report"></a>Revise el informe del comprobador de soluciones
Cuando se completa una comprobación de soluciones, el informe de análisis pasa a estar disponible para descarga desde el explorador web. El informe está en formato [!INCLUDE [pn-excel-short](../../includes/pn-excel-short.md)] y contiene varias visualizaciones y columnas que ayudan a identificar de impacto, tipo, y la ubicación de cada problema detectado en la solución. Un vínculo a orientación detallada sobre cómo resolver el problema también se proporciona. 

1. En el panel izquierdo, seleccione **Soluciones**.
2. Junto a la solución no administrada donde desea descargar el informe del comprobador de soluciones, seleccione **...**, señale a **Comprobador de soluciones** y, a continuación seleccione **Descargar últimos resultados**.  
3. El archivo zip del comprobador de soluciones se descarga en la carpeta especificada por el explorador web.

Este es un resumen de cada columna del informe.

|Campo del informe |Descripción  |Se aplica al componente   |
|---------|---------|---------|
|Problema     |   El título del problema identificado en la solución.      | Todo        |
|Categoría     | La clasificación del problema identificado, por ejemplo, **Rendimiento**, **Uso** o **Compatibilidad**.      |  Todo     |
|Gravedad     | Representa el impacto potencial del problema identificado. Los tipos de impacto disponibles son **Alto**, **Medio**, **Bajo** e **Informativo**.         |  Todo       |
|Instrucciones     |  Vínculo al artículo que detalla el problema, el impacto, y acción recomendada.       |  Todo       |
|Componente     |  El componente de soluciones donde se identificó el problema.        |   Todo      |
|Location     |  La ubicación y/o el archivo de origen del componente donde se produjo el problema que se ha identificado, como el ensamblado o el nombre de archivo JavaScript.        |  Todo       |
|Nº. de línea     |  La referencia de número de línea del problema en el componente del recurso web afectado.       |  Recursos web       |
|Módulo     | Nombre del módulo donde se detectó el problema identificado en el ensamblado.     |   Complemento o actividad de flujo de trabajo personalizada      |
|Escriba     | Tipo de problema identificado en el ensamblado.        | Complemento o actividad de flujo de trabajo personalizada        |
|Integrante     |  Miembro del problema identificado en el ensamblado.      | Complemento o actividad de flujo de trabajo personalizada        |
|Instrucción     | La instrucción de código o configuración produjo el problema.        |  Todo       |
|Comentarios     | Detalles acerca del problema que incluyen pasos de resolución de alto nivel.         |  Todo       |


## <a name="best-practice-rules-used-by-solution-checker"></a>Reglas de prácticas recomendadas usadas por el comprobador de soluciones

|Componente de la solución  |Nombre de regla  |Descripción de la regla  |
|---------|---------|---------|
|Complemento o actividad de flujo de trabajo   | [il-specify-column](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-specify-column&client=PAChecker&source=featuredocs)  | Evite seleccionar todas las columnas mediante API de consulta de Dynamics 365 for Customer Engagement.     |
|Complemento o actividad de flujo de trabajo   | [meta-remove-dup-reg](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-remove-dup-reg&client=PAChecker&source=featuredocs)     | Evite registros de complementos de Dynamics 365 for Customer Engagement duplicados.     |
|Complemento o actividad de flujo de trabajo   | [il-turn-off-keepalive](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-turn-off-keepalive&client=PAChecker&source=featuredocs)   | Establezca KeepAlive en false para interactuar con hosts externos en un complemento de Dynamics 365 for Customer Engagement.     |
|Complemento o actividad de flujo de trabajo   | [il-avoid-unpub-metadata](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-unpub-metadata&client=PAChecker&source=featuredocs)   | Evite recuperar metadatos de Dynamics 365 for Customer Engagement no publicados.     |
|Complemento o actividad de flujo de trabajo   | [il-avoid-batch-plugin](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-batch-plugin&client=PAChecker&source=featuredocs)   | Evite usar tipos de solicitud por lotes en complementos y actividades de flujo de trabajo de Dynamics 365 Customer Engagement.    |
|Complemento o actividad de flujo de trabajo   | [meta-avoid-reg-no-attribute](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-avoid-reg-no-attribute&client=PAChecker&source=featuredocs)  | Incluya atributos de filtro con registros de complementos de Dynamics 365 for Customer Engagement.    |
|Complemento o actividad de flujo de trabajo   | [meta-avoid-reg-retrieve](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-avoid-reg-retrieve&client=PAChecker&source=featuredocs)  | Tenga cuidado con complementos de Dynamics 365 for Customer Engagement registrados para mensajes de recuperación y de recuperación múltiple.    |
|Complemento o actividad de flujo de trabajo   | [meta-remove-inactive](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-remove-inactive&client=PAChecker&source=featuredocs)    | Quite configuraciones inactivas en Dynamics 365 for Customer Engagement.    |
|Complemento o actividad de flujo de trabajo   | [Evite usar window.top](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-window-top&client=PAChecker&source=featuredocs)   | Evite usar window.top.    |
|Complemento o actividad de flujo de trabajo   | [il-meta-avoid-crm2011-depr-message](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-crm2011-depr-message&client=PAChecker&source=featuredocs)  | No use mensajes obsoletos de Microsoft Dynamics CRM 2011.     |
|Complemento o actividad de flujo de trabajo   | [meta-avoid-crm4-event](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-avoid-crm4-event&client=PAChecker&source=featuredocs) | No use la fase de registro de complementos Microsoft Dynamics CRM 4.0.    |
|Complemento o actividad de flujo de trabajo   | [il-avoid-specialized-update-ops](http://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-specialized-update-ops&client=PAChecker&source=featuredocs)  | No use solicitudes de operaciones de actualización especializadas en Dynamics 365 for Customer Engagement.        |
|Recursos web  | [web-use-async](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-async&client=PAChecker&source=featuredocs)  |  Interactúe con recursos HTTP y HTTPS forma asincrónica.   |
|Recursos web  | [meta-remove-invalid-form-handler](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-remove-invalid-form-handler&client=PAChecker&source=featuredocs)  | Corrija o quite registros de eventos de formularios de Dynamics 365 for Customer Engagement no válidos.   |
|Recursos web  | [meta-remove-orphaned-form-element](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-remove-orphaned-form-element&client=PAChecker&source=featuredocs)  | Corrija o quite registros de eventos de formularios de Dynamics 365 for Customer Engagement huérfanos.   |
|Recursos web  | [web-avoid-modals](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-modals&client=PAChecker&source=featuredocs)  | Evite el uso de diálogos modales.   |
|Recursos web  | [web-avoid-crm2011-service-odata](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-crm2011-service-odata&client=PAChecker&source=featuredocs)   | No se dirija al extremo de Microsoft Dynamics CRM 2011 OData 2.0.     |
|Recursos web  | [web-avoid-crm2011-service-soap](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-crm2011-service-soap&client=PAChecker&source=featuredocs)  | No se dirija a los servicios de Microsoft Dynamics CRM 2011 SOAP.   |
|Recursos web  | [web-avoid-browser-specific-api](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-browser-specific-api&client=PAChecker&source=featuredocs) | No use complementos del explorador o API heredados de Internet Explorer.   |
|Recursos web  | [web-avoid-2011-api](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-2011-api&client=PAChecker&source=featuredocs)  | No use el modelo de objetos de Microsoft Dynamics CRM 2011 en desuso.  |
|Recursos web  | [web-use-relative-uri](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-relative-uri&client=PAChecker&source=featuredocs)   | No use las direcciones URL absoutas del extremo de Common Data Service.    |
|Recursos web  | [web-use-client-context](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-client-context&client=PAChecker&source=featuredocs)  | Use contextos del cliente.   |
|Recursos web  | [web-use-dialog-api-param](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-dialog-api-param&client=PAChecker&source=featuredocs)   | Usar parámetros API de diálogo.   |
|Recursos web  | [web-use-org-setting](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-org-setting&client=PAChecker&source=featuredocs)   | Use configuración de organización.   |
|Recursos web  | [web-use-grid-api](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-use-grid-api&client=PAChecker&source=featuredocs)   | Use las API de cuadrícula.    |
|Recursos web  | [web-avoid-isActivityType](http://go.microsoft.com/fwlink/?LinkID=398563&error=web-avoid-isActivityType&client=PAChecker&source=featuredocs)   | Reemplace el método Xrm.Utility.isActivityType por el nuevo Xrm.Utility.getEntityMetadata y no lo utilice en reglas de cinta de opciones.    |
|Recursos web  | [meta-avoid-silverlight](http://go.microsoft.com/fwlink/?LinkID=398563&error=meta-avoid-silverlight&client=PAChecker&source=featuredocs)   | El uso del recurso web de Silverlight ha quedado obsoleto.   |


## <a name="see-also"></a>Vea también
[Prácticas recomendadas e instrucciones para Common Data Service](../../developer/common-data-service/best-practices/index.md)<br />
[Prácticas recomendadas e instrucciones para aplicaciones basadas en modelos](../../developer/model-driven-apps/best-practices/index.md)<br />
[Problemas y soluciones comunes para el Comprobador de soluciones](common-issues-resolutions-solution-checker.md)<br />
