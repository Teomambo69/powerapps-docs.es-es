---
title: Asignar campos de entidad en PowerApps| Microsoft Docs
description: Obtenga información sobre cómo asignar campos de entidad
ms.custom: ''
ms.date: 05/29/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 7c5aa1c3-bde9-43f1-a369-fdcdbf14dec0
caps.latest.revision: 33
ms.author: matp
manager: kvivek
tags: ''
ms.openlocfilehash: 7e84e10a824ea218063cb2dccdc15ed7ae2340da
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39711626"
---
# <a name="map-entity-fields"></a>Asignar campos de entidad
 
Puede asignar atributos entre las entidades que tienen una relación de entidad. Esto le permitirá establecer valores predeterminados para un registro que se cree en el contexto de otro registro. 

## <a name="easier-way-to-create-new-records-in-model-driven-apps"></a>Modo más sencillo de crear nuevos registros en aplicaciones controladas por modelos

Supongamos que se quiere agregar un nuevo registro de contacto para alguien que es empleado de una cuenta específica. Puede hacerlo de dos formas distintas:  
  
### <a name="the-hard-way"></a>La forma difícil

Se podría simplemente navegar en la aplicación para crear un nuevo registro de contacto desde cero. A continuación, sin embargo, hay que establecer la cuenta principal y escribir varios elementos de información (como la información relativa a la dirección y el teléfono), los cuales son probablemente los mismos que la cuenta principal. Esto puede llevar mucho tiempo y presenta oportunidades para que se produzcan errores.  
  
### <a name="the-easier-way"></a>La forma más fácil

La forma más fácil consiste en empezar con esta entidad de cuenta y, mediante la subcuadrícula **Contactos** del formulario, seleccione **+** para agregar un contacto. Primero hará de guía para que se busque cualquier contacto relacionado existente a fin de que no se cree accidentalmente un registro duplicado. Si no se encuentra un registro existente, se puede seleccionar **Nuevo** y crear un nuevo registro de contacto. 

El nuevo formulario de registro de contacto incluirá cualquiera de los valores de atributo asignados de la cuenta (como la información relativa a la dirección y el teléfono) como valores predeterminados. Se pueden editar estos valores antes de que se guarde el registro.

## <a name="how-this-works"></a>Cómo funciona esto

Al asignar campos de entidad para una relación de entidad 1:N, determinados elementos de datos del registro de entidad principal se copiarán en el nuevo formulario de entidad relacionada para establecer valores predeterminados que se pueden editar antes de guardarlos.
 
  
> [!NOTE]
> Estas asignaciones solo establecen valores predeterminados en un registro antes de guardarlo. Se pueden editar los valores antes de guardarlos. Los datos que se transfieren son los datos de ese momento. No se sincroniza si los datos de origen cambian posteriormente.
>   
> Estas asignaciones no se aplican a los registros relacionados creados mediante un proceso del cuadro de diálogo o flujo de trabajo. No se aplican automáticamente a los nuevos registros creados mediante código, aunque los desarrolladores pueden usar un mensaje especial llamado `InitializeFrom` ([función InitializeFrom](/dynamics365/customer-engagement/web-api/initializefrom?view=dynamics-ce-odata-9) o [clase InitializeFromRequest](/dotnet/api/microsoft.crm.sdk.messages.initializefromrequest?view=dynamics-general-ce-9)) para crear un nuevo registro mediante las asignaciones disponibles.  

## <a name="open-solution-explorer"></a>Abrir el Explorador de soluciones

La única forma de asignar campos de entidad consiste en usar el Explorador de soluciones.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]
  
La asignación de campos se realiza en el contexto de una relación de entidad 1:N o N:1, por lo que primero debe [ver relaciones de entidad 1:N o N:1](create-edit-1n-relationships-solution-explorer.md#view-entity-relationships).

## <a name="view-mappable-fields"></a>Ver campos asignables

Las asignaciones de campos no se definen realmente en las relaciones de entidad, pero se exponen en la interfaz de usuario de la relación. No todas las relaciones de entidad 1:N las tienen. Si ve una lista de relaciones de entidad 1:N (o N:1) para una entidad, puede filtrar las relaciones mostradas por tipo. Puede seleccionar **Todo**, **Personalizado**, **Personalizable** o **Asignable**. Las relaciones de entidad asignables proporcionan acceso para permitir la asignación de campos de entidad. 

![Ver relaciones de entidad asignables](media/mappable-entity-relationships.png) 

Al abrir una relación de entidad asignable, seleccione **Asignaciones** en la barra de navegación izquierda.

![Seleccionar Asignaciones para la relación de entidad](media/map-entity-fields-ui-solution-explorer.png)

## <a name="delete-mappings"></a>Eliminar asignaciones

Si hay alguna asignación que no desea aplicar, puede seleccionarla y hacer clic en el ![Icono de eliminación](media/delete.gif) .

## <a name="add-new-mappings"></a>Agregar nuevas asignaciones

Para crear una nueva asignación, haga clic en **Nuevo** en la barra de herramientas. Esto abrirá el cuadro de diálogo **Crear asignación de campos**.

![Crear cuadro de diálogo Crear asignación de campos](media/create-field-mapping-dialog.png)

Seleccione un campo de entidad de origen y un campo de entidad de destino con los valores que desea asignar. 

![Configurar asignación de campos](media/configure-field-mapping.png)

A continuación, seleccione **Aceptar** para cerrar el cuadro de diálogo.

Las siguientes reglas muestran qué tipos de datos se pueden asignar.  
  
- Ambos campos deben ser del mismo tipo y el mismo formato.  
- La longitud del campo de destino debe ser igual o superior a la longitud del campo de origen.  
- El campo de destino no se puede asignar a otro campo todavía.  
- El campo de origen debe ser visible en el formulario.  
- El campo de destino debe ser un campo en el que un usuario pueda escribir datos.  
- Los valores de id. de dirección no se pueden asignar.
- Si asigna a o desde un campo que no se muestra en un formulario, la asignación no se realizará hasta que se agregue el campo a un formulario.
- Si los campos son conjuntos de opciones, los valores enteros de cada opción deben ser idénticos.  
  
> [!NOTE]
>  Si tiene que asignar campos de conjuntos de opciones, recomendamos que configure ambos campos para usar el mismo conjunto de opciones global. De lo contrario, puede resultar difícil mantener dos conjuntos independientes de opciones sincronizadas manualmente. Si los valores enteros de cada opción no se asignan correctamente, puede generar problemas en sus datos. Más información: [Crear y editar conjuntos de opciones globales de Common Data Service para aplicaciones (listas desplegables)](create-edit-global-option-sets.md)  
  
## <a name="automatically-generate-field-mappings"></a>Generar asignaciones de campos automáticamente  

También puede generar asignaciones automáticamente seleccionando **Generar asignaciones** en el menú **Más acciones**.

Debe tener cuidado al hacer esto con entidades del sistema. Use esto al crear entidades personalizadas y cuando desee aprovechar la asignación. 

> [!WARNING]
> De este modo, se quitarán las asignaciones existentes, las cuales se reemplazarán por asignaciones recomendadas basadas solo en los campos con tipos de datos y nombres similares. Si usa esto en una entidad del sistema, podría perder algunas asignaciones previstas. En las entidades personalizadas, ayuda a ahorrar tiempo, ya que puede eliminar con mayor facilidad las asignaciones que no desea y agregar otras que la acción de generación de asignaciones no creó.  


## <a name="publish-customizations"></a>Publicar personalizaciones 

Dado que las asignaciones de campos no son metadatos, debe publicarlas antes de que se apliquen los cambios. 
<!-- TODO Need a general topic about publishing to link to in situations like this -->

### <a name="see-also"></a>Vea también
[Create and edit 1:N (one-to-many) or N:1 (many-to-one) entity relationships using solution explorer](create-edit-1n-relationships-solution-explorer.md) (Crear y editar relaciones de entidad 1:N (uno a varios) o N:1 (varios a uno) mediante el Explorador de soluciones)<br />
[Developer Documentation: Customize entity and attribute mappings](/dynamics365/customer-engagement/developer/customize-entity-attribute-mappings) (Documentación para desarrolladores: personalizar asignaciones de atributos y entidades)<br />
[Developer Documentation: Web API Create a new entity from another entity](/dynamics365/customer-engagement/developer/webapi/create-entity-web-api#create-a-new-entity-from-another-entity) (Documentación para desarrolladores: API web: crear una entidad a partir de otra entidad)
