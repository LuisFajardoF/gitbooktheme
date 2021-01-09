---
title:  Numeración de páginas
author: Luis E. Fajardo
date: 09-01-2021
edited: 09-01-2021
category: plaintext
layout: post
---

***

La numeración de páginas es otro párametro que puede agregar en **md2tex**. Por defecto, 
**md2tex** enumera las páginas con números arábigos. Para manipular la númeracion de páginas
existe el parámetro *pagenumbering*, este puede cambiar el tipo de numeración de páginas.

Los tipos de numerácion de páginas que **md2tex** y LaTeX soportan son los siguientes:

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