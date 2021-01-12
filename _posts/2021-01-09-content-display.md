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
- **depth**: Indica la profundidad que se aplicará a la tabla de contenido. Puede aplicar
valores entre 1 y 5; esto es recíproco con los niveles de encabezado que LaTeX proporciona
para la clase _article_. Por defecto, la profundidad de la tabla de contenido es 3.



