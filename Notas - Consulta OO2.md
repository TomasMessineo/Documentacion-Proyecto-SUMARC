
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
Prosiguiendo con el punto 4, para solucionar el bad smell "long method" (que en realidad es el bad smell principal de este método getCostoTotal) aplico un extract method en las líneas 28 a 33 creando un método privado "calcularCostoExtra()" el cual recibe 2 parámetros, y luego un replace temp with query para reemplazar la variable temporal utilizada, llevando todo al return directamente.

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

**Paso 2:**
Bad smell Uncommunicative Name en las líneas 11 y 12 de "Empresa". El nombre de las constantes no es claro.
Para corregirlo aplico el refactoring "Rename Variable"

**Paso 3:**
Duplicate Code en las líneas 32 a 45 de la clase "Empresa".
Para solucionar esto aplico move method extrayendo la lógica común de ambos ifs en un nuevo método "crearCliente()"