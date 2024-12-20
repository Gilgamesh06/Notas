# Contenido Audio Visual

## Enlaces

* Nos permite enlazar documentos HTML entre si, secciones internas del propio documento o vincular hacia sitios y aplicaciones externas.

* En el atributo **href** colocamos la url del enlace que queremos vincular.

* El atributo **target** con el valor **_blank** permite abrir el enlace en una nueva pestaña, esto es muy util cuando tenemos enlaces hacia sitios externos y redes sociales.

```html
<a href="cursos.html">Ir a la página Cursos</a>
<a href="https://youtube.com/jonmircha" target="_blank">Canal de YouTube</a>
<a href="#top">Regresar al Temario</a>
<a href="mailto:jonmircha@gmail.com">jonmircha@gmail.com</a>
<a href="https://jonmircha.com/html" target="_blank">
  <img src="img/category/html5.svg" alt="HTML5" />
</a>
```

## Imagenes

* La etiqueta **img** nos permite incrustar imagenes en nuestro documento html.
* En el atributo **src** se define la ruta donde se encuentra la imagen.
* En el atributo **alt** se define un texto alternativo para la imagen, este texto no se visualiza, pero es importante agregarlo por temas de accesibilidad (este texto los screen reades de una person con discapacidad visual)

```html
<img src="img/html-for-babies.jpg" alt="HTML para bebés" />
<img src="img/kenai.png" alt="Kenai" />
<img src="img/this-is-fine.gif" alt="This is Fine" />
<img src="img/html5.svg" alt="HTML5" />
<img src="img/wolf-chamanic.webp" alt="Chamanic Wolf" />
```

## Audio y Video

* La etiqueta **audio** y **video** nos permite incrustrar elementos multimedia en formato **mp3** y **mp4** en nuestro documento html.

* En el atributo **src** se define la ruta donde se encuentra el archivo multimedia.

* El atributo **controls** permite visualizar los controles de reproduccion del elemento multimedia.
* El atributo **preload** Permite que se precargue el elemento multimedia, cuando se cargue el documento html en el navegador.
* El atributo **poster** define una imagen previa que se visualizara antes de reproducir el video.

```html
<audio src="assets/feels-patrick-patrikios.mp3" controls preload></audio>

<video
  src="assets/kenai.mp4"
  poster="img/puesta-de-sol.jpg"
  controls
  preload
></video>
```