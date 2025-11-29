# MultiPlatform-PC-Mobile-Example-

## Cross-Platform Player Controller for Unity

Un paquete de Unity simple y eficiente para implementar controles cross-platform (móvil y escritorio) en tu juego.

## 🎮 Características

- **Control de Cámara con Ratón/Táctil**: Rotación suave de cámara con sensibilidad configurable
- **Movimiento Cross-Platform**: Compatible con teclado (WASD) y joystick virtual táctil
- **Zona Muerta Táctil**: Evita interferencias entre controles de movimiento y cámara
- **Fácil Configuración**: Interface intuitiva en el Inspector de Unity
- **Compatibilidad**: Desarrollado en Unity 2021.3.15f1, compatible con versiones más modernas

## 📋 Requisitos

- Unity 2021.3.15f1 o superior
- Dispositivo con pantalla táctil (para controles móviles)

## 🚀 Instalación

1. Importa el paquete `CrossPlatformPlayerController.unitypackage` en tu proyecto Unity
2. Abre la escena `SceneCrossPlatformUnity` incluida en el paquete
3. Configura los controles según tus necesidades

## ⚙️ Configuración

### SimpleMouseLook (Control de Cámara)

```csharp
[Header("Configuración de Rotación")]
public float mouseSensitivity = 100f;    // Sensibilidad para ratón
public float touchSensitivity = 50f;     // Sensibilidad para pantalla táctil

[Header("Límites de Rotación")]
public bool limitXRotation = true;       // Limitar rotación vertical
public float minXAngle = -90f;           // Ángulo mínimo en X
public float maxXAngle = 90f;            // Ángulo máximo en X

[Header("Control Táctil")]
public bool enableTouchControl = true;   // Habilitar controles táctiles
public GameObject touchControlPanel;     // Panel para rotación con touch
public GameObject touchDeadZonePanel;    // Zona muerta para evitar interferencias
```

### SimpleMover (Control de Movimiento)

```csharp
[Header("Configuración de Movimiento")]
public float moveSpeed = 5.0f;           // Velocidad de movimiento

[Header("Joystick Virtual")]
public bool useVirtualJoystick = true;   // Usar joystick virtual en móviles
public GameObject joystickBackground;    // Fondo del joystick
public GameObject joystickHandle;        // Mango/control del joystick
```

## 🎯 Configuración de UI en el Inspector

### Para SimpleMouseLook:
1. **Touch Control Panel**: Arrastra el GameObject UI que actuará como área para rotar la cámara
2. **Touch Dead Zone Panel**: Arrastra el GameObject UI que será la zona muerta (generalmente entre joystick y área de rotación)

### Para SimpleMover:
1. **Joystick Background**: Arrastra el GameObject UI que será el fondo del joystick
2. **Joystick Handle**: Arrastra el GameObject UI que será el mango móvil del joystick

## 🎮 Configuración de Event Triggers

### Para el Touch Control Panel:
- Agrega un **Event Trigger** component
- Configura los eventos:
  - `Drag` → `SimpleMouseLook.OnDragEvent()`

### Para el Touch Dead Zone Panel:
- Agrega un **Event Trigger** component  
- Configura los eventos:
  - `Pointer Enter` → `SimpleMouseLook.OnDeadZoneEnter()`
  - `Pointer Exit` → `SimpleMouseLook.OnDeadZoneExit()`
  - `Begin Drag` → `SimpleMouseLook.OnDeadZoneDragStart()`
  - `End Drag` → `SimpleMouseLook.OnDeadZoneDragEnd()`

### Para el Joystick Background:
- Agrega un **Event Trigger** component
- Configura los eventos:
  - `Drag` → `SimpleMover.OnJoystickDrag()`
  - `Pointer Up` → `SimpleMover.OnJoystickRelease()`

## 🎯 Uso

### En Escritorio:
- **Movimiento**: Teclas WASD o flechas direccionales
- **Rotación de Cámara**: Arrastrar con el ratón

### En Móvil:
- **Movimiento**: Joystick virtual en la parte izquierda de la pantalla
- **Rotación de Cámara**: Arrastrar en la parte derecha de la pantalla (excepto zona muerta)

### Layout Recomendado para Móvil:
```
┌─────────────────────────────────┐
│                                 │
│    [JOYSTICK]       [ZONA]      │
│                   [MUERTA]      │
│                     [ÁREA]      │
│                   [ROTACIÓN]    │
│                                 │
└─────────────────────────────────┘
```

## 🛠️ Scripts Incluidos

### SimpleMouseLook.cs
Controla la rotación de la cámara con soporte para:
- Ratón (escritorio)
- Toques (móvil)
- Límites de rotación vertical
- Zona muerta para evitar interferencias

### SimpleMover.cs
Controla el movimiento del jugador con soporte para:
- Teclado (WASD)
- Joystick virtual táctil
- Movimiento suave y normalizado

## 🔧 Personalización

### Ajustar Sensibilidad:
```csharp
// En el Inspector, modifica:
mouseSensitivity = 150f;    // Más sensible
touchSensitivity = 75f;     // Para controles táctiles
```

### Modificar Velocidad:
```csharp
moveSpeed = 8.0f;    // Movimiento más rápido
```

### Configurar Límites de Cámara:
```csharp
minXAngle = -60f;    // No mirar demasiado hacia abajo
maxXAngle = 80f;     // No mirar directamente hacia arriba
```

## 🐛 Solución de Problemas

**Problema**: Los controles táctiles no funcionan
**Solución**: Verifica que `enableTouchControl` esté activado y los paneles UI estén correctamente asignados con sus Event Triggers

**Problema**: El joystick no responde
**Solución**: Asegúrate de que `useVirtualJoystick` esté activado y los objetos del joystick estén asignados en el Inspector con los Event Triggers configurados

**Problema**: Rotación de cámara muy lenta/rápida
**Solución**: Ajusta los valores de `mouseSensitivity` o `touchSensitivity` según sea necesario

**Problema**: Interferencia entre joystick y rotación
**Solución**: Asegúrate de que la zona muerta esté correctamente configurada entre ambas áreas de control

## 📞 Soporte

Desarrollado por **Michael Mora**  
**GameDev by Dreams of Heaven Games**

Si encuentras algún problema o tienes sugerencias, no dudes en contactar.

## 📄 Licencia

Este paquete está disponible para uso en proyectos personales y comerciales.

---
