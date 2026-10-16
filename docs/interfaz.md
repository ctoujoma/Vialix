# Vialix: interfaz

> Cómo se ve y se toca el juego. Diseño en [`diseno.md`](diseno.md).

## 1. Principios

1. **Cada estación tiene su pantalla.** La tienda es un espacio que la cámara recorre: la ventanilla, el taller y, más adelante, el mercado. Cada una ocupa la pantalla entera; nada de meterlo todo junto.
2. **La tienda es una habitación 3D.** La cámara está en el centro de un cubo y gira sobre sí misma: delante la **ventanilla**, a la derecha el **taller**, detrás el **almacén** y a la izquierda la **puerta al mercado**. Al girar se ven el suelo (tablones y una alfombra con el círculo alquímico) y el techo (vigas, lámpara de velas, hierbas colgadas y un cocodrilo disecado). La cámara tiene un campo de visión natural (64°) en una habitación cuadrada: cada pared es más ancha que la pantalla y continúa hasta su esquina (con un poste, decoración y penumbra), así que al girar se ve la esquina real y no una deformación de ojo de pez. Se gira deslizando el dedo (la cámara lo sigue y la vuelta es continua) o con las pestañas. El giro por defecto es el **cubo 3D** (la tienda como una caja que gira, vista desde fuera), elegido tras probar el mockup; el botón de cámara del HUD permite comparar con el giro desde dentro y con el barrido lateral.
3. **El fondo da vida al pueblo.** Por la ventanilla se ve la plaza: gente que pasa, palomas, la fuente, la torre del Gremio, la hora del día. Y en la gente que pasa se ven los efectos de lo que vendes.
4. **Vertical y con una mano.** Las acciones están en la mitad inferior, al alcance del pulgar.
5. **La escena es el tutorial.** Las probetas, el caldero y Gus explican el sistema con animaciones, sin muros de texto.
6. **Todo se lee sin color.** Cada esencia tiene color y símbolo.
7. **Todo el texto es traducible.** Nada de texto en imágenes; claves de idioma desde el primer día.
8. **Nada de texto pedante.** Lo que se ve no se explica (el color del caldero, los frascos de la vitrina). Las explicaciones de cómo se juega salen solo las primeras veces y luego desaparecen. Los avisos son cortos y de uno en uno. Antes de añadir un texto, pregunta si dice algo que la pantalla no muestre ya.

**Mockup jugable:** [`mockup/vialix.html`](mockup/vialix.html).

## 2. Las estaciones

El arte tiene **unos 180–215 px de ancho** y se escala siempre a múltiplos enteros, así que cada píxel queda nítido en cualquier móvil. La altura se adapta: en los móviles altos crecen el cielo y la pared, no la interfaz.

```
 ◀── deslizar ──▶          ◀── deslizar ──▶
┌──────────────┐   ┌──────────────┐   ┌──────────────┐
│  VENTANILLA  │   │    TALLER    │   │   MERCADO    │
│ plaza viva,  │   │ probetas,    │   │ (más         │
│ cliente,     │   │ caldero, Gus,│   │  adelante)   │
│ mostrador,   │   │ alambique,   │   │              │
│ vitrina,     │   │ estante de   │   │              │
│ sellos       │   │ ingredientes │   │              │
└──────────────┘   └──────────────┘   └──────────────┘
```

### 2.1 HUD superior (común)
Día y día de la semana · monedas · reputación en este pueblo · sonido. Más adelante, los días hasta el alquiler.
- **Esperar:** el reloj del día es un botón. Al tocarlo el tiempo corre diez veces más deprisa y el sol se cambia por ⏩. Se para solo cuando llega alguien a la cola o a la ventanilla, al abrir, o si hay algo que hacer antes (no deja saltarse el domingo del tutorial). Un cartel sobre la vitrina lo ofrece cuando no hay nada que hacer: «Esperar a la cola» antes de abrir y «Esperar al siguiente» con la tienda abierta y vacía.
- En pantallas estrechas el día va abreviado («Lun · 8:07»).

