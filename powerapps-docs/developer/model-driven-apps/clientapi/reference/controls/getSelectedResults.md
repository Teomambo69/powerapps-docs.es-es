---
title: getSelectedResults (referencia de la API de cliente)| MicrosoftDocs
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: reference
ms.assetid: 4d025f92-db16-440c-9f82-e40d71e09862
author: KumarVivek
ms.author: kvivek
manager: annbe
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getselectedresults-client-api-reference"></a>getSelectedResults (referencia de la API de cliente)


Use este método para obtener el resultado seleccionado actualmente del control de búsqueda. El resultado seleccionado actualmente también representa el resultado que está abierto actualmente. 

## <a name="control-types-supported"></a>Tipos de control admitidos

Control de búsqueda de knowledge base

## <a name="syntax"></a>Sintaxis

```
var kbSearchControl = formContext.getControl("<name>");
var kbSearchResult = kbSearchControl.getSelectedResults();
```

## <a name="return-value"></a>Valor de retorno 

**KBSearchResult**. El resultado seleccionado actualmente.

## <a name="kbsearchresult-properties"></a>Propiedades de KBSearchResult

| **Propiedad**        | **Tipo** | **Descripción**  |
|---------------------|----------|------------------|
| **answer**          | String   | El formato HTML que contiene el contenido del artículo. Podría pasar este contenido a una acción personalizada que pudiera incluirla en un correo electrónico para enviar al cliente. |
| **articleId**       | String   | El identificador del artículo que se usa como clave alternativa. Puede usarlo para averiguar si este artículo ya existe en Common Data Service o no.|
| **articleUid**      | String   | El identificador único de artículo. Este valor se usa como clave alternativa. Este Id. es necesario para crear un nuevo registro de KB mientras asocia un artículo si aún no existe uno. |
| **attachmentCount** | Número   | Número de datos adjuntos del artículo. |
| **createdOn**       | Date     | Fecha en que se creó el artículo. Este valor usará la zona horaria y el formato del usuario actual. Es posible que desee usar la antigüedad del artículo de la lógica de negocios. |
| **expiredDate**     | Date     | Fecha en que el artículo expiró o expirará. Puede comparar esta fecha los datos actuales para determinar si el artículo ha expirado o no. El valor usa la zona horaria y el formato del usuario actual.|
| **folderHref**      | String   | El vínculo a la ruta de la carpeta del artículo.|
| **href**            | String   | El vínculo directo al artículo.|
| **isAssociated**    | Boolean  | Indica si el artículo está asociado con el registro primario o no. Puede comprobar esta valor antes de asociar el artículo con el registro actual usando scripts de formulario o en otro proceso iniciado por scripts de formulario. |
| **lastModifiedOn**  | Date     | Fecha en la que el elemento se modificó por última vez. Este valor usará la zona horaria y el formato del usuario actual. |
| **publicUrl**       | String   | Dirección URL del portal de soporte técnico del artículo. Si desconecta la opción de dirección URL del portal, ésta estará en blanco. Use una acción personalizada para incluir esto en un víonculo en el contenido de un correo electrónico para enviar a un cliente. |
| **published**       | Boolean  | Indica si el artículo está en estado publicado. **True** si se publica, de lo contrario, **False**. Debe comprobar si el artículo está publicado antes de enviar la información sobre él a un cliente. |
| **question**        | String   | Título del artículo. Si va a hacer referencia al artículo en cualquier proceso de negocio, puede hacer referencia a él por nombre mediante este valor.  |
| **rating**          | Número   | Calificación del artículo.  |
| **searchBlurb**     | String   | Un breve fragmento del contenido del artículo que contiene las áreas que ha encontrado la consulta de búsqueda. Use esta opción para ofrecer un vistazo del artículo a los usuarios en la lista de búsqueda y ayudarles a determinar si este es el artículo que están buscando. |
| **serviceDeskUri**  | String   | Vinculo al artículo. Utilice este vínculo para abrir el artículo.   |
| **timesViewed**     | Número   | El número de veces que los clientes ven un artículo en el portal.  |