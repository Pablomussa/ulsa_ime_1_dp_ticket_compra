PRÁCTICA: TICKET DE COMPRA

1. Descripción del problema (Fase 1)

Mi programa sirve para generar un ticket de compra de una tienda. Permite ingresar el nombre del producto, su precio, la cantidad y el descuento. Después realiza los cálculos del subtotal, descuento, IVA y total para mostrar el resultado de la compra.

2. Entradas y salidas (Fase 1)

Entradas:

Entrada	Tipo de dato	Función de utilerias.h
Nombre del producto	string	leerCadena()
Precio unitario	double	leerDecimal()
Cantidad de piezas	int	leerEntero()
Descuento	double	leerDecimal()

Salida:

El ticket muestra el nombre del producto, precio unitario, cantidad, subtotal, descuento, IVA y total a pagar.

¿El IVA se calcula sobre el subtotal o sobre lo que queda después del descuento? ¿Por qué?

Se calcula sobre lo que queda después del descuento, porque primero se resta el descuento al subtotal y después se aplica el 16% de IVA sobre esa cantidad.

3. Restricciones e invariante (Fases 1 y 2)

Restricciones:

Dato	¿Qué valores son válidos?	¿Por qué?
Nombre del producto	Texto no vacío	Para identificar el producto.
Precio	Mayor que 0	No se pueden vender productos con precio negativo o cero.
Cantidad	Enteros mayores que 0	Debe existir al menos una pieza.
Descuento (%)	De 0 a 99	Para evitar descuentos negativos o mayores al límite establecido en el programa.

¿Qué hace mi programa si el usuario escribe un dato fuera de rango?

Muestra un mensaje de error y vuelve a solicitar el dato hasta que el usuario escriba uno válido.

¿Puede el total salir negativo? ¿Por qué?

No, porque el descuento está limitado y no puede superar el subtotal. Además, el IVA se suma a la cantidad restante.

Invariante 1:

Después del ciclo de validación, el precio siempre debe ser mayor que cero.

Invariante 2:

El subtotal menos el descuento es la base imponible. A esa cantidad se le calcula el IVA y finalmente se suma para obtener el total.

4. Casos resueltos a mano (Fase 1)

Caso	Nombre	Precio	Cantidad	Descuento (%)	Subtotal	Descuento ($)	IVA	Total
1 (sin descuento)	Mouse	100	1	0	100.00	0.00	16.00	116.00
2 (con descuento)	Cuaderno	50	2	10	100.00	10.00	14.40	104.40
3 (precio con centavos)	Pluma	19.99	1	0	19.99	0.00	3.20	23.19

5. Tipo de dato abstracto (Fase 1)

TDA	Datos (¿qué tiene?)	Operaciones (¿qué se puede hacer con él?)
Producto	nombre, precio, cantidad	Calcular su subtotal.
Ticket	subtotal, descuento, IVA, total	Calcular e imprimir los importes de la compra.

Jerarquías:

Sí, los dos son productos porque ambos se venden en una tienda. Tienen en común el nombre y el precio, pero cambia la forma de medir la cantidad: uno se vende por piezas y otro por peso.

6. Análisis descendente (Fase 2)

Generar ticket de compra
├── 1. Mostrar bienvenida
├── 2. Pedir los datos
│     ├── 2.1 Pedir el nombre del producto (ya existe)
│     ├── 2.2 Pedir el precio (y validar que sea mayor que 0)
│     ├── 2.3 Pedir la cantidad y validar que sea mayor que 0
│     └── 2.4 Pedir el descuento y validar que esté entre 0 y 99
├── 3. Calcular los importes
│     ├── 3.1 Calcular el subtotal
│     ├── 3.2 Calcular el monto del descuento
│     ├── 3.3 Calcular la base imponible y el IVA
│     └── 3.4 Calcular el total
└── 4. Imprimir el ticket (ya existe)

Análisis ascendente: ¿qué partes del árbol ya estaban resueltas por una función que existe? ¿Cuáles?

Las funciones de utilerías para leer cadenas, números enteros y decimales. También tengo las funciones calcularSubtotal, calcularDescuento, calcularIVA e imprimirTicket.

¿Alguna parte del árbol hacía más de una cosa? ¿Cómo la dividiste?

Sí, la parte de calcular los importes realiza varias operaciones. La dividí en subtotal, descuento, base imponible, IVA y total para que fuera más fácil entender cada cálculo.

7. Módulos y receta (Fase 2)