### 2.2 Ventanilla
```
┌──────────────────────────────────┐
│ Día 1 · Lunes      🪙 120  ★★★★☆  🔊 │ HUD
│ ┌──────────────────────────────┐ │
│ │ SRA. PELLEJO                 │ │ bocadillo (arriba, no tapa la plaza)
│ │ Algo para que mi suegra…     │ │
│ └──────────────────────────────┘ │
│ 📜  cielo, banderines, torre   🏮 │ edicto clavado · farol
│     casas, puestos, fuente       │
│     gente que pasa · la cola     │ plaza viva
│        ┌──────────┐              │
│        │ CLIENTE  │              │ cliente a medio cuerpo
│ 📕 ════╧══════════╧═══ 🪙  🔔 ═══ │ mostrador: libreta, monedas, campanilla
│   🧪  🧪  ·   ·   ·   ·          │ vitrina (6 huecos × 3 frascos)
│  [RECHAZAR] [APUNTAR] [SERVIR]   │ sellos de caucho
│  Ventanilla    Taller   Mercado  │ pestañas
└──────────────────────────────────┘
```
- **Profundidad real (diorama 3D):** la ventanilla es un portal. Detrás hay una calle de verdad: el suelo es un plano en perspectiva con su textura de adoquines, las fachadas de los lados se alejan hacia el punto de fuga y cada persona u objeto está a su distancia. Todo se pinta en pixel art «en reposo»; al girar, cada pieza se reproyecta desde el ojo de la cámara sobre el plano de la pared. Nada se sale del hueco de la ventana, así que el giro del cubo no invade las otras pantallas.
- **La calle:** al fondo, la Casa del Gremio (portalón, balcón, estandartes con el sello) y la torre con su reloj (hora real del día de juego) y un sello gigante que da un golpe cada hora; a los lados, casas con entramado, voladizos, tejas con musgo, ventanas emplomadas, contraventanas, jardineras, toldos y carteles colgantes; la fuente con la estatua en bronce del fundador sellando algo; puestos del mercado, farolas, ropa tendida, banderines, palomas que se espantan y un gato dormido en las cajas. La pared izquierda está a la sombra y proyecta su sombra sobre el suelo. Detrás, ciudad lejana con el palacio y montañas.
- **El clima** cambia cada día (sol, nublado, lluvia, tormenta, niebla, nieve) y la Gaceta lo anuncia. Lluvia: gotas a tres distancias, salpicaduras, charcos, suelo mojado, gotas que resbalan por el cristal y paraguas. Tormenta: rayos y truenos. Niebla: bancos que se arrastran y la calle se pierde al fondo. Nieve: copos, suelo blanco y nieve sobre tejados y cornisas. En el mockup se puede cambiar tocando el cielo.
- **La gente que pasa** va en tres carriles a distinta distancia (cruce cercano, calle mayor de callejón a callejón y el fondo), con su tamaño según la perspectiva. Algunos llevan efectos de pociones: uno flota, otro es un pato, otro mide un palmo. Los clientes a los que sirves salen a la calle **con el efecto puesto**, y al día siguiente aparecen los de terceros (la suegra eructando humo). Si Ignatius se duerme, queda roncando en la calle.
- **La cola** se ve por la ventana: figuritas esperando a la derecha.
- **El cliente** a medio cuerpo, con parpadeo y boca al hablar. Llega y se va deslizándose con pasos. Ignatius no cabe: asoma la cabeza, y su llegada hace temblar la pantalla.
- **El bocadillo** está arriba, con el texto letra a letra (un toque lo completa).
- **Mostrador:** libreta (abre los encargos), cuenco de monedas (crece con la caja), campanilla (llama al siguiente) y el edicto clavado en el marco (se abre al tocarlo).
- **Vitrina:** 6 huecos bajo el mostrador, y en cada hueco hasta 3 frascos iguales (18 en total). El de delante brilla con su color; los de detrás asoman en penumbra. Al servir sale el de delante. Los huecos vacíos se ven. Un cartel sobre ella dice qué hacer: «Vitrina vacía · prepara la poción en el Taller ▶» (se toca para ir), «Toca una poción o arrástrala hasta…» o «Pulsa SERVIR…».
- **Servir:** se arrastra el frasco hasta el cliente (se ilumina al pasar por encima), o se toca el frasco y luego el sello Servir. Desde el taller, si hay alguien esperando, la tarjeta de la poción ofrece **«Servir a…»**: la cámara gira sola y el frasco vuela al cliente.
- **Sellos de caucho:** Rechazar, Apuntar y Servir. Al pulsar, el sello golpea con salpicadura de tinta y sonido. Servir se ilumina cuando hay una poción elegida.
- **Penumbra interior** con la luz del farol, y un haz de sol que entra por la ventanilla con motas de polvo.

