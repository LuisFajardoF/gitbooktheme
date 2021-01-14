# md2tex

Es una herramienta creada con el fin de proporcionar una interfaz simple para la elaboración de documentos PDF, utilizando _Markdown_ y LaTeX. El usuario necesita conocer la estructura sintáctica de **md2tex** pero no necesita conocer la estructura sintáctica de LaTeX, ya que **md2tex** es quien se encarga de generar código LaTeX para una posterior compilación con _pdfLaTeX_ y este finalmente produce un documento en formato PDF.

La sintaxis de **md2tex** trata de seguir el formato sintáctico de _Markdown_, aunque con algunas variantes; así que algunas estructuras sintácticas de **md2tex** no siguen rigurosamente el formato sintáctico de _Markdown_.

Con **md2tex** se abordan las principales funcionalidades de LaTeX, de manera que el usuario pueda escribir documentación técnica con la calidad que LaTeX proporciona. Se busca que el usuario aproveche estas funcionalidades al máximo aunque no tenga conocimientos previos de LaTeX.

**md2tex** requiere de una entrada proporcionada por el usuario, es decir, el usuario crea un nuevo archivo de texto con la extensión .md, escribe texto en el archivo, **md2tex** tratará de interpretar el contenido del archivo y si no se producen errores generará código LaTeX creando un archivo de extensión `.tex`, este archivo podrá ser compilado por el compilador _pdfLaTeX_ y de esta manera se generará un archivo de extensión _.pdf_.

> _:file_folder: El archivo ejecutable de **md2tex** puede encontrarlo [aquí][2]._

## Acerca de la documentación de _md2tex_

En este repositorio se encuentra la documentación de la herramienta **md2tex**. El sitio donde se 
encuentra la documentación es servido por [GitHub Pages][1], el contenido de la página es gestionado
con [Jekyll][4] y la plantilla utilizada es **jekyll-gitbook**:pushpin:. 
> :information_source: [¿Que es Jekyll?][6]

La página de **md2tex** se encuentra en el siguiente enlace: https://luisfajardof.github.io/md2tex-docs/. 
La documentación esta redactada como __*entradas de post*__ y el contenido es el siguiente:

> :link: [**md2tex**][7]  
> :link: [**Instalación de paquetes LaTeX**][8]  
> :link: [**Entorno de ejecución**][9]  
> :link: [**Procesamiento de Texto Plano**][10]  
> :link: [**Énfasis de Texto**][11]  
> :link: [**Encabezados**][12]  
> :link: [**Numeración de páginas**][13]  
> :link: [**Figuras**][14]  
> :link: [**Generación de contenido**][15]  
> :link: [**Portadas**][16]  
> :link: [**Recursos**][17]  

## Compilación con Ruby

Cambie la versión de Ruby a: 2.5.5 en `Gemfile` _(2.5.5 es la versión Ruby mi sistema)_.

En la línea de comandos, ejecute:
```bash
$ bundle install
$ bundle exec jekyll serve
```

O ejecute los archivos de la carpeta `scripts`:

```bash
$ sh scripts/server
```

> :information_source: En algunos casos deberá ejecutar los scripts: `bootstrap`, `build` y `cibuild` antes de ejecutar el script `server`.

El comando anterior inicia el servicio _(localhost)_ en la siguiente dirección: `http://127.0.0.1:4000/md2tex-docs/`.

***

> :pushpin: La plantilla utilizada en la documentación de **md2tex** es un fork de: https://github.com/sighingnow/jekyll-gitbook/ 

[1]: https://pages.github.com
[2]: https://github.com/LuisFajardoF/md2tex-docs/releases
[3]: https://github.com/sighingnow/jekyll-gitbook/
[4]: https://jekyllrb.com/
[6]: http://www.arquitectoit.com/jekyll/que-es-jekyll/
[7]: https://luisfajardof.github.io/md2tex-docs/
[8]: https://luisfajardof.github.io/md2tex-docs/env/2021-01-05-install-latex.html
[9]: https://luisfajardof.github.io/md2tex-docs/env/2021-01-05-execution-env.html
[10]: https://luisfajardof.github.io/md2tex-docs/plaintext/2021-01-05-plain-text.html
[11]: https://luisfajardof.github.io/md2tex-docs/plaintext/2021-01-06-emphasis.html
[12]: https://luisfajardof.github.io/md2tex-docs/plaintext/2021-01-08-headers.html
[13]: https://luisfajardof.github.io/md2tex-docs/plaintext/2021-01-09-pagenumbering.html
[14]: https://luisfajardof.github.io/md2tex-docs/figures/2021-01-10-figures.html
[15]: https://luisfajardof.github.io/md2tex-docs/voc/2021-01-12-content-display.html
[16]: https://luisfajardof.github.io/md2tex-docs/covers/2021-01-13-covers.html
[17]: https://luisfajardof.github.io/md2tex-docs/resources.html
