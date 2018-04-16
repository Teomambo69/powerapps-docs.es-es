---
title: Tutorial para la creación de una entidad personalizada que tiene componentes con PowerApps | Microsoft Docs
description: Tutorial con instrucciones paso a paso para crear y configurar una entidad para usar con una aplicación de PowerApps.
services: ''
suite: powerapps
documentationcenter: na
author: Mattp123
manager: bycho
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/21/2018
ms.author: matp
ms.openlocfilehash: 3fd8b262849fb1f6bf2a7ff70d9d9af8b082efac
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="tutorial-create-a-custom-entity-that-has-components-in-powerapps"></a>Tutorial: Creación de una entidad personalizada que tiene componentes en PowerApps

Con [!INCLUDE [powerapps](../../includes/powerapps.md)], la aplicación se adapta para ajustarla al sector, la nomenclatura y los procesos de negocio únicos de la organización. El desarrollo de aplicaciones de [!INCLUDE [powerapps](../../includes/powerapps.md)] incluye la adición de entidades estándar de fábrica o la creación de entidades personalizadas. Una entidad define la información de la que se quiere realizar el seguimiento en forma de registros, que suelen incluir propiedades como el nombre de la empresa, la ubicación, los productos, el correo electrónico y el teléfono. 

En este tutorial se crea una entidad y, después, se agregan o personalizan componentes clave como campos, relaciones, vistas y formularios. Obtendrá información sobre cómo:

- Crear una entidad personalizada
- Agregar campos personalizados a la entidad
- Agregar una relación de entidad
- Personalizar una vista 
- Personalizar un formulario

> [!IMPORTANT]
> [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-definition.md)]

En el tutorial se sigue a la empresa Contoso, que tiene un negocio de peluquería de mascotas para perros y gatos. Contoso necesita una aplicación para el seguimiento de clientes y mascotas que los empleados puedan usar en diferentes dispositivos.

## <a name="prerequisites"></a>Requisitos previos

