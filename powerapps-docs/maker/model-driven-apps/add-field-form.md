---
title: Agregar un campo a un formulario de aplicación controlada por modelos en Power Apps | MicrosoftDocs
ms.custom: ''
ms.date: 05/04/2020
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
author: Mattp123
ms.assetid: 29499887-6e7b-44a1-86a7-eaad33f3075d
caps.latest.revision: 30
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: dcf292660c89e55ec83739c4dba662ff4cf7bff4
ms.sourcegitcommit: 52b7f59e271437e86ffff226fb6c1982bf7f08b1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "3332502"
---
# <a name="add-a-field-to-a-model-driven-app-form"></a>Agregar un campo a un formulario de aplicación controlada por modelos 

Si un formulario de Power Apps para una entidad estándar no cumple los requisitos empresariales de su organización, puede personalizar el formulario cambiando los campos existentes o agregando nuevos campos. Si bien puede que sea más fácil editar los campos existentes en un formulario, a veces es mejor agregar un campo para abordar un escenario específico de negocio.

En este tema, agregará un campo a un formulario.   
  
1.  Inicie sesión en [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).  

2.  Expanda **Datos**, seleccione **Entidades**, seleccione la entidad que desee y, a continuación, seleccione la pestaña **Formularios**.  

3.  En la lista, abra un formulario con el tipo **Principal** para editarlo.  
  
4.  En el formulario, haga clic en la sección a la que desea agregar un campo y, en el panel **Campos**, haga clic en el campo desee agregar al formulario.  
  
    > [!TIP]
    >  Cuando agrega un campo de conjunto de opciones en el formulario, la lista desplegable que contiene los valores del conjunto de opciones puede mostrar sólo dos valores. Los usuarios deben desplazarse para ver más valores de la lista. Si desea mostrar más de dos valores sin que los usuarios tengan que desplazarse, agregue uno o varios controles **Separador** bajo el campo del conjunto de opciones en el formulario. Cada control **Separador** proporciona un espacio para un valor de conjunto de opciones adicional. Por ejemplo, si desea mostrar cuatro valores en la lista desplegable sin desplazarse, agregue dos controles **Separador** bajo el campo del conjunto de opciones en el formulario.  
  
5.  Para publicar personalizaciones del formulario está editando, con el formulario abierto, haga clic en **Publicar**. 
  
6.  Cuando haya terminado de editar el formulario, haga clic en **Guardar y cerrar**.  
  
> [!IMPORTANT]
>  En la interfaz unificada, cuando configura la seguridad a nivel de campo, no recomendamos que configure solo lectura en un campo obligatorio utilizando las reglas de seguridad a nivel de campo.  Cuando se crea el registro, la canalización para guardar ignorará la configuración de solo lectura en el campo requerido y guardará el registro. Se recomienda configurar la entidad en solo lectura mediante la seguridad basada en roles. Esto ayuda a garantizar que no haya conflictos al crear o guardar un registro.
  
  
> [!NOTE]
>  La publicación de personalizaciones pueden interferir en el funcionamiento normal del sistema. Le recomendamos que publique cuando perjudique menos a los usuarios.

  
## <a name="next-steps"></a>Pasos siguientes  
 
 [Creación y diseño de formularios](create-design-forms.md)
