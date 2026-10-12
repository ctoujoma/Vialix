# Vialix: interfaz

> Cómo se ve y se toca el juego. Diseño en [`diseno.md`](diseno.md).

## 1. Principios

1. **Cada estación tiene su pantalla.** La tienda es un espacio que la cámara recorre: la ventanilla, el taller y, más adelante, el mercado. Cada una ocupa la pantalla entera; nada de meterlo todo junto.
2. **La cámara gira entre estaciones.** Se desliza el dedo o se toca la pestaña, y la cámara hace un barrido (desenfoque de movimiento, líneas de velocidad, cambio de luz). Debe sentirse como darse la vuelta dentro de la tienda.
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
- **La plaza:** cielo por bandas que cambia con la hora (mañana → atardecer), nubes, banderines al viento, la torre del Gremio con su reloj (marca la hora real del día de juego) y un sello gigante en lo alto, casas con puestos, la fuente con la estatua del fundador, farola, palomas que se espantan, charco que refleja el cielo.
- **La gente que pasa** va en dos carriles (lejos y cerca). Algunos llevan efectos de pociones: uno flota, otro es un pato, otro mide un palmo. Los clientes a los que sirves salen a la plaza **con el efecto puesto**, y al día siguiente aparecen los de terceros (la suegra eructando humo). Si Ignatius se duerme, queda roncando en la plaza.
- **La cola** se ve por la ventana: figuritas esperando a la derecha.
- **El cliente** a medio cuerpo, con parpadeo y boca al hablar. Llega y se va deslizándose con pasos. Ignatius no cabe: asoma la cabeza, y su llegada hace temblar la pantalla.
- **El bocadillo** está arriba, con el texto letra a letra (un toque lo completa).
- **Mostrador:** libreta (abre los encargos), cuenco de monedas (crece con la caja), campanilla (llama al siguiente) y el edicto clavado en el marco (se abre al tocarlo).
- **Vitrina:** 6 huecos bajo el mostrador; las pociones brillan con su color. Al tocar una, se levanta y aparece su ficha.
- **Sellos de caucho:** Rechazar, Apuntar y Servir. Al pulsar, el sello golpea con salpicadura de tinta y sonido. Servir se ilumina cuando hay una poción elegida.
- **Penumbra interior** con la luz del farol, y un haz de sol que entra por la ventanilla con motas de polvo.

### 2.3 Taller
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
- **Estante de ingredientes** abajo: se toca un tarro y salta al caldero en parábola, con salpicadura y ondas. Los desconocidos muestran «? ? ?» hasta la primera vez.
- **Espíritus de esencia:** salen del caldero y vuelan a su probeta, que se llena. Las opuestas se anulan con chispas y siseo.
- **Modo del caldero:** Hervir (llamas bajo el caldero), Congelar (escarcha y vapor frío), Macerar (un haz de luna entra por la ventana).
- **Predicción:** «→ ??? · Normal» hasta descubrir el efecto; después, el nombre y el secundario. En Desmedido, el aviso tiembla y el caldero también.
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
Portada → [Amanecer: Gaceta → Edicto] → Taller ⇄ Mercado
                                            │
                                     «Abrir ventanilla»
                                            ▼
                                   Ventanilla (cliente a cliente)
                                            │
                                     «Cerrar la tienda»
                                            ▼
                         Cierre: libro de cuentas → «Dormir» → Amanecer
```

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
