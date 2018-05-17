---
title: Tutorial para la creación de una entidad personalizada que tiene componentes con PowerApps | Microsoft Docs
description: Tutorial con instrucciones paso a paso para crear y configurar una entidad para usar con una aplicación de PowerApps.
author: Mattp123
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: tutorial
ms.date: 05/01/2018
ms.author: matp
ms.openlocfilehash: c587ed6488ae498e3ec662016ee1d028023e4095
ms.sourcegitcommit: b3b6118790d6b7b4285dbcb5736e55f6e450125c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2018
---
# <a name="tutorial-create-a-custom-entity-that-has-components-in-powerapps"></a>Tutorial: Creación de una entidad personalizada que tiene componentes en PowerApps

Con [!INCLUDE [powerapps](../../includes/powerapps.md)], la aplicación se adapta para ajustarla al sector, la nomenclatura y los procesos de negocio únicos de la organización. El desarrollo de aplicaciones de [!INCLUDE [powerapps](../../includes/powerapps.md)] incluye la adición de entidades estándar de fábrica o la creación de entidades personalizadas. Una entidad define la información de la que se quiere realizar el seguimiento en forma de registros, que suelen incluir propiedades como el nombre de la empresa, la ubicación, los productos, el correo electrónico y el teléfono. 

En este tutorial se crea una entidad y, después, se agregan o personalizan componentes clave como campos, relaciones, vistas y formularios. Obtendrá información sobre cómo:

- Crear una entidad personalizada
- Agregar campos personalizados a la entidad
- Agregar una relación de entidad
- Personalizar una vista 
- Personalizar un formulario

En el tutorial se sigue a la empresa Contoso, que tiene un negocio de peluquería de mascotas para perros y gatos. Contoso necesita una aplicación para el seguimiento de clientes y mascotas que los empleados puedan usar en diferentes dispositivos.

## <a name="prerequisites"></a>Requisitos previos

Inicie sesión en [PowerApps](https://powerapps.microsoft.com/). Si todavía no tiene una cuenta de [!INCLUDE [powerapps](../../includes/powerapps.md)], haga clic en el vínculo **Inicio gratuito** desde [powerapps.com](https://web.powerapps.com).

## <a name="create-a-custom-entity"></a>Crear una entidad personalizada

1. En el panel de navegación de la izquierda, expanda **Datos**, haga clic en **Entidades** y, después, en **Nueva entidad**.
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
4. En la pestaña **Campos** de la barra de herramientas del diseñador de entidades haga clic en **Agregar campo**. En el panel **Propiedades de campo**, escriba o seleccione las opciones y los valores siguientes.
  - **Nombre para mostrar**. *Especie*
  - **Tipo de datos**. *Conjunto de opciones*
  - **Conjunto de opciones**. *Nuevo conjunto de opciones*
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

1. Haga clic en la pestaña **Relaciones**, haga clic en **Agregar relación** en la barra de herramientas del Diseñador de entidades y, después, seleccione **Varios a uno**. 
2. En el panel de la derecha, en la lista **Relacionada**, seleccione **Cuenta**.
3. Seleccione **Listo**.
4. Haga clic en **Guardar entidad**.

Tenga en cuenta que, cuando se agrega una relación varios a uno, se agrega automáticamente un campo **Cuenta** con el tipo de datos **Búsqueda** a la lista de campos en la pestaña **Campos**. ![Campo de búsqueda de cuentas](media/create-custom-entity/account-lookup-field.png)

## <a name="customize-a-view"></a>Personalizar una vista

1. Haga clic en la pestaña **Vistas** y, después, seleccione la vista **Mascotas activas**. Si no ve la vista **Mascotas activas**, haga clic en **Quitar filtro**.
2. En el diseñador de vistas, haga clic en **Agregar columnas**, seleccione las columnas siguientes y, después, haga clic en **Aceptar**.
  - Cuenta
  - Fecha de la cita 
  - Raza 
  - Especie
3. Seleccione la columna **Creado el**, haga clic en **Quitar** y después en **Aceptar** para confirmar la eliminación de la columna.
4. Para organizar las columnas, seleccione la columna que quiera mover y, después, pulse los botones de flecha <- y -> hasta que la vista tenga este aspecto.
    ![Vista de mascotas activas](media/create-custom-entity/active-pets-view.png)
5. En la barra de herramientas del diseñador de vistas, haga clic en **Guardar y cerrar**.  

## <a name="model-driven-apps-only-customize-the-main-form"></a>Solo para aplicaciones controladas por modelos: personalizar el formulario principal

Omita este paso si solo quiere usar la entidad Mascota en una aplicación de lienzo. 

1. En el panel de navegación de la izquierda de [!INCLUDE [powerapps](../../includes/powerapps.md)], seleccione **Basado en modelos**.
2. En el panel de navegación de la izquierda, expanda **Datos**, haga clic en **Entidades** y, después, seleccione **Mascota**.
3. Haga clic en la pestaña **Formularios** y, después, seleccione **Información** junto al tipo de formulario **Principal** para abrir el editor de formularios.
    ![Editar el formulario principal](media/create-custom-entity/main-form-edit.png)
4. En el editor de formularios, arrastre y coloque los campos **Especie**, **Raza**, **Fecha de la cita** y **Cuenta** situados en el panel Explorador de campos a la sección General del lienzo del formulario hasta que el formulario tenga este aspecto.
    ![Seleccionar los campos del formulario principal](media/create-custom-entity/main-form-edit2.png) 
5. Seleccione **Guardar**.
6. Haga clic en **Publicar**.
7. Haga clic en **Guardar y cerrar** para cerrar el Diseñador de formularios.

## <a name="add-the-custom-entity-to-an-app"></a>Agregar la entidad personalizada a una aplicación

Ahora la entidad está lista para usarse para compilar una aplicación de lienzo o controlada por modelos. 

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, ha obtenido información sobre cómo crear una entidad que puede usarse para crear una aplicación útil. 
- Para obtener información sobre cómo crear una aplicación controlada por modelos, vea [Creación de su primera aplicación controlada por modelos](../model-driven-apps/build-first-model-driven-app.md).
- Para obtener información sobre cómo crear una aplicación de lienzo, vea [Creación de una aplicación desde cero](../canvas-apps/get-started-create-from-blank.md).
