
**10 de refactoring:**

Cuando hay un bad smell de switch statement y hay un setter, existen indicios de que el polimorfismo no alcanza y que hay que usar un Strategy o un State.

### Refactoring

**Ejercicio 7:**  

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

**Ejercicio 9:**

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

Luego de hacer esto, me doy cuenta que puedo volver a hacer otro extract method pero esta vez en calcularDescuentoPorAntiguedad()... así también como otro replace temp with query, eliminadno la variable correspondiente a la fecha¿esto está bien hacerlo 2 veces seguidas, o está mal?

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

		private double calcularDescuentoPorAntiguedad(
			double costoProductos,
			double extraFormaPago
		){
			int añosDesdeFechaAlta = this.cliente.añosDesdeFechaAlta();
		    if (this.mayorQueCinco(años)) {  
		      return (costoProductos + extraFormaPago) * 0.9;  
		    }  
		    return costoProductos + extraFormaPago;  
		}
		
		private double calcularTotal() {
		
		}
		
		private boolean mayorQueCinco(int num) {
			return num > 5;
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