# Vialix: decisiones de octubre de 2026

Tras jugar el mockup v0.8 había tres cosas que no convencían: el ritmo del día, cómo se hacen las pociones y la estética. Se decidieron con el [legajo de decisiones](https://claude.ai/artifact/8Vgh5sUoT3xeBkBqa8JWa3) (15 de octubre) y una ronda de cabos sueltos en la conversación.

Este documento es el registro: qué se decidió y por qué. El detalle de cada sistema vive en [diseno.md](diseno.md) y el orden de trabajo en [plan-desarrollo.md](plan-desarrollo.md).

## 1. El ritmo del día

| Tema | Decisión |
| --- | --- |
| Madrugada | El día empieza a las 5:00 en el taller, con la tienda cerrada. El reloj corre solo, pero despacio: unos **2 minutos reales por hora** de juego (provisional, se ajusta al probar). |
| Abrir | **Abres cuando quieras.** Desde ese momento el reloj va a velocidad de juego: unos **40 segundos reales por hora** (provisional). |
| Qué empuja a abrir | Desde las 8:00 se forma **cola fuera**. Un aviso dice cuánta gente espera, y esa gente se impacienta: abrir tarde cuesta clientes. No hay multa del Gremio. |
| Cierre | Al **atardecer** (20:00). |
| Reloj visual | Un reloj en pantalla muestra el paso del tiempo (por diseñar: reloj de la torre en el HUD, sol que cruza, o ambos). |
| Cliente que espera | Si pide algo que no tienes y vas a prepararlo, **se impacienta y se va** si tardas: mira el reloj, golpea el cristal y se marcha con una mala reseña en la Gaceta. |
| Urgentes | Los clientes con urgencia **no aceptan «vuelva mañana»**: para ellos no hay Apuntar. |
| Domingo | **Cerrado.** Se cocina sin prisa y se revisa el stock. **No hay mercado.** |
| Mercado | Abre de lunes a sábado. **Ir al mercado deja la tienda cerrada** y el tiempo sigue corriendo: comprar rápido o con calma es una decisión. |
| Primer día | La partida **empieza en domingo**: un día entero para aprender y preparar el género antes de abrir el lunes. |

## 2. La alquimia

Inspirada en la de *Kingdom Come: Deliverance II*: la alquimia es física y la calidad sale de hacer bien los pasos.

| Tema | Decisión |
| --- | --- |
| Base líquida | Se distinguen las **bases** (el líquido) de los **ingredientes** que se añaden. La base sustituye a los botones Hervir, Congelar y Macerar. |
| Tratamientos | Cada ingrediente se puede echar **entero, troceado, molido o tostado**, y cambia cómo suelta sus esencias. |
| Esencias | Se mantienen como la química de debajo: deciden el efecto también cuando sigues una receta. |
| Recetas | Una receta es el procedimiento correcto escrito: base, ingredientes con su tratamiento, orden, vueltas de reloj de arena y pasos finales. **Se compran**, o se **descubren** experimentando y probando en Gus: si sale algo útil, se apunta en tu recetario. |
| Fuerza | La da el **tiempo de hervor**, contado con el reloj de arena. Pasarse de vueltas concentra la mezcla y puede reventar el caldero. |
| Lectura | **A ojo** (color, burbujas, vapor y los comentarios de Gus). El **aerómetro**, que muestra las esencias, se compra en el mercado. |
| Lotes | Cada preparación da **3 o 4 frascos** iguales; un caldero mejor da más. |
| Duración | Una preparación dura **de 30 a 60 segundos reales**. La prisa puede hacer que salga peor. |

## 3. Personal (más adelante, no en la primera versión)

- **Gus** hace de catador (prueba pociones) y de entretenedor (gana tiempo con un cliente impaciente), pero **una cosa cada vez**: si entretiene, no puede probar.
- Se podrá contratar un **segundo ayudante**.
- **Becarios** con nivel: preparan por ti recetas hasta cierta complejidad, y se pueden entrenar para subir de nivel.

## 4. Estética

| Tema | Decisión |
| --- | --- |
| Dirección | **LucasArts pintado**, al estilo de *Monkey Island 1 y 2*. |
| Prioridad | **Paleta y estilo de dibujo:** una gama limitada por escena, fondos suaves con tramado y personajes con más contraste que el fondo. |
| Arquitectura torcida | **Sutil.** Se valora, pero no es el foco. |
| Interfaz | **Se queda como está** de momento, para ver lo anterior con la interfaz actual. Se valoran más adelante: diálogo como texto de color sobre el personaje, interfaz de madera apagada, una sola fuente pixel y menos partículas y brillos. |

## 5. Tutorial

- El domingo del primer día es el tutorial: la carta de Remedios y Gus enseñando el oficio con la alquimia nueva.
- Sustituye a la preapertura del mockup v0.8 (persiana bajada y 3 pociones obligatorias). La idea de no abrir sin género se mantiene: el lunes no abres con la vitrina vacía.

## 6. Propuestas para probar (no cerradas)

Salen de las decisiones, pero hay que jugarlas antes de darlas por buenas:

- **Qué hace cada base:** Agua potencia (Valor, Curación, Piel de piedra, Carisma, Suerte), Aguardiente suprime (Sueño, Olvido, Encoger, Silencio, Anti-maldición) y Vino transforma (Aliento de fuego, Filtro de amor, Crecepelo, Invisibilidad, Polimorfia). El Aceite queda para efectos nuevos más adelante.
- **Qué hace cada tratamiento:**
  - Entero: suelta sus esencias poco a poco, un punto por vuelta de reloj.
  - Troceado: la mitad al echarlo y el resto en la vuelta siguiente.
  - Molido: todo de golpe y un punto más de su esencia principal. Más fuerza, menos control.
  - Tostado: pierde su esencia menor, que es una forma de evitar el efecto secundario sin alambique.
- **Vueltas de más:** cada vuelta después de que todo esté suelto suma un punto a todas las esencias presentes. Pasar de 9 en una revienta el caldero.

## 7. Ronda de pulido tras jugar la v0.11 (16 de octubre)

| Tema | Decisión |
| --- | --- |
| Tutorial | Gus se presenta antes de nada, y el primer encargo es «preparar algo de género antes de abrir». Si te sales del guion (otra base, otro ingrediente u otro tratamiento), Gus lo dice y ofrece vaciar el caldero. |
| Bases | Fuera de la pantalla el «Agua potencia, Aguardiente suprime…»: confundía al llegar. Queda como nota de Remedios en el libro, en palabras llanas: «el agua da, el aguardiente quita, el vino cambia». |
| Recetario | Índice y una hoja por receta con los pasos dibujados, como en *Kingdom Come*. El libro solo se desplaza en vertical; en pantallas anchas, a doble página. |
| Cifras | Fuente pixel aparte para los números (el 2, el 5 y el 8 se confundían). |
| Aerómetro | No es un camino obligado: desaparece el botón del taller y lo vende el vidriero ambulante del mercado. |
| Vitrina | 6 huecos con hasta 3 frascos iguales cada uno (18 en total). |
| Esperar | El reloj del HUD es un botón que pasa el tiempo deprisa hasta que llega alguien. |
| Gente de la calle | Caricaturas con gracia propia al estilo LucasArts, no figuras genéricas. |
