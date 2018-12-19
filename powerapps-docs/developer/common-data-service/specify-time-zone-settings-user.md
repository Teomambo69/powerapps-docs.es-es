---
title: Especificar la configuración de zona horaria para un usuario (Common Data Service para aplicaciones) | Microsoft Docs
description: Más información sobre el uso de la entidad UserSettings para especificar la configuraciń de zona horario para un usuario en Dynamics 365. Los siguientes atributos se exponen para la entidad UserSettings relacionada con la zona horaria. Todos los atributos de huso horario en la entidad UserSettings son de tipo entero.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: paulliew
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="specify-time-zone-settings-for-a-user"></a>Especificación de la configuración de zona horaria para un usuario

Use la entidad `UserSettings` para especificar la configuración de zona horaria para un usuario en Common Data Service para aplicaciones Los siguientes atributos se exponen para la entidad `UserSettings` relacionada con la zona horaria. Todos los atributos de zona horaria de la entidad `UserSettings` son del tipo de datos `Integer`.  


|       Nombre de atributo        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                      Descripción                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|       `TimeZoneBias`        |                                                                                                                                                                                                                                                                                                                                                                                                       Ajuste de zona horaria local para el usuario. La calcula el sistema en función de la zona horaria especificada por el usuario en el atributo `TimeZoneCode`.                                                                                                                                                                                                                                                                                                                                                                                                       |
|       `TimeZoneCode`        |                                                                                                                                                                                                                                                 Código de zona horaria local del usuario.<br /><br /> Para obtener una lista de valores del código de zona horaria admitidos en CDS para aplicaciones, use el atributo `TimeZoneDefinition.TimeZoneCode`. El atributo `TimeZoneDefinition.StandardName` almacena los nombres estándar de los códigos de zona horaria correspondientes. Más información: [Entidades de zona horaria](time-zone-entities.md)                                                                                                                                                                                                                                                 |
|   `TimeZoneDaylightBias`    |                                                                                                                                                                                                                                                                                                                                                                                                  Ajuste de zona horaria local para el horario de verano del usuario. La calcula el sistema en función de la zona horaria especificada por el usuario en el atributo `TimeZoneCode`.                                                                                                                                                                                                                                                                                                                                                                                                   |
|    `TimeZoneDaylightDay`    |           Primera, segunda, tercera, cuarta o quinta instancia de un *día* en un *mes* cuando tiene efecto el horario de verano para el usuario de acuerdo con zona horaria local. Los valores de *día* y *mes* se toman de los atributos `TimeZoneDaylightDayOfWeek` y `TimeZoneDaylightMonth` respectivamente para determinar la fecha válida. La calcula el sistema en función de la zona horaria especificada por el usuario en el atributo `TimeZoneCode`.<br /><br /> Por ejemplo, para la zona horaria Hora estándar del Este de EE. UU. (EST), tenga en cuenta los siguientes valores de atributo:<br /><br /> -   `TimeZoneDaylightDay`: 2               //Denota segunda aparición<br />-   `TimeZoneDaylightDayOfWeek`: 0                         //Denota primer día de la semana (domingo)<br />-   `TimeZoneDaylightMonth`: 3               //Denota 3er mes (marzo)<br /><br /> Esto implica que el horario de verano entra en vigor el 2º domingo de marzo, que es en la práctica el 8 de marzo de 2015.           |
| `TimeZoneDaylightDayOfWeek` |                                                                                                                                                                                                                                        El día de la semana (domingo=0, lunes=1,...) en un *mes* cuando el horario de verano entra en vigor para el usuario según la zona horaria local. El valor *mes* se toma del atributo `TimeZoneDaylightMonth` , y se usa junto con el valor de atributo `TimeZoneDaylightDay` para determinar la fecha de entrada en vigor. La calcula el sistema en función de la zona horaria especificada por el usuario en el atributo `TimeZoneCode`.<br /><br /> Vea el ejemplo del atributo `TimeZoneDaylightDay`.                                                                                                                                                                                                                                         |
|   `TimeZoneDaylightHour`    |                                                                                                                                                                                                                                                                                                                                                                                    Hora en que el horario de verano entra en vigor para el usuario según la zona horaria local. La calcula el sistema en función de la zona horaria especificada por el usuario en el atributo `TimeZoneCode`.                                                                                                                                                                                                                                                                                                                                                                                     |
|  `TimeZoneDaylightMinute`   |                                                                                                                                                                                                                                                                                                                                                                                   Minuto en que el horario de verano entra en vigor para el usuario según la zona horaria local. La calcula el sistema en función de la zona horaria especificada por el usuario en el atributo `TimeZoneCode`.                                                                                                                                                                                                                                                                                                                                                                                    |
|   `TimeZoneDaylightMonth`   |                                                     El mes (enero=1, febrero=2,...) en que el horario de verano entra en vigor para el usuario según la zona horaria local. Se utiliza junto con los atributos `TimeZoneDaylightDay` y `TimeZoneDaylightDayOfWeek` para determinar la fecha válida. La calcula el sistema en función de la zona horaria especificada por el usuario en el atributo `TimeZoneCode`.<br /><br /> Por ejemplo, para la zona horaria Hora estándar del Este de EE. UU. (EST), tenga en cuenta los siguientes valores de atributo:<br /><br /> -   `TimeZoneDaylightDay`: 2               //Denota segunda aparición<br />-   `TimeZoneDaylightDayOfWeek`: 0               // Denota primer día de la semana (domingo)<br />-   `TimeZoneDaylightMonth`: 3               // Denota 3er mes (marzo)<br /><br /> Esto implica que el horario de verano entra en vigor el 2º domingo de marzo, que es en la práctica el 8 de marzo de 2015.                                                     |
|  `TimeZoneDaylightSecond`   |                                                                                                                                                                                                                                                                                                                                                                                   Segundo en que el horario de verano entra en vigor para el usuario según la zona horaria local. La calcula el sistema en función de la zona horaria especificada por el usuario en el atributo `TimeZoneCode`.                                                                                                                                                                                                                                                                                                                                                                                    |
|   `TimeZoneDaylightYear`    |                                                                                                                                                                                                                                                                                                                                                                                   Año de horario de verano de la zona horaria local del usuario. Se establece como 0 para indicar todos los años. La calcula el sistema en función de la zona horaria especificada por el usuario en el atributo `TimeZoneCode`.                                                                                                                                                                                                                                                                                                                                                                                    |
|   `TimeZoneStandardBias`    |                                                                                                                                                                                                                                                                                                                                                                                                   Diferencia horaria estándar de zona horaria local del usuario. La calcula el sistema en función de la zona horaria especificada por el usuario en el atributo `TimeZoneCode`.                                                                                                                                                                                                                                                                                                                                                                                                   |
|    `TimeZoneStandardDay`    | Primera, segunda, tercera, cuarta o quinta instancia de un *día* en un *mes* cuando tiene efecto el horario estándar para el usuario de acuerdo con zona horaria local. Los valores de *día* y *mes* se toman de los atributos `TimeZoneStandardDayOfWeek` y `TimeZoneStandardMonth` respectivamente para determinar la fecha válida. La calcula el sistema en función de la zona horaria especificada por el usuario en el atributo `TimeZoneCode`.<br /><br /> Por ejemplo, para la zona horaria Hora estándar del Este de EE. UU. (EST), tenga en cuenta los siguientes valores de atributo:<br /><br /> -   `TimeZoneStandardDay`: 1               //Denota primera aparición<br />-   `TimeZoneStandardDayOfWeek`: 0                         //Denota primer día de la semana (domingo)<br />-   `TimeZoneStandardMonth`: 11               //Denota 11º mes (noviembre)<br /><br /> Esto implica que el horario estándar entra en vigor el 1º domingo de noviembre, que es en la práctica el 1 de noviembre de 2015. |
| `TimeZoneStandardDayOfWeek` |                                                                                                                                                                                                                                      El día de la semana (domingo=0, lunes=1,...) en un *mes* cuando el horario estándar entra en vigor para el usuario según la zona horaria local. El valor *mes* se toma del atributo `TimeZoneStandardMonth` , y se usa junto con el valor de atributo `TimeZoneStandardDay` para determinar la fecha de entrada en vigor. La calcula el sistema en función de la zona horaria especificada por el usuario en el atributo `TimeZoneCode`.<br /><br /> Vea el ejemplo del atributo `TimeZoneStandardDay`.                                                                                                                                                                                                                                      |
|   `TimeZoneStandardHour`    |                                                                                                                                                                                                                                                                                                                                                                                    Hora en que el horario estándar entra en vigor para el usuario según la zona horaria local. La calcula el sistema en función de la zona horaria especificada por el usuario en el atributo `TimeZoneCode`.                                                                                                                                                                                                                                                                                                                                                                                     |
|  `TimeZoneStandardMinute`   |                                                                                                                                                                                                                                                                                                                                                                                   Minuto en que el horario estándar entra en vigor para el usuario según la zona horaria local. La calcula el sistema en función de la zona horaria especificada por el usuario en el atributo `TimeZoneCode`.                                                                                                                                                                                                                                                                                                                                                                                    |
|   `TimeZoneStandardMonth`   |                                             El mes (enero=1, febrero=2,...) en que el horario estándar entra en vigor para el usuario según la zona horaria local. Se utiliza junto con los atributos `TimeZoneStandardDay` y `TimeZoneStandardDayOfWeek` para determinar la fecha válida. La calcula el sistema en función de la zona horaria especificada por el usuario en el atributo `TimeZoneCode`.<br /><br /> Por ejemplo, para la zona horaria Hora estándar del Este de EE. UU. (EST), tenga en cuenta los siguientes valores de atributo:<br /><br /> -   `TimeZoneDaylightDay`: 1               //Denota primera aparición<br />-   `TimeZoneDaylightDayOfWeek`: 0               // Denota primer día de la semana (domingo)<br />-   `TimeZoneDaylightMonth`: 11               //Denota 11º mes (noviembre)<br /><br /> Esto implica que el horario estándar entra en vigor el 1º domingo de noviembre, que es en la práctica el 1 de noviembre de 2015.                                              |
|  `TimeZoneStandardSecond`   |                                                                                                                                                                                                                                                                                                                                                                                   Segundo en que el horario estándar entra en vigor para el usuario según la zona horaria local. La calcula el sistema en función de la zona horaria especificada por el usuario en el atributo `TimeZoneCode`.                                                                                                                                                                                                                                                                                                                                                                                    |
|   `TimeZoneStandardYear`    |                                                                                                                                                                                                                                                                                                                                                                                   Año de horario estándar de la zona horaria local del usuario. Se establece como 0 para indicar todos los años. La calcula el sistema en función de la zona horaria especificada por el usuario en el atributo `TimeZoneCode`.                                                                                                                                                                                                                                                                                                                                                                                    |

### <a name="see-also"></a>Vea también  
 [Entidad SystemUser](reference/entities/systemuser.md)   
 [Entidades de zona horaria](time-zone-entities.md)   
 [Comportamiento y formato del atributo de fecha y hora](behavior-format-date-time-attribute.md)   
 [Entidades de usuarios y equipos](user-team-entities.md)