---
title: Comprender cómo se combinan las soluciones administradas (Common Data Service) | Microsoft Docs
description: 'Para evitar que múltiples soluciones instaladas interfieran entre sí, siga las prácticas recomendadas mientras construye una solución.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: shmcarth
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="understand-how-managed-solutions-are-merged"></a>Comprender cómo se combinan soluciones administradas

Al preparar la solución administrada para la instalación, recuerde que es posible que una organización tenga varias soluciones instaladas o que admita la instalación de otras soluciones en el futuro. Cree una solución que siga las prácticas recomendadas de manera que su solución no interfiera con otras soluciones.  
  
 Los procesos que utiliza Common Data Service para combinar las personalizaciones hacen hincapié en mantener la funcionalidad de la solución. Si bien se hacen todos los esfuerzos necesarios para mantener la presentación, algunas incompatibilidades entre las personalizaciones pueden requerir que la resolución computarizada modifique algunos detalles de la presentación a favor de mantener la funcionalidad de la personalización.  
  
<a name="BKMK_MergingFormCustomizations"></a>   

## <a name="merge-form-customizations"></a>Combinar personalizaciones de formularios  
 Las únicas personalizaciones de formularios que deben combinarse son aquellas que se realizan en cualquiera de los formularios de entidad existentes en la organización. Normalmente, esto significa que las personalizaciones de formularios solo se deben combinar cuando la solución personaliza los formularios que se incluyeron para las entidades creadas cuando se instaló Common Data Service. Una forma de evitar la combinación de formularios consiste en proporcionar formularios nuevos para cualquier entidad de Common Data Service. Los formularios para entidades personalizadas no requerirán combinación a menos que esté creando una solución que actualice o modifique una solución administrada existente que creó las entidades personalizadas y los formularios respectivos.  
  
 Cuando una solución se empaqueta como una solución administrada, las definiciones de formulario almacenadas en FormXML se comparan con el FormXML original y solo se incluyen las diferencias en la solución administrada. Cuando la solución administrada se instala en una organización nueva, las diferencias de personalización del formulario se combinan con el FormXML para que el formulario existente cree una nueva definición del formulario. Esta nueva definición del formulario es lo que ve el usuario o y lo que puede modificar un personalizador del sistema. Cuando se desinstala la solución administrada, solo se quitan los elementos del formulario que se encuentran en la solución administrada.  
  
 Cuando se agregan elementos nuevos a un formulario que se debe combinar, se recomienda incluir los elementos nuevos dentro de elementos contenedores nuevos (fichas o secciones). Las adiciones a un contenedor se anexarán al final del contenedor. Por ejemplo, los campos que se agregan a una sección se colocarán al final de la sección. Se espera que un personalizador que instala una solución modifique el formulario para reorganizar los elementos después de la instalación.  
  
 Las soluciones administradas que contienen formularios que usan nuevos roles de seguridad dependen de esos roles. Debe incluir estos roles de seguridad en la solución administrada. Si hay roles de seguridad asociados a un formulario que no está en la organización en la que se instala la solución administrada, la instalación se realizará correctamente pero es posible que los formularios no se asocien con los roles de seguridad. Cuando se desinstala la solución administrada, se quitarán los roles de seguridad incluidos en ella. Cualquier formulario que esté fuera de la solución administrada ya no se podrá asociar a esos roles de seguridad.  
  
> [!NOTE]
>  Cuando una entidad de solución administrada contiene varios formularios y el formulario de entidad de la organización también contiene varios formularios, los nuevos formularios no se agregan en la parte inferior de la lista de formularios disponible: se intercalan con los formularios de entidad originales.  
  
<a name="BKMK_MergingNavigationCustomizations"></a>   
## <a name="merge-navigation-sitemap-customizations"></a>Combinar personalizaciones de navegación (mapa del sitio)  
 Cuando una solución se empaqueta como administrada, el XML de mapa del sitio se compara con el XML de mapa del sitio original y cualquier otra personalización realizada en el mapa del sitio. Solo se incluyen las diferencias en la solución administrada. Estas diferencias incluyen elementos que se han cambiado, movido, agregado o quitado. Cuando la solución administrada se instala en una nueva organización, los cambios del mapa del sitio se combinan con el XML de mapa del sitio encontrado para la organización donde se está instalando la solución administrada. Una nueva definición del mapa del sitio es lo que ven los usuarios.  
  
 En este punto, un personalizador puede exportar el mapa del sitio a una solución no administrada y la definición del mapa del sitio incluirá todos los elementos del mapa del sitio activo. A continuación, el personalizador puede modificar el mapa del sitio y volver a importarlo como una personalización no administrada.  Posteriormente, si se desinstala la solución administrada, se hará referencia al XML de mapa del sitio que se importó con la solución administrada para quitar los cambios introducidos con esa solución administrada. A continuación, se calcula un nuevo mapa de sitio activo.  
  
 Siempre que un nuevo elemento visible se agregue al mapa del sitio, aparece en la parte inferior de cualquier contenedor al que pertenece. Por ejemplo, una nueva área aparece en la parte inferior del área de navegación. Para colocar los elementos que se han agregado, debe exportar el mapa del sitio, editarlo para definir la ubicación exacta y volver a importarlo como una solución no administrada.  
  
> [!NOTE]
>  Solo se puede aplicar una personalización del mapa del sitio entre publicaciones. Las personalizaciones del mapa del sitio sin publicar se perderán cuando se importe una nueva definición del mapa del sitio.  
  
<a name="BKMK_MergingOptionSetOptions"></a>   
## <a name="merge-option-set-options"></a>Combinar opciones del conjunto de opciones  
 Cada nueva opción del conjunto de opciones se inicializa con un valor entero asignado que incluye un prefijo de valor de opción. El prefijo de valor de opción es un conjunto de cinco dígitos que se antepone el valor de opción. Un prefijo de valor de opción se genera en función del prefijo de personalización de los editores de soluciones pero se puede establecer en cualquier valor. El prefijo de valor de opción ayuda a diferenciar las nuevas opciones del conjunto de opciones creadas en el contexto de un editor de soluciones específico y reduce la oportunidad para las colisiones de los valores de opción. Se recomienda el uso del prefijo de valor de opción, pero no es obligatorio.  
  
 Por lo general, una solución administrada actualiza o agrega opciones para los conjuntos de opciones que ya están en la organización, por ejemplo, los conjuntos de opciones de la Categoría o Sector de la cuenta. Cuando una solución administrada modifica las opciones disponibles en un conjunto de opciones, todas las opciones definidas en la solución administrada están disponibles en la organización. Cuando se desinstala la solución administrada, las opciones del conjunto de opciones regresan a su estado original.  
  
### <a name="see-also"></a>Vea también  
 [Planear el desarrollo de la solución](/dynamics365/customer-engagement/developer/plan-solution-development)   
 [Usar propiedades administradas](use-managed-properties.md)   
 [Personalizar formularios de entidad](/dynamics365/customer-engagement/developer/customize-dev/customize-entity-forms)   
 [Cambiar navegación de la aplicación con el mapa del sitio](/dynamics365/customer-engagement/developer/customize-dev/change-application-navigation-using-sitemap)
