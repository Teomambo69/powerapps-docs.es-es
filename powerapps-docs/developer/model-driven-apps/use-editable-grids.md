---
title: Usar cuadrículas editables en aplicaciones basadas en modelos | Microsoft Docs
description: 'La cuadrícula editable es un nuevo control personalizado en Dynamics 365 Customer Engagement que proporciona funciones de edición en línea enriquecidas en clientes web y móviles (Dynamics 365 for phones y Dynamics 365 for tablets) incluida la capacidad de agrupar, ordenar y filtrar los datos dentro de la misma cuadrícula de manera que no tenga que cambiar los registros o las vistas.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: shilpas
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-editable-grids"></a>Usar cuadrículas editables

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/use-editable-grids-dynamics-365 -->

La cuadrícula editable es un control personalizado que proporciona funciones de edición en línea enriquecidas en clientes web y móviles (Dynamics 365 for phones y Dynamics 365 for tablets) incluida la capacidad de agrupar, ordenar y filtrar los datos dentro de la misma cuadrícula de manera que no tenga que cambiar los registros o las vistas. El control de cuadrícula editable se admite en la cuadrícula principal y las subcuadrículas de un formulario en el cliente web y en paneles y en cuadrículas de formulario de los clientes móviles. Aunque el control de cuadrícula editable proporcione la función de edición, respeta la configuración de metadatos de la cuadrícula de solo lectura y de seguridad a nivel de campo. Las cuadrículas editables también admiten reglas de negocio y scripts de formularios para que pueda aplicar lógica de negocios personalizada según los requisitos de la organización.  

> [!NOTE] 
> Si usa formularios antiguos (versiones anteriores a Dynamics CRM 2016) y habilita una cuadrícula editable en una subcuadrícula, la subcuadrícula editable no se representará. Los administradores del sistema pueden desactivar los formularios antiguos en la configuración del sistema, si es necesario. 

