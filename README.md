# Ejercicioo-09
using System;

namespace TiendaVirtual
{
    class Cuenta
    {
        private string nombre;
        private double saldo;

        public Cuenta(string nombre, double saldo)
        {
            this.nombre = nombre;
            this.saldo = saldo;
        }

        public void MostrarDatos()
        {
            Console.WriteLine("\n--- DATOS DE LA CUENTA ---");
            Console.WriteLine("Titular: " + nombre);
            Console.WriteLine("Saldo: $" + saldo);
        }

        public void Depositar(double cantidad)
        {
            saldo += cantidad;
            Console.WriteLine("Depósito realizado correctamente.");
        }

        public void Retirar(double cantidad)
        {
            if (cantidad <= saldo)
            {
                saldo -= cantidad;
                Console.WriteLine("Retiro realizado correctamente.");
            }
            else
            {
                Console.WriteLine("Saldo insuficiente.");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            string nombre;
            double saldo;
            int opcion;

            Console.WriteLine("*** Creando mi Cuenta ***");
            Console.Write("\nIngrese el nombre del titular: ");
            nombre = Console.ReadLine();

            Console.Write("Ingrese el saldo inicial: ");
            saldo = double.Parse(Console.ReadLine());

            // Crear objeto de la clase Cuenta
            Cuenta cue = new Cuenta(nombre, saldo);
            Console.WriteLine("Cuenta creada...");

            cue.MostrarDatos();

            // Menú de operaciones
            do
            {
                Console.WriteLine("\n*** Operaciones Disponibles ***");
                Console.WriteLine("1. Depositar saldo");
                Console.WriteLine("2. Retirar saldo");
                Console.WriteLine("3. Ver datos de la cuenta");
                Console.WriteLine("4. Salir");
                Console.Write("Seleccione la opción: ");
                opcion = int.Parse(Console.ReadLine());

                switch (opcion)
                {
                    case 1:
                        Console.Write("Ingrese la cantidad a depositar: ");
                        double cantDep = double.Parse(Console.ReadLine());
                        cue.Depositar(cantDep);
                        break;
                    case 2:
                        Console.Write("Ingrese la cantidad a retirar: ");
                        double retiro = double.Parse(Console.ReadLine());
                        cue.Retirar(retiro);
                        break;
                    case 3:
                        cue.MostrarDatos();
                        break;
                    case 4:
                        Console.WriteLine("Saliendo del programa...");
                        break;
                    default:
                        Console.WriteLine("Opción no válida.");
                        break;
                }

            } while (opcion != 4);
        }
    }
}
