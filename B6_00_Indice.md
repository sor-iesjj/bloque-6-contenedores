---
Bloque: 06_Contenedores
Unidad: UD08
Horas: 22
RA: RA1, RA4, RA5, RA6
CE: 1.a, 1.b, 1.e, 1.i, 4.a, 4.b, 4.c, 4.f, 5.a, 5.b, 5.c, 5.f, 6.a, 6.b, 6.c, 6.e
Playlist: B6_Contenedores
Estado: Fases B6.0 a B6.5 completas · fases B6.6 y B6.7 en construcción
---

# 📦 Bloque 6 — Aislamiento de servicios con contenedores

> Bloque **integrador**, situado al final del módulo (a partir del 16 de marzo). No introduce una asignatura nueva: coge **todo lo que ya sabes** —sistema de archivos, usuarios y permisos, procesos, puertos, servicios, monitorización— y te lo enseña otra vez desde un ángulo distinto, en miniatura y sin poder romper nada.

> [!abstract] La idea que vertebra el bloque entero
> **Un contenedor es un sistema operativo en red reducido a lo mínimo imprescindible para que un servicio funcione.**
>
> Por eso este bloque pertenece a Sistemas Operativos en Red y no a otra cosa: dentro de un contenedor reaparecen el sistema de archivos, los usuarios, los UID, los permisos, los procesos y los puertos. Todo lo del curso, pero cabiendo en 20 MB y arrancando en un segundo.

---

## 🎯 Por qué este bloque existe

> [!info] Esto no es "aprender Docker"
> El objetivo **no** es que salgas sabiendo Docker. El objetivo es que entiendas **qué es aislar un servicio** y por qué la industria dejó de montar un servidor entero para cada cosa.
>
> Docker es solo la herramienta con la que lo vamos a ver, igual que Ventoy fue la herramienta con la que viste los medios de instalación en el Bloque 1. Lo que se evalúa es el concepto de sistema operativo en red, no la herramienta.

**Encaje curricular** (módulo 0224, RD 1691/2007 y Orden 29/07/2009 CV):

| RA | CE | Cómo lo trabaja este bloque |
|---|---|---|
| **RA1** — Instala SO en red describiendo sus características | `1.a` `1.b` `1.e` `1.i` | Compara virtualización **pesada** (UD03/UD04) frente a aislamiento **ligero**. Otro modo de desplegar un sistema, sumado a los de UD02. El eje "¿necesita otro SO?" es un estudio de compatibilidad (`1.a`); elegir imagen y etiqueta es seleccionar componentes (`1.e`); B6.7.2 comprueba la conectividad con el cliente (`1.i`). |
| **RA4** — Gestiona recursos compartidos determinando niveles de seguridad | `4.a` `4.b` `4.c` `4.f` | Volúmenes y *bind mounts* (`4.b` `4.c`), el choque de UID/GID —que es **permiso frente a derecho** en estado puro (`4.a`)— y contenedores sin privilegios como nivel de seguridad (`4.f`). |
| **RA5** — Monitorización | `5.a` `5.b` `5.c` `5.f` | `docker stats` frente a `htop` (`5.a`), medición real de RAM y arranque (`5.b`), y **`docker logs` como trazas generadas por el propio sistema** (`5.c`). |
| **RA6** — Integración de SO libres y propietarios | `6.a` `6.b` `6.c` `6.e` | Servicios Linux sobre Windows con WSL2 (`6.b`), compartir carpetas entre ambos mundos (`6.e`) y comparar con Samba/NFS de UD07 (`6.c`). |

> [!note] Objetivo general de referencia
> **OGCl** — *"Detectar y analizar cambios tecnológicos para elegir nuevas alternativas y mantenerse actualizado dentro del sector."*
> El decreto del título es de 2007 y no nombra los contenedores porque entonces no existían tal como los conocemos. Este objetivo general es el que obliga a mantener el módulo al día.

---

## 🧭 Metodología (igual que en el resto del curso)

- Cada práctica se **graba entera con OBS**, presentándote y con **timestamps**.
- **Playlist:** `B6_Contenedores` · **Vídeo:** `B6.n.m · título` (No listado) · **una sola entrega**.
- Estructura fija: ficha → fundamento → 📹 grabación → procedimiento (Paso 0 + pasos + cierre) → errores/verificación → preguntas → entregables → resumen.
- **Excepción:** las fichas de la Fase B6.0 son **documentos de concepto**, no prácticas. No se graban ni se entregan: se leen antes de tocar el ordenador.

> [!tip] Por qué hay tantas subfases
> Porque cada una introduce **una sola idea nueva**. Es deliberado. Prefiero catorce pasos pequeños que se entienden a cuatro pasos grandes que se copian sin entender. Si una subfase te lleva veinte minutos, vas bien.

---

## 📚 Índice del bloque

### Fase B6.0 · El concepto — *antes de tocar nada* (2 h) · ✅ completa
> Sin ordenador. Se lee, se dibuja y se discute. Son documentos de concepto, no prácticas evaluables.

| # | Documento | Tipo |
|---|-----------|------|
| B6.0.1 | [[B6_0.1_Que_es_un_contenedor\|¿Qué es un contenedor?]] | Concepto |
| B6.0.2 | [[B6_0.2_Contenedor_vs_Maquina_Virtual\|Contenedor frente a máquina virtual]] | Concepto |
| B6.0.3 | [[B6_0.3_Vocabulario\|Vocabulario: imagen, contenedor, registro, capa]] | Concepto |

