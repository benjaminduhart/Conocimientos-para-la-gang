# Guía Rápida de Git y Formatos

> **Úsala como chuleta (cheat sheet).** Cuando tengas dudas, consulta primero esta guía y luego a los administradores.

---

## 1. Flujo básico de Git (paso a paso)

Cada vez que quieras subir cambios, sigue esta secuencia. **Hazlo poco a poco** y sin prisa.

### 1.1 Antes de empezar a editar (bajar lo último)

```bash
# Bajar los cambios que otros han subido
git pull
```

> **Tip:** Haz esto siempre antes de crear o modificar cualquier nota. Así evitas conflictos.

### 1.2 Después de editar (subir tus cambios)

```bash
# Ver qué has modificado
git status

# Añadir tus archivos al "paquete" de subida
git add "ruta/del/archivo.md"
# O si estás seguro de todo lo que cambiaste:
git add .

# Crear el "paquete" con un mensaje descriptivo
git commit -m "Añado nota sobre fuentes switching"

# Subir el paquete al repositorio
git push
```

### 1.3 Resumen visual del flujo

```
git pull  →  editas archivos  →  git status  →  git add .  →  git commit -m "..."  →  git push
```

### 1.4 Comandos de emergencia

| Situación | Comando |
|-----------|---------|
| Me equivoqué en el último commit (mensaje mal) | `git commit --amend -m "mensaje correcto"` |
| Quiero deshacer cambios locales en un archivo | `git checkout -- archivo.md` |
| No sé qué ramas hay | `git branch -a` |
| Quiero ver el historial | `git log --oneline` |
| Tengo un conflicto y no sé qué hacer | **Para y consulta con un administrador.** |

> **Regla de oro:** Si `git push` falla con error de "rejected", haz primero `git pull` y luego `git push` de nuevo. Si hay conflicto, pide ayuda.

---

## 2. Qué tipo de archivos subir (y cuáles no)

### 2.1 Formatos recomendados para el repositorio Git

| Formato | ¿Subirlo? | ¿Por qué? |
|---------|-----------|-----------|
| `.md` (Markdown) | **Sí, siempre** | Es texto plano, ligero, Git lo maneja genial. Es el formato estrella del vault. |
| `.txt` | **Sí** | Igual que `.md`, pero sin formato. Bien para logs o datos crudos. |
| `.csv` | **Sí** | Tablas y datos ligeros. Git los trackea bien. |
| `.py`, `.js`, `.c`, `.ino`, etc. (código) | **Sí** | Código fuente pequeño o scripts de apoyo. |
| `.json`, `.yaml`, `.xml` | **Sí** | Configuraciones o estructuras de datos. |
| `.png`, `.jpg`, `.svg` | **Sí, con moderación** | Diagramas, capturas de pantalla, esquemas. Intenta que no pesen más de 1-2 MB cada una. Comprime antes. |
| `.pdf` (datasheets, manuales) | **Sí, con moderación** | Si son inferiores a ~5 MB. Son binarios, Git no los gestiona tan bien, pero para documentación clave merece la pena. |
| `.zip`, `.rar`, `.7z` | **NO** | Mejor en Drive compartido (ver sección 3). |

### 2.2 Formatos que NO debes subir a Git

| Formato | ¿Por qué no? | Alternativa |
|---------|-------------|-------------|
| `.zip`, `.rar`, `.7z` grandes | Git no maneja bien binarios grandes. Hincha el repo y lo vuelve lento. | Sube a **Google Drive compartido** y pon un enlace en una nota `.md`. |
| `.exe`, `.dll`, `.bin` | Son ejecutables/binarios. Riesgo de seguridad y tamaño. | Drive compartido. |
| `.docx`, `.pptx`, `.xlsx` | Binarios pesados que Git no puede comparar. No aportan al vault. | Si es una nota, conviértela a `.md`. Si es un documento formal, Drive. |
| `.mp4`, `.avi`, `.mkv` (vídeos) | Demasiado pesados. | YouTube (no listado) o Drive. Enlaza desde `.md`. |
| Archivos de proyecto (`.eprj`, `.acda`, etc.) | Binarios grandes de software de automatización/CAD. | Drive con enlace en `.md`. |
| `.iso`, imágenes de disco | Peso enorme, inmanejable. | Drive. |

### 2.3 Regla nemotécnica

> **Texto plano y ligero → Git. Binario grande o ejecutable → Drive con enlace.**

---

## 3. Cómo organizar distintos formatos de apuntes y proyectos

### 3.1 Dentro del vault (Git)

Sigue la estructura de carpetas que ya existe en el proyecto:

```
Conocimientos Coleguis/
├── Mapa de Navegación (General).md
├── Bienvenido.md
├── Guía para Principiantes.md
└── Carpeta Conocimientos 2026/
    ├── automacion/
    │   ├── plc/
    │   │   ├── siemens_basics.md
    │   │   ├── siemens_basics_imagenes/   ← carpeta de imágenes de esa nota
    │   │   └── codesys_tips.md
    │   └── scada/
    ├── electronica/
    │   ├── fuentes/
    │   └── pcb/
    ├── computing/
    │   └── py/
    └── ...
```

