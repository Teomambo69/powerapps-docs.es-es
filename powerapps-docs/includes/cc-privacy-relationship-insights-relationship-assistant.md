Al habilitar la característica Asistente de relaciones, se recuperan datos de intercambio limitados, lo que incluye el nombre y la dirección de correo electrónico de un remitente, así como extractos del cuerpo de correo electrónico (pero no se almacenan en [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]), con el fin de mostrar información importante del correo electrónico. Además, la característica Asistente de relaciones se puede configurar para recuperar información relativa a noticias, finanzas e información del vuelos, enviando solicitudes a componentes externos como MSN Dinero y Bing (que no se consideran servicios principales de [!INCLUDE[pn_ms_dyn_365](pn-ms-dyn-365.md)]). Para habilitar y deshabilitar la característica Asistente de relaciones, un administrador debe ir a **Configuración** > **Configuración de inteligencia**, hacer clic en la pestaña **Asistente de relaciones** y seleccionar la opción adecuada.  
  
 En las siguientes secciones se detallan los componentes externos involucrados en la funcionalidad Asistente de relaciones.  
  
 **[!INCLUDE[pn_bing](pn-bing.md)]**  
  
 El Asistente de relaciones utiliza [!INCLUDE[pn_bing](pn-bing.md)] para buscar noticias relevantes para mostrar a un usuario usando los nombres de cuenta de los datos de [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] del usuario.  
  
 **[!INCLUDE[pn_ms_MSN_Money](pn-ms-msn-money.md)]**  
  
 El Asistente de relaciones utiliza [!INCLUDE[pn_ms_MSN_Money](pn-ms-msn-money.md)] para mostrar a un usuario noticias de bolsa relevantes usando el símbolo de cotización de la cuenta que figura en los datos de [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] de dicho usuario.