Inicie sesión en [PowerApps](https://powerapps.microsoft.com/). Si todavía no tiene una cuenta de [!INCLUDE [powerapps](../../includes/powerapps.md)], haga clic en el vínculo **Inicio gratuito** desde [powerapps.com](https://web.powerapps.com).

## <a name="create-a-custom-entity"></a>Crear una entidad personalizada

1. En el panel de navegación de la izquierda debajo de **Common Data Service**, haga clic en **Entidades** y, después, en **Nueva entidad**.
    ![Nueva entidad](media/create-custom-entity/create-new-entity.png)
2. En el panel de la derecha, escriba los valores siguientes y, después, haga clic en **Siguiente**.
  - **Nombre para mostrar**: *Mascota* 
  - **Descripción**: *Entidad personalizada para realizar el seguimiento de los servicios para mascotas*
3. Haga clic en **Guardar entidad**.

## <a name="add-and-customize-fields"></a>Agregar y personalizar campos

1. En la pestaña **Campos**, seleccione el campo **Nombre principal**.
2. En el panel de la derecha, realice los cambios siguientes en el campo **Nombre principal**: 
  - Cambie el **Nombre para mostrar** de **Nombre principal** a *Nombre de la mascota*.
  - Haga clic en **Se puede buscar**.

    ![Cambiar el campo principal](media/create-custom-entity/primary-field.png)
3. Seleccione **Listo**.
4. En la barra de herramientas del diseñador de entidades haga clic en **Agregar** campo. En el panel **Propiedades de campo**, escriba o seleccione las opciones y los valores siguientes.
  - **Nombre para mostrar**. *Especie*
  - **Tipo de datos**. *Conjunto de opciones*
  - **Conjunto de opciones**. *Nuevo*
5. Crear el conjunto de opciones

  a. Haga clic en **Agregar nuevo elemento**. 
  
  b. Reemplace **Nueva opción** con *Perro*. 
   
  c. Haga clic en **Agregar nuevo elemento**. 
    
  d.  Reemplace **Nueva opción** con *Gato*. 
    
  e. Seleccione **Guardar**. 

  ![Nuevo conjunto de opciones](media/create-custom-entity/optionset-add-items.png)

6. Haga clic en **Se puede buscar** y después en **Listo**.

7. En la barra de herramientas del diseñador de entidades haga clic en **Agregar campo**. En el panel **Propiedades de campo**, escriba o seleccione las opciones y los valores siguientes, y después haga clic en **Listo**.
  - **Nombre para mostrar**. *Raza*
  - **Tipo de datos**. *Texto*
  - **Se puede buscar**. *Sí*

8. En la barra de herramientas del diseñador de entidades haga clic en **Agregar campo**. 

9. En el panel **Propiedades de campo**, escriba o seleccione las opciones y los valores siguientes, y después haga clic en **Listo**. 
  - **Nombre para mostrar**. *Fecha de la cita*
  - **Tipo de datos**. *Fecha y hora*

10. Haga clic en **Guardar entidad**.

## <a name="add-a-relationship"></a>Agregar una relación

1. Haga clic en la pestaña **Relaciones** y, después, en la barra de herramientas del Diseñador de entidades, haga clic en **Agregar relación**. 
2. En el panel de la derecha, en la lista **Entidades relacionadas**, seleccione **Account** y, después, haga clic en **Listo**.
3. Haga clic en **Guardar entidad**.

Tenga en cuenta que, cuando se agrega una relación, se agrega automáticamente un campo con el tipo de datos **Búsqueda** a la lista de campos en la pestaña **Campos**. ![Campo de búsqueda de cuentas](media/create-custom-entity/account-lookup-field.png)

## <a name="customize-a-view"></a>Personalizar una vista

1. Haga clic en la pestaña **Vistas** y, después, seleccione la vista **Mascotas activas**.
2. En el diseñador de vistas, haga clic en **Agregar columnas**, seleccione las columnas siguientes y, después, haga clic en **Aceptar**.
  - Cuenta
  - Fecha de la cita 
  - Raza 
  - Especie
3. Seleccione la columna **Creado el**, haga clic en **Quitar** y después en **Aceptar** para confirmar la eliminación de la columna.
4. Para organizar las columnas, seleccione la columna que quiera mover y, después, pulse los botones de flecha <- y -> hasta que la vista tenga este aspecto.
    ![Vista de mascotas activas](media/create-custom-entity/active-pets-view.png)
5. En la barra de herramientas del diseñador de vistas, haga clic en **Guardar y cerrar**.  
6. Haga clic en **Guardar entidad**.

## <a name="model-driven-apps-only-customize-the-main-form"></a>Solo para aplicaciones controladas por modelos: personalizar el formulario principal

Omita este paso si solo quiere usar la entidad Mascota en una aplicación de lienzo. 

1. En el panel de navegación de la izquierda de [!INCLUDE [powerapps](../../includes/powerapps.md)], seleccione **Basado en modelos**.
2. En el panel de navegación de la izquierda, haga clic en **Opciones avanzadas**.
3. En el panel de navegación de la izquierda de la ventana de la solución, haga clic en **Entidades**, expanda **Mascota** y, después, haga clic en **Formularios**.
4. Haga clic en **Información** junto al tipo de formulario **Principal** para abrir el editor de formularios.
    ![Editar el formulario principal](media/create-custom-entity/main-form-edit.png)
5. En el editor de formularios, arrastre y coloque los campos **Especie**, **Raza**, **Fecha de la cita** y **Cuenta** situados en el panel Explorador de campos a la sección General del lienzo del formulario hasta que el formulario tenga este aspecto.
    ![Seleccionar los campos del formulario principal](media/create-custom-entity/main-form-edit2.png) 
6. Haga clic en **Guardar y cerrar**.
7. En la ventana de la solución, haga clic en **Publicar todas las personalizaciones**.
    ![Publicar todas las personalizaciones](media/create-custom-entity/publish-all-customizations.png)

## <a name="add-the-custom-entity-to-an-app"></a>Agregar la entidad personalizada a una aplicación

Ahora la entidad está lista para usarse para compilar una aplicación de lienzo o controlada por modelos. 

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, ha obtenido información sobre cómo crear una entidad que puede usarse para crear una aplicación útil. Para obtener información sobre cómo crear una aplicación de lienzo, vea [Creación de una aplicación desde cero](../canvas-apps/get-started-create-from-blank.md).
