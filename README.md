<p align='center'>
<img width='20%' src='https://fqms.github.io/images/favicon.png' />
</p>

<p align='center'>
<a href='https://github.com/mrf345/FQM/actions/workflows/ci.yml'>
  <img src='https://github.com/mrf345/FQM/workflows/Build/badge.svg'>
</a>
<a href='https://github.com/mrf345/FQM/releases'>
  <img src='https://img.shields.io/github/v/release/mrf345/FQM.svg' alt='release'>
</a>
</p>

<p align='center'>
<a href='https://github.com/mrf345/FQM/actions/workflows/ci.yml'>
  <img src='https://img.shields.io/endpoint?url=https://gist.githubusercontent.com/mrf345/bc746d7bfe356b54fbb93b2ea5d0d2a4/raw/FQM__heads_master.json' alt='Coverage Percentage' />
</a>
<a href='https://www.python.org/dev/peps/pep-0008/'>
  <img src='https://img.shields.io/badge/code%20style-PEP8-orange.svg' alt='Code Style PEP8' />
</a>
<a href='https://github.com/mrf345/FQM/issues?q=is%3Aissue+is%3Aclosed'>
  <img alt="GitHub closed issues" src="https://img.shields.io/github/issues-closed/mrf345/FQM">
</a>
</p>

<h3 align='center'> Free Queue Manager (beta). Un sistema de gesti\u00f3n de filas basado en la web construido con Python Flask, Bootstrap y jQuery. </h3>
<hr />

### Caracter\u00edsticas:

- Soporta impresoras POS USB en los principales sistemas operativos.
- Interfaces personalizables.
- Anuncios mediante sintetizador de voz.

### Instalaci\u00f3n:

#### - Desde el c\u00f3digo fuente:

- Configuraci\u00f3n con Docker para producci\u00f3n, sigue esta [gu\u00eda](./docs/setup.md#1-docker-setup)
- Configuraci\u00f3n est\u00e1ndar con Python (legado), sigue esta [gu\u00eda](./docs/setup.md#2-standard-python-setup)

#### - Con ejecutable [ya no soportado]:

Puedes encontrar un ejecutable para tu sistema operativo en:

- [FQMS](https://fqms.github.io/#download)
- [Github Release](https://github.com/mrf345/FQM/releases/)
- [Sourceforge](https://sourceforge.net/projects/free-queue-manager/)


#### - Migraci\u00f3n de la base de datos:

Desde la versi\u00f3n `0.7` es posible migrar los datos generados en versiones previas a las nuevas.

- Debes copiar el archivo `data.sqlite` de la carpeta principal del proyecto a la carpeta de la nueva versi\u00f3n.
- Si has subido archivos de `Multimedia` en tu configuraci\u00f3n previa, aseg\u00farte de copiarlos manualmente a la nueva carpeta `FQM/static/multimedia/`.

**Aseg\u00farate de realizar la migraci\u00f3n antes de ejecutar la nueva versi\u00f3n del sistema**.

### Documentaci\u00f3n:

- [Gu\u00eda de usuario \u00fatil pero desactualizada](https://fqms.github.io/images/user_guide.pdf).
- [\u00bfC\u00f3mo a\u00f1adir soporte para mi idioma?](docs/localization.md)
- [\u00bfC\u00f3mo agregar configuraciones y personalizaciones adicionales?](docs/settings.md)

<br />
<p align='center'>
<img width='70%' src='https://fqms.github.io/images/logo.gif' />
</p>

### Historial de versiones

| Versi\u00f3n | Descripci\u00f3n |
|-----------|-------------|
| v0.0.1    | Versi\u00f3n inicial |
