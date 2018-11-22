Al habilitar la inserción de ventanas y paneles de Power BI, cuando un usuario inserta un mosaico o un panel de Power BI, ese token de autorización de [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] del cliente para [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] se usa para autenticarse en el servicio de Power BI con una concesión implícita, que proporciona una experiencia de "inicio de sesión único" perfecta para el usuario final.  
  
 Un administrador puede deshabilitar la inserción de ventanas y paneles de Power BI en cualquier momento, para dejar de usar el token de autorización de [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] para autenticarse en el servicio de Power BI. Cualquier ventana o panel existente detendrán la representación para el usuario final.  
  
 En la siguiente sección se detalla el componente o servicio de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] implicado en la inserción de ventanas de Power BI.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
 Este servicio proporciona el token de autenticación intercambiado con el servicio de Power BI para la autenticación API y de la interfaz de usuario.