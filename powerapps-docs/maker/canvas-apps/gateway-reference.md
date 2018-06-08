---
title: Información sobre las puertas de enlace de datos locales | Microsoft Docs
description: Información de referencia, incluida la instalación y solución de problemas, para puertas de enlace de datos locales
documentationcenter: na
author: aftowen
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: canvas
ms.date: 10/20/2017
ms.author: anneta
ms.openlocfilehash: 2c754fa8e479494ae1002e5339d2d8d5eeb2480f
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "32330454"
---
# <a name="understand-on-premises-data-gateways-for-microsoft-powerapps"></a>Información sobre las puertas de enlace de datos locales para Microsoft PowerApps
## <a name="installation-and-configuration"></a>Instalación y configuración
**Requisitos previos**

Mínimo:

* .NET Framework 4.5
* Versión de 64 bits de Windows 7 o Windows Server 2008 R2 (o versiones posteriores)

Recomendado:

* CPU de 8 núcleos
* 8 GB de memoria
* Versión de 64 bits de Windows 2012 R2 (o posteriores)

Consideraciones relacionadas:

* No puede instalar una puerta de enlace en un controlador de dominio.
* No debe instalar una puerta de enlace en un equipo, tales como portátiles, que puedan estar apagados, suspendidos o no conectados a Internet porque la puerta de enlace no se puede ejecutar en estas circunstancias. Además, el rendimiento de la puerta de enlace puede verse afectado en una red inalámbrica.

**Instalación de una puerta de enlace**

