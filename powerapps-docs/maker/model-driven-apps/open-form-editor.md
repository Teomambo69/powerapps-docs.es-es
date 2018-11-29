---
title: Abrir el editor de formularios de una aplicación controlada por modelos en PowerApps | MicrosoftDocs
ms.custom: ''
ms.date: 06/27/2018
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
ms.assetid: 8478a07a-c697-4784-874b-36958eb4f95d
caps.latest.revision: 63
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="open-the-model-driven-app-form-editor"></a>Abrir el editor de formularios de una aplicación controlada por modelos 
El editor de formularios es donde debe diseñar los formularios colocando componentes como secciones, pestañas, campos y controles sobre el lienzo del editor de formularios. En este tema aprenderá varias formas de acceder al editor de formularios.
 
Si crea componentes de la solución nuevos en el proceso de edición del formulario, como recursos web, los nombres de los componentes usarán el prefijo de personalización del editor de soluciones de la solución predeterminada y estos componentes solo se incluirán en la solución predeterminada. Si desea que los nuevos componentes de la solución se incluyan en una solución no administrada específica, debe abrir el editor de formularios a través de esa solución no administrada.  

## <a name="access-the-form-editor-from-the-powerapps-site"></a>Acceder al editor de formularios desde el sitio de PowerApps

1. Iniciar sesión en [PowerApps](https://web.powerapps.com/). 

2. Seleccione **Datos** > **Entidades** y, a continuación, seleccione la entidad que desee, como la entidad Cuenta. 

3. Seleccione la pestaña **Formularios** y abra el formulario que desee, como el formulario principal **Cuenta**.

## <a name="access-the-form-editor-from-solution-explorer"></a>Acceder al editor de formularios desde el explorador de soluciones
  
1.  Abra el [explorador de soluciones](advanced-navigation.md#solution-explorer).
  
2.  En **Componentes**, expanda **Entidades** y, a continuación, expanda la entidad que desea y haga clic en **Formularios**.  
  
3.  En la lista de formularios, haga clic en el formulario que desea editar.  
  

## <a name="access-the-form-editor-through-the-command-bar-within-a-model-driven-app"></a>Acceder al editor de formularios mediante la barra de comandos dentro de una aplicación controlada por modelos 
  
1.  Abra un registro.  
  
2.  Si hay varios formularios principales para la entidad, compruebe que el formulario es el que desea editar. Si no lo es, use el selector de formularios para elegir el formulario que desea editar.  
  
3.  Seleccione el botón **Más comandos** ![Botón Más comandos en Actividad de cita](media/more-commands.gif "Botón Más comandos en Actividad de cita").  
  
4.  Seleccione **Editor de formularios**.  

## <a name="access-the-form-editor-from-within-dynamics-365-customer-engagement"></a>Acceder al editor de formularios desde Dynamics 365 Customer Engagement
  
 Puede acceder al editor de formularios en Dynamics 365 Customer Engagement a través de la barra de comandos o la cinta, en función de la entidad. Ambos métodos abrirán el formulario en el contexto de la solución predeterminada. 

## <a name="access-the-form-editor-for-an-unmanaged-solution"></a>Acceso al editor de formularios de una solución no administrada  
  
1.  Abra [soluciones](advanced-navigation.md#solutions).  
  
2.  Haga doble clic en la solución no administrada que desea utilizar.  
  
3.  Busque la entidad con el formulario que desea editar. Si la entidad no está presente, deberá agregarla. Más información: [Agregar una entidad a una solución no administrada](#add-an-entity-to-an-unmanaged-solution) 
  
### <a name="add-an-entity-to-an-unmanaged-solution"></a>Agregar una entidad para una solución no administrada  
  
1.  Seleccione el nodo **Entidades** y, en la barra de herramientas situada encima de la lista, haga clic en **Agregar existente**.  
  
2.  En el cuadro de diálogo **Seleccionar componentes de la solución**, con el selector **Tipo de componente** definido en **Entidad**, seleccione la entidad que desee agregar y haga clic en **Aceptar**.  
  
3.  Si aparece el cuadro de diálogo **Faltan componentes necesarios**, puede hacer clic en **No, no incluir los componentes necesarios** si no piensa exportar esta solución no administrada a otro entorno. Si elige no incluir los componentes necesarios que faltan en este momento, puede agregarlos más adelante. Recibirá una notificación de nuevo si exporta esta solución en el futuro.  
  
5.  En el explorador de soluciones, expanda la entidad con el formulario que desee editar y seleccione **Formularios**.  
  
6.  En la lista de formularios, haga doble clic en el formulario que desea editar.  

## <a name="next-steps"></a>Pasos siguientes

[Crear y diseñar formularios](create-design-forms.md)
