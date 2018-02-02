---
title: Apertura de los datos de entidad en Excel | Microsoft Docs
description: "Abra los datos de la entidad en Excel para la visualización y edición interactivas."
services: powerapps
documentationcenter: na
author: chrisgarty
manager: kfend
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/06/2016
ms.author: kfend
ms.openlocfilehash: d559774c65ee2db99f891e41472f6110e330bfc1
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2018
---
# <a name="open-entity-data-in-excel"></a>Abrir los datos de la entidad en Excel
Al abrir los datos de la entidad en Microsoft Excel, estos se pueden ver y editar de forma rápida y sencilla mediante el complemento de Excel de Microsoft PowerApps. Este complemento requiere Microsoft Excel 2016.

> [!NOTE]
> Si su inquilino de Microsoft Azure Active Directory (Azure AD) está configurado para usar Servicios de federación de Active Directory (AD FS), debe asegurarse de que se ha aplicado la actualización de mayo de 2016 para que el complemento de Excel pueda iniciar su sesión correctamente.

## <a name="open-entity-data-in-excel"></a>Abrir los datos de la entidad en Excel
1. En [powerapps.com](https://web.powerapps.com), expanda la sección **Common Data Service** y pulse o haga clic en **Entidades** en el panel de navegación izquierdo. Se muestran todas las entidades.
2. Haga clic en los puntos suspensivos (...) que hay a la derecha de la entidad que le interesa.
3. Haga clic en **Abrir en Excel** y abra el libro que se genera. Dicho libro generado información de enlace de la entidad, un puntero a su entorno y un puntero para el complemento de Excel de PowerApps.  
4. En Excel, haga clic en **Habilitar edición** para habilitar la ejecución del complemento de Excel de PowerApps. El complemento de Excel se ejecutará en un panel de la derecha de la ventana de Excel.
5. Si es la primera vez que ejecuta el complemento, de Excel de PowerApps, haga clic en **Confiar en este complemento** para permitir que se ejecute el complemento de Excel.
6. Si se le solicita que inicie sesión, haga clic en **Inicio de sesión** y hágalo con las mismas credenciales que usó en [powerapps.com](https://web.powerapps.com). El complemento de Excel utilizará un contexto de inicio de sesión anterior e iniciará sesión automáticamente, en caso de que sea posible. Por tanto, compruebe el nombre de usuario en la parte superior derecha del complemento de Excel.

El complemento de Excel lee automáticamente los datos de la entidad que ha seleccionado. Tenga en cuenta que no habrá ningún dato en el libro hasta que el complemento de Excel los lea.

## <a name="view-and-refresh-entity-data-in-excel"></a>Visualizar y actualizar los datos de la entidad en Excel
Después de que el complemento de Excel lea los datos de la entidad en el libro, se pueden actualizar en cualquier momento, solo es preciso hacer clic en **Actualizar** en el complemento de Excel.

## <a name="edit-entity-data-in-excel"></a>Editar los datos de la entidad en Excel
Para cambiar los datos de la entidad y volver a publicarlos, haga clic en **Publicar** en el complemento de Excel.

Para editar un registro, seleccione una celda en la hoja de cálculo y cambie su valor.

Para agregar un registro nuevo, siga uno de estos pasos:

* Haga clic en cualquier parte en la hoja de cálculo y, después, en **Nuevo** en el complemento de Excel.
* Haga clic en la última fila de la hoja de cálculo y presione la tecla TAB hasta que el cursor pase la última columna de la fila y se cree una fila nueva.
* Haga clic en la fila inmediatamente inferior de la hoja de cálculo y empieza a escribir datos en una celda. Cuando cambia de celda, la hoja de cálculo se expande e incluye la nueva fila.

Para eliminar un, siga uno de estos pasos:

* Haga clic con el botón derecho en el número de fila situado junto a la va a eliminar y, después, haga clic en **Eliminar**.
* Haga clic con el botón derecho en la fila de la hoja de cálculo que va a eliminar y, después, haga clic en **Eliminar** > **Filas de la tabla**.

## <a name="add-or-remove-columns"></a>Agregar o quitar columnas
Puede utilizar el diseñador para ajustar las columnas que se agregan automáticamente a la hoja de cálculo.

1. Para habilitar el diseñador de orígenes de datos del complemento de Excel, haga clic en el botón **Opciones** (el símbolo de engranaje) y active la casilla **Habilitar diseño**.
2. Haga clic en **Diseño** en el complemento de Excel. Aparecerán todos los orígenes de datos.
3. Junto al origen de datos, haga clic en el botón **Editar** (el símbolo del lápiz).
4. Ajuste la lista del campo **Campos seleccionados** como sea necesario:
   * Para agregar un campo de **Campos disponibles** a **Campos seleccionados**, haga clic en él y, después, en **Agregar**. Como alternativa, haga doble clic en el campo.
   * Para quitar un campo de **Campos seleccionados**, haga clic en él y, después, en **Quitar**. Como alternativa, haga doble clic en el campo.
   * Para cambiar el orden de los campos, haga clic en **Campos seleccionados** y, después, en **Arriba** o **Abajo**.
5. Para aplicar los cambios al origen de datos, haga clic en **Actualizar** y, después, en **Listo** para salir del diseñador. Si ha agregado un campo (columna), haga clic en **Actualizar** para recopilar un conjunto de datos actualizado.

## <a name="troubleshooting"></a>Solución de problemas
Hay algunos problemas que se pueden resolver mediante algunos pasos sencillos.

* Si recibe el mensaje "Prohibido" cuando el complemento de Excel carga los metadatos, significará que la cuenta con la que ha iniciado sesión en el complemento de Excel no tiene permiso para utilizar la base de datos de Common Data Service de destino. Para resolver este problema, compruebe que el nombre de usuario correcto aparece en la parte superior derecha del complemento de Excel. Si es necesario, haga clic en el nombre de usuario en la parte superior derecha del complemento de Excel, cierre la sesión y vuelva a iniciarla.
* Si se abre una página web en blanco durante el proceso de inicio de sesión, la cuenta requiere AD FS, pero la versión de Excel que ejecuta el complemento no es lo suficientemente reciente como para cargar el cuadro de diálogo de inicio de sesión. Si es necesario, actualice la versión de Excel. Para ello, use la [herramienta de implementación de Office](https://technet.microsoft.com/library/jj219422.aspx) para [moverse del canal diferido al canal actual](https://technet.microsoft.com/library/mt455210.aspx).

Si aparece algún problema que no se describe aquí, póngase en contacto con nosotros a través de las [páginas de soporte técnico](https://powerapps.microsoft.com/support/).

## <a name="next-steps"></a>Pasos siguientes
* [Administrar campos de una entidad](data-platform-manage-fields.md)
* [Definir relaciones entre entidades](data-platform-entity-lookup.md)
* [Generar una aplicación mediante una base de datos de Common Data Service](data-platform-create-app.md)
* [Create an app from scratch using a Common Data Service database](data-platform-create-app-scratch.md) (Crear una aplicación desde cero mediante una base de datos de Common Data Service)

