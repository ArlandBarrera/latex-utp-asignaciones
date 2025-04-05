# 📑 Template asignaciones UTP 🛠️

Template de documentos de la UTP como: tareas, laboratorios, investigaciones o asignaciones.

## 🗂️ Estructura de archivos

```
documento
├── imagenes
│   ├── fisc.png
│   └── utp.png
├── temauno
│   ├── ref-temauno.tex
│   └── subtema.tex
├── temados
│   ├── ref-temados.tex
│   └── subtema.tex
├── estilos.tex
├── hipervinculos.tex
├── main.tex
├── nuevos-comandos.tex
├── paquetes.tex
├── portada.tex
├── referencias.bib
├── renombrar-comandos.tex
└── strings.txt
```

## 📋 Lista de temas y subtemas

La lógica que maneja esto se encuentra en el arhivo `nuevos-comandos.tex`.

Al nombrar los elementos no debe haber `-` (guión), `_` (barra baja) o `' '` (espacio). Esto no representa un problema para insertar archivos en el archivo principal `main.tex` mediante `\input{ruta/a/archivo.tex}`, sino que al utilizar hipervinculos mediante commados se acepta que el nombre solo sea texto `\alguncomando`.

```latex
\newcommand{\temas}{temauno,temados}
```

```latex
\newcommand{\subtemas}{subtemauno,subtemados}
```

El nombre del tema debe ser igual en los siguientes puntos:

- Definición en la lista `{\temas}{alguntema}`.
- Directorio del tema `alguntema/`.
- Archivo `ref-alguntema.tex` dentro del directorio `alguntema/`.
- Label `\label{lbl-alguntema}` dentro del archivo `ref-alguntema.tex`.

En la carpeta respectiva de un tema `alguntema/`, debe haber un archivo `ref-alguntema.tex` que sirve como anclaje para crear ordenar y referenciar de forma sencilla cada tema y sus respectivos subtemas.

```latex
\chapter{Tema 1}\label{lbl-temauno}
\section{Subtema 1}\label{lbl-subtemauno}
\input{temauno/algun-subtemauno.tex}
```

Al observar la definición de los input se recalca la importancia de mantener un consistencia:

```latex
\newcommand{\incap}[1]{
  \input{#1/ref-#1.tex}
}
```

**NOTA:** Al nombrar el label del subtema, en principio, solo es relevante que tenga el mismo nombre que en la definición del subtema en la lista de subtemas.

**NOTA:** todas las rutas deben ser relativas al archivo `main.tex`.

## 🏷️ Labels de temas y subtemas

Los labels son nombrados `\label{lbl-alguntema}`, esto se debe a que para mantener la consistencia entre los nombres y referencias es más cómodo que se llamen igual.

## 🔗 Hipervinculos a temas y subtemas

**NOTA:** Esto es opcional y está activo en la estructura base.

La lógica que maneja los hipervinculos se encuentra en el archivo `hipervinculos.tex`, el cual es importado dentro del archivo `nuevos-comandos.tex`.

## 📈 Entorno flotante de gráficas y ecuaciones

**NOTA:** Esto es opcional y está inactivo en la estructura base.

Se definen dos entornos flotantes nuevos:

- Gráficas.
- Ecuaciones con un marco alrededor.
