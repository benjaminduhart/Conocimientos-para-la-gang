# Guía Práctica de Obsidian — Sin vueltas

> Esto no es un manual de 300 páginas. Es lo que de verdad usamos a diario para no perdernos y trabajar rápido. Si algo no lo entiendes, pregunta en el grupo o a un administrador.

---

## 1. Lo mínimo que necesitas saber para no perderte

### 1.1 Los tres paneles que ves al abrir

```
+------------------+--------------------------+------------------+
|   EXPLORADOR     |       NOTA ABIERTA       |     PANEL DERECHO  |
|   (carpetas)     |       (editas aquí)      |   (opcional)      |
+------------------+--------------------------+------------------+
```

- **Izquierda:** tus carpetas y archivos. Si no lo ves, pulsa `Ctrl + Shift + E`.
- **Centro:** donde escribes y lees notas.
- **Derecha:** vista previa de enlaces salientes, backlinks, outline de la nota, tags... Aparece al pulsar `Ctrl + Shift + L`.

### 1.2 Modo edición vs modo lectura

- `Ctrl + E` — cambia entre **editar** (escribes markdown crudo) y **leer** (lo ves bonito renderizado).
- También puedes pinchar el icono del libro/lápiz arriba a la derecha.

### 1.3 Abrir rápido cualquier nota

`Ctrl + O` → escribes parte del nombre → Enter. No navegues carpetas como en Windows, esto es mucho más rápido.

### 1.4 La paleta de comandos (tu mejor amiga)

`Ctrl + P` → te sale un buscador donde escribes lo que quieres hacer: "insertar plantilla", "mover nota", "abrir vista de gráfico"... Con el tiempo no tocas menús.

---

## 2. Escribir en Markdown sin sufrir

Markdown es texto plano con símbolos sencillos. Aquí tienes lo esencial:

| Lo que quieres     | Cómo se escribe               | Atajo de teclado                         |
| ------------------ | ----------------------------- | ---------------------------------------- |
| **Negrita**        | `**texto**`                   | `Ctrl + B`                               |
| *Cursiva*          | `*texto*`                     | `Ctrl + I`                               |
| `código en línea`  | `` `código` ``                | —                                        |
| Bloque de código   | ````` ```python <Enter> ````` | —                                        |
| Título nivel 1     | `# Título`                    | —                                        |
| Título nivel 2     | `## Subtítulo`                | —                                        |
| Título nivel 3     | `### Sección`                 | —                                        |
| Lista con puntos   | `- elemento`                  | —                                        |
| Lista numerada     | `1. elemento`                 | —                                        |
| Checkbox           | `- [ ] tarea`                 | —                                        |
| Cita               | `> texto citado`              | —                                        |
| Línea horizontal   | `---`                         | —                                        |
| Enlace web         | `[texto](url)`                | `Ctrl + K`                               |
| Enlace a otra nota | `[[Nombre de la Nota]]`       | —                                        |
| Imagen             | `![[imagen.png]]`             | (arrastra la imagen desde el explorador) |

> **Tip ninja:** Escribe `---` al principio de una nota para añadir metadatos YAML (tags, fecha, autor). Lo llamamos "frontmatter":
>
> ```yaml
> ---
> tags: [plc, siemens, tia portal]
> fecha: 2026-07-27
> autor: Ivan
> ---
> ```

---

## 3. Organización dentro de Obsidian

### 3.1 La estructura de carpetas ya está pensada

```
Conocimientos Coleguis/
└── Carpeta Conocimientos 2026/
    ├── automacion/
    │   ├── plc/
    │   └── scada/
    ├── electronica/
    ├── mecanica/
    ├── telecom/
    └── computing/
        ├── py/
        └── redes/
```

No te compliques. Si tu nota es sobre PLC Siemens, ponla en `automacion/plc/`. Si no existe la subcarpeta, créala con `Ctrl + Shift + N` (nueva carpeta) desde el explorador.

### 3.2 Tags: el pegamento invisible

Al final de cada nota (o en el frontmatter YAML), pon etiquetas para cruzar temas:

```markdown
## Tags
#plc #siemens #mantenimiento #tiaportal
```

Luego puedes buscar cualquier tag desde la búsqueda (`Ctrl + Shift + F`) escribiendo `tag:#plc`.

**Convención de tags que usamos:**

- `#area_grande` → `#plc`, `#python`, `#electronica`, `#mecanica`, `#telecom`, `#redes`
- `#tipo_contenido` → `#tutorial`, `#solucion`, `#datasheet`, `#script`, `#teoria`
- `#nivel` → `#basico`, `#intermedio`, `#avanzado`

### 3.3 Backlinks (o "quién me enlaza a mí")

