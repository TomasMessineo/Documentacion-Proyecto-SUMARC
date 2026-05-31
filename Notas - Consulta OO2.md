
**10 de refactoring:**

Cuando hay un bad smell de switch statement y hay un setter, existen indicios de que el polimorfismo no alcanza y que hay que usar un Strategy o un State.

### Refactoring

# **Ejercicio 7:**  

|                                                                                                                                                                                                                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1<br>2<br>3<br>4<br>5<br>6<br>7<br>8<br>9<br>10<br>11<br>12<br>13<br>14<br>15<br>16<br>17<br>18<br>19<br>20<br>21<br>22<br>23<br>24<br>25<br>26<br>27<br>28<br>29<br>30<br>31<br>32<br>33<br>34<br>35<br>36<br> | abstract class Etiqueta {<br>    protected String nombreProducto;<br>    protected double precio;<br><br>    public Etiqueta(String nombre, double precio) {<br>        this.nombreProducto = nombre;<br>        this.precio = precio;<br>    }<br>} <br><br>class EtiquetaSimple extends Etiqueta {<br>    public EtiquetaSimple(String nombre, double precio) {<br>        super(nombre, precio);<br>    }<br><br>    public void generar() {<br>        System.out.println("--- ETIQUETA BÁSICA ---");<br>        System.out.println("Producto: " + nombreProducto);<br>        System.out.println("Precio: $" + precio);<br>        System.out.println("-----------------------");<br>    }<br>}<br><br>class EtiquetaDetalle extends Etiqueta {<br><br>    public EtiquetaDetalle(String nombre, double precio) {<br>        super(nombre, precio);<br>    }<br><br>    public void generar() {<br>        System.out.println("--- ETIQUETA DETALLE ---");<br>        System.out.println("Producto: " + nombreProducto);<br>        System.out.println("Precio sin imp.: $" + (precio * 0.79));<br>        System.out.println("Precio final: $" + precio);<br>        System.out.println("-----------------------");<br>    } |
1) Sí, existe código duplicado en las líneas 18 con 32, 19 con 34, y 20 con 35.

2) Para aplicar el refactoring Pull Up Method primero tengo que aplicar una serie de refactorings más antes de poder hacerlo, debido a que los métodos aún no tienen exactamente el mismo cuerpo.

3) Para poder aplicar el refactoring Pull Up Method podría aplicar un refactoring que me permite llegar a un patrón de diseño: Form Template Method, que como consecuencia me deja expresado en el código el patrón de diseño Template Method.
   Para aplicar este refactoring tengo que tener en cuenta que debo separar toda la lógica idéntica en métodos diferentes en cambas clases... no significa que los cuerpos de los métodos
   
4) 

**Aplicando extract method:**

| 1<br>2<br>3<br>4<br>5<br>6<br>7<br>8<br>9<br>10<br>11<br>12<br>13<br>14<br>15<br>16<br>17<br>18<br>19<br>20<br>21<br>22<br> 23<br>24<br>25<br>26<br>27<br>28<br>29<br>30<br>31<br>32<br>33<br>34<br>35<br>36<br> | abstract class Etiqueta {<br>    protected String nombreProducto;<br>    protected double precio;<br><br>    public Etiqueta(String nombre, double precio) {<br>        this.nombreProducto = nombre;<br>        this.precio = precio;<br>    }<br>} <br><br>class EtiquetaSimple extends Etiqueta {<br>    public EtiquetaSimple(String nombre, double precio) {<br>        super(nombre, precio);<br>    }<br><br>    public void generar() {<br>        this.imprimirEncabezado();<br>        this.imprimirNombreProducto();<br>        this.imprimirPrecio();<br>        this.imprimirLineaDeFin();<br>    }<br><br>	public String imprimirEncabezado(){<br>	     System.out.println("--- ETIQUETA BÁSICA ---");<br>	}<br><br>    public String imprimirPrecio() {<br>	    System.out.println("Precio: $" + precio);<br>	}<br><br>	public String imprimirNombreProducto() {<br>        System.out.println("Producto: " + nombreProducto);<br>	}<br><br>	public String imprimirLineaDeFin(){<br>        System.out.println("-----------------------");<br>	}<br>}<br><br>class EtiquetaDetalle extends Etiqueta {<br><br>    public EtiquetaDetalle(String nombre, double precio) {<br>        super(nombre, precio);<br>    }<br><br>     public void generar() {<br>        this.imprimirEncabezado();<br>        this.imprimirNombreProducto();<br>        this.imprimirPrecio();<br>        this.imprimirLineaDeFin();<br>    }<br><br>	public String imprimirEncabezado(){<br>	     System.out.println("--- ETIQUETA DETALLE ---");<br>	}<br><br>    public String imprimirPrecio() {<br>    	System.out.println("Precio sin imp.: $" + (precio * 0.79));<br>	    System.out.println("Precio: $" + precio);<br>	}<br><br>	public String imprimirNombreProducto() {<br>        System.out.println("Producto: " + nombreProducto);<br>	}<br><br>	public String imprimirLineaDeFin(){<br>        System.out.println("-----------------------");<br>	}<br>} |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
Luego aplico un pull up method sobre todo lo que sea idéntico en ambas clases: generar(), imprimirNombreProducto() e imprimirLineaFIn(). A su vez, también declaro como abstractos y protegidos los métodos imprimirPrecio e imprimirEncabezado en "Etiqueta", ya que cada subclase hace algo particular y diferente en este paso del Template Method, y esto sirve para definir los "Hooks" o ganchos que Fowler define en el libro.
Luego de hacer esto, ya se habrá aplicado el Form Template Method.

