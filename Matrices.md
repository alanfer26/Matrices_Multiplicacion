# using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace MATRICES_TAREA
{
    class Program
    {
        int[,] mat1;
        int[,] mat2;
        int[,] m;
        int fila1;
        int fila2;
        int celda1;
        int celda2;
        static void Main(string[] args)
        {
            Program matrix_mult = new Program();
            matrix_mult.cargar_matriz();
            matrix_mult.imprimir_matriz();
            matrix_mult.multiplicar_matriz();
            matrix_mult.imprimir_mult();
            Console.ReadKey();
        }
        public void cargar_matriz()
        {
            
            Console.WriteLine("*Ingrese el tamaño de la primera matriz: ");
            Console.Write("Ingrese la cantidad de FILAS\n");
            fila1 = Int32.Parse(Console.ReadLine());
            Console.Write("Ingrese la cantidad de COLUMNAS\n");
            celda1 = Int32.Parse(Console.ReadLine());
            Console.WriteLine();

            Console.WriteLine("Ingrese el tamaño de la segunda matriz: ");
            Console.Write("Ingrese la cantidad de FILAS\n");
            fila2 = Int32.Parse(Console.ReadLine());
            Console.Write("Ingrese la cantidad de COLUMNAS\n");
            celda2 = Int32.Parse(Console.ReadLine());
            Console.WriteLine();

            mat1 = new int[fila1 + 1, celda1 + 1];
            mat2 = new int[fila2 + 1, celda2 + 1]; 
            m = new int[fila1 + 1, celda2 + 1];

            Random r1 = new Random();
           

            for (int i = 1; i < mat1.GetLength(0); i++)
            {
                for (int k = 1; k < mat1.GetLength(1); k++)
                {
                    int num1 = r1.Next(1, 10);
                    mat1[i, k] = num1;
                }
            }
           

            for (int i = 1; i < mat2.GetLength(0); i++)
            {
                for (int k = 1; k < mat2.GetLength(1); k++)
                {
                    int num1 = r1.Next(1, 10);
                    mat2[i, k] = num1;
                }
            }
            Console.WriteLine();
        }


        public void imprimir_matriz()
        {
            Console.WriteLine("ELEMENTOS DE LA PRIMERA MATRIZ..");
            for (int i = 1; i < mat1.GetLength(0); i++)
            {
                for (int k = 1; k < mat1.GetLength(1); k++)
                {
                    Console.Write(mat1[i, k] + " ");
                }
                Console.WriteLine();
            }

            Console.WriteLine("ELEMENTOS DE LA SEGUNDA MATRIZ..");
            for (int i = 1; i < mat2.GetLength(0); i++)
            {
                for (int k = 1; k < mat2.GetLength(1); k++)
                {
                    Console.Write(mat2[i, k] + " ");
                }
                Console.WriteLine();
            }
        }

        public void multiplicar_matriz()
        {
            if (celda1 == fila2)
            {
                // Multiplicando las 2 matrices
                for (int i = 1; i <= fila1; i++)
                {
                    for (int k = 1; k <= celda2; k++)
                    {
                        m[i, k] = 0;
                        for (int z = 1; z <= celda1; z++)
                        {
                            m[i, k] = mat1[i, z] * mat2[z, k] + m[i, k];
                        }
                        //Console.WriteLine(m[i, j] + " ");
                    }
                }
            }

        }

        public void imprimir_mult()
        {

            if (celda1 == fila2)
            {
                Console.WriteLine();
                Console.WriteLine("*** RESULTADO DE LA MULTIPLICACIÓN DE LAS MATRICES ***\n");
                for (int i = 1; i <= fila1; i++)
                {
                    for (int k = 1; k <= celda2; k++)
                    {
                       
                        Console.Write("{0} ", m[i, k]);
                       
                    }
                    Console.WriteLine();
                  
                }
            }
            else
            {
                Console.WriteLine("Error: No se puede multiplicar las matrices" + "  Columnas: {0}!= Filas: {1}", celda1, fila2);
            }

        }
    }
}
