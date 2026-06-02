# 🔧 Instalación de Herramientas CLI para Agentes IA

Guía paso a paso para instalar asistentes de IA por terminal en Windows (WSL/Ubuntu).

---

## 📋 Requisitos Previos

### 1. WSL (Windows Subsystem for Linux)

Si usás Windows, necesitás WSL para correr Ubuntu:

```powershell
# En PowerShell como Administrador
wsl --install -d Ubuntu
```

Reiniciá la PC y configurá tu usuario de Ubuntu cuando te lo pida.

### 2. Node.js y npm

La mayoría de los CLI de IA se instalan con npm:

```bash
# En Ubuntu/WSL
curl -fsSL https://deb.nodesource.com/setup_22.x | sudo -E bash -
sudo apt-get install -y nodejs

# Verificar instalación
node --version   # Debe mostrar v22.x.x
npm --version    # Debe mostrar 10.x.x
```

### 3. Git

```bash
sudo apt update && sudo apt install git -y
git --version
```

### 4. GitHub CLI (opcional, recomendado)

```bash
# En Ubuntu/WSL
(type -p wget >/dev/null || sudo apt-get install wget -y) &&
sudo mkdir -p -m 755 /etc/apt/keyrings &&
wget -qO- https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo tee /etc/apt/keyrings/githubcli-archive-keyring.gpg > /dev/null &&
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null &&
sudo apt update &&
sudo apt install gh -y

# Autenticarse
gh auth login
```

---

## 🤖 Herramientas de Agentes IA

### Opción 1: OpenCode (Recomendada) ⭐

**Open source, gratuita, sin costo de API.** Funciona con modelos gratuitos incluidos o podés conectar tu propia API key.

```bash
# Instalación rápida (Linux/macOS/WSL)
curl -fsSL https://opencode.ai/install | bash

# O con npm
npm install -g @anthropic-ai/opencode

# Verificar
opencode --version
```

**Primer uso:**
```bash
# Iniciar opencode en tu proyecto
cd mi-proyecto
opencode

# Para pegar un prompt grande, escribí /paste o simplemente
# copiá y pegá el texto directamente en la terminal
```

**Ventajas educativas:**
- 100% open source → los estudiantes pueden ver cómo funciona
- Modelos gratuitos incluidos → nadie paga API keys
- Ideal para aprender sin depender de suscripciones

---

### Opción 2: Gemini CLI (Google)

CLI oficial de Google para interactuar con modelos Gemini.

```bash
# Instalación global con npm
npm install -g @google/gemini-cli

# Verificar
gemini --version

# Autenticarse (necesitás API key gratuita de Google AI Studio)
# 1. Andá a https://aistudio.google.com/apikey
# 2. Creá una API key
# 3. Configurala:
export GEMINI_API_KEY="tu-api-key"

# También podés guardarla en ~/.bashrc para que persista:
echo 'export GEMINI_API_KEY="tu-api-key"' >> ~/.bashrc
source ~/.bashrc
```

**Ventajas:**
- Gratuito (Google AI Studio da cuota gratuita generosa)
- Modelo Gemini 2.5 Flash/Pro muy bueno para código
- Extensión oficial para VS Code disponible

---

### Opción 3: Kimi CLI (Moonshot AI)

Kimi es un asistente de IA desarrollado por Moonshot AI. Para usarlo en terminal Ubuntu/WSL:

```bash
# Instalación (verificar en https://kimi.moonshot.cn para CLI oficial)
# Si usás Docker:
docker pull moonshotai/kimi-cli

# O con npm (si está disponible):
npm install -g kimi-cli

# Configurar API key
export KIMI_API_KEY="tu-api-key"
```

> ⚠️ **Nota para el docente**: Verificar la URL oficial de instalación del CLI de Kimi en [kimi.moonshot.cn](https://kimi.moonshot.cn). La disponibilidad del CLI puede variar según la región.

---

### Opción 4: GitHub Copilot en Terminal

Si ya tenés cuenta de GitHub con Copilot habilitado:

```bash
# Instalar extensión de GitHub Copilot para CLI
gh extension install github/gh-copilot

# Usar
gh copilot explain "git status"
gh copilot suggest "cómo hago un servidor web simple en Python"
```

---

## 🧪 Verificación Rápida

Después de instalar cualquier herramienta, probala:

```bash
# opencode
echo "Hola, explicame en una línea qué es un API REST" | opencode

# gemini
echo "Hola, explicame en una línea qué es un API REST" | gemini

# copilot
gh copilot explain "explicame qué es un API REST"
```

---

## 📂 Configurar el Entorno de Trabajo

Armá una carpeta para tus proyectos educativos:

```bash
mkdir -p ~/desarrollo-software/andamiaje
cd ~/desarrollo-software/andamiaje

# Iniciá tu herramienta preferida:
opencode   # o: gemini, kimi, etc.
```

Y pegá el **Prompt 1** para empezar.

---

## ❓ Problemas Comunes

| Problema | Solución |
|----------|----------|
| `npm: command not found` | Instalar Node.js (ver sección 2) |
| `wsl: command not found` | Instalar WSL desde PowerShell Admin |
| Error de API key | Verificar que la variable de entorno esté exportada |
| Error de permisos con npm global | Usar `npx` o instalar con `--user` |

---

## 🔗 Referencias

| Herramienta | Docs oficiales |
|-------------|---------------|
| OpenCode | [opencode.ai/docs](https://opencode.ai/docs) |
| Gemini CLI | [github.com/google-gemini/gemini-cli](https://github.com/google-gemini/gemini-cli) |
| Kimi | [kimi.moonshot.cn](https://kimi.moonshot.cn) |
| GitHub Copilot CLI | [docs.github.com/copilot](https://docs.github.com/en/copilot) |
