---
name: prueba-local
description: Detecta cómo se ejecuta un proyecto web, lo levanta en localhost, verifica su funcionamiento básico y lo deja disponible para probar, sin realizar deploy ni modificar producción.
---

# Prueba local

Usá esta skill cuando el usuario quiera ver, probar o verificar un proyecto web durante el desarrollo mediante localhost.

## Objetivo

Levantar el proyecto localmente para que pueda navegarse y probarse en el navegador antes de publicarlo.

La prioridad es:

1. detectar correctamente cómo se ejecuta el proyecto;
2. levantarlo en localhost;
3. verificar errores básicos;
4. informar la URL local;
5. dejar el servidor funcionando;
6. no realizar deploy.

## Reglas obligatorias

- No hacer deploy.
- No publicar el proyecto en internet.
- No modificar producción.
- No cambiar DNS, dominios, hosting ni configuraciones remotas.
- No ejecutar migraciones de base de datos sin autorización explícita.
- No borrar, reemplazar ni modificar datos reales.
- No asumir el comando de inicio: primero revisar los archivos del proyecto.
- No instalar dependencias globales si no es necesario.
- No corregir errores ajenos al pedido sin explicarlos primero.
- No detener el servidor después de levantarlo, salvo que el usuario lo pida.
- No crear archivos o carpetas auxiliares para levantar el proyecto cuando pueda ejecutarse directamente mediante un servidor temporal.

## Enlace de acceso

Después de verificar que el servidor funciona:

1. Mostrar la URL local completa en una línea separada.
2. Escribirla fuera de bloques de código, tablas o recuadros técnicos.
3. Usar el formato directo `http://localhost:PUERTO` para que la plataforma pueda convertirla en enlace clickeable.
4. No abrir automáticamente el navegador ni la vista previa.
5. Dejar que el usuario decida cuándo abrir el proyecto.
6. Si la plataforma no convierte la URL en enlace, mostrarla igualmente completa para copiar.
  
## Procedimiento

### 1. Confirmar la carpeta del proyecto

- Verificar que la terminal esté ubicada en la raíz correcta.
- No ejecutar la rutina sobre la carpeta personal, el escritorio completo o una carpeta superior que contenga varios proyectos.
- Si hay dudas, mostrar la ruta actual y pedir confirmación antes de continuar.

### 2. Detectar el tipo de proyecto

Revisar, según corresponda:

- `package.json`
- `README.md`
- `vite.config.*`
- `next.config.*`
- `astro.config.*`
- `angular.json`
- `nuxt.config.*`
- `index.html`
- `pyproject.toml`
- `requirements.txt`
- `docker-compose.yml`
- otros archivos de configuración relevantes

Identificar:

- tecnología o framework;
- administrador de paquetes;
- comando de desarrollo;
- puerto esperado;
- variables de entorno necesarias.

### 3. Revisar scripts antes de ejecutar

Si existe `package.json`, leer la sección `scripts`.

Preferir el administrador de paquetes indicado por los archivos del proyecto:

- `package-lock.json` → npm
- `pnpm-lock.yaml` → pnpm
- `yarn.lock` → yarn
- `bun.lock` o `bun.lockb` → bun

No mezclar administradores de paquetes sin una razón clara.

### 4. Verificar dependencias

- Comprobar si las dependencias ya están instaladas.
- Instalar solamente si faltan o si el proyecto no puede iniciar por ese motivo.
- Informar antes de realizar una instalación que pueda tardar o modificar archivos de bloqueo.

### 5. Verificar servicios externos

Antes de probar funciones sensibles, revisar si el proyecto utiliza:

- Supabase;
- Firebase;
- bases de datos remotas;
- APIs externas;
- servicios de correo;
- pagos;
- almacenamiento;
- autenticación real.

Advertir si la interfaz es local pero puede conectarse a datos o servicios reales.

No probar acciones destructivas sin autorización.

### 6. Levantar el proyecto

Usar el comando definido por el proyecto, por ejemplo:

- `npm run dev`
- `npm start`
- `pnpm dev`
- `yarn dev`
- `bun dev`
- otro comando documentado

No inventar comandos si existen instrucciones explícitas en el proyecto.

### 7. Verificar el arranque

Comprobar:

- que el servidor inició;
- que no hubo errores de compilación;
- que la URL responde;
- que el puerto está disponible;
- que la página principal carga;
- que no hay errores críticos visibles en la terminal.

Cuando sea posible, revisar también:

- navegación principal;
- botones básicos;
- rutas;
- formularios no destructivos;
- errores de consola;
- recursos faltantes.

### 8. Informar al usuario

Al finalizar, indicar claramente:

- tecnología detectada;
- comando ejecutado;
- URL local exacta;
- puerto utilizado;
- estado del servidor;
- errores o advertencias encontrados;
- si existen conexiones con servicios reales;
- cómo detener el servidor.

Ejemplo:

```text
Proyecto levantado correctamente.

Tecnología: Vite + React
Comando: npm run dev
URL local: http://localhost:5173
Estado: funcionando
Advertencias: usa una base de datos Supabase remota
Para detenerlo: Ctrl + C en la terminal
```

### 9. Mantener el servidor activo

Dejar el proceso en ejecución para que el usuario pueda probar el proyecto.

No confundir localhost con producción:

- el proyecto funciona en la computadora;
- puede navegarse y probarse;
- no está publicado para el público;
- algunas funciones pueden usar servicios externos reales.

## En caso de error

Si el proyecto no inicia:

1. leer el mensaje completo;
2. identificar la causa probable;
3. explicar el problema;
4. proponer el cambio mínimo necesario;
5. no realizar cambios amplios sin autorización;
6. volver a intentar después de corregir.

Separar siempre:

- error que impide iniciar;
- advertencia;
- mejora opcional.

## Resultado esperado

El usuario debe quedar con:

- el proyecto funcionando en localhost;
- una URL clara para abrirlo;
- información sobre posibles riesgos;
- el servidor activo;
- ninguna publicación realizada.
