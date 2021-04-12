---
title: Bibliografías
author: Luis E. Fajardo
date: 03-04-2021
edited: 12-04-2021
category: env
layout: post
---

**Contenido**
* TOC
{:toc}

***

**md2tex** agrega soporte para bibliografías siguiendo la sintaxis de Markdown pero con
algunas variantes. En el caso de las bibliografías, puede citarse una fuente bibliográfica
en cualquier parte del documento escribiendo el número de fuente bibliográfica de la siguiente
manera: `[<key>]`. Por lo general, las citas bibliográficas aparecen junto con el texto plano 
en un documento, por lo tanto, deberan aparecer donde el escritor decida.

Las bibliografías en **md2tex** se pueden escribir al final del documento y la sintaxis para agregar
fuentes bibliográficas es la siguiente:

~~~
```bib
[<key>]: <kind> {
    <info>: <value>
    <info>: <value>
    ...
}

[<key>]: <kind> {
    <info>: <value>
    <info>: <value>
    ...
}
...
```
~~~

- **key:** se refiere al número de bibliografía, sirve como _"enlace"_ entre la cita bibliográfica y 
la fuente bibliográfica. En **md2tex** este campo siempre deberá ser un número entero.
- **kind:** hace referencia al tipo de bibliografía que se quiere mostrar. Los campos de una bibliografía
serán definidos en función del tipo de bibliografía que se indique en _kind_. Los tipos de bibliografía
mas utilizados en LaTeX son los siguientes:
> | **kind**        | **Definición**                            |
> |-----------------|-------------------------------------------|
> |article          |Artículo de una revista o diario.          |
> |book             |Un libro publicado.                        |
> |booklet          |Una obra impresa pero que no tiene un editor o institución patrocinadora.|
> |conference       |Un artículo expuesto en una conferencia.   |
> |inbook           |Una parte de un libro _(sección, capítulo, etc)_.|
> |incollection     |Una parte de un libro con título propio.   |
> |inproceedings    |Un artículo expuesto en una conferencia.   |
> |manual           |Documentación técnica.                     |
> |mastersthesis    |Una tesis de maestría.                     |
> |phdthesis        |Una tesis doctoral.                        |
> |proceedings      |Lo mismo que un artículo de conferencia.   |
> |techreport       |Reporte publicado por una institución.     |
> |unpublished      |Documento no publicado formalmente, con autor y título.|
> |misc             |Una bibliografía que no encaja con las anteriores.|
>
> <i class="fas fa-info-circle fa-1x"></i> La tabla anterior ha sido tomada y traducida de: [https://www.overleaf.com/learn/latex/bibliography_management_with_bibtex][1]{:target="_blank"}.
> Existen otros tipos de bibliografía, aunque los mencionados en la tabla anterior son los mas utilizados.
- **info:** indica el campo de información que se quiere mostrar, cada campo es gestionado por el 
compilador de LaTeX según su tipo. El nombre de los campos puede ser:
> | **info**        | **Definición**                            |
> |-----------------|-------------------------------------------|
> |author           |Nombre del autor, pueden definirse varios autores utilizando _and_ entre el nombre de cada uno.|
> |chapter          |Indica el capítulo al que hace referencia. |
> |date             |Fecha de publicación, de preferencia utilizar el formato: _yyyy-mm-dd_.
> |doi              |Identificación digital del documento.      |
> |edition          |La edición del documento (puede ser un número).|
> |institution      |Institución académica o de negocios.       |
> |isbn             |Número del estandar internacional de libros.|  
> |issn             |Número del estandar internacional de series.|
> |journaltitle     |Título del journal.                        |
> |keywords         |Una lista de palabras destacadas, separadas por comas.|
> |location         |Lugar en que reside quien publica la información.|
> |month            |El mes de publicación, puede ser un número de 1 al 12 o una abreviatura del mes.|
> |note             |Datos adicionales.                         |
> |pages            |Páginas donde se encuentra la información. |
> |publisher        |La compañía que ha publicado la información.|
> |subtitle         |El subtítulo del documento (en caso que lo tenga).|
> |title            |El título del artículo o documento.        |
> |url              |Dirección web donde se encuentra la información.|
> |urldate          |Fecha en que se accedió a la información, de preferecia utilizar el formato: _yyyy-mm-dd_.
> |version          |Número de versión.                         |
> |year             |Año de publicación de la información.      |
>
> <i class="fas fa-info-circle fa-1x"></i> La tabla anterior ha sido tomada y traducida de: [https://www.mn.uio.no/ifi/tjenester/it/hjelp/latex/biblatex-guide.pdf][2]{:target="_blank"}.
> Los campos anteriores y sus definiciones pueden ser asociados a cualquier tipo de bibliografía. 
- **value:** es la información que se le deberá proveer a cada campo presente en la bibliografía.

Al ejecutar **md2tex** se generará un archivo llamado `bibliography.bib` en la carpeta `latex/bib/`,
en este archivo aparecerán todas las referencias bibliográficas que el usuario haya escrito. El código
LaTeX generado por **md2tex** para las bibliografías será el siguiente:

```latex
@<kind> {
    <key>,
    <info> = "<value>",
    <info> = "<value>",
    ...
}

@<kind> {
    <key>,
    <info> = "<value>",
    <info> = "<value>",
    ...
}
...
```

### Procesamiento de bibliografías con *biber*

Biber es un programa de procesamiento bibliográfico que funciona en conjunto con los paquetes de LaTeX 
ofreciendo soporte completo para Unicode. Biber es un reemplazo para el software BibTeX. Ambos programas
se encargan de generar bibliografía en LaTeX, pero Biber ofrece muchas mas funciones que BibTeX.

Para instalar Biber en su sistema, introduzca lo siguiente en la línea de comandos:

```sh
$ apt install biber
```
> <i class="fas fa-info-circle fa-1x"></i> Es posible que necesite permisos de **superusuario** para ejecutar el comando anterior.

### El parámetro _bibstyle_

Este parámetro sirve para indicarle a LaTeX el estilo de bibliografía que mostrará en el documento PDF.
La sintaxis a utilizar es la siguiente:

```md
!--
    bibstyle: <style>
--!
```

Los estilos de bibliografía que pueden ser utilizados son los siguientes:

|-----------|-----------|-----------|-----------|-----------|
|b-alphabetic|b-authoryear|b-authortitle|b-authoryear-icomp|numeric|
|verbose    |reading    |draft      |apa        |bwl-FU     |
|chem-acs   |chem-angew |chem-biochem|chem-rsc  |ieee       |
|nature     |nejm       |phys       |science    |oscola     |

> <i class="fas fa-info-circle fa-1x"></i> Al no indicar un estilo de bibliografía, por defecto se utiliza el estilo **numeric**.

El parámetro *bibstyle* genera el siguiente código en el preámbulo del archivo de LaTeX:

```tex
\usepackage[backend=biber,style=<style>]{biblatex}
```
Donde _style_ puede ser cualquier estilo de la tabla anterior.

### Demostración

En un archivo de texto _(por ejemplo: `bibliography.md`)_; escriba lo siguiente:

~~~md
!--
    bibstyle: apa
--!

# Bibliography

This is a bibliography test. [1].  
This is a bibliography test. [2].  
This is a bibliography test. [3].

```bib
[1]: article {
    author:     Albert Einstein
    title:      Zur Elektrodynamik bewegter Korper
    journal:    Annalen der Physik
    volume:     322
    number:     10
    pages:      891--921
    year:       1905
    doi:        http://dx.doi.org/10.1002/andp.19053221004       
}

[2]: book {
    author:     Michel Goossens and Frank Mittelbach and Alexander Samarin
    title:      The LaTeX Companion
    year:       1993
    publisher:  Addison-Wesley
    address:    Reading, Massachusetts
}

[3]: misc {
    author:     Donald Knuth
    title:      Knuth: Computers and Typesetting
    url:        http://www-cs-faculty.stanford.edu/uno/abcde.html
    note:       accessed on 2021-02-16
}
```
~~~

Ejecute **md2tex**:
```sh
$ ./md2tex bibliography.md
```
Después de ejecutar **md2tex** se creará un archivo en la carpeta `latex/tex/` y también
se creará un archivo en la carpeta `latex/bib/`. 
- El código LaTeX generado en el archivo `latex/tex/bibliography.tex` es el siguiente:

```latex
\documentclass{article}

\usepackage[backend=biber,style=apa]{biblatex}
\bibliography{../bib/bibliography}

\begin{document}

	\section*{Bibliography}
	This is a bibliography test. \cite{1}.\newline
  
	This is a bibliography test. \cite{2}.\newline
  
	This is a bibliography test. \cite{3}.
	\newpage
	\printbibliography
\end{document}
```
- Las referencias bibliográficas se generaran en el archivo `latex/tex/bibliography.bib`. El contenido del archivo es el siguiente:

```latex
@ARTICLE {
	1,
	AUTHOR = "Albert Einstein",
	TITLE = "Zur Elektrodynamik bewegter Korper",
	JOURNAL = "Annalen der Physik",
	VOLUME = "322",
	NUMBER = "10",
	PAGES = "891--921",
	YEAR = "1905",
	DOI = "http://dx.doi.org/10.1002/andp.19053221004",
}

@BOOK {
	2,
	AUTHOR = "Michel Goossens and Frank Mittelbach and Alexander Samarin",
	TITLE = "The LaTeX Companion",
	YEAR = "1993",
	PUBLISHER = "Addison-Wesley",
	ADDRESS = "Reading, Massachusetts",
}

@MISC {
	3,
	AUTHOR = "Donald Knuth",
	TITLE = "Knuth: Computers and Typesetting",
	URL = "http://www-cs-faculty.stanford.edu/uno/abcde.html",
	NOTE = "accessed on 2021-02-16",
}
```

Vaya a la carpeta `latex/tex` para ejecutar pdfLaTeX, escriba lo siguiente desde la línea de comandos:

```sh
$ pdflatex bibliography.tex
$ biber bibliography
$ pdflatex bibliography.tex
```

Al ejecutar el primer comando se generan dos archivos auxiliares, _(aparte de los archivos auxiliares que pdfLaTeX ya genera)_ la extensión de estos archivos es `.bcf` y `.run.xml`.

- **bibliography.bcf:** Este es un archivo de control utilizado por _biblatex_.
- **bibliography.run.xml:** Este es un archivo XML _(Extensible Markup Language)_ utilizado por _biber_.

El segundo comando también genera dos archivos auxiliares con la extensión `.bbl` y `.blg`.

- **bibliography.bbl:** Este archivo es generado por BibTeX. Esto produce una llamada a _biber_ y la información generada es utilizada por el comando `\bibliography`.
- **bibliography.blg:** Este archivo contiene la lista de mensajes que se generaron cuando se ejecutó _biber_. Este archivo es una copia exacta de los mensajes que aparecen en la línea de comandos al ejecutar _biber_.

El tercer comando se encarga de _"hacer un enlace"_ entre la información generada en la primera ejecución
de pdfLaTeX y la ejecución de _biber_. Cuando se ejecuta pdfLaTeX por segunda vez, aparecen las citas y las 
referencias bibliográficas en el archivo PDF generado. Este comando también modifica los archivos con 
extensión `.bcf` y `.run.xml`.

El archivo PDF generado en esta demostración es el siguiente:

<iframe src="https://docs.google.com/gview?url={{site.url}}{{site.baseurl}}/assets/pdf/bibliography_demo.pdf&embedded=true" style="width:100%; height:500px;" frameborder="0"></iframe>

- [Ver PDF - Demostración de Bibliografías][3]{:target="_blank"}

[1]: https://www.overleaf.com/learn/latex/bibliography_management_with_bibtex
[2]: https://www.mn.uio.no/ifi/tjenester/it/hjelp/latex/biblatex-guide.pdf
[3]: {{site.url}}{{site.baseurl}}/assets/pdf/bibliography_demo.pdf