# Vialix: plan de desarrollo

**Objetivo:** prototipo jugable en el navegador (móvil y escritorio) que después se empaqueta como app Android **sin reescribirlo**. Mismo flujo que AdventurersGuild: pruebas con artefactos de Claude → GitHub Pages → Android con Capacitor.

## 1. Tecnología

Se reutiliza el stack de AdventurersGuild, que ya funciona, y se añade una capa WebGL para la escena, porque aquí los efectos visuales son un pilar.

| Pieza | Elección | Por qué |
| --- | --- | --- |
| Lenguaje | **TypeScript** | Igual que AdventurersGuild |
| Build | **Vite** con `base: './'` | El mismo build sirve en Pages, en local y en Capacitor |
| Interfaz (paneles, textos) | **Preact** + CSS propio | Texto legible, traducible y accesible |
| Escena (tienda, caldero, efectos) | **WebGL** (PixiJS v8 o un renderizador propio, por decidir en el prototipo) | Partículas por miles, shaders de líquido, brillo y luz sin castigar al móvil |
| Núcleo del juego | **TS puro, sin DOM** | Testeable y ejecutable en Node para simular el balance |
| Aleatoriedad | Generador con semilla | Partidas y bugs reproducibles |
| Tests | **Vitest** | |
| Guardado | `localStorage` tras una interfaz; Capacitor Preferences en Android | |
| Idiomas | Archivos `src/i18n/<idioma>.json` | Español primero, traducible desde el día 1 |
| CI/CD | GitHub Actions + **GitHub Pages** | Lint, tipos, tests y build en cada push |
| Android | **Capacitor** | Misma web en una app nativa, con vibración y botón atrás |

## 2. Arquitectura (prevista)

```
src/
  core/      lógica sin DOM: modelo, alquimia, clientes, día, economía, reducer
  data/      contenido: esencias, ingredientes, efectos, clientes, edictos, plantillas
  i18n/      textos por idioma
  art/       paleta, píxeles y piezas dibujadas en código
  scene/     escena WebGL: tienda, caldero, partículas, luz, cámara
  audio/     sonido sintetizado
  ui/        paneles Preact
  platform/  guardado, vibración (web y Capacitor)
```

**Principios:**
- El estado es JSON serializable y versionado.
- Las acciones pasan por un reducer puro.
- El contenido vive en `data/`: un pueblo, un cliente o un ingrediente nuevo no tocan la lógica.
- La interfaz no calcula reglas: la alquimia se resuelve en `core/`.

## 3. Fases

| Fase | Qué | Se prueba con |
| --- | --- | --- |
| **0. Definición** | Documentos de diseño, interfaz y arte | Este repo |
| **1. Mockups** | Pantallas clave en pixel art: tienda (ventanilla + taller), caldero en acción, Gaceta, mercado. El caldero, jugable para tocar la alquimia | Artefacto de Claude |
| **2. Cimientos** | Vite + TS + Preact + WebGL, CI, despliegue en Pages, guardado, i18n | GitHub Pages |
| **3. Rodaja vertical** | Un día completo: ~10 ingredientes, 15 efectos, 5 clientes (2 recurrentes), 1 edicto, la Gaceta, Gus | GitHub Pages |
| **4. Contenido y espectáculo** | Mercado, facciones, más clientes y arcos, mejoras, pulido de efectos y sonido | GitHub Pages |
| **5. Android** | Capacitor, rendimiento, vibración, guardado nativo, Play Store | APK |
| **6. Ambulante** | Mapa, pueblos y esencias nuevas | |

## 4. Plan de implementación (octubre de 2026)

Tras las [decisiones de octubre](decisiones.md), la fase 1 (mockups) sigue con estos pasos antes de pasar a los cimientos. Cada paso es una versión del mockup que se prueba en el artefacto antes de seguir.

| Versión | Qué | Por qué en este orden |
| --- | --- | --- |
| **v0.9 · Prueba de estilo** (hecha: falta tu visto bueno) | La ventanilla repintada al estilo LucasArts: una gama por escena, calle suave con tramado, personajes con contraste, torcido sutil. Con un interruptor para comparar con el estilo actual. La interfaz no cambia | La dirección de arte afecta a todo lo demás; mejor validarla en una pantalla antes de repintar el resto |
| **v0.10 · Alquimia nueva** (hecha; en la v0.10.1, reloj de arena por timing, sprites por estado y solapes) | Taller con bases líquidas, tratamientos (entero, troceado, molido, tostado), reloj de arena, lectura a ojo con aerómetro, recetario (recetas compradas y descubiertas) y lotes de 3 o 4 frascos | Es el corazón del juego, y su duración real (30 a 60 s por preparación) decide el ajuste del reloj |
| **v0.11 · El ritmo del día** (hecha: pendiente de probar) | Reloj visual, madrugada lenta, abrir cuando quieras, cola desde las 8:00 con aviso, paciencia de los clientes, urgentes sin Apuntar, cierre al atardecer y domingo cerrado | Con la alquimia ya jugable se pueden ajustar las velocidades del reloj y la paciencia |
| **v0.12 · Mercado y economía** | Ingredientes con precio y existencias, salir al mercado cierra la tienda, el librero de recetas y el aerómetro a la venta | Da sentido al stock y a las recetas compradas |
| **v0.13 · Tutorial del domingo** | La partida empieza en domingo: carta de Remedios y Gus enseñando la alquimia nueva; el lunes se abre | Va al final porque enseña todo lo anterior |
| **v0.14 · Repintar el resto** | Taller, almacén, puerta y gente de la calle con el estilo validado en la v0.9 | Solo cuando el estilo esté aprobado |

Después, la **fase 2 (cimientos)**: Vite + TypeScript, núcleo sin DOM con tests, guardado y despliegue en GitHub Pages, portando lo validado en el mockup.

Queda para más adelante, fuera de estos pasos: el personal (Gus como entretenedor, segundo ayudante y becarios), los retoques de interfaz pendientes de valorar (ver [arte.md](arte.md)) y las mejoras de la tienda.
