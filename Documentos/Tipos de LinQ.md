## LinQ en Objetos
Este tipo de uso del LinQ permite realizar consultas sobre arreglos y listas. Es la forma mas comun de utilizar LinQ y permite aplicar operaciones como filtrado, proyeccion
y agregacion sobre los datos en memoria.
```csharp
List<string> frutas = new List<string> { "Manzana", "Banana", "Cereza", "Durazno" };

var frutasConA = from fruta in frutas
                 where fruta.Contains("a")
                 select fruta;

foreach (var fruta in frutasConA)
{
    Console.WriteLine(fruta);
}
```
En este ejemplo usamos una lista tipo string en la cual almacenamos frutas en la cual el LinQ va contado las a que tienen las frutas para luego soltarnos una respuesta
que la leemos con un foreach
## LinQ en SQL
Este tipo de uso del LinQ facilita la interaccion con bases de datos de SQL Server utilizando una sintaxis LinQ. Permitiendo realizar consultas las tablas de la base
de datos como si fueran objetos en C#, lo que simplifica el accesso a los datos.
DataContext db = new DataContext("connectionString");
```csharp
var clientes = from cliente in db.GetTable<Cliente>()
               where cliente.Ciudad == "Madrid"
               select cliente;

foreach (var cliente in clientes)
{
    Console.WriteLine(cliente.Nombre);
}
```
En este ejempo usamos el objeto clientes que obtenemos de la base de datos almacenandolo en una variable tipo var cuando la ciudad del cliente sea madrir para luego
con un foreach mostrar los clientes que cumplen esa condicion.
## LinQ en XML
Este tipo de uso del LinQ proporciona una forma sencilla y manipular documentos de XML. Permitiendo realizar consultas usando la sintaxis de LinQ, lo que facilita
la extraccion y transformacion de datos XML.
XDocument xmlDoc = XDocument.Load("frutas.xml");
```csharp
var frutasConA = from fruta in xmlDoc.Descendants("fruta")
                 where fruta.Value.Contains("a")
                 select fruta;

foreach (var fruta in frutasConA)
{
    Console.WriteLine(fruta.Value);
}
```
En este ejemplo usamos el documento de XML para poder llenar la variable de tipo var y contar las letras a de las frutas para luego presentar en un foreach.