### 2.3 Taller (mockup v0.12)

```
┌──────────────────────────────────┐
│ HUD    🔔 Sra. Pellejo espera…   │ aviso si hay alguien en la ventanilla
│ ◯ ventana    [licencia]  Vitrina │
│        ┌ pizarra ──────┐         │ garabatos de Remedios; con el aerómetro,
│        │  (tiza)       │         │ 5 probetas con cifras
│        └───────────────┘         │
│        [Huele a Valor]           │ lectura a ojo (o predicción con aerómetro)
│ [⌛ 2 vueltas]                   │ reloj de arena
│          ╭──────────╮       🧌   │ caldero · Gus en su taburete
│   ⚗️     ╰──────────╯       🛢   │ alambique · barril
│              🔥🔥                │ fuego (más vivo mientras hierve)
│ [📖] [Agua][Aguardiente][Vino] [Embotellar]
│ ◂ tarros del estante ▸           │
│  Ventanilla    Taller   Mercado  │
└──────────────────────────────────┘
```
- **Base primero:** agua, aguardiente o vino. Se vierte al caldero y lo tiñe. Lo que hace cada una no se explica en pantalla: está en las notas de Remedios del libro («el agua da, el aguardiente quita, el vino cambia»).
- **Vaciar el caldero:** con ingredientes dentro, tocar dos veces la base vacía el caldero (el primer toque avisa). También se vacía al embotellar o al explotar.
- **Tratamientos:** al tocar un tarro aparece «¿cómo lo echas?» con cuatro opciones.
  - **Entero:** va directo al caldero.
  - **Troceado:** tres toques con el cuchillo.
  - **Molido:** frotar en círculos en el mortero.
  - **Tostado:** mantener pulsado sobre el fuego y soltar en la franja verde; si te pasas, se quema y la poción sale peor.
- **Fuego y reloj de arena** (botón a la izquierda del caldero, y el reloj dibujado sobre el hogar). Como en *Kingdom Come*, la gracia está en el momento justo:
  - «Al fuego» empieza a hervir y la arena corre. Cada 5 segundos se acaba, el reloj se gira solo y cuenta una vuelta.
  - Al acabar cada vuelta, lo entero y lo tostado sueltan un punto de cada esencia, y lo troceado suelta lo que le quedaba.
  - Cuando ya no queda nada por soltar, cada vuelta de más concentra la mezcla (+1 a todo) hasta el ¡bum!
  - «Retirar» lo saca del fuego. Si lo retiras justo cuando se acaba la arena, el botón dice «¡Justo!». Si lo retiras a media vuelta («A medias»), la poción pierde una estrella y no cuenta como receta seguida al pie de la letra.
- **Animaciones:** chorro de la jarra al verter la base. El ingrediente vuela al caldero según su estado: en pedazos, como polvo de su color o tostado con humo (negro si se quemó). Al caer, el molido levanta una nube y el troceado salpica en varios sitios.
- **Lectura a ojo:** el color del líquido es la esencia dominante, su viveza es la intensidad, y el color del vapor es la segunda esencia. No se describe con palabras: se mira. Gus comenta a qué huele al retirar el caldero, y si el efecto ya se conoce el panel dice «Huele a Valor».
- **Aerómetro:** es una compra opcional, no un paso obligado. Lo vende el vidriero ambulante del mercado (40 monedas). Sin él, en la pared hay una pizarra con garabatos de tiza; al comprarlo aparecen las probetas con cifras y la predicción completa.
- **Remover:** igual que antes, sube la calidad. Quemar un ingrediente la baja, y seguir una receta al pie de la letra la sube.
- **Lote:** cada preparación da 3 frascos.
  - La tarjeta dice el efecto, la fuerza (Leve, Normal, Fuerte), los frascos y el secundario, y ofrece guardarlos (los que quepan), servir uno al cliente que espera, probar uno en Gus o destilar el lote entero.
  - Si Gus prueba algo útil hecho sin receta, se apunta en tu recetario.
