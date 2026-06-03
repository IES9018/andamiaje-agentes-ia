### 🏫 **Institución:** IES 9-018 "Gobernador Celso Jaque"
### 📚 **Carrera:** Tecnicatura Superior en Desarrollo de Software
### 👨‍🏫 **Profesor:** Paulo Alvarez
### 📅 **Año:** 2026

---

# 🐙 Flujo de Trabajo con Git y GitHub — Guía del Estudiante

> **Objetivo:** Que aprendas a trabajar con control de versiones como un profesional, permitiendo que tu docente pueda hacer seguimiento de tu progreso, darte feedback y evaluar tu trabajo.

---

## 🧭 Mapa General del Flujo

```
CREAR REPO  →  CLONAR  →  RAMA  →  TRABAJAR  →  COMMIT  →  PUSH  →  PR (entrega)
    ↓            ↓         ↓         ↓           ↓         ↓         ↓
  GitHub      Local    feature/   Editar,    Guardar   Subir a   Solicitar
 (tu cuenta)          agente-01  diseñar,   cambios   GitHub    revisión
                                  codear
```

Cada vez que termines un agente del andamiaje, repetís: **RAMA → TRABAJAR → COMMIT → PUSH → PR**.

---

## 1. Crear tu Repositorio en GitHub

### Opción A: En tu cuenta personal (recomendada para este andamiaje)

Cada estudiante construye un sistema distinto. No hay un repo base para forkear. Creás **tu propio repositorio** con el nombre de tu proyecto.

```bash
# 1. Entrá a GitHub → botón "+" → "New repository"
# 2. Nombre: el nombre de tu sistema (ej: sistema-gestion-biblioteca)
# 3. Visibilidad: Public
# 4. NO marques "Add a README file" (lo creamos nosotros)
# 5. NO marques .gitignore ni licencia
# 6. Click "Create repository"
```

```bash
# Con GitHub CLI (más rápido):
gh repo create sistema-gestion-biblioteca --public --clone
```

### Opción B: Fork del repositorio base (si el docente lo indica)

Si tu materia ya tiene un repo base en `IES9018`, hacés fork:

```bash
gh repo fork IES9018/proyecto-adi-2026 --clone=true
```

### 📋 Dato clave para el docente

Apenas crees tu repo, **pasale el link a tu profesor** para que lo agregue a la lista de seguimiento. El formato esperado es:

```
https://github.com/TU-USUARIO/nombre-de-tu-sistema
```

**Ejemplo:**
```
https://github.com/LL1121/sistema-gestion-biblioteca
```

---

## 2. Configuración Inicial (se hace una sola vez)

Después de clonar tu repo, configuralo:

```bash
cd nombre-de-tu-sistema

# Configurar tu identidad (si no lo hiciste antes)
git config user.name "Tu Nombre"
git config user.email "tu@email.com"

# Crear .gitignore (fundamental)
cat > .gitignore << 'EOF'
# Python
__pycache__/
*.py[cod]
*.egg-info/
venv/
.env

# Node
node_modules/

# IDE
.vscode/
.idea/

# OS
.DS_Store
Thumbs.db

# Archivos grandes / binarios
*.exe
*.dll
*.so
*.dylib

# Secrets (¡nunca subas claves!)
.env
*.pem
secrets.yaml
EOF

# Primer commit de seguridad
git add .gitignore
git commit -m "chore: configuración inicial del repositorio"
git push -u origin main
```

---

## 3. Estrategia de Ramas

### ¿Cuándo crear una rama nueva?

| Situación | Rama |
|-----------|------|
| Iniciás un agente nuevo del andamiaje | `feat/agente-01-analista` |
| Vas a implementar una funcionalidad | `feat/login-usuarios` |
| Corregís algo que ya entregaste | `fix/error-validacion-dni` |
| Documentación o README | `docs/actualizar-readme` |
| Experimentás una idea (sin romper main) | `experimento/nueva-ui` |

**Regla de oro:** `main` siempre debe compilar y estar limpia. Todo trabajo se hace en ramas.

### Crear y trabajar en una rama

```bash
# Asegurate de estar en main actualizada
git checkout main
git pull origin main

# Crear y moverte a la rama nueva
git checkout -b feat/agente-01-analista

# Verificar en qué rama estás
git branch   # La rama activa tiene un *
```

