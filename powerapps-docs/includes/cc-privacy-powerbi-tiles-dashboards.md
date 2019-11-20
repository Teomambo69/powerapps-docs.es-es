Al habilitar la inserción de mosaicos y paneles de Power BI, cuando un usuario inserta un mosaico o un panel de Power BI, ese símbolo de autorización de [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] del cliente para Common Data Service se usa con el fin de autenticarse en el servicio de Power BI con una concesión implícita, que proporciona una experiencia de "inicio de sesión único" perfecta para el usuario final.  
  
 Los administradores pueden deshabilitar la inserción de mosaicos y paneles de Power BIen cualquier momento para dejar de usar el símbolo de autorización de [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] con el fin de autenticarse en el servicio de Power BI. Los mosaicos o los paneles existentes detendrán la representación para el usuario final.  
  
 En la siguiente sección se describe el componente o servicio de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] involucrado en la inserción de mosaicos de Power BI.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
 Este servicio proporciona el símbolo de autenticación intercambiado con el servicio de Power BI para la autenticación de la API y la interfaz de usuario.
