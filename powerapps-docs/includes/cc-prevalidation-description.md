Para la operación inicial, esta fase se producirá antes de la operación del sistema principal.<br /><br />Esto brinda una oportunidad para incluir lógica para cancelar la operación antes de la transacción de la base de datos.<br /><br />Las operaciones posteriores desencadenadas por extensiones registradas en otras fases pasarán esta fase, pero se incluirán en la transacción de las extensiones de llamada.<br /><br />Esta fase tiene lugar antes de las comprobaciones de seguridad que se realizan para comprobar que el usuario que hace la llamada o que ha iniciado sesión tiene el permiso adecuado para realizar la operación prevista.