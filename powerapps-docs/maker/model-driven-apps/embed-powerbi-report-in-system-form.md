---
title: Insertar un informe de Power BI en un formulario basado en modelos | MicrosoftDocs
ms.custom: ''
ms.date: 03/05/2019
ms.reviewer: matp
ms.service: powerapps
ms.topic: get-started-article
author: adrianorth
ms.author: aorth
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: c31121b0de0c1256d12f6bbdbb4367d8122cab68
ms.sourcegitcommit: c6906775005aec98973b1f5c3dbe5924aff6d26e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "3341455"
---
# <a name="embed-a-power-bi-report-in-a-model-driven-system-form"></a>Insertar un informe de Power BI en un formulario basado en modelos
Puede usar informes de Power BI en aplicaciones basadas en modelos Power Apps para incluir informes y análisis enriquecido en los formularios del sistema y permitir a los usuarios conseguir más. Esto desbloquea la capacidad de agregar datos en entre los sistemas, y adaptarlos al contexto de un solo registro.
 
## <a name="prerequisites"></a>Requisitos previos
Insertar contenido de Power BI es una característica opcional y está deshabilitada en todos los entornos de forma predeterminada. Debe habilitarla para poder insertar contenido de Power BI. Más información: [Visualizaciones de Power BI en la organización](/power-platform/admin/use-power-bi#embed--visualizations-on-personal-dashboards).

Esta característica requiere exportar una solución, modificarla para agregar el fragmento de código XML, y luego volver a importarla al entorno. Asegúrese de importar los cambios en el entorno de destino mediante una solución administrada únicamente. Vea [Importar, actualizar y exportar soluciones](https://docs.microsoft.com/powerapps/maker/common-data-service/import-update-export-solutions) para obtener instrucciones sobre instalar una actualización en una solución administrada existente.

## <a name="embed-without-contextual-filtering"></a>Insertar sin filtrado contextual
Puede usar los informes y ventanas de Power BI simplemente insertándolos, y obtener el mismo informe exacto. Esto no implica contextualizarlos en el formulario actual basado en modelos y, por tanto, obtiene el mismo informe o ventana en todos los registros de la entidad. Por ejemplo, el siguiente informe muestra la ubicación geográfica de todas las cuentas a la vez, y es muy útil para mostrar la información de resumen.

> [!div class="mx-imgBorder"] 
> ![](media/embed-powerbi/embed-powerbi-report-in-system-form-unfiltered.png "Embed-powerbi-report-in-system-form-unfiltered")

Puede insertar una sección que hospede informes y ventanas de Power BI en los formularios del sistema agregando el fragmento de código siguiente en el bloqueo `<sections>` del XML del formulario. A continuación, importe la solución en el entorno de destino. 

```xml
<section id="{d411658c-7450-e1e3-bc80-07021a04bcc2}" locklevel="0" showlabel="true" IsUserDefined="0" name="tab_4_section_1" labelwidth="115" columns="1" layout="varwidth" showbar="false">
    <labels>
        <label languagecode="1033" description="Unfiltered Power BI embedding demo"/>
    </labels>
    <rows>
        <row>
            <cell id="{7d18b61c-c588-136c-aee7-03e5e74a09a1}" showlabel="true" rowspan="20" colspan="1" auto="false">
                <labels>
                    <label languagecode="1033" description="Accounts (Parent Account)"/>
                </labels>
                <control id="unfilteredreport" classid="{8C54228C-1B25-4909-A12A-F2B968BB0D62}">
                    <parameters>
                        <PowerBIGroupId>00000000-0000-0000-0000-000000000000</PowerBIGroupId>
                        <PowerBIReportId>544c4162-6773-4944-900c-abfd075f6081</PowerBIReportId>
                        <TileUrl>https://xyz.powerbi.com/reportEmbed?reportId=544c4162-6773-4944-900c-abfd075f6081</TileUrl>
                    </parameters>
                </control>
            </cell>
        </row>
        <row/>
    </rows>
</section>
```
> [!IMPORTANT]
> Asegúrese de usar el control `classid="{8C54228C-1B25-4909-A12A-F2B968BB0D62}"` como se indica en el XML de ejemplo.

 En esta tabla se describen las propiedades del ejemplo anterior.

|                                                 Propiedad                                                  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      Descripción                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|-----------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                         **PowerBIGroupId**                          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  El Id. del área de trabajo de Power BI. El área de trabajo predeterminada del usuario es siempre 00000000-0000-0000-0000-000000000000. Puede comprobar el Id. de cualquier área de trabajo viendo su dirección URL. Por ejemplo, https://xyz.powerbi.com/groups/0ddbe381-256d-44bc-93de-34e47f3d9ab4/.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|                               **PowerBIReportId**                                |                             La identificación del informe de Power BI. Reemplace esto con el informe que desea insertar. Puede comprobar el Id. de cualquier informe viendo su dirección URL. Por ejemplo, https://xyz.powerbi.com/groups/me/reports/544c4162-6773-4944-900c-abfd075f6081.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|                                       **TileUrl**                                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        La dirección URL del informe o la ventana de Power BI que desea insertar. Asegúrese de usar el nombre de instancia correcto de Power BI (reemplace msit.powerbi.com por el suyo) y el Id. de informe (reemplace reportId=544c4162-6773-4944-900c-abfd075f6081 por el suyo). Por ejemplo, https://xyz.powerbi.com/reportEmbed?reportId=544c4162-6773-4944-900c-abfd075f6081.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |

## <a name="embed-with-contextual-filtering"></a>Insertar con filtrado contextual
Puede hacer que los informes y ventanas de Power BI sean más significativos aplicando filtros contextuales al formulario basado en modelos, de forma que el informe o la ventana se basen en filtros de atributos del registro actual. Por ejemplo, el siguiente informe muestra la ubicación geográfica de una cuenta, filtrando el informe de Power BI con el nombre de cuenta. Esto permite que un informe solo muestre información contextualizada para todos los registros de la entidad.

> [!div class="mx-imgBorder"] 
> ![](media/embed-powerbi/embed-powerbi-report-in-system-form-filtered.png "Embed-powerbi-report-in-system-form-filtered")

El filtrado se realiza agregando un elemento `<PowerBIFilter>` en el bloque `<parameter>` como se muestra aquí. Puede usar cualquier atributo de entidad del formulario para generar expresión de filtro. Más información: [Construir filtros](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Filters#contructingfilters) para comprender cómo crear sus propios filtros.
    
```xml
<control id="filteredreport" classid="{8C54228C-1B25-4909-A12A-F2B968BB0D62}">
    <parameters>
        <PowerBIGroupId>00000000-0000-0000-0000-000000000000</PowerBIGroupId>
        <PowerBIReportId>544c4162-6773-4944-900c-abfd075f6081</PowerBIReportId>
        <TileUrl>https://xyz.powerbi.com/reportEmbed?reportId=544c4162-6773-4944-900c-abfd075f6081</TileUrl>
        <PowerBIFilter>{"Filter": "[{\"$schema\":\"basic\",\"target\":{\"table\":\"My Active Accounts\",\"column\":\"Account Name\"},\"operator\":\"In\",\"values\":[$a],\"filterType\":1}]", "Alias": {"$a": "name"}}</PowerBIFilter>
    </parameters>
</control>
```

Tenga en cuenta que se usa el mismo control que la inserción del informe sin filtrar y, por tanto, el Id. de clases control se mantiene sin cambios. 

En esta tabla se describen las propiedades adicionales utilizadas en el ejemplo anterior.

|                                                 Propiedad                                                  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      Descripción                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|-----------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                         **PowerBIFilter**                          |        La expresión de filtro que contextualiza el informe de Power BI pasando los atributos de formulario como parámetros. Para hacer que sea más legible, el filtro se construye como se muestra aquí.    |

```json
    {
            "Filter": "[{
                    \"$schema\":\"basic\",
                    \"target\":{
                            \"table\":\"My Active Accounts\",
                            \"column\":\"Account Name\"
                    },
                    \"operator\":\"In\",
                    \"values\":[$a, $b],
                    \"filterType\":1
            }]",
            "Alias": {
                    "$a": "firstname",
                    "$b":"lastname"
            }
    }
```

La parte de destino de la expresión anterior identifica la tabla y la columna a la que aplicar filtros. El operador identifica la lógica y los valores identifican los últimos datos pasados desde la aplicación basada en modelos de Power Apps. Para parametrizar de una forma genérica, los valores son construidos mediante alias. En la expresión anterior, se pasa el valor de **firstname** y **lastname** de una cuenta, y se busca cualquiera de ellos en la columna **Nombre de cuenta** en el informe de Power BI. Tenga en cuenta que **firstname** y **lastname** son los nombres únicos de los atributos de la entidad de cuenta, cuyo valor será pasado aquí. 

Puede crear expresiones de filtro más complejas consultando ejemplos de [Construir los filtros](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Filters#contructingfilters) y proporcionando los valores adecuados para $schema y filterType. Asegúrese de escapar cada literal en la parte de filtro con *\"*, para generar JSON correctamente.

## <a name="known-issues-and-limitations"></a>Problemas y limitaciones conocidos
1. Esta integración solo está disponible en el cliente de la interfaz unificada, en exploradores web y los dispositivos móviles compatibles.
2. Al abrir este formulario en el diseñador de formularios de Power Apps no se mostrará el control en una forma significativa. Esto se debe a que el control se personaliza fuera del diseñador de formularios.
3. Los usuarios se autenticarán en Power BI automáticamente con su nombre de usuario y contraseña de Power Apps. Si no existe una cuenta de Power BI con credenciales coincidentes, un inicio de sesión mensaje se muestra como se ilustra aquí. 

   > [!div class="mx-imgBorder"] 
   > ![](media/embed-powerbi/embed-powerbi-report-in-system-form-auth-1.png "Embed-powerbi-report-in-system-form-auth-1")

4. No se mostrarán datos si una cuenta incorrecta se usa para iniciar sesión en Power BI. Para iniciar sesión con las credenciales correctas, cierre sesión y, a continuación vuelva a iniciar sesión.

   > [!div class="mx-imgBorder"] 
   > ![](media/embed-powerbi/embed-powerbi-report-in-system-form-auth-2.png "Embed-powerbi-report-in-system-form-auth-2")

   > [!div class="mx-imgBorder"] 
   > ![](media/embed-powerbi/embed-powerbi-report-in-system-form-auth-3.png "Embed-powerbi-report-in-system-form-auth-3")

5. La vista de los datos de informe que se muestran en Power Apps es igual que en Power BI, y los roles de seguridad y los privilegios de Power Apps no afectan a los datos que se muestran. Por lo tanto, los datos son esencialmente iguales que los que vería el creador del conjunto de datos de Power BI. Para aplicar las restricciones de acceso a datos similares a los roles de seguridad y equipos de Power Apps, use [Seguridad de nivel de fila (RLS) con Power BI](https://docs.microsoft.com/power-bi/service-admin-rls).
6. Si el formulario no muestra el informe de Power BI después de importar la solución y de publicar las personalizaciones, ábrala en el editor de formularios basados en modelos y guárdelo, para que se genere el JSON de formulario.


### <a name="see-also"></a>Vea también

[Insertar un panel de Power BI en un panel personal basado en modelos de Power Apps](/powerapps/user/add-powerbi-dashboards)

[Usar Power BI con aplicaciones de Dynamics 365](/power-platform/admin/use-power-bi)

[Importar, actualizar y exportar soluciones](../common-data-service/import-update-export-solutions.md)
