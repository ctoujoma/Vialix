# Vialix: documento de diseño

> **Vialix** = *Vial* + *Elixir*. Juego de alquimia para móvil (Android), primero en el navegador.
> Versión 0.1 · Estado: en definición. Interfaz en [`interfaz.md`](interfaz.md), arte en [`arte.md`](arte.md), plan técnico en [`plan-desarrollo.md`](plan-desarrollo.md).

## 1. Concepto

> Regentas una botica en Vialix, una ciudad de fantasía medieval tan burocrática que hasta los dragones piden cita previa. Cada día pasan por tu ventanilla clientes con peticiones vagas, raras o directamente ilegales. Tú decides a quién atiendes, interpretas lo que *de verdad* necesitan y experimentas en el caldero hasta dar con algo que funcione… más o menos.

**Género:** gestión y experimentación por días, con decisiones al estilo *Papers, Please*. Sesiones cortas, en vertical y con una mano.

### Pilares

1. **Experimentar es el juego.** La alquimia es un sistema con reglas que se pueden descubrir, no una lista de recetas. Siempre hay más de una solución.
2. **Interpretar al cliente.** Las peticiones son ambiguas a propósito («que mi suegra deje de hablar… *temporalmente*»). Acertar con una solución lateral es tan válido como la de libro, y a veces más divertido.
3. **Consecuencias visibles y graciosas.** Lo que vendes sale al día siguiente en *La Gaceta de Vialix*. Los clientes vuelven con cuernos, con quejas o con propina.
4. **Espectáculo.** Cada mezcla debe *sentirse*: color, burbujas, luz, partículas, explosiones y vibración. El caldero es el protagonista.
5. **Infinito y ampliable.** No hay final. El contenido (pueblos, ingredientes, clientes, esencias) se añade como datos.

### Referencias

| Juego | Qué tomamos |
| --- | --- |
| Papers, Please | Ventanilla, documentos, normas que cambian cada día, dilemas |
| Potion Craft | Fantasía de alquimista, mezcla física (nos diferenciamos con la ventanilla y las consecuencias) |
| Moonlighter / Recettear | Tienda como base, stock y precios |
| Mundodisco (Pratchett) | Humor, sátira de instituciones |
| Frostpunk / Papers, Please | El periódico como resumen de tus decisiones |

## 2. Ambientación y tono

**Vialix** es una ciudad-estado medieval de fantasía, pero sus problemas son de hoy: el **Gremio de Alquimistas** es una pesadilla de trámites, los bardos son influencers con «seguidores», los goblins venden esquemas piramidales, el casero sube el alquiler cada mes y las reseñas de una estrella se clavan en el tablón de la plaza.

**Tono:** humor amable con mordiscos ácidos de vez en cuando. La sátira apunta hacia arriba: el poder, la burocracia, la codicia, la vanidad. Nunca contra colectivos reales.

- Amable: *«Sir Mantecas gana el torneo a pesar de los cuernos.»*
- Ácido: *«Necrológicas: el señor Ruiz, que compró una poción de juventud en una botica sin licencia, ha vuelto a la lactancia. Le sobreviven sus hijos, ahora mayores que él.»*

**Mid/late game (la tienda ambulante):** el Gremio te expulsa, o simplemente decides irte, y la tienda pasa a viajar a lomos de un caracol gigante (por decidir: caracol, gólem o carromato). Se desbloquea el **mapa** y otros pueblos, cada uno con su mercado, sus clientes, sus facciones y sus edictos. Si un pueblo te odia, te mudas a otro donde no te conocen. **Los pueblos olvidan:** la mala reputación se recupera poco a poco.

## 3. Bucles de juego

Son tres escalas del mismo juego, no alternativas: un **encargo** pasa dentro de un **día**, y los días forman la **progresión**.

### 3.1 El día (núcleo)

El tiempo **no corre en tiempo real**. La unidad es el día y solo avanza cuando el jugador cierra la tienda.

