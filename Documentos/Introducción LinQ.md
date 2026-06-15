# Introducción a LINQ
LinQ o Language Integrated Query son un conjunto de herramientas de Microsoft para realizar todo tipo de consultas a distintas fuentes de datos, base de datos. Para ello, usan tipo de funciones propias , que unifican las operaciones mas comunes en todos los entornos para conseguir un mismo lenguaje para todo tipo de tareas con datos.
## LinQ en C#
La sintaxis es parecida a SQL, pero con las ventajas de que tenemos la potencia de .net y visual studio a la hora de codificar. 
<img width="1051" height="96" alt="Captura de pantalla 2026-06-15 120304" src="https://github.com/user-attachments/assets/f47b2c11-a9b1-4772-9c23-d882c29a1134" />
Como se puede ver accedemos a una coleccion y filtramos todos los elementos que cumplan con la propiedad 1 sea verdadera. Del resultado de esa consulta, podemos sacar una lista de elemntos con el ToList() y el numero de ellos con un count().
## Operadores LAMBDA
Aparte del metodo anterior para acceder a las operaciones de LinQ, podemos hacer uso de una sintaxis más directa a la hora de interactuar con LinQ. Esto puede hacerse mediante expresiones de metodos apoyados por operadores lambda. Con ellas podemos llamar a las funciones de where, join, select directamente desde el objeto.

<img width="630" height="45" alt="image" src="https://github.com/user-attachments/assets/4c30b744-202c-4fc6-8678-2b5418cb69f7" />

# Consulta de LinQ en C#
Una consulta es una expresion que recupera datos de un origen de datos. Los distintos origenes de datos tienen diferentes lenguajes de consulta nativa, como en SQL para base de datos relacionales. Los desarrolladores deben aprender un nuevo tipo de leguaje por cada tipo de origen de datos. LinQ simplifica esta situacion al ofrecer un modelo de lenguaje C# coherente para tipos de origenes de datos. Usando los mismos patrones de codificacion basicos para consultas de datos.
## Partes de una operacion de consulta
- Obtenga el origen de datos.
- Cree la consulta.
- Ejecutar la consulta.
En el siguiente ejemplo se usa un vector de enteros como origen de datos:

```csharp
int[] numbers = { 0, 1, 2, 3, 4, 5, 6 };

// Creación de la consulta
var numQuery = from num in numbers
               where (num % 2) == 0
               select num;

// Ejecución de la consulta
foreach (int num in numQuery)
{
    Console.Write("{0} ", num);
}
```
