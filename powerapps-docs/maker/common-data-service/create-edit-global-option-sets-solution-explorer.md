---
title: Creación y edición de conjuntos de opciones globales para Common Data Service utilizando el explorador de soluciones | MicrosoftDocs
ms.custom: ''
ms.date: 05/26/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
ms.author: matp
manager: kvivek
author: Mattp123
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5fce8b9f693d56cd5f0955779152dbd7d8100378
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2757904"
---
# <a name="create-and-edit-global-option-sets-for-common-data-service-using-solution-explorer"></a>Creación y edición de conjuntos de opciones globales para Common Data Service utilizando el explorador de soluciones

El explorador de soluciones proporciona una forma de crear y editar conjuntos de opciones globales para Common Data Service.

El [portal de PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) permite configurar las opciones más comunes, pero algunas opciones solo se pueden configurar usando el explorador de soluciones. <br />Más información: 
- [Crear y editar conjuntos de opciones globales para Common Data Service](create-edit-global-option-sets.md)
- [Crear un conjunto de opciones](custom-picklists.md)

## <a name="open-solution-explorer"></a>Abra el explorador de soluciones

La parte del nombre de cualquier conjunto de opciones globales que cree es el prefijo de personalización. Esto se establece en función del editor de soluciones para la solución en la que trabaja. Si le interesa el prefijo de personalización, asegúrese de que está trabajando en una solución no administrada donde el prefijo de personalización es el que desea para este conjunto de opciones globales. Más información: [Cambiar el prefijo del editor de soluciones](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="view-global-option-sets"></a>Ver conjuntos de opciones globales

Con el explorador de soluciones abierto, en **Componentes** seleccione **Conjuntos de opciones**.

![Ver conjuntos de opciones globales](media/view-global-option-sets-solution-explorer.png)

> [!NOTE]
> Algunos conjuntos de opciones globales del sistema no se pueden personalizar. Estas opciones pueden cambiar con actualizaciones o nuevas versiones, por lo que le recomendamos que no los use a menos que esté seguro de que sus requisitos se alinean con la manera en que Common Data Service usa estos valores.

## <a name="create-a-global-option-set"></a>Creación de un conjunto de opciones global

> [!NOTE]
> No es necesario crear un conjunto de opciones global antes usarlo en un campo personalizado. Al crear un nuevo campo de conjunto de opciones tiene la opción de crear un nuevo conjunto de opciones global o usar uno existente. Vea [Opciones de campos Conjunto de opciones](create-edit-field-solution-explorer.md#option-set-field-options)

Mientras ve conjuntos de opciones globales, haga clic en **Nuevo** para abrir un formulario para definir el conjunto de opciones global.

![Crear conjunto de opciones global](media/create-global-option-set-solution-explorer.png)

Escriba un **Nombre para mostrar** que será visible para las personas con rol de administrador del sistema o personalizador que elegirán este conjunto de opciones global al definir los nuevos campos que lo usen. Este nombre no estará visible para las personas que usen sus aplicaciones.

Se generará un valor de campo **Nombre** en función del valor de **Nombre para mostrar** que escriba. Incluirá el prefijo de personalización del editor de soluciones en el contexto de la solución en la que está trabajando. Puede cambiar la parte generada del valor del campo **Nombre** antes de guardar.

Escribir una **Descripción** para el conjunto de opciones global. 

> [!TIP]
> Use la **Descripción** para explicar el objetivo de este conjunto de opciones global. Este valor no es visible para los usuarios de la aplicación, es para otras personas con rol de administrador del sistema o personalizador que quieran saber para qué se creó este conjunto de opciones global concreto.

### <a name="configure-options"></a>Configurar opciones

[!INCLUDE [cc_configure-option-set-options-solution-explorer](../../includes/cc_configure-option-set-options-solution-explorer.md)]

## <a name="edit-a-global-option-set"></a>Edición de un conjunto de opciones global

Mientras ve conjuntos de opciones globales, seleccione el conjunto de opciones que desea editar para abrir el panel para editarlo.

Con la excepción de cambiar el valor del campo **Nombre** o el **Valor** del número asignado a una opción, puede realizar cualquier de los cambios que puede al crear el conjunto de opciones global.

[!INCLUDE [cc_remove-option-warning](../../includes/cc_remove-option-warning.md)]

## <a name="delete-a-global-option-set"></a>Eliminar un conjunto de opciones global

Para eliminar un conjunto de opciones global, mientras ve la lista seleccione el ![comando Eliminar](media/delete.gif) comando en la barra de comandos.

> [!IMPORTANT]
> Si el conjunto de opciones global se ha usado para un campo, no podrá eliminarlo hasta que se elimine ese campo.
  
### <a name="see-also"></a>Vea también
 
[Crear y editar conjuntos de opciones globales para Common Data Service](create-edit-global-option-sets.md)<br />
[Crear un conjunto de opciones](custom-picklists.md)<br />
[Crear y editar campos](create-edit-fields.md)<br />
[Documentación para desarrolladores: Personalizar conjuntos de opciones globales](/dynamics365/customer-engagement/developer/org-service/customize-global-option-sets)
