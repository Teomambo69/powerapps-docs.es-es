---
title: Proporcionar a los clientes una versión de prueba de las aplicaciones de lienzo en AppSource | Microsoft Docs
description: Utilice AppSource para compartir aplicaciones de lienzo con los clientes y genere clientes potenciales para su empresa.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/08/2017
ms.author: litran
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 324c7880643a6e06bc147d1bbafb1b9638b8f2ec
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74731598"
---
# <a name="let-customers-test-drive-your-canvas-app-on-appsource"></a>Proporcionar a los clientes una versión de prueba de las aplicaciones de lienzo en AppSource

¿Le apasiona la creación de aplicaciones de lienzo en Power apps? ¿Quiere compartir una aplicación de lienzo con los clientes? [AppSource.com](https://appsource.microsoft.com) es compatible con las soluciones de Power apps Test Drive como una manera de compartir aplicaciones con los clientes y generar clientes potenciales para su negocio.

## <a name="what-is-a-test-drive-solution"></a>¿Qué es una solución de versión de prueba?

Una solución de versión de prueba permite a los clientes probar una aplicación real, sin registrarse en un plan de Power apps ni instalar ninguna aplicación. Los clientes simplemente inician sesión en AppSource.com con su cuenta de Azure Active Directory (AAD) y ejecutan la aplicación en un explorador web. Sin la versión de prueba, los clientes solo pueden leer acerca de la aplicación o ver un vídeo que la describe. Con la versión de prueba, los clientes se hacen una idea mejor acerca de la solución y de la funcionalidad de la aplicación. Y tienen una experiencia de uso real de la aplicación. Los clientes no pueden ver cómo está construida la aplicación, por lo que la propiedad intelectual está protegida. Recopilamos y compartimos información de clientes potenciales que han ejecutado la versión de prueba de la aplicación para ayudar en el desarrollo de su negocio.

Este es el ejemplo de la [descripción de una aplicación](https://go.microsoft.com/fwlink/?linkid=848867) en AppSource.com:

![Ejemplo de descripción en AppSource ](./media/dev-appsource-test-drive/sample-app-source-listing.png)

Al seleccionar el vínculo **evaluación gratuita** desde la lista de aplicaciones anterior, se inicia la aplicación de Power apps Test Drive directamente en el explorador del usuario:

![Ejecución de la aplicación web de ejemplo](./media/dev-appsource-test-drive/sample-app-web-player.png)

## <a name="how-do-i-build-a-test-drive-solution"></a>¿Cómo se puede crear una solución de versión de prueba?
Compilar una aplicación para una solución de versión de prueba es igual que compilar cualquier aplicación en Power Apps, pero se usan datos incrustados en lugar de conexiones de datos externos. El uso de datos incrustados reduce la barrera de implementación de la aplicación en el cliente, por lo que no hay ninguna fricción para probarlo. La solución completa que se distribuye en última instancia a los clientes normalmente incluye conexiones de datos, pero los datos incrustados funcionan bien para una solución de versión de prueba.

Power apps admite de forma nativa la creación de aplicaciones con datos incrustados, por lo que solo necesita datos de ejemplo para su aplicación. Estos datos se deben capturar en un archivo de Excel como una o varias tablas. En Power Apps, extrae los datos de las tablas de Excel en la aplicación y trabaja con ellos allí, en lugar de hacerlo a través de una conexión externa. El siguiente proceso en tres pasos muestra cómo extraer datos y usarlos en la aplicación.

### <a name="step-1-import-data-into-the-app"></a>Paso 1: Importar datos en la aplicación
Suponga que tiene un archivo de Excel con dos tablas: **SiteInspector** y **SitePhotos**.

![Tablas de Excel que se importarán](./media/dev-appsource-test-drive/excel-file.png)

Importe estas dos tablas en Power apps mediante la opción **Agregar datos estáticos a la aplicación**.

![Agregar datos estáticos a la aplicación](./media/dev-appsource-test-drive/static-data.png)

Ahora dispone de las tablas como orígenes de datos en la aplicación.

![Tablas de Excel como orígenes de datos importados](./media/dev-appsource-test-drive/data-sources.png)

### <a name="step-2-handling-read-only-and-read-write-scenarios"></a>Paso 2: Administración de escenarios de solo lectura y de lectura y escritura
Los datos que importó son de tipo *estático*, por lo tanto, de solo lectura. Si la aplicación es de solo lectura (es decir, solo muestra los datos al usuario), se hace referencia a las tablas directamente en la aplicación. Por ejemplo, si desea tener acceso al campo **Title** de la tabla **SiteInspector**, utilice **SiteInspector.Title** en la fórmula.

Si la aplicación es de lectura y escritura, primero extraiga los datos de cada tabla en una *colección*, que es una estructura de datos tabulares en Power apps. A continuación, trabaje con la colección en lugar de con la tabla. Para extraer datos de las tablas **SiteInspector** y **SitePhotos** en las colecciones **SiteInspectorCollect** y **SitePhotosCollect**:

```powerapps-dot
ClearCollect( SiteInspectorCollect, SiteInspector ); 
ClearCollect( SitePhotosCollect, SitePhotos )
```

La fórmula borra ambas colecciones y, a continuación, recopila los datos de cada tabla en la colección adecuada:

* Llame a esta fórmula en alguna parte de la aplicación para cargar los datos.
* Para ver todas las colecciones de la aplicación, vaya a **Archivo** > **Colecciones**.
* Para más información, consulte [Crear y actualizar una colección en la aplicación](../canvas-apps/create-update-collection.md).

Ahora, si desea tener acceso al campo **Title**, use **SiteInspectorCollect.Title** en la fórmula.

### <a name="step-3-add-update-and-delete-data-in-your-app"></a>Paso 3: Agregar, actualizar y eliminar datos de la aplicación
Ha visto cómo leer datos directamente y desde una colección; ahora, vamos a mostrarle cómo agregar, actualizar y eliminar datos de una colección:

**Para agregar una fila a una colección**, use [Collect( DataSource, Item, ... )](../canvas-apps/functions/function-clear-collect-clearcollect.md):

```powerapps-dot
Collect( SiteInspectorCollect,
    {
        ID: Value( Max( SiteInspectorCollect, ID ) + 1 ),
        Title: TitleText.Text,
        SubTitle: SubTitleText.Text,
        Description: DescriptionText.Text
    }
)
```

**Para actualizar una fila de una colección**, use [UpdateIf( DataSource, Condition1, ChangeRecord1 [, Condition2, ChangeRecord2, ...] )](../canvas-apps/functions/function-update-updateif.md):

```powerapps-dot
UpdateIf( SiteInspectorCollect,
    ID = record.ID,
    {
        Title: TitleEditText.Text,
        SubTitle: SubTitleEditText.Text,
        Description: DescriptionEditText.Text
    }
)
```

**Para eliminar una fila de una colección**, use [RemoveIf( DataSource, Condition [, ...] )](../canvas-apps/functions/function-remove-removeif.md):

```powerapps-dot
RemoveIf( SiteInspectorCollect, ID = record.ID )
```

> [!NOTE]
> Las colecciones contienen datos solo mientras se ejecuta la aplicación; los cambios se descartan cuando se cierra la aplicación.

En resumen, puede crear una versión de la aplicación con datos insertados, que simula la experiencia de la aplicación con conexión a datos externos. Después de insertar los datos, estará listo para publicar la aplicación como una solución de versión de prueba en AppSource.com.

## <a name="how-do-i-list-my-test-drive-solution-on-appsourcecom"></a>¿Cómo muestro mi solución de versión de prueba en AppSource.com?
Ahora que la aplicación está lista, es el momento de publicarla en AppSource.com. Para iniciar este proceso, complete el formulario de la [aplicación](https://powerapps.microsoft.com/partners/get-listed/) en Power apps.com.

Una vez realizada la solicitud, recibirá un correo electrónico con las instrucciones de envío de la aplicación para que sea publicada en AppSource.com. También se puede descargar la documentación de incorporación que contiene todo el proceso de [aquí](https://go.microsoft.com/fwlink/?linkid=851031).

