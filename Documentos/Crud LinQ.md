# Proceso CRUD
CRUD es un acrónimo en inglés que define las cuatro operaciones fundamentales que se pueden realizar en cualquier sistema de almacenamiento de datos (como una base de datos, un archivo de texto o una lista en memoria).
Cada letra representa una acción que permite gestionar el ciclo de vida completo de la información.
## Create (Crear)
En LINQ añadir elementos a una secuencia existente no modifica la secuencia original (ya que LINQ es de naturaleza inmutable y diferida). En su lugar, se generan nuevas secuencias combinadas.
## Read (Leer)
La lectura es la operación más compleja debido a que impacta directamente en la percepción de velocidad que tiene el usuario. Cuando lees una entidad que tiene relaciones (por ejemplo, un Cliente que tiene una lista de Pedidos), existen tres formas de gestionar esa lectura en .NET
## Update (Actualizar)
En la programación funcional y con LINQ, el "Update" profesional no altera las propiedades del objeto original (lo cual podría causar efectos secundarios en aplicaciones multi-hilo). En su lugar, se utiliza Select() para proyectar una nueva colección con los datos modificados.
## Delete (Eliminar)
En LINQ, "eliminar" no significa destruir un objeto o usar .Remove(). Significa excluir elementos de la secuencia resultante. La herramienta definitiva para esto es el operador Where() configurado con lógica inversa, o el operador Except().
# Ejemplos
## Insercion
```csharp
var nuevoProducto = new Producto { Id = 2, Nombre = "Teclado", Precio = 50 };
IEnumerable<Producto> listaConNuevo = productosIniciales.Append(nuevoProducto);
```
## Leer
```csharp
var reporteProductos = listaCompleta
    .Where(p => p.Precio > 50 && p.Categoria == "Premium") // Filtro de lectura
    .OrderByDescending(p => p.Precio)                     // Ordenamiento
    .Select(p => new {                                    // Proyección (Leer solo lo necesario)
        p.Nombre,
        PrecioConImpuesto = p.Precio * 1.15m
    })
    .ToList();
```
## Actualizar
```csharp
var productosModificados = listaCompleta.Select(p => 
{
    if (p.Precio > 100)
    {
        return new Producto { Id = p.Id, Nombre = p.Nombre, Precio = p.Precio * 0.9m };
    }
    return p; 
});
```
## Eliminar
```csharp
var productosFiltrados = listaCompleta.Where(p => p.Precio > 50);
```


