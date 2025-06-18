# PREPARACION






using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace S12_Teoria
{
    class Program
    {
        static void Main(string[] args)
        {
            int[] deposito = { 3700, 3200, 2300, 2200, 3500, 2100, 3900, 8000, 2500, 3100 };
            
            // Llamar a las funciones existentes
            Console.WriteLine("Tamaño: " + tamano(deposito));
            Console.WriteLine("Depósito obtenido: " + obtenerDeposito(deposito, 3));
            Console.WriteLine("Promedio obtenido: " + promedioDepositos(deposito));
            Console.WriteLine("Depósito mayor: " + depositoMayor(deposito));
            Console.WriteLine("Depósito menor: " + depositoMenor(deposito));
            Console.WriteLine("Cantidad de depósitos mayores a 3000: " + cantidadMayores3000(deposito));
            Console.WriteLine("Cantidad de depósitos menores a 2500: " + cantidadMenores2500(deposito));
            Console.WriteLine("Primer valor del rango de 2000 a 2500: " + posPrimerDeposito(deposito));
            Console.WriteLine("Último valor del rango de 3500 a 4000: " + posUltimoDeposito(deposito));

            // Llamamos a la funcion reemplazarDeposito()
            reemplazarDeposito(2, deposito, 5555);
            // Listamos los datos
            listarDatos(deposito);
            
            // Nuevas funciones implementadas
            Console.WriteLine("\n=== Funciones adicionales ===");
            
            // Intercambiar depósitos
            Console.WriteLine("\nAntes de intercambiar:");
            listarDatos(deposito);
            intercambiarDepositos(deposito, 0, 9);
            Console.WriteLine("\nDespués de intercambiar posiciones 0 y 9:");
            listarDatos(deposito);
            
            // Generar nuevos depósitos aleatorios
            generarDepositos(deposito);
            Console.WriteLine("\nNuevos depósitos aleatorios generados:");
            listarDatos(deposito);
            
            Console.WriteLine("\nPresione cualquier tecla para salir...");
            Console.ReadKey();
        }

        // Funcion que retorna la longitud del arreglo
        static int tamano(int[] deposito)
        {
            return deposito.Length;
        }

        // Método obtenerDeposito que reciba una posición y retorne el depósito almacenado
        static int obtenerDeposito(int[] deposito, int pos)
        {
            return deposito[pos];
        }
         
        // Método promedioDepositos que retorne el promedio de todos los depositos
        static double promedioDepositos(int[] deposito)
        {
            int suma = 0;
            for(int i = 0; i < deposito.Length; i++)
            {
                suma += deposito[i];
            }
            return (double)suma / deposito.Length;
        }
        
        // Métodos para obtener el depósito mayor y menor
        static int depositoMayor(int[] deposito)
        {
            int mayor = deposito[0];
            for (int i = 0; i < deposito.Length; i++)
                if (deposito[i] > mayor)
                    mayor = deposito[i];
            return mayor;
        }
        
        static int depositoMenor(int[] deposito)
        {
            int menor = deposito[0];
            for (int i = 0; i < deposito.Length; i++)
                if (deposito[i] < menor)
                    menor = deposito[i];
            return menor;
        }
        
        // Métodos para contar depósitos mayores a 3000 y menores a 2500
        static int cantidadMayores3000(int[] deposito)
        {
            int mayor3000 = 0;
            for (int i = 0; i < deposito.Length; i++)
                if (deposito[i] > 3000)
                    mayor3000++;
            return mayor3000;
        }
        
        static int cantidadMenores2500(int[] deposito)
        {
            int menor2500 = 0;
            for (int i = 0; i < deposito.Length; i++)
                if (deposito[i] < 2500)
                    menor2500++;
            return menor2500;
        }
        
        // Método para encontrar la posición del primer depósito en rango 2000-2500
        static int posPrimerDeposito(int[] deposito)
        {
            for (int i = 0; i < deposito.Length; i++)
            {
                if (deposito[i] >= 2000 && deposito[i] <= 2500)
                    return i; // Devuelve la posición, no el valor
            }
            return -1;
        }

        // Método para encontrar la posición del último depósito en rango 3500-4000
        static int posUltimoDeposito(int[] deposito)
        {
            for (int i = deposito.Length-1; i >= 0; i--)
            {
                if (deposito[i] >= 3500 && deposito[i] <= 4000)
                    return i; // Devuelve la posición, no el valor
            }
            return -1;
        }

        // Método para reemplazar un depósito en una posición específica
        static void reemplazarDeposito(int pos, int[] deposito, int nuevoDep)
        {
            deposito[pos] = nuevoDep;
        }
        
        // Método para listar todos los depósitos
        static void listarDatos(int[] deposito)
        {
            for (int i = 0; i < deposito.Length; i++)
            {
                Console.WriteLine($"Posición {i}: {deposito[i]}");
            }
        }
        
        // Método para intercambiar dos depósitos (NUEVO)
        static void intercambiarDepositos(int[] deposito, int pos1, int pos2)
        {
            if (pos1 < 0 || pos1 >= deposito.Length || pos2 < 0 || pos2 >= deposito.Length)
            {
                Console.WriteLine("Posiciones inválidas para intercambio");
                return;
            }
            
            int temp = deposito[pos1];
            deposito[pos1] = deposito[pos2];
            deposito[pos2] = temp;
        }
        
        // Método para generar depósitos aleatorios entre 2000 y 10000 (NUEVO)
        static void generarDepositos(int[] deposito)
        {
            Random rnd = new Random();
            for (int i = 0; i < deposito.Length; i++)
            {
                deposito[i] = rnd.Next(2000, 10001); // 10001 porque el máximo es exclusivo
            }
        }
    }
}
