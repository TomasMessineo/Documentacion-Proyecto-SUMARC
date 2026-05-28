- Que la HU de iniciar sesión diga: "redirigir a mis clases". 
- Falta poner ejemplos en la HU de iniciar sesión. No entendí acá a qué se refererían... pero lo escuché y lo anoto. Entiendo que es actualizar los datos ingresados de la HU a los ejemplos que hardcodeamos en la BD.
- Tener otra compu con el Taiga abierto.
- Anotar el orden en el que vamos a mostrar en la DEMO. Que no se turnen uno a uno, sino que una parte cada uno. Por ejemplo: Iniciar sesión, ver mis clases, anotarme, etc. Cuando llegue el turno de pagar, si Seba por ejemplo tiene que pagar, por un momento se puede desviar ese "bloque" para que Seba explique el pago y luego vuelva el flujo a Massi.
- Revisar escenario 5 de pago con tarjeta: Falta decir que la tarjeta hace algo, no sé... era este escenario pero no escuché bien qué. Cambiar también el escenario de pago por tarjeta vencida diciendo "Pago fallido por tarjeta vencida". El error está mal expresado también en el error que muestra el frontend. Revisar el dado de todos los escenarios de pagar con tarjeta
- NO mostrar la inscripción a clase mensual... ponerla al final y decir que tiene los mismos escenarios que la inscripción a clase individual. Decirle al JTP que es lo mismo pero si quiere se la mostramos.
- Dado que el alumno con DNI x ya tiene reservada una clase para tal día y tal horario, cuando el alumno presiona "inscribirse" en una clase distinta... entonces... y así. Esto cambiarlo en la inscripción a clase 
- Agregar un Hola, "nombre", "rol" para cada uno de los roles. Para que la JTP vea mejor todo.

Crear clase:

- Al dado del escenario fallido por cupo excedido habría que modificarlo.  Dado quew para el martes a las trece el cupo total de todas las clases registradas es 3 y que la clase funcional con cupo 15 supere el máximo... (algo así escuché decir a tadeo). 
- Evaluar poner cupo negativo para el crear clase. Hacer un escenario nuevo. El cupo no debe ser negativo.
- Al crear una clase, para todo el mes deben crearse también. Revisar que las clases creadas se repitan todas las semanas. Tienen un período de 2 meses.
- 