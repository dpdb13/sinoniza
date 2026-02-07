# Sinoniza - Flashcards de Sinónimos

## Sobre el proyecto
- App de flashcards para estudiar sinónimos para oposiciones de educación
- Un solo archivo HTML (sin framework, sin build step)
- URL: https://dpdb13.github.io/sinoniza/
- Repo: https://github.com/dpdb13/sinoniza

## Tech stack
- HTML + CSS + JavaScript vanilla (todo en un archivo)
- Sin React, sin Vite, sin dependencias
- Google Fonts (DM Sans) por CDN
- localStorage para persistencia
- Deploy directo a GitHub Pages (legacy, sin workflow)
- Anti-cache con meta tags (no hay Service Worker)

## Funcionalidades implementadas
- **600 pares de sinónimos** en 6 categorías: Verbo (115), Adjetivo (105), Sustantivo (105), Arcaísmo (100), Cultismo (80), Educación (95)
- **Flashcard con flip 3D**: ver palabra → pensar → girar → ver sinónimo → acierto/error
- **Repetición espaciada (Leitner 5 cajas)**: lo que aciertas sale menos, lo que fallas sale más
- **Filtro por categorías**: toca una para jugar solo esa, toca otra vez para todas
- **Modo "Fallos"**: ver lista de palabras falladas + jugar solo esas
- **Gamificación**:
  - XP por acierto (10 * dificultad + bonus racha)
  - Penalización por fallo (-3 * dificultad, más en rachas)
  - 10 niveles: Principiante → Leyenda (con emojis)
  - Popup de subida/bajada de nivel durante el juego
  - Rachas: fuego (aciertos) y hielo (fallos)
  - Popup animado "+XP" / "-XP"
- **Panel de niveles**: toca la sección de nivel para ver todos los niveles, XP requerida, cómo funciona
- **Vista de palabras falladas**: desde resumen o desde inicio
- **Persistencia**: progreso, settings, XP en localStorage

## Diseño
- Tema oscuro (fondo #0D0D12)
- Color primario morado (#8B5CF6)
- Fuente DM Sans
- Tarjeta centrada con CSS Grid (3 filas)
- Font-size con clamp() para responsive
- Botones grandes para móvil

## Decisiones técnicas
- CSS Grid para centrado de palabras en tarjeta (no flex, evita problemas de centrado)
- `overflow-wrap: break-word` en vez de `word-break: break-word` (no rompe palabras a mitad)
- Categorías: toggle individual (toca una = solo esa, toca otra vez = todas)
- `startLevelName` en sessionStats para comparar nivel inicio vs final (en vez de flag booleana)
- `function` declarations (no `const`) para funciones llamadas desde onclick inline (necesitan scope global)

## Bugs resueltos
- Palabras cortadas verticalmente: `word-break: break-word` → `overflow-wrap: break-word`
- Palabras clipeadas horizontalmente: `white-space: nowrap` + flex → `text-align: center` + clamp()
- "6100%": racha y porcentaje pegados → separar en elementos distintos
- Nivel incorrecto en resumen: flag `leveledUp` → comparar `startLevelName` vs nivel final

## Plan backup
- Existe plan para convertir en PWA con Vite + React en: `~/.claude/plans/sinoniza-plan-completo-backup.md`

## Estado actual (6 febrero 2026)
- App funcional y desplegada
- Todas las funcionalidades listadas arriba implementadas
- Sin bugs conocidos
