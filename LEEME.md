# sisnet-skills

Este repositorio está dedicado a gestionar todas las habilidades (skills) posibles que pueden interactuar con los datos y ficheros de Sisnet.

La estructura básica de carpetas solo incluye `.github/skills/` en el directorio de tu proyecto. Cada habilidad es una carpeta que contiene un archivo `SKILL.md` y, opcionalmente, scripts, ejemplos u otros recursos. Los miembros del equipo reciben las actualizaciones mediante el flujo de trabajo habitual de Git: clonar, hacer pull o fusionar una PR; no necesitan instalarla en su perfil personal.
```text
your-repo/
└── .github/
    └── skills/
        └── skill-name-1/
            ├── SKILL.md
            └── examples/
            ...
        └── skill-name-2/
            ├── SKILL.md
            └── examples/
```
Si una habilidad (skill) está pensada para funcionar con varios agentes de IA, considera usar `.agents/skills/`; VS Code admite ambas ubicaciones. Comprueba que los demás agentes que usa tu equipo admitan la misma ubicación y las mismas funciones.
