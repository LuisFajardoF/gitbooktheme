---
title: Instalación de paquetes LaTeX
author: Luis E. Fajardo
date: 05-01-2021
edited: 21-01-2021
category: env
layout: post
---

***

Para compilar con LaTeX, necesitará el compilador *pdfLaTeX*; este compilador
viene junto con los paquetes básicos que necesitará para crear documentos PDF.
Algunos paquetes no estan en el conjunto de paquetes que LaTeX instala; los paquetes
faltantes serán descargados vía `tlmgr`.

Los requerimientos para elaborar documentos PDF con **md2tex** son los siguientes:
- Sistema operativo Linux (de preferencia Debian).
- Instalación de paquete `texlive-latex-base`.

```sh
# En debian o derivados
$ apt install texlive-latex-base
```


### Configuración de _tlmgr_

__tlmgr__ administra una instalación existente de TeXLive, tanto los paquetes como las 
opciones de configuración. Para empezar a configurar __tlmgr__ en su sistema, ejecute:

```sh
$ tlmgr init-usertree
```
El comando anterior configurará __tlmgr__ para que funcione en modo usuario. Se creará
una carpeta denominada `texmf` en la ruta `/home/<your user>/` _(sistemas Debian y derivados)_.

Dentro de la carpeta `texmf` se crearán las siguientes archivos y carpetas:

```sh
texmf/
├── tlpkg/
└── web2c/
    └── tlmgr.log
```
Se crearán varios archivos auxiliares; el archivo `tlmgr.log` es importante, ya que lleva un
registro detallado de las acciones que se han ejecutado con __tlmgr__.

Para que **tlmgr** descargue paquetes, deberá indicarle un repositorio del cual descargarlos.
Utilice el siguiente comando para que **tlmgr** apunte a un repositorio.

```sh
$ tlmgr option repository <url repository>
```
> <i class="fas fa-info-circle fa-1x"></i> Si está utilizando un sistema Debian o derivado, se recomienda utilizar el siguiente repositorio: [ftp://tug.org/historic/systems/texlive/2018/tlnet-final][4]{:target="_blank"}

Para instalar paquetes con **tlmgr**, utilice el siguiente comando:

```sh
$ tlmgr install <package>
```
> <i class="fas fa-exclamation-triangle"></i> La operación anterior tardará varios minutos, los paquetes descargados se instalarán en la carpeta 
`texmf`.   
> <i class="fas fa-info-circle fa-1x"></i> Se recomienda poner todos los paquetes a descargar en un solo comando.

Los paquetes que necesitará descargar para el funcionamiento de **md2tex** son los siguientes:
> <i class="fas fa-check-square"></i> _subfigure_

**md2tex** hace uso del paquete `setspace` pero este no se puede descargar a través de **tlmgr**; este 
paquete se deberá instalar manualmente. Descargue el paquete _setspace_ [aquí][1] o busquelo en la 
sección [Recursos][2], en el apartado _Paquete setspace_.

Una vez descargado descomprima el archivo en la ruta: `/home/<your user>/texmf/tex/latex`.

### Pruebas unitarias

Se ha desarrollado un _script_ para que usted pueda verificar que los paquetes de LaTeX requeridos se 
encuentran en su sistema. En este apartado encontrará un conjunto de pruebas unitarias que interpretan 
con **md2tex** un archivo, luego lo compilan con _pdfLaTeX_ y muestran el resultado en una carpeta llamada
`output`.

La estructura de la carpeta de pruebas unitarias es la siguiente:

```
unit-tests/
├── chktex
├── md2tex
├── run-tests
├── <test 1>/
├── <test 2>/
└── <test n>/
```
En la carpeta de `unit-tests` encontrará lo siguiente:

- La versión mas reciente de **md2tex**; en este caso **md2tex** es utilizado en el entorno
local por el _script_ `run-tests`.
- La versión mas reciente de **chktex**; este es un ejecutable que verifica que los paquetes requeridos 
se encuentran en el sistema.
> Este ejecutable está escrito en C++, en el fondo ejecuta el comando  
> `tlmgr list --only-installed`.
> **chktex** puede recibir el flag `--manual-config` como segundo parámetro, con lo cual **NO** ejecutará el comando de __tlmgr__ sino que irá a verificar que las carpetas de los paquetes requeridos existan
> en la ruta  
> `/home/<your user>/texmf/tex/latex/`.
- El _script_ `run-tests` ejecuta **md2tex** y *pdfLaTeX* por cada carpeta de test que encuentra.
- Las carpetas de tests; __los nombres de estas carpetas no deberán ser modificados__.
> Por cada carpeta de test se generará una carpeta `output` en la ruta `<test>/latex/tex/`.

> <i class="fas fa-file-archive fa-1x"></i> Descargue las pruebas unitarias [aquí][3]

##### Ejecución de pruebas unitarias

Para ejecutar las pruebas unitarias, escriba en la línea de comandos:
```sh
$ cd unit-tests
$ bash run-tests
```
> <i class="fas fa-exclamation-triangle"></i> Si el archivo `run-tests` necesita permisos de ejecución, ejecute el siguiente comando: _chmod +rwx run-tests_.

La ejecución del _script_ será similar a la siguiente:

![unit tests][5]{:title="unit-tests" class="center-image"}

### Configuración manual

Debido a que __tlmgr__ tarda mucho tiempo en descargar paquetes; usted puede hacer una configuración 
manual de los paquetes, si así lo desea. Cuando el compilador de _pdfLaTeX_ no encuentra un paquete
en sus archivos, vá a consultar la carpeta de __usuario__ llamada `texmf`; si encuentra el paquete,
lo utilizará para generar el documento final.

Para crear la carpeta `texmf` vaya a la ruta `/home/<your user>/` y escriba lo siguiente:

```sh
# comando para inicializar tlmgr en modo usuario
$ tlmgr init-usertree

# o puede crear la carpeta directamente
$ mkdir texmf
```

Independientemente del comando que haya ejecutado; dentro de `texmf` deberá crear la carpeta `tex`
y dentro de la carpeta `tex`, creará la carpeta `latex`. En línea de comandos lo haría de la 
siguiente manera:

```sh
$ cd texmf
$ mkdir tex
$ cd tex
$ mkdir latex
```

Dentro de la carpeta `latex`, podrá descomprimir los archivos y carpetas que se brindan en
esta documentación.
> <i class="fas fa-file-archive fa-1x"></i> Descargue los paquetes de LaTeX requeridos por **md2tex** [aquí][6]. 

##### Ejecución de pruebas unitarias

Para ejecutar las pruebas unitarias deberá ejecutar el script `run-tests`, con el flag `--manual-config`.

```sh
$ bash run-tests --manual-config
```

[1]: {{site.url}}{{site.baseurl}}/assets/zip/setspace.zip
[2]: {{site.url}}{{site.baseurl}}/resources.html
[3]: {{site.url}}{{site.baseurl}}/assets/zip/unit-tests.zip
[4]: ftp://tug.org/historic/systems/texlive/2018/tlnet-final
[5]: {{site.url}}{{site.baseurl}}/assets/images/unit-tests.gif
[6]: {{site.url}}{{site.baseurl}}/assets/zip/latex_packs.zip