```
 ┌─► AMANECER ──────────────────────────────────────────────────┐
 │   · La Gaceta: consecuencias de lo que vendiste ayer         │
 │   · El Edicto del Día: normas nuevas del Gremio              │
 │   · Fermentaciones listas, encargos que vencen hoy           │
 │                                                              ▼
 │   CIERRE                                                TALLER (sin tiempo)
 │   · Libro de cuentas: ingresos, gastos, tasas           · Experimentar con calma
 │   · Reputación por facción                              · Preparar stock para hoy
 │   · Mejoras de la tienda                                · Encargos de la libreta
 │   · Dormir ─────────────────────────────────┐           · Mercado (días de mercado)
 │                                             │                │
 └─────────────────────────────────────────────┘           VENTANILLA (por turnos)
                                                            · 5–8 clientes, uno a uno
                                                            · Servir, apuntar o rechazar
                                                            · Urgentes ocasionales
```

**Presión:** no hay cronómetro. La presión viene del alquiler semanal, las tasas del Gremio, los plazos de los encargos y la cola de clientes (se ve cuántos quedan por la ventana).

### 3.2 El encargo

1. El cliente llega a la ventanilla. Habla y, a veces, deja documentos en el mostrador (receta del clérigo, licencia, carta, formulario A-38).
2. El jugador **interpreta** lo que pide y lo coteja con el Edicto del Día.
3. Tiene tres respuestas posibles:

| Respuesta | Qué pasa |
| --- | --- |
| **Servir** | Arrastra una poción de la vitrina al mostrador. El cliente reacciona al momento. |
| **Apuntar** | No hay nada adecuado: el encargo va a la **libreta** con plazo («vuelvo en 2 días») y recompensa. |
| **Rechazar** | El cliente se va, con su frase. También tiene consecuencias (reputación, arcos). |

**Urgentes (ocasionales):** *«¡Mi marido es un sapo! ¡AHORA!»*. El cliente se queda en la ventanilla mientras el jugador improvisa en el caldero, que está en la misma pantalla. No hay reloj duro: hay impaciencia creciente (frases, gestos) que baja la propina.

**Hacer stock es una apuesta:** ¿qué pedirán mañana? La Gaceta (titulares, horóscopo, clasificados), el Edicto y la estación dan pistas («Se anuncia ola de calor», «Torneo el sábado»).

### 3.3 Progresión (sin final)

- **Tienda:** más vitrina, mejores herramientas (caldero, alambique, barril, lupa), decoración que atrae clientela.
- **Rango en el Gremio:** licencias que permiten vender pociones de más categoría (y dan más inspecciones).
- **Códice:** la colección de ingredientes, efectos, secundarios y recetas. Siempre hay huecos.
- **Reputación por facción y por pueblo.**
- **Clientes recurrentes con arcos** que se amplían sin fin.
- **Mapa y pueblos** (mid-game), y con ellos **esencias nuevas** que amplían la tabla de efectos.

## 4. Alquimia

La gramática de una poción:

> **QUÉ afecta** (esencia dominante) × **CÓMO** (modo del caldero) × **CUÁNTO** (cantidad) + **efecto secundario** (segunda esencia)

### 4.1 Esencias

| Esencia | Color | Símbolo | Dominio | Opuesta |
| --- | --- | --- | --- | --- |
| Ígneo | rojo | llama | energía, fuerza, ánimo | Acuoso |
| Acuoso | azul | gota | salud, emociones | Ígneo |
| Terroso | verde | hoja | cuerpo físico, tamaño, resistencia | Etéreo |
| Etéreo | blanco-violeta | remolino | mente, voz, percepción | Terroso |
| Caótico | magenta iridiscente | espiral | forma, suerte, lo absurdo | ninguna |

- Las **opuestas se cancelan** punto a punto. Sirven para afinar: si te pasas de Ígneo, añades algo Acuoso.
- El **Caótico** no tiene opuesta: solo puede compensarse destilando. Siempre añade inestabilidad.
- Cada esencia tiene color **y** símbolo, para que se lean sin depender del color.

