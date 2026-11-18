# Hábitos

Seguimiento personal de hábitos con rachas, pausas y estadísticas. Se instala como app (PWA) en el PC (Chrome) y en Android.

**App:** https://carlosmera10.github.io/habitos/

## Qué hace

- **Hábitos** de dos tipos: **sí / no** y **cantidad** (con objetivo diario y unidad: vasos, minutos, páginas…).
- **Programación**:
  - Días fijos: todos los días, días de la semana, **días del mes** (el 31 cuenta como último día en los meses cortos) o cada N días.
  - Cuotas: **X veces por semana**, **al mes** (mes natural), **al año** (año natural) o **cada N días** (periodos seguidos de N días desde el inicio).
  - Si se cambia, los días anteriores se siguen calculando con la programación que tenían entonces.
- **Para hacerlo fácil** (ideas de *Hábitos atómicos*, Atoms, Productive y Daylio): plantillas al crear, momento del día (Hoy se agrupa en mañana, tarde y noche), señal («Después del café»), **versión mínima** (cuenta como hecho y queda anotada), identidad («Soy una persona que lee»), aviso **«No falles dos veces»**, celebración de **hitos** de racha (3, 7, 14, 21, 30, 50, 66, 100… unidades) y del **día perfecto**, y **ánimo del día** (1 a 5 con nota) con su año por colores y la relación entre tu ánimo y cada hábito.
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
- **Diseño propio** («cada día es una casilla»): papel con trama de puntos, casillas cuadradas, marcador amarillo para hoy, barra superior en el PC y barra inferior clara en el móvil; «Hoy» como hoja de calendario de taco con la semana en casillas que se llenan con lo cumplido.
- Tema automático, claro u oscuro; la semana empieza el lunes (se puede cambiar al domingo).
- **Calendario** (fase 2): vista mensual de todos los hábitos (todos cumplidos, algunos, ninguno, pausa o no tocaba) o de uno solo (hecho, parcial, no cumplido, pausa o no tocaba; en los de «X veces por semana», una columna con la cuota de cada semana). Tocar un día abre «Hoy» en ese día o el detalle del hábito. Debajo, la cuadrícula de los últimos 12 meses.
- **Estadísticas** (fase 2): cifras (cumplimiento a 30 días, del mes y del año, días perfectos; o racha, mejor racha y registros de un hábito), barras de cumplimiento por mes y cuadrícula anual, para los últimos 12 meses o un año. Descripción al pasar el ratón y «Ver tabla» con los valores. Con «Todos los hábitos», el cumplimiento es la media de los hábitos que tocaban.
- **Tipo «Evitar»**: para dejar algo. Solo se marca el día que se recae; el resto de días programados cuentan como limpios (hoy cuenta cuando termina).
- **Hoy en varios días**: hábitos en filas y los últimos días en columnas (4 en el móvil, 7 en el PC), para marcar de un toque, como la lista de Loop.
- **Ficha de cada hábito** (al estilo de Loop): resumen con la **puntuación** (fuerza del hábito) y su cambio en el mes y el año, puntuación por día, semana, mes, trimestre o año, historial de veces (o cantidad, o recaídas), media diaria frente al objetivo, calendario con números, mejores rachas, frecuencia por día de la semana y mes, cumplimiento por día de la semana y por mes, y cifras (racha, mejor racha, cumplimiento, tendencia, mejor día, mejor mes, días sin recaer).
- **Estadísticas de todos**: cumplimiento a 30 días y del periodo, tendencia, días perfectos, mejor y peor día, fin de semana frente a entre semana, cumplimiento por mes y por semana, por día de la semana, ranking por cumplimiento o racha, comparación de hábitos o categorías, reparto por categoría y etiqueta, «Hábitos que van juntos» y cuadrícula anual. Filtros de periodo, categoría, etiqueta y archivados.
- **Tablas** ordenables y exportables a CSV para Excel (separador «;» y coma decimal): resumen, meses, semanas, días de la semana, categorías y etiquetas, rachas, registros (con búsqueda, páginas de 100 y edición) y relaciones entre hábitos. En el móvil, la primera columna queda fija.
- En el móvil, barra inferior con Hoy, Calendario, Estadísticas, Tablas y «Más» (Hábitos, Ajustes y avisos, Instrucciones).

