---
title: Generación de contenido
author: Luis E. Fajardo
date: 12-01-2021
edited: 13-01-2021
category: voc
layout: post
---

**Contenido**
* TOC
{:toc}

***

En **md2tex** se proveen parámetros para visualizar contenido, como ser: tabla de contenido,
lista de figuras y lista de tablas. Los parámetros en **md2tex** son: `toc`, `lof` y `lot`.
Los parámetros: _lof_ y _lot_ son de tipo _binario_, se pueden establecer en _yes_ o _no_; 
por defecto **md2tex** lo ha establecido en _no_. 

Parámetro   | Acción            | LaTeX
:-----------|:------------------|:--------------------
toc         | Muestra la tabla de contenido del documento.                      | `\tableofcontents`
lof         | Muestra una lista de todas las figuras que hay en el documento.   | `\listoffigures`
lot         | Muestra una lista de todas las tablas que hay en el documento.    | `\listoftables`

> <i class="fas fa-exclamation-circle fa-1x"></i> Para mostrar la tabla de contenido, el parámetro _numbered_ debe estar establecido en _yes_.

## Tabla de Contenido

Para generar la tabla de contenido **md2tex** hace uso del parámetro `toc` y puede tener 3 valores: 
_yes_, _no_ y _custom_. Al establecerlo en _custom_ podrá definir los sub-parámetros _spacing_ y 
_depth_. Con estos parámetros podrá manipular la tabla de contenido.

A continuación se describe una sintaxis para mostrar la tabla de contenido del documento:

```md
!--
    numbered: yes
    toc: yes
--!
```
La sintaxis anterior genera una tabla de contenido con `spacing` y `depth` por defecto.

Para modificar la apariencia de la tabla de contenido, puede utilizar la sintaxis siguiente:
```md
!--
    numbered: yes
    toc: custom {
        spacing: <value>
        depth: <value>
    }
--!
```
- **spacing**: Proporciona un espaciado entre los elementos de la tabla de contenido. El 
parámetro _spacing_ puede tener los siguientes valores: `single`, `onehalf` y `double`.
Por defecto, **md2tex** no aplicará ningún espaciado y será LaTeX quien lo aplique.
> <i class="fas fa-info-circle fa-1x"></i> En LaTeX se hace uso del paquete **setspace** 
> para aplicar el espaciado a la tabla de contenido. El comando `\tableofcontents` se 
> declarará dentro de un entorno que puede ser: _singlespacing_, _onehalfspacing_ o 
> _doublespacing_.
- **depth**: Indica la profundidad que se aplicará a la tabla de contenido. Puede aplicar
valores entre 1 y 5; esto es recíproco con los niveles de encabezado que LaTeX proporciona
para la clase _article_. Por defecto, la profundidad de la tabla de contenido es 3.

#### Demostración

La siguiente tabla de contenido tendrá una profundidad de _5_ y un espaciado _onehalf_.
Escriba los siguiente en un archivo de texto _(puede llamarlo `test.md`)_:

```md
!--
    numbered: yes
    toc: custom {
        spacing: onehalf
        depth: 5
    }
--!

---

# Secci'on

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor 
incididunt ut labore et dolore magna aliqua. Semper eget duis at tellus at urna 
condimentum. Volutpat lacus laoreet non curabitur. Ipsum a arcu cursus vitae congue 
mauris rhoncus aenean. Risus nec feugiat in fermentum posuere urna nec. Sagittis id 
consectetur purus ut faucibus pulvinar elementum integer. 

## Sub-secci'on

Purus faucibus ornare suspendisse sed. Dignissim sodales ut eu sem integer vitae. 
Facilisis leo vel fringilla est ullamcorper eget nulla facilisi. Eget sit amet 
tellus cras adipiscing enim. Interdum velit laoreet id donec ultrices tincidunt 
arcu non sodales. Nec dui nunc mattis enim ut tellus. Bibendum ut tristique et 
egestas quis ipsum suspendisse ultrices gravida.

### Sub-sub-secci'on

Facilisi etiam dignissim diam quis. Convallis aenean et tortor at. Ut aliquam purus 
sit amet luctus venenatis lectus magna. Vulputate eu scelerisque felis imperdiet 
proin fermentum leo vel orci. Sagittis aliquam malesuada bibendum arcu. Mollis nunc 
sed id semper risus in hendrerit.

#### P'arrafo

Id semper risus in hendrerit. Eget egestas purus viverra accumsan in nisl nisi 
scelerisque. Nam at lectus urna duis convallis convallis tellus id interdum. Sapien 
pellentesque habitant morbi tristique senectus et netus et. Neque sodales ut etiam 
sit amet nisl. Neque volutpat ac tincidunt vitae semper quis.

##### Sub-p'arrafo

Eu scelerisque felis imperdiet proin fermentum. Dolor sit amet consectetur adipiscing 
elit. Quisque non tellus orci ac auctor augue mauris augue neque. Eget sit amet tellus 
cras adipiscing. Blandit volutpat maecenas volutpat blandit aliquam etiam erat velit 
scelerisque. Faucibus in ornare quam viverra.
```

