# REGLAS SAGRADAS GLOBALES DE COMUNICACIÓN CON ÁLVARO AVACA (OBLIGATORIAS EN TODO PROYECTO, AGENTE Y CONVERSACIÓN)

1. **Lectura en Voz Alta Automática con Identificación Obligatoria de Proyecto y Sesión (`[Proyecto + Sesión]` con voz `Paulina`, sin segundo turno):**
   - **Álvaro NO lee los mensajes en pantalla y mantiene múltiples proyectos y sesiones abiertos al mismo tiempo** (ej. `Agentes de IA`, `EidenERP`, `Eiden-Ecosystem`, `Conciliaciones`, `Conciliaciones Empresas`, etc.).
   - Por regla global absoluta de este computador y de la Casa de Software, **TODA lectura en voz alta DEBE empezar identificando el Nombre del Proyecto y la Sesión o Agente que está hablando**, para que Álvaro sepa de inmediato qué ventana le habla y a quién contestarle:
     - Formato obligatorio al inicio del audio: **`"Desde el proyecto ValorizadorXML, sesión [Nombre del Agente o Tema de la Sesión]: Álvaro, ..."`** (o **`"Habla [Agente/Sesión] desde el proyecto ValorizadorXML: Álvaro, ..."`**).
   - Antes de terminar **cada turno**, ejecuta siempre con `IsDaemon: false` (termina en 10ms, inyecta automáticamente `[Proyecto + Sesión]` si faltara, y deja `say` corriendo desacoplado sin disparar un segundo turno):
     ```bash
     killall say 2>/dev/null || true; node -e 'const path=require("path"),{spawn}=require("child_process"),p="ValorizadorXML",s=process.env.EIDEN_SESSION_ID||process.env.EIDEN_SESSION_NAME||"Casa de Software",m=process.argv[1]||"";const txt=/^(desde el proyecto|habla )/i.test(m)?m:`Desde el proyecto ${p}, sesión ${s}: ${m}`;spawn("say",["-v","Paulina","-r","185",txt],{detached:true,stdio:"ignore"}).unref()' "Desde el proyecto ValorizadorXML, sesión Casa de Software: Álvaro, resumen claro en español chileno..."
     ```
   - Alternativa directa mediante el CLI global de la Casa de Software (`IsDaemon: false`):
     ```bash
     ~/.arnes-factory/bin/arnes say "Álvaro, resumen claro en español chileno..." --project "ValorizadorXML" --session "Casa de Software"
     ```
2. **Idioma Estricto:**
   - **Con Álvaro (el dueño):** 100% en **español chileno claro, directo, conciso y pensado para ser escuchado**, sin jerga técnica innecesaria.
   - **Entre agentes internos, código y logs:** 100% en **inglés técnico** para máxima precisión y ahorro de tokens.
3. **Preguntas Interactivas (Una a la vez):**
   - Cuando necesites definir algo con Álvaro, haz **una sola pregunta clara a la vez**, leyéndosela también en voz alta con la identificación `[Proyecto + Sesión]` al inicio.
4. **Arquitectura `ZERO_HARNESS_IN_PRODUCT_REPOS` (El Arnés NUNCA se sube a los repositorios de productos):**
   - **En los repositorios de aplicaciones/proyectos (`AlvaroAvaca/*`) JAMÁS se debe guardar ni subir el Arnés** (`.eiden/`, `.agents/`, `.claude/`, `.arnes/`, `eiden_software_factory/` deben estar siempre en `.gitignore` y fuera de `git status`). Al repositorio del producto solo se envía la aplicación y los archivos puntero `GEMINI.md` y `AGENTS.md`.
   - **El Arnés vive única y exclusivamente en `https://github.com/AlvaroAvaca/casa-de-software.git` (`main`).**
   - Siempre que un proyecto lo necesite (o al clonar/abrir cualquier repositorio), el agente debe descargarlo o actualizarlo directamente desde allí ejecutando autónomamente:
     ```bash
     if [ ! -x "$HOME/.arnes-factory/bin/arnes" ]; then curl -fsSL https://raw.githubusercontent.com/AlvaroAvaca/casa-de-software/main/install.sh | bash; else "$HOME/.arnes-factory/bin/arnes" self-update; fi && "$HOME/.arnes-factory/bin/arnes" install "$(pwd)"
     ```

Read and follow [AGENTS.md](AGENTS.md) for project rules of ValorizadorXML.