| 1<br>2<br>3<br>4<br>5<br>6<br>7<br>8<br>9<br>10<br>11<br>12<br>13<br>14<br>15<br>16<br>17<br>18<br>19<br>20<br>21<br>22<br> 23<br>24<br>25<br>26<br>27<br>28<br>29<br>30<br>31<br>32<br>33<br>34<br>35<br>36<br> | abstract class Etiqueta {<br>    protected String nombreProducto;<br>    protected double precio;<br><br>    public Etiqueta(String nombre, double precio) {<br>        this.nombreProducto = nombre;<br>        this.precio = precio;<br>    }<br><br>	public void generar() {<br>        this.imprimirEncabezado();<br>        this.imprimirNombreProducto();<br>        this.imprimirPrecio();<br>        this.imprimirLineaDeFin();<br>    }<br><br>    public String imprimirNombreProducto() {<br>        System.out.println("Producto: " + nombreProducto);<br>	}<br><br>	public String imprimirLineaDeFin(){<br>        System.out.println("-----------------------");<br>	}<br>    <br>    protected abstract String imprimirEncabezado();<br>    protected abstract String imprimirPrecio();<br>} <br><br>class EtiquetaSimple extends Etiqueta {<br>    public EtiquetaSimple(String nombre, double precio) {<br>        super(nombre, precio);<br>    }<br><br>	public String imprimirEncabezado(){<br>	     System.out.println("--- ETIQUETA BÁSICA ---");<br>	}<br><br>    public String imprimirPrecio() {<br>	    System.out.println("Precio: $" + precio);<br>	}<br>}<br><br>class EtiquetaDetalle extends Etiqueta {<br><br>    public EtiquetaDetalle(String nombre, double precio) {<br>        super(nombre, precio);<br>    }<br><br>	public String imprimirEncabezado(){<br>	     System.out.println("--- ETIQUETA DETALLE ---");<br>	}<br><br>    public String imprimirPrecio() {<br>    	System.out.println("Precio sin imp.: $" + (precio * 0.79));<br>	    System.out.println("Precio: $" + precio);<br>	}<br>} |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

# **Ejercicio 9:**

```java
01: public class Pedido {  
02:  private Cliente cliente;  
03:  private List<Producto> productos;  
04:  private String formaPago;  
05:  public Pedido(Cliente cliente, List<Producto> productos, String formaPago) {  
06:     if (!"efectivo".equals(formaPago)  
07:        && !"6 cuotas".equals(formaPago)  
08:        && !"12 cuotas".equals(formaPago)) {  
09:          throw new Error("Forma de pago incorrecta");  
10:    }  
11:    this.cliente = cliente;  
12:    this.productos = productos;  
13:    this.formaPago = formaPago;  
14:   }  
15:   public double getCostoTotal() {  
16:     double costoProductos = 0;  
17:     for (Producto producto : this.productos) {  
18:       costoProductos += producto.getPrecio();  
19:     }  
20:     double extraFormaPago = 0;  
21:     if ("efectivo".equals(this.formaPago)) {  
22:       extraFormaPago = 0;  
23:     } else if ("6 cuotas".equals(this.formaPago)) {  
24:       extraFormaPago = costoProductos * 0.2;  
25:     } else if ("12 cuotas".equals(this.formaPago)) {  
26:       extraFormaPago = costoProductos * 0.5;  
27:     }  
28:     int añosDesdeFechaAlta = Period.between(this.cliente.getFechaAlta(), LocalDate.now()).getYears();  
29:     // Aplicar descuento del 10% si el cliente tiene más de 5 años de antiguedad  
30:     if (añosDesdeFechaAlta > 5) {  
31:       return (costoProductos + extraFormaPago) * 0.9;  
32:     }  
33:     return costoProductos + extraFormaPago;  
34:   }  
35: }  
36: public class Cliente {  
37:   private LocalDate fechaAlta;  
38:   public LocalDate getFechaAlta() {  
39:     return this.fechaAlta;  
40:   }
```

1) 
   
**PASO 1:**
Aplico primero el extract method y luego un move method de la linea 28 para resolver el bad smell feature envy. Primero, aplico extract method extrayendo/desacoplando la lógica almacenada en la variable añosDesdeeFechaAlta en un método separado.

```java
01: public class Pedido {  
02:  private Cliente cliente;  
03:  private List<Producto> productos;  
04:  private String formaPago;  
05:  public Pedido(Cliente cliente, List<Producto> productos, String formaPago) {  
06:     if (!"efectivo".equals(formaPago)  
07:        && !"6 cuotas".equals(formaPago)  
08:        && !"12 cuotas".equals(formaPago)) {  
09:          throw new Error("Forma de pago incorrecta");  
10:    }  
11:    this.cliente = cliente;  
12:    this.productos = productos;  
13:    this.formaPago = formaPago;  
14:   }  
15:   public double getCostoTotal() {  
16:     double costoProductos = 0;  
17:     for (Producto producto : this.productos) {  
18:       costoProductos += producto.getPrecio();  
19:     }  
20:     double extraFormaPago = 0;  
21:     if ("efectivo".equals(this.formaPago)) {  
22:       extraFormaPago = 0;  
23:     } else if ("6 cuotas".equals(this.formaPago)) {  
24:       extraFormaPago = costoProductos * 0.2;  
25:     } else if ("12 cuotas".equals(this.formaPago)) {  
26:       extraFormaPago = costoProductos * 0.5;  
27:     }  
28:     int añosDesdeFechaAlta = this.añosDesdeFechaAlta();
29:     // Aplicar descuento del 10% si el cliente tiene más de 5 años de antiguedad  
30:     if (añosDesdeFechaAlta > 5) {  
31:       return (costoProductos + extraFormaPago) * 0.9;  
32:     }  
33:     return costoProductos + extraFormaPago;  
34:   }  

		public añosDesdeFechaAlta() {
			return Period.between(this.cliente.getFechaAlta(), LocalDate.now()).getYears();
		}
35: }  
36: public class Cliente {  
37:   private LocalDate fechaAlta;  
38:   public LocalDate getFechaAlta() {  
39:     return this.fechaAlta;  
40:   }
```

Aplico el refactoring move method, moviendo el método añosDesdeFechaAlta() hacia la clase "Cliente", y modificando el envío de mensaje a dicho método en la clase this por la referencia a la variable de instancia interna "cliente".

```java
01: public class Pedido {  
02:  private Cliente cliente;  
03:  private List<Producto> productos;  
04:  private String formaPago;  
05:  public Pedido(Cliente cliente, List<Producto> productos, String formaPago) {  
06:     if (!"efectivo".equals(formaPago)  
07:        && !"6 cuotas".equals(formaPago)  
08:        && !"12 cuotas".equals(formaPago)) {  
09:          throw new Error("Forma de pago incorrecta");  
10:    }  
11:    this.cliente = cliente;  
12:    this.productos = productos;  
13:    this.formaPago = formaPago;  
14:   }  
15:   public double getCostoTotal() {  
16:     double costoProductos = 0;  
17:     for (Producto producto : this.productos) {  
18:       costoProductos += producto.getPrecio();  
19:     }  
20:     double extraFormaPago = 0;  
21:     if ("efectivo".equals(this.formaPago)) {  
22:       extraFormaPago = 0;  
23:     } else if ("6 cuotas".equals(this.formaPago)) {  
24:       extraFormaPago = costoProductos * 0.2;  
25:     } else if ("12 cuotas".equals(this.formaPago)) {  
26:       extraFormaPago = costoProductos * 0.5;  
27:     }  
28:     int añosDesdeFechaAlta = this.cliente.añosDesdeFechaAlta();
29:     // Aplicar descuento del 10% si el cliente tiene más de 5 años de antiguedad  
30:     if (añosDesdeFechaAlta > 5) {  
31:       return (costoProductos + extraFormaPago) * 0.9;  
32:     }  
33:     return costoProductos + extraFormaPago;  
34:   }  
35: }  

36: public class Cliente {  
37:   private LocalDate fechaAlta;  
38:   public LocalDate getFechaAlta() {  
39:     return this.fechaAlta;  
40:   }

		public añosDesdeFechaAlta() {
			return Period.between(this.cliente.getFechaAlta(), LocalDate.now()).getYears();
		}
```