Módulo	¿Qué recibe?	¿Qué devuelve?	¿Función o procedimiento?
calcularSubtotal	precio, cantidad	El subtotal	Función
calcularDescuento	subtotal, porcentaje	Monto del descuento	Función
calcularIVA	base, tasa	Monto del IVA	Función
imprimirTicket	nombre, cantidad, precio, subtotal, descuento, IVA y total	No devuelve nada	Procedimiento
imprimirTicketImpl	Los mismos datos del ticket	No devuelve nada	Procedimiento

¿Probé mi receta a mano con mis 3 casos?

Sí.

¿Tuve que corregirla? ¿Qué cambié?

Sí, organicé mejor los cálculos para separar el subtotal, el descuento, la base imponible y el IVA.

8. Cómo compilar y ejecutar (Fase 3)

¿En qué sistema operativo trabajé?

Pendiente de confirmar.

9. Ejemplo de ejecución (Fase 3)

=== SISTEMA DE VENTAS MECATRONICA ===
Ingrese el nombre del producto: Cuaderno
Ingrese el precio unitario: 50
Ingrese la cantidad de piezas: 2
Ingrese el porcentaje de descuento (0-99): 10
 TICKET DE VENTA MECATRÓNICA
Producto: Cuaderno
Precio U: $50
Cantidad: 2
Subtotal: $100
Descuento: -$10
IVA: $14.4
------------------------
TOTAL:    $104.4
Gracias por su compra :)

10. De la receta al código (Fase 3)

Paso de la receta	Módulo o instrucción de C++ que lo implementa
1. Mensaje de bienvenida	std::cout
2. Pedir nombre del producto	leerCadena()
3. Pedir y validar precio	leerDecimal() y while
4. Pedir y validar cantidad	leerEntero() y while
5. Pedir y validar descuento	leerDecimal() y while
6. Calcular subtotal	precio * cantidad
7. Calcular descuento	subtotal * descuento / 100.0
8. Calcular IVA	baseImponible * 16.0 / 100.0
9. Calcular total	baseImponible + iva
10. Imprimir ticket	imprimirTicket()

¿Hubo algún paso de mi receta que me costó traducir a C++? ¿Cuál y por qué?

Sí, la validación de los datos, porque tuve que utilizar ciclos while para que el programa volviera a pedir la información cuando el usuario ingresara un dato incorrecto.

Formato del ticket: ¿qué ancho usé en std::setw y por qué? ¿Qué pasa si uso un número menor que el largo de la etiqueta más larga?

No aplica. En mi código actual no utilicé std::setw, por lo que todavía no tengo un ancho definido. Si el número es menor que el largo de la etiqueta, no se logra una alineación correcta.

¿Convertí el ancho de las líneas del ticket (36) en una constante? ¿Cómo la llamé?

No aplica. Todavía no utilicé una constante para el ancho de las líneas.

11. Experimentos y depuración (Fase 3)

Experimento A: depuración de calcularDescuento

Paso de depuración	Lo que hice o encontré
1. Reproduce: ¿con qué datos falló?	No tengo registrados los datos exactos de la prueba que provocó el error.
2. Aísla: ¿qué valor intermedio estaba mal?	No aplica, no tengo las salidas DEBUG.
3. Explica: ¿cuál era la causa?	No puedo confirmar la causa sin el código anterior que tenía el error.
4. Corrige: ¿qué cambiaste?	La fórmula correcta es subtotal por porcentaje dividido entre 100.
5. Limpia: ¿comentaste tus salidas DEBUG?	No aplica, no aparecen salidas DEBUG en el código compartido.

La prueba con 0 % pasó aunque la función tenía un error. ¿Qué me enseña eso sobre elegir mis casos de prueba?

Que no es suficiente probar solamente un caso sin descuento. También hay que probar diferentes porcentajes para comprobar que la función trabaje correctamente.

Experimento B: al cambiar el IVA a 8 %, ¿cuántas líneas tuve que cambiar? ¿Qué mejoraría?

En mi código actual tendría que cambiar una línea, donde se encuentra el 16%. Mejoraría el programa utilizando una constante para la tasa del IVA.

¿Mi ticket seguía diciendo IVA (16%)? ¿Qué hice al respecto?

No aplica, porque mi ticket solamente muestra la palabra IVA y no incluye el porcentaje.

Experimento C (opcional): al cambiar el parámetro dentro de calcularIVA, ¿cambió la variable de main()? ¿Por qué?

No aplica. No realicé este experimento. Sin embargo, al recibir parámetros por valor, los cambios dentro de la función no modifican la variable original de main().

12. La constante “Le atendio” (Fase 3)

¿Dónde definí la constante con mi nombre?

No aplica. En el código compartido todavía no está definida.