### 4.2 Modos del caldero (el verbo)

| Modo | Cómo se activa | Verbo |
| --- | --- | --- |
| Hervir | Fuelle bajo el caldero | **Potenciar** |
| Congelar | Runa de escarcha | **Suprimir** |
| Macerar | Lente de luna | **Transformar** |

### 4.3 Modificadores (pasos opcionales)

| Paso | Dónde | Efecto |
| --- | --- | --- |
| Majar | Mortero, antes de echar el ingrediente | Efecto inmediato y más intensidad de ese ingrediente |
| Destilar | Alambique, después de embotellar | Quita el efecto secundario, pero **baja un escalón de intensidad** (se pierde volumen). Un Leve no se puede destilar. El alambique tiene **2 usos al día** (ampliable) |
| Fermentar | Barril, después de embotellar | Más duración. **Tarda 1 día** (está lista al amanecer) |

**Destilar es una decisión, no un trámite.** Cada cliente opina del efecto secundario: a Sir Mantecas o a Gorzag les molesta (baja la satisfacción), a Lirio Dorado o a la Sra. Pellejo les encanta (la sube), y a otros les da igual. Y si un cliente necesita intensidad (Ignatius pide «dosis de dragón», Fuerte como mínimo), destilar le deja corto.

### 4.4 Tabla de efectos base (5 × 3 = 15)

| | Potenciar | Suprimir | Transformar |
| --- | --- | --- | --- |
| Ígneo | Valor / Fuerza | Sueño | Aliento de fuego |
| Acuoso | Curación | Olvido | Filtro de amor |
| Terroso | Piel de piedra | Encoger | Crecepelo |
| Etéreo | Carisma / Ingenio | Silencio | Invisibilidad |
| Caótico | Suerte | Anti-maldición | Polimorfia |

### 4.5 Efectos secundarios (segunda esencia)

Aparecen si la segunda esencia llega a un umbral (por decidir: ≥ 1 punto o ≥ ⅓ de la dominante).

| Segunda esencia | Efecto secundario |
| --- | --- |
| Ígneo | Hipo con humo, eructos de fuego |
| Acuoso | Llanto incontrolable, sudor a chorros |
| Terroso | Piel con musgo, pesadez |
| Etéreo | Flota a dos palmos del suelo, voz de pito |
| Caótico | Transformación parcial aleatoria (orejas de conejo, cuernos, cola) |

### 4.6 Cantidad, intensidad y calidad

- **Intensidad** según los puntos de la esencia dominante (tras cancelar): Leve · Normal · Fuerte · Desmedido.
- **Desmedido** puede hacer el efecto permanente o hacer explotar el caldero.
- **Calidad (★ a ★★★)** según el minijuego del caldero (remover en círculo con el dedo, mantener la aguja en la zona buena). Afecta al precio y a la probabilidad del secundario.

### 4.7 Descubrimiento

- Un ingrediente nuevo muestra sus esencias como «???» hasta que se echa al caldero por primera vez. Entonces las probetas reaccionan y quedan apuntadas en el códice.
- Un efecto de la tabla está oculto hasta que se consigue por primera vez. Cuando ya se conoce, el caldero **predice** el resultado mientras mezclas («→ Silencio · Normal · secundario: hipo con humo»). Conocimiento = poder en la interfaz.
- **Gus, el becario homúnculo**, prueba pociones antes de venderlas: muestra el efecto real y el secundario. Solo aguanta 3 pruebas al día (se marea). Sin probar, vendes a ciegas.
- Las **recetas del mercado** llegan incompletas o dañadas («Susurro embotellado + ??? · congelar»).
- Las **recetas guardadas** se pueden repetir con *elaboración rápida* (sin minijuego, calidad ★★ como máximo) para no repetir el trabajo.

### 4.8 Ingredientes de ejemplo

