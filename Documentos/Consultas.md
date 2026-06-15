# La consulta
Es la encargada de especificar la informacion que se va a obtener del origen de datos. Opcionalmente, una consulta puede especificar como se debe organizar, agrupar y la forma de la informacion antes de presentarse. 
Una consulta se almacena en una variable de consulta y se inicializa con una expresion de consulta. Usando la sintaxis de C# para escribir consultas.
# Clasificacion de operadores de consulta
Las implementaciones LinQ de los metodos de operador consulta estandar se ejecutan de una de estas dos maneras principales: inmediatas o diferidas. Los operadores de consulta que usan la ejecucion diferida se pueden dividir 
en dos categorias: streaming y no streaming.
## Inmediata
Significa que el origen de datos se lee y la operacion se realiza una vez. 
Todos los operadores de consulta estandar que devuelven un resultado escalar se ejecutan inmediatamente. Como ejemplo esta el MAX, COUNT, AVERAGE Y FIRST.
Esta consulta devuelve un valor unico, no una coleccion. Puede forzar que cualquier consulta se ejecute inmediatamente por los metodos. La ejecucion inmediata proporciona 
reutilizacion de los resultados de la consulta, no de la declaracion de consulta. 
## Diferida
Significa que la opreacion no se realiza en el punto de codigo donde se declara la consulta. La operacion solo se realiza cuando se enumera la variable de consulta,
por ejemplo mediante un foreach. Los resultados de ejecutar la consulta dependen del contenido del origen de datos cuando se ejecuta la consulta en lugar de caundo 
se define la consulta. Si la variable de consulta se enumera varias veces, los resultados pueden diferir cada vez. La ejecucion diferedia proporciona la facilidad
de reutilizar las consultas, ya que las consultas capturan datos actualizados de origen de datos cada vez que se iteran los resultados de la consulta.
## Streaming
Los operadores de streaming no tienen que leer todos los datos de origen antes de que produzcan elementos. En el momento de la ejecucion. un operador de streaming
realiza su operacion en cada elemento de origen mientras se lee y proporciona el elemento si es necesario, continua leyendo elementos de origen hasta que se pueda
generar un elemento de resultado.
## No Streaming
Los operadores de no streaming deben leer todos los datos fuente antes de poder producir un elemento de resultado. Las operaciones como la agrupacion se divide en esta 
categoria. En la ejecucion, los operadores de consultas que no son de streaming leen todos los datos de origen, lo colocan en una estructura de datos, y producen los elementos
resultantes.
