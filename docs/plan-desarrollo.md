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