| Ingrediente | Esencias | Rasgo |
| --- | --- | --- |
| Susurro embotellado | Etéreo 3 | |
| Pluma de gallo insomne | Etéreo 2, Ígneo 1 | |
| Guindilla de dragón | Ígneo 3, Caótico 1 | |
| Lágrima de sirena | Acuoso 3, Etéreo 1 | |
| Seta saltarina | Caótico 3, Terroso 1 | |
| Mandrágora | Terroso 2, Etéreo 2 | Grita al cortarla |
| Babas de caracol | Terroso 2, Acuoso 1 | Pegajoso |
| Polvo de hada (procedencia dudosa) | Etéreo 2, Caótico 2 | Volátil, ilegal según el edicto |

### 4.9 Ejemplos resueltos

**La suegra.** *«Algo para que mi suegra deje de hablar… temporalmente, ¿eh? TEMPORALMENTE.»*
- Voz → Etéreo; dejar de → Suprimir; temporalmente → sin fermentar y en dosis baja.
- **De libro:** susurro embotellado + pluma de gallo, congelado → Etéreo 5 · Ígneo 1 → **Silencio Normal**, secundario Ígneo: la señora eructa humo cada vez que intenta hablar. *Gaceta:* «Vecina de la calle Mayor, nombrada dragón honorífico».
- **Laterales que el juego reconoce:** *Sueño* («Ha dormido tres días. No era lo que pedí… ¿tienes más?»), *Encoger* («Sigue hablando, pero ya no la oigo»).
- **Pasarse:** *Silencio Desmedido* la deja muda para siempre. El cliente vuelve furioso… o encantado, según su arco.

**Sir Mantecas** (recurrente). *«El torneo es pasado mañana. Necesito valor. Mucho. Y que no se note.»*
- Ígneo potenciado; hay plazo, así que se puede fermentar para que dure el torneo; «que no se note» = destilar.
- Si no destilas y usaste guindilla (secundario Caótico), le salen cuernos. Gana igual, y su arco cambia: ahora quiere quitárselos (encargo de *Anti-maldición*).

**El dilema.** *Edicto: «Quedan prohibidas las pociones que alteren la voluntad ajena.»* Un goblin con traje quiere «algo para que la gente confíe en mí, para mi negocio de oportunidades».
- *Carisma*, hoy ilegal. Paga el triple.
- **Vender:** dinero y Bajos Fondos, riesgo de inspección. **Rechazar:** Gremio. **Placebo** (agua con colorante): legal, pero si lo descubre deja una reseña de 1★… salvo que sea tan crédulo que le funcione.

**La noche de prueba.** Seta saltarina macerada → *Polimorfia*. Gus se convierte en pato el resto del día y atiende la tienda siendo pato.

## 5. Clientes

### 5.1 Peticiones

Cada petición define por dentro:
- **Efectos aceptados**, cada uno con su grado de satisfacción y su frase de reacción (la solución de libro y las laterales).
- **Restricciones:** intensidad, duración, secundarios tolerados, legalidad según el edicto, plazo.
- **Pago ofrecido** y propina posible.

### 5.2 Tipos de cliente

| Tipo | Qué es | Contenido |
| --- | --- | --- |
| **Recurrentes** | Personajes con nombre y arco de varios encargos | Escritos a mano; se amplían sin fin |
| **Procedurales** | Arquetipo × necesidad × giro | Plantillas; la cola nunca se agota |
| **Inspectores** | Del Gremio; revisan licencias y vitrina | Aparecen según tu notoriedad |

Los aspectos de los clientes se montan por piezas (cuerpo, cabeza, pelo, sombrero, accesorio, paleta), igual que los retratos de AdventurersGuild, así que cada cliente procedural tiene cara propia.

### 5.3 Recurrentes de partida (borrador)

- **Sir Mantecas**, caballero con síndrome del impostor.
- **La señora Pellejo** y su suegra.
- **Nicodemo**, vecino nigromante con un «proyecto de jardinería».
- **Gorzag**, goblin de los esquemas piramidales («oportunidades»).
- **Lirio Dorado**, bardo influencer obsesionado con sus seguidores.
- **Ignatius**, dragón con burnout.
- **El inspector Grijalba**, del Gremio, que te tiene manía.

