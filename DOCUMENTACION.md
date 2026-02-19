# Documentación del Proyecto — Turnero
# Hospital Centro de Salud Municipal Malvinas Argentinas

Sistema web para gestión de turnos médicos.

---

## Estructura del Proyecto

```
Turnero/
├── index.html              → Página principal (toda la estructura HTML)
├── DOCUMENTACION.md        → Este archivo, documentación general
├── .gitignore              → Archivos/carpetas ignorados por git
├── src/
│   └── logo.png            → Imagotipo / logo del sistema
├── styles/
│   ├── globales.css        → Variables CSS (paleta de colores del proyecto)
│   ├── header.css          → Estilos del header / barra de navegación
│   ├── panel.css           → Estilos del panel, banner, botones y tarjetas de especialidades
│   └── footer.css          → Estilos del footer
└── scripts/
    └── main.js             → Script principal (inyecta el año actual en el footer)
```

---

## Archivos y qué hace cada uno

### index.html
Página principal del sistema. Contiene:
- **Header nav**: barra de navegación superior con logo clickeable, links con iconos (Inicio con casita, Mis Turnos con calendario), campanita de notificaciones con hover ovalado, divisor vertical e info estática del usuario
- **Sección panel**: título "Panel de Paciente" con descripción y banner de guardia 24hs (parpadeo que se aclara, se detiene en hover)
- **Botones de acción**: dos botones grandes rectangulares con bordes redondeados:
  - "Pedir Turno" — cuadradito azul (--Iconos) con ícono calendario + plus en la esquina
  - "Mis Turnos" — cuadradito verde (--BotonVerde) con ícono calendario + tilde
- **Tarjetas de especialidades**: 4 cards (Cardiología, Odontología, Pediatría, Clínica Médica)
- **Footer**: copyright ©, año dinámico, crédito "Desarrollado por Sion Tech"

### styles/globales.css
Variables CSS que definen la paleta de colores de todo el proyecto:
- **Colores principales:**
  - `--H1`: #4A89AC (azul, títulos principales)
  - `--Textos`: #4F5257 (gris oscuro, textos y párrafos)
  - `--Iconos`: #4A89AC (azul, fondo de cuadraditos de íconos)
  - `--Hover`: #464188 (violeta oscuro, hover de links del nav)
- **Fondos:**
  - `--Fondo`: #FFFFFF (blanco, fondo general)
  - `--FondoSecundario`: #0ea5e9 (celeste, fondo del nav)
- **Banner de guardia:**
  - `--GuardiaRojo`: #DC2626 (rojo base del banner)
  - `--GuardiaRojoClaro`: #F87171 (rojo clarito del parpadeo y cuadradito ambulancia)
- **Botones de acción:**
  - `--BotonVerde`: #22C55E (verde, cuadradito de "Mis Turnos")
- **Textos sobre fondos oscuros:**
  - `--TextoClaro`: #FFFFFF (blanco, para contraste sobre fondos de color)

### styles/header.css
Estilos del header de navegación. Incluye:
- Reset del body (margin/padding 0 para que el nav toque los bordes)
- `.header-nav`: contenedor flex del nav, fondo --FondoSecundario
- `.header-nav__logo-link` / `__logo`: logo clickeable que te lleva al inicio (60px de alto)
- `.header-nav__links`: zona de links empujada a la derecha con margin-left auto
- `.header-nav__link`: cada enlace con icono SVG, hover rectangular redondeado con --Hover
- `.header-nav__link.active`: clase para marcar la sección actual (queda con el fondo hover visible)
- `.header-nav__link-icon`: iconitos SVG dentro de los links (casita, calendario)
- `.header-nav__bell`: campanita de notificaciones con hover ovalado (border-radius: 50px)
- `.header-nav__divider`: barrita vertical separadora (blanco semi-transparente)
- `.header-nav__user`: bloque con nombre y rol del usuario
- `.header-nav__user-icon`: circulito con ícono de persona (fondo blanco semi-transparente)
- Todos los colores blancos usan var(--TextoClaro)

### styles/panel.css
Estilos de la sección del panel de paciente:

**Panel superior (título + banner):**
- `.panel-section`: contenedor flex, título a la izq y banner a la der, centrado verticalmente
- `.panel-section__title`: H1 "Panel de Paciente" con color --H1
- `.panel-section__desc`: párrafo descriptivo con color --Textos
- `.guardia-banner`: rectángulo rojo (--GuardiaRojo) con animación de parpadeo que se aclara a --GuardiaRojoClaro
- `.guardia-banner:hover`: detiene el parpadeo (animation: none) y queda en rojo fijo con glow
- `.guardia-banner__icon-box`: cuadradito --GuardiaRojoClaro con ícono de ambulancia
- `.guardia-banner__text`: textos "Guardia 24hs" y "Urgencias y emergencias"
- `.guardia-banner__arrow`: flechita a la derecha

