---
title: Recursos
author: Luis E.Fajardo
date: 21-01-2021
edited: 21-01-2021
layout: home
---

Aquí encuentra las herramientas de desarrollo, tutoriales y demostraciones para el uso de 
**md2tex**; también encontrará la aplicación ejecutable en entornos Linux.

***

### <i class="fas fa-file-download fa-1x"></i> [md2tex v1][1]{:target="_blank"}
> Descargue la primera versión de **md2tex**. Esta vesión aún se encuentra en desarrollo.

***

### <i class="fas fa-file-pdf fa-1x"></i> [Instalación de herramientas para compilación de md2tex][2]{:target="_blank"}
> Explicación paso a paso de las herramientas a instalar para la compilación del proyecto **md2tex**.  
> La herramienta **md2tex** ha sido desarrollada en C++.

***

### <i class="fas fa-file-pdf fa-1x"></i> [Funcionalidades md2tex][3]{:target="_blank"}
> Demostración del funcionamiento de **md2tex**. Explicación y demostración de aspectos sintácticos de la herramienta.

***

### <i class="fas fa-external-link-square-alt fa-1x"></i> [Cmake][4]{:target="_blank"}
> Descargue la versión mas reciente de **Cmake** para Linux. Una vez descargado descomprima el archivo y
> ejecute los siguientes comandos:
> ```sh
> $ ./bootstrap
> $ make && make install
> ```
> Para comprobar que **Cmake** se ha instalado en su sistema, ejecute:
> ```sh
> $ cmake --version
> ```

***

### <i class="fas fa-file-code fa-1x"></i> [UseLATEX.cmake][5]{:target="_blank"}
> Descargue **UseLATEX.cmake**, este archivo le servirá para compilar sus archivos LaTeX con Cmake.
> Este archivo deberá estar dentro de la carpeta `latex/` de su proyecto.  
> <i class="fas fa-info-circle fa-1x"></i> **UseLATEX.cmake** pertenece al proyecto **UseLATEX** y ha sido desarrollado por  
> [Kenneth Moreland][6]{:target="_blank"}.
> Si desea leer documentación acerca del uso de **UseLATEX.cmake**:  
> [LaTeX Document Building Made Easy][7]{:target="_blank"}.

***

### <i class="fas fa-file-archive fa-1x"></i> [Paquete _setspace_][8]{:target="_blank"}
> Este paquete es requerido por **md2tex**. Si hace su instalación de paquetes con **tlmgr**, necesitará descomprimirlo en la ruta `/home/<your user>/texmf/tex/latex/`.

***

### <i class="fas fa-file-archive fa-1x"></i> [Paquetes LaTeX][9]{:target="_blank"}
> Si hace una instalación manual de los paquetes de LaTeX, deberá descomprimir este archivo en la ruta: `/home/<your user>/texmf/tex/latex/`.

***

### <i class="fas fa-file-archive fa-1x"></i> [Pruebas unitarias][10]{:target="_blank"}
> Descomprima este archivo en cualquier ruta de su sistema. Si ha hecho su configuración con **tlmgr**, puede ejecutar:  
> ```sh
> $ bash run-tests
> ```
> Si ha hecho su configuración manualmente, puede ejecutar:
> ```sh
> $ bash run-tests --manual-config
> ```
> _<i class="fas fa-info-circle fa-1x"></i> Es probable que el archivo **run-tests** necesite permisos de ejecución. Si es el caso, ejecute: `chmod +rwx run-tests`_.


[1]: {{site.url}}{{site.baseurl}}/assets/app/v1/md2tex
[2]: {{site.url}}{{site.baseurl}}/assets/pdf/dev-tools.pdf
[3]: {{site.url}}{{site.baseurl}}/assets/pdf/md2tex-v1.pdf
[4]: https://cmake.org/download/
[5]: {{site.url}}{{site.baseurl}}/assets/cmake/UseLATEX.cmake
[6]: https://gitlab.kitware.com/kmorel/UseLATEX/
[7]: https://gitlab.kitware.com/kmorel/UseLATEX/raw/master/UseLATEX.pdf
[8]: {{site.url}}{{site.baseurl}}/assets/zip/setspace.zip
[9]: {{site.url}}{{site.baseurl}}/assets/zip/latex_packs.zip
[10]: {{site.url}}{{site.baseurl}}/assets/zip/unit-tests.zip