### ¿Por qué usar ramas?

- **No rompés lo que ya funciona.** Si te equivocás, volvés a `main` y empezás de nuevo.
- **El docente puede ver cada entrega por separado.** Cada rama = una unidad de trabajo.
- **Practicás el flujo real de la industria.** Nadie trabaja directo en `main`.

---

## 4. Commits: Cuándo y Cómo

### Frecuencia de commits

> **Hacé commits chicos y frecuentes.** Un commit = una idea atómica.

| Momento | Commit |
|---------|--------|
| Terminaste un archivo de requisitos | `git commit -m "docs: requisitos funcionales del sistema"` |
| Agregaste el diagrama de clases | `git commit -m "docs: diagrama de clases UML"` |
| Implementaste una función | `git commit -m "feat: endpoint POST /usuarios"` |
| Arreglaste un bug | `git commit -m "fix: validación de email vacío"` |
| Actualizaste el README | `git commit -m "docs: instrucciones de instalación"` |

### Formato de mensajes (Conventional Commits)

Usamos el estándar **Conventional Commits** que usan las empresas:

```
<tipo>: <descripción breve en presente>

[opcional: cuerpo explicando el por qué del cambio]
```

**Tipos de commit:**

| Prefijo | Cuándo usarlo |
|---------|---------------|
| `feat:` | Nueva funcionalidad o archivo de diseño |
| `fix:` | Corrección de un error |
| `docs:` | Documentación (README, comentarios, diagramas) |
| `chore:` | Tareas de mantenimiento (.gitignore, config) |
| `refactor:` | Mejora de código sin cambiar funcionalidad |
| `test:` | Agregar o modificar tests |
| `style:` | Cambios de formato (espacios, comas) |

**Ejemplos reales:**

```bash
# ✅ BUENOS commits
git commit -m "feat: agrega endpoint de login con JWT"
git commit -m "fix: corrige error 500 cuando el DNI está vacío"
git commit -m "docs: agrega ADR-003 sobre elección de SQLite"
git commit -m "refactor: extrae lógica de validación a modulo separado"

# ❌ MALOS commits (no hagas esto)
git commit -m "cambios"
git commit -m "arreglos varios"
git commit -m "asdfgh"
git commit -m "version final final 2 definitiva"
```

### Commit de seguridad antes de cada push

Antes de subir a GitHub, hacé un **commit de seguridad** con todo lo pendiente:

```bash
# Ver qué archivos cambiaron
git status

# Agregar todo lo nuevo y modificado
git add .

# Commit descriptivo de lo que hiciste en esta sesión
git commit -m "feat: completa agente 01 - requisitos funcionales y stakeholders"
```

---

## 5. Push: Subir tu Trabajo a GitHub

```bash
# La primera vez que subís una rama nueva
git push -u origin feat/agente-01-analista

# Las siguientes veces (ya está vinculada)
git push
```

**¿Cada cuánto hacer push?**
- Al terminar una sesión de trabajo (aunque no esté completo)
- Al finalizar un agente del andamiaje
- **Nunca te vayas a dormir sin haber hecho push.** Tu computadora puede fallar; GitHub no.

---

## 6. Pull Request (PR): La Entrega Formal

El PR es cómo le decís al docente: *"Terminé este agente, revisá mi trabajo"*.

### Crear un PR

```bash
# Con GitHub CLI (recomendado)
gh pr create \
  --base main \
  --head feat/agente-01-analista \
  --title "Agente 01: Análisis de Requisitos" \
  --body "## Qué hice
- Entrevista con el agente analista
- Documento de requisitos funcionales y no funcionales
- Identificación de stakeholders

## Archivos generados
- 00_REFERENCIAS/requisitos.md
- 00_REFERENCIAS/stakeholders.md

## Decisiones clave
- Se priorizó autenticación JWT sobre sesiones por ser stateless
- Se descartó búsqueda full-text por complejidad innecesaria"
```

### Ciclo de revisión

```
   Tú creás PR  →  Docente revisa  →  Feedback  →  Corregís  →  Docente aprueba  →  Merge
       ↑                                                           ↓
       └─────────── Nuevos commits en la misma rama ───────────────┘
```

**Importante:** No cierres el PR para hacer correcciones. Hacé nuevos commits en la misma rama y el PR se actualiza solo.

