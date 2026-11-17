# Hábitos

Seguimiento personal de hábitos con rachas, pausas y estadísticas. Se instala como app (PWA) en el PC (Chrome) y en Android.

**App:** https://carlosmera10.github.io/habitos/

## Qué hace (fase 1)

- **Hábitos** de dos tipos: **sí / no** y **cantidad** (con objetivo diario y unidad: vasos, minutos, páginas…).
- **Programación**: diario, días concretos de la semana, **X veces por semana** o **cada N días**. Si se cambia, los días anteriores se siguen calculando con la programación que tenían entonces.
- **Hoy**: los hábitos que tocan, con casilla de un toque (o botones + y − en los de cantidad), la racha de cada uno y el progreso semanal de los de «X veces por semana». Flechas, selector de fecha y botón «Ayer» para registrar días pasados. Los que no tocan ese día se pueden desplegar aparte.
- **Detalle del día** (tocando el nombre): hecho o cantidad exacta, nota y día de pausa con motivo.
- **Rachas**:
  - Diario, días concretos y cada N días: días programados seguidos cumplidos. Hoy sin marcar no rompe la racha; se rompe cuando pasa un día programado sin cumplir.
  - X veces por semana: semanas seguidas con la cuota cumplida. La semana en curso no rompe mientras aún se pueda cumplir. La primera semana incompleta solo suma si se cumple.
  - Los días de pausa ni suman ni rompen.
- **Pausas** de un día o de un periodo (vacaciones), para un hábito o para todos, con su lista para quitarlas.
- **Hábitos**: alta, edición, archivo, borrado (con confirmación y opción de archivar), color, icono, categoría, etiquetas y orden con botones subir/bajar. Racha actual, mejor racha y cumplimiento a 7 y 30 días.
- **Deshacer** en cada cambio (botón del aviso o `Ctrl+Z`).
- **Copias de seguridad**: exportar a JSON e importar con **Fusionar** (por cada hábito, registro o pausa gana la versión más reciente; lo borrado no reaparece) o **Sustituir todo**. Recordatorio de copia configurable.
- **Avisos** solo con la app abierta: al abrirla, cuántos hábitos quedan pendientes hoy. Con la app cerrada no hay avisos.
- Tema automático, claro u oscuro; la semana empieza el lunes (se puede cambiar al domingo).

Próximas fases: calendario y estadísticas (2), tablas y gráficos (3), importar de Habitica (4), refinamientos (5).

## Cumplimiento

- Diario, días concretos y cada N días: días cumplidos entre días programados. No cuentan las pausas, los días anteriores al inicio ni hoy si aún no está hecho.
- X veces por semana: cada semana completa vale `min(registros, X) / X` y se hace la media. La primera semana incompleta no cuenta.
- Hábitos de cantidad: un día cumple si la cantidad llega al objetivo.

## Instalación

### Publicar (una vez)

1. En https://github.com, botón **«+»** (arriba a la derecha) → **«New repository»** → nombre `habitos`, **Public**, marca **«Add a README file»** → **«Create repository»**.
2. En el repositorio: **«Settings»** → menú izquierdo **«Pages»** → **«Build and deployment»** → **«Source»: «Deploy from a branch»** → **«Branch»: `main`** y carpeta **`/ (root)`** → **«Save»**.
3. Al cabo de uno o dos minutos la dirección aparece arriba en esa misma página.

### PC (Chrome)

1. Abre la dirección de la app en Chrome.
2. Pulsa el icono de instalar de la derecha de la barra de direcciones, o el menú **⋮** → **«Transmitir, guardar y compartir»** → **«Instalar página como aplicación…»** (el nombre puede variar según la versión de Chrome). También aparece **«Instalar app»** en la barra lateral cuando Chrome lo permite.
3. Confirma con **«Instalar»**.

### Android (Chrome)

1. Abre la dirección de la app en **Chrome**.
2. Menú **⋮** → **«Instalar aplicación»** (o **«Añadir a la pantalla de inicio»** → **«Instalar»**).
3. Confirma. El icono aparece en la pantalla de inicio.

No abras `index.html` desde el disco (`file://`): no se puede instalar. Usa siempre la dirección publicada.

## Dónde se guardan los datos

- En **IndexedDB** del navegador, base de datos `habitos_v1`, almacén `state`, con un único documento JSON. El navegador pide que el almacenamiento sea persistente al primer arranque.
- Si hay varias pestañas abiertas, se avisan entre sí (`BroadcastChannel('habitos')`) y recargan los datos.
- Las preferencias de cada dispositivo (vista, tema, barra lateral, filtros) van en `localStorage` con la clave `habitos_v1_ui`.
- El token de Habitica (fase 4) irá en `localStorage` con la clave `habitos_v1_hab`, **fuera** de los datos: nunca entra en las copias ni en los archivos exportados.
- **No uses «Borrar datos del sitio» de Chrome**: borraría también las otras apps publicadas en `carlosmera10.github.io`. Para empezar de cero, **Ajustes y avisos → Aplicación → Vaciar** (solo afecta a Hábitos).
- Para pasar los datos entre el PC y el móvil: **Exportar** en uno e **Importar → Fusionar** en el otro.

## Publicación

Se sirve con GitHub Pages desde la rama `main`, carpeta `/ (root)`. Archivos: `index.html`, `sw.js`, `app.webmanifest`, `icon-192.png`, `icon-512.png`.

- El service worker descarga primero de internet (`no-store`) y solo usa la copia guardada sin conexión.
- **Si cambia `sw.js`, hay que subir antes el número de `CACHE`** (ahora `habitos-v1`).
- Para comprobar una publicación: abre la dirección en Chrome del PC, **F12** → pestaña **«Application»** → **«Cache Storage»** y mira que aparece el nombre de caché nuevo.

## Pruebas

Ganchos en `window.__habitos`: `state`, `normalizeState`, `normalizeItem`, `isDue`, `isScheduled`, `computeStreaks`, `computeStats`, `compliance`, `unitsOf`, `mergeStates`, `undo`, `exportData`, `parseNum`, `setToday(fecha)` (fija «hoy») y `setState(json)` (escribe en IndexedDB y repinta). Con `?nosw` en la dirección no se registra el service worker.
