---
title: Crear una entidad personalizada que tiene componentes con Power Apps | Microsoft Docs
description: Tema con las instrucciones paso a paso para crear y configurar una entidad para usar con una aplicación de Power Apps.
author: Mattp123
manager: kvivek
ms.service: powerapps
ms.component: cds
ms.topic: tutorial
ms.date: 01/23/2019
ms.author: matp
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4323e0a658508616c5ba0a19644fc74c1c7681fc
ms.sourcegitcommit: 3c6c5594b73abd5ff438d50f3b579d56cef7241c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2020
ms.locfileid: "3286054"
---
# <a name="create-a-custom-entity-that-has-components-in-power-apps"></a>Crear una entidad personalizada que tenga componentes en Power Apps

Con in Power Apps puede personalizar su aplicación para que se ajuste más al sector, la nomenclatura y los procesos de negocio únicos de la organización. El desarrollo de aplicaciones de Power Apps incluye agregar entidades predefinidas estándar o crear entidades personalizadas. Una entidad define la información a la que desea realizar seguimiento en forma de registros, que incluyen normalmente propiedades como el nombre, ubicación, productos, correo electrónico, y teléfono de la compañía. 

En este tema creará una entidad y luego agregará o personalizará componentes clave como campos, relaciones, vistas, y formularios. Aprenderá a:

- Crear una entidad personalizada
- Agregar campos personalizados a la entidad
- Agregar una relación entre entidades
- Personalizar vistas 
- Personalizar formularios

El tema seguirá a la compañía, Contoso, que es un negocio de cuidado de animales domésticos que cuida perros y gatos. Contoso necesita una aplicación para seguimiento de clientes y animales domésticos que pueden usar los empleados a través de una variedad de dispositivos.

## <a name="prerequisites"></a>Requisitos previos

