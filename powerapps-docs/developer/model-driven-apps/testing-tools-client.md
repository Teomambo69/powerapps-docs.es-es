---
title: Herramientas de prueba para desarrollo del lado del cliente (Common Data Service para aplicaciones) | Microsoft Docs
description: Obtenga más información sobre los marcos de prueba para desarrollo del lado del cliente.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: aengusheaney
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="testing-tools-for-client-side-development"></a>Herramientas de pruebas para desarrollo del lado del cliente

Microsoft proporciona un marco de pruebas automatizado de la interfaz de usuario específicamente para aplicaciones basadas en modelos llamado [Easy Repro](https://github.com/Microsoft/EasyRepro). Este marco se crea mediante el proyecto de código abierto de automatización del explorador [SeleniumHQ](https://www.seleniumhq.org/).

Easy Repro proporciona un conjunto de clases y métodos para trabajar con distintas páginas en aplicaciones basadas en modelos de modo que no necesite analizar los elementos HTML de la aplicación al escribir los casos de prueba. Esto hace que las pruebas sean resistentes a cambios en los elementos HTML que forman las páginas de la aplicación.

## <a name="benefits-of-unit-testing"></a>Beneficios de pruebas de unidad

Las pruebas de unidad se recomiendan pero no se requieren. Cuando esté empezando o si la cantidad de código en la solución es relativamente pequeña, puede pensar que dedica más tiempo a escribir pruebas que a las funciones incluidas en la solución.

Los ventajas de las pruebas de unidad empiezan a aumentar cuando la solución se hace más grande y compleja. Para desarrollo del lado del cliente, un marco de trabajo automatizado de interfaz de usuario para probar puede ayudarle a detectar problemas iniciados por acciones del usuario.  

Cuando una solución se desarrolla con pruebas de unidad, los desarrolladores obtienen mayor productividad y un producto de mejor calidad.

### <a name="see-also"></a>Vea también

[Herramientas de pruebas para el desarrollo de servidor](../common-data-service/testing-tools-server.md)<br />
[Vídeo:  Crear y ejecutar prueba de la interfaz de usuario](https://youtu.be/ryWgK34Akt0)<br />
[Publicación de blog: Easy Repro: ¿qué es?](http://www.itaintboring.com/dynamics-crm/easy-repro-what-is-it/)<br />
[Vídeo: Introducción a DevOps](https://youtu.be/AorM792M8nY)
