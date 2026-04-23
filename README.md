# 🚀 VSCode Advanced Post-Clone Automation

Sistema de automatización avanzada para VSCode que detecta el tipo de proyecto, instala dependencias, configura el entorno y ejecuta tareas post-clone automáticamente.

## 📦 Archivos incluidos

```
.vscode/
├── tasks.json      # Tareas automatizadas (setup, test, lint, reset, docker)
├── settings.json   # Configuración del workspace
├── extensions.json # Extensiones recomendadas
├── launch.json     # Configuraciones de debug
└── .detected-type  # (generado) Tipo de proyecto detectado
```

## 🎯 Características

| Feature | Descripción |
|---------|-------------|
| 🔍 **Detección automática** | Identifica Node.js, Python, Go, Rust, .NET, Java, Flutter, PHP, Docker |
| 📦 **Instalación inteligente** | Instala dependencias según el tipo detectado |
| 📝 **Generación de .env** | Crea archivos de entorno desde templates o valores por defecto |
| 🔧 **Git hooks** | Configura pre-commit hooks automáticamente |
| 🧪 **Tests integrados** | Comando único para ejecutar tests según el proyecto |
| 🐳 **Docker ready** | Tareas para docker-compose build/up |
| 🧹 **Lint/Format** | Normaliza el código con herramientas específicas |
| 🔄 **Reset completo** | Elimina e reinstala todo desde cero |
| 🐞 **Debug configs** | Launch.json preconfigurado para múltiples lenguajes |

## 🚀 Uso

### Automático (al abrir la carpeta)
1. Copia la carpeta `.vscode` a tu proyecto
2. Abre el proyecto en VSCode
3. Aparecerá la notificación: *"Hay tareas de carpeta disponibles"*
4. Haz clic en **"Permitir"**
5. El setup se ejecutará automáticamente

### Manual
```bash
# Ctrl+Shift+P → Run Task → 🚀 Post-Clone: Setup Completo
```

### Scripts individuales disponibles
| Comando | Acción |
|---------|--------|
| `🚀 Post-Clone: Setup Completo` | Ejecuta todo el pipeline |
| `🔥 Reset completo` | Borra e reinstala dependencias |
| `🧹 Lint y Formatear` | Linter + formatter según proyecto |
| `🧪 Ejecutar Tests` | Tests específicos del proyecto |
| `🐳 Docker: Build y Up` | Construye y levanta contenedores |

## ⚙️ Personalización

### Modificar inputs
Edita `tasks.json` → sección `"inputs"` para cambiar:
- Tipos de proyecto disponibles
- Valores por defecto del .env
- Confirmaciones adicionales

### Agregar un nuevo tipo de proyecto
1. En `tasks.json`, busca `"🔍 Detectar Tipo de Proyecto"`
2. Agrega un nuevo `elseif` con la condición
3. En `"📦 Instalar Dependencias"`, agrega el caso en el `switch`
4. En `"🧪 Ejecutar Tests"`, agrega los comandos de test

### Desactivar ejecución automática
En `.vscode/settings.json`:
```json
"task.allowAutomaticTasks": "off"
```

## 🔗 Integración con el Wrapper PowerShell

Combínalo con el script `clone-and-open.ps1` para un flujo completo:

```powershell
# 1. Clona y abre
.\clone-and-open.ps1 -RepoUrl "https://github.com/user/repo"

# 2. VSCode detecta .vscode/tasks.json
# 3. Ejecuta setup automático al abrir
# 4. ¡Listo para desarrollar!
```

## 📋 Requisitos

- VSCode 1.80+
- PowerShell 5.1+ (Windows) o PowerShell Core 7+
- Git instalado
- SDKs/Runtimes según el proyecto (Node.js, Python, Go, etc.)

## 🛡️ Seguridad

- Las tareas automáticas requieren confirmación la **primera vez** que se ejecutan
- Nunca se ejecuta código no revisado sin tu permiso
- Los archivos `.env` generados nunca se commitean (gitignore implícito)
