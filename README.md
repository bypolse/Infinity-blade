# Infinity Blade

## Introducción
Este repositorio contiene la guía paso a paso para crear **Infinity Blade**, un juego **2D por turnos** en Unity, inspirado en el estilo artístico de *Sea of Stars* y *Final Fantasy Resonance* y en la mecánica de pruebas de habilidad de *Clair Obscur: Expedition 33*.

## Estructura del proyecto
```text
Infinity-blade/
├─ Assets/                 # Contenido del proyecto Unity
│   ├─ Scenes/            # Escenas del juego
│   │   └─ Main.unity
│   ├─ Scripts/           # Código C#
│   │   ├─ Core/          # Motor del juego, gestión de estado
│   │   ├─ UI/            # Interfaces de usuario
│   │   ├─ Characters/    # Lógica de personajes y enemigos
│   │   └─ Utils/        # Utilidades y helpers
│   ├─ Prefabs/           # Prefabricados reutilizables
│   ├─ Materials/        # Materiales y shaders
│   ├─ Audio/            # Sonidos y música
│   └─ Plugins/          # Plugins externos (Rider, etc.)
├─ ProjectSettings/       # Configuración del proyecto Unity
├─ Packages/              # Paquetes de Unity (manifest.json)
├─ .gitignore            # Ignorar archivos generados por Unity
├─ README.md             # Esta guía
├─ .env                  # Variables de entorno (si se usan scripts externos)
└─ build/                # Salida de builds (generated)
```

## Paso a paso
### 1️⃣ Inicialización del proyecto
- Instalar Unity Hub y la versión LTS recomendada (2022.3 o superior).
- Crear un nuevo proyecto **2D** llamado `InfinityBlade`.
- Añadir el archivo `.gitignore` de Unity (el que ya está en el repo).
- Realizar el primer *commit* con la estructura de carpetas vacía.

### 2️⃣ Configuración del entorno
- Configurar los *layers* y *tags* necesarios (Player, Enemy, UI).
- Ajustar `ProjectSettings/Quality` y `Graphics` según la visión del juego.
- Crear un `Scenes/Main.unity` vacío y guardarlo.
- Configurar control de versiones (Git) y habilitar LFS para assets grandes.

### 3️⃣ Núcleo del juego (Core)
- En `Scripts/Core/` crear `GameManager.cs` que maneje el ciclo de vida del juego (Init, Play, Pause, GameOver).
- Crear `TurnManager.cs` que controle la secuencia de turnos (jugador → enemigo) y gestione las pruebas de habilidad.
- Implementar un *singleton* para acceso global.
- Añadir un sistema simple de *state machine* (Menu, Playing, Paused, End).

### 4️⃣ Personajes y jugabilidad
- Crear carpetas `Scripts/Characters/Player` y `Scripts/Characters/Enemy`.
- Implementar `PlayerController.cs` con movimiento, salto y ataques.
- Implementar `EnemyAI.cs` con patrón de patrulla y detección del jugador.
- Generar *prefabs* de jugador y enemigo y guardarlos en `Prefabs/`.

### 5️⃣ UI y HUD
- En `Scripts/UI/` crear `MainMenu.cs`, `HUD.cs` y `PauseMenu.cs`.
- Diseñar las escenas UI usando *Canvas* y enlaces a los scripts.
- Conectar los eventos del `GameManager` a la UI (p.ej., mostrar puntuación).

### 6️⃣ Audio y efectos
- Importar archivos de audio en `Audio/` (música de fondo, efectos).
- Añadir `AudioManager.cs` para reproducir SFX y música con *AudioSource* persistente.

### 7️⃣ Pruebas y depuración
- Escribir pruebas unitarias con **Unity Test Framework** en `Tests/` (p.ej., lógica de daño).
- Ejecutar pruebas en el *Editor* y asegurarse de que pasen antes de cada commit.
- Realizar *playtesting* frecuente y ajustar la dificultad.

### 8️⃣ Optimización y build
- Configurar *Addressables* para recursos externos si el proyecto crece.
- Comprimir y generar *AssetBundles* para escenas secundarias.
- Ejecutar `File > Build Settings` para crear versiones para Windows/macOS.
- Verificar el build en la carpeta `build/` y crear un *tag* de versión en Git.

## Próximos pasos
- Integrar **Cinemachine** y **Timeline** para cinemáticas.
- Añadir un sistema de inventario y habilidades.
- Implementar guardado/carga de partida.

---
*Esta guía está pensada para ser seguida secuencialmente; cada fase depende de la anterior. Puedes adaptar los nombres de carpetas o añadir más según tus necesidades.*