Ejecute **md2tex**:

```bash
$ ./md2tex test.md
```

El código generado por **md2tex** es el siguiente:

```latex
\documentclass{article}

\usepackage{setspace}

\begin{document}
	\setcounter{tocdepth}{5}
	\begin{onehalfspacing}
		\tableofcontents
	\end{onehalfspacing}
	\newpage

	\section{Secci\'on}
	Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor 
	incididunt ut labore et dolore magna aliqua. Semper eget duis at tellus at urna 
	condimentum. Volutpat lacus laoreet non curabitur. Ipsum a arcu cursus vitae congue 
	mauris rhoncus aenean. Risus nec feugiat in fermentum posuere urna nec. Sagittis id 
	consectetur purus ut faucibus pulvinar elementum integer. 

	\subsection{Sub-secci\'on}
	Purus faucibus ornare suspendisse sed. Dignissim sodales ut eu sem integer vitae. 
	Facilisis leo vel fringilla est ullamcorper eget nulla facilisi. Eget sit amet 
	tellus cras adipiscing enim. Interdum velit laoreet id donec ultrices tincidunt 
	arcu non sodales. Nec dui nunc mattis enim ut tellus. Bibendum ut tristique et 
	egestas quis ipsum suspendisse ultrices gravida.

	\subsubsection{Sub-sub-secci\'on}
	Facilisi etiam dignissim diam quis. Convallis aenean et tortor at. Ut aliquam purus 
	sit amet luctus venenatis lectus magna. Vulputate eu scelerisque felis imperdiet 
	proin fermentum leo vel orci. Sagittis aliquam malesuada bibendum arcu. Mollis nunc 
	sed id semper risus in hendrerit.

	\paragraph{P\'arrafo}
	Id semper risus in hendrerit. Eget egestas purus viverra accumsan in nisl nisi 
	scelerisque. Nam at lectus urna duis convallis convallis tellus id interdum. Sapien 
	pellentesque habitant morbi tristique senectus et netus et. Neque sodales ut etiam 
	sit amet nisl. Neque volutpat ac tincidunt vitae semper quis.

	\subparagraph{Sub-p\'arrafo}
	Eu scelerisque felis imperdiet proin fermentum. Dolor sit amet consectetur adipiscing 
	elit. Quisque non tellus orci ac auctor augue mauris augue neque. Eget sit amet tellus 
	cras adipiscing. Blandit volutpat maecenas volutpat blandit aliquam etiam erat velit 
	scelerisque. Faucibus in ornare quam viverra.
\end{document}
```
Vaya a la carpeta `latex/tex` para ejecutar pdfLaTeX escriba lo siguiente en la línea de comandos:

```bash
# necesitará compilar dos veces para que hayan
# cambios en la tabla de contenido.
$ pdflatex test.tex
$ pdflatex test.tex
```
La primera vez que se compila con pdfLaTeX se crea un archivo auxiliar de extensión `.toc` pero
la tabla no se genera en el documento. En la segunda compilación pdfLaTeX lee el contenido del 
archivo `.toc` y lo pone en el documento final.
> <i class="fas fa-lightbulb"></i> Si utiliza CMake para generar su documento, **NO** necesitará 
> compilar 2 veces los archivos `.tex`.

El resultado final será el siguiente:

<iframe src="https://docs.google.com/gview?url={{site.url}}{{site.baseurl}}/assets/pdf/toc_demo.pdf&embedded=true" style="width:100%; height:500px;" frameborder="0"></iframe>

- [Ver PDF - Demostración Tabla de contenido][3]{:target="_blank"}

[1]: {{site.url}}{{site.baseurl}}/assets/pdf/toc_demo.pdf

## Lista de Figuras

Para aplicar una lista de figuras en **md2tex** se utiliza el parámetro `lof`, este es un parámetro
de tipo _binario_: los valores que puede tener son _yes_ o _no_. Por defecto, **md2tex**, no incluye
la implementación de lista de figuras en el código generado. La sintaxis para el parámetro `lof`
es la siguiente:

```md
!--
	lof: <value>
--!
```

