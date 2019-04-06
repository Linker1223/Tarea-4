# Tarea-4

## 1\. Considera el siguiente fragmento de programa:

System;

class A

{

public int a;

public A()

{

a = 10;

}

public \_\_\_\_\_\_\_ string Display()

{

return a.ToString();

}

}

class B:A

{

public int b;

public B():base()

{

b = 15;

}

//
\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#

// \# Después de contestar la pregunta 1

// \# Redefine el método Display( ) en este espacio, debe regresar el
campo b como string.

//
\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#

}

class Program

{

public static void Main()

{

A objA = new A();

B objB = new B();

Console.WriteLine(objA.Display()); //// (1 )

Console. WriteLine(objB.Display()); //// ( 2)

}

}

## 1.1 ¿Qué valores imprimen las lineas (1) y (2) ?

10 y
10

## 1.2. Redefine el método Display en el espacio indicado, Una vez redefinido el método, ¿qué valores imprimen las lineas (1) y (2) ?.

10 y
15

## 1.3. ¿Que palabra debes agregar en la linea (public \_\_\_\_\_\_\_ string Display()) al definir A.Display()?

Virtual

## 2.0 Considera el siguiente fragmento de programa:

`using System;

using System.Collections.Generic;

\_\_\_\_\_\_\_\_ class Musico

{

public string nombre;

public Musico (string n)

{

nombre = n;

}

public abstract **(A)** void Afina(); **(B)**

public **(C)** string Display()

{

return nombre;

}

}

class Bajista; Musico

{

public string instrumento;

public Bajista (string n, string i ) ......

.........

public \_\_\_\_\_\_\_\_\_ Afina()

{

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

}

}

class Guitarrista \_\_\_\_\_\_\_\_\_\_\_\_

{

public instrumento;

// Falta el constructor y otras cosas??

}

class Program

{

public static Main()

{

Musico musico = new Musico("Django"); **(D)**

Bajista b = new Bajista("Flea");

Guitarrista g = new Guitarrista("Santana");

List\<Musico\> musicos = \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

musicos.Add( b);

musicos.Add(g);

foreach ( \_\_\_\_\_in musicos\_\_\_\_\_\_)

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

// (m as IAfina).Afina()

Console.ReadKey();

}

}`


## 2.1. Completa el programa.

    using System;
    using System.Collections.Generic;
    abstract class Musico
    {
        public string nombre;
        public Musico(string n)
        {
            nombre = n;
        }
        public abstract void Afina();
        public string Display()
        {
            return nombre;
        }
    }
    class Bajista : Musico
    {
        public string instrumento;
        public Bajista(string n, string i) : base(n)
        {
            this.instrumento = i;
        }
        public override void Afina()
        {
            Console.WriteLine("{0} afina el {1}", nombre, instrumento);
        }
    }
    class Guitarrista : Musico
    {
        public string instrumento;
        public Guitarrista(string n, string i) : base(n)
        {
            this.instrumento = i;
        }
        public override void Afina()
        {
            Console.WriteLine("{0} afina el {1}", nombre, instrumento);
        }
    }
    class Program
    {
        public static void Main()
        {
            //No se puede instanciar una objeto de una clase virtual
            //Musico m = new Musico("Django"); 
            Bajista b = new Bajista("Flea", "bajo acústico");
            Guitarrista g = new Guitarrista("Santana", "guitarra Yamaha");
            List<Musico> musicos = new List<Musico>();
            musicos.Add(b);
            musicos.Add(g);
            foreach (Musico musico in musicos)
            {
                Console.WriteLine(musico.Afina());
                musico.Afina();
            }
            Console.ReadKey();
        }
    }
    
## 2.2. Hay un error en uno de los puntos (A)(B)(C)(D). ¿Cuál es y por qué?
En el D ya que no se pueden crear instancias u objetos en la clase

## 2.3. ¿Qué método se debe implementar obligatoriamente en ambas clases y por qué?
El metodo afina, nos marcaria error siempre por ser abstracto

## 2.4. ¿Por qué no se ponen las llaves en (B)?, ¿Cuando si se pondrían?
Al ser abstracto, este no requiere cuerpo, no como otros metodos que regresan valores

## 2.5. ¿Qué pasa si el método Afina() lo hacemos virtual en lugar de abstract?
Al hacerlo virtual, tendriamos que agregarle un cuerpo, aparte de implementar el override posteriormente

## 3. Implementa el programa utilizando interfaces en lugar de herencia.
using System;

using System.Collections.Generic;

interface IAfinable

{

  void Afina();
  
}

abstract class Musico

{

    public string nombre;

    public Musico(string name)
    {
        nombre = name;
    }
    public string Display()
    {
        return nombre;
    }
}

class Bajista : Musico, IAfinable

{

    public string instrumento;
    public Bajista(string n, string i) : base(n)
    {
        this.instrumento = i;
    }
    public void Afina()
    {
        Console.WriteLine("{0} afina el {1}", nombre, instrumento);
    }
    
}

class Guitarrista : Musico, IAfinable

{

    public string instrumento;
    public Guitarrista(string n, string i) : base(n)
    {
        this.instrumento = i;
    }
    public void Afina()
    {
        Console.WriteLine("{0} afina la {1}", nombre, instrumento);
    }
    
}

class Program

{

  public static void Main()
  
    {
        Bajista b = new Bajista("Flea", "bajo acústico");
        Guitarrista g = new Guitarrista("Santana", "guitarra Yamaha");
        List<Musico> musicos = new List<Musico>();
        musicos.Add(b);
        musicos.Add(g);
        foreach (Musico musico in musicos)
        {
            Console.WriteLine(musico.Display());
            (musico as IAfinable).Afina();
        }
        Console.ReadKey();
    }
}

(Enserio, no entiendo por que markdown no detecta ciertas partes del codigo como codigo...)