<a name="Enable"></a>   
## <a name="enable-editable-grids"></a>Habilitar cuadrículas editables  
 Puede habilitar cuadrículas editables en el nivel de entidad para usar en la cuadrícula principal, o en el nivel de formulario para reemplazar subcuadrículas de solo lectura (cuadrículas asociadas) con una cuadrícula editable.  
  
 Puede habilitar el control de cuadrícula editable para una entidad mediante la herramienta de personalización en aplicaciones basadas en modelos (pestaña **Configuración** > **Personalizaciones**  > **Personalización del sistema** > **Entidades** > *[Entity_Name]* > **Controles**.  
  
 Para habilitar la cuadrícula editable para una cuadrícula en un formulario, abra el editor de formularios, haga doble clic en la cuadrícula de sólo lectura que desea sustituir con la cuadrícula editables, y luego agregue/habilite la cuadrícula editable en la pestaña **Controles**.  
  
 Puede para revertir a la cuadrícula no editable en cualquier momento para la cuadrícula principal y cuadrículas asociadas, si es necesario. Además, en tiempo de ejecución, los usuarios cambiar entre cuadrículas editables y cuadrículas de solo lectura.  
  
 Más información: [Crear cuadrículas (listas) editables de aplicaciones basadas en modelos mediante el control personalizado Cuadrículas editables](../../maker/model-driven-apps/make-grids-lists-editable-custom-control.md)  
  
<a name="FormScripting"></a>   
## <a name="form-scripting-support"></a>Soporte de scripts de formularios  
 Las cuadrículas editables admiten eventos y métodos del lado del cliente que se pueden usar para escribir extensiones de cliente personalizadas de acuerdo con su necesidad de negocio. Más informacikón: [Cuadrículas y subcuadrículas en aplicaciones basadas en modelos (referencia de API de cliente)](clientapi/reference/grids.md)
  
<a name="EntitiesSupported"></a>   
## <a name="entities-and-views-supported-by-editable-grid"></a>Entidades y vistas admitidas por la cuadrícula editable  
 No todas las entidades y vistas admiten el uso de cuadrícula editable.  
  
 En el cliente web, una entidad admitirá la cuadrícula editable si se cumplen las siguientes condiciones:  
  
- La entidad es personalizable (IsCustomizable = true)  
  
- La entidad es actualizada (IsAIRUpdated = true) o personalizada (IsCustomEntity = true)  
  
- La entidad no es una entidad secundaria (IsChildEntity = false)  
  
  En el cliente móvil, una entidad admitirá la cuadrícula editable si la entidad puede mostrarse en el mapa del sitio del cliente móvil.  
  
  Para obtener información acerca de las entidades que admiten cuadrículas editables, consulte la sección **Entidades predefinidas admitidas** en TechNet: [Crear cuadrículas (listas) editables de aplicaciones basadas en modelos mediante el control personalizado Cuadrícula editable](../../maker/model-driven-apps/make-grids-lists-editable-custom-control.md) 
   
  Las cuadrículas editables no admiten vistas asociadas de informe asociadas (**Tipo de informe** = `Related`).  
  
  Use el código de ejemplo siguiente para generar un archivo XML que pueda abrir en Excel como tabla XML para ver información de compatibilidad de entidades para controles editables. Excel determinará el esquema automáticamente, y mostrará la información en las siguientes columnas:  
  
- `LogicalName`: Nombre lógico de la entidad.  
  
- `DisplayName`: Nombre para mostrar de entidad.  
  
- `CanEnableEditableGridWeb`: Muestra el estado (True o False) si la cuadrícula editable se admite para la entidad en el cliente web.  
  
- `CanEnableEditableGridMobile`: Muestra el estado (True o False) si la cuadrícula editable se admite para la entidad en clientes móviles. (Dynamics 365 for phones y Dynamics 365 for tablets).  
  
```csharp  
using System;  
using System.Linq;  
using System.Xml.Linq;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
using System.Collections.Generic;  
using System.Xml.Serialization;  
using System.Xml;  
using System.IO;  
  
// These namespaces are found in the Microsoft.Xrm.Sdk.dll assembly  
// found in the SDK\bin folder.  
using Microsoft.Xrm.Sdk;  
using Microsoft.Xrm.Sdk.Query;  
using Microsoft.Xrm.Sdk.Metadata;  
using Microsoft.Xrm.Sdk.Client;  
using Microsoft.Xrm.Sdk.Messages;  
  
// This namespace is found in Microsoft.Crm.Sdk.Proxy.dll assembly  
// found in the SDK\bin folder.  
using Microsoft.Crm.Sdk.Messages;  
  
namespace Microsoft.Crm.Sdk.Samples  
{  
    /// <summary>  
    /// This sample generates an XML table to display the entity-support information for   
    ///  editable controls.  
    /// </summary>  
    public class DumpEditableGridEntityInfo  
    {  
        #region Class Level Members  
  
        /// <summary>  
        /// Stores the organization service proxy.  
        /// </summary>  
        OrganizationServiceProxy _serviceProxy;  
  
        // Create storage for new attributes being created  
        public List<AttributeMetadata> addedAttributes;  
  
        // Specify which language code to use in the sample. If you are using a language  
        // other than US English, you will need to modify this value accordingly.  
        // See https://msdn.microsoft.com/library/0h88fahh.aspx  
        public const int _languageCode = 1033;  
  
        // Define the IDs/variables needed for this sample.  
        public int _insertedStatusValue;  
  
        #endregion Class Level Members  
  
        #region How To Sample Code  
        /// <summary>  
        /// </summary>  
        /// <param name="serverConfig">Contains server connection information.</param>  
        /// <param name="promptForDelete">When True, the user will be prompted to delete all  
        /// created entities.</param>  
        public void Run(ServerConnection.Configuration serverConfig, bool promptForDelete)  
        {  
            try  
            {  
  
                // Connect to the Organization service.   
                // The using statement assures that the service proxy will be properly disposed.  
                using (_serviceProxy = new OrganizationServiceProxy(serverConfig.OrganizationUri, serverConfig.HomeRealmUri, serverConfig.Credentials, serverConfig.DeviceCredentials))  
                {  
                    // This statement is required to enable early-bound type support.  
                    _serviceProxy.EnableProxyTypes();  
  
                    //<snippetDumpEditableGridEntityInfo1>  
                    RetrieveAllEntitiesRequest request = new RetrieveAllEntitiesRequest()  
                    {  
                        EntityFilters = EntityFilters.Entity,  
                        RetrieveAsIfPublished = true  
                    };  
  
                    // Retrieve the MetaData.  
                    RetrieveAllEntitiesResponse response = (RetrieveAllEntitiesResponse)_serviceProxy.Execute(request);  
  
                    // Create an instance of StreamWriter to write text to a file.  
                    // The using statement also closes the StreamWriter.  
                    // To view this file, right click the file and choose open with Excel.   
                    // Excel will figure out the schema and display the information in columns.  
  
                    String filename = String.Concat("EditableGridEntityInfo.xml");  
                    using (StreamWriter sw = new StreamWriter(filename))  
                    {  
                        // Create Xml Writer.  
                        XmlTextWriter metadataWriter = new XmlTextWriter(sw);  
  
                        // Start Xml File.  
                        metadataWriter.WriteStartDocument();  
  
                        // Metadata Xml Node.  
                        metadataWriter.WriteStartElement("Metadata");  
  
                        foreach (EntityMetadata currentEntity in response.EntityMetadata)  
                        {  
                            // Start Entity Node  
                            metadataWriter.WriteStartElement("Entity");  
  
                            bool canBeDisplayedInSitemap = currentEntity.IsCustomizable.Value;  
  
                            if (canBeDisplayedInSitemap)  
                            {  
                                metadataWriter.WriteElementString("LogicalName", currentEntity.LogicalName);  
                                metadataWriter.WriteElementString("DisplayName", currentEntity.DisplayName.UserLocalizedLabel?.Label);  
                                metadataWriter.WriteElementString("CanEnableEditableGridWeb", (!(bool)currentEntity.IsChildEntity && ((bool)currentEntity.IsAIRUpdated || (bool)currentEntity.IsCustomEntity)).ToString());  
                                metadataWriter.WriteElementString("CanEnableEditableGridMobile", (currentEntity.IsVisibleInMobileClient.Value || currentEntity.IsVisibleInMobileClient.CanBeChanged).ToString());  
                            }  
  
                            // Write the Entity's Information.  
  
                            //End Entity Node  
                            metadataWriter.WriteEndElement();  
                        }  
  
                        // End Metadata Xml Node  
                        metadataWriter.WriteEndElement();  
                        metadataWriter.WriteEndDocument();  
  
                        // Close xml writer.  
                        metadataWriter.Close();  
                        Console.WriteLine("Dumped information in the EditableGridEntityInfo.xml file");  
                    }  
                }  
            }  
  
            // Catch any service fault exceptions that Microsoft Dynamics CRM throws.  
            catch (FaultException<Microsoft.Xrm.Sdk.OrganizationServiceFault>)  
            {  
                // You can handle an exception here or pass it back to the calling method.  
                throw;  
            }  
        }  
        #endregion How To Sample Code  
  
        #region Main  
        /// <summary>  
        /// Standard Main() method used by most SDK samples.  
        /// </summary>  
        /// <param name="args"></param>  
        static public void Main(string[] args)  
        {  
            try  
            {  
                // Obtain the target organization's Web address and client logon   
                // credentials from the user.  
                ServerConnection serverConnect = new ServerConnection();  
                ServerConnection.Configuration config = serverConnect.GetServerConfiguration();  
                DumpEditableGridEntityInfo app = new DumpEditableGridEntityInfo();  
                app.Run(config, false);                  
            }  
            catch (FaultException<Microsoft.Xrm.Sdk.OrganizationServiceFault> ex)  
            {  
                Console.WriteLine("The application terminated with an error.");  
                Console.WriteLine("Timestamp: {0}", ex.Detail.Timestamp);  
                Console.WriteLine("Code: {0}", ex.Detail.ErrorCode);  
                Console.WriteLine("Message: {0}", ex.Detail.Message);  
                Console.WriteLine("Plugin Trace: {0}", ex.Detail.TraceText);  
                Console.WriteLine("Inner Fault: {0}",  
                    null == ex.Detail.InnerFault ? "No Inner Fault" : "Has Inner Fault");  
            }  
            catch (System.TimeoutException ex)  
            {  
                Console.WriteLine("The application terminated with an error.");  
                Console.WriteLine("Message: {0}", ex.Message);  
                Console.WriteLine("Stack Trace: {0}", ex.StackTrace);  
                Console.WriteLine("Inner Fault: {0}",  
                    null == ex.InnerException.Message ? "No Inner Fault" : ex.InnerException.Message);  
            }  
            catch (System.Exception ex)  
            {  
                Console.WriteLine("The application terminated with an error.");  
                Console.WriteLine(ex.Message);  
  
                // Display the details of the inner exception.  
                if (ex.InnerException != null)  
                {  
                    Console.WriteLine(ex.InnerException.Message);  
  
                    FaultException<Microsoft.Xrm.Sdk.OrganizationServiceFault> fe  
                        = ex.InnerException  
                        as FaultException<Microsoft.Xrm.Sdk.OrganizationServiceFault>;  
                    if (fe != null)  
                    {  
                        Console.WriteLine("Timestamp: {0}", fe.Detail.Timestamp);  
                        Console.WriteLine("Code: {0}", fe.Detail.ErrorCode);  
                        Console.WriteLine("Message: {0}", fe.Detail.Message);  
                        Console.WriteLine("Plugin Trace: {0}", fe.Detail.TraceText);  
                        Console.WriteLine("Inner Fault: {0}",  
                            null == fe.Detail.InnerFault ? "No Inner Fault" : "Has Inner Fault");  
                    }  
                }  
            }  
            // Additional exceptions to catch: SecurityTokenValidationException, ExpiredSecurityTokenException,  
            // SecurityAccessDeniedException, MessageSecurityException, and SecurityNegotiationException.  
  
            finally  
            {  
  
                Console.WriteLine("Press <Enter> to exit.");  
                Console.ReadLine();  
            }  
  
        }  
        #endregion Main  
  
    }  
}  
```  
  
### <a name="see-also"></a>Vea también  
 [Cuadrículas y subcuadrículas en aplicaciones basadas en modelos (referencia de API de cliente)](clientapi/reference/grids.md)   
 [Crear cuadrículas (listas) editables de aplicaciones controladas por modelos mediante el control personalizado Cuadrícula editable](../../maker/model-driven-apps/make-grids-lists-editable-custom-control.md)