1. [Descargue el instalador](http://go.microsoft.com/fwlink/?LinkID=820931) y ejecútelo.

    ![Ejecutar el instalador](./media/gateway-reference/run-installer.png)

2. En la primera pantalla del asistente para la instalación, pulse o haga clic en **Siguiente** para confirmar el aviso acerca de la instalación de una puerta de enlace en un equipo portátil.

    ![Pantalla de aviso](./media/gateway-reference/laptop-reminder.png)

3. Especifique la ubicación donde desea instalar la puerta de enlace, active la casilla para aceptar los términos de uso y la declaración de privacidad y, a continuación, pulse o haga clic en **Instalar**.

4. En los cuadros de diálogo **Control de cuentas de usuario**, pulse o haga clic en **Sí** para continuar.

5. En la siguiente pantalla del asistente, pulse o haga clic en **Iniciar sesión**.

    ![Iniciar sesión](./media/gateway-reference/sign-in.png)

6. Pulse o haga clic en la opción para registrar una nueva puerta de enlace o para migrar, restaurar o utilizar una puerta de enlace existente y, a continuación, pulse o haga clic en **Siguiente**.

    ![Elegir nueva o existente](./media/gateway-reference/new-existing.png)

   * Para configurar una puerta de enlace, escriba un **nombre** y una **clave de recuperación**, pulse o haga clic en **Configurar** y, a continuación, pulse o haga clic en **Cerrar**.

       ![Configuración de una nueva puerta de enlace](./media/gateway-reference/configure-new.png)

       Especifique una clave de recuperación que contenga al menos ocho caracteres, y guárdela en un lugar seguro. Necesitará esta clave si desea migrar, restaurar o utilizar su puerta de enlace.

   * Para migrar, restaurar o utilizar a través de una puerta de enlace existente, proporcione el nombre de la puerta de enlace y su clave de recuperación, pulse o haga clic en **Configurar** y siga las indicaciones adicionales.

       ![Recuperar una puerta de enlace existente](./media/gateway-reference/recover-existing.png)

**Reinicio de la puerta de enlace**

La puerta de enlace se ejecuta como un servicio de Windows, por lo que se puede iniciar y detener de varias maneras. Por ejemplo, puede abrir un símbolo del sistema con permisos elevados en el equipo donde se está ejecutando la puerta de enlace y, a continuación, ejecutar cualquiera de estos comandos:

* Para detener el servicio, ejecute este comando:<br>
  **net stop PBIEgwService**

* Para iniciar el servicio, ejecute este comando:<br>
  **net start PBIEgwService**

**Configuración de un firewall o servidor proxy**

Para más información sobre cómo proporcionar información de proxy para la puerta de enlace, consulte [Configuración de proxy para la puerta de enlace de datos local](https://docs.microsoft.com/power-bi/service-gateway-proxy).

Puede comprobar si el firewall o el servidor proxy podrían estar bloqueando conexiones; para ello, ejecute el siguiente comando desde un símbolo del sistema de PowerShell. Este comando probará la conectividad con Azure Service Bus. Esto solo prueba la conectividad de red y no tiene nada que ver con el servicio de servidor de nube o la puerta de enlace. Ayuda a determinar si el equipo realmente puede obtener acceso a internet.

**Test-NetConnection -ComputerName watchdog.servicebus.windows.net -Port 9350**

El resultado será similar a este ejemplo. Si **TcpTestSucceeded** no es **True**, podría estar bloqueado por un firewall.

    ComputerName           : watchdog.servicebus.windows.net
    RemoteAddress          : 70.37.104.240
    RemotePort             : 5672
    InterfaceAlias         : vEthernet (Broadcom NetXtreme Gigabit Ethernet - Virtual Switch)
    SourceAddress          : 10.120.60.105
    PingSucceeded          : False
    PingReplyDetails (RTT) : 0 ms
    TcpTestSucceeded       : True

Si desea ser exhaustivo, sustituya los valores de **ComputerName** y **Port** por los que se indican en **Configuración de puertos**, más adelante en este tema.

El firewall también podría estar bloqueando las conexiones que Azure Service Bus hace con los centros de datos de Azure. Si es así, quizás desee incluir las direcciones IP de esos centros de datos para su región en una lista de permitidos. Puede obtener una lista de direcciones IP de Azure [aquí](https://www.microsoft.com/download/details.aspx?id=41653).

**Configuración de puertos**

La puerta de enlace crea una conexión de salida hacia Azure Service Bus. Se comunica en los puertos de salida: TCP 443 (valor predeterminado), 5671, 5672 y 9350 a 9354. La puerta de enlace no requiere puertos de entrada.

Más información acerca de las [soluciones híbridas](https://azure.microsoft.com/documentation/articles/service-bus-fundamentals-hybrid-solutions/).

Se recomienda incluir las direcciones IP de su región de datos en la lista de permitidos del firewall. Puede descargar la [lista de direcciones IP de los centros de datos de Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653), que se actualiza semanalmente.

> [!NOTE]
> En la lista de direcciones IP del centro de datos de Azure, las direcciones se muestran en [notación CIDR](http://whatismyipaddress.com/cidr). Por ejemplo, 10.0.0.0/24 no significa de 10.0.0.0 a 10.0.0.24.

Esta es una lista de los nombres de dominio completos que la puerta de enlace utiliza.

| Nombres de dominio | Puertos de salida | Descripción |
| --- | --- | --- |
| *.analysis.windows.net |443 |HTTPS |
| *.login.windows.net |443 |HTTPS |
| *.servicebus.windows.net |5671-5672 |Advanced Message Queuing Protocol (AMQP) |
| *.servicebus.windows.net |443, 9350-9354 |Agentes de escucha de Service Bus Relay a través de TCP (requiere el puerto 443 para la adquisición de tokens de Access Control) |
| *. frontend.clouddatahub.net |443 |HTTPS |
| *.core.windows.net |443 |HTTPS |
| login.microsoftonline.com |443 |HTTPS |
| *.msftncsi.com |443 |Se usa para probar la conectividad a Internet si la puerta de enlace no está accesible para el servicio Power BI. |

**Cuenta de inicio de sesión**

Los usuarios iniciarán sesión con una cuenta de trabajo o académica. Esta es la cuenta de su organización. Si se registró para una oferta de Office 365 y no ha proporcionado su correo electrónico de trabajo real, podría aparecer como nancy@contoso.onmicrosoft.com. La cuenta, en un servicio en la nube, se almacena en un inquilino de Azure Active Directory (AAD). En la mayoría de los casos, el UPN de la cuenta AAD coincidirá con la dirección de correo electrónico.

**Cuenta de servicio de Windows**

La puerta de enlace de datos local está configurada para usar *NT SERVICE\PBIEgwService* como credenciales de inicio de sesión del servicio de Windows. De forma predeterminada, tiene derecho a iniciar como un servicio. Esto es así en el contexto de la máquina en la que va a instalar la puerta de enlace.

Esta no es la cuenta utilizada para conectarse a orígenes de datos locales ni la cuenta profesional o académica con la que inicia sesión en los servicios en la nube.

Si tiene problemas de autenticación con el servidor proxy, puede cambiar la cuenta de servicio de Windows por una cuenta de usuario de dominio o una cuenta de servicio administrado, tal y como se describe en la [configuración del servidor proxy](https://docs.microsoft.com/power-bi/service-gateway-proxy#changing-the-gateway-service-account-to-a-domain-user).

## <a name="tenant-level-administration"></a>Administración de nivel de inquilino 

En la actualidad no hay un solo lugar donde los administradores de inquilinos puedan administrar todas las puertas de enlace que otros usuarios han instalado y configurado.  Si es un administrador de inquilinos, se recomienda pedir a los usuarios de la organización que lo agreguen como administrador para todas las puertas de enlace que instalen. Esto le permite administrar todas las puertas de enlace de la organización a través de la página Configuración de puerta de enlace o de [comandos de PowerShell](https://docs.microsoft.com/power-bi/service-gateway-high-availability-clusters#powershell-support-for-gateway-clusters).

## <a name="frequently-asked-questions"></a>Preguntas más frecuentes
#### <a name="general"></a>General
**Pregunta:** ¿Qué orígenes de datos admite la puerta de enlace?  
**Respuesta:** En el momento de redactar este documento:

* SQL Server
* SharePoint
* Oracle
* Informix
* Filesystem
* DB2

**Pregunta:** ¿Necesito una puerta de enlace para orígenes de datos en la nube, como SQL Azure?  
**Respuesta:** No. Una puerta de enlace solo se conecta a orígenes de datos locales.

**Pregunta:** ¿Cómo se llama en realidad el servicio de Windows?  
**Respuesta:** En servicios, la puerta de enlace se llama **Servicio Power BI Enterprise Gateway**.

**Pregunta:** ¿Hay conexiones de entrada hacia la puerta de enlace desde la nube?  
**Respuesta:** No. La puerta de enlace utiliza conexiones de salida hacia Azure Service Bus.

**Pregunta:** ¿Qué ocurre si bloqueo las conexiones de salida? ¿Qué tengo que abrir?  
**Respuesta:** Consulte más arriba la lista de puertos y hosts que utiliza la puerta de enlace.

**Pregunta:** ¿La puerta de enlace debe estar instalada en el mismo equipo que el origen de datos?  
**Respuesta:** No. La puerta de enlace se conectará con el origen de datos con la información de conexión que se proporcionó. En este sentido, piense en la puerta de enlace como en una aplicación de cliente. Solo tendrá que poder conectar con el nombre del servidor que se proporcionó.

**Pregunta:** ¿Qué es la latencia para ejecutar consultas a un origen de datos desde la puerta de enlace? ¿Cuál es la mejor arquitectura?  
**Respuesta:** Para reducir la latencia de red, instale la puerta de enlace lo más cerca del origen de datos como sea posible. Si puede instalar la puerta de enlace en el mismo origen de datos, minimizará la latencia. Tenga en cuenta también los centros de datos. Por ejemplo, si el servicio usa el centro de datos del oeste de Estados Unidos y tiene SQL Server hospedado en una máquina virtual de Azure, querrá tener la máquina virtual de Azure también en el oeste de Estados Unidos. Esto minimizará la latencia y evitará cargos en la máquina virtual de Azure.

**Pregunta:** ¿Hay algún requisito de ancho de banda de red?  
**Respuesta:** Se recomienda tener una conexión de red con buena capacidad. Cada entorno es diferente, y la cantidad de datos que se envíen afectará a los resultados. El uso de ExpressRoute puede ayudar a garantizar un nivel de rendimiento entre las instalaciones locales y los centros de datos de Azure.

Puede usar la herramienta de terceros [Azure Speed Test](http://azurespeedtest.azurewebsites.net/) para evaluar cuál es su rendimiento.

**Pregunta:** ¿El servicio de Windows de la puerta de enlace puede ejecutarse con una cuenta de Azure Active Directory?  
**Respuesta:** No. El servicio de Windows debe tener una cuenta de Windows válida. De forma predeterminada, se ejecutará con el SID de servicio, *NT SERVICE\PBIEgwService*.

**Pregunta:** ¿Cómo se envían resultados a la nube?  
**Respuesta:** Esto se consigue mediante Azure Service Bus. Para más información, consulte [cómo funciona](gateway-reference.md#how-the-gateway-works).

**Pregunta:** ¿Dónde se almacenan las credenciales?  
**Respuesta:** Las credenciales que especifique para un origen de datos se almacenan cifradas en el servicio de puerta de enlace en la nube. Las credenciales se descifran en la puerta de enlace local.

**Pregunta:** ¿puedo colocar la puerta de enlace en una red perimetral (también conocida como DMZ, zona desmilitarizada y subred filtrada)?  
**Respuesta:** La puerta de enlace requiere conectividad con el origen de datos. Si el origen de datos no se encuentra en la red perimetral, es posible que la puerta de enlace no pueda conectarse a él. Por ejemplo, el equipo que ejecuta SQL Server no puede estar en la red perimetral y no puede conectarse a ese equipo desde la red perimetral. Si ha colocado la puerta de enlace en la red perimetral, la puerta de enlace no podrá comunicarse con el equipo que ejecuta SQL Server.

#### <a name="high-availabilitydisaster-recovery"></a>Recuperación ante desastres y alta disponibilidad
**Pregunta:** ¿Existen planes para habilitar escenarios de alta disponibilidad con la puerta de enlace?  
**Respuesta:** Está en la hoja de ruta, pero aún no tenemos una previsión de tiempo.

**Pregunta:** ¿Qué opciones hay disponibles para la recuperación ante desastres?  
**Respuesta:** Puede usar la clave de recuperación para restaurar o mover una puerta de enlace. Cuando se instala la puerta de enlace, especifique la clave de recuperación.

**Pregunta:** ¿Cuál es la ventaja de la clave de recuperación?  
**Respuesta:** Proporciona un mecanismo para migrar o recuperar la configuración de puerta de enlace después de un desastre.

#### <a name="troubleshooting"></a>Solución de problemas
**Pregunta:** ¿Donde están los registros de puerta de enlace?  
**Respuesta:** Consulte [Herramientas](gateway-reference.md#tools) más adelante en este tema.

**Pregunta:** ¿Cómo se puede ver qué consultas se envían al origen de datos local?  
**Respuesta:** Puede habilitar el seguimiento de consultas, que incluirá las consultas que se envían. No olvide cambiar el valor original cuando haya finalizado la solución de problemas. Deja habilitado el seguimiento de consultas hará que los registros sean mayores.

También puede mirar las herramientas que el origen de datos tiene para realizar el seguimiento de las consultas. Por ejemplo, puede usar Extended Events o SQL Profiler para SQL Server y Analysis Services.

## <a name="how-the-gateway-works"></a>Cómo funciona la puerta de enlace
![Así funciona](./media/gateway-reference/gateway-arch.png)

Cuando un usuario interactúa con un elemento que está conectado a un origen de datos local:  

1. El servicio en la nube crea una consulta, junto con las credenciales cifradas del origen de datos, y envía la consulta a la cola de la puerta de enlace para su procesamiento.

2. El servicio de puerta de enlace en la nube analiza la consulta y envía la solicitud a [Azure Service Bus](https://azure.microsoft.com/documentation/services/service-bus/).

3. La puerta de enlace de datos local sondea Azure Service Bus para ver si hay solicitudes pendientes.

4. La puerta de enlace obtiene la consulta, descifra las credenciales y se conecta a los orígenes de datos con esas credenciales.

5. La puerta de enlace envía la consulta al origen de datos para su ejecución.

6. Los resultados se envían desde el origen de datos a la puerta de enlace y, a continuación, al servicio en la nube. A continuación, el servicio utiliza los resultados.

## <a name="troubleshooting"></a>Solución de problemas
#### <a name="update-to-the-latest-version"></a>Actualización a la versión más reciente
Muchos problemas pueden deberse a que la versión de la puerta de enlace no está actualizada.  Es un procedimiento recomendado asegurarse de tener la versión más reciente.  Si no ha actualizado la puerta de enlace durante un mes o más, puede que desee considerar la instalación de la versión más reciente de la puerta de enlace y ver si puede reproducir el problema.

#### <a name="error-failed-to-add-user-to-group---2147463168---pbiegwservice---performance-log-users---"></a>Error: Error al agregar el usuario al grupo.  (-2147463168   PBIEgwService   Performance Log Users   )
Puede recibir este error si intenta instalar la puerta de enlace en un controlador de dominio, lo que no se admite. Debe implementar la puerta de enlace en un equipo que no es un controlador de dominio.

## <a name="tools"></a>Herramientas
#### <a name="collecting-logs-from-the-gateway-configurator"></a>Recopilación de registros desde el configurador de puerta de enlace
Puede recopilar diversos registros para la puerta de enlace. Empiece siempre con los registros.

**Registros del instalador**

%localappdata%\Temp\On-premises_data_gateway_*.log

**Registros de configuración**

%localappdata%\Microsoft\on-premises data gateway\GatewayConfigurator*.log

**Registros del servicio de puerta de enlace de empresa**

C:\Users\PBIEgwService\AppData\Local\Microsoft\on-premises data gateway\Gateway*.log

**Registros de eventos**

Los registros de eventos del **servicio de puerta de enlace de datos local** se encuentran en **Registros de aplicaciones y servicios**.

![Registros de eventos](./media/gateway-reference/event-logs.png)

#### <a name="fiddler-trace"></a>Seguimiento de Fiddler
[Fiddler](http://www.telerik.com/fiddler) es una herramienta gratuita de Telerik que supervisa el tráfico HTTP.  Puede ver el tráfico de entrada y salida del servicio Power BI desde el equipo cliente. Puede mostrar errores y otra información relacionada.