**Paso 3:**
Prosiguiendo con el punto 4, para solucionar el bad smell "long method" (que en realidad es el bad smell principal de este método getCostoTotal) aplico un extract method en las líneas 28 a 33 creando un método privado "calcularCostoExtra()" el cual recibe 2 parámetros, y luego un refactoring Inline Temp para reemplazar la variable temporal utilizada, llevando todo al return directamente.

```java
01: public class Pedido {  
02:  private Cliente cliente;  
03:  private List<Producto> productos;  
04:  private String formaPago;  
05:  public Pedido(Cliente cliente, List<Producto> productos, String formaPago) {  
06:     if (!"efectivo".equals(formaPago)  
07:        && !"6 cuotas".equals(formaPago)  
08:        && !"12 cuotas".equals(formaPago)) {  
09:          throw new Error("Forma de pago incorrecta");  
10:    }  
11:    this.cliente = cliente;  
12:    this.productos = productos;  
13:    this.formaPago = formaPago;  
14:   }  
15:   public double getCostoTotal() {  
16:     double costoProductos = 0;  
17:     for (Producto producto : this.productos) {  
18:       costoProductos += producto.getPrecio();  
19:     }  
20:     double extraFormaPago = 0;  
21:     if ("efectivo".equals(this.formaPago)) {  
22:       extraFormaPago = 0;  
23:     } else if ("6 cuotas".equals(this.formaPago)) {  
24:       extraFormaPago = costoProductos * 0.2;  
25:     } else if ("12 cuotas".equals(this.formaPago)) {  
26:       extraFormaPago = costoProductos * 0.5;  
27:     }  

		return this.calcularDescuentoPorAntiguedad(costoProductos, extraFormaPago);
34:   }

		private calcularDescuentoPorAntiguedad(
			double costoProductos,
			double extraFormaPago
		){
			int añosDesdeFechaAlta = this.cliente.añosDesdeFechaAlta();
		    if (añosDesdeFechaAlta > 5) {  
		      return (costoProductos + extraFormaPago) * 0.9;  
		    }  
		    return costoProductos + extraFormaPago;  
		}
35: }  






36: public class Cliente {  
37:   private LocalDate fechaAlta;  
38:   public LocalDate getFechaAlta() {  
39:     return this.fechaAlta;  
40:   }

		public añosDesdeFechaAlta() {
			return Period.between(this.cliente.getFechaAlta(), LocalDate.now()).getYears();
		}
```

Luego de hacer esto, me doy cuenta que puedo volver a hacer otro extract method para solucionar duplicate code, pero esta vez en calcularDescuentoPorAntiguedad()... así también como otro replace temp with query, eliminando la variable correspondiente a los años y agregandola en la condición IF... **¿está bien si vuelvo a aplicar otra vez el mismo refactoring? Tengo que aplicar solo los que me dice, o en caso de que surja otro refactoring que no entra dentro de los mencionados en el enunciado NO puedo aplicarlo?**

```java
01: public class Pedido {  
02:  private Cliente cliente;  
03:  private List<Producto> productos;  
04:  private String formaPago;  

05:  public Pedido(Cliente cliente, List<Producto> productos, String formaPago) {  
06:     if (!"efectivo".equals(formaPago)  
07:        && !"6 cuotas".equals(formaPago)  
08:        && !"12 cuotas".equals(formaPago)) {  
09:          throw new Error("Forma de pago incorrecta");  
10:    }  
11:    this.cliente = cliente;  
12:    this.productos = productos;  
13:    this.formaPago = formaPago;  
14:   }  
15:   public double getCostoTotal() {  
16:     double costoProductos = 0;  
17:     for (Producto producto : this.productos) {  
18:       costoProductos += producto.getPrecio();  
19:     }  
20:     double extraFormaPago = 0;  
21:     if ("efectivo".equals(this.formaPago)) {  
22:       extraFormaPago = 0;  
23:     } else if ("6 cuotas".equals(this.formaPago)) {  
24:       extraFormaPago = costoProductos * 0.2;  
25:     } else if ("12 cuotas".equals(this.formaPago)) {  
26:       extraFormaPago = costoProductos * 0.5;  
27:     }  

		return this.calcularDescuentoPorAntiguedad(costoProductos, extraFormaPago);
34:   }

		private double calcularDescuentoPorAntiguedad( double costoProductos, double extraFormaPago){
		    if (this.cliente.añosDesdeFechaAlta() > 5) {   // Otros refactorings como la creación de constantes por magic numbers NO podría aplicarlos porque el enunciado no lo indica, ¿o sí?
		      return this.calcularTotal() * 0.9;  
		    }  
		    return this.calcularTotal();
		}
		
		private double calcularTotal(double costoProductos, double extraFormaPago) {
			return costoProductos + extraFormaPago;
		}
35: }  




36: public class Cliente {  
37:   private LocalDate fechaAlta;  
38:   public LocalDate getFechaAlta() {  
39:     return this.fechaAlta;  
40:   }

		public añosDesdeFechaAlta() {
			return Period.between(this.cliente.getFechaAlta(), LocalDate.now()).getYears();
		}
```

**Paso 3:**

Aplico un refactoring replace loop with pipeline en la línea 17-19, debido a un bad smell relacionado con el uso de un foreach, cuando realmente deberían usarse los streams de java.

