# ARBOLBINARIODEBUSQUEDAUMG.
public class ArbolBinarioUMG {
//´fredy martinez
    public ArbolBinarioUMG()
    {
        raiz = null;
    }
    int contadorNodos;
HashSet<Integer> numeros = new HashSet<Integer>();
		System.out.println("Tamaño antes de generar números: " + numeros.size());
		int rechazados = 0;
		long tiempoInicial = System.currentTimeMillis();
		while(numeros.size() < 1_000_000) { 
		    if (!numeros.add((int)((Math.random()*1_000_000) + 1)))
		    	rechazados++;
		}
		long tiempoFinal = System.currentTimeMillis();
		System.out.println("Tamaño despues de generar números: " + numeros.size());
		System.out.println("números rechazados: " + rechazados);
		System.out.printf("transcurridos: %.2f", (tiempoFinal - tiempoInicial)/1000f);
 


    class Nodo
    {
        int info;
        ArbolBinarioOrdenado.Nodo izq;
        ArbolBinarioOrdenado.Nodo der;
    }
   

    ArbolBinarioOrdenado.Nodo raiz;
   
   
     public void insertar(int info)
    {
        //Declaramos objeto nuevoArbol
        ArbolBinarioOrdenado.Nodo nuevoArbol = new ArbolBinarioOrdenado.Nodo();
       
        //Asigamos información
        nuevoArbol.info = info;
        nuevoArbol.izq = null;
        nuevoArbol.der = null;
       
        //Verificamos si es raiz
        if (raiz == null)
        {
            raiz = nuevoArbol;
        }
        else
        {
            //Inicializamos dos nuevos nodos
            ArbolBinarioOrdenado.Nodo anterior = null;
            ArbolBinarioOrdenado.Nodo actual = null;
           
            //Igualamos el nodo actual a la raiz
            actual = raiz;
            //Realizamos la logica de ir recorriendo el nodo actual y sus subarboles
            while (actual != null)
            {
                anterior = actual;
                if (info < actual.info)
                {
                    actual = actual.izq;
                }
                else
                {
                    actual = actual.der;
                }
            }
            //Si el nodo actual es nulo, agregamos información a sus lados
            if (info < anterior.info)
            {
                anterior.izq = nuevoArbol;       
            }
            else
            {
                anterior.der = nuevoArbol;
            }
        }
    }//Termina método Insertar
     
     private void imprimirPreOrden(ArbolBinarioOrdenado.Nodo recorriendo)
    {
        //Funcion recursiva Preorden
        //Recorrido Raiz Izq. Der.
        if (recorriendo != null)
        {
            System.out.print(recorriendo.info + " ");
            imprimirPreOrden(recorriendo.izq);
            imprimirPreOrden(recorriendo.der);
        }
    }
       
    private void imprimirInOrden(ArbolBinarioOrdenado.Nodo recorriendo)
    {
        //Funcion recursiva InOrden
        //Recorrido  Izq. Raiz Der.
        if (recorriendo != null)
        {
            imprimirInOrden(recorriendo.izq);
            System.out.print(recorriendo.info + " ");
            imprimirInOrden(recorriendo.der);
        }
    }
    private void imprimirPosOrden(ArbolBinarioOrdenado.Nodo recorriendo)
    {
        //Funcion recursiva PosOrden
        //Recorrido  Izq. Der. Raiz
        if (recorriendo != null)
        {
            imprimirPosOrden(recorriendo.izq);
            imprimirPosOrden(recorriendo.der);
            System.out.print(recorriendo.info + " ");
        }
    }
     
    public void llamarPreorden()
    {
        System.out.println("\nImpresion preorden: ");
        imprimirPreOrden(raiz);
        System.out.println();
    }
    public void llamarInorden()
    {
        System.out.println("\nImpresion inorden: ");
        imprimirInOrden(raiz);
        System.out.println();   
    }
   
    public void llamarPosorden()
    {
         System.out.println("\nImpresion postorden: ");
        imprimirPosOrden(raiz);
        System.out.println();   
    }
       
    public static void main(String[] args)
    {
        ArbolBinarioOrdenado abo  = new ArbolBinarioOrdenado();
       
       
        abo.insertar(56);
        abo.insertar(24);
        abo.insertar(76);
        abo.insertar(12);
        abo.insertar(27);
        abo.insertar(87);
        abo.insertar(45);
        abo.insertar(85);
        abo.insertar(90);
        abo.insertar(40);
        abo.insertar(54);
        abo.llamarPreorden();
        abo.llamarInorden();
        abo.llamarPosorden();       
