## Sintaxis Integrada
Se escriben utilizando una sintaxis similar a SQL, lo que hace que se mas facil y familiar para los desarrolladores trabajar con datos.
 var palabras = new List<string> { "casa", "carro", "perro", "cama", "cielo" };

            // Sintaxis integrada de consulta (Query Syntax)
            var grupos = from palabra in palabras
                         group palabra by palabra[0] into grupoLetra
                         orderby grupoLetra.Key
                         select grupoLetra;

            Console.WriteLine("Agrupación por primera letra:");
            foreach (var grupo in grupos)
            {
                Console.WriteLine($"Letra: {grupo.Key}");
                foreach (var p in grupo)
                    Console.WriteLine("  " + p);
            }
