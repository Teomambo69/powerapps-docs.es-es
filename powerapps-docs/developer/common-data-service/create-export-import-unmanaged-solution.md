---
title: 'Crear, exportar, o importar una solución no administrada (Common Data Service para aplicaciones) | Microsoft Docs'
description: Una solución no administrada es útil como método para agrupar un conjunto de personalizaciones no administradas en un conjunto que se puede transportar entre las organizaciones
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
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
---
# <a name="create-export-or-import-an-unmanaged-solution"></a>Crear, exportar o importar una solución no administrada

Además de ser un requisito previo para crear una solución administrada, una solución no administrada es útil como método para agrupar un conjunto de personalizaciones no administradas en un conjunto que se puede transportar entre las organizaciones.  

 Más información: [Usar soluciones para las personalizaciones](/dynamics365/customer-engagement/developer/customize/use-solutions-for-your-customizations).  

<a name="BKMK_CreateUnmanagedSolution"></a> 

## <a name="create-an-unmanaged-solution"></a>Creación de una solución no administrada  
 Cada solución necesita un editor. Si no se piensa distribuir la solución, se puede usar el editor predeterminado creado para la organización. Para obtener información sobre cómo crear un editor de soluciones, consulte [Crear un editor de soluciones](create-export-import-unmanaged-solution.md#BKMK_CreateSolutionPublisher).  

 La siguiente tabla enumera los campos y descripciones que contiene una solución.  


|      Etiqueta de campo       |                                                                                                                                                              Descripción                                                                                                                                                               |
|------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    **Nombre para mostrar**    |                                                                                                                                                       El nombre de la solución.                                                                                                                                                       |
|        **Nombre**        |                                     Common Data Service para aplicaciones genera un nombre único basado en el **Nombre**. Puede editar el nombre exclusivo. El nombre exclusivo solo puede contener caracteres alfanuméricos o el carácter de subrayado.                                     |
|     **Editor**      |                                                                                                                                Use la búsqueda **Editor** para asociar la solución con un editor.                                                                                                                                |
|      **Versión**       |                                                                                                                     Especifique una versión con el siguiente formato: principal.secundaria.compilación.revisión (por ejemplo, 1.0.0.0).                                                                                                                     |
| **Página de configuración** | Si incluye un recurso web HTML en la solución, puede usar esta búsqueda para agregarlo como su página de configuración designada.<br /><br /> Más información: [Use la página de configuración de la solución](create-export-import-unmanaged-solution.md#BKMK_UseSolutionConfigurationPage) |
|    **Descripción**     |                                                                                                                                  Use este campo para incluir todos los detalles relevantes sobre la solución.                                                                                                                                   |

 Después de crear una solución no administrada puede agregar componentes de solución creándolos en el contexto de esta solución o agregando componentes existentes de otras soluciones. Para obtener información sobre cómo crear una solución mediante programación, consulte [Crear una solución](work-solutions.md#BKMK_CreateASolution)  

<a name="BKMK_CreateSolutionPublisher"></a>   

### <a name="create-a-solution-publisher"></a>Crear un editor de soluciones  
 Si desea distribuir soluciones administradas, debe crear un `Publisher`. La siguiente tabla enumera los campos las y descripciones que contiene un `Publisher`.  


|          Etiqueta          |                                                                                                                                                                                                       Descripción                                                                                                                                                                                                        |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    **Nombre para mostrar**     |                                                                                                                                                                       El nombre que se mostrará en el campo de búsqueda **Editor** de la solución.                                                                                                                                                                        |
|        **Nombre**         |                               CDS for Apps genera un nombre exclusivo basado en el **Nombre**. El nombre único solo puede contener caracteres alfanuméricos y el carácter de subrayado. **Nota:**  Puede utilizar el `Unique Name` para identificar de forma exclusiva un `Publisher`. Las soluciones administradas que comparten el mismo editor pueden actualizarse entre ellas.                               |
|     **Descripción**     |                                                                                                                                                                           Use este campo para incluir todos los detalles relevantes sobre la solución.                                                                                                                                                                            |
|       **Prefijo**        |                   El prefijo de personalización ayuda a identificar qué editor ha agregado un componente de la solución. Por ejemplo, el prefijo se agrega al nombre lógico de cualquier entidad o atributo creado en el contexto de una solución asociada con este editor. El prefijo debe tener entre dos y ocho caracteres, y solo puede contener caracteres alfanuméricos. No puede comenzar por 'mscrm'.                   |
| **Prefijo de valor de opción** | Esta opción le ayuda a separar opciones que agrega a conjuntos de opciones para admitir la combinación de opciones. Un valor se genera automáticamente en función del texto **Prefijo** para hacerlo más exclusivo. El valor debe estar entre 10.000 y 99.999.<br /><br /> Más información: [Combinación de las opciones del conjunto de opciones](/dynamics365/customer-engagement/developer/understand-managed-solutions-merged#BKMK_MergingOptionSetOptions) |
|   **Detalles del contacto**   |                                                                                                                                                           Use estos campos para agregar información que permitirá a las personas que instalan la solución ponerse en contacto con usted.                                                                                                                                                           |

 Para obtener información sobre cómo crear un editor mediante programación, consulte [Crear un editor](work-solutions.md#BKMK_CreatePublisher).  

<a name="BKMK_UseSolutionConfigurationPage"></a>   
### <a name="use-the-solution-configuration-page"></a>Use la página de configuración de la solución  
 La página de configuración de la solución proporciona un lienzo que puede usar para mostrar información o para permitir a los clientes realizar acciones en el contexto de la solución. Establezca la página de configuración con el campo de búsqueda **Página de configuración** para seleccionar un recurso Web de la página web (HTML) incluido en la solución. Esto hará que un nuevo nodo **Configuración** aparezca en la ventana de la solución debajo del nodo **Información** y sobre el nodo **Componentes**. El nodo **Configuración** mostrará el recurso web que establezca.  

 Puede usar la página de configuración de la solución para mostrar los controles que configurarán la solución. Por ejemplo, puede ofrecer algunas entidades en la solución que controlen su comportamiento. Con la API web para acceder a los datos, puede ofrecer controles personalizados en la página de recursos web para actualizar datos en estas entidades.  

<a name="BKMK_UnmanagedSolution"></a>   
## <a name="export-an-unmanaged-solution"></a>Exportar una solución no administrada  
 Es posible que desee exportar una solución no administrada en las situaciones siguientes:  

- Tiene que modificar determinado contenido XML en el archivo customizations.xml, por ejemplo, puede que quiera editar el mapa del sitio o crear cintas personalizadas.  

- Desea transportar su solución no administrada de una organización a otra.  

- Desea crear una copia de seguridad del conjunto actual de personalizaciones.  

  Exportar una solución no administrada creará un archivo comprimido (zip) que se puede luego importar a otra organización o a la misma organización.  

  Solo las personalizaciones publicadas se incluyen cuando se exporta una solución para asegurar que se publican los cambios antes de exportarla.  

  Cuando se exporta una solución con la aplicación web, si la solución contiene cualquier componente necesario que falta, verá el paso **Faltan componentes necesarios**. Puede ignorar esta advertencia solo si tiene previsto volver a realizar la importación como una solución no administrada en la organización original. De lo contrario, siga las instrucciones del cuadro de diálogo para cancelar la exportación y agregar los componentes necesarios.  

  Use el mensaje <xref:Microsoft.Crm.Sdk.Messages.ExportSolutionRequest> para exportar una solución mediante programación. Más información: [Exportar o empaquetar una solución](work-solutions.md#BKMK_ExportPackageSolution)  

  Cuando se exporta una solución con la aplicación web, en el paso **Exportar configuración del sistema (avanzado)**, puede elegir qué configuración del sistema incluir en la solución. Estas opciones están disponibles para programadores mediante <xref:Microsoft.Crm.Sdk.Messages.ExportSolutionRequest> a través de los miembros disponibles en la solicitud. Vea los comentarios para la solicitud para obtener más información acerca de qué configuración se incluye.  

  <!--You can pick a target version when you export a solution. You can export a solution that is compliant with earlier versions. More information: [Export a solution for a specific Dynamics 365 version](export-solution-specific-version.md).-->  

<a name="BKMK_ImportUnmanagedSolution"></a>   
## <a name="import-an-unmanaged-solution"></a>Importar una solución no administrada  
 Debe importar una solución no administrada en las situaciones siguientes:  

- Desea transportar un conjunto de personalizaciones desde una organización a otra y desea permitir el cambio de los componentes de la solución.  

- Desea restaurar o revertir a un conjunto anterior de definiciones de los componentes de la solución.  

  Importar una solución no administrada es un proceso aditivo. Cuando se importa una versión anterior de una solución administrada no se quitan los componentes de la solución incluidos en una versión más reciente. Sin embargo, la definición de las propiedades de componentes de la solución se sobrescribirá con la definición incluida en la última solución no administrada que importe.  

> [!IMPORTANT]
>  Los cambios que se aplican importando una solución no administrada no se pueden deshacer. No instale una solución no administrada si desea revertir los cambios.  

 Esta operación se realiza mediante programación usando el mensaje de <xref:Microsoft.Crm.Sdk.Messages.ImportSolutionRequest>. Puede escribir código para ejecutar este mensaje asincrónicamente. Más información: [Ejecutar mensajes en segundo plano (asincrónicamente)](/dynamics365/customer-engagement/developer/org-service/use-messages-request-response-classes-execute-method#bkmk_executeasync). Puede realizar un seguimiento del progreso de la importación o generar un informe del éxito de la importación mediante la entidad `ImportJob`. Más información: [Instalar o actualizar una solución](work-solutions.md#BKMK_InstallUpgradeSolution).  

> [!IMPORTANT]
>  La instalación de una solución o la publicación de personalizaciones puede interferir en el funcionamiento normal del sistema. Se recomienda programar importaciones de la solución cuando menos afecte a los usuarios.  

<a name="BKMK_MaxSizeOfSolution"></a>   
### <a name="maximum-size-of-solution-to-import"></a>Tamaño máximo de la solución que se va a importar  
 Para CDS for Apps el tamaño máximo de una solución es 29,296 MB.  

 Para organizaciones locales, el tamaño máximo predeterminado para una solución es 6 MB, pero esto se puede aumentar según sea necesario.  

 Cambie el tamaño máximo permitido modificando el elemento [\<httpRuntime>](https://msdn.microsoft.com/library/e1f13641\(v=vs.100\).aspx) del archivo web.config para la aplicación. Modifique los atributos de `executionTimeout` y de `maxRequestLength` para permitir el tamaño necesario. Cuando termine de instalar la solución puede establecerla en el tamaño que desee.  

### <a name="see-also"></a>Vea también  
 [Planear el desarrollo de la solución](/dynamics365/customer-engagement/developer/plan-solution-development)   
 [Empaquetar y distribuir extensiones con soluciones de Dynamics 365](/dynamics365/customer-engagement/developer/package-distribute-extensions-use-solutions)   
 [Esquema de archivo de soluciones de personalización](/dynamics365/customer-engagement/developer/customize-dev/customization-solutions-file-schema)   
 [Crear, instalar y actualizar una solución administrada](create-install-update-managed-solution.md)   
 [Desinstalar o eliminar una solución](uninstall-delete-solution.md)