Inicie sesión en [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc). Si aún no tiene una cuenta de Power Apps, seleccione el vínculo **Introducción gratuita** de [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

## <a name="create-a-custom-entity"></a>Crear una entidad personalizada

1. En el panel de navegación izquierdo, expanda **Datos**, seleccione **Entidades** y seleccione **Nueva entidad**.

    > [!div class="mx-imgBorder"] 
    > ![Entidad nueva](media/create-custom-entity/create-new-entity.png)

2. En el panel derecho, escriba los siguientes valores y luego seleccione **Crear**.

    - **Nombre para mostrar**: *Animal doméstico* 
    - **Descripción**: *Entidad personalizada para seguir servicios de animales domésticos*

## <a name="add-and-customize-fields"></a>Agregue y personalice campos
 
1. En la lista de entidades, seleccione la entidad **Animal doméstico** que se creó en la sección anterior.

2. En la pestaña **Campos**, seleccione el campo **Animal doméstico**.

3. En el panel derecho realice los cambios siguientes en el campo **Nombre para mostrar**: 

    - Cambie el **Nombre para mostrar** de **Animal doméstico** a *Nombre de animal doméstico*
    -   Seleccione **Búsqueda**.  
  
      > [!div class="mx-imgBorder"] 
      > ![Cambiar campo principal](media/create-custom-entity/primary-field.png)

4. Seleccione **Listo**.

5. En la pestaña **Campos** en la barra de herramientas del diseñador de entidades seleccione **Agregar campo**. En el panel **Propiedades de campo** , escriba o seleccione los siguientes valores y opciones.
    - **Nombre para mostrar**. *Especie*
    - **Tipo de datos**. *Conjunto de opciones*
    - **Conjunto de opciones**. *Nuevo conjunto de opciones*
  
6. Seleccione **Ver más** y luego seleccione **Conjunto de opciones local**.

7. Crear el conjunto de opciones

      a. Reemplace **Nueva opción** con *Perro*. 
      
      b. Seleccione **Agregar nuevo elemento**. 
        
      c.  Reemplace **Nueva opción** con *Gato*. 
        
      d. Seleccione **Guardar**. 

    > [!div class="mx-imgBorder"] 
    > ![Nuevo conjunto de opciones](media/create-custom-entity/optionset-add-items.png)

6. Seleccione **Búsqueda**y, a continuación seleccione **Listo**.

7. En la barra de herramientas del diseñador de entidades seleccione **Agregar campo**. En el panel **Propiedades de campo**, escriba o seleccione los siguientes valores y luego seleccione **Listo**.
    - **Nombre para mostrar**. *Raza*
    - **Tipo de datos**. *Texto*

8. Seleccione **Búsqueda**y, a continuación seleccione **Listo**.

8. En la barra de herramientas del diseñador de entidades seleccione **Agregar campo**. 

9. En el panel **Propiedades de campo**, escriba o seleccione los siguientes valores y luego seleccione **Listo**. 
    -   **Nombre para mostrar**. *Fecha de cita*
    - **Tipo de datos**. *Fecha y hora*

10. Seleccione **Listo**.

## <a name="add-a-relationship"></a>Agregar una relación

1. Seleccione la pestaña **Relaciones**, en la barra de herramientas del diseñador de entidades seleccione **Agregar relación** y, a continuación seleccione **Varios a uno**.

2. En el panel derecho, en el lista **Relacionado** seleccione **Cuenta**.

3. Seleccione **Listo**.

4. Seleccione **Guardar entidad**.

  Recuerde que cuando agrega una relación de varios a uno, un campo **Cuenta** con el tipo de datos **Búsqueda** se agrega automáticamente a la lista de campos en la pestaña **Campos**.
  > [!div class="mx-imgBorder"]
  > ![Campo de búsqueda de cuentas](media/create-custom-entity/account-lookup-field.png)

## <a name="customize-a-view"></a>Personalizar vistas

1. Seleccione la pestaña **Vistas** y, a continuación seleccione la vista **Animales domésticos activos**. Si no ve la vista **Mascotas activas**, cambie el filtro en la barra de comandos de **Predeterminado** a **Todas**.

2. En el diseñador de vistas seleccione **Agregar columnas**, seleccione las columnas siguientes y, a continuación seleccione **Aceptar**.

    - Cuenta
    - Fecha de la cita 
    - Raza 
    - Especie

3. Seleccione la columna **Fecha de creación**, y después seleccione **Quitar**.

4. Para organizar las columnas, seleccione la columna que desea mover y use **Mover izquierda** y **Mover derecha** hasta que la vista sea como esta.
    > [!div class="mx-imgBorder"] 
    > ![Vista de animales domésticos activos](media/create-custom-entity/active-pets-view.png)

5. En la barra de herramientas del diseñador de vistas, seleccione **Guardar**.  

## <a name="model-driven-apps-only-customize-the-main-form"></a>Solo aplicaciones basadas en modelo: Personalizar el formulario principal

Omita este paso si sólo desea usar la entidad Animal doméstico en una aplicación de lienzo. 

1. En el panel de navegación izquierdo, expanda **Datos**, seleccione **Entidades** y seleccione **Animal doméstico**.

2. Seleccione la pestaña **Formularios** y, a continuación seleccione **Información** junto al tipo de formulario **Principal** para abrir el diseñador de formularios.

    > [!div class="mx-imgBorder"] 
    > ![Editar formulario principal](media/create-custom-entity/main-form-edit.png)

3. En el editor de formularios, arrastre y coloque los campos **Especie**, **Raza**, **Fecha de cita**, y **Cuenta** situados en el panel del Explorador de campos en la sección General del lienzo de formulario hasta que el formulario tenga este aspecto.

    > [!div class="mx-imgBorder"] 
    > ![Seleccionar campos para formulario principal](media/create-custom-entity/main-form-edit2.png) 

4. Seleccione **Guardar**.

5. Seleccione **Publish**.

6. Vuelva a la página principal de Power Apps.

## <a name="add-the-custom-entity-to-an-app"></a>Agregue la entidad personalizada a una aplicación

La entidad está lista ahora para usarse para crear una basada de lienzo o basada en modelo. 

## <a name="next-steps"></a>Pasos siguientes

En este tema, aprendió cómo crear una entidad que puede usarse para crear una aplicación útil. 
- Para obtener más información sobre cómo crear una aplicación basada en modelo, consulte [Crear la primera aplicación basada en modelo](../model-driven-apps/build-first-model-driven-app.md).
- Para obtener más información sobre cómo crear una aplicación de lienzo, consulte [Cree una aplicación desde cero](../canvas-apps/get-started-create-from-blank.md).
