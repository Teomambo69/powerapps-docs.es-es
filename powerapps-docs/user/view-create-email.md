---
title: Ver y crear correo electrónico en aplicaciones controladas por modelos | MicrosoftDocs
description: Ver y crear correo electrónico mientras se usa una aplicación controlada por modelos.
ms.date: 02/03/2020
ms.service:
- dynamics-365
ms.topic: article
author: lalexms
ms.author: lalexms
manager: shujoshi
ms.openlocfilehash: 7a0dee04334f52518c1746b6650f75ebfb67634d
ms.sourcegitcommit: 68a31e3fa4d1635ccf4cd8bd9da5fba1bfecefa4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/06/2020
ms.locfileid: "77051922"
---
# <a name="preview-view-and-create-email-through-the-activities-grid"></a>Vista previa: ver y crear correo electrónico a través de la cuadrícula de actividades

Ver y crear correo electrónico a través de la cuadrícula de actividades es una característica de acceso temprano. Puede participar pronto para habilitar estas características en su entorno. Esto le permitirá probar estas características y después adoptarlas en sus entornos. Para obtener información sobre cómo habilitar estas características, consulte [participación en las actualizaciones de la versión 1 de 2020](https://docs.microsoft.com/power-platform/admin/opt-in-early-access-updates).

Las aplicaciones controladas por modelos de Dynamics 365 permiten interactuar con los clientes a través del correo electrónico. La funcionalidad de correo electrónico le permite:

- Ver y responder a correos electrónicos. 

- Use la funcionalidad común de la barra de herramientas de correo electrónico y controles de editor de texto enriquecido. 

- Ver e insertar imágenes alineadas con la funcionalidad de arrastrar y colocar o de copiar y pegar. 

- Cree el correo electrónico en una ventana emergente.  

- Plantillas de vista previa antes de aplicarlas. 



## <a name="view-your-email"></a>Ver el correo electrónico

Para ver el correo electrónico:

1. En el mapa del sitio de la aplicación controlada por modelos, seleccione **actividades**. 

2. Seleccione la lista desplegable **todas las actividades** y, a continuación, seleccione **mis correos electrónicos recibidos**.

    ![Ver correo electrónico](media/view-email.png "Mostrar correos electrónicos recibidos")

3. Seleccione el correo electrónico que desea ver para abrirlo. Se abrirá el correo electrónico, donde podrá responder al remitente y a los destinatarios o reenviarlo.

## <a name="create-email"></a>Crear correo electrónico

En los pasos siguientes se detalla cómo crear un correo electrónico.

1. En el mapa del sitio de la aplicación controlada por modelos, seleccione **actividades**.

2. En la barra de comandos, seleccione **correo electrónico**. Se abre una nueva ventana de correo electrónico.

    ![crear: correo electrónico](media/create-email.png "Crear un nuevo correo electrónico")

    El campo **desde** se rellena automáticamente en función del usuario que ha iniciado la sesión actual.

3. Escriba el correo electrónico directamente en el compositor o seleccione **Insertar plantilla** para buscar y aplicar una plantilla. Para obtener más información sobre la inserción de una plantilla de correo electrónico, consulte [inserción de una plantilla de correo electrónico](insert-email-template.md).

4. Para redactar el correo electrónico en una ventana de pantalla completa, seleccione el icono de expandir.

    ![correo electrónico-expandir-ventana](media/email-expand-window.png "Expandir la ventana correo electrónico")

    El cuadro de mensaje tiene un editor de texto enriquecido que le permite crear contenido enriquecido y con formato correcto para los mensajes de correo electrónico con énfasis. El editor aporta características comunes del procesador de texto como: 

    - Copiar formato
    - Fuente y tamaño
    - Negrita, cursiva y subrayado
    - Color de fondo para el texto y el color del texto
    - Lista numerada y con viñetas
    - Reducir y aumentar sangría
    - Comilla de bloque
    - Alineación del texto (alinear a la izquierda, centro y derecha)
    - Vincular y desvincular
    - Tachado de texto
    - Imagen
    - Dirección del texto de derecha a izquierda y de izquierda a derecha
    - Deshacer y rehacer
    - Quitar formato
    - Table

    ![correo electrónico-barra de herramientas](media/email-toolbar.png "Usar las características del editor de texto enriquecido")

5. Cuando haya terminado, seleccione **Enviar**.


### <a name="see-also"></a>Vea también

[Configuración del correo electrónico mejorado](https://docs.microsoft.com/power-platform/admin/system-settings-dialog-box-email-tab)<br>
[Insertar una plantilla de correo electrónico](insert-email-template.md)
