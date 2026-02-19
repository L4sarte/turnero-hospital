# Documentación del Proyecto — Turnero
# Hospital Centro de Salud Municipal Malvinas Argentinas

Sistema web para gestión de turnos médicos.

---

## Estructura del Proyecto

```
Turnero/
├── index.html              → Página principal (toda la estructura HTML)
├── DOCUMENTACION.md        → Este archivo, documentación general
├── src/
│   └── logo.png            → Imagotipo / logo del sistema
├── styles/
│   ├── globales.css        → Variables CSS (paleta de colores del proyecto)
│   ├── header.css          → Estilos del header / barra de navegación
│   └── panel.css           → Estilos del panel de paciente y banner de guardia
└── scripts/                → (pendiente) Archivos JavaScript
```

---

## Archivos y qué hace cada uno

### index.html
Página principal del sistema. Contiene:
- **Header nav**: barra de navegación superior con logo, links (Inicio, Mis Turnos), campanita de notificaciones, divisor vertical e info del usuario
- **Sección panel**: título "Panel de Paciente" con descripción y banner de guardia 24hs

### styles/globales.css
Variables CSS que definen la paleta de colores de todo el proyecto:
- `--Navegaciones` / `--Iconos` / `--Enlaces`: #4A89AC (azul)
- `--Hover`: #464188 (violeta oscuro, para efectos hover)
- `--H1` / `--Subtitulos`: #4A89AC (azul, para títulos)
- `--Textos` / `--Bordes`: #4F5257 (gris oscuro)
- `--Fondo`: #FFFFFF (blanco)
- `--FondoSecundario`: #0ea5e9 (celeste, fondo del nav)

### styles/header.css
Estilos del header de navegación. Incluye:
- Reset del body (margin/padding 0 para que el nav toque los bordes)
- `.header-nav`: contenedor flex del nav, fondo --FondoSecundario
- `.header-nav__logo-link` / `__logo`: logo clickeable que te lleva al inicio
- `.header-nav__links`: zona de links empujada a la derecha con margin-left auto
- `.header-nav__link`: cada enlace con icono SVG, hover rectangular redondeado con --Hover
- `.header-nav__link.active`: clase para marcar la sección actual (queda con el fondo hover)
- `.header-nav__link-icon`: iconitos SVG dentro de los links (casita, calendario)
- `.header-nav__bell`: campanita de notificaciones con hover ovalado
- `.header-nav__divider`: barrita vertical separadora
- `.header-nav__user`: bloque con nombre, rol e ícono del usuario
- `.header-nav__user-icon`: circulito con ícono de persona

### styles/panel.css
Estilos de la sección del panel de paciente:
- `.panel-section`: contenedor flex, título a la izq y banner a la der
- `.panel-section__title`: H1 "Panel de Paciente" con color --H1
- `.panel-section__desc`: párrafo descriptivo con color --Textos
- `.guardia-banner`: rectángulo rojo de guardia 24hs con animación de parpadeo (se aclara)
- `.guardia-banner:hover`: detiene el parpadeo y queda en rojo fijo
- `.guardia-banner__icon-box`: cuadradito rosa con ícono de ambulancia
- `.guardia-banner__text`: textos "Guardia 24hs" y "Urgencias y emergencias"
- `.guardia-banner__arrow`: flechita a la derecha

---

## Notas
- Los datos del usuario (nombre, rol) son **estáticos por ahora**. Se harán dinámicos con el backend.
- Los íconos son **SVG inline** para evitar dependencias externas.
- Se usa la fuente **Inter** de Google Fonts.
- Metodología **BEM** para nombres de clases CSS.
