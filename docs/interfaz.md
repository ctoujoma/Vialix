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
│   🧪  🧪  ·   ·   ·   ·          │ vitrina (6 huecos)
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
- **Vitrina:** 6 huecos bajo el mostrador, con frascos grandes que brillan con su color y huecos vacíos visibles. Un cartel sobre ella dice qué hacer: «Vitrina vacía · prepara la poción en el Taller ▶» (se toca para ir), «Toca una poción o arrástrala hasta…» o «Pulsa SERVIR…».
- **Servir:** se arrastra el frasco hasta el cliente (se ilumina al pasar por encima), o se toca el frasco y luego el sello Servir. Desde el taller, si hay alguien esperando, la tarjeta de la poción ofrece **«Servir a…»**: la cámara gira sola y el frasco vuela al cliente.
- **Sellos de caucho:** Rechazar, Apuntar y Servir. Al pulsar, el sello golpea con salpicadura de tinta y sonido. Servir se ilumina cuando hay una poción elegida.
- **Penumbra interior** con la luz del farol, y un haz de sol que entra por la ventanilla con motas de polvo.

### 2.3 Taller

> Describe el taller del mockup v0.8. Con la alquimia decidida en octubre de 2026 ([decisiones.md](decisiones.md)) cambiará: bases líquidas en lugar de Hervir, Congelar y Macerar; mortero, cuchillo y fuego para tratar ingredientes; reloj de arena para el hervor; lectura a ojo (las probetas pasan a ser el aerómetro, que se compra); y varios frascos por preparación.

```
┌──────────────────────────────────┐
│ HUD    🔔 Sra. Pellejo espera…   │ aviso si hay alguien en la ventanilla
│ ◯ ventana    [licencia]    🕯 🫙  │
│ 🫙🕯       5    1                │ cifras sobre las probetas
│        ║ ║ ║ ║ ║                 │ 5 probetas
│        🔥 💧 🌿 🌬 🌀              │
│   [→ Silencio · Normal · + hipo] │ predicción
│          ╭──────────╮       🧌   │ caldero · Gus en su taburete
│   ⚗️     ╰──────────╯       🛢   │ alambique · barril
│              🔥🔥                │ hogar (fuego, escarcha o luna)
│ [📖] [Hervir][Congelar][Macerar] [Embotellar]
│ ◂ tarros del estante ▸           │
│  Ventanilla    Taller   Mercado  │
└──────────────────────────────────┘
```
- **Contador de la vitrina** arriba a la derecha («Vitrina 1/6 · servir ▶»), que lleva a la ventanilla.
- **Estante de ingredientes** abajo: se toca un tarro y salta al caldero en parábola, con salpicadura y ondas. Los desconocidos muestran «? ? ?» hasta la primera vez.
- **Espíritus de esencia:** salen del caldero y vuelan a su probeta, que se llena. Las opuestas se anulan con chispas y siseo.
- **Modo del caldero:** Hervir (llamas bajo el caldero), Congelar (escarcha y vapor frío), Macerar (un haz de luna entra por la ventana).
- **Predicción:** «→ ??? · Normal» hasta descubrir el efecto; después, el nombre y el secundario. En Desmedido, el aviso tiembla y el caldero también.
- **Cada pared es un nicho en 3D:** el taller, el almacén y la puerta tienen pared del fondo, suelo de tablones en perspectiva, techo con vigas y paredes laterales con su pilar de madera. Los muebles y personajes están a su distancia (el caldero y Gus delante, las probetas en la pared), así que al girar se nota la profundidad.
- **El caldero se ve desde arriba:** boca ancha y la superficie de la poción como un shader de píxeles (remolinos que siguen al cucharón, brillo de la ventana, ondas de cada ingrediente, escarcha al congelar, estrellas al macerar, pulso rojo si va a explotar).
- **Remover:** se dibujan círculos con el dedo dentro del caldero. A buen ritmo aparece un anillo de runas y sube la calidad (★ a ★★★). Demasiado rápido, salpica.
- **Embotellar:** el líquido baja, el frasco sube con una columna de luz del color de su calidad y estalla en chispas.
- **Gus** reacciona al tocarlo, prueba pociones (3 al día) y se transforma: se calla, flota, se vuelve pato…
- **¡BUM!** Con 10 o más puntos en una esencia: el caldero tiembla, explota (destello, sacudida, parón de un instante, escombros) y el hollín cubre la pantalla hasta que lo limpias con el dedo. Gus se queda tiznado el resto del día.

## 3. Pantallas y paneles

| Pantalla | Tipo | Qué hay |
| --- | --- | --- |
| **Portada** | Pantalla | Logo animado, el caldero burbujeando, continuar o nueva partida |
| **Amanecer: La Gaceta** | Pantalla completa | Periódico que sale de la imprenta: titular con ilustración, breves, reseñas, clasificados y horóscopo. Se pasa con un toque |
| **Amanecer: Edicto** | Superposición | Pergamino que se despliega y sello de lacre que cae con polvo. Después se clava en la ventanilla |
| **Libreta de encargos** | Panel (libreta) | Encargos con retrato, la frase original del cliente, plazo, recompensa y notas. Los que vencen hoy, marcados |
| **Códice** | Panel (libro con pestañas) | Esencias · Ingredientes · Efectos (la tabla de 5 × 3 con huecos) · Secundarios · Recetas guardadas · Clientes (fichas y progreso de sus arcos) |
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

- **Reloj visual** siempre a la vista (por diseñar: en el HUD, en la torre de la plaza o ambos).
- **Aviso de cola** antes de abrir: cuánta gente espera fuera.
- **Domingo:** sin abrir y sin mercado; solo taller. La partida empieza en domingo.

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
- Textos en `src/i18n/es.json` desde el principio. Las plantillas de la Gaceta y de los clientes usan marcadores (`{cliente}`, `{efecto}`) y concordancia de género y número.
- Tamaño de texto ajustable.

## 8. Pendiente de validar con el mockup

- [ ] ¿El giro de cámara entre estaciones se siente bien, o mejor otro movimiento (vertical, rotación)?
- [ ] ¿El minijuego de remover es divertido o cansa a la décima poción? (Para eso está la elaboración rápida.)
- [ ] ¿La cola de clientes y los efectos en la gente que pasa se leen bien?
- [ ] ¿Gus como probador encaja, o prefieres otra forma de descubrir?
