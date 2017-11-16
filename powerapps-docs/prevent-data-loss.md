---
title: "Directivas de prevención de pérdida de datos (DLP) | Microsoft Docs"
description: "Introducción a las directivas de prevención de pérdida de datos para Microsoft PowerApps."
services: 
suite: powerapps
documentationcenter: na
author: msftman
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/28/2016
ms.author: deonhe
ms.openlocfilehash: 67fb178a95131e041d0ea3ac5f3c2f24095505ed
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="data-loss-prevention-dlp-policies"></a>Directivas de prevención de pérdida de datos (DLP)
## <a name="what-is-a-data-loss-prevention-policy"></a>¿Qué es una directiva de prevención de pérdida de datos?
Los datos de una organización son fundamentales para su éxito. Los datos tienen que estar disponibles de inmediato para la toma de decisiones, pero tienen que protegerse de manera que no se compartan con personas que no deben tener acceso a ellos. Para proteger estos datos, Microsoft PowerApps (PowerApps) le proporciona la capacidad de crear y aplicar directivas que definen qué datos empresariales específicos de los conectores/servicios al consumidor pueden compartirse. Estas directivas que definen cómo se pueden compartir los datos se conocen como directivas de prevención de pérdida de datos (DLP).  

## <a name="why-create-a-dlp-policy"></a>¿Por qué crear una directiva DLP?
Debe crear directiva DLP para definir claramente qué datos empresariales de servicios al consumidor pueden compartirse. Por ejemplo, es posible que una organización que utiliza PowerApps no desee que los datos empresariales que se almacenan en SharePoint se publiquen automáticamente en su publicación de Twitter. Para evitar esto, puede crear una directiva DLP que bloquee la utilización de esos datos de SharePoint como fuente de tuits.

## <a name="benefits-of-a-dlp-policy"></a>Ventajas de una directiva DLP
* Garantiza que los datos se administran de manera uniforme en toda la organización  
* Evita que los datos empresariales importantes se publiquen accidentalmente en servicios como sitios de redes sociales.   

## <a name="managing-dlp-policies"></a>Administración de directivas DLP
**Requisitos previos**  
Para crear, editar o eliminar las directivas de DLP son necesarios los siguientes elementos:

* Permisos del administrador de inquilinos o entornos. Puede aprender más acerca de los permisos en el [tema de entornos](environments-administration.md)

## <a name="create-a-dlp-policy"></a>Crear una directiva DLP
**Requisitos previos**  
Para crear una directiva DLP, debe tener permisos para al menos un entorno.  

Siga estos pasos para crear una directiva DLP que impida que se publiquen en Twitter los datos almacenados en la base de datos de SharePoint:  

1. Cuando esté en la pestaña Directiva de datos, seleccione el vínculo **Nueva directiva**:  
   ![Iniciar sesión](./media/prevent-data-loss/create-policy-1.png)    
2. Escriba el nombre de la directiva DLP como *Acceso a los datos seguros para Contoso* en la etiqueta **Nombre de la directiva de datos** en la parte superior de la página que se abre:   
   ![Iniciar sesión](./media/prevent-data-loss/create-policy-2.png)  
3. Seleccione el [entorno](environments-administration.md) en la pestaña **Se aplica a**.  
   ![Iniciar sesión](./media/prevent-data-loss/create-policy-3.png)  
4. Seleccione la pestaña **Grupos de datos**:  
   ![Iniciar sesión](./media/prevent-data-loss/create-policy-4.png)  
5. Seleccione el vínculo **+ Agregar** situado dentro del cuadro de grupo **Solo datos empresariales**:    
   ![Iniciar sesión](./media/prevent-data-loss/create-policy-5.png)  
6. Seleccione los servicios de **SharePoint** y **Salesforce** desde la página **Agregar servicios**:  
   ![Iniciar sesión](./media/prevent-data-loss/create-policy-6.png)  
7. Seleccione el botón **Agregar servicios** botón para agregar los servicios que seleccionó en la lista de servicios que permiten compartir datos empresariales:    
   ![Iniciar sesión](./media/prevent-data-loss/create-policy-7.png)  
