# Hábitos — panel de Habitica

Panel personal para **Habitica**: las diarias y los hábitos se marcan en Habitica, y aquí se importan solos para ver el personaje, el establo, calendarios, estadísticas y tablas. Nunca escribe en Habitica. Se instala como app (PWA) en el PC (Chrome) y en Android.

**App:** https://carlosmera10.github.io/habitos/

## Pantallas

- **Panel**: personaje con su mascota y montura (iconos de Habitica), vida, experiencia, maná y oro; misión del grupo con la vida del jefe o los objetos; resumen del establo; diarias de hoy (hecha, pendiente o no toca, racha de Habitica, lista de comprobación y color de la tarea); hábitos de hoy con lo pulsado en + y −; tareas pendientes (vencidas y para hoy); diarias cumplidas y experiencia ganada de los últimos 14 días; año de diarias. Aviso de copia de seguridad.
- **Establo**: arriba, con todo el detalle, las mascotas que ya pueden ser montura con tu comida. Lo demás va en grupos desplegables: qué puedes eclosionar (por huevo: huevo + poción = mascota, nueva o para recuperar), mascotas que crecen (por la comida que les gusta: lo que necesitan y lo que te queda), tu comida, huevos y pociones, y tu colección por tipos (normales, de misión, mágicas, raras y especiales), con la tabla 9 × 10 de las normales. Los iconos se cargan de `habitica-assets.s3.amazonaws.com/mobileApp/images/` (los de la app de Android); si uno falla, se ve un icono propio.
- **Calendario**: mes de todos los hábitos o de uno; tocar un día abre su detalle (solo consulta).
- **Estadísticas**: con todos los hábitos, experiencia ganada por día, semana, mes o año (se guarda cada cambio de día en `habitica.xp`), a qué hora marcas las diarias (día de la semana × hora), color de cada tarea en Habitica (valor negativo o positivo), rachas actuales de Habitica, cumplimiento por dificultad, por mes, por semana y por día de la semana, ranking, comparación de hábitos o etiquetas, reparto por etiqueta, «Hábitos que van juntos» y cuadrícula anual. Con un hábito, su ficha: puntuación (como Loop), valor en Habitica a lo largo del tiempo, balance + / − en los hábitos con los dos botones, historial, calendario con números, mejores rachas, frecuencia y cumplimiento por día de la semana y por mes.
- **Tablas** ordenables y exportables a CSV (separador «;» y coma decimal): resumen, meses, semanas, días de la semana, etiquetas, rachas, registros y relaciones.
- **Ajustes**: conexión con Habitica (y hábitos anteriores que no vienen de Habitica, para archivarlos o borrarlos), apariencia, copias de seguridad, sincronización con el Gist y vaciar.
- **Ayuda**: uso del panel y guía para crear cada frecuencia en Habitica.
- En el móvil, barra inferior con Panel, Establo, Calendario, Estadísticas y «Más» (Tablas, Ajustes, Ayuda).

### Puntuación

Como en Loop: media móvil exponencial de lo cumplido. Cada día con obligación aporta 1 si se cumple y 0 si no (en los de cantidad, la parte cumplida). La vida media es de 13/√f días, siendo f las veces esperadas por día.

## Cumplimiento

- Días cumplidos entre días programados. No cuentan las pausas, los días anteriores al inicio ni hoy si aún no está hecho.
- Hábitos de cantidad (botón +): un día cumple si llega a 1 vez. «Evitar» (botón −): el día cumple si no se pulsó.

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

**Markdown:** títulos, notas, etiquetas y nombres se interpretan como en Habitica (markdown-it con enlaces automáticos y sus emojis `:nombre:`): negrita, cursiva, tachado, código, enlaces, imágenes (como enlace), entidades (`&amp;`…), escapes, títulos, listas, citas y código. El analizador es una adaptación reducida de markdown-it y linkify-it (MIT) y se comprobó contra `habitica-markdown` 4.1.0: 73 casos escritos a mano, 64 títulos y notas realistas y unas 30.000 cadenas aleatorias dan el mismo texto visible (solo cambia, en casos raros, cómo se codifica la dirección de algún enlace con caracteres no ingleses). Los nombres se guardan como texto limpio y se muestran con formato en el Panel, la ficha y las listas; nunca se inserta HTML del texto.

