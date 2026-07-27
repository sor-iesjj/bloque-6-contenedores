# Bloque 6 — Aislamiento de servicios con contenedores

> **Módulo:** SOR — Sistemas Operativos en Red · 2.º SMR · **Profesor:** Pedro Navarro Miralles · IES Jorge Juan (Alicante)
> **Autor y propietario:** © 2026 Pedro Navarro Miralles. **Licencia:** [CC BY-NC-SA 4.0](LICENSE) — atribución obligatoria, uso no comercial.

Bloque **integrador**, al final del módulo. No introduce una asignatura nueva: coge todo lo que ya sabes —sistema de archivos, usuarios y permisos, procesos, puertos, servicios, monitorización— y te lo enseña otra vez desde un ángulo distinto, en miniatura y sin poder romper nada.

> **La idea que vertebra el bloque:** un contenedor es un sistema operativo en red reducido a lo mínimo imprescindible para que un servicio funcione.

**Esto no es "aprender Docker".** El objetivo es entender **qué es aislar un servicio** y por qué la industria dejó de montar un servidor entero para cada cosa. Docker es la herramienta con la que lo vemos, igual que Ventoy lo fue en el Bloque 1.

## Metodología

Cada práctica se **graba entera con OBS** (presentándote, con timestamps) y se sube a la playlist **`B6_Contenedores`** de YouTube (No listado). Entrega única. Estructura fija: ficha → fundamento → grabación → procedimiento (Paso 0 + pasos + cierre) → errores/verificación → preguntas → entregables → resumen.

> **Excepción:** las fichas de la Fase B6.0 son **documentos de concepto**, no prácticas. No se graban ni se entregan: se leen antes de tocar el ordenador.

## Índice

**Fase B6.0 · El concepto** *(2 h — sin ordenador)* ✅ **completa**
- `B6.0.1` — ¿Qué es un contenedor?
- `B6.0.2` — Contenedor frente a máquina virtual
- `B6.0.3` — Vocabulario: imagen, contenedor, registro, capa

**Fase B6.1 · Primer contacto** *(3 h)*
- `B6.1.1` — Instalar Docker Engine en Ubuntu Server
- `B6.1.2` — Tu primer contenedor: qué acaba de pasar
- `B6.1.3` — Ciclo de vida: `run`, `ps`, `stop`, `start`, `rm`
- `B6.1.4` — Imágenes: `pull`, `images`, `rmi`

**Fase B6.2 · Mirar dentro: qué es el aislamiento** *(3 h)*
- `B6.2.1` — Entrar en un contenedor y explorarlo
- `B6.2.2` — Procesos: `ps aux` dentro y fuera — **la demostración**
- `B6.2.3` — El contenedor es efímero

**Fase B6.3 · Red y puertos** *(3 h)*
- `B6.3.1` — Nginx sin `-p`: por qué no responde
- `B6.3.2` — Publicar puertos con `-p 8080:80`
- `B6.3.3` — Varios contenedores y conflictos de puerto

**Fase B6.4 · Persistencia y permisos** *(4 h — el corazón del bloque)*
- `B6.4.1` — Volúmenes: que los datos sobrevivan
- `B6.4.2` — Montar una carpeta del anfitrión (*bind mount*)
- `B6.4.3` — El choque de UID/GID — reencuentro con UD05
- `B6.4.4` — Ejecutar un contenedor sin ser root

**Fase B6.5 · Integración libre ↔ propietario** *(2 h · RA6)*
- `B6.5.1` — Docker Desktop sobre Windows con WSL2
- `B6.5.2` — Compartir una carpeta entre Windows y el contenedor Linux
- `B6.5.3` — Comparativa con Samba y NFS de UD07

**Fase B6.6 · Monitorización** *(2 h · RA5)*
- `B6.6.1` — `docker stats` frente a `htop`
- `B6.6.2` — Registros del servicio con `docker logs`
- `B6.6.3` — **La medición:** VM contra contenedor, con números

**Fase B6.7 · Proyecto integrador** *(3 h)*
- `B6.7.1` — De comandos larguísimos a un `compose.yaml`
- `B6.7.2` — Un servicio accesible desde el cliente Windows del dominio
- `B6.7.3` — Versionar el proyecto en GitHub y entregar

## Los dos límites del bloque

- **El controlador de dominio NO se contenedoriza.** Se queda en su máquina. Un contenedor aquí es *un servicio más* que se añade a la infraestructura, nunca el corazón del dominio.
- **No se ven** `Dockerfile`, registros privados, integración continua ni orquestación (Kubernetes). Eso es despliegue de aplicaciones, es de grado superior y no pertenece a este módulo.

Consulta el índice completo con enlaces en [`B6_00_Indice.md`](B6_00_Indice.md).
