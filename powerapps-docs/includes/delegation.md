## <a name="delegation"></a>Delegación
Cuando sea posible, PowerApps delegará las operaciones de filtro y ordenación al origen de datos y se desplazará por los resultados a petición. Por ejemplo, al iniciar una aplicación que muestre un control **[galería](../controls/control-gallery.md)** relleno con datos, inicialmente solo se pasará al dispositivo el primer conjunto de registros. Cuando el usuario se desplace, se mueven datos adicionales desde el origen de datos. El resultado es una reducción del tiempo de inicio de la aplicación y el acceso a conjuntos de datos muy grandes.

Sin embargo, es posible que la delegación no siempre se pueda realizar. Los orígenes de datos varían en cuanto a las funciones y los operadores que admiten con la delegación. Si no es posible la delegación completa de una fórmula, el entorno de creación marcará con una advertencia la parte que no se puede delegar. Cuando sea posible, considere la posibilidad de cambiar la fórmula para evitar funciones y operadores que no se puedan delegar.  La [lista de delegación](../delegation-list.md) detalla los orígenes de datos y operaciones que se pueden delegar.

Si la delegación no es posible, PowerApps extraerá solo un pequeño conjunto de registros para trabajar localmente. Las funciones de filtro y ordenación operarán en un conjunto reducido de registros. Es posible que en la **[galería](../controls/control-gallery.md)** no esté todo disponible, lo que podría generar confusión a los usuarios. 

Para más información, consulte la [introducción a la delegación](../delegation-overview.md).

