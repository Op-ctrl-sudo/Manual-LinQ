# Que son las funciones de agregado
Las funciones de agregado en programación y bases de datos (como SQL o LINQ en C#) son herramientas que toman un conjunto de valores o una lista de registros y los procesan para devolver un único valor resumido.
En lugar de analizar fila por fila de forma individual, estas funciones miran el panorama completo para darte una métrica estadística o matemática.
## Funcionalidades de las funciones de agregado
- Count (Conteo): Cuenta cuántos elementos o registros existen en total.
- Sum (Sumatoria): Suma todos los valores numéricos de una columna.
- Average / Avg (Promedio): Calcula la media aritmética de los valores.
- Min (Mínimo): Encuentra el valor más bajo de la lista.
- Max (Máximo): Encuentra el valor más alto de la lista.
## Ventajas y Deventajas
| Ventajas | Desventaja |
| :--- | :--- |
| **Alta eficiencia:** El motor de la base de datos procesa millones de filas en milisegundos porque está optimizado para cálculos matemáticos directos en el disco. | **Bloqueo de tablas:** Si se ejecuta un agregado masivo (SUM o COUNT) en tablas gigantes sin los índices correctos, se puede ralentizar toda la base de datos temporalmente. |
| **Ahorro crítico de RAM:** El servidor web no se satura. En lugar de transferir gigabytes de registros por la red, solo viaja un único número (ej. el resultado del conteo). | **Falta de detalle:** Al recibir solo el dato resumido, pierdes el acceso a los registros individuales. No puedes saber quién compró, solo cuánto se vendió en total. |
| **Legibilidad y abstracción:** Herramientas como LINQ permiten escribir operaciones complejas (Average, Max) en una sola línea de código muy limpia. | **Curva de aprendizaje en la traducción:** Si escribes mal la consulta en LINQ, EF Core podría no saber cómo traducirla a SQL y arrojará un error en tiempo de ejecución (InvalidOperationException). |
| **Automatización:** Motores como SQL ignoran los valores NULL automáticamente al promediar o sumar, evitando errores de formato. | | **Riesgo de Excepciones:** En LINQ, si aplicas .Average() o .Max() sobre una lista que termina estando completamente vacía, el programa lanzará un error si no validas la existencia de datos previamente. |
---
## Ejemplos
Conteo y promedio:
```csharp
public List<ReporteCursoDTO> ObtenerEstadisticasCursos()
{
    var reporte = _context.Matriculas
        .Where(m => m.Curso.Activo == true)
        .GroupBy(m => m.Curso.NombreCurso) 
        .Select(grupo => new ReporteCursoDTO 
        {
            NombreCurso = grupo.Key,
            TotalEstudiantes = grupo.Count(), // Cuenta registros en el grupo
            NotaPromedio = grupo.Average(m => m.CalificacionFinal) // Calcula el promedio del grupo
        })
        .OrderBy(r => r.NombreCurso)
        .ToList();

    return reporte;
}
```
Min y el Max:
```csharp
public List<dynamic> ObtenerRangosDePreciosPorCategoria()
{
    return _context.Cursos
        .GroupBy(c => c.Categoria.NombreCategoria)
        .Select(g => new {
            Categoria = g.Key,
            PrecioMinimo = g.Min(c => c.Precio), // Obtiene el menor valor
            PrecioMaximo = g.Max(c => c.Precio)  // Obtiene el mayor valor
        })
        .ToList<dynamic>();
}
```
