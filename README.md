using System;
using System.Collections;

namespace Practica3
{
  public class Persona
	{
		public String codigo;
		public String nombre;
		public String domicilio;
		public String telefono;
		public String facebook;
		
		
		public Persona(){
			this.codigo = "";
			this.nombre = "";
			this.domicilio = "";
			this.telefono = "";
			this.facebook = "";
		}

		Hashtable hashtable = new Hashtable ();

		public void ingresarDatos(Persona persona){
			for (int i=0; i<=3; i++) {
				Console.WriteLine ("Ingresa el codigo");
				persona.codigo = Console.ReadLine ();
				Console.WriteLine ("Dame tu nombre:");
				persona.nombre = Console.ReadLine ();
				Console.WriteLine ("Dame tu domicilio:");
				persona.domicilio = Console.ReadLine ();
				Console.WriteLine ("Dame tu telefono:");
				persona.telefono = Console.ReadLine ();
				Console.WriteLine ("Dame tu facebook:");
				persona.facebook = Console.ReadLine ();
				Console.WriteLine ("");	
			}
		}
		
		public void Hashtable(Persona persona){  
			hashtable.Add(persona.codigo,persona);
			
		}


		public void pedirCodigo(){
			Console.WriteLine("Introduce el codigo a buscar");
			string cod = Console.ReadLine();
			if(hashtable.ContainsKey(cod) == true){         
				Persona persona = (Persona)this.hashtable[cod];      
				Console.WriteLine("Codigo encontrado");	
				persona.mostrarDatos(persona);
				Console.WriteLine("Pulse una tecla para continuar");	
				Console.ReadKey();	
				Console.Clear();
				Console.WriteLine("Desea eliminar este codigo e introducir uno nuevo? Si/No");
				string opcion = Console.ReadLine();
				if(opcion == "Si"){	
					persona.editarDatos(persona);       
				}else{
					Console.Clear();
				}
				
			}else{
				Console.WriteLine("No encontrado");
			}
		}
		
		
		
		
		public void editarDatos(Persona persona){
		
			hashtable.Remove(persona);
			persona.ingresarDatos(persona);
			hashtable.Add(persona.codigo,persona);
		}

		
		
		
		
		public void mostrarDatos(Persona persona){
			Console.WriteLine(persona.nombre);
			Console.WriteLine(persona.domicilio);
			Console.WriteLine(persona.telefono);
			Console.WriteLine(persona.facebook);
		
		}
		
		
		
		public void imprimeTodos(){
			ICollection personas = this.hashtable.Values;
			Console.WriteLine("Imprimiendo todos los valores de la hashtable");
			foreach( object objeto in personas )
			{
				Persona persona = (Persona) objeto;
				this.mostrarDatos(persona);
			}	
		}

	}
}
		


using System;
using System.Collections;


namespace Practica3
{
  class Principal
	{	
		public Principal(){
			
		}
		
		
		public static void Main (string[] args)
		{
			Persona programa= new Persona();	
			Persona persona = new Persona();

			persona.ingresarDatos(persona);

			
			programa.pedirCodigo();
			programa.imprimeTodos();
		}
	}
}
