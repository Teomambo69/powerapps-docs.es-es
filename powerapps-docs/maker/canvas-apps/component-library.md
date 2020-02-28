---
title: Creación de una biblioteca de componentes para las aplicaciones de Canvas | Microsoft Docs
description: Biblioteca de componentes reutilizables para aplicaciones de lienzo
author: yifwang
ms.service: powerapps
ms.topic: article
ms.date: 02/20/2020
ms.author: yifwang
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: af43eeb3cfa5b2b99bc302360af150f662e1c0af
ms.sourcegitcommit: 59f0b3adc56279b5673cbf04b4a55bd7678e1ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/28/2020
ms.locfileid: "77911454"
---
# <a name="component-library"></a>Biblioteca de componentes

> [!IMPORTANT]
> Esta característica todavía está en versión preliminar pública. Para obtener más información, vea [Características en versión preliminar y experimentales](working-with-experimental.md).

En el artículo de [información general](create-component.md) para crear componentes, se introducen los componentes dentro de la aplicación Canvas. A medida que crea componentes dentro de una aplicación, también puede crear una biblioteca de componentes que se pueden volver a usar. Mediante la creación de una biblioteca de componentes, los responsables de las aplicaciones comparten y actualizan fácilmente uno o más componentes con otros responsables.

Las bibliotecas de componentes son contenedores de definiciones de componentes que facilitan:

- Detectar y buscar componentes.
- Publicar actualizaciones en entornos.
- Notificar a los responsables de las actualizaciones de componentes disponibles. 