```bash
# El docente te pidió cambios. Corregís en la misma rama:
git checkout feat/agente-01-analista
# ... editás los archivos ...
git add .
git commit -m "fix: incorpora feedback del docente sobre stakeholders"
git push
# El PR se actualiza automáticamente
```

### Merge: cuándo y cómo

**Solo hacés merge cuando el docente lo aprueba.**

```bash
# Opción 1: Merge desde la interfaz de GitHub (recomendado)
# El botón verde "Merge pull request" en la página del PR

# Opción 2: Merge local
git checkout main
git pull origin main
git merge feat/agente-01-analista
git push origin main
```

---

## 7. Flujo Completo por Agente (Resumen)

Este es el ciclo que repetís con cada agente del andamiaje:

```bash
# 1. Volver a main limpia
git checkout main
git pull origin main

# 2. Crear rama para el agente
git checkout -b feat/agente-02-arquitecto

# 3. Trabajar con el agente IA (editar archivos, crear diagramas...)
# ...

# 4. Commit de seguridad al terminar la sesión
git add .
git commit -m "feat: completa agente 02 - visión arquitectónica y ADRs"

# 5. Push
git push -u origin feat/agente-02-arquitecto

# 6. Abrir PR para que el docente revise
gh pr create \
  --base main \
  --title "Agente 02: Arquitectura de Solución" \
  --body "## Qué hice
- Diagrama de contexto C4
- 3 ADRs documentados
- Arquitectura hexagonal definida

## Archivos
- 03_ARQUITECTURA/diagramas/c4-contexto.md
- 03_ARQUITECTURA/adr/ADR-001-stack.md
- 03_ARQUITECTURA/hexagonal.md"
```

---

## 8. Errores Comunes y Cómo Evitarlos

| Error | Consecuencia | Cómo lo evito |
|-------|-------------|---------------|
| Trabajar directo en `main` | Mezclás todo, perdés trazabilidad | **Siempre** creá una rama antes de tocar código |
| Commits gigantes con 30 archivos | Imposible saber qué cambió y por qué | Hacé commits chicos y frecuentes |
| No pushear por días | Si se rompe tu PC, perdiste todo | Push al final de cada sesión |
| Subir el `.env` o claves API | Vulnerabilidad de seguridad | Verificá que `.env` esté en `.gitignore` |
| Usar `git push --force` | Borrás trabajo de otros | **Nunca** uses `--force` sin preguntar al docente |
| Commits con mensajes vacíos o "varios" | El docente no entiende tu progreso | Usá Conventional Commits |
| Cerrar PR y abrir otro para corregir | Se pierde el hilo de la conversación | Corregí en la misma rama, el PR se actualiza solo |

---

## 9. Comandos de Supervivencia

```bash
# ¿En qué rama estoy y qué cambié?
git status

# ¿Qué commits tengo sin pushear?
git log origin/main..HEAD --oneline

# Ver historial de commits (bonito)
git log --oneline --graph --all

# Deshacer cambios en un archivo (volver al último commit)
git checkout -- nombre-archivo.md

# Deshacer el último commit (manteniendo los cambios en archivos)
git reset --soft HEAD~1

# ¿Me olvidé de algo en el último commit?
git add archivo-olvidado.md
git commit --amend -m "feat: mensaje corregido"

# Ver diferencias con lo último commiteado
git diff

# Traer cambios de GitHub (si trabajás en dos PCs)
git pull origin main
```

---

## 10. Checklist Antes de Cada Entrega (PR)

Antes de abrir un PR, revisá:

- [ ] ¿Estoy en la rama correcta? (`git branch`)
- [ ] ¿Hice commit de todo? (`git status` no muestra nada pendiente)
- [ ] ¿El mensaje del último commit es descriptivo?
- [ ] ¿Hice push? (`git log origin/main..HEAD --oneline` no muestra nada)
- [ ] ¿No subí archivos `.env`, claves, ni binarios?
- [ ] ¿El PR tiene un título claro y una descripción de lo que hice?
- [ ] ¿Linkeé el PR en el issue o canal que corresponda?

---

**Regla final:** El historial de Git cuenta la historia de tu proyecto. Si el docente puede leer tus commits y entender qué hiciste, cuándo y por qué, vas por buen camino.
