# Vialix: dirección de arte

> Borrador. Se cerrará con los mockups.

## Estilo: LucasArts pintado

> Decidido en octubre de 2026 ([decisiones.md](decisiones.md)). Sustituye a la dirección «HD pixel art» del principio, que en el mockup quedaba demasiado estruendosa: todo con el mismo contraste y la misma saturación.

Referencia principal: *The Secret of Monkey Island* y *Monkey Island 2: LeChuck's Revenge* (y *Indiana Jones and the Fate of Atlantis*). Fondos pintados reducidos a una paleta corta, con tramado; personajes limpios que resaltan sobre ellos.

- **Una gama por escena.** Unos 32 a 48 colores, de la misma familia, con las sombras hacia el violeta y las luces hacia el ocre. Cada estación (ventanilla, taller, almacén, puerta) tiene su color dominante, y la hora del día lo desplaza.
- **Jerarquía de valores.** El fondo (la calle, las paredes) va suave, lejano y con poco contraste; los personajes y lo que se puede tocar llevan más contraste. Nada compite con el cliente.
- **Tramado en los degradados** (cielo, luz del farol, niebla) en vez de transiciones suaves.
- **Luz cálida en pocas ventanas**, no en todas.
- **Arquitectura ligeramente torcida**, sutil: fachadas que se inclinan un poco y tejados algo combados. No es el foco.
- **Pixel art a unos 180 px de ancho**, escalado a múltiplos enteros, como hasta ahora.
- **Colores de las esencias** reservados: ningún fondo usa sus tonos más saturados, para que una poción siempre se lea.
- **Prueba v0.9 (solo la calle de la ventanilla):** las piezas se pintan igual y al final se gradúan. Bajan la saturación y el contraste con la distancia, hacia un tono medio malva; las sombras van hacia el violeta azulado y las luces hacia el ocre; y todo se reduce a una paleta de 77 tonos (11 rampas de 7) con un tramado ordenado suave. La gente no se gradúa, para que resalte. Un botón «Estilo» en la ventanilla cambia entre este estilo y el anterior para comparar.
- **Pendiente de valorar más adelante:** reducir partículas y brillos, diálogo como texto de color sobre el personaje, interfaz de madera apagada y una sola fuente pixel. De momento la interfaz no cambia.

## Producción: el arte vive en el código

Como en AdventurersGuild: cada pieza es una rejilla de caracteres o un pincel que coloca píxeles (`src/art`). Se revisa en los diffs, se recolorea con la paleta y los tests comprueban que nada se sale de su rejilla. Si algún día hay PNG de Aseprite, se cargan igual.

- **Retratos con volúmenes:** cada personaje se pinta como volúmenes (cabeza, nariz, orejas, pelo, ropa, accesorios). El sombreado sale solo: un campo de distancias da relieve a cada volumen, la luz viene de arriba a la izquierda, las rampas de color van de un violeta oscuro a un blanco cálido y hay tramado ordenado en las transiciones. Donde un volumen tapa a otro aparece una línea de contorno interior, y el contorno exterior usa el tono más oscuro de cada zona. Las narices y los pómulos no son piezas aparte: se esculpen como relieve dentro de la cabeza, con brillo en el puente, media luna de sombra y fosa nasal, sin contorno. El colorete es un tinte que sigue el sombreado. Ojos, cejas, bocas, arrugas y accesorios se dibujan a mano encima. Los retratos miden 100 × 116 px.
- **Clientes por piezas:** cuerpo, cabeza, rasgos, pelo, sombrero, accesorio y paleta. La semilla del cliente decide la combinación: cada procedural tiene cara propia y los recurrentes tienen piezas exclusivas.
- **Ingredientes** a 16 × 16, con su tarro.
- **Frascos** con forma según el efecto y líquido del color de la mezcla.

## Efectos

- **Líquido del caldero:** shader de píxeles cuantizado a 5 tonos con remolinos, brillo, ondas, burbujas y espuma.
- **La calle en 3D:** pixel art pintado en reposo y reproyectado sobre un diorama (suelo en perspectiva, fachadas laterales, piezas a su distancia), al estilo de las calles de las aventuras gráficas pero con paralaje real al girar.
- **Gente de la calle (v0.12):** caricaturas al estilo de *Monkey Island*. Cada figura exagera algo: narigón, papada, chepa, cabezón, flaca como un palo o redonda como un tonel. La semilla combina silueta, nariz (gancho, patata, punta, respingona), barbilla, cejas (que dan la expresión), peinado, barba o bigote, sombrero y estampado (rayas, chaleco, fajín, mandil, remiendos). Hay tipos reconocibles: mercaderes, viejos con canas, nobles con capa y guardias. El sombreado es plano, de tres tonos con contorno oscuro y sin degradados, para que se lean por la silueta y el gesto. La ropa va algo apagada para no competir con las pociones. Miden de 16 a 70 píxeles. El paso tiene ocho fotogramas y uno quieto para la cola; el fotograma sale de la distancia recorrida, así que los pies no patinan, y caminan a casi media altura por segundo. El contorno es del color de cada pieza (más claro del lado de la luz) en vez de tinta negra; se puede comparar con el de tinta y con ninguno.
- **Partículas en GPU:** espíritus de esencia, vapor, chispas, humo, monedas, polvo.
- **Luz dinámica:** el caldero ilumina el taller con el color de la mezcla; las velas parpadean.
- **Cámara:** sacudida, destello y *hit-stop*.

## Sonido

Sintetizado con WebAudio, como en AdventurersGuild: burbujeo que cambia con la temperatura, salpicaduras, cristal, monedas, la campanilla de la ventanilla, la imprenta de la Gaceta, y una música de laúd y zanfona que cambia de la mañana a la ventanilla.
