---
title: Exportación e importación de recursos | Microsoft Docs
description: Exportación e importación de recursos en PowerApps
author: nimakms
manager: kvivek
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.date: 07/28/2017
ms.author: nimak
ms.openlocfilehash: db5861b9f598045436ad0bf796f04ed1df4b8903
ms.sourcegitcommit: 2e7b621066cdc3e7be329d5213ecfee0b4223641
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2018
ms.locfileid: "39349763"
---
# <a name="export-and-import-resources"></a>Exportar e importar recursos
Si ha creado varios entornos para admitir el desarrollo de la base de datos y las aplicaciones, debe mover los cambios de un entorno a otro. Puede usar **Exportar recursos** e **Importar recursos** para mover recursos entre entornos.

## <a name="why-use-multiple-environments"></a>¿Por qué usar varios entornos?
Cada entorno contiene recursos, como entidades, flujos y aplicaciones, que crea o modifica durante el proceso de desarrollo. 

Por lo general, el desarrollo se realiza en el mismo entorno que el que usan los usuarios finales de la organización. Este entorno se conoce como entorno predeterminado. Resulta relativamente fácil administrar cambios en los recursos del mismo entorno. Se validan los cambios para asegurarse de que todas las aplicaciones y los procesos de negocio esenciales sean funcionales y se libera la aplicación.

En ocasiones, el desarrollo y las pruebas se llevan a cabo en entornos independientes y los cambios se mueven al entorno predeterminado cuando están listos para los usuarios finales. Existen varios motivos por los que podría usar entornos independientes. Por ejemplo, puede que haya utilizado un entorno independiente cuando evaluó inicialmente el sistema. Como alternativa, podría minimizar el riesgo que supone realizar cambios en el entorno predeterminado. Los entornos independientes proporcionan aislamiento, dado que los cambios se hacen en un entorno diferente del predeterminado. Según el alcance de los riesgos, podría crear un entorno de ensayo adicional. En este caso, tendrá un entorno de desarrollo, uno de ensayo y uno predeterminado.

## <a name="moving-resource-changes"></a>Mover los cambios de recursos
Para mover recursos por medio de procesos independientes de exportación e importación, se usan archivos de paquete (.zip). El archivo de paquete se exporta, se guarda en almacenamiento local, se envía al administrador del entorno de destino y después se importa al entorno de destino. El proceso de importación suele ir seguido de pruebas de validación para ayudar a garantizar que ningún proceso de negocio esencial se vea afectado negativamente.

La funcionalidad para la importación y la exportación de recursos está disponible en la sección **Entornos** del centro de administración. Tanto la exportación como la importación se producen en el contexto de un entorno seleccionado.

### <a name="export-resources"></a>Exportar recursos
El paquete de exportación contendrá todos los cambios de **entidades y listas desplegables**. Estamos trabajando para hacer posible la exportación de más tipos de recursos, como aplicaciones, flujos, conectores, roles, etc. Esta opción le permite mover el contenido de un entorno a otro.

1. En el [centro de administración](https://admin.powerapps.com), en el panel de navegación izquierdo, haga clic en **Entornos**.
2. Seleccione el entorno de origen.
3. En la esquina superior derecha, haga clic en **Exportar recursos**.
4. Elija los recursos con los que desea comenzar:
   1. Seleccione la pestaña correspondiente a un tipo de recurso que desea seleccionar, por ejemplo, **Entidades**.
   2. Para seleccionar todos los recursos de ese tipo, haga clic en la casilla del encabezado, o seleccione los recursos individualmente.
   3. Haga clic en **Siguiente**.
5. Incluya los recursos relacionados si es necesario:
   1. Si detectamos recursos relacionados, le mostraremos una lista con una selección previa.
   2. Para excluir todos los recursos relacionados, haga clic en la casilla del encabezado o anule la selección de cada recurso individualmente.
   3. Haga clic en **Siguiente**.
6. Agregue un **Nombre** para el paquete exportado.
7. También puede personalizar las acciones de configuración para que se realicen al importar los recursos:
   1. Para cada recurso, haga clic en **Configuración de importación** para ver un cuadro de diálogo.
   2. Seleccione la acción de configuración que desea realizar de forma predeterminada cuando se importe este paquete.
   3. Haga clic en **Guardar**.
8. Haga clic en **Exportar**.
9. Cuando haya terminado la exportación, guarde el archivo de paquete en el almacenamiento local.

También puede hacer clic en **Seleccionar todos los recursos**, en la página de selección de recursos, para incluir todos los recursos de todos los tipos admitidos en el paquete final e ir directamente a la página final de la exportación.

### <a name="import-resources"></a>Importar recursos
El primer paso consiste en seleccionar un archivo de paquete que se exportara desde el entorno de origen. El proceso de importación valida, analiza e intenta importar el paquete.

1. En el [centro de administración](https://admin.powerapps.com), en el panel de navegación, haga clic en **Entornos**.
2. Seleccione el entorno de destino.
3. En la esquina superior derecha, haga clic en **Importar recursos**.
4. Haga clic en **Cargar** y busque un archivo de paquete en el almacenamiento local.
5. Haga clic en **Siguiente** para ir a la página final de importación.
6. Resuelva las advertencias y errores de validación de la importación:
   1. Busque las advertencias o errores, tal y como indica el icono a la izquierda del **Nombre** de un recurso.
   2. Haga clic en el campo **Configuración de importación** o en el icono **Acción** para obtener más información.
   3. Seleccione la acción de configuración de la importación correspondiente.
   4. El paquete que se va a importar se valida automáticamente de nuevo.
7. Continúe con **Importar** si no hay errores.

Si el paquete se ha aplicado solo parcialmente, recibirá un mensaje de error que describe qué se ha importado y qué no.

## <a name="resource-types"></a>Tipos de recursos
El proceso de desarrollo puede conllevar cambios a muchos tipos de recursos. Por ejemplo, si actualiza una aplicación, podría agregar, quitar o actualizar varias entidades o conexiones. Los cambios en algunos tipos de recursos, aunque no todos, se pueden mover entre entornos. En las secciones siguientes se describen los tipos de recursos que se pueden mover.

### <a name="entities-picklists"></a>Entidades, listas desplegables
Puede exportar e importar entidades y listas desplegables, como sigue:

* **Entidades estándar**: solo se mueven las personalizaciones entre los entornos. (No se pueden modificar los campos de serie de las entidades estándar).
* **Entidades personalizadas**: las entidades personalizadas se mueven entre entornos.
* **Listas desplegables personalizadas**: las listas desplegables personalizadas se mueven entre entornos.

## <a name="data"></a>Datos
No se pueden mover datos de la base de datos como parte de la exportación e importación de recursos. Para mover datos, puede usar Microsoft Excel. 