## 6. Mercado

- **Días de mercado** (por decidir: cada 3 días o semanal). Se visita en la fase de Taller y no consume tiempo.
- **Puestos** con mercaderes con personalidad: herbolaria, pescadero de criaturas, librero de pergaminos (recetas dañadas y tratados que revelan esencias), chatarrero de herramientas.
- **Regateo:** minijuego rápido. Cada mercader tiene su paciencia y sus manías.
- **Precios dinámicos** según estación y sucesos de la Gaceta («Plaga de ranas» → ranas baratas).
- **El mercader turbio**, en un callejón y solo algunos días: rarezas, recetas sospechosas e ingredientes que mañana pueden ser ilegales.

## 7. Facciones y reputación

| Facción | Le gusta | Le disgusta |
| --- | --- | --- |
| Gremio de Alquimistas | Cumplir edictos, pagar tasas | Contrabando, placebos |
| Bajos Fondos | Discreción, pociones ilegales | Chivatos, rechazar sus encargos |
| Nobleza | Calidad, exclusividad, rapidez | Efectos secundarios visibles |
| Iglesia de la Santa Burocracia | Curaciones, anti-maldiciones | Polimorfia, filtros de amor |

La reputación es **por pueblo** y se recupera con el tiempo. Las reseñas del tablón y las inspecciones dependen de ella.

## 8. La Gaceta de Vialix

El periódico de cada amanecer, y el gran pago del humor:
- **Titular**: la consecuencia más llamativa de lo que vendiste ayer.
- **Breves**: otras consecuencias y noticias del mundo.
- **Reseñas del tablón**: de 1★ a 5★, con su texto.
- **Clasificados y horóscopo del mago**: pistas de la demanda de los próximos días.
- **Necrológicas**, de vez en cuando (el toque ácido).

Todo el texto se genera con plantillas e idiomas intercambiables: nada de texto pintado en las imágenes.

## 9. Economía

- **Ingresos:** ventas, propinas y encargos.
- **Gastos:** ingredientes, alquiler semanal (el casero lo sube), tasas del Gremio, multas y sobornos.
- **Derrota blanda:** si no pagas el alquiler, desahucio. Por decidir si se pierde la partida o se pasa a ambulante a la fuerza.

## 10. Para el juego completo (apuntado tras probar los mockups)

- **Tutorial y preapertura** (ya en el mockup v0.8):
  - El primer día empieza con la persiana a medio bajar y un cartel de «Cerrado». En el mostrador hay una carta de Remedios, la antigua dueña.
  - Gus guía paso a paso desde un panel arriba e ilumina lo que hay que tocar. Primero, Valor (Guindilla + Hervir + remover + embotellar + guardar). Después, Silencio (Susurro + Congelar), que se prueba en Gus para descubrir qué hace. La tercera poción es libre.
  - No se puede abrir hasta tener 3 pociones en la vitrina, también si te saltas las explicaciones («Ya conozco el oficio»).
  - Al subir la persiana llegan el edicto, la cola (entra andando) y el primer cliente. Un aviso explica Apuntar y Rechazar.
  - Si te adelantas, el tutorial te sigue. Si el caldero explota, vuelve al paso de la guindilla.
- **Ampliar la vitrina.** 6 huecos al principio; mejoras de la tienda para pasar a 9, 12… y el **almacén** (la pared de atrás) como depósito de pociones y de ingredientes.
- **Mejoras del alambique** (más usos al día) y de otras herramientas.

## 11. Por decidir

- [ ] Montura de la tienda ambulante: caracol gigante, gólem o carromato.
- [ ] ¿Vialix comparte mundo con AdventurersGuild? (su diseño ya lo menciona: héroes del gremio como clientes, cameos).
- [ ] Umbral exacto del efecto secundario y escalones de intensidad (se ajusta en el prototipo).
- [ ] Frecuencia del mercado y de los urgentes.
- [ ] Monetización.