Solo se hacen lecturas: nunca se puntúa, nunca se llama a `POST /cron` ni se cambia nada en Habitica.

**Conectar:** habitica.com → icono de usuario → **Ajustes** → pestaña **API** (o `https://habitica.com/user/settings/api`): copia el **ID de usuario** y el **Token de la API** («Mostrar token de la API») y pégalos en el **Panel** → **Conectar**.

- El ID y el token se guardan **solo en el `localStorage` de ese dispositivo** (`habitos_v1_hab`): no entran en el estado, las copias, lo exportado ni el Gist. Cada petición lleva `x-client` (`<ID>-habitos`). Los nombres en español de huevos, pociones, comida y misiones (y la vida de cada jefe) se piden a `/content?language=es` y se guardan 30 días (`habitos_v1_habnames2`).
- Se importa al abrir la app, al volver a ella, cada 3 minutos y con «Importar ahora»: usuario, diarias, hábitos, tareas pendientes y grupo. Si Habitica limita las peticiones (429), se espera lo que indique `Retry-After`.
- **Todo se importa solo**: cada diaria y cada hábito nuevo crea su hábito aquí con su historial. Lo que se borra en Habitica queda archivado aquí con su historial; una diaria «en gris» (cada 0) se archiva y vuelve si se reactiva. El nombre, la programación y las etiquetas siguen a Habitica.
- En cada día que Habitica conoce, el registro queda como allí (marcado, desmarcado o con su número). Lo que había antes en la app (por ejemplo, de Loop) se conserva.
- **Diarias** → hábitos sí/no con la programación de Habitica: cada X días, días de la semana cada X semanas, días del mes o N-ésimo día de la semana cada X meses, y cada X años.
- **Hábitos** → «+» como cantidad (veces al día) y «−» como «Evitar» con las veces del día; los que tienen **+ y −** se importan como dos y su ficha añade el **balance + / −**.
- **Ánimo del día:** lo único que se anota en la app. A partir de `settings.moodHour` (20 por defecto) se abre una ventana con las cinco opciones y una nota corta (140 caracteres, admite emojis); si falta el día anterior, se pregunta primero por ese (solo desde el día en que se creó el estado). «Ahora no» pospone ese día una hora en este dispositivo (`habitos_v1_moodask`). Con `settings.mood` en falso no pregunta y se ocultan la estadística y la tabla del ánimo. Al pulsar un día del calendario del ánimo se ven el ánimo y la nota, y se pueden cambiar.
- **Personaje:** atributos con su desglose (nivel/2, puntos, equipo, bonus de clase ×2 del equipo de tu clase, buffs) y sus efectos según las fórmulas de Habitica (INT: +2,5 % de experiencia y 2 de maná máximo por punto; PER: +2 % de oro; CON: −0,4 % de vida perdida; FUE: críticos y daño al jefe); habilidades de la clase con sus cifras; buffs de hoy y los que pueden dar los compañeros según su clase y nivel.
- **Equipamiento:** mejor combinación entre las piezas que tienes para cada objetivo (arma a dos manos frente a una mano más mano secundaria) y la siguiente pieza de tu clase en la tienda si mejora la propuesta. Usa `items.gear` del usuario y `gear.flat` del contenido (guardado 30 días, junto con `spells`).
- **Misión:** escenario del jefe con la vida, el golpe pendiente (`party.quest.progress.up`), quién pega más, previsión y golpe a golpe a partir de los mensajes de sistema del chat del grupo (`GET /groups/party/chat`, tipo `boss_damage`); vida y clase de los compañeros con `GET /groups/party/members` cada 15 minutos.
- **Para vender (Establo):** huevos y pociones que ya no hacen falta para ninguna mascota ni montura, con el oro que da Habitica al venderlos (el `value` del contenido). Los huevos normales se reservan también para todas las pociones mágicas y raras que existen; lo que se podría vender si no se van a comprar más va aparte. Cada combinación compatible reserva 2 si no tienes ni mascota ni montura, 1 si tienes solo una de las dos (criar la mascota hasta montura obliga a volver a eclosionarla) y 0 si tienes las dos; las pociones raras (sin montura) reservan 1 si falta la mascota. Se cuentan siempre los huevos y pociones normales; los huevos de misión y las pociones mágicas o raras, si los tienes o ya tienes alguna de sus mascotas o monturas.
- **Alerta de vida baja:** banda fija arriba, en todas las pantallas, cuando la vida baja del umbral de Ajustes → Habitica (20 por defecto; 0 la apaga). Se guarda en `settings.hpAlert`.
- **Diarias con lista que hacen de cuota** (una diaria semanal, mensual, anual o cada N días con un solo día fijo y 2 o más elementos en la lista, como «Gimnasio: Día 1, Día 2, Día 3» los domingos): se importan como «N de la lista por semana/mes/año», con ciclos que van del día siguiente al anterior día fijo hasta el día fijo (incluido). Cuentan los elementos marcados en el ciclo (varios en un día suman todos); el ciclo se cumple al completar la lista o si la diaria se marca en Habitica (también si se marca hasta 3 días después del día fijo sin haber cerrado ese ciclo, o con «Registrar la actividad de ayer»). Habitica no guarda cuándo se marca cada elemento: se anota el día en que la app lo ve marcado (o el de la última modificación de la tarea, si es posterior a la importación anterior), en `habitica.checks`; los ciclos dados por hechos, en `habitica.done`. En los calendarios, el periodo cumplido va en claro y los días anotados en oscuro, más intenso cuantos más elementos; el día fijo de un ciclo no cumplido, en rojo. La ficha añade «Lista por ciclo». Las listas de un solo elemento siguen como diaria normal.
- **Historial:** cada marca de una diaria cuenta para el día que Habitica tenía abierto (zona horaria, inicio de día personalizado y cambios de día de `history.exp`); cada fallo, para el día que se cerró. Lo que Habitica ya comprimió en medias se guarda aparte (`habitica.history`) y se ve como puntos huecos en «Valor en Habitica».

