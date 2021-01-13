---
title: Tablas de contenido 
author: Luis E. Fajardo
date: 12-01-2021
edited: 12-01-2021
category: voc
layout: post
---

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

El parámetro `toc` puede tener 3 valores: _yes_, _no_ y _custom_. Al establecerlo en _custom_
podrá definir los sub-parpámetros _spacing_ y _depth_. Con estos parámetros podrá manipular
la tabla de contenido.

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
> <i class="fas fa-lightbulb"></i> Si utiliza CMake para generar su documento, no necesitará 
> compilar 2 veces los archivos `.tex`.

El resultado final será el siguiente:

<iframe src="https://docs.google.com/gview?url={{site.url}}{{site.baseurl}}/assets/pdf/toc_demo.pdf&embedded=true" style="width:100%; height:500px;" frameborder="1"></iframe>

- [Ver PDF - Demostración Tabla de contenido][1]{:target="_blank"}

[1]: {{site.url}}{{site.baseurl}}/assets/pdf/toc_demo.pdf