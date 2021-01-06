---
title: Entorno de ejecución de md2tex
author: Luis Fajardo
date: 06-01-2021
category: jekyll
layout: post
---

Los requerimientos para elaborar documentos PDF con **md2tex** son los siguientes:
- Sistema operativo Linux (de preferencia Debian).
- Instalación de paquete `texlive-lang-spanish`.
```
# En debian o derivados
apt install texlive-lang-spanish
```
- Los paquetes faltantes se instalarán con `tlmgr`.
```
# Establecer el repositorio de donde tlmgr descargará los paquetes.
tlmgr option repository ftp://tug.org/historic/systems/texlive/2018/tlnet-final
# Para descargar paquetes con tlmgr
tlmgr install <package>
```