---
title: Detectar datos duplicados con código (Common Data Service para aplicaciones) | Microsoft Docs
description: La detección de duplicados permite a las organizaciones establecer directivas de detección de duplicados y crear reglas de detección de duplicados para entidades de negocio y personalizadas.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="detect-duplicate-data-using-code"></a>Detección de datos duplicados con código

La detección de duplicados permite a las organizaciones establecer directivas de detección de duplicados y crear reglas de detección de duplicados para entidades de negocio y personalizadas. Estas reglas se pueden aplicar en diferentes tipos de registros en Common Data Service (CDS) para aplicaciones. Por ejemplo, una organización puede definir que un cliente potencial es un duplicado de un contacto, si tienen el mismo nombre y número de teléfono. En función de las reglas de detección de duplicados establecidas por el administrador, el sistema advierte al usuario acerca de posibles duplicados cuando el usuario intenta crear nuevos registros o actualizar los registros existentes. Para mantener la calidad de los datos, puede programar un trabajo de detección de duplicados para comprobar si existen duplicados en todos los registros que coincidan con determinados criterios. Para limpiar los datos, puede eliminar, desactivar o combinar los duplicados que surgen del informe de un trabajo de detección de duplicados.

> [!NOTE]
> Para obtener información sobre cómo crear reglas y ejecutar trabajos del sistema para la detección de datos duplicados mediante la interfaz de usuario (IU) consulte [Detectar datos duplicados para poder corregirlos o eliminarlos](/dynamics365/customer-engagement/admin/detect-duplicate-data).

Puede usar el servicio web de API o de la organización para detectar datos duplicados. Los temas en esta sección proporcionan información sobre cómo puede detectar datos duplicados mediante los dos servicios web. 

### <a name="see-also"></a>Vea también

[Habilitar y deshabilitar la detección de duplicados](enable-disable-duplicate-detection.md)<br/>
[Ejecutar detección de duplicados](run-duplicate-detection.md)<br/>
[Mensajes de detección de duplicados](duplicate-detection-messages.md)<br/>
[Entidades de regla de duplicados](duplicaterule-entities.md)