¿Por qué elegí esa opción?

No aplica.

¿Qué otras partes del programa podrían necesitar el nombre de quien atiende?

En el mensaje de bienvenida, en el ticket de devolución o en otros comprobantes de compra.

Si mañana atiende otra persona, ¿en cuántos lugares tengo que cambiar el nombre?

En mi código actual no aparece el nombre de quien atiende, por lo que todavía no se utiliza.

Si el nombre se leyera del teclado o de un archivo, ¿cuánto código tendría que cambiar con mi opción?

Solamente tendría que cambiar la parte donde se obtiene el nombre y guardar el nuevo dato en una variable.

13. Tabla de pruebas (Fase 4)

#	Caso	Esperado (subtotal / descuento / IVA / total)	Obtenido	¿Pasó?
1	Sin descuento	100.00 / 0.00 / 16.00 / 116.00	Pendiente	Pendiente
2	Con descuento	100.00 / 10.00 / 14.40 / 104.40	100.00 / 10.00 / 14.40 / 104.40	Sí, cálculo
3	Descuento de 15 %	600.00 / 90.00 / 81.60 / 591.60	Pendiente	Pendiente
4	Precio con centavos	19.99 / 0.00 / 3.20 / 23.19	Pendiente	Pendiente
5	Descuento total	90.00 / 90.00 / 0.00 / 0.00	No válido con la validación actual	No
6	Precio inválido	Vuelve a pedir el precio dos veces; 40.00 / 0.00 / 6.40 / 46.40	Pendiente	Pendiente
7	Cantidad inválida	Vuelve a pedir la cantidad dos veces; 20.00 / 0.00 / 3.20 / 23.20	Pendiente	Pendiente
8	Descuento inválido	Vuelve a pedir el descuento dos veces; 100.00 / 20.00 / 12.80 / 92.80	Pendiente	Pendiente
9	Texto en el precio	Vuelve a pedir el precio una vez; 100.00 / 0.00 / 16.00 / 116.00	Pendiente	Pendiente
10	Nombre con espacios	Muestra el nombre completo; 25.50 / 0.00 / 4.08 / 29.58	Pendiente	Pendiente
11	Nombre vacío	Vuelve a pedir el nombre una vez; 12.00 / 0.00 / 1.92 / 13.92	No valida nombre vacío	No
12	Caso propio 1: Compra sin descuento	200.00 / 0.00 / 32.00 / 232.00	Pendiente	Pendiente
13	Caso propio 2: Compra con descuento	300.00 / 30.00 / 43.20 / 313.20	Pendiente	Pendiente

En el caso 4 el IVA real es 3.1984. ¿Por qué mi ticket muestra 3.20?

Porque el resultado se redondea a dos decimales al momento de mostrarlo, ya que el dinero normalmente se representa con dos cifras decimales.

En el caso 10, ¿el ticket siguió alineado? Si no, ¿qué corregí?

No aplica. Mi código todavía no utiliza std::setw para alinear las columnas.

14. Generalización (Fase 4)

¿Qué cálculo hacen calcularDescuento y calcularIVA? ¿Qué cambia entre una y otra?

Las dos funciones calculan un porcentaje de una cantidad. La diferencia es que una calcula el descuento que se resta al subtotal y la otra calcula el IVA que se suma a la base imponible.

Receta de calcularPorcentaje:

1. Recibir una cantidad y un porcentaje.
2. Multiplicar la cantidad por el porcentaje.
3. Dividir el resultado entre 100.
4. Devolver el resultado.

¿Cómo quedaron el descuento y el IVA después del cambio?

No aplica todavía, porque en el código compartido no he implementado calcularPorcentaje.

¿Volví a correr toda la tabla de pruebas después del cambio? ¿Todo siguió pasando?

No aplica, porque todavía no realicé ese cambio.

¿Agregué calcularPorcentaje a mi tabla de módulos (sección 7)?

No.

¿En qué otro programa podría reutilizar calcularPorcentaje?

En un programa de nómina para calcular impuestos, comisiones o aumentos salariales.

15. Revisión de calidad (Fase 4)

Principio	Pregunta	¿Lo cumple?	Evidencia
Correcto	¿Pasa todas las pruebas de la tabla?	Parcialmente	Los cálculos principales están implementados.
Robusto	¿Resiste datos inválidos sin fallar ni terminar?	Parcialmente	Utiliza ciclos while para validar los datos numéricos.
Legible	¿Otra persona entiende tu código sin que se lo expliques?	Sí	Tiene comentarios que explican cada paso.
Modular	¿Cada función hace una sola cosa?	Sí, parcialmente	Existen funciones separadas para los cálculos y la impresión.
Sin números mágicos	¿Los valores fijos tienen nombre?	No	El 16% está escrito directamente en el cálculo.
Fácil de mantener	Si cambia el IVA o quien atiende, ¿cuántas líneas cambias?	Parcialmente	El IVA está escrito directamente y todavía no existe la constante del empleado.
Reutilizable	¿Alguna de tus funciones serviría en otro programa?	Sí	calcularSubtotal, calcularDescuento y calcularIVA.

