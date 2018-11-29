---
title: addNotification (referencia API de cliente) en aplicaciones basadas en modelo| Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 4d025f92-db16-440c-9f82-e40d71e09862
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="addnotification-client-api-reference"></a>addNotification (referencia de la API de cliente)



Muestra una notificación de error o de recomendación para un control, y permite especificar acciones para ejecutar basadas en la notificación. Cuando especifica un tipo de error de notificación, un icono rojo” X” aparece junto al control. Cuando especifica un tipo de recomendación de notificación, un icono rojo ”i” aparece junto al control. En los clientes móviles de Dynamics 365, al pulsar en el icono se mostrará el mensaje, y le permitirá realizar la acción configurado haciendo clic en el botón **Aplicar** o descartar el mensaje. 

## <a name="control-types-supported"></a>Tipos de control admitidos

Todas

## <a name="syntax"></a>Sintaxis

`formContext.getControl(arg).addNotification(notification);`

## <a name="parameters"></a>Parámetros

<table style="width:100%">
<tr>
<th>Nombre</th>
<th>Tipo</th>
<th>Obligatoria</th>
<th>Descripción</th>
</tr>
<tr>
<td>notification</td>
<td>Objeto</td>
<td>Sí</td>
<td>La notificación a agregar. El objeto contiene los siguientes atributos:
<ul>
<li><b>actions</b>: (opcional) matriz de objetos. Una colección de objetos con los atributos siguientes:
<ul>
<li><b>message</b>: cadena (opcional). El mensaje del cuerpo de la notificación que se mostrará al usuario. Limite el mensaje a 100 caracteres para una experiencia de usuario óptima.</li>
<li><b>actions</b>: (opcional) matriz de funciones. Las acciones correspondientes para el mensaje.</li>
</ul>
<li><b>messages</b>: matriz de cadenas. El mensaje que se mostrarán en la notificación. En la versión actual, sólo el primer mensaje especificado en esta matriz se mostrará. La cadena que especifique aquí aparece como texto en negrita en la notificación, y normalmente se usa para el título o el asunto de la notificación. Debe limitar el mensaje a 50 caracteres para una experiencia de usuario óptima.</li>
<li><b>notificationLevel</b>: cadena. Define el tipo de notificación. Los valores válidos son ERROR o RECOMMENDATION.</li>
<li><b>uniqueId</b>: cadena. El identificador que se usará para borrar esta notificación al usar el método <b>clearNotification</b>.</li>
</ul></td>
</tr>

</table>

## <a name="return-value"></a>Valor devuelto

**Type**: booleano

**Description**: indica si el método se realizó correctamente.


## <a name="remarks"></a>Comentarios

El método **addNotification** muestra una notificación con los mensajes que ha especificado y dos botones estándar: **Aplicar** y **Descartar**. Al hacer clic en **Aplicar** se ejecuta la acción que define; al hacer clic en **Descartar** se cierra el mensaje de notificación. 

## <a name="example"></a>Ejemplo

El siguiente código de ejemplo muestra una notificación en el campo **Nombre de cuenta** del formulario de cuentas para establecer el **Símbolo del valor** si el campo **Nombre de cuenta** contiene ”Microsoft”, y el símbolo del valor aún no está establecido en "MSFT". Al hacer clic en **Aplicar** en la notificación se establecerá el campo **Símbolo del valor** como "MSFT".

```JavaScript
function addTickerSymbolRecommendation(executionContext) {
    var formContext = executionContext.getFormContext();
    var myControl = formContext.getControl('name');
    var accountName = formContext.data.entity.attributes.get('name');
    var tickerSymbol = formContext.data.entity.attributes.get('tickersymbol');

    if (accountName.getValue() == 'Microsoft' && tickerSymbol.getValue() != 'MSFT') {
        var actionCollection = {
            message: 'Set the Ticker Symbol to MSFT?',
            actions: null
        };

        actionCollection.actions = [function () {
            tickerSymbol.setValue('MSFT');
            myControl.clearNotification('my_unique_id');
        }];

        myControl.addNotification({
            messages: ['Set Ticker Symbol'],
            notificationLevel: 'RECOMMENDATION',
            uniqueId: 'my_unique_id',
            actions: [actionCollection]
        });
    }
    else
        console.log("Notification not set");
}
```

### <a name="related-topics"></a>Temas relacionados

[clearNotification](clearNotification.md)

[setNotification](setNotification.md)



