## <a name="mapping-functions-for-dynamics-365-customer-engagement-plan"></a>Funciones de mapas para Dynamics 365 Customer Engagement Plan 
 Field Service y Project Service Automation cuentan con funciones clave que se basan en la ubicación. Por ejemplo, la ubicación de las cuentas de servicio (que definen dónde se llevan a cabo los servicios o las tareas) o la ubicación inicial y final de los recursos (personas que realizan servicios o tareas).  Para que el sistema muestre estos elementos en un mapa, o para que calcule las distancias existentes entre los puntos, es necesario usar un servicio de asignación (en este caso, Mapas de Bing).  
  
 A continuación se muestra el flujo de trabajo hacia y desde el servicio Mapas de Bing:  
  
|Desde Microsoft Dynamics 365|Mapas de Bing devuelve|Nota|  
|-----------------------|-----------------------|----------|  
|Dirección (cuenta o recurso)|Latitud y longitud de la dirección (ubicación)|Esto se denomina “codificación geográfica” de una dirección.|  
|Conjunto de ubicaciones (latitud/longitud)|Distancia entre ubicaciones|Se puede utilizar para encontrar las rutas óptimas para los recursos o para calcular los tiempos de viaje.|  
|Conjunto de ubicaciones (latitud/longitud)|Vista de mapa con las ubicaciones como marcadores en el mapa|Se utiliza para ver las cuentas y los recursos en una vista de mapa.|  
  
> [!NOTE]
>  Aparte de los datos mencionados anteriormente, no se envía ningún otro dato al servicio Mapas de Bing.