### Demostración

En un archivo de texto _(por ejemplo: `test.md`)_, escriba lo siguiente:

```md
!--
	lof: yes
--!

## Ciudades Coloniales

![Ciudad de Cartagena de Indias, w=8cm, h=6cm, oht](cartagena_indias.jpg)
![Ciudad de San Miguel Allende, w=8cm, h=6cm, oht](san_miguel_allende.jpg)
![Ciudad de Cuzco, w=10cm, h=7cm, oht](cuzco.jpg)

## Figuras Planas

![{Figuras geometricas de dos dimensiones, oht}:Cuadrado, w=2.5cm, h=2.5cm; Circulo, w=2.5cm, h=2.5cm; Rombo, s=0.5; Pentagono, s=0.5, a=45](figuras2d/cuadrado.png, figuras2d/circulo.png, figuras2d/rombo.png, figuras2d/pentagono.png) 
```
> <i class="fas fa-file-archive fa-1x"></i> Puede descargar las imagenes: [figuras simples][1]{:target="_blank"} y [figuras múltiples][2]{:target="_blank"}.

Desde la línea de comandos, ejecute:

```bash
$ ./md2tex test.md
```

El código generado por **md2tex**, es el siguiente:

```latex
\documentclass{article}

\usepackage{graphicx}
\usepackage{subfigure}

\begin{document}
	\listoffigures

	\subsection*{Ciudades Coloniales}

	\begin{figure}[!ht]
		\centering
		\includegraphics[width=8cm, height=6cm]{../images/cartagena_indias.jpg}
		\caption{Ciudad de Cartagena de Indias}
	\end{figure}

	\begin{figure}[!ht]
		\centering
		\includegraphics[width=8cm, height=6cm]{../images/san_miguel_allende.jpg}
		\caption{Ciudad de San Miguel Allende}
	\end{figure}

	\begin{figure}[!ht]
		\centering
		\includegraphics[width=10cm, height=7cm]{../images/cuzco.jpg}
		\caption{Ciudad de Cuzco}
	\end{figure}

	\subsection*{Figuras Planas}

	\begin{figure}[!ht]
		\centering
		\subfigure[Cuadrado]{
			\includegraphics[width=2.5cm, height=2.5cm]{../images/figuras2d/cuadrado.png}
		}
		\subfigure[ Circulo]{
			\includegraphics[width=2.5cm, height=2.5cm]{../images/figuras2d/circulo.png}
		}
		\subfigure[ Rombo]{
			\includegraphics[scale=0.5]{../images/figuras2d/rombo.png}
		}
		\subfigure[ Pentagono]{
			\includegraphics[scale=0.5, angle=45]{../images/figuras2d/pentagono.png}
		}
		\caption{Figuras geometricas de dos dimensiones}
	\end{figure}
\end{document}
```
Vaya a la carpeta `latex/tex`. Necesitará compilar dos veces el archivo `test.tex`, para
generar el archivo PDF.

```bash
$ pdflatex test.tex
$ pdflatex test.tex
```
Al igual que en las tablas de contenido; para las figuras, en la primera compilación LaTeX 
genera un archivo de extensión `.lof` y en la segunda compilación lee este archivo y muestra
su contenido en el documento final.
> <i class="fas fa-lightbulb"></i> Si utiliza CMake para generar su documento, **NO** necesitará 
> compilar 2 veces los archivos `.tex`.

El resultado final es el siguiente:

<iframe src="https://docs.google.com/gview?url={{site.url}}{{site.baseurl}}/assets/pdf/lof_demo.pdf&embedded=true" style="width:100%; height:500px;" frameborder="0"></iframe>

- [Ver PDF - Demostración Lista de Figuras][4]{:target="_blank"}

## Lista de Tablas

Una lista de tablas en **md2tex** es gestionada mediante el parámetro `lot`, este también es un parámetro
de tipo _binario_. Por defecto, **md2tex**, no incluye la implementación de lista de tablas en el código
generado. La sintaxis para el parámetro `lot` es la siguiente:

```md
!--
	lot: <value>
--!
```

### Demostración

<div class="container" align="center">
    <i class="fas fa-laptop-code fa-7x"></i>
	<h5>En desarrollo...</h5>
</div>


[1]: {{site.url}}{{site.baseurl}}/assets/zip/simple_figures.zip
[2]: {{site.url}}{{site.baseurl}}/assets/zip/multiple_figures.zip
[3]: {{site.url}}{{site.baseurl}}/assets/pdf/toc_demo.pdf
[4]: {{site.url}}{{site.baseurl}}/assets/pdf/lof_demo.pdf