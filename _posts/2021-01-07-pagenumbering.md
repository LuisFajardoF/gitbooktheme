---
title:  Numeración de páginas
author: Luis E. Fajardo
date: 09-01-2021
edited: 10-01-2021
category: plaintext
layout: post
---

***

La numeración de páginas es otro párametro que puede agregar en **md2tex**. Por defecto, 
**md2tex** enumera las páginas con números arábigos. Para manipular la numeración de páginas
existe el parámetro *pagenumbering*, este puede cambiar el tipo de numeración de páginas.

Los tipos de numeración de páginas que **md2tex** y LaTeX soportan son los siguientes:

Tipo de numeración  | Descripción
:-------------------|:---------------------------
__gooble__          | Quita la numeración de páginas.
__arabic__          | Enumera las páginas con números arábigos.
__roman__           | Enumera las páginas con números romanos en minúscula.
__Roman__           | Enumera las páginas con números romanos en mayúscula.
__alph__            | Enumera las páginas con letras del alfabeto latino en minúscula.
__Alph__            | Enumera las páginas con letras del alfabeto latino en mayúscula.

La sintaxis para la numeración de páginas en **md2tex** puede ser la siguiente:

```md
!--
    pagenumbering: <type_numbering>
--!
```
> Donde `<type_numbering>` puede ser: gooble, arabic, roman, Roman, alph o Alph.

Al incluir este parámetro en su documento, en el código LaTeX generado deberá aparecer: 

```latex
% si el parámetro pagenumbering: Roman
\pagenumbering{Roman}
```

La numeración puede cambiar en cualquier parte del documento; si usted desea cambiar
el tipo de numeración puede escribir `!-- pagenumbering: <type_numbering> --!` en 
cualquier parte del documento.

Adicionalmente, el parámetro pagenumbering posee un paramétro _set_. Este parámetro
sirve para reiniciar la numeración de páginas con el número que usted desee.

Por ejemplo, en cualquier parte del documento puede escribir lo siguiente:

```md
!--
    pagenumbering: arabic {
        set: 3
    }
--!
```

El parámetro anterior generará el siguiente código en LaTeX:

```latex
\pagenumbering{arabic}
\setcounter{page}{3}
```

La numeración de páginas aparecerá en el pie de página con orientación centrada.