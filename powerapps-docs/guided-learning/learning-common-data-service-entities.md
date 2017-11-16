---
title: "Descripción de las entidades de Common Data Service | Microsoft Docs"
description: Defina y utilice las entidades que se corresponden con sus datos y procesos empresariales
services: 
suite: powerapps
documentationcenter: na
author: mgblythe
manager: anneta
editor: 
tags: 
featuredvideoid: JJa6n_YaD-w
courseduration: 8m
ms.service: powerapps
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/09/2016
ms.author: mblythe
ms.openlocfilehash: 3239a2c90edcd4274f9fabbbb47bd110c3ebcee6
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="understand-entities"></a>Entidades
En el primer tema de esta sección, le presentamos Common Data Service, que incluye Common Data Model. A su vez, este modelo contiene entidades. Las entidades son fragmentos de datos compartidos que se pueden modificar, almacenar, recuperar, y con los que se puede interactuar. En este tema, aprenderá más acerca de las entidades, los campos y los tipos de datos.

## <a name="standard-entities"></a>Entidades estándar
Common Data Model incluye un conjunto de entidades estándar para diferentes necesidades empresariales comunes. A continuación se muestran algunas de las entidades estándar.

![Entidades estándar de Common Data Service](./media/learning-common-data-service-entities/standard-entities.png)

Las entidades se agrupan en categorías para que resulte fácil ver cuáles trabajan normalmente juntas en una solución.

| Grupo funcional | Descripción |
| --- | --- |
| Customer Service |Las entidades Customer Service administran los problemas de los clientes, incluido el seguimiento, el escalado y la documentación. |
| Foundation |Las entidades Foundation contienen información relevante para casi cualquier otro grupo de entidades. Este grupo contiene entidades como Address y Currency. |
| People, Organizations y Groups |Estas entidades abarcan un amplio conjunto de personas y organizaciones con las que puede interactuar, incluidos empleados, contratistas, donantes, voluntarios, seguidores, ex alumnos y familias. |
| Purchasing |Las entidades Purchasing permiten crear soluciones de compras. |
| Ventas |Las entidades Sales permiten crear soluciones de ventas integrales, desde seguimiento de clientes potenciales y oportunidades hasta seguimiento de contactos, aceptación y entrega de pedidos o envío de facturas. |

## <a name="fields-and-data-types"></a>Campos y tipos de datos
Cada entidad contiene un conjunto de campos predeterminados que no se pueden cambiar ni eliminar. Algunos de esos campos, como **Contact ID**, son específicos de una entidad. Otros, como **Created on date time**, son comunes a todas las entidades. Para ampliar las entidades estándar, puede agregar campos. Simplemente haga clic o pulse en **Agregar campo** y especifique las propiedades del nuevo campo.

![Campos y tipos de datos de la entidad Contact](./media/learning-common-data-service-entities/contact-entity-fields.png)

Si necesita una entidad que sea completamente diferente (es decir, ampliar una entidad estándar no es suficiente), necesita crear una entidad personalizada. Esto se explicará en el tema siguiente.

Los campos de una entidad tienen un tipo de datos, por ejemplo, número. Resulta útil tener diferentes tipos de datos, en lugar de un solo tipo de datos genérico, porque permite que las aplicaciones realizar todo tipo de cosas interesantes. Por ejemplo, si tiene un campo de tipo número, sus aplicaciones pueden usar un control deslizante cuando un usuario edite ese campo. Puede elegir entre más de doce tipos de datos. En la lista siguiente se muestran algunos tipos representativos:

* Tipos básicos, como texto y número
* Tipos más complejos, como correo electrónico y teléfono
* Tipos especiales, como búsqueda (para la creación de relaciones) y lista de selección (para contener un conjunto fijo de valores de un campo)  

## <a name="working-with-entities"></a>Trabajar con entidades
Al abrir una entidad, verá una gran cantidad de información y varias acciones que puede realizar. Veremos brevemente las pestañas que hay disponibles y las acciones que puede realizar para administrar los datos de la entidad.

![Pestañas de entidad](./media/learning-common-data-service-entities/entity-tabs.png)

* **Campos**: vea los campos y los tipos de datos, y agregue campos; todo ello se explicó anteriormente.
* **Clave**: campo que identifica cada fila de una entidad, como Contact ID para la entidad Contact.
* **Relaciones**: conexiones entre las entidades relacionadas, como Product y Product category. Veremos un ejemplo en el tema siguiente.
* **Grupos de campos**: se usa para controlar distintos comportamientos, como qué campos se muestran automáticamente cuando se crea una pantalla de aplicación en PowerApps.
* **Datos**: examine los datos de ejemplo y sus propios datos después de importarlos.

![Acciones de entidad](./media/learning-common-data-service-entities/entity-actions.png)

* **Abrir en Excel**: si tiene instalado el complemento PowerApps, use esta opción para explorar y editar los datos en Excel.
* **Importar datos**: importe datos desde Excel y archivos CSV.
* **Exportar datos**: exporte datos a un archivo de Excel.
* **Exportar plantilla**: exporte la estructura de una entidad a un archivo de Excel para rellenar el archivo, y vuelva a importarlo a la entidad.
* **Configuración** y **Eliminar**: no están disponibles para las entidades estándar.

## <a name="connecting-to-a-standard-entity-in-powerapps-studio"></a>Conexión a una entidad estándar en PowerApps Studio
Ahora que sabe lo que son las entidades, analizaremos cómo conectarse a la entidad Contact en PowerApps Studio. Haga clic en **Nuevo** y, en **Common Data Service**, haga clic en **Diseño de teléfono**. Se ven las conexiones de datos disponibles a la izquierda y la lista de entidades a la derecha. Intente conectarse por su cuenta y generar una aplicación a partir de la entidad.

![Conexión a una entidad en PowerApps Studio](./media/learning-common-data-service-entities/connect-to-standard-entity.png)

En el tema siguiente, le mostraremos cómo crear entidades personalizadas, así como las relaciones entre las entidades.

