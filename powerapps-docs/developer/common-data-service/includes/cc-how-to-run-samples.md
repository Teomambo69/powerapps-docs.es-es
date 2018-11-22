1. Descargar o clonar el informe de  [Muestras](https://github.com/Microsoft/PowerApps-Samples) para que tenga una copia local.
1. (Opcional) Edite el archivo cds/App.config para definir una cadena de conexión que especifique la instancia Common Data Service para aplicaciones a la que desea conectarse.
1. Abra la solución de ejemplo en Visual Studio y presione **F5** para ejecutar la muestra. Una vez que especifique una cadena de conexión en cds/App.config, cualquier muestra que ejecute utilizará esa información de conexión.

Si no especifica una cadena de conexión en el archivo cds/App.config, se abrirá un diálogo cada vez que ejecute la muestra y tendrá que introducir información acerca de a qué instancia CDS for Apps desea conectarse y qué credenciales desea usar. Este diálogo guardará en caché conexiones anteriores para que pueda elegir una conexión usada previamente.

Las muestras en este informe que requieran una conexión a una instancia Common Data Service para aplicaciones para ejecutarse incluirá una referencia vinculada al archivo cds/App.config.