**Botones de acción:**
- `.action-buttons`: contenedor flex de los dos botones en fila
- `.action-btn`: botón grande con padding vertical alto (1.8rem), fondo difuminado de --Textos, bordes redondeados
- `.action-btn:first-child`: margin-left alineado con el H1 de arriba
- `.action-btn:last-child`: margin-right alineado con el banner de guardia
- `.action-btn--blue`: variante azul (fondo celeste clarito, borde izquierdo --Iconos)
- `.action-btn--green`: variante verde (fondo verde clarito, borde izquierdo --BotonVerde)
- `.action-btn__icon-box`: cuadradito de 58x58px con ícono, dos variantes de color
- `.action-btn__text`: título y descripción del botón
- `.action-btn__title`: texto principal 1.15rem semibold
- `.action-btn__desc`: texto secundario 0.9rem con opacidad 0.7
- `.action-btn__arrow`: flechita empujada a la derecha con margin-left auto

**Sección header (títulos de sección reutilizable):**
- `.section-header`: contenedor flex para título de sección + link a la derecha
- `.section-header__title`: título H2 más chico que el H1, color --H1, alineado con el H1
- `.section-header__link`: link celeste (--FondoSecundario) sin fondo, font-weight 600, hover con opacidad
- `.section-header__link-arrow`: flechita celeste de 5em, se mueve 3px a la derecha en hover

**Tarjetas de especialidades:**
- `.especialidades-grid`: grilla CSS de 4 columnas, alineada con el H1 y el borde derecho
- `.especialidad-card`: tarjeta individual con fondo blanco, borde sutil, sombra, hover eleva la card
- `.especialidad-card__icon-box`: cuadradito de 48x48px con ícono, 4 variantes de color:
  - `--red`: fondo #FEE2E2, ícono #EF4444 (Cardiología)
  - `--blue`: fondo #DBEAFE, ícono --Iconos (Odontología)
  - `--yellow`: fondo #FEF3C7, ícono #F59E0B (Pediatría)
  - `--teal`: fondo #CCFBF1, ícono #14B8A6 (Clínica Médica)
- `.especialidad-card__title`: nombre de la especialidad, 1.05rem bold
- `.especialidad-card__desc`: descripción corta, 0.82rem con opacidad 0.65
- `.especialidad-card__link`: "Consultar >" celeste al final de la tarjeta

---

## Notas
- Los datos del usuario (nombre, rol) son **estáticos por ahora**. Se harán dinámicos con el backend.
- Las especialidades son **estáticas por ahora**. Se podrían hacer dinámicas desde una base de datos.
- Los íconos son **SVG inline** para evitar dependencias externas.
- Se usa la fuente **Inter** de Google Fonts.
- Metodología **BEM** para nombres de clases CSS.
- Todos los colores se manejan desde `globales.css` con variables CSS, nada hardcodeado.
- Repositorio: https://github.com/L4sarte/turnero-hospital

---

## Historial de Cambios

| Fecha | Qué se hizo |
|-------|-------------|
| 18/02/2026 | Header nav con logo, links, campanita, divisor, info usuario |
| 18/02/2026 | Hover rectangular redondeado en links, ovalado en campanita |
| 18/02/2026 | Iconos casita y calendario en los links del nav |
| 18/02/2026 | Logo clickeable que lleva al inicio |
| 18/02/2026 | Clase .active para marcar la sección actual |
| 18/02/2026 | Sección panel: H1 + descripción + banner guardia 24hs |
| 18/02/2026 | Animación de parpadeo en el banner (se aclara, se detiene en hover) |
| 18/02/2026 | Primer push a GitHub |
| 19/02/2026 | Botones de acción: Pedir Turno y Mis Turnos |
| 19/02/2026 | Limpieza de globales.css: eliminadas variables no usadas, agregadas nuevas |
| 19/02/2026 | Reemplazo de colores hardcodeados por variables CSS |
| 19/02/2026 | Ícono de Pedir Turno actualizado (+ en la esquina del calendario) |
| 19/02/2026 | Botones más altos con íconos y textos más grandes |
| 19/02/2026 | Botones rediseñados: fondo tintado, borde izquierdo de color, flechitas |
| 19/02/2026 | Sección "Explorar Especialidades" con link "Ver todas" celeste |
| 19/02/2026 | Flechita de "Ver todas" alineada al alto del texto (5em) |
| 19/02/2026 | Tarjetas de especialidades: Cardiología, Odontología, Pediatría, Clínica Médica |
| 19/02/2026 | Íconos outline: corazón con frecuencia cardíaca, muela solo bordes |
| 19/02/2026 | Footer con copyright ©, año dinámico (JS externo) y crédito Sion Tech |