## Publicación

Se sirve con GitHub Pages desde la rama `main`, carpeta `/ (root)`. Archivos: `index.html`, `sw.js`, `app.webmanifest`, `icon-192.png`, `icon-512.png`.

- El service worker descarga primero de internet (`no-store`) y solo usa la copia guardada sin conexión.
- **Si cambia `sw.js`, hay que subir antes el número de `CACHE`** (ahora `habitos-v1`).
- Para comprobar una publicación: abre la dirección en Chrome del PC, **F12** → pestaña **«Application»** → **«Cache Storage»** y mira que aparece el nombre de caché nuevo.

## Pruebas

Ganchos en `window.__habitos`: `state`, `normalizeState`, `normalizeItem`, `isDue`, `isScheduled`, `scoreSeries`, `scoreAt`, `relations`, `weekdayRates`, `buildTable`, `dayGlobal`, `habitDay`, `monthCompliance`, `globalCompliance`, `computeStreaks`, `computeStats`, `compliance`, `unitsOf`, `mergeStates`, `undo`, `exportData`, `parseNum`, `syncNow`, `fingerprint`, `habSync`, `habRt`, `stableInfo`, `pmStats`, `habAlerts`, `habSchedule`, `habDailyDays`, `habHabitDays`, `dueFixed`, `normSchedule`, `mark(id, fecha, valor)` (solo para pruebas), `setToday(fecha)` (fija «hoy») y `setState(json)` (escribe en IndexedDB y repinta). Con `?nosw` en la dirección no se registra el service worker.

## Privacidad y avisos

- La app no tiene servidor ni estadísticas de uso: los datos de cada persona se guardan en su navegador (IndexedDB `habitos_v1`). Solo salen hacia Habitica (lecturas con su ID y token) y, si se activa la sincronización, hacia su propio Gist secreto de GitHub, cifrado.
- El token de Habitica se guarda en `localStorage` (`habitos_v1_hab`), fuera de las copias y de los archivos exportados.
- La cabecera `X-Client` lleva el ID de usuario de Habitica del autor (`HAB_CREATOR_ID`) y `habitos`, como piden las normas de la API. Las importaciones automáticas (cada 10 minutos con la app a la vista, o al volver a ella si hace más de 5) espacian las llamadas 2,5 s.
- App gratuita y no oficial, sin relación con Habitica. Arte de Habitica con licencia CC BY-NC-SA 3.0 y código adaptado de markdown-it, linkify-it y markdown-it-emoji (MIT): véase [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).

