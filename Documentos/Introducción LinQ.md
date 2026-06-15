# Introducción
a LINQ
Language Integrated Query (LINQ) es una de las herramientas más potentes de C#. Te permite realizar consultas, filtrar y transformar datos directamente en tu código utilizando una sintaxis limpia y unificada, sin importar si los datos provienen de una lista en memoria, un archivo XML o una base de datos.

---

## 🚀 Sintaxis de Consulta vs. Sintaxis de Métodos

En LINQ existen dos formas de escribir la misma consulta. Es importante que conozcas ambas, aunque en el día a día se suele preferir la **Sintaxis de Métodos**.

Supongamos que tenemos una lista de números y queremos obtener solo los que son mayores a 5:

csharp
List<int> numeros = new List<int> { 2, 4, 6, 8, 10 };
