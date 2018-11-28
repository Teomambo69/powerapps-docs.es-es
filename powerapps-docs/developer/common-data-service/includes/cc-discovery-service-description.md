Puede crear un cliente para un entorno de CDS concreto y no proporcionar al usuario ninguna opción sobre a qué entorno se puede conectar. Solo los usuarios válidos para ese entorno concreto pueden usar su cliente.

Si desea que las personas que usan su cliente puedan conectarse a cualquier entorno de CDS al que tengan acceso, puede pedirles en que introduzcan la dirección URL de su entorno, pero no se recomienda. Cada usuario puede tener acceso a varios entornos de CDS. Puede que los usuarios no sepan o no recuerden la dirección URL de su entorno. Esperar que las personas introduzcan esta dirección URL es algo que frustrará a los usuarios. 

En su lugar, su cliente debe proporcionar una lista de cada uno de los entornos disponibles basados en las credenciales del usuario. Si hay más de un entorno disponible, su aplicación debe pedir al usuario que seleccione a qué entorno desean conectarse.

Con CDS for Apps, la asignación de servidor y de organización puede cambiar como parte del equilibrio de carga y administración del centro de datos. Por lo tanto, el servicio de detección proporciona una forma de detectar qué servidor proporciona una instancia en un momento determinado.