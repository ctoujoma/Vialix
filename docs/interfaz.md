# Vialix: interfaz

> Cómo se ve y se toca el juego. Diseño en [`diseno.md`](diseno.md).

## 1. Principios

1. **Una sola escena manda.** La tienda es la pantalla principal y casi todo se abre tocando objetos de la escena (la libreta, el códice, la puerta). Los paneles son superposiciones, no pantallas sueltas.
2. **Vertical y con una mano.** Lo que se toca a menudo está en la mitad inferior, al alcance del pulgar. Arriba se *mira* (el cliente); abajo se *hace* (el taller).
3. **Ventanilla y taller a la vez.** El cliente y el caldero comparten pantalla. Así funcionan los urgentes: el cliente te mira mientras mezclas.
4. **La escena es el tutorial.** Las probetas, el caldero y Gus explican el sistema con animaciones, sin muros de texto.
5. **Todo se lee sin color.** Cada esencia tiene color y símbolo.
6. **Todo el texto es traducible.** Nada de texto en imágenes; claves de idioma desde el primer día.

## 2. Pantalla principal: la tienda

Arte a **180 px de ancho** (×4 en 720p, ×6 en 1080p, ×8 en 1440p). La altura se adapta al móvil (de 320 a ~400 px): en los móviles altos crecen el cielo de la calle y el suelo del taller, no la interfaz.

```
┌──────────────────────────────────┐
│ Día 12 · Lunes   🪙 340   ★★★☆   🏠3d │ ← HUD (DOM)
├──────────────────────────────────┤
│ ░░ calle: paralaje, gente, clima ░░ │
│      ┌──────┐                      │ ← VENTANILLA
│  💬  │CLIENT│   (cola por la ventana)│   el cliente, su bocadillo,
│      └──────┘                      │   la calle de fondo
│ ═══════ MOSTRADOR ═══════ 🔔 📜     │ ← documentos, monedas,
│ [🧪][🧪][🧪][  ][  ][  ]  VITRINA    │   campanilla, edicto clavado
├──────────────────────────────────┤
│  [Rechazar]  [Apuntar]  [Servir]   │ ← FRANJA DE DECISIÓN
├──────────────────────────────────┤
│   🔥  💧  🌿  🌬️  🌀   ← 5 probetas │
│                                    │
│  🥣          ╭─────╮         🧌     │ ← TALLER
│ mortero     │CALDERO│        Gus    │   probetas, caldero, mortero,
│             ╰─────╯                │   Gus, alambique y barril
│   ⚗️    [ 🔥 Hervir | ❄️ | 🌙 ]   🛢️  │ ← modo del caldero
│  → Silencio · Normal · hipo humo   │ ← predicción (si se conoce)
├──────────────────────────────────┤
│ ◂ [🌿][💧][🪶][🌶️][🍄][🫙] ▸  ⇡   │ ← ESTANTE DE INGREDIENTES
│  📒 Libreta  📖 Códice  🚪  ☰       │ ← barra inferior
└──────────────────────────────────┘
```

### 2.1 HUD superior
Día y día de la semana · monedas · reputación en este pueblo · días hasta el alquiler (avisa en rojo si no llegas). Al tocarlo se abre el libro de cuentas.

### 2.2 Ventanilla (arriba, para mirar)
- **Calle** con paralaje: luz según la hora, clima, transeúntes y, por la ventana, la **cola** de los clientes que quedan.
- **Cliente** a medio cuerpo, con parpadeo, gestos y reacciones (impaciencia, alegría, transformación).
- **Bocadillo** con texto que se escribe letra a letra (un toque lo completa).
- **Mostrador:** el cliente deja documentos, que se abren en grande al tocarlos para compararlos con el edicto. Aquí caen las monedas.
- **Edicto del día** clavado en el marco, siempre a mano.
- **Vitrina:** el stock, frascos que brillan según su rareza. Para servir se arrastra un frasco al mostrador.

### 2.3 Franja de decisión (centro)
Cambia según la fase:

| Fase | Contenido |
| --- | --- |
| Taller | «Abrir ventanilla» (botón grande) · «Mercado» si es día de mercado |
| Ventanilla, con cliente | Rechazar · Apuntar · Servir (Servir se ilumina al arrastrar un frasco) |
| Ventanilla, sin cola | «Cerrar la tienda» |
| Urgente | Frase del cliente y su barra de impaciencia (sin reloj duro) |

### 2.4 Taller (abajo, para hacer)
- **5 probetas** sobre el caldero: se llenan de líquido de color al echar ingredientes. Un ingrediente desconocido muestra sus esencias por primera vez aquí. Las opuestas se vacían con chispas al cancelarse.
- **Caldero** en el centro: el líquido mezcla los colores en tiempo real.
- **Selector de modo:** Hervir (fuelle) · Congelar (runa de escarcha) · Macerar (lente de luna).
- **Minijuego:** remover en círculo con el dedo dentro del caldero y mantener la aguja de temperatura en la zona buena. Da la calidad.
- **Predicción** bajo el caldero, solo para efectos ya descubiertos; si no, «→ ???».
- **Mortero** (izquierda): soltar un ingrediente encima para majarlo antes.
- **Alambique y barril:** soltar encima un frasco recién hecho para destilar o fermentar.
- **Gus** (derecha): soltarle un frasco encima para probarlo. Sus 3 pruebas del día se ven como 3 caras de mareo.
- **Embotellar:** un cazo; tirar de él hacia arriba llena el frasco, que vuela a la vitrina.

### 2.5 Estante de ingredientes (abajo del todo)
Tira horizontal de tarros, con desplazamiento lateral. Tocar y mantener muestra la ficha (esencias conocidas o «???», rasgo, cantidad). Se arrastra al caldero o al mortero; también vale tocar el tarro y luego el destino. El asa (⇡) lo despliega como cuadrícula completa con filtros por esencia.

### 2.6 Barra inferior
**Libreta** · **Códice** · **Puerta** (mercado y, más adelante, mapa) · **Menú**. Son los mismos objetos que hay en la escena, para quien no quiera buscarlos.

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

## 8. Pendiente de validar con los mockups

- [ ] ¿Caben en 180 px de ancho la vitrina, las probetas y el estante sin agobiar?
- [ ] ¿La franja de decisión al centro se alcanza bien con el pulgar?
- [ ] ¿El minijuego de remover es divertido o cansa a la décima poción? (Para eso está la elaboración rápida.)
- [ ] ¿La cola de clientes se lee bien por la ventana?
