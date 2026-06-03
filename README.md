### 🏫 **Institución:** IES 9-018 "Gobernador Celso Jaque"
### 📚 **Carrera:** Tecnicatura Superior en Desarrollo de Software
### 👨‍🏫 **Profesor:** Paulo Alvarez
### 📅 **Año:** 2026

---

# 🎓 Andamiaje de Agentes IA para Desarrollo de Software

## ¿Qué es esto?

Un **método de trabajo con 2 prompts** que convierte a la IA en tu **equipo de desarrollo estructurado**, no en una caja mágica que escupe código.

**Objetivo pedagógico:** Que aprendas a orquestar agentes de IA con disciplina profesional, aplicando arquitectura hexagonal, DDD, y documentación viva. **No se trata de que la IA te haga el proyecto. Se trata de que vos dirijas el proceso.**

---

## 🧭 Flujo de Trabajo (2 Fases)

```
FASE 0 (SCOUTING)                    FASE 1 (CONSTRUCCIÓN)
┌──────────────────────┐            ┌──────────────────────────┐
│  Prompt 1            │            │  Prompt 2                │
│  "Definición y       │  ──────▶   │  "Andamiaje de           │
│   Acotamiento del    │            │   Agentes IA"            │
│   Proyecto"          │            │                          │
│                      │            │  Crea equipo de agentes  │
│  IA te entrevista    │            │  Genera estructura       │
│  Define alcance      │            │  Guía el desarrollo      │
│  Propone opciones    │            │  paso a paso             │
└──────────────────────┘            └──────────────────────────┘
```

### Paso a paso

1. **Leé** [`flujo-trabajo-github.md`](./flujo-trabajo-github.md) para entender cómo crear tu repo, usar ramas, commits y PRs
2. **Abrí tu terminal** con el CLI de IA que prefieras (opencode, gemini, kimi, etc.)
3. **Pegá el Prompt 1** → La IA te va a entrevistar para definir tu proyecto
4. Cuando la IA te diga *"¡Perfecto! Hemos definido claramente el proyecto"*, **copiá el resumen del proyecto** que te dio
5. **Pegá el Prompt 2** + el resumen → La IA orquesta agentes y genera toda la estructura
6. **Seguí las instrucciones** de los agentes para construir tu sistema

---

## 📁 Estructura del Repositorio

| Archivo | Contenido |
|---------|-----------|
| `README.md` | Esta guía (flujo de trabajo e instrucciones) |
| `flujo-trabajo-github.md` | **Guía de Git/GitHub**: crear repo, ramas, commits, push, PR, merge |
| `prompts/01-definicion-proyecto.md` | **Prompt 1**: Fase de scoping y definición |
| `prompts/02-andamiaje-agentes.md` | **Prompt 2**: Andamiaje universal de agentes IA (8 agentes) |
| `instalacion-herramientas-cli.md` | Guía de instalación de herramientas CLI (opencode, gemini, kimi, etc.) |

---

## 🔧 Herramientas CLI Recomendadas

Para usar estos prompts necesitás un asistente de IA por terminal. Las opciones que recomendamos:

| Herramienta | Instalación | Ventaja |
|-------------|-------------|---------|
| **opencode** | `npm install -g @anthropic-ai/opencode` | Open source, sin costo, ideal para educar |
| **Gemini CLI** | `npm install -g @google/gemini-cli` | Gratuito, integración Google |
| **Kimi CLI** | Via Moonshot AI | Buena relación calidad/precio |

> 📖 **Guía completa de instalación** → [`instalacion-herramientas-cli.md`](./instalacion-herramientas-cli.md)

---

## ⚠️ Regla de Oro

> **Un buen proyecto educativo es pequeño pero completo. Mejor un sistema simple bien hecho que uno grande y caótico.**

No le pidas a la IA que "te haga el proyecto". Usá estos prompts para que **orqueste un equipo de agentes** que trabaje de forma estructurada bajo tu dirección.

---

## 🔗 Repositorios Relacionados

| Materia | Repo |
|---------|------|
| Arquitectura y Diseño de Interfaces | [IES9018/proyecto-adi-2026](https://github.com/IES9018/proyecto-adi-2026) |
| Práctica Profesionalizante III | [IES9018/proyecto-pp3-2026](https://github.com/IES9018/proyecto-pp3-2026) |
| Programación III (WebSocket/MQTT) | [IES9018/laboratorio-websocket-mqtt-2026](https://github.com/IES9018/laboratorio-websocket-mqtt-2026) |
| Modelado de Software 2025 | [IES9018/proyecto-modelado-2025](https://github.com/IES9018/proyecto-modelado-2025) |
