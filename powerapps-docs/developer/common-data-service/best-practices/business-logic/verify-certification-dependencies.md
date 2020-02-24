---
title: Verificar las dependencias de certificación para complementos que realizan llamadas salientes | MicrosoftDocs
description: Asegúrese de que los certificados de los que depende su código para las llamadas salientes tengan una cadena de certificados válida.
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: ryjones
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 01/08/2020
ms.author: jdaly
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: ee8dd188c1b88aea4aedb8330e4a0251216b0bb5
ms.sourcegitcommit: 5e23beed96cc14efae9ff264405956d59fae1e7c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/09/2020
ms.locfileid: "2945033"
---
# <a name="verify-certification-dependencies-for-plug-ins-making-outbound-calls"></a>Verificar dependencias de certificación para complementos que realizan llamadas salientes

**Categoría**: mantenimiento, compatibilidad

**Potencial de impacto**: alto

<a name='symptoms'></a>

## <a name="symptoms"></a>Síntomas

Puede recibir este error cuando su complemento realiza una llamada https a un recurso externo:

`WebException: The underlying connection was closed: Could not establish trust relationship for the SSL/TLS secure channel.`


<a name='guidance'></a>

## <a name="guidance"></a>Instrucciones

Debe verificar que el sitio con el que desea conectarse tiene una cadena de certificados válida. Utilice una de las herramientas de prueba en línea, como [Prueba de servidor SSL de Qualys SSL Labs](https://www.ssllabs.com/ssltest/analyze.html) para verificar que el sitio proporciona una cadena válida de certificados.


<a name='additional'></a>

## <a name="additional-information"></a>Información adicional

Puede encontrar esto cuando se conecta a un nuevo extremo por primera vez o cuando ha cambiado algo sobre el certificado.

Cuando el código en su complemento que se ejecuta en el espacio aislado intenta conectarse a un extremo externo usando https, el espacio aislado de CDS iniciará una negociación SSL/TLS. El extremo presenta un certificado para usar para el cifrado. Si el certificado tiene uno o más certificados intermedios, debe presentar toda la cadena para completar correctamente la negociación SSL/TLS. Si no se presenta la cadena completa, no se puede establecer comunicación SSL/TLS. 




<a name='seealso'></a>

### <a name="see-also"></a>Vea también

[Escribir un complemento](../../write-plug-in.md) <br /> 
[Establecer KeepAlive en false para interactuar con hosts externos en un complemento](set-keepalive-false-interacting-external-hosts-plugin.md)<br /> 
[Establecer tiempo de espera al realizar llamadas externas en un complemento](set-timeout-for-external-calls-from-plug-ins.md)