Abre el panel derecho (`Ctrl + Shift + L`) y mira la pestaña **Backlinks**. Te muestra todas las notas que enlazan a la que tienes abierta. Es magia: entiendes cómo se conecta el conocimiento sin hacer nada extra.

### 3.4 El gráfico de conocimiento

`Ctrl + G` → ves un mapa de bolitas y líneas. Cada bolita es una nota, cada línea es un enlace `[[...]]`. No sirve para trabajar, pero es bonito y te da perspectiva de cómo crece el cerebro.

---

## 4. Técnicas de trabajo que ahorran horas

### 4.1 Notas atómicas (una idea = una nota)

No hagas una nota de 20 páginas titulada "Todo PLC". Mejor trocea:

- `siemens_primeros_pasos.md`
- `siemens_bloques_ob_fc_fb.md`
- `siemens_comunicacion_profinet.md`
- `siemens_recetas_hmi.md`

Cada nota resuelve **un solo problema**. Luego las enlazas entre sí con `[[...]]`. Cuando vuelvas en 6 meses a buscar cómo hacer recetas en un HMI Siemens, irás directo a la nota justa sin tragarte 18 páginas.

### 4.2 MOCs (Maps of Content) — Tu índice personal

Un MOC es una nota que solo contiene enlaces a otras notas sobre un mismo tema. Es como la tabla de contenidos de un libro:

```markdown
# MOC — PLC Siemens

## Primeros pasos
- [[siemens_primeros_pasos]]
- [[instalar_tia_portal]]

## Programación
- [[siemens_bloques_ob_fc_fb]]
- [[siemens_datos_estructurados_udt]]

## Comunicación
- [[siemens_comunicacion_profinet]]
- [[siemens_opc_ua]]
```

Ya tenemos el `Mapa de Navegación (General).md`, pero puedes crear MOCs para temas concretos cuando sientas que crecen mucho.

### 4.3 Plantillas (templates)

Si siempre empiezas tus notas con la misma estructura, crea una plantilla:

1. Crea una carpeta `_templates/` (si no existe).
2. Dentro, crea una nota llamada `nota-estandar.md` con esto:

   ```markdown
   ---
   tags: []
   fecha: {{date}}
   autor: 
   ---

   # {{title}}

   ## Contexto
   ¿Qué problema resuelve esto?

   ## Desarrollo

   ## Tags
   #pendiente

   ## Relacionado
   ```

3. Ve a Ajustes → Plantillas → carpeta de plantillas → `_templates/`.
4. Cuando crees una nota nueva, `Ctrl + P` → "Insertar plantilla" → elige la tuya. El `{{title}}` y `{{date}}` se rellenan solos.

> **Tip:** También puedes habilitar el plugin "Templates" (viene de serie en Obsidian, solo actívalo en Ajustes → Plugins principales).

### 4.4 Captura rápida: no pierdas ideas

- `Ctrl + N` — crea nota nueva al instante. Escribe la idea aunque sea un borrador. Ya la pulirás luego.
- Si estás en otra nota y se te ocurre algo que merece su propia nota, escribe `[[Nombre de la Nueva Nota]]`, luego haz `Ctrl + Click` sobre el enlace y se crea sola.

### 4.5 Búsqueda avanzada

`Ctrl + Shift + F` y luego puedes afinar:

| Búsqueda | Resultado |
|----------|-----------|
| `tag:#plc` | Todas las notas con ese tag |
| `path:automacion` | Solo notas dentro de la carpeta automacion |
| `file:.py` | Solo archivos Python |
| `line:("def "` | Notas que contengan "def " en alguna línea |
| `tag:#plc path:automacion` | Combina filtros |

---

## 5. Atajos de teclado imprescindibles (póntelos de fondo de pantalla un par de días)

| Atajo                              | Acción                                                   |
| ---------------------------------- | -------------------------------------------------------- |
| `Ctrl + O`                         | Abrir nota rápidamente                                   |
| `Ctrl + P`                         | Paleta de comandos                                       |
| `Ctrl + N`                         | Nueva nota                                               |
| `Ctrl + Shift + N`                 | Nueva carpeta                                            |
| `Ctrl + E`                         | Cambiar edición / lectura                                |
| `Ctrl + Shift + E`                 | Mostrar/ocultar explorador                               |
| `Ctrl + Shift + F`                 | Buscar en todas las notas                                |
| `Ctrl + F`                         | Buscar dentro de la nota actual                          |
| `Ctrl + H`                         | Buscar y reemplazar dentro de la nota                    |
| `Ctrl + K`                         | Insertar enlace web                                      |
| `Ctrl + G`                         | Abrir gráfico de conocimiento                            |
| `Ctrl + Shift + L`                 | Mostrar/ocultar panel derecho (backlinks, outline, tags) |
| `Ctrl + W`                         | Cerrar pestaña actual                                    |
| `Ctrl + Tab`                       | Siguiente pestaña                                        |
| `Ctrl + Shift + Tab`               | Anterior pestaña                                         |
| `Ctrl + Click` en enlace `[[...]]` | Abrir esa nota en pestaña nueva                          |
| `Ctrl + Shift + Click` en enlace   | Abrir esa nota en panel dividido (modo split)            |