```java
01: public class Pedido {  
02:  private Cliente cliente;  
03:  private List<Producto> productos;  
04:  private String formaPago;  

05:  public Pedido(Cliente cliente, List<Producto> productos, String formaPago) {  
06:     if (!"efectivo".equals(formaPago)  
07:        && !"6 cuotas".equals(formaPago)  
08:        && !"12 cuotas".equals(formaPago)) {  
09:          throw new Error("Forma de pago incorrecta");  
10:    }  
11:    this.cliente = cliente;  
12:    this.productos = productos;  
13:    this.formaPago = formaPago;  
14:   }  
15:   public double getCostoTotal() {  
16:     double costoProductos = this.productos.stream()
								  .mapToDouble(p -> p.getPrecio())
								  .sum();  
		
20:     double extraFormaPago = 0;  
21:     if ("efectivo".equals(this.formaPago)) {  
22:       extraFormaPago = 0;  
23:     } else if ("6 cuotas".equals(this.formaPago)) {  
24:       extraFormaPago = costoProductos * 0.2;  
25:     } else if ("12 cuotas".equals(this.formaPago)) {  
26:       extraFormaPago = costoProductos * 0.5;  
27:     }  

		return this.calcularDescuentoPorAntiguedad(costoProductos, extraFormaPago);
34:   }

		private double calcularDescuentoPorAntiguedad( double costoProductos, double extraFormaPago){
		    if (this.cliente.añosDesdeFechaAlta() > 5) {   // Otros refactorings como la creación de constantes por magic numbers NO podría aplicarlos porque el enunciado no lo indica, ¿o sí?
		      return this.calcularTotal() * 0.9;  
		    }  
		    return this.calcularTotal();
		}
		
		private double calcularTotal(double costoProductos, double extraFormaPago) {
			return costoProductos + extraFormaPago;
		}
35: }  




36: public class Cliente {  
37:   private LocalDate fechaAlta;  
38:   public LocalDate getFechaAlta() {  
39:     return this.fechaAlta;  
40:   }

		public añosDesdeFechaAlta() {
			return Period.between(this.cliente.getFechaAlta(), LocalDate.now()).getYears();
		}
```

**Paso 4:**
Por último, soluciono el bad smell de "If statement" aplicando el refactoring "replace conditional with polimorphism" en las líneas 21 a 27. Para ello voy a realizar los siguientes pasos:

- Crear una interfaz llamada "FormaPago", la cual definirá el método "calcularExtra(double costoProductos)"
- Crear 3 clases más que implementen dicha interfaz: "DoceCuotas", "SeisCuotas" y "Efectivo".
- En cada una de las clases que implementan la interfaz "FormaPago", implemento el método "calcularExtra(double costoProductos)".
- Cambio el tipo de dato de la variable instancia "formaPago" de la clase Pedido por el tipo de la interfaz "FormaPago".
- Elimino el bloque de código que genera el bad smell "if statement", dejando solo la variable temporal "extraFormaPago" que retornará el resultado de enviar el mensaje "calcularExtra" a la interfaz FormaPago.
- **Elimino también las líneas 06 a 10, ya que ahora no tiene sentido tener eso debido a que "formaPago" ya no es un string, sino una interfaz, y en tiempo de ejecución se definirá que subclase que implementa la interfaz va a ejecutar el método de forma polimórfica. Es más, ahora directamente tiraría error el compilador de Java si se quiere instanciar una clase que no esté definida y que implemente la interfaz "FormaPago"** 

```java
01: public class Pedido {  
02:  private Cliente cliente;  
03:  private List<Producto> productos;  
04:  private FormaPago formaPago;  

05:  public Pedido(Cliente cliente, List<Producto> productos, FormaPago formaPago) {  
11:    this.cliente = cliente;  
12:    this.productos = productos;  
13:    this.formaPago = formaPago;  
14:   }  
15:   public double getCostoTotal() {  
16:     double costoProductos = this.productos.stream()
								  .mapToDouble(p -> p.getPrecio())
								  .sum();  
20:     double extraFormaPago = this.formaPago.calcularExtra(costoProductos);
		return this.calcularDescuentoPorAntiguedad(costoProductos, extraFormaPago);
34:   }

		private double calcularDescuentoPorAntiguedad( double costoProductos, double extraFormaPago){
		    if (this.cliente.añosDesdeFechaAlta() > 5) {   // Otros refactorings como la creación de constantes por magic numbers NO podría aplicarlos porque el enunciado no lo indica, ¿o sí?
		      return this.calcularTotal() * 0.9;  
		    }  
		    return this.calcularTotal();
		}
		
		private double calcularTotal(double costoProductos, double extraFormaPago) {
			return costoProductos + extraFormaPago;
		}
35: }  


36: public class Cliente {  
37:   private LocalDate fechaAlta;  
38:   public LocalDate getFechaAlta() {  
39:     return this.fechaAlta;  
40:   }

		public añosDesdeFechaAlta() {
			return Period.between(this.cliente.getFechaAlta(), LocalDate.now()).getYears();
		}
	}
	
	
	interface FormaPago {
		public double calcularExtra(double costo);
	}
	
	
	public class DoceCuotas implements FormaPago {
		public double calcularExtra(double costo) {
			return costo * 0.5;
		}
	}
	
	public class SeisCuotas implements FormaPago {
		public double calcularExtra(double costo) {
			return costo * 0.2;
		}
	}
	
	public class Efectivo implements FormaPago{
		public double calcularExtra(double costo) {
			return 0;	
		}
	}
```

**Con esto terminaría de aplicar los pasos.**

**DUDA: VEO QUE TAMBIÉN TENGO BAD SMELLS COMO MAGIC NUMBERS, PERO PUEDO APLICAR UN REFACTORING PARA ELLO LUEGO DE HABER APLICADO LO QUE EL EJERCICIO ME SOLICITABA, O NO ES NECESARIO? O A LO MEJOR PUEDO ANOTARLO COMO OBSERVACIÓN EXTRA (teniendo en cuenta una situación así en el parcial)**

**También podría seguir refactorizando... como por ejemplo aplicar otro replace temp with query para eliminar las 2 variables temporales que me quedaron en getCostoTotal()... para ello llevaría el stream de productos a otro método privado que retorne un double, y enviar el mensaje calcularExtra a la interfaz dentro del llamado al método calcularDescuento, para tener todo en una línea de código... 
Haciendo esto, el método getCostoTotal() me quedaría algo así:**

```java
	// ANTES
	public double getCostoTotal() {  
	    double costoProductos = this.productos.stream()
									  .mapToDouble(p -> p.getPrecio())
									  .sum();  
	    double extraFormaPago = this.formaPago.calcularExtra(costoProductos);
		return this.calcularDescuentoPorAntiguedad(costoProductos, extraFormaPago);
	}
		
	//DESPUÉS
	public double getCostoTotal() {
		return this.calcularDescuentoPorAntiguedad(
					this.calcularCostoProductos,
					this.formaPago.calcularExtra(this.calcularCostoProductos) // Se puede hacer algo así en el parcial? Es decir, aplicar un paso extra que no se indicó o algo así.
		);
	}
	
	private double calcularCostoProductos() {
		return this.productos.stream()
				  .mapToDouble(p -> p.getPrecio())
				  .sum();  
	}
```