- **Recetario** en el libro (códice), como en *Kingdom Come*: un índice con las recetas de Remedios y las tuyas, y al tocar una se abre su hoja con los pasos numerados y dibujados (base, cada ingrediente con su tratamiento, las vueltas de reloj y el final). El libro solo tiene desplazamiento vertical; en pantallas anchas se abre a doble página.
- **Igual que antes:** la vista desde arriba del caldero con su shader, la explosión con hollín, Gus y el nicho en 3D.

### 2.4 Modo foco (contrarreloj)

Mientras el caldero está al fuego o se prepara un ingrediente, la pantalla se calla para que se pueda mirar la arena:
- Solo quedan el aviso del cliente (nombre y una barrita de paciencia, sin frases), una línea de lectura del caldero y el botón del reloj.
- Se ocultan el contador de la vitrina, el botón del aerómetro, la segunda línea de la lectura y los comentarios de Gus. Gus comenta el olor una vez, al retirar el caldero.
- Los avisos no urgentes esperan a que acabe el contrarreloj y salen de uno en uno. Los urgentes (en rojo) salen al momento.
- Las indicaciones del caldero («Elige la base», «Ponlo al fuego») solo salen hasta la primera poción.

## 3. Pantallas y paneles

| Pantalla | Tipo | Qué hay |
| --- | --- | --- |
| **Portada** | Pantalla | Logo animado, el caldero burbujeando, continuar o nueva partida |
| **Amanecer: La Gaceta** | Pantalla completa | Periódico que sale de la imprenta: titular con ilustración, breves, reseñas, clasificados y horóscopo. Se pasa con un toque |
| **Amanecer: Edicto** | Superposición | Pergamino que se despliega y sello de lacre que cae con polvo. Después se clava en la ventanilla |
| **Libreta de encargos** | Panel (libreta) | Encargos con retrato, la frase original del cliente, plazo, recompensa y notas. Los que vencen hoy, marcados |
| **Códice** | Panel (libro con pestañas) | Recetas (índice y una hoja por receta) · Efectos (la tabla de 5 × 3 con huecos) · Ingredientes con las notas de Remedios. Más adelante: Secundarios y Clientes (fichas y progreso de sus arcos) |
| **Documento** | Superposición | Receta, licencia o carta en grande, para leer y comparar |
| **Mercado** | Pantalla (escena) | Calle con puestos que se recorre deslizando. Cada mercader abre su género y su regateo. El callejón del turbio, solo algunos días |
| **Regateo** | Superposición | Minijuego de tira y afloja con la paciencia del mercader |
| **Cierre: libro de cuentas** | Pantalla | Ingresos, gastos, tasas, cambios de reputación por facción. Botón «Dormir» |
| **Mejoras** | Panel | Plano de la tienda con lo mejorable y su coste |
| **Mapa** (mid-game) | Pantalla | Pergamino con pueblos, rutas, reputación en cada uno y el caracol avanzando |
| **Ajustes** | Panel | Sonido, vibración, idioma, tamaño de texto, guardado |

## 4. Flujo de un día

```
Portada → [5:00 Gaceta → Edicto] → Taller ⇄ Mercado (lun-sáb; la tienda queda cerrada)
                                      │   reloj lento · desde las 8:00, aviso de cola
                               «Abrir», cuando quieras
                                      ▼
                         Ventanilla ⇄ Taller (reloj de juego; los clientes esperan)
                                      │
                               20:00, atardecer
                                      ▼
                   Cierre: libro de cuentas → «Dormir» → 5:00
```

