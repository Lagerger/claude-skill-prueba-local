# Skill `prueba-local` para Claude Code

Una skill sencilla para levantar proyectos web en `localhost`, verificar su funcionamiento básico y dejarlos disponibles para probar durante el desarrollo, sin realizar deploy.

## ¿Para qué sirve?

Durante el desarrollo es útil poder ver y probar el proyecto antes de publicarlo.

Esta skill le indica a Claude Code que:

- detecte la tecnología utilizada;
- revise los comandos reales del proyecto;
- instale dependencias solo si hace falta;
- levante el proyecto en localhost;
- compruebe errores básicos;
- informe la URL exacta;
- deje el servidor funcionando;
- no haga deploy.

## Qué significa localhost

`localhost` permite ejecutar y probar una aplicación en la propia computadora.

El proyecto puede:

- abrirse en el navegador;
- navegarse;
- recibir clics;
- probar formularios y recorridos;
- mostrar cómo funcionaría antes de publicarse.

Pero no está disponible públicamente en internet.

> Importante: aunque la interfaz sea local, el proyecto puede estar conectado a bases de datos, APIs o servicios reales. La skill revisa y advierte sobre esas conexiones antes de probar acciones sensibles.

## Instalación

### Opción 1: copiar la carpeta manualmente

Copiá esta carpeta:

```text
skills/prueba-local
```

dentro de la carpeta global de skills de Claude Code.

#### Windows

```text
C:\Users\TU_USUARIO\.claude\skills\prueba-local
```

#### macOS y Linux

```text
~/.claude/skills/prueba-local
```

Después cerrá y volvé a abrir Claude Code.

### Opción 2: instalarla solo en un proyecto

Copiá la carpeta dentro del proyecto:

```text
TU_PROYECTO/.claude/skills/prueba-local
```

Esta variante sirve cuando querés que la skill esté disponible únicamente en ese repositorio.

## Uso

Dentro de Claude Code, podés escribir:

```text
/prueba-local
```

También podés acompañarla con una indicación concreta:

```text
/prueba-local Levantá solamente el frontend y dejalo funcionando para que lo pruebe.
```

O pedirlo en lenguaje natural:

```text
Usá la skill prueba-local para levantar este proyecto en localhost.
```

## Qué hace

La rutina sigue este orden:

1. verifica la carpeta del proyecto;
2. detecta la tecnología;
3. revisa los scripts y archivos de configuración;
4. identifica el administrador de paquetes;
5. verifica dependencias;
6. revisa posibles servicios externos;
7. levanta el proyecto;
8. comprueba errores básicos;
9. informa la URL;
10. deja el servidor funcionando.

## Qué no hace

- No realiza deploy.
- No publica el proyecto.
- No modifica dominios ni DNS.
- No cambia producción.
- No ejecuta migraciones sin autorización.
- No prueba acciones destructivas sobre datos reales.
- No inventa comandos si el proyecto ya define cómo iniciarse.

## Ejemplo de respuesta esperada

```text
Proyecto levantado correctamente.

Tecnología: Vite + React
Comando: npm run dev
URL local: http://localhost:5173
Estado: funcionando
Advertencias: usa una base de datos Supabase remota
Para detenerlo: Ctrl + C en la terminal
```

## Compatibilidad

La skill está pensada para proyectos web y puede adaptarse a entornos como:

- Vite
- React
- Next.js
- Astro
- Angular
- Nuxt
- HTML, CSS y JavaScript
- otros proyectos con instrucciones de ejecución documentadas

## Estructura del repositorio

```text
claude-skill-prueba-local/
├── README.md
└── skills/
    └── prueba-local/
        └── SKILL.md
```

## Filosofía

Construir, levantar localmente, probar, corregir y recién después pensar en publicar.

La skill busca facilitar esa rutina y reducir errores u olvidos durante el desarrollo.

## Licencia

Podés usarla, modificarla y adaptarla libremente para tus proyectos o para crear nuevas versiones.
