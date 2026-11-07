Receta: Ticket de compra

Receta del programa principal (main)

1. MOSTRAR "=== SISTEMA DE VENTAS MECATRONICA ==="
2. SOLICITAR el nombre del producto y guardarlo en nombre.
3. SOLICITAR el precio unitario y guardarlo en precio.
4. MIENTRAS precio sea menor o igual a 0:
      MOSTRAR mensaje de error.
      VOLVER A SOLICITAR el precio.
5. SOLICITAR la cantidad de piezas y guardarla en cantidad.
6. MIENTRAS cantidad sea menor o igual a 0:
      MOSTRAR mensaje de error.
      VOLVER A SOLICITAR la cantidad.
7. SOLICITAR el porcentaje de descuento y guardarlo en descuento.
8. MIENTRAS descuento sea menor que 0 o mayor que 99:
      MOSTRAR mensaje de error.
      VOLVER A SOLICITAR el descuento.
9. CALCULAR subtotal utilizando precio y cantidad.
10. CALCULAR montoDescuento utilizando subtotal y descuento.
11. CALCULAR baseImponible restando el descuento al subtotal.
12. CALCULAR iva utilizando baseImponible y la tasa del 16%.
13. CALCULAR total sumando baseImponible e iva.
14. LLAMAR al módulo imprimirTicket enviando:
      nombre, cantidad, precio, subtotal,
      montoDescuento, iva y total.
15. FINALIZAR el programa.

Recetas de los módulos

calcularIVA

MODULO calcularIVA(base, tasa)
1. RECIBIR la base imponible y la tasa del IVA.
2. MULTIPLICAR la base por la tasa.
3. DIVIDIR el resultado entre 100.
4. GUARDAR el resultado como IVA.
5. DEVOLVER el IVA.
FIN MODULO

imprimirTicket

MODULO imprimirTicket(nombre, cantidad, precio,
                      subtotal, descuentoMonto, iva, total)
1. RECIBIR los datos de la compra.
2. MOSTRAR el título "TICKET DE VENTA MECATRÓNICA".
3. MOSTRAR el nombre del producto.
4. MOSTRAR el precio unitario.
5. MOSTRAR la cantidad de piezas.
6. MOSTRAR el subtotal.
7. MOSTRAR el descuento aplicado.
8. MOSTRAR el IVA.
9. MOSTRAR una línea de separación.
10. MOSTRAR el total a pagar.
11. MOSTRAR "Gracias por su compra :)".
FIN MODULO

calcularPorcentaje (Fase 4)

MODULO calcularPorcentaje(cantidad, porcentaje)
1. RECIBIR una cantidad y un porcentaje.
2. MULTIPLICAR la cantidad por el porcentaje.
3. DIVIDIR el resultado entre 100.
4. GUARDAR el resultado.
5. DEVOLVER el resultado.
FIN MODULO

Otros módulos que agregues

calcularSubtotal

MODULO calcularSubtotal(precio, cantidad)
1. RECIBIR el precio y la cantidad.
2. MULTIPLICAR el precio por la cantidad.
3. GUARDAR el resultado como subtotal.
4. DEVOLVER el subtotal.
FIN MODULO

calcularDescuento

MODULO calcularDescuento(subtotal, porcentaje)
1. RECIBIR el subtotal y el porcentaje de descuento.
2. MULTIPLICAR el subtotal por el porcentaje.
3. DIVIDIR el resultado entre 100.
4. GUARDAR el resultado como monto del descuento.
5. DEVOLVER el monto del descuento.
FIN MODULO

imprimirTicketImpl

MODULO imprimirTicketImpl(nombre, cantidad, precio,
                           subtotal, descuentoMonto, iva, total)
1. RECIBIR todos los datos de la compra.
2. MOSTRAR el título del ticket.
3. MOSTRAR los datos del producto.
4. MOSTRAR los importes calculados.
5. MOSTRAR el total de la compra.
6. MOSTRAR el mensaje de agradecimiento.
FIN MODULO