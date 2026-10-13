# RecaModas · Reglas para la lista de producción de camisetas

Estas reglas definen cómo se reparten las camisetas sin estampar entre los diseños.
Cualquier chat nuevo debe leer este archivo antes de armar una lista.

## Datos de entrada

- Inventario actual por variante (diseño, color, talla), exportado de Loyverse o por API.
- Ventas de los últimos 30 días por variante.
- Historial de inventario (opcional): sirve para ver qué se produjo y qué se agotó.
- Lista de camisetas sin estampar disponibles: color, talla y cantidad.

## Reglas

### 1. Lo que se vende es el diseño-color, no la talla

- La demanda se mide por **diseño + color**: por ejemplo, CHCH en beis.
- Las ventas por talla no deciden la producción, porque una talla "vende menos" muchas veces solo porque no había stock.

### 2. Igualar las tallas

- Dentro de cada diseño-color, las tallas S, M y L deben tener cantidades **parecidas** disponibles.
- Al producir, se le da prioridad a la talla que tiene menos stock en ese diseño-color, aunque no sea la que más se vende.
- Ejemplo: si hay 10 CHCH beis M y solo 1 CHCH beis S, se producen primero S (y L si también está baja) hasta acercarlas a M.

### 3. Mínimo 4 unidades por diseño

- Cada diseño que entra en la lista lleva **4 o más unidades**.
- Hacer 1 unidad de 10 diseños distintos cuesta mucho más que hacer 4 unidades de 3 diseños.
- Si a un diseño le tocan menos de 4, esas camisetas se pasan a otro diseño que ya esté en la lista.

### 4. Diseños dormidos

- Los diseños dormidos son los que casi no se venden. Pero no se venden porque no se producen: es un ciclo.
- En cada producción se reserva una parte para **sobreproducir 1 o 2 diseños dormidos elegidos**. Ejemplo: la producción anterior llevó 10 Balenciaga y otro diseño dormido.
- Esto se hace **sin descuidar lo que realmente se necesita**: primero se cubre lo urgente y lo que sobra va a los dormidos.
- Los dormidos también respetan las reglas 2 (tallas parejas) y 3 (mínimo 4).

### 5. Combinaciones permitidas

- Solo se proponen diseño-color que ya han existido en la tienda (producidos, vendidos o en stock).
- "CTA VARIADOS" no se incluye, porque no es un diseño fijo.

## Cómo se arma la lista

1. **Demanda por diseño-color**: ventas de los últimos 30 días, proyectadas a ~4 semanas.
2. **Reserva para dormidos**: se aparta la parte acordada (ver pendientes).
3. **Reparto de lo urgente**: cada camiseta sin estampar va al diseño-color que se agota más pronto. Dentro de ese diseño-color, va a la talla con menos stock.
4. **Mínimo 4**: los diseños que quedaron con menos de 4 unidades se eliminan y sus camisetas se reasignan.
5. **Dormidos**: la reserva se reparte entre los dormidos elegidos, con tallas parejas.
6. **PDF**: un resumen por diseño, y luego una tabla de color × talla para cada diseño con casillas para marcar.

## Pendiente de confirmar

- [ ] ¿El mínimo de 4 es por **diseño** en total o por **diseño-color**?
- [ ] ¿Qué parte de cada producción va a los dormidos? (por ejemplo, un 10–15 % o unas 10 unidades por dormido)
- [ ] ¿Quién elige los dormidos: tú en cada producción, o yo te propongo según las ventas?
- [ ] ¿Las tallas deben quedar exactamente iguales, o M puede llevar un poco más?
