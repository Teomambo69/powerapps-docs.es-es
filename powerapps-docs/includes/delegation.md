## <a name="delegation"></a>Delegación
Siempre que sea posible, Power Apps delegará las operaciones de filtrado y ordenación al origen de datos y se desplazará por los resultados a petición. Por ejemplo, cuando se inicia una aplicación que muestra un control **[Galería](../maker/canvas-apps/controls/control-gallery.md)** lleno de datos, inicialmente solo se traerá al dispositivo el primer conjunto de registros. A medida que el usuario se desplace por los datos, se traerán más datos del origen de datos. El resultado es un inicio más rápido de la aplicación y acceso a conjuntos de datos muy grandes.

Sin embargo, la delegación no siempre es posible. La compatibilidad de funciones y operadores con la delegación varía según el origen de datos. Si la delegación completa de una fórmula no es posible, el entorno de creación indicará la parte que no se puede delegar con una advertencia. Si es posible, considere la posibilidad de cambiar la fórmula para que no incluya las funciones y los operadores que no se pueden delegar.  La [lista de delegación](../maker/canvas-apps/delegation-list.md) detalla qué orígenes de datos y operaciones se pueden delegar.

Si la delegación no es posible, Power Apps solo descargará un conjunto reducido de registros para trabajar localmente. Las funciones de filtrado y ordenación trabajarán con un conjunto reducido de registros. En la **[Galería](../maker/canvas-apps/controls/control-gallery.md)** puede no estará disponible la historia completa, y esto puede resultar confuso a los usuarios. 

Consulte la [información general sobre delegación](../maker/canvas-apps/delegation-overview.md) para obtener más información.

