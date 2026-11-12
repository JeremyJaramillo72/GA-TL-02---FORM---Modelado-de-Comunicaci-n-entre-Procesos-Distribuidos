# GA-TL-02 — Taller de Modelado de Comunicación entre Procesos Distribuidos

Repositorio correspondiente a la actividad formativa grupal preparatoria para la Práctica Experimental de la Unidad 1 (PE-U1 / GA-SUM-01) de la asignatura Aplicaciones Distribuidas.

---

## 1. Información Académica e Institucional

- **Institución:** Universidad Técnica Estatal de Quevedo (UTEQ).
- **Facultad:** Facultad de Ciencias de la Ingeniería (FCI).
- **Carrera:** Ingeniería de Software.
- **Asignatura:** Aplicaciones Distribuidas (SOF-I-R).
- **Nivel / Paralelo:** 7mo Nivel — Paralelo "A".
- **Docente:** Dr. Gleiston Cicerón Guerrero Ulloa.
- **Período / Semana:** Semana 2 (2 al 8 de noviembre de 2026).
- **Código de Actividad:** GA-TL-02 - FORM.
- **Carácter de la Actividad:** Formativa (preparatoria para PE-U1 / GA-SUM-01).
- **Escenario de Negocio Asignado:** Sistema Bancario de Transferencias.

---

## 2. Descripción de la Actividad

El presente taller práctico modela la arquitectura de comunicación entre procesos distribuidos para un Sistema Bancario de Transferencias. El diseño desarrollado sirve como base técnica conceptual para la implementación práctica que se evaluará en la Práctica Experimental de la Unidad 1 (PE-U1), donde se implementará y comparará la comunicación mediante Sockets TCP y RPC (gRPC).

- **Enlace al Diagrama en Línea (draw.io):** [Diagrama del Sistema Bancario en diagrams.net](https://app.diagrams.net/#G1-uXBEb-HvhBgk12dZY92STUV4sAz9cFo#%7B%22pageId%22%3A%22sFHvxhZjUFzQrptnvxQm%22%7D)

---

## 3. Integrantes del Equipo de Trabajo

| N.º | Nombres y Apellidos |
|:---:|---|
| 1 | Luis Jeremy Jaramillo Acosta |
| 2 | Kenny Isaías España Vera |
| 3 | Luis Alberto Paca Pilataza |
| 4 | Heiner Ariel Zambrano Ronquillo |

---

## 4. Estructura del Repositorio

```text
├── .gitignore                                          # Exclusión de temporales de compilación y carpetas locales
├── README.md                                           # Información institucional, integrantes e instrucciones de compilación
├── diagrama_bancario.drawio                            # Archivo editable del diagrama de comunicación (draw.io)
├── Diagrama de Comunicación-Página-1.drawio (4).pdf     # Exportación vectorial del diagrama en PDF
├── Diagrama de Comunicación-Página-1.drawio.png         # Exportación del diagrama en imagen PNG
├── main.tex                                            # Notas de presentación y respuestas a preguntas críticas en LaTeX
├── main.pdf                                            # Documento compilado en PDF de las notas de presentación
└── referencias.bib                                     # Fuentes bibliográficas en formato BibTeX (estilo IEEE)
```

> **Acceso directo al diagrama:** [Abrir diagrama editable en diagrams.net (draw.io)](https://app.diagrams.net/#G1-uXBEb-HvhBgk12dZY92STUV4sAz9cFo#%7B%22pageId%22%3A%22sFHvxhZjUFzQrptnvxQm%22%7D)

---

## 5. Instrucciones de Compilación del Documento LaTeX (`main.tex`)

El archivo `main.tex` contiene las notas de la presentación, las preguntas críticas recibidas y las respuestas técnicas sustentadas con referencias bibliográficas en formato IEEE.

Para compilar `main.tex` y generar el archivo `main.pdf`:

### Requisitos Previos
Contar con una distribución de LaTeX instalada ([MiKTeX](https://miktex.org/) en Windows o [TeX Live](https://tug.org/texlive/) en Linux) con el procesador bibliográfico **Biber**.

### Opción 1: Compilación por Línea de Comandos (CLI)
Al utilizar `biblatex` con backend `biber`, se debe ejecutar la siguiente secuencia:

```powershell
# 1. Generar archivos auxiliares
pdflatex -interaction=nonstopmode main.tex

# 2. Procesar las referencias bibliográficas
biber main

# 3. Vincular las citas en el documento
pdflatex -interaction=nonstopmode main.tex

# 4. Resolver referencias cruzadas y numeración final
pdflatex -interaction=nonstopmode main.tex
```

### Opción 2: Compilación Automatizada con `latexmk`
```powershell
latexmk -pdf main.tex
```

### Opción 3: Editores de Escritorio (VS Code / TeXstudio)
- **Visual Studio Code:** Abrir `main.tex` con la extensión *LaTeX Workshop* instalada y presionar `Ctrl + Alt + B`.
- **TeXstudio:** Configurar el backend bibliográfico como `Biber` y presionar `F5` (Compilar y Ver).

### Opción 4: Compilación en Overleaf
1. Subir `main.tex` y `referencias.bib` al proyecto.
2. En **Menu** (esquina superior izquierda), comprobar que el compilador sea **pdfLaTeX** y la versión de TeX Live sea actual.
3. Presionar **Recompile**.
