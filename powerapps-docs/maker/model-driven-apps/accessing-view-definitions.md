---
title: Acceso a una definición de vista de aplicación controlada por modelos | MicrosoftDocs
description: 'En este tema, aprenderá a acceder a vistas de entidad'
ms.custom: ''
ms.date: 11/27/2018
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
ms.assetid: 034c8bef-0d1c-4ef9-8da7-f81343c4553a
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="access-a-model-driven-app-view-definition-in-powerapps"></a>Acceso a una definición de vista de aplicación controlada por modelos en PowerApps

 En este tema abrirá una definición de vista para mostrar propiedades y opciones para configurar la vista. Existen varias formas de acceder a definiciones de vista en PowerApps. 
  
  
## <a name="open-a-view-for-editing-in-the-latest-view-designer"></a>Abra una vista para editar en el último diseñador de vistas

> [!IMPORTANT]
> La versión más reciente del diseñador de vistas está funcionando actualmente en vista previa. Algunas características como el filtrado avanzado, controles personalizados, así como propiedades de columnas aún no se admiten. Para realizar estas tareas [Abra una vista para editar en el explorador de soluciones](#open-a-view-for-editing-in-solution-explorer).

1.  Iniciar sesión en [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).  


    > [!IMPORTANT]
    > “Si el modo de diseño **Controlado por modelos** no está disponible, puede que tenga que [Crear un entorno](https://docs.microsoft.com/powerapps/administrator/create-environment). 

2.  Expanda **Datos**, seleccione **Entidades** y, a continuación, seleccione la entidad que desee, como la entidad **Cuenta**.   
3. Seleccione la ficha **Vistas**.

    > [!div class="mx-imgBorder"] 
    > ![Definiciones de vista de cuenta](media/account-view-definitions.png)

4. Seleccione la vista que desea abrir como, por ejemplo, la vista **Todas las cuentas** de la entidad de cuenta.

    > [!div class="mx-imgBorder"] 
    > ![Vista Todas las cuentas](media/account-view-designer.png)

5. En el editor de vistas puede realizar varias tareas: 
 
- [Ordenar registros en una vista](configure-sorting.md)
- [Elegir y configurar columnas en vistas](choose-and-configure-columns.md)

## <a name="open-a-view-for-editing-from-a-legacy-web-app"></a>Abra una vista para editarla desde una aplicación web heredada
En cualquier vista de lista para una entidad de una aplicación web heredada, en la barra de comandos encontrará los siguientes comandos tras seleccionar el botón de puntos (...):  

- **Vista**: Abre la definición de la vista actual de la solución predeterminada.  
  
- **Nueva vista del sistema**: Abre una ventana nueva para crear una nueva vista de la entidad actual en la solución predeterminada.  
  
- **Personalizar entidad**: Le llevará a la definición de la entidad actual en la solución predeterminada donde puede seleccionar **Vistas**.  
  
- **Vistas del sistema**: Abre la misma que ventana que **Personalizar entidad**, pero con **Vistas** seleccionado.  

   ![Abra el editor de vistas desde una aplicación web heredada](media/open-view-editor-from-view.png)

## <a name="open-a-view-for-editing-in-solution-explorer"></a>Abrir una vista para editarla en el Explorador de soluciones 
1.  Abra el [explorador de soluciones](advanced-navigation.md#solution-explorer).  
  
2.  En **Componentes**, expanda **Entidades** y, a continuación, expanda la entidad que desea.  
  
3.  Seleccione **Vistas**.  
  
4.  Haga doble clic en la vista que desea abrir. Esto abrirá el diseñador de vistas clásico.
    
    > [!div class="mx-imgBorder"] 
    > ![Vista Todas las cuentas](media/all-accounts-view.png)

 Esta lista de vistas tiene cuatro filtros que puede usar para encontrar las vistas que desea más fácilmente:  
  
- **Todas las vistas activas**  

- **Vistas públicas activas**  

- **Vistas públicas inactivas**  

- **Vistas activas definidas por el sistema**  
  
 Si la entidad con la que está asociada la vista forma parte de una solución no administrada, puede crear o editar vistas para esa entidad en la solución predeterminada. Las vistas del sistema se asocian con una entidad y no están disponibles como componentes de soluciones independientes. A diferencia de los campos, las vistas no usan un prefijo de personalización en un nombre único que deba ser coherente en una solución, de modo que no es necesario crear vistas en el contexto de una solución. 
 
## <a name="next-steps"></a>Pasos siguientes
[Comprender las vistas ](create-edit-views.md)