8. Seleccione **Guardar directiva**:  
   ![Iniciar sesión](./media/prevent-data-loss/create-policy-8.png)  
9. Transcurridos unos minutos, la nueva directiva DLP se mostrará en la lista de directivas de prevención de pérdida de datos:  
   ![Iniciar sesión](./media/prevent-data-loss/create-policy-9.png)  
10. **Opcional** Envíe un correo electrónico u otra comunicación al equipo avisándoles de que hay ahora una nueva directiva DLP disponible.

Enhorabuena, ahora ha creado una directiva DLP que permite a la aplicación compartir datos entre SharePoint y Salesforce y que bloquea el uso compartido de datos con cualquier otro servicio.  

## <a name="find-a-dlp-policy"></a>Buscar una directiva DLP
### <a name="admins"></a>Administradores
Los administradores pueden usar la característica de búsqueda desde el Centro de administración para buscar directivas DLP específicas.  

**NOTA:** Los administradores deben publicar todas las directivas DLP para que los usuarios de la organización sean conscientes de las directivas antes de crear PowerApps.

### <a name="makers"></a>Responsables de toma de decisiones
Si no tiene permisos de administrador y desea obtener más información acerca de las directivas DLP en su organización, póngase en contacto con su administrador. También puede obtener más información en el [tema de entornos del responsable de la toma de decisiones](environments-overview.md)  

**NOTA:** Solo los administradores pueden editar o eliminar las directivas DLP.  

## <a name="edit-a-dlp-policy"></a>Editar una directiva DLP
1. Inicie el Centro de administración dirigiéndose a https://admin.powerapps.com.   
2. En el Centro de administración que se inicia, seleccione la **datos directivas** vínculo en el lado izquierdo.  
   ![Iniciar sesión](./media/prevent-data-loss/2.png)  
3. Busque en la lista de directivas DLP existentes y seleccione el vínculo de edición situado junto a la directiva que desee editar:  
   ![Iniciar sesión](./media/prevent-data-loss/3.png)  
4. Realice los cambios que desee realizar. Puede modificar el entorno o los servicios en los grupos de datos, por ejemplo.  
5. Seleccione **Guardar directiva** para guardar los cambios:  
   ![Iniciar sesión](./media/prevent-data-loss/create-policy-8.png)  

La directiva se ha actualizado ahora. Puede confirmar que se han realizado los cambios en la directiva buscándola en la lista de prevención de pérdida de datos y revisando sus propiedades.   

## <a name="delete-a-dlp-policy"></a>Eliminar una directiva DLP
1. Inicie el Centro de administración dirigiéndose a https://admin.powerapps.com.    
2. En el Centro de administración que se inicia, seleccione la **datos directivas** vínculo en el lado izquierdo.  
   ![Iniciar sesión](./media/prevent-data-loss/2.png)  
3. Busque en la lista de directivas de DLP existentes y seleccione el vínculo de eliminación que aparece junto a la directiva que desea eliminar:  
   ![Iniciar sesión](./media/prevent-data-loss/3-delete.png)  
4. Confirme que realmente desea eliminar la directiva seleccionando el botón **Eliminar**:  
   ![Iniciar sesión](./media/prevent-data-loss/4.png)  

La directiva se ha eliminado ahora. Puede confirmar que la directiva ya no aparece en la lista de directivas de prevención de pérdida de datos seleccionando el vínculo **Directivas de datos** de la izquierda y revisando la lista de directivas.   

## <a name="dlp-policy-permissions"></a>Permisos de las directivas DLP
Solo los administradores de inquilinos y entornos pueden crear y modificar directivas DLP. Puede aprender más acerca de los permisos en el tema de [entornos](environments-administration.md).  

## <a name="next-steps"></a>Pasos siguientes
* [Aprender más acerca de los entornos](environments-administration.md)  
* [Más información acerca de Microsoft PowerApps](getting-started.md)  
* [Más información acerca del Centro de administración](introduction-to-the-admin-center.md)  

