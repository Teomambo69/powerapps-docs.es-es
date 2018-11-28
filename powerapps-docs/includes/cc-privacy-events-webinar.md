Al aceptar los términos y condiciones de la administración de eventos, se activa la característica de integración de seminarios web. La característica de integración de seminarios web utiliza un partner proveedor de seminarios web para llevar a cabo un evento o una sesión como un seminario web. Para usar el servicio de un proveedor de seminarios web, debe tener una cuenta con ese proveedor. En estos momentos, el único servicio de partner proveedor de seminarios web listo para usar que se proporciona es ON24. Cuando se utiliza la característica de integración de seminarios web, los datos esenciales para proporcionar y ejecutar el seminario web se procesan y almacenan en [!INCLUDE[pn-azure-service-fabric](../includes/pn-azure-service-fabric.md)] y, después, se envían a ON24. Esos datos incluyen los datos de registro de los participantes en el seminario web, como sus nombres, direcciones de correo electrónico y nombres de compañía. Además, ON24 envía métricas de los seminarios web, como la duración de visualización de los mismos, a [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] a través de [!INCLUDE[pn-azure-service-fabric](../includes/pn-azure-service-fabric.md)].

No es necesario activar la característica de seminarios web para usar el resto de la solución de administración de eventos. Un administrador puede desactivar la característica de integración de seminarios web si quita las credenciales en la configuración del seminario web.

La característica de integración de seminarios web utiliza estos componentes y servicios de [!INCLUDE[pn-windows-azure](../includes/pn-windows-azure.md)]:

- [!INCLUDE[pn_azure_key_vault](../includes/pn_azure_key_vault.md)] ([!INCLUDE[proc-more-information](../includes/proc-more-information.md)] [¿Qué es Azure Key Vault?](https://docs.microsoft.com/en-us/azure/key-vault/key-vault-whatis))
  - Proporciona la clave de cifrado para cifrar o descifrar las credenciales de la cuenta de ON24 del cliente
- [!INCLUDE[pn-azure-service-fabric](../includes/pn-azure-service-fabric.md)] ([!INCLUDE[proc-more-information](../includes/proc-more-information.md)] [Información general de Azure Service Fabric](https://docs.microsoft.com/en-us/azure/service-fabric/service-fabric-overview))
  - Procesa y envía a ON24 los datos de registro y las credenciales de cuenta de los seminarios web
  - Recupera las métricas de los seminarios web de On24 en [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)]: almacena las credenciales de la cuenta de ON24 del cliente (cifrado personalizado)