### Fase B6.1 · Primer contacto (3 h) · ✅ completa
| # | Práctica | Nivel |
|---|----------|-------|
| B6.1.1 | [[B6_1.1_Instalar_Docker_Engine\|Instalar Docker Engine en Ubuntu Server]] | Básico |
| B6.1.2 | [[B6_1.2_Primer_Contenedor\|Tu primer contenedor: qué acaba de pasar]] | Básico |
| B6.1.3 | [[B6_1.3_Ciclo_de_Vida\|Ciclo de vida: `run`, `ps`, `stop`, `start`, `rm`]] | Básico |
| B6.1.4 | [[B6_1.4_Imagenes\|Imágenes: `pull`, `images`, `rmi`. ¿Dónde vive lo que descargas?]] | Básico |

### Fase B6.2 · Mirar dentro: qué es el aislamiento (3 h) · ✅ completa
| # | Práctica | Nivel |
|---|----------|-------|
| B6.2.1 | [[B6_2.1_Entrar_en_un_Contenedor\|Entrar en un contenedor y explorarlo por dentro]] | Básico |
| B6.2.2 | [[B6_2.2_Procesos_Dentro_y_Fuera\|Procesos: `ps aux` dentro y fuera — **la demostración**]] | Intermedio |
| B6.2.3 | [[B6_2.3_El_Contenedor_es_Efimero\|El contenedor es efímero: escribe, borra, desaparece]] | Básico |

### Fase B6.3 · Red y puertos (3 h) · ✅ completa
| # | Práctica | Nivel |
|---|----------|-------|
| B6.3.1 | [[B6_3.1_Nginx_sin_Publicar\|Nginx sin `-p`: por qué no responde]] | Básico |
| B6.3.2 | [[B6_3.2_Publicar_Puertos\|Publicar puertos con `-p 8080:80`]] | Intermedio |
| B6.3.3 | [[B6_3.3_Conflictos_de_Puerto\|Varios contenedores a la vez y conflictos de puerto]] | Intermedio |

### Fase B6.4 · Persistencia y permisos — *el corazón del bloque* (4 h) · ✅ completa
| # | Práctica | Nivel |
|---|----------|-------|
| B6.4.1 | [[B6_4.1_Volumenes\|Volúmenes: que los datos sobrevivan al contenedor]] | Intermedio |
| B6.4.2 | [[B6_4.2_Bind_Mount\|Montar una carpeta del anfitrión (*bind mount*)]] | Intermedio |
| B6.4.3 | [[B6_4.3_Choque_UID_GID\|El choque de UID/GID — reencuentro con UD05]] | Avanzado |
| B6.4.4 | [[B6_4.4_Sin_Privilegios\|Ejecutar un contenedor sin ser root]] | Avanzado |

### Fase B6.5 · Integración libre ↔ propietario (2 h) · **RA6** · ✅ completa
| # | Práctica | Nivel |
|---|----------|-------|
| B6.5.1 | [[B6_5.1_Docker_Desktop_WSL2\|Docker Desktop sobre Windows con WSL2]] | Intermedio |
| B6.5.2 | [[B6_5.2_Compartir_Carpeta_Windows\|Compartir una carpeta entre Windows y el contenedor Linux]] | Intermedio |
| B6.5.3 | [[B6_5.3_Comparativa_Samba_NFS\|Comparativa con Samba y NFS de UD07]] | Intermedio |

### Fase B6.6 · Monitorización (2 h) · **RA5** · 🚧 en construcción
| # | Práctica | Nivel |
|---|----------|-------|
| B6.6.1 | `docker stats` frente a `htop` | Básico |
| B6.6.2 | Registros del servicio con `docker logs` | Básico |
| B6.6.3 | **La medición:** VM contra contenedor, con números | Intermedio |

### Fase B6.7 · Proyecto integrador (3 h) · 🚧 en construcción
| # | Práctica | Nivel |
|---|----------|-------|
| B6.7.1 | De comandos larguísimos a un fichero: `compose.yaml` | Intermedio |
| B6.7.2 | Un servicio accesible desde el cliente Windows del dominio | Avanzado |
| B6.7.3 | Versionar el proyecto en GitHub y entregar | Integrador |

---

## ⛔ Los dos límites del bloque

> [!danger] El controlador de dominio NO se contenedoriza
> Tu Samba AD DC (o tu AD DS) se queda donde está: en su máquina, instalado como toca. Un contenedor aquí es **un servicio más** que se añade a la infraestructura, nunca el corazón del dominio.
>
> No es una manía: un controlador de dominio en contenedor es frágil, y además dejaría de demostrar lo que el módulo tiene que evaluar — que sabes instalar y administrar un sistema operativo en red de verdad.

> [!danger] Dónde se para este bloque
> No vamos a ver `Dockerfile`, registros privados, integración continua ni orquestación (Kubernetes y compañía). Eso es **despliegue de aplicaciones**, es de grado superior, y no pertenece a este módulo.
>
> Con `run`, `ps`, `logs`, `exec`, `-p`, `-v` y un `compose.yaml` sencillo sobra para todo el bloque.

---

## 🧰 Herramientas del bloque

Docker Engine (Ubuntu Server) · Docker Desktop + WSL2 (Windows) · `docker compose` · `docker stats` · `htop` · OBS · Git/GitHub.

> [!summary] Qué te llevas de este bloque
> - Entender **qué significa aislar** un servicio y en qué se diferencia de virtualizar.
> - Reconocer que los permisos, los UID y los puertos **son los mismos** dentro y fuera de un contenedor.
> - Saber levantar un servicio en contenedor y hacerlo accesible desde tu red.
> - Tener un criterio para decidir **cuándo conviene** un contenedor y cuándo una máquina.
