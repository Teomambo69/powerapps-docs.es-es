---
title: Configure el seguimiento para los útiles de XRM (Common Data Service para aplicaciones)| Microsoft Docs
description: 'Aprenda cómo puede configurar el seguimiento para componentes como llamadas a operaciones, advertencias, excepciones y otros eventos importantes en útiles de XRM.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: d7586a5a-40da-427e-bbeb-4f8a371a8dcf
caps.latest.revision: 8
author: MattB-msft
ms.author: kvivek
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="configure-tracing-for-xrm-tooling"></a>Configurar el seguimiento de útiles de XRM

Puede habilitar el seguimiento para registrar datos relacionados con los hitos de proceso en todos los componentes de los útiles de XRM, como llamadas de operación, advertencias, excepciones, y otros acontecimientos descriptivos. Esta información se puede usar para solucionar problemas operativos y de rendimiento en las aplicaciones cliente de Windows. El seguimiento en útiles de XRM se genera en la parte superior de [System.Diagnostics.Tracing](/dotnet/api/system.diagnostics.tracing). Para habilitar el seguimiento para un montaje o un componente, por ejemplo Microsoft.Xrm.Tooling.Connector, debe definir las siguientes tres cosas para cada componente del código o del archivo de configuración de la aplicación (*\<AppName>*.exe.config):  
  
- Origen de seguimientos  
- Agente de escucha de seguimientos  
- Nivel de seguimiento que no sea **Desconectado**. Estos son los otros valores que puede especificar: **Error**, **Advertencia**, **Información** y **Detallado**.  
  
 Aquí se muestra configuración para habilitar el seguimiento para un componente en útiles de XRM. Por ejemplo, la siguiente configuración solo habilita el seguimiento para el componente de Microsoft.Xrm.Tooling.CrmConnectControl:  
  
```xml  
</configuration>  
  <system.diagnostics>  
    <trace autoflush="true" />  
    <sources>  
      <source name="DynamicsCrm.CrmConnectControl"  
        switchName="DynamicsCrm.CrmConnectControl"  
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console" type="System.Diagnostics.DefaultTraceListener" />  
          <remove name="Default"/>  
          <add name ="fileListener"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <!--   
            Possible values for switches: Off, Error, Warning, Info, Verbose  
                Verbose:    includes Error, Warning, Info, Trace levels  
                Info:       includes Error, Warning, Info levels  
                Warning:    includes Error, Warning levels  
                Error:      includes Error level  
        -->  
      <add name="DynamicsCrm.CrmConnectControl" value="Verbose"/>  
    </switches>  
    <sharedListeners>  
      <add name="fileListener" type="System.Diagnostics.TextWriterTraceListener" initializeData="XRMLoginControl.log"/>  
      <add name="eventLogListener" type="System.Diagnostics.EventLogTraceListener" initializeData="XRMLogin"/>  
    </sharedListeners>  
  </system.diagnostics>  
</configuration>  
```  
  
Si desea habilitar el seguimiento de todos los componentes en útiles de XRM, puede hacer eso también. Esta es la configuración de un seguimiento combinado de los tres de los componentes en útiles de XRM:  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="true" />  
    <sources>  
      <source name="Microsoft.Xrm.Tooling.Connector.CrmServiceClient"  
              switchName="Microsoft.Xrm.Tooling.Connector.CrmServiceClient"  
              switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console" type="System.Diagnostics.DefaultTraceListener" />  
          <remove name="Default"/>  
          <add name ="fileListener"/>  
        </listeners>  
      </source>  
  
      <source name="Microsoft.Xrm.Tooling.CrmConnectControl"  
              switchName="Microsoft.Xrm.Tooling.CrmConnectControl"  
              switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console" type="System.Diagnostics.DefaultTraceListener" />  
          <remove name="Default"/>  
          <add name ="fileListener"/>  
        </listeners>  
      </source>  
  
      <source name="Microsoft.Xrm.Tooling.WebResourceUtility"  
        switchName="Microsoft.Xrm.Tooling.WebResourceUtility"  
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console" type="System.Diagnostics.DefaultTraceListener" />  
          <remove name="Default"/>  
          <add name ="fileListener"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <!--   
            Possible values for switches: Off, Error, Warning, Info, Verbose  
                Verbose:    includes Error, Warning, Info, Trace levels  
                Info:       includes Error, Warning, Info levels  
                Warning:    includes Error, Warning levels  
                Error:      includes Error level  
        -->  
      <add name="Microsoft.Xrm.Tooling.Connector.CrmServiceClient" value="Verbose" />  
      <add name="Microsoft.Xrm.Tooling.CrmConnectControl" value="Verbose"/>  
      <add name="Microsoft.Xrm.Tooling.WebResourceUtility" value="Verbose" />  
  
    </switches>  
    <sharedListeners>  
      <add name="fileListener" type="System.Diagnostics.TextWriterTraceListener" initializeData="XRMToolingLogs.log"/>        
      <add name="eventLogListener" type="System.Diagnostics.EventLogTraceListener" initializeData="XRMTooling" />  
    </sharedListeners>  
  
  </system.diagnostics>  
</configuration>  
```  
  
### <a name="see-also"></a>Vea también

[Crear aplicaciones cliente de Windows mediante las herramientas XRM](build-windows-client-applications-xrm-tools.md)