16. Reto obligatorio (Fase 4)

¿Qué reto elegí?

No puedo confirmar el número del reto porque no tengo la lista de retos de PRACTICA.md.

¿Por qué lo elegí?

No aplica.

¿Cómo lo resolví? ¿Qué módulos agregué o cambié?

No aplica.

¿Hice algún otro reto opcional? ¿Cuál?

No aplica.

17. Bitácora de mejoras (Fase 4)

#	¿Qué falló o qué quise mejorar?	¿Qué cambié?	¿Funcionó?
1	Quería evitar que se ingresaran precios negativos o iguales a cero.	Agregué un ciclo while para validar el precio.	Sí, según la lógica del código.
2	Quería evitar cantidades y descuentos fuera del rango permitido.	Agregué ciclos while para validar ambos datos.	Sí, según la lógica del código.

18. Dudas para el profesor (Fase 3)

Duda	Lo que ya intenté
¿Cómo puedo hacer que el ticket tenga una mejor alineación utilizando std::setw?	Actualmente utilizo std::cout directamente para imprimir cada dato.

19. Reflexión final

¿Qué aprendí con esta práctica?

Aprendí a realizar un programa que calcula los importes de una compra y valida los datos que ingresa el usuario. También aprendí a utilizar funciones para organizar mejor el código y hacerlo más fácil de entender.

Ahora que terminé, ¿qué cambiaría de mi proceso?

Primero organizaría mejor las funciones y probaría cada una por separado antes de juntarlas en el programa principal.

¿Qué fue lo más difícil y cómo lo resolví?

Lo más difícil fue realizar las validaciones y entender cómo organizar los cálculos. Lo resolví utilizando ciclos while y separando las operaciones.

¿Qué pregunta me quedó sin responder?

Me quedó la duda de cómo mejorar la presentación del ticket para que todos los datos queden alineados correctamente.

Comparado con las prácticas anteriores, donde todo estaba en main(), ¿dividir el programa en módulos me facilitó o me complicó el trabajo? ¿Por qué?

Me facilitó el trabajo porque pude separar cada operación y entender mejor qué hace cada función. Aunque al principio fue un poco más complicado organizar todo, después fue más sencillo encontrar y corregir errores.

¿Cómo encontré el error de calcularDescuento? ¿Lo habría encontrado si solo hubiera probado sin descuento?

La forma de encontrar un error en esa función es probar diferentes porcentajes y revisar los resultados intermedios. Si solamente hubiera probado con 0%, posiblemente no habría encontrado el error porque no se realiza ningún descuento.

20. Commits (Fase 5)

¿Cuántos commits hice durante la práctica?

Pendiente de revisar mi repositorio de GitHub.

Si hice menos de 3, ¿por qué?

No aplica hasta revisar el historial de commits.

21. Lista de verificación antes de entregar (Fase 5)

* [ ]	Llené las secciones 1 a 20.
* [ ]	Completé el árbol de análisis descendente y la tabla de módulos.
* [ ]	Escribí en RECETA.md la receta de main y la de cada módulo.
* [ ]	Cada bloque de main.cpp tiene su comentario // Paso N.
* [ ]	Corregí el error de calcularDescuento y documenté cómo lo encontré.
* [ ]	Hice los Experimentos A y B.
* [x]	Mi ticket muestra los datos de la compra.
* [ ]	Agregué la constante con mi nombre.
* [ ]	Escribí calcularPorcentaje y volví a correr las pruebas.
* [ ]	Hice al menos uno de los retos y lo documenté.
* [x]	No tengo salidas DEBUG activas en el código compartido.
* [ ]	Mi programa compila sin advertencias.
* [ ]	Probé todos los casos de la tabla.
* [ ]	Revisé los principios de calidad.
* [ ]	No modifiqué utilerias.h.
* [ ]	Tengo al menos 3 commits con mensajes claros.
* [ ]	Hice git push y verifiqué mi fork en GitHub.
* [ ]	Mi fork tiene el nombre solicitado y los archivos en las carpetas correspondientes.
* [ ]	Entregué el enlace de mi fork en Classroom.