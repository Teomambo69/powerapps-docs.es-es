---
title: Asignar campos de entidad en Power Apps | MicrosoftDocs
description: Aprenda cómo asignar campos de entidad
ms.custom: ''
ms.date: 05/29/2018
ms.reviewer: ''
ms.service: powerapps
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
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: a5da8b9ecfb2bbba2a4e03fbc0d28301c41e2a7c
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "2860915"
---
# <a name="map-entity-fields"></a>Asignar campos de entidad
 
Puede asignar atributos entre entidades que tienen una relación de entidad. Esto le permite establecer valores predeterminados para un registro creado en el contexto de otro registro. 

## <a name="easier-way-to-create-new-records-in-model-driven-apps"></a>Una forma más fácil de crear nuevos registros en aplicaciones controladas por modelos

Supongamos que los usuarios desean agregar un nuevo registro de contacto para una persona que es un empleado de una cuenta específica. Pueden hacerlo de dos maneras distintas:  
  
### <a name="the-hard-way"></a>La forma complicada

Pueden navegar simplemente a la aplicación para crear un nuevo registro de contacto desde cero. No obstante, luego deberán establecer la cuenta primaria y especificar varios elementos de información (como información de dirección y número de teléfono) que probablemente coincidirán con los de la cuenta primaria. Esto puede resultar largo y presenta posibilidad de errores.  
  
### <a name="the-easier-way"></a>La forma más fácil

La forma más sencilla es empezar con la entidad de cuenta y, mediante la subcuadrícula **Contactos** del formulario, seleccionar **+** para agregar un contacto. Primero guiará a los usuarios a buscar un contacto relacionado existente para que no creen accidentalmente un registro duplicado. Si no encuentran un registro existente, pueden seleccionar **Nuevo** y crear un nuevo registro de contacto. 

El nuevo formulario de registro de contacto incluirá cualquiera de los valores de atributo asignados de la cuenta (como información de dirección y de teléfono) como los valores predeterminados. Los usuarios pueden editar estos valores antes de guardar el registro.

## <a name="how-this-works"></a>Cómo funciona

Cuando asigna campos de entidad para una relación de entidad 1:N, algunos datos del registro de entidad principal se copiarán en el nuevo formulario de la entidad relacionada para definir los valores predeterminados que los usuarios pueden editar antes de guardar.
 
  
> [!NOTE]
> Estas asignaciones solo establecen los valores predeterminados en un registro antes de guardarlo. Los usuarios pueden modificar los valores antes de guardarlos. Los datos se transfieren son los datos en ese momento. No se sincroniza si cambian los datos de origen más adelante.
>   
> Estas asignaciones no se aplican a los registros relacionados creados mediante un flujo de trabajo o un proceso de diálogo. No se aplican automáticamente a los nuevos registros creados mediante código, aunque los desarrolladores pueden usar un mensaje especial llamado `InitializeFrom` ([Función InitializeFrom](/dynamics365/customer-engagement/web-api/initializefrom?view=dynamics-ce-odata-9) o [Clase InitializeFromRequest](/dotnet/api/microsoft.crm.sdk.messages.initializefromrequest?view=dynamics-general-ce-9)) para crear un nuevo registro mediante las asignaciones disponibles.  

## <a name="open-solution-explorer"></a>Abra el explorador de soluciones

La única forma de asignar campos de una entidad es usar el explorador de soluciones.

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]
  
