# Bitácora — Personalización de perfil de GitHub (FranOsenda)

## Objetivo
Armar el `README.md` del repo especial `github.com/FranOsenda/FranOsenda` (perfil de GitHub), tomando como base visual el template [Aurorp1g](https://github.com/durgeshsamariya/awesome-github-profile-readme-templates/blob/master/templates/Aurorp1g.md) y el stack técnico real del usuario.

## Decisiones de diseño (definidas por preguntas guiadas)

| Aspecto | Decisión |
|---|---|
| Paleta / tema | Oscuro estilo **Tokyo Night** (violeta/azul) |
| Estilo de íconos | Inicialmente **skill-icons**; luego migrado a **badges uniformes de shields.io** (ver "Cambios de la revisión 2") |
| Header | Banner con **typing animado** (nombre + roles rotando) |
| Sección Industrial/Automatización | Sección propia destacada: PLC, SCADA, AutoCAD, Schneider Electric |
| Conocimientos secundarios | Sección aparte "También manejé / conozco" (Jira, Postman, Swagger, Haskell, Prolog) |
| Widgets de stats | Solo **GitHub Stats + Top Languages** (sin gráfico de contribuciones) |
| Redes / contacto | Solo **LinkedIn + Email** |
| Extras (visitas, streak) | Ninguno |
| Footer | Línea divisoria simple (sin banda/ola decorativa) |

## Stack cubierto en el README
- **Frontend:** HTML, CSS, JavaScript, Figma
- **Backend:** Python, C#, C, .NET, Cicode (scripting basado en C para SCADA)
- **IDEs:** VS Code, Visual Studio
- **Bases de datos:** SQL, SQL Server
- **Herramientas:** Git, GitHub, Docker, Cloudflare
- **Sistemas operativos:** Linux, Ubuntu, CachyOS, Hyprland, DMS (Dank), Windows, Windows Server
- **Privacidad:** Proton VPN, Proton Mail, Proton Pass
- **Industrial:** AutoCAD, PLC Programming, SCADA, Schneider Electric
- **También conoce:** Jira, Postman, Swagger, Haskell, Prolog

## Revisión 1 — versión inicial
Se generó el primer `README.md` con:
- Header con typing SVG
- Badges de `skillicons.dev` para el stack con ícono oficial
- Badges custom de `shields.io` (sin logo) para lo que no tiene ícono en skillicons (SQL Server, CachyOS, Hyprland, DMS, Windows Server, Proton, PLC, SCADA, Schneider Electric, Cicode, Prolog)
- Repos destacados vía `github-readme-stats` pin API (placeholders `REPO_1`...`REPO_4`)
- Stats + Top Languages con tema `tokyonight`
- Username placeholder `TU_USUARIO`

## Problemas detectados (con capturas del usuario) y causas

1. **Badges apilados verticalmente en vez de en fila**
   Causa: cada `<img>` estaba en su propia línea "suelta" en el Markdown, sin envolver en un contenedor único. GitHub interpreta esas líneas sueltas como bloques HTML independientes → cada una termina en su propia "fila".
   **Fix:** envolver cada grupo de badges en un único `<p align="center"> ... </p>`, sin líneas en blanco internas.

2. **Mezcla visual inconsistente** (cuadraditos tipo logo de skillicons + pastillas de texto de shields.io en la misma sección)
   **Fix:** se unificó **todo** el README a un solo formato: badges "pill" de `shields.io` estilo `for-the-badge`, sin mezclar con los cuadrados de skillicons. Se sacrifica algo de reconocibilidad de logos a cambio de consistencia total y cero íconos rotos (varios logos —AutoCAD, Jira, Swagger, Prolog, SQL Server, etc.— no existen en todas las librerías de íconos y podían romperse).

3. **Subtítulo "IT Developer · Argentina" superpuesto/flotando junto al título**
   Causa: el `<sub>` estaba pegado (misma línea de flujo) al `<img>` del header, ambos elementos inline sin bloque propio.
   **Fix:** el subtítulo pasó a su propio `<p align="center">`, separado por líneas en blanco del header.

4. **Lista de "Sobre mí" renderizada como párrafo corrido, sin viñetas**
   Causa: había un comentario HTML (`<!-- ... -->`) pegado justo antes de la lista, sin línea en blanco. Eso hace que GitHub trate la lista como continuación del bloque HTML (texto plano) en lugar de Markdown.
   **Fix:** se sacaron los comentarios sueltos intercalados en el cuerpo y se dejó la lista de Markdown limpia, con líneas en blanco antes y después.

5. **Repos destacados y stats con imagen rota**
   Causa: quedó el placeholder `TU_USUARIO` sin reemplazar en las URLs de `github-readme-stats`.
   **Fix:** reemplazado por el username real `FranOsenda` y por el repo real:
   `https://github.com/FranOsenda/TP-Unidad-API-Rest---Programaci-n-2-`
   (por ahora un solo repo destacado; el usuario agrega el resto más adelante).

## Revisión 2 — versión corregida (actual)
- Todos los badges migrados a `shields.io` uniforme (`style=for-the-badge`)
- Cada fila de badges dentro de un único bloque `<p align="center">`
- Header, subtítulo y redes sociales en bloques `<p>` separados
- Lista "Sobre mí" en Markdown puro, sin HTML intercalado
- Username real (`FranOsenda`) aplicado en stats, top-langs y pin de repo
- Placeholders de texto pendientes: `TU_NOMBRE`, `TU_ROL`, `TU_UBICACION`, `TU_LINKEDIN`, `TU_EMAIL`, `TU_DESCRIPCION_*`, `TU_PROYECTO_*`, `TU_FECHA`

## Pendiente / próximos pasos
- [ ] Completar placeholders de texto con datos reales
- [ ] Subir el `README.md` al repo `FranOsenda/FranOsenda` (debe ser público)
- [ ] Verificar en "Preview" de GitHub que todas las filas de badges carguen bien y queden en línea
- [ ] Agregar más repos destacados cuando el usuario lo decida
- [ ] Evaluar más adelante si reincorporar logos reales a algunos badges (una vez confirmado que todo renderiza sin romperse)