### Bonus: Modo zen (sin distracciones)

`Ctrl + Shift + E` (oculta explorador) + `Ctrl + Shift + L` (oculta panel derecho). Solo tú y la nota. Para volver, repites los atajos.

---

## 6. Plugins recomendados (todos gratuitos y de la comunidad)

Actívalos desde Ajustes → Plugins comunitarios → Explorar:

| Plugin | ¿Para qué sirve? |
|--------|------------------|
| **Dataview** | Convierte tus notas en una base de datos. Puedes hacer consultas tipo "muéstrame todas las notas con tag #plc ordenadas por fecha". Es magia negra útil. |
| **Calendar** | Calendario visual. Si creas notas diarias, las ves en un calendario. |
| **Excalidraw** | Dibuja esquemas, diagramas de bloques, croquis de cableado... todo dentro de Obsidian. Ideal para mantenimiento y automatización. |
| **Paste URL into selection** | Copias una URL, seleccionas un texto en la nota, `Ctrl + V` y se convierte en `[texto](url)` automáticamente. |
| **Tag Wrangler** | Renombra tags de forma masiva. Si pasas de `#Siemens` a `#siemens`, lo cambia en todas las notas a la vez. |
| **Note Refactor** | Seleccionas parte de una nota, `Ctrl + Shift + C`, y la extrae a su propia nota nueva dejando un enlace `[[...]]` en la original. Perfecto para atomizar notas largas. |

> **No instales 30 plugins de golpe.** Empieza con 1-2, domínalos y luego añade otro. Poco a poco.

---

## 7. Flujo de trabajo diario recomendado

```
ABRIR VAULT
    │
    ├─► Ctrl + P → "Abrir nota del día" (si usas daily notes)
    │
    ├─► ¿Vienes a buscar algo?
    │       └─► Ctrl + O → escribes el nombre → lees/consultas
    │
    ├─► ¿Vienes a aportar algo nuevo?
    │       └─► Ctrl + N → escribes → frontmatter + tags → guardas
    │
    ├─► ¿Vienes a mejorar algo que ya existe?
    │       └─► Ctrl + O → buscas la nota → editas → guardas
    │
    └─► Antes de cerrar:
            ├─► git pull (bajar cambios de otros)
            ├─► git add . && git commit -m "lo que hiciste"
            └─► git push (subir tus cambios)
```

---

## 8. Errores típicos de principiante (y cómo esquivarlos)

| Error | Solución |
|-------|----------|
| "No encuentro una nota que sé que existe" | Usa `Ctrl + O`, no navegues carpetas. La búsqueda difusa encuentra aunque escribas mal. |
| "Tengo 40 pestañas abiertas y no sé cuál es cuál" | `Ctrl + W` las cierra de una en una. O pincha con botón derecho en cualquier pestaña → "Cerrar todas las demás". |
| "Escribí un `[[enlace]]` y no se crea la nota" | Pulsa `Ctrl + Click` encima del enlace. La nota se crea automáticamente si no existía. |
| "Se me ha ido el formato y veo todo en crudo" | Has puesto Obsidian en modo edición. `Ctrl + E` para alternar. |
| "He borrado algo sin querer" | `Ctrl + Z` deshace. También puedes ir al historial de versiones del archivo con `Ctrl + P` → "Open file recovery". |
| "No sé qué tags ponerle a esta nota" | Pon solo 2-3. `#area` y `#tipo`. Ya refinarás luego. No te paralices por los tags. |
| "Mi nota es un desorden, ¿la borro?" | No la borres. Ponle un tag `#revisar` y ya la arreglarás cuando tengas tiempo. Una nota imperfecta publicada > una nota perfecta que no existe. |

---

## 9. Resumen en tres frases

1. **Busca con `Ctrl + O`, enlaza con `[[...]]`, etiqueta con `#tags`.**
2. **Una nota = una idea. Si crece, la troceas y enlazas.**
3. **No esperes a tenerlo perfecto. Escribe, enlaza, sube. Poco a poco.**

---

> Si algo de esta guía no te funciona o ves que falta algo, edítala sin miedo o avisa a los administradores. Este vault es de todos.