# Ejercicio 10

En el material adicional encontrará una aplicación que registra y factura llamadas telefónicas. Para lograr tal objetivo, la aplicación permite administrar números telefónicos, como así también clientes asociados a un número. Los clientes pueden ser personas físicas o jurídicas. Además, el sistema permite registrar las llamadas realizadas, las cuales pueden ser nacionales o internacionales. Luego, a partir de las llamadas, la aplicación realiza la facturación, es decir, calcula el monto que debe abonar cada cliente.

Importe el [material adicional](https://drive.google.com/file/d/1pYLNrobyZdUW2cwwK0AuEkH5tLdbrRC8/view?usp=sharing) provisto por la cátedra y analícelo para identificar y corregir los malos olores que presenta. En forma iterativa, realice los siguientes pasos: 

(i) indique el mal olor, 
(ii) indique el refactoring que lo corrige, 
(iii) aplique el refactoring (modifique el código). 
(iv) asegúrese de que los tests provistos corran exitosamente.
Si vuelve a encontrar un mal olor, retorne al paso (i).

Tareas:
1. Describa la solución inicial con un diagrama de clases UML.
2. Documente la secuencia de refactorings aplicados, como se indica previamente. 
3. Describa la solución final con un diagrama de clases UML.

---

**Paso 1:**
Bad smell Public Fields en la clase Empresa, líneas 11 y 12.
Para solucionarlo, aplico el refactoring "Encapsulate Field" de las constantes.

---

**Paso 2:**
Bad smell Uncommunicative Name en las líneas 11 y 12 de "Empresa". El nombre de las constantes no es claro.
Para corregirlo aplico el refactoring "Rename Variable"

---

**Paso 3:**
Duplicate Code en las líneas 32 a 45 de la clase "Empresa":

```java
public Cliente registrarUsuario(String data, String nombre, String tipo) {
	Cliente var = new Cliente();
	if (tipo.equals("fisica")) {
		var.setNombre(nombre);
		String tel = this.obtenerNumeroLibre();
		var.setTipo(tipo);
		var.setNumeroTelefono(tel);
		var.setDNI(data);
	}
	else if (tipo.equals("juridica")) {
		String tel = this.obtenerNumeroLibre();
		var.setNombre(nombre);
		var.setTipo(tipo);
		var.setNumeroTelefono(tel);
		var.setCuit(data);
	}
	clientes.add(var);
	return var;
}
```

Para solucionar esto aplico move method extrayendo la lógica común de ambos ifs en un nuevo método "crearCliente()"

---

**Paso 4:**

Feature Envy en el método agregarNumeroTelefono de "Empresa", en 

```java
public boolean agregarNumeroTelefono(String str) {
	boolean encontre = guia.getLineas().contains(str);
	if (!encontre) 
		guia.getLineas().add(str);
		encontre= true;
		return encontre;
	}
	else {
		encontre= false;
		return encontre;
	}
}
```

Para solucionar esto aplico move method para mover esa lógica que no debe estar en Empresa hacia GestorNumerosDisponibles, y luego modificando los llamados de referencia en agregarNumeroTelefono().

```java
public boolean agregarNumeroTelefono(String str) {
	boolean encontre = guia.contiene(str);
	if (!encontre) 
		guia.agregar(str);
		encontre= true;
		return encontre;
	}
	else {
		encontre= false;
		return encontre;
	}
}
```

Puedo aplicar también un refactoring replace temp with query, ya que ahora el código tiene la variable temporal encontre que no son necesarias y dificultan la legibilidad. Agrego el llamado a guia.contiene() dentro del if. Modifico también los retornos de forma específica por true si encontré y false si no lo hice.

```java
public boolean agregarNumeroTelefono(String str) {
	if (!guia.contiene(str)) 
		guia.agregar(str);
		return true;
	}
	return false;
}
```

---

**Paso 5:**

Feature Envy en el método registrarLlamada en la clase Empresa, el agregado a las llamadas de origen debería ser a través de un método. Además, se está accediendo directamente a una variable pública, lo cual es un bad smell "Public Field".
Para solucionar esto, primero aplico un refactoring Encapsulate Field en la clase Cliente, haciendo que la variable "llamadas" sea privada, lo cual supone crear un getter en la clase Cliente y modificar las referencias directas a esa variable "llamadas" en todas las clases que lo requieran. Esto soluciona el bad smell Public Field.

Luego de hacer esto, soluciono el feature envy aplicando un move method, moviendo la lógica de agregar la llamada a la clase "Cliente", creando un método agregarLlamada();

```java
public Llamada registrarLlamada(Cliente origen, Cliente destino, String t, int duracion) {
	Llamada llamada = new Llamada(t, origen.getNumeroTelefono(), destino.getNumeroTelefono(), duracion);
	llamadas.add(llamada);
	origen.agregarLlamada(llamada);
	return llamada;
}
```

---

**Paso 6:**

Feature Envy en el método calcularMontoTotalLlamadas de Empresa.

```java
public double calcularMontoTotalLlamadas(Cliente cliente) {
	double c = 0;
	for (Llamada l : cliente.getLlamadas()) {
		double auxc = 0;
		if (l.getTipoDeLlamada() == "nacional") {
			// el precio es de 3 pesos por segundo más IVA sin adicional por establecer la llamada
			auxc += l.getDuracion() * 3 + (l.getDuracion() * 3 * 0.21);
		} else if (l.getTipoDeLlamada() == "internacional") {
			// el precio es de 150 pesos por segundo más IVA más 50 pesos por establecer la llamada
			auxc += l.getDuracion() * 150 + (l.getDuracion() * 150 * 0.21) + 50;
		}
		if (cliente.getTipo() == "fisica") {
			auxc -= auxc*descuentoFisica;
		} else if(cliente.getTipo() == "juridica") {
			auxc -= auxc*descuentoJuridica;
		}
		c += auxc;
	}
	return c;
}
```

Para solucionarlo, muevo el método a la clase Cliente, ya que es algo que debería hacer el cliente y no la Empresa. Aplico Move Method de dicho método a la clase Cliente, y hago que empresa lo delegue a cliente. Envío descuentoFisica y descuentoJuridica por parámetro

```java
// En empresa:
public double calcularMontoTotalLlamadas(Cliente cliente) {
	return cliente.calcularMontoTotalLlamadas(descuentoFisica, descuentoJuridica);
}

// En cliente:

public double calcularMontoTotalLlamadas(double descuentoFisica, double descuentoJuridica) {
	double c = 0;
	for (Llamada l: this.llamadas) {
		double auxc = 0;
		if (l.getTipoDeLlamada() == "nacional") {
			// el precio es de 3 pesos por segundo más IVA sin adicional por establecer la llamada
			auxc += l.getDuracion() * 3 + (l.getDuracion() * 3 * 0.21);
		} else if (l.getTipoDeLlamada() == "internacional") {
			// el precio es de 150 pesos por segundo más IVA más 50 pesos por establecer la llamada
			auxc += l.getDuracion() * 150 + (l.getDuracion() * 150 * 0.21) + 50;
		}
		  
		if (this.tipo == "fisica") {
			auxc -= auxc*descuentoFisica;
		} else if(this.tipo == "juridica") {
			auxc -= auxc*descuentoJuridica;
		}
	}
	return c;
}
```

También puedo mover las constantes descuentoJuridica y descuentoFisica de la clase Empresa a la clase Cliente, ya que no tiene sentido que estén en Empresa si solo el cliente las utiliza. Para ello utilizo un refactoring Move Field. Además así ya no debería pasarse por parámetro a calcularMontoTotalLlamadas del Cliente, por ende aplico un refactoring Change Method Signature

---

**Paso 7:**

Identifico otro feature envy luego del paso anterior, esta vez tiene que ver con el cómo se calcula el precio de la llamada dependiendo de si es nacional o internacional... esto debería hacerlo la llamada, no el cliente. Aplico un extract method, sacando a un método "calcularPrecio" a Cliente, y luego moviendolo a Llamada mediante un Move Method:

```java

// En cliente:
public double calcularMontoTotalLlamadas() {
	double c = 0;
	for (Llamada l: this.llamadas) {
		double auxc = l.calcularPrecio();
		  
		if (this.tipo == "fisica") {
			auxc -= auxc*descuentoFisica;
		} else if(this.tipo == "juridica") {
			auxc -= auxc*descuentoJuridica;
		}
	}
	return c;
}

// En llamada
public double calcularPrecio() {
		int auxc = 0;
		if (this.tipoDeLlamada == "nacional") {
			// el precio es de 3 pesos por segundo más IVA sin adicional por establecer la llamada
			auxc += this.duracion * 3 + (this.duracion * 3 * 0.21);
		} else if (this.tipoDeLlamada == "internacional") {
			// el precio es de 150 pesos por segundo más IVA más 50 pesos por establecer la llamada
			auxc += this.duracion * 150 + (this.duracion * 150 * 0.21) + 50;
		}
		z
		return auxc;
}

```

Aplico un refactoring replace temp with query para solucionar el bad smell temporary variable de calcularPrecio en Llamada:

```java
// En llamada
public double calcularPrecio() {
		if (this.tipoDeLlamada == "nacional") {
			// el precio es de 3 pesos por segundo más IVA sin adicional por establecer la llamada
			return this.duracion * 3 + (this.duracion * 3 * 0.21);
		} else if (this.tipoDeLlamada == "internacional") {
			// el precio es de 150 pesos por segundo más IVA más 50 pesos por establecer la llamada
			return this.duracion * 150 + (this.duracion * 150 * 0.21) + 50;
		}
		
		return 0;
}

```

---

**Paso 8**

En la clase Cliente ahora identifico los bad smells: Primitive Obsession (tiene una variable "tipo", que representa al tipo)... esto puede generar if statements, que de hecho también existe en el método calcularMontoTotalLlamadas, solo que por el momento hay 2 ifs, pero podría haber mas si esto escala.

```java
// En Empresa
public Cliente registrarUsuario(String data, String nombre, String tipo) {
	Cliente var = this.crearCliente(nombre, tipo);
	if (tipo.equals("fisica")) {
		var.setDNI(data);
	}
		else if (tipo.equals("juridica")) {
		var.setCuit(data);
	}
	clientes.add(var);
	return var;
}

// En cliente
public double calcularMontoTotalLlamadas() {
	double c = 0;
	for (Llamada l : this.llamadas) {
		double auxc = l.calcularPrecio();
		if (this.tipo == "fisica") {
			auxc -= auxc*descuentoFisica;
		} else if(this.tipo == "juridica") {
			auxc -= auxc*descuentoJuridica;
		}
		c += auxc;
	}
	return c;
}
```

Para solucionar esto puedo aplicar el refactoring "Replace Conditional with Polymorphism", donde debería crear dos subclases que extiendan de Cliente: ClienteFisica y ClienteJuridica. La clase Cliente definiría un método abstracto para obtener el descuento de forma polimórfica dependiendo de cuál sea la instancia a la que se envíe el mensaje (sea ClienteJuridica o ClienteFisica). Además, la clase Cliente debería tener un constructor que defina los atributos en común de las clases ClienteFisica y ClienteJurídica, y las subclases tendrán atributos propios que diferencien a una de la otra (Cuit y DNI). La variable "Tipo" ya no va a existir ya que se resolverá polimórficamente. También aplico un Move Field de los valores de las constantes de descuentos correspondientes a cada una de las subclases según corresponda.
También debería acomodar el método registrarUsuario de la clase Empresa, para instanciar un Cliente u otro dependiendo de qué tipo sea:

```java
// En Empresa

// Este método crearCliente ya NO es necesario, así que tengo que eliminarlo.
private Cliente crearCliente(String nombre, String tipo) {
	Cliente var = new Cliente();
	var.setNombre(nombre);
	var.setTipo(tipo);
	var.setNumeroTelefono(this.obtenerNumeroLibre());
	return var;
}

public Cliente registrarUsuario(String data, String nombre, String tipo) {
	Cliente var;
	if (tipo.equals("fisica")) {
		var = new ClienteFisica(data, nombre, this.obtenerNumeroLibre());
	}
	else if (tipo.equals("juridica")) {
		var = new ClienteFisica(data, nombre, this.obtenerNumeroLibre());
	}
	clientes.add(var);
	return var;
}

// En ClienteJuridica
public ClienteJuridica {
	private String cuit;
	private static double descuentoJuridica = 0.15;
	
	public ClienteJuridica(String cuit, String nombre, String numeroTelefono) {
		super(nombre, numeroTelefono);
		this.cuit = cuit;
	}
	
	public double getDescuento() {
		return this.descuentoJuridica;
	}
}

// En ClienteFisica
public ClienteFisica {
	private String dni;
	private static double descuentoFisica = 0;

	private ClienteFisica(String cuit, String nombre, String numeroTelefono) {
		super(nombre, numeroTelefono);
		this.dni = dni;
	}
	
	public double getDescuento() {
		return this.descuentoFisica;
	}
}

// En Cliente
public class Cliente {
	private List<Llamada> llamadas = new ArrayList<Llamada>();
	private String nombre;
	private String numeroTelefono;
	
	public Cliente(String nombre, String numeroTelefono) {
		this.nombre = nombre;
		this.numeroTelefono = numeroTelefono;
	}

	public String getTipo() {
		return tipo;
	}
	public void setTipo(String tipo) {
		this.tipo = tipo;
	}
	public String getNombre() {
		return nombre;
	}
	public void setNombre(String nombre) {
		this.nombre = nombre;
	}
	public String getNumeroTelefono() {
		return numeroTelefono;
	}
	public void setNumeroTelefono(String numeroTelefono) {
		this.numeroTelefono = numeroTelefono;
	}
	public String getCuit() {
		return cuit;
	}
	public void setCuit(String cuit) {
		this.cuit = cuit;
	}
	public String getDNI() {
		return dni;
	}
	public void setDNI(String dni) {
		this.dni = dni;
	}
	
	public List<Llamada> getLlamadas() {
		return this.llamadas;
	}
	
	public void agregarLlamada(Llamada llamada) {
		this.llamadas.add(llamada);
	}
	
	public double calcularMontoTotalLlamadas() {
		double c = 0;
		for (Llamada l : this.llamadas) {
			double auxc = l.calcularPrecio();
			auxc -= auxc * this.getDescuento;
			c += auxc;
		}
		return c;
	}
	
	public abstract double getDescuento();
}
```

Al hacer esto, veo que tengo el bad smell dead code en algunos métodos como setTipo o getTipo... así que los elimino, aplicando remove method.. También muevo los getters y setters correspondientes a las subclases, para que el código quede bien estructurado, aplicando move method.

```java
// En ClienteJuridica
public ClienteJuridica extends Cliente {
	private String cuit;
	private static double descuentoJuridica = 0.15;
	
	public ClienteJuridica(String cuit, String nombre, String numeroTelefono) {
		super(nombre, numeroTelefono);
		this.cuit = cuit;
	}
	
	public double getDescuento() {
		return this.descuentoJuridica;
	}
	
	public String getCuit() {
		return cuit;
	}
	public void setCuit(String cuit) {
		this.cuit = cuit;
	}
}

// En ClienteFisica
public ClienteFisica extends Cliente {
	private String dni;
	private static double descuentoFisica = 0;

	private String ClienteFisica(String cuit, String nombre, String numeroTelefono) {
		super(nombre, numeroTelefono);
		this.dni = dni;
	}
	
	public double getDescuento() {
		return this.descuentoFisica;
	}
	
	public String getDNI() {
		return dni;
	}
	public void setDNI(String dni) {
		this.dni = dni;
	}
}

// En Cliente
abstract class Cliente {
	private List<Llamada> llamadas = new ArrayList<Llamada>();
	private String nombre;
	private String numeroTelefono;
	
	public Cliente(String nombre, String numeroTelefono) {
		this.nombre = nombre;
		this.numeroTelefono = numeroTelefono;
	}
	
	public String getNombre() {
		return nombre;
	}
	public void setNombre(String nombre) {
		this.nombre = nombre;
	}
	public String getNumeroTelefono() {
		return numeroTelefono;
	}
	public void setNumeroTelefono(String numeroTelefono) {
		this.numeroTelefono = numeroTelefono;
	}
	
	public List<Llamada> getLlamadas() {
		return this.llamadas;
	}
	
	public void agregarLlamada(Llamada llamada) {
		this.llamadas.add(llamada);
	}
	
	public double calcularMontoTotalLlamadas() {
		double c = 0;
		for (Llamada l : this.llamadas) {
			double auxc = l.calcularPrecio();
			auxc -= auxc * this.getDescuento;
			c += auxc;
		}
		return c;
	}
	
	public abstract double getDescuento();
}
```

Luego aplico un refactoring Replace loop with Pipeline para solucionar el bad smell "Imperative Loops" del método calcularMontoTotalLlamadas, en Cliente.

```java
	// En cliente
	public double calcularMontoTotalLlamadas() {
		double c = this.llamadas.stream()
					.mapToDouble(l -> l.calcularPrecio() - (l.calcularPrecio() * this.getDescuento()))
					.sum();
		return c;
	}
```

Por último, puedo aplicar un Inline Temp para solucionar el bad smell Temporary Variable:

```java
	// En cliente
	public double calcularMontoTotalLlamadas() {
		return this.llamadas.stream()
					.mapToDouble(l -> l.calcularPrecio() - (l.calcularPrecio() * this.getDescuento()))
					.sum();;
	}
```
---

**Paso 9:**

Bad smell Primitive Obsession en la clase Llamada, en el método calcularPrecio. Esto a futuro puede ocasionar un bad smell Switch Statement.

```java
// En Empresa:
public Llamada registrarLlamada(Cliente origen, Cliente destino, String t, int duracion) {
	Llamada llamada = new Llamada(t, origen.getNumeroTelefono(), destino.getNumeroTelefono(), duracion);
	llamadas.add(llamada);
	origen.agregarLlamada(llamada);
	return llamada;
}

// En Llamada:
public class Llamada {
	
	private String tipoDeLlamada;
	private String origen;
	private String destino;
	private int duracion;

	public Llamada(String tipoLlamada, String origen, String destino, int duracion) {
		this.tipoDeLlamada = tipoLlamada;
		this.origen= origen;
		this.destino= destino;
		this.duracion = duracion;
	}

	public String getTipoDeLlamada() {
		return tipoDeLlamada;
	}

	public String getRemitente() {
		return destino;
	}
	
	public int getDuracion() {
		return this.duracion;
	}
	
	public String getOrigen() {
		return origen;
	}
	
	public double calcularPrecio() {
		if (this.tipoDeLlamada == "nacional") {
			// el precio es de 3 pesos por segundo más IVA sin adicional por establecer la llamada
			return this.duracion * 3 + (this.duracion * 3 * 0.21);
		} else if (this.tipoDeLlamada == "internacional") {
			// el precio es de 150 pesos por segundo más IVA más 50 pesos por establecer la llamada
			return this.duracion * 150 + (this.duracion * 150 * 0.21) + 50;
		}
		return 0;
	}

}
```

Para solucionarlo, aplico lo mismo que en el paso anterior: El refactoring Replace Conditional with Polymorphism junto con un inline temp para devolver todo en un return de forma limpia y legible. 
Para ello, hago que la clase Llamada sea abstracta, y crear dos subclases de la misma: LlamadaNacional y LlamadaInternacional. La clase Llamada definirá un método abstracto, "calcularPrecio", el cual será implementado por las dos subclases para poder resolver esta tarea de forma polimórfica. El método calcularPrecio de Llamada no tiene sentido tenerlo, ya que delegará la tarea a cada subclase
También las subclases tendrán su propio constructor, pasando todos los datos a "Llamada" con super().
A su vez, también tengo que modificar el método registrarLlamada de Empresa, para evaluar qué tipo se utiliza y en base a eso saber qué tipo de llamada instanciar.

```java
// En Empresa:
public Llamada registrarLlamada(Cliente origen, Cliente destino, String t, int duracion) {
	Llamada llamada = null;
	if (t.equals("nacional")) {
		llamada = new LlamadaNacional(origen.getNumeroTelefono(), destino.getNumeroTelefono(), duracion)
	}
	else if (t.equals("internacional")) {
		llamada = new LlamadaInternacional(origen.getNumeroTelefono(), destino.getNumeroTelefono(), duracion)
	}
	origen.agregarLlamada(llamada);
	return llamada;
}

// En Llamada:
abstract class Llamada {
	private String origen;
	private String destino;
	private int duracion;

	public Llamada(String origen, String destino, int duracion) {
		this.origen= origen;
		this.destino= destino;
		this.duracion = duracion;
	}

	public String getRemitente() {
		return destino;
	}
	
	public int getDuracion() {
		return this.duracion;
	}
	
	public String getOrigen() {
		return origen;
	}
	
	public abstract double calcularPrecio();
}

public class LlamadaInternacional extends Llamada {
	public LlamadaInternacional(String origen, String destino, int duracion) {
		super(origen, destino, duracion)
	}
	
	public double calcularPrecio() {
		return this.getDuracion() * 3 + (this.duracion * 3 * 0.21);
	}
}

public class LlamadaNacional extends Llamada {
	public LlamadaInternacional(String origen, String destino, int duracion) {
		super(origen, destino, duracion)
	}
	
	public double calcularPrecio() {
		return this.duracion * 150 + (this.duracion * 150 * 0.21) + 50;
	}
}
```

**Paso 10:**

En la clase GestorNumerosDisponibles identifico los bad smells "Primitive obsession" y "Switch Statements".
Para solucionar el bad smell Switch Statements aplico el refactoring "Replace Conditional with Strategy", y a su vez, de la mano solucionaría el bad smell "Primitive Obsession" modificando el tipo de dato de la variable de instancia "tipoGenerador" por la estrategia abstracta o interfaz.

```java
public class GestorNumerosDisponibles {
	private SortedSet<String> lineas = new TreeSet<String>();
	private String tipoGenerador = "ultimo";

	public SortedSet<String> getLineas() {
		return lineas;
	}

	public String obtenerNumeroLibre() {
		String linea;
		switch (tipoGenerador) {
			case "ultimo":
				linea = lineas.last();
				lineas.remove(linea);
				return linea;
			case "primero":
				linea = lineas.first();
				lineas.remove(linea);
				return linea;
			case "random":
				linea = new ArrayList<String>(lineas)
						.get(new Random().nextInt(lineas.size()));
				lineas.remove(linea);
				return linea;
		}
		return null;
	}

	public void cambiarTipoGenerador(String valor) {
		this.tipoGenerador = valor;
	}
	
	public boolean contiene(String str) {
		return this.getLineas().contains(str);
	}
	
	public void agregar(String str) {
		this.lineas.add(str);
	}
}
```

Primero aplico el refactoring Replace Conditional with Strategy, para esto hago lo siguiente:
- Creo una nueva clase abstracta "Linea" y 3 subclases que extenderán a esta misma: "UltimaLinea", "PrimerLinea" y "LineaRandom".
- Delego la lógica del método obtenerNumeroLibre de GestorNumerosDisponibles a la clase "Linea", la cuál ahora pasará a tener esta misma firma de método pero como abstracto para que sus subclases lo implementen, y hacer un hook o gancho... 
- Aprovecho para solucionar el bad smell Primitive Obsession, cambiando el tipo de dato de tipoGenerador de GestorNumerosDisponibles por "Linea", así también como su asignación, que ahora debería ser un objeto "UltimaLinea".

```java
public class UltimaLinea extends Linea { // Esta clase sería el rol "ConcreteStrategy" en el patrón Strategy
	public String obtenerNumeroLibre(SortedSet<String> lineas) {
		String linea;
		linea = lineas.last();
		lineas.remove(linea);
		return linea;
		}
	}

public class PrimerLinea extends Linea { // Esta clase sería el rol "ConcreteStrategy" en el patrón Strategy
	public String obtenerNumeroLibre(SortedSet<String> lineas) {
		String linea;
		linea = lineas.first();
		lineas.remove(linea);
		return linea;
	}
}

public class LineaRandom extends Linea { // Esta clase sería el rol "ConcreteStrategy" en el patrón Strategy
	public String obtenerNumeroLibre(SortedSet<String> lineas) {
		String linea;
		linea = new ArrayList<String>(lineas)
		.get(new Random().nextInt(lineas.size()));
		lineas.remove(linea);
		return linea;
	}
}

abstract class Linea {
	public abstract String obtenerNumeroLibre(SortedSet<String> lineas);
}

public class GestorNumerosDisponibles { // Esta clase sería el rol "Context" en el patrón Strategy.
	private SortedSet<String> lineas = new TreeSet<String>();
	private Linea tipoGenerador = new UltimaLinea();

	public SortedSet<String> getLineas() {
		return this.lineas;
	}

  

	public String obtenerNumeroLibre() {
		return this.tipoGenerador.obtenerNumeroLibre(lineas);
	}

  
	public void cambiarTipoGenerador(String tipoGenerador) {
		switch (tipoGenerador) {
			case "ultimo":
				this.tipoGenerador = new UltimaLinea();
			case "primero":
				this.tipoGenerador = new PrimerLinea();
			case "random":
				this.tipoGenerador = new LineaRandom();
		}
	}
	
	public void agregar(String str) {
		this.lineas.add(str);
	}
	
	public boolean contiene(String str) {
		return this.getLineas().contains(str);
		}
	}
```

*COMO OBSERVACIÓN*: Los tests fallan si cambio el tipo de parámetro de cambiarTipoGenerador por otro, como Linea en este caso para cambiar la estrategia...
Para que los tests no se rompan, opté por dejar el bad smell switch statement pero en esta clase para saber qué setear como estrategia.