La asignación de campos se realiza en el contexto de una relación de entidad 1:N o N:1, de modo que primero debe [ver las relaciones de entidad 1:N o N:1](create-edit-1n-relationships-solution-explorer.md#view-entity-relationships).

## <a name="view-mappable-fields"></a>Ver los campos que se pueden asignar

Las asignaciones de campos no se definen realmente dentro de las relaciones de entidad, sino que se muestran en la interfaz de usuario de la relación. No todas las relaciones de entidad de 1:N los tienen. Al ver una lista de relaciones de entidad de 1:N (o N:1), puede filtrar las relaciones mostradas por tipo. Puede seleccionar **Todo**, **Personalizado**, **Personalizable** o **Se puede asignar**. Las relaciones entre entidades que se pueden asignar proporcionan acceso para permitir la asignación de campos de entidad. 

![Ver relaciones entre entidades que se pueden asignar](media/mappable-entity-relationships.png) 

Al abrir una relación de entidad que se puede asignar, seleccione **Asignaciones** en la navegación izquierda.

![Seleccionar asignaciones para la relación de la entidad](media/map-entity-fields-ui-solution-explorer.png)

## <a name="delete-mappings"></a>Eliminar asignaciones

Si existen asignaciones que no desea que se apliquen, puede seleccionarlas y hacer clic en el icono de ![eliminación](media/delete.gif) icono.

## <a name="add-new-mappings"></a>Agregar nuevas asignaciones

Para crear una nueva asignación, en la barra de herramientas haga clic en **Nuevo**. Se abrirá el cuadro de diálogo **Crear asignación de campos**.

![Cuadro de diálogo Crear asignación de campos](media/create-field-mapping-dialog.png)

Seleccione un campo de entidad de origen y campos de una entidad de destino con los valores que desee asignar. 

![Configurar la asignación de campos](media/configure-field-mapping.png)

A continuación, seleccione **Aceptar** para cerrar el cuadro diálogo.

Las siguientes reglas muestran qué tipos de datos se pueden asignar.  
  
- Los dos campos deben ser del mismo tipo y del mismo formato.  
- La longitud del campo de destino debe ser igual o mayor que la longitud del campo de origen.  
- El campo de destino no puede estar asignado a otro campo.  
- El campo de origen debe estar visible en el formulario.  
- El campo de destino debe ser un campo en el que un usuario pueda especificar datos.  
- Los valores de identificador de dirección no se pueden asignar.
- Si realiza asignaciones a un campo (o desde este) que no aparece en un formulario, la asignación no se efectuará hasta que se agregue el campo a un formulario.
- Si los campos son conjuntos de opciones, los valores enteros de cada opción deben ser idénticos.  
  
> [!NOTE]
>  Si necesita asignar campos de conjunto de opciones, se recomienda configurar ambos campos para que usen el mismo conjunto de opciones globales. Si no, puede resultar difícil mantener dos conjuntos de opciones separados sincronizadas manualmente. Si los valores enteros de cada opción no se asignan correctamente puede experimentar problemas con los datos. Más información: [Creación y edición de conjuntos de opciones globales para Common Data Service (listas desplegables)](create-edit-global-option-sets.md)  
  
## <a name="automatically-generate-field-mappings"></a>Generar asignaciones de campos automáticamente  

También puede generar asignaciones automáticamente seleccionando **Generar asignaciones** en el menú **Más acciones**.

Debe prestar atención al hacerlo con entidades del sistema. Use esta opción cuando cree entidades personalizadas y desee aprovechar la asignación. 

> [!WARNING]
> Esto quita cualquier asignación existente y la reemplaza con asignaciones sugeridas que se basan únicamente en los campos con nombres y tipos de datos similares. Si usa esto en una entidad del sistema, podría perder algunas asignaciones esperadas. Para las entidades personalizadas, ayuda a ahorrar tiempo porque puede eliminar más fácilmente las asignaciones que no desea y agregar otras que la acción de generar asignaciones no ha creado.  


## <a name="publish-customizations"></a>Publicación de personalizaciones 

Puesto que las asignaciones de campos no son metadatos, debe publicarlas para que los cambios surtan efecto. 
<!-- TODO Need a general topic about publishing to link to in situations like this -->

### <a name="see-also"></a>Vea también
[Creación y edición de relaciones entre entidades 1:N (uno a varios) o N:1 (varios a uno) con el explorador de soluciones](create-edit-1n-relationships-solution-explorer.md)<br />
[Documentación para desarrolladores: Personalizar asignaciones de atributos y entidades](/dynamics365/customer-engagement/developer/customize-entity-attribute-mappings)<br />
[Documentación para desarrolladores: API web para crear una nueva entidad desde otra entidad](/dynamics365/customer-engagement/developer/webapi/create-entity-web-api#create-a-new-entity-from-another-entity)