> [!NOTE]
> Las bibliotecas de componentes son la manera recomendada de reutilizar los componentes entre las aplicaciones. Cuando se usa la biblioteca de componentes, una aplicación mantiene las dependencias de los componentes que usa. El creador de la aplicación recibirá una alerta cuando las actualizaciones de los componentes dependientes estén disponibles. Por lo tanto, todos los componentes reutilizables nuevos deben crearse dentro de las bibliotecas de componentes. Una característica de Power apps anterior que permitía la [importación de componentes de una aplicación de lienzo a otra](create-component.md?#import-and-export-components) quedará en desuso.

## <a name="difference-between-an-app-and-a-component-library"></a>Diferencia entre una aplicación y una biblioteca de componentes

Una biblioteca de componentes proporciona un repositorio centralizado y administrado de componentes para su reutilización. 

Si crea una biblioteca de componentes, el panel **Insertar** en la navegación izquierda tiene como valor predeterminado la pestaña componentes. Al crear una aplicación, esta vista muestra pantallas en lugar de componentes. 

Las pantallas dentro de una biblioteca de componentes solo están disponibles para pruebas. Proporciona a los creadores de bibliotecas una manera de probar rápidamente los componentes creados en la pantalla real y validar también el comportamiento de la actualización a medida que los componentes se mejoran con el tiempo. Para usar los componentes de la biblioteca de componentes, debe crear una aplicación que use la biblioteca de componentes.

Puede obtener una vista previa de los componentes de la biblioteca de componentes mediante las pantallas dentro de la biblioteca con la opción Play. Al seleccionar la pestaña componente, se deshabilita la opción reproducir. La biblioteca de componentes no se muestra cuando se usa Power apps Mobile.

> [!NOTE]
> La biblioteca de componentes que se describe en este artículo es diferente del marco de trabajo de componentes de Power apps que permite a los desarrolladores y a los desarrolladores crear componentes de código para aplicaciones de lienzo y controladas por modelos. Para obtener más información, lea [información general sobre el marco de trabajo de componentes de Power apps](https://docs.microsoft.com/powerapps/developer/component-framework/overview).

## <a name="working-with-component-library"></a>Trabajar con la biblioteca de componentes

Puede crear una nueva biblioteca de componentes o editar una biblioteca de componentes existente desde la misma interfaz. Vaya a [make.powerapps.com](https://make.powerapps.com), seleccione **aplicaciones**y, a continuación, seleccione **bibliotecas de componentes**:

![Crear o editar la biblioteca de componentes](./media/component-library/create-edit-component-library.png)

## <a name="create-an-example-component-library"></a>Crear una biblioteca de componentes de ejemplo

Los pasos para crear componentes dentro de una biblioteca de componentes son los mismos que para crear componentes dentro de una aplicación. Creará una biblioteca de componentes. Y vuelva a usar el [ejemplo de introducción](create-component.md#create-an-example-component)a los pasos para crear componentes desde componentes. A continuación, usará la biblioteca de componentes para proporcionar los componentes reutilizables en una nueva aplicación.

1. Inicie sesión en [make.powerapps.com](https://make.powerapps.com).

1. Seleccione **aplicaciones** en el panel de navegación izquierdo, seleccione **bibliotecas de componentes**y, a continuación, seleccione **nueva biblioteca de componentes**.

1. Asigne a la biblioteca de componentes el nombre como *componentes de menú*; también puede proporcionar un nombre diferente de su elección.

1. Siga los pasos para crear componentes en el [ejemplo de información general de componentes](create-component.md#create-an-example-component). No tiene que abrir Power apps Studio ni crear una nueva aplicación vacía, ya que ya ha creado una nueva biblioteca de componentes. Comience con el paso 2. 

    Después de realizar los pasos siguientes para crear los componentes, siga el siguiente conjunto de pasos para [Agregar los componentes a una pantalla](create-component.md#add-component-to-a-screen) con los pasos para [crear la propiedad de salida](create-component.md#create-and-use-output-property). 

1. Después de completar la creación y las pruebas de los componentes, guarde la biblioteca de componentes seleccionando el menú **archivo** y, a continuación, seleccione **Guardar**. 

    También tiene la opción de guardar una nota de la **versión**. La nota de la versión es útil para recuperar versiones de una biblioteca de componentes. Y al actualizar los componentes usados en aplicaciones de esta biblioteca de componentes.

    ![Nota de la versión al guardar la biblioteca de componentes](./media/component-library/save-component-libray-version-note.png)

    > [!TIP]
    > La nota sobre la versión es útil cuando se revisan las versiones de una biblioteca de componentes y los responsables de la aplicación usan la biblioteca de componentes para revisar los cambios y actualizar las aplicaciones que consumen estos componentes según sea necesario. Lea [actualizar una biblioteca de componentes](component-library.md?#update-a-component-library) para obtener más detalles.   

1. La biblioteca de componentes guardada se puede publicar. Solo las actualizaciones de la biblioteca de componentes publicadas están disponibles para las aplicaciones que consumen una biblioteca de componentes. Seleccione **publicar** para publicar la versión de la biblioteca de componentes:

    ![Publicar versión de la biblioteca de componentes](./media/component-library/publish-component-library.png)

## <a name="import-from-a-component-library"></a>Importar desde una biblioteca de componentes

Después de crear una biblioteca de componentes y publicarla, las aplicaciones pueden usar los componentes de esta biblioteca de componentes importando la biblioteca. También puede [compartir una biblioteca de componentes](component-library.md#component-library-permissions).

Para importar desde una biblioteca de componentes, edite una aplicación existente o cree una nueva aplicación. Una vez que se abra la aplicación en canvas App Studio, seleccione **Insertar** o el **+** en el panel de navegación izquierdo. Y, a continuación, seleccione **obtener más componentes** para enumerar las bibliotecas de componentes disponibles en el entorno actual:

![Obtener más componentes](./media/component-library/get-more-components.png)

Verá la lista de bibliotecas de componentes disponibles en el entorno actual en el lado derecho de la pantalla. Seleccione un componente individual de una biblioteca de componentes. O bien, use **seleccionar todo** para importar todos los componentes de la biblioteca a la vez:

![Importar componentes](./media/component-library/components.png)

> [!NOTE]
> Si Maker no ve la biblioteca de componentes enumerada en la sección importar, asegúrese de que la biblioteca de componentes se comparte con el creador. Para obtener más información, lea permisos de la [biblioteca de componentes](component-library.md#component-library-permissions). 

Tenga en cuenta que puede seleccionar e importar más de un componente y entre diferentes bibliotecas de componentes. 

Los componentes disponibles dentro de la aplicación se muestran en categoría **personalizada** en lista de componentes en el panel **Insertar** . Los componentes disponibles de las bibliotecas de componentes importados aparecen en la categoría **componentes de biblioteca** :

![Inserción de componentes en la aplicación](./media/component-library/insert-components.png)

## <a name="update-a-component-library"></a>Actualizar una biblioteca de componentes

Puede modificar la biblioteca de componentes existente y guardar cualquier cambio con notas de versión adicionales. Sin embargo, la versión actualizada de la biblioteca de componentes debe publicarse para su uso en aplicaciones existentes que usan la biblioteca de componentes. En los pasos de la [biblioteca de componentes de ejemplo](component-library.md#create-an-example-component-library) anteriores se explica cómo publicar una biblioteca de componentes después de guardarla.

Se notifica a los responsables de otras aplicaciones los componentes actualizados que están disponibles. La notificación aparece cuando los responsables editan las aplicaciones en canvas App Studio. Y pueden optar por actualizar los componentes:

![Actualización disponible](./media/component-library/update-available.png)

Seleccione **revisar**y verá la opción para actualizar el componente:

![Actualizar componente](./media/component-library/update-components.png)

Observe que la nota de la versión que agregó al publicar la versión de la biblioteca de componentes se muestra aquí. 

Seleccione **Actualizar** para actualizar los componentes.

## <a name="component-library-permissions"></a>Permisos de la biblioteca de componentes

Compartir una biblioteca de componentes funciona de la misma manera que comparte una aplicación de lienzo. Cuando comparte una biblioteca de componentes, permite que otros usuarios vuelvan a usar la biblioteca de componentes. Una vez compartido, otros usuarios pueden editar la biblioteca de componentes e importar los componentes de esta biblioteca de componentes compartidos para crear y editar aplicaciones. Si se comparte como copropietario, el usuario puede usar, editar, compartir la biblioteca de componentes pero no eliminar ni cambiar el propietario.

## <a name="known-limitations"></a>Limitaciones conocidas

- Las [limitaciones conocidas](create-component.md#known-limitations) aplicables a los componentes de también se aplican a la biblioteca de componentes.
- No se pueden importar componentes mediante la biblioteca de componentes desde el archivo de biblioteca de componentes guardado localmente. Si intenta importar una biblioteca de componentes guardada localmente con el **archivo** -> **Guardar como** -> **este equipo** y descargar el archivo de biblioteca de componentes como una aplicación, aparece el mensaje de error siguiente: 

    ![Importar archivo de biblioteca de componentes](./media/component-library/import-component-library-file.png)

- No se pueden agregar bibliotecas de componentes existentes a una [solución](add-app-solution.md). Sin embargo, puede crear nuevas bibliotecas de componentes para soluciones mediante el flujo agregar biblioteca de componentes.

- Si importa un componente desde una biblioteca de componentes, no podrá editarlo dentro de la aplicación de consumo. Si selecciona **Editar componente**, verá una opción para crear una copia del componente en la aplicación actual para que realice cambios: 

    ![Editar componente de biblioteca](./media/component-library/edit-library-component.png)

    Si selecciona **crear una copia**, el componente se copia en la aplicación local. La copia local del componente aparece bajo la categoría **personalizada** en el panel **Insertar** . Esta copia local del componente no recibirá actualizaciones si se publica una nueva versión de la biblioteca de componentes de origen posteriormente.
    
- Cuando se agrega un componente a una aplicación desde la biblioteca de componentes y se actualiza el tema de la aplicación, el componente se convierte en un componente de aplicación local y ya no está asociado al componente maestro en la biblioteca de componentes.

## <a name="next-steps"></a>Pasos siguientes

Obtenga información sobre las [fórmulas de comportamiento](component-behavior.md) para la aplicación Canvas.

### <a name="see-also"></a>Vea también

Lea [información general sobre los componentes](create-component.md) de la aplicación Canvas y cómo trabajar con componentes en una aplicación.