**Reglas de organización:**

1. **Notas de texto** (`.md`) → van dentro de su carpeta temática.
2. **Imágenes** (`.png`, `.jpg`) de una nota → crea una subcarpeta `nombre-de-la-nota_imagenes/` al lado de la nota.
3. **Datasheets** (`.pdf`) → dentro de una carpeta `datasheets/` en el área correspondiente (ej: `electronica/datasheets/`).
4. **Código fuente suelto** (`.py`, `.js`, `.ino`) → dentro de una carpeta `scripts/` o `codigo/` en su área.
5. **Proyectos o programas muy grandes** (`.zip`, proyectos de TIA Portal, CAD, etc.) → **NO van en Git.** Van en Drive (ver sección siguiente).

### 3.2 Fuera del vault (Drive compartido): LOS GORDOS

Para archivos pesados o proyectos completos, usamos **Google Drive compartido** con esta estructura sugerida:

```
Drive Compartido "Conocimientos Gang"/
├── Proyectos de Automatización/
│   └── proyecto_horno_tia_v2.zip
├── CAD y Diseño Mecánico/
│   └── soporte_motor.step
├── Software y ISOs/
│   └── codesys_3.5_instalador.zip
├── Cursos y Vídeos/
│   └── curso_plc_avanzado.mp4
└── Documentación pesada/
    └── manual_completo_s7300.pdf
```

**Y dentro de una nota `.md` en el vault pones un enlace directo:**

```markdown
## Recursos externos
- Proyecto TIA Portal del horno: [descargar desde Drive](https://drive.google.com/...)
```

Así todo queda conectado: el vault es el **índice inteligente** y el Drive es el **almacén de pesados**.

---

## 4. ¿Subimos archivos ZIP de proyectos grandes al Drive compartido?

### Respuesta: **Sí, 100% recomendado. Drive es la mejor opción.**

### Argumentos:

| Factor | Git | Google Drive |
|--------|-----|--------------|
| **Tamaño máximo práctico** | ~100 MB (y ya sufre) | Ilimitado (hasta donde dé el espacio compartido) |
| **Velocidad de clonado** | Se degrada mucho con binarios grandes | Siempre rápida, descargas solo lo que necesitas |
| **Historial** | Cada binario se almacena completo en cada commit. El repo engorda para siempre aunque borres el archivo. | No mantiene historial automático de binarios, pero puedes versionar manualmente (`proyecto_v1.zip`, `proyecto_v2.zip`). |
| **Comparación (diff)** | Con binarios no puedes ver qué cambió entre versiones. | Irrelevante para zips. |
| **Colaboración simultánea** | Conflictos binarios = dolor de cabeza. | Descargas, trabajas, resubes con nuevo nombre de versión. |
| **Límite de plataformas** | GitHub: 100 MB por archivo, 1 GB por repo (recomendado). GitLab: 10 GB por repo. | Google Drive: 15 GB gratis por cuenta, ampliable. Drive compartido: según plan del workspace. |

### Tips de experto

1. **Nombra con versiones claras los ZIP en Drive:**
   - `proyecto_horno_tia_v1.0_2026-07-27.zip`
   - NUNCA subas `proyecto_final.zip`, `proyecto_final_v2.zip`, `proyecto_final_definitivo.zip`... es un clásico del caos.

2. **Pon siempre una nota `.md` puente en el vault:**
   - Explica qué contiene el ZIP, qué software necesitas para abrirlo, versión y fecha.
   - Pega el enlace de Drive.
   - Ejemplo:

   ```markdown
   # Proyecto Horno Rotativo - TIA Portal v17

   - **Archivo:** proyecto_horno_tia_v1.0_2026-07-27.zip (45 MB)
   - **Software:** TIA Portal v17 + WinCC
   - **Enlace:** [Abrir en Drive](https://drive.google.com/...)
   - **Autor:** Iván
   - **Notas:** Versión funcional con bloques de temperatura y PID ajustado.
   ```

3. **Comprime con `.zip` (no `.rar` ni `.7z`):**
   - ZIP lo abre cualquiera sin instalar nada extra en Windows, Mac y Linux. Evita fricción.

4. **No comprimas si no es necesario:**
   - Un STEP, un PDF de 200 MB o un ISO ya están optimizados. Comprimirlos a ZIP no ahorra casi nada y añade un paso extra.

5. **Si el proyecto es código fuente** (no binario compilado), considera usar Git directamente en su propio repositorio. Si es un proyecto de PLC/CAD/HMI binario, Drive sin dudarlo.

6. **Revisa permisos del Drive compartido:**
   - Asegúrate de que todos los de la gang tengan al menos acceso de **lectura**. Para editar, que sea por turnos o por copias locales para no pisarse.

---

## 5. ¿Tienes dudas?

- **Primero**, revisa esta guía, el `README.md` general y las `Reglas de Colaboración Horizontal`.
- **Segundo**, pregunta en el grupo de chat de la gang.
- **Tercero**, consulta directamente con los administradores del repositorio. Para eso estamos.

---

> **Poco a poco se construye un buen segundo cerebro. Mejor un commit pequeño hoy que un commit perfecto que nunca llega.**
