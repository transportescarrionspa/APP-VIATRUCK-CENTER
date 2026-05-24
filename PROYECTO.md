# VIATRUCK CENTER — Instrucciones del Proyecto

## Qué es este proyecto
App mobile-first para el **taller mecánico de camiones VIATRUCK CENTER**.
Es un portal para los **clientes del taller** (dueños de camiones) donde pueden:
- Ver el estado de sus camiones en tiempo real
- Aprobar diagnósticos y cotizaciones
- Seguir el avance de la orden de trabajo
- Chatear con el mecánico
- Ver el historial de servicios

## Stack técnico
- **Un solo archivo HTML** — sin build, sin dependencias locales
- React 18 + Babel standalone (CDN)
- CSS inline con variables CSS
- Sin frameworks de UI externos
- Funciona abriendo el archivo directo en el navegador

## Archivo principal
`index.html` — contiene todo: estilos, componentes, datos demo y lógica.
Versión de respaldo: `index.v1.html` (versión anterior guardada)

## Repositorio GitHub
- **Repo:** `transportescarrionspa/APP-VIATRUCK-CENTER`
- **Rama de trabajo:** `claude/viatruck-center-app-qqRm0`

## Diseño
- **Estilo:** Dark theme, profesional, mobile-first
- **Color primario:** Naranja `#EA580C` + blanco
- **Verde:** `#059669` (operativo/éxito)
- **Rojo:** `#DC2626` (urgente/error)
- **Cyan:** `#0891B2` (info)
- **Tipografía:** DM Sans (texto) + DM Mono (números/PPU)
- **Pantalla:** Phone shell de 375×780px centrado en la página
- **Sin emojis innecesarios** — solo donde aportan al UX

## Componentes principales
- `LoginScreen` — selector empresa + numpad PIN
- `HomeScreen` — lista de flota con card activa destacada
- `BottomSheet` — detalle del camión al tocarlo desde home
- `DiagnosticoScreen` — fallas con nivel de urgencia
- `CotizacionScreen` — ítems con aprobación/selección/rechazo
- `OTScreen` — orden de trabajo con progreso en tiempo real
- `ChatScreen` — mensajes con mecánico y typing indicator
- `HistorialScreen` — timeline de visitas anteriores
- `NotificacionesScreen` — alertas con badge en top bar
- `StatusBar` — barra de estado con reloj en vivo
- `StepIndicator` — breadcrumb del flujo Diagnóstico → Cotización → OT
- `TabBar` — Flota / OT Activa / Chat / Historial

## Estado global (App)
- `screen`: "login" | "app"
- `empresa`: cliente seleccionado
- `view`: "home" | "ot" | "chat" | "historial"
- `subView`: "diagnostico" | "cotizacion" | "historial-detail" | null
- `camion`: camión seleccionado
- `sheet`: camión en bottom sheet
- `otTareas`: estado de tareas OT (levantado a App para persistir)
- `msgs`: mensajes de chat (levantado a App para persistir)
- `navDir`: "forward" | "back" | "tab" — controla dirección de transición

## Datos demo
**Clientes:**
- Transportes Carrión SpA — RUT 76.123.456-7 — PIN cualquier 4 dígitos
  - PPU-3341: Mercedes Actros 2546 — OPERATIVO
  - BKF-1104: Volvo FH 500 — EN TALLER (camión activo con OT)
  - KTJ-881: Scania R450 — LISTO PARA RETIRO
- Minera Atacama — RUT 76.987.654-3
  - GHJ-445: Kenworth T800 — EN ESPERA
  - KTJ-220: Freightliner Cascadia — OPERATIVO

**OT activa:** OT-2025-089 en BKF-1104
**Mecánico:** Rodrigo Tapia — Especialista Motor — ⭐ 4.9
**ETA:** 17:30 hrs
**Cotización total:** $411.000 CLP

## UX implementado (v2)
- Transiciones direccionales: slide derecha (avanzar) / izquierda (volver) / fadeUp (tab)
- Bottom Sheet al tocar camión desde home
- Status bar con reloj en vivo + íconos SVG
- Step indicator en flujo de aprobación
- Typing indicator en chat (3 dots animados)
- OT badge pulsando en tab cuando hay trabajo activo
- Toast de confirmación al aprobar cotización
- Estado de OT y chat persiste al navegar entre tabs

## Convenciones de código
- Estilos siempre como objetos inline en JSX (no clases excepto animaciones)
- Variables CSS en `:root` para colores y fuentes
- Animaciones CSS nombradas en kebab-case
- Componentes en PascalCase, helpers en camelCase
- `clp(n)` para formatear precios en CLP
- `nowT()` para hora actual en formato HH:MM
- No agregar comentarios al código salvo que el WHY sea no obvio

## Cómo continuar trabajando
1. Pedile a Claude que modifique `index.html`
2. Claude entrega el archivo actualizado para descargar
3. Guardarlo en `C:\Proyectos\viatruck-center\`
4. Abrir con doble clic en Chrome o Firefox

## Próximas ideas (backlog)
- Pantalla de perfil de empresa
- Módulo de pagos / boletas
- Push notifications reales
- Modo claro (light theme)
- PWA para instalar en el celular
- Backend real con API