### Puntuación

Como en Loop: media móvil exponencial de lo cumplido. Cada día (o semana, en «X veces por semana») con obligación aporta 1 si se cumple, 0 si no, o la parte cumplida (cantidad entre objetivo; registros entre cuota). La vida media es de 13/√f días, siendo f las veces esperadas por día: 13 días en un hábito diario, unos 20 en uno de 3 veces por semana. Las pausas y los días que no tocan no la cambian.

Próximas fases: importar de Habitica (4), refinamientos (5).

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
- Sin sincronización, para pasar los datos entre el PC y el móvil: **Exportar** en uno e **Importar → Fusionar** en el otro.

## Sincronizar el PC y el móvil

En **Ajustes y avisos → Sincronización (PC y móvil)**, con los pasos para crear el token dentro de la propia pantalla:

1. Pega un token de GitHub *fine-grained* con un único permiso de cuenta: **Gists: Read and write**. **Sirve el mismo token del Revisor de Tareas.**
2. Elige una contraseña de cifrado (mínimo 8 caracteres, la misma en todos los dispositivos) y pulsa **Activar sincronización**.
3. Repite en el otro dispositivo con el mismo token y la misma contraseña.

- Los datos se guardan en un **Gist secreto** propio (`habitos-sync.json`, distinto del del Revisor), **cifrados** en el navegador (PBKDF2-SHA256 de 600 000 vueltas + AES-GCM de 256 bits, con compresión previa).
- El token y la contraseña se guardan **solo en el `localStorage` de cada dispositivo** (`habitos_v1_sync`) y nunca entran en las copias.
- Se sincroniza al abrir la app, unos segundos después de cada cambio, al volver a la app o recuperar la conexión, y cada 3 minutos.
- **Fusión elemento a elemento**: en cada hábito, registro, pausa, categoría y etiqueta gana la versión más reciente; los borrados se anotan (180 días) para que no reaparezcan. Un dispositivo recién estrenado adopta lo que hay en GitHub.
- **No se sincronizan** los ajustes ni la interfaz de cada dispositivo.
- Si algo falla (token caducado, contraseña incorrecta…), aparece un aviso y un punto rojo en «Ajustes y avisos»; la sincronización queda en pausa hasta corregirlo y pulsar «Sincronizar ahora».

## Habitica

Se marca **solo en Habitica**; Hábitos **importa** y analiza. Solo se hacen lecturas: nunca se puntúa, nunca se llama a `POST /cron` ni se cambia nada allí. Pantalla **Habitica** (en el PC, en la barra superior; en el móvil, en **Más**).

**Conectar:** habitica.com → icono de usuario → **Ajustes** → pestaña **API** (o `https://habitica.com/user/settings/api`): copia el **ID de usuario** y el **Token de la API** («Mostrar token de la API») y pégalos en la pantalla Habitica → **Conectar**.