- **Reloj visual:** en el HUD («Lunes · 8:07») y en la torre de la plaza, que marca la hora y estampa su sello cada hora. Se para mientras lees un papel (edicto, Gaceta, libro, cuentas).
- **Paciencia:** la gente de la cola se cansa a las dos horas y media de juego, y se va. En la ventanilla, una barra sobre el mostrador se vacía de verde a rojo (hora y media; una hora si es urgente). Si llega a cero, el cliente se va y deja una reseña de 1★ en la Gaceta.
- **Abierta y sin cliente:** el botón llama al siguiente («Llamar al siguiente · 2 en la cola») o, si no hay nadie, permite cerrar antes. A las 20:00 el Gremio manda cerrar; si hay un cliente, se cierra en cuanto se va.
- **Aviso de cola** antes de abrir: cuánta gente espera fuera.
- **Domingo:** sin abrir y sin mercado; solo taller. La partida empieza en domingo.
- **Esperar:** el botón del reloj (ver 2.1) adelanta las horas muertas.

### 4.1 El domingo del tutorial

- Gus se presenta primero («Soy Gus, el homúnculo de la casa…») y después propone preparar género antes de abrir.
- Guía dos pociones: Valor (agua y Guindilla de dragón entera, tres vueltas) y «Para que callen» (aguardiente y Susurro embotellado molido, una vuelta).
- **Si te sales del guion, Gus lo dice** con un aviso en rojo: base equivocada («Para esta receta va el agua…»), ingrediente equivocado o mal tratado. El aviso ofrece «Vaciar el caldero» para empezar otra vez. Si ya vas por delante, el tutorial te sigue.

## 5. Momentos de efecto visual («wow»)

| Momento | Qué se ve y se siente |
| --- | --- |
| Echar un ingrediente | Salpicadura, onda en el líquido; espíritus de color salen volando del caldero hacia su probeta |
| Cancelar opuestas | Las dos probetas se vacían a la vez con chispas y siseo |
| Remover bien | Remolino de runas brillantes en la superficie; vibración suave |
| Pasarse de dosis | El caldero tiembla, el líquido sube… y explota: destello, sacudida, parón de un instante (*hit-stop*) y hollín en la pantalla que se limpia con el dedo |
| Poción terminada | El frasco se eleva y brilla según su rareza; las legendarias, con columna de luz |
| Descubrir un efecto | El hueco del códice se rellena con un sello y fanfarria |
| Servir | El frasco vuela al mostrador; monedas que caen y rebotan |
| Cliente transformado | *¡Poof!* de humo de colores, el cliente cambia allí mismo |
| Gus prueba | Gus bebe, se tambalea y muestra el efecto (flota, se encoge, se vuelve pato) |
| Edicto | El pergamino se despliega y el sello cae con polvo |
| La Gaceta | La imprenta golpea y el papel sale con el titular |

**Luz:** el resplandor del caldero tiñe todo el taller con el color de la mezcla. De día entra luz por la ventanilla; al cerrar baja la persiana y quedan las velas.

## 6. Interacción

- **Arrastrar y soltar** como gesto principal, siempre con alternativa de **tocar y luego tocar el destino**.
- **Mantener pulsado** = información (fichas, esencias, documentos).
- **Gestos solo donde suman:** remover en círculo, tirar del cazo, limpiar el hollín.
- **Vibración** en momentos de peso (explosión, servir, descubrir), con interruptor en Ajustes.
- **Botón atrás de Android** cierra el panel abierto; en la tienda, abre el menú.
- **Objetivos táctiles** de al menos 44 px en pantalla, aunque el arte sea más pequeño.

## 7. Texto e idiomas

- Los textos largos (bocadillos, Gaceta, códice) van en **DOM** con una fuente legible; los números y etiquetas cortas, en fuente pixel. Ambas con soporte completo de acentos y ñ.
- Las **cifras** usan una fuente pixel aparte (los dígitos de VT323), porque en Pixelify Sans el 2, el 5 y el 8 se confundían.
- Textos en `src/i18n/es.json` desde el principio. Las plantillas de la Gaceta y de los clientes usan marcadores (`{cliente}`, `{efecto}`) y concordancia de género y número.
- Tamaño de texto ajustable.

## 8. Pendiente de validar con el mockup

- [ ] ¿El giro de cámara entre estaciones se siente bien, o mejor otro movimiento (vertical, rotación)?
- [ ] ¿El minijuego de remover es divertido o cansa a la décima poción? (Para eso está la elaboración rápida.)
- [ ] ¿La cola de clientes y los efectos en la gente que pasa se leen bien?
- [ ] ¿Gus como probador encaja, o prefieres otra forma de descubrir?
