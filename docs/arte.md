# Vialix: dirección de arte

> Borrador. Se cerrará con los mockups.

## Estilo: «HD pixel art»

Sprites de baja resolución nítidos, con iluminación, brillos y partículas modernas por encima. Referencias: *Moonlighter*, *Eastward*, *Blasphemous*, *Hyper Light Drifter*.

- **Pixel art a 180 px de ancho**, escalado a múltiplos enteros. Contornos oscuros selectivos, sombras en bloques, 3–4 tonos por material.
- **Por encima, a resolución de pantalla:** brillo (*bloom*), halos de luz, partículas suaves y destellos. Los sprites siguen siendo píxel a píxel; la luz no.
- **Paleta propia,** distinta de la de AdventurersGuild: fondos de madera y piedra cálidos y oscuros, para que destaquen los colores de joya de las pociones. Punto de partida: *Resurrect 64* (Lospec), ajustada.
- **Colores de las esencias** reservados: ningún fondo usa sus tonos más saturados, para que una poción siempre se lea.

## Producción: el arte vive en el código

Como en AdventurersGuild: cada pieza es una rejilla de caracteres o un pincel que coloca píxeles (`src/art`). Se revisa en los diffs, se recolorea con la paleta y los tests comprueban que nada se sale de su rejilla. Si algún día hay PNG de Aseprite, se cargan igual.

- **Retratos con volúmenes:** cada personaje se pinta como volúmenes (cabeza, nariz, orejas, pelo, ropa, accesorios). El sombreado sale solo: un campo de distancias da relieve a cada volumen, la luz viene de arriba a la izquierda, las rampas de color van de un violeta oscuro a un blanco cálido y hay tramado ordenado en las transiciones. Donde un volumen tapa a otro aparece una línea de contorno interior, y el contorno exterior usa el tono más oscuro de cada zona. Ojos, cejas, bocas, arrugas y accesorios se dibujan a mano encima. Los retratos miden 100 × 116 px.
- **Clientes por piezas:** cuerpo, cabeza, rasgos, pelo, sombrero, accesorio y paleta. La semilla del cliente decide la combinación: cada procedural tiene cara propia y los recurrentes tienen piezas exclusivas.
- **Ingredientes** a 16 × 16, con su tarro.
- **Frascos** con forma según el efecto y líquido del color de la mezcla.

## Efectos

- **Líquido del caldero:** shader con mezcla de color, ondas, burbujas y espuma.
- **Partículas en GPU:** espíritus de esencia, vapor, chispas, humo, monedas, polvo.
- **Luz dinámica:** el caldero ilumina el taller con el color de la mezcla; las velas parpadean.
- **Cámara:** sacudida, destello y *hit-stop*.

## Sonido

Sintetizado con WebAudio, como en AdventurersGuild: burbujeo que cambia con la temperatura, salpicaduras, cristal, monedas, la campanilla de la ventanilla, la imprenta de la Gaceta, y una música de laúd y zanfona que cambia de la mañana a la ventanilla.