- El ID y el token se guardan **solo en el `localStorage` de ese dispositivo** (`habitos_v1_hab`): no entran en el estado, las copias, lo exportado ni el Gist. Si el token se expone, se regenera en esa misma página. Cada petición lleva `x-client` (`<ID>-habitos`). Los nombres en español de huevos, pociones, comida y misiones se piden a `/content?language=es` y se guardan 30 días (`habitos_v1_habnames`).
- Se importa al abrir la app, al volver a ella y cada 3 minutos (y con «Importar ahora»). Si Habitica limita las peticiones (429), se espera lo que indique `Retry-After`.
- **Importar** crea los hábitos con su historial; **Enlazar con…** une una tarea a un hábito que ya existe, **conserva lo que había** y añade los días de Habitica. Los enlaces (y sus quitas) se sincronizan por el Gist.
- En los hábitos enlazados manda Habitica: en cada día que Habitica conoce, el registro queda como allí (marcado, desmarcado o con su número). No se marcan desde Hábitos (aparece la etiqueta «Habitica» y un aviso); al quitar el enlace vuelven a ser normales.
- **Diarias** → hábitos sí/no con la programación de Habitica: cada X días, días de la semana cada X semanas, días del mes o N-ésimo día de la semana cada X meses, y cada X años (mismas reglas que Habitica). Una diaria «en gris» se importa archivada. El nombre y la programación siguen a Habitica.
- **Hábitos** → «+» como cantidad (veces al día), «−» como «Evitar» con el número de veces del día; los que tienen **+ y −** se importan como dos y su ficha añade el **balance + / −**: proporción a favor, días ganados y perdidos, + y − al día, días sin −, tendencia, color del valor en Habitica, gráfico divergente por día, semana o mes, y medias por día de la semana.
- **Historial:** cada marca de una diaria cuenta para el día que Habitica tenía abierto (zona horaria, inicio de día personalizado y cambios de día de `history.exp`); cada fallo, para el día que se cerró. Lo que Habitica ya comprimió en medias no tiene días: se guarda aparte (`habitica.history`).
- **Panel:** nombre, nivel y clase; vida, experiencia y maná; oro; mascota y montura; misión del grupo.
- **Establo:** huevos que se pueden eclosionar (las pociones mágicas y raras solo con huevos normales; incluye las mascotas que ya son montura) y mascotas que la comida que tienes puede convertir en montura (favorita +5, otra +2, mágicas cualquier comida; raras y especiales no se alimentan), con sillas de montar. «Hoy» avisa si hay algo.
- **Guía** «Cómo crear cada frecuencia en Habitica», con los pasos en la web y en Android.

## Días pasados

- Cualquier día pasado se registra desde «Hoy» (flechas, fecha o «Ayer»), «Varios días», el calendario o la ficha del hábito.
- Registrar un día **anterior al inicio** adelanta el inicio del hábito a ese día (en «Evitar», el inicio se cambia en el editor).
- En la ficha: **Editar** en el calendario marca y desmarca días de un toque, y **Rellenar días** marca (o borra) todos los días de un periodo, eligiendo los días de la semana y, en los de cantidad, la cantidad.

## Publicación

Se sirve con GitHub Pages desde la rama `main`, carpeta `/ (root)`. Archivos: `index.html`, `sw.js`, `app.webmanifest`, `icon-192.png`, `icon-512.png`.

- El service worker descarga primero de internet (`no-store`) y solo usa la copia guardada sin conexión.
- **Si cambia `sw.js`, hay que subir antes el número de `CACHE`** (ahora `habitos-v1`).
- Para comprobar una publicación: abre la dirección en Chrome del PC, **F12** → pestaña **«Application»** → **«Cache Storage»** y mira que aparece el nombre de caché nuevo.

## Pruebas

Ganchos en `window.__habitos`: `state`, `normalizeState`, `normalizeItem`, `isDue`, `isScheduled`, `scoreSeries`, `scoreAt`, `relations`, `weekdayRates`, `buildTable`, `dayGlobal`, `habitDay`, `monthCompliance`, `globalCompliance`, `computeStreaks`, `computeStats`, `compliance`, `unitsOf`, `mergeStates`, `undo`, `exportData`, `parseNum`, `syncNow`, `fingerprint`, `habSync`, `habRt`, `stableInfo`, `pmStats`, `habAlerts`, `habSchedule`, `habDailyDays`, `habHabitDays`, `dueFixed`, `normSchedule`, `mark(id, fecha, valor)`, `setToday(fecha)` (fija «hoy») y `setState(json)` (escribe en IndexedDB y repinta). Con `?nosw` en la dirección no se registra el service worker.
