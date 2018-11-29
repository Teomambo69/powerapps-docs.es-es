---
title: Dependencias de recursos web (aplicaciones basadas en modelos) | Microsoft Docs
description: Obtenga más información sobre la definición de dependencias entre recursos web en CDS para aplicaciones
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: shilpas
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="web-resource-dependencies"></a>Dependencias de recursos web

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/web-resource-dependencies -->

Puede definir dependencias entre otros recursos web. La finalidad principal de esta característica es permitir asociación de recursos web de cadena (RESX) con los recursos web de JavaScript que se utilizan. También es la forma en que se pueden configurar los recursos web requeridos por los recursos web HTML para usarlos sin conexión para que también estén disponible sin conexión. 

Sin embargo, hay algunos otros comportamientos que los desarrolladores que usan recursos web de JavaScript pueden aprovechar.

En la siguiente imagen se muestra la ficha dependencias en el formulario de recursos web. En la lista superior se configuran las dependencias entre recursos web. Las dependencias del atributo están configuradas mediante la lista inferior. Las dependencias del atributo solo están disponibles para los recursos web de JavaScript. Más información [Dependencias del atributo](#attribute-dependencies)

![Etiqueta de las dependencias de recursos web](media/web-resource-dependencies.PNG)

Puede definir dependencias dentro de componentes de la solución en una solución. Hasta aplicaciones basadas en modelos la finalidad principal de estas dependencias era evitar la eliminación de componentes de una solución cuando otro componente de la solución depende de él. Con aplicaciones basadas en modelos el comportamiento para recursos web de JavaScript se ha mejorado para que los otros recursos web listados como una dependencia a la web de JavaScript se carguen junto con los recursos de web JavaScript. 

> [!NOTE]
> La dependencia solo se establece después de que se ha configurado y se publica el recurso web. Las dependencias de recursos web no publicados no se aplicarán hasta que se publiquen los recursos web.

El escenario más común es asociar recursos web de cadena (RESX) a un recurso web JavaScript que depende de él. Habrá un recurso web de cadena (RESX) para cada idioma que está asociado al recurso de JavaScript web que lo utiliza. Cuando se cargan los recursos web de JavaScript, también automáticamente se cargarán los valores traducidos de idioma preferido del usuario y el idioma de base de la organización para que estén disponibles para su uso. Puesto que se debe crear dependencias de solución entre estos recursos de todos modos, tendrá las ventajas adicionales de saber que los recursos dependientes de RESX se cargarán automáticamente cuando los necesite.

Sin embargo, las dependencias de recursos web no se limitan a recursos web RESX solamente. Puede asociar un recurso web de JavaScript a cualquier otro tipo de recursos web para crear dependencias que originan los recursos web asociados para que se carguen junto con los recursos web JavaScript. Esto ahorra tiempo, porque no se deben cargar explícitamente recursos web dependientes de varios al registrar una secuencia para un evento de forma, simplemente registre la secuencia principal y permita que la configuración de dependencia cargue el resto. Incluso puede crear una cadena de dependencias porque los recursos web JavaScript que se cargan debido a los principales recursos web JavaScript incluyen cualquier recurso web asociado a ellos.

> [!IMPORTANT]
> Las dependencias de recursos web no le proporcionan ningún control sobre el orden en el que se cargan los recursos web. Todos los recursos web se cargan asincrónicamente y en paralelo. Si tiene un recursos web de JavaScript que depende de otro recursos web de JavaScript que se cargan y se inicializan antes de que se puedan inicializar, debe administrar esa dependencia de otra forma.

<a name="attribute-dependencies"></a>

# <a name="attribute-dependencies"></a>Dependencias de atributos
<!--TODO: Add links to the attribute and attribute.controls collection definitions in the Client API reference --> A partir de aplicaciones basadas en modelos, si los recursos web JavaScript dependen de un valor de atributo de la entidad que no desea mostrar en el formulario, puede establecer el atributo como una dependencia para los recursos web de JavaScript. Esto significa que el atributo estará disponible en el conjunto de atributos de API del cliente para que pueda obtener o establecer el valor en el código. Cuando se agrega una dependencia de este modo, el conjunto de controles de atributo estará vacía porque no habrá ningún control en el formulario.

Antes de esta característica se debe agregar manualmente el atributo al formulario y, después, configurar el control para ocultar. Ahora puede establecer esta dependencia más directamente y eliminar la posibilidad de que alguien quite el campo oculto del formulario. 


## <a name="see-also"></a>Vea también
[Recursos web](web-resources.md)<br />
[Crear recursos web accesibles](create-accessible-web-resources.md)<br />
[Recursos web de página web (HTML)](webpage-html-web-resources.md)<br />
[Recursos web de script (JScript)](script-jscript-web-resources.md)<br />
[Recursos web de imagen (JPG, PNG, GIF, ICO)](image-web-resources.md)<br />
[Recursos web de hoja de estilo (XSL)](stylesheet-xsl-web-resources.md)<br />
[Recursos web (XML) de datos](data-xml-web-resources.md)<br />
[Recursos web CSS](css-web-resources.md)<br />
[Recursos web RESX](resx-web-resources.md)<br />
[Referencia de la entidad WebResource](../common-data-service/reference/entities/webresource.md)<br />
[Ejemplo: pasar varios valores a un recurso web mediante el parámetro de datos](sample-pass-multiple-values-web-resource-through-data-parameter.md)<br />
[Ejemplo: importar archivos como recursos web](sample-import-files-web-resources.md)<br />
