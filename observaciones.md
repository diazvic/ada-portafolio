# Observaciones

Querida Vicky, felicitaciones por tu trabajo. Tu portfolio se ve muy lindo y se nota muchísimo el esfuerzo por hacer que se asemeje al modelo de Ada. Hay muchos detalles que lo mejoran - los efectos en el hover por ejemplo - y recorriendolo, una tiene la sensación de una web profesional y hecha con esmero. 

El mayor problema en tu portfolio es que el responsive no funciona, lo que afecta negativamente tu nota a pesar de que se nota que pusiste esfuerzo en tu portfolio. Una web sin responsive no está completa: la mayoría de nuestros usuarios van a ver nuestra web desde el celular, por lo que es absolutamente necesario poder ofrecerles la misma experiencia a ellos. Noto el interés por hacer que el responsive funcione, por lo que me pregunto si lo que faltó es tiempo o si no pudiste resolver algunas cosas: si es el segundo caso, por favor, no dejes de consultarme. 

Te dejo varios comentarios para mencionar cositas puntuales. Como comentamos en clase, este trabajo no se hace para que constates conocimientos, sino para que aprendas: en ese sentido, mi intencion es que estos comentarios te sirvan para aprender, mejorar tu codigo a futuro e ir apreciando mejor qué se espera de nosotras como desarrolladoras front end.

## Estructura correcta de documento HTML

Tu HTML esta muy bien. Claro, prolijo, sin elementos de más, muy bien comentado. 

En `nav` tenes una `ul`, pero ningún `li`. Esto le quita todo el propósito a la lista: sin elementos, es lo mismo que la etiqueta no esté. 

## Respeta la consigna 

- El portfolio cuenta con las secciones solicitadas 

Cumplido

- Al clickear en los links de navegación, debe llevar a la sección correspondiente

No cumplido para "contacto" ni para los links del footer. 

- Al clickear en los links de contacto, debe llevar a la página externa
correspondiente 

Cumplido, excepto por el email. Para agregar un link a un email usa el atributo `mailto`: `<a href="mailto: vicky@gmail.com">Email</a>` 

- El portfolio debe tener un diseño responsivo y verse correctamente en distintos dispositivos 

No cumplido. Veo el intento, pero te juega en contra que muchas cosas faltan, y que otras estan mal planteadas. 

Lo que falta es, principalmente, una estrategia para hacer el diseño *responsivo* en oposición a hacerlo *visible en celulares*. Una web responsiva es una web que se adapta a cualquier tamaño de pantalla; idealmente, un diseño deberia adaptarse lo mas posible, pero esto no siempre es posible y por eso solemos enfocarnos en las pantallas mas habituales. Comenté en clase que la guia de bootstrap para las media queries me parece la mejor, te la dejo acá. Esto nos permite enfocarnos en los tamaños mas habituales, y a la vez asegurarnos de que no dejamos afuera a ningún dispositivo. 


```css
/* Celulares */
@media (max-width: 576px) { ... }

/* Celulares en modo horizontal y tablets pequeñas */
@media (max-width: 768px) { ... }

/* Tablets  */
@media (max-width: 992px) { ... }

/* Monitores pequeños */
@media (max-width: 1200px) { ... }

/* Monitores grandes */
@media (max-width: 1400px) { ... }
```

En tu caso, tenemos dos resoluciones: para escritorio, y para pantallas menores a 600px. Eso significa que todas las resoluciones entre 600px y 1000px no estan incluidas, y no se ven bien. 

Comenté en clase que celulares es lo que más importa, ya que allí están la mayoría de los usuarios. Por ese motivo que el punto anterior no sería tan importante si tu web funcionara bien en celulares. Lamentablemente no lo hace. 

La primera decisión cuestionable es que en celulares le diste al html un width de 200%. No puedo entender esta decision. Al decir esto, lo que decis es: mi pagina va a tener como ancho el doble del ancho que tiene la pantalla del celular de mi usuario. Estás asegurándote de que tu web *no* funcione. De hecho, sacando esa sola orden, el responsive mejora un montón. No deberíamos tocar el width del body o del html, salvo en diseños muy complejos y cuando estemos totalmente seguras de lo que estamos haciendo: cada pantalla tiene un width distinto en el body, y es correcto dejar que sea la pantalla la que nos guíe. 

Si sacamos ese width para el html tu responsive mejora un montón para pantallas de entre 500px y 600px. Esa es la absoluta minoría entre celulares: la mayoría están entre 360 y 440px. Pero aún no está perfecta incluso entre 500 y 600: notá en que en ese caso tenemos un scroll horizontal y lo que parece ser una barra blanca a la derecha. 

Este scroll horizontal es muy, muy habitual y muy molesto. Ocurre cuando un elemento ocupa mas espacio del que le da el body, ya sea por un width, un margin, un padding o la combinacion de los tres. Encontrarlo es dificil, requiere recorrer con paciencia cada uno de nuestros elementos. Pero es un ejercicio necesario. En tu caso, el culpable es el div "columnas flex" en la seccion "Mis conocimientos". Le diste en el css de escritorio un width de 1000px, y no le sacaste ese ancho fijo en la media query, por lo que sigue midiendo 1000px y rebalsando cualquier celular. Una vez solucionado eso (debería tener un width de 100%) hay otros elementos que siguen rebalsando, aunque de manera menos dramatica. Prestá atención a los margin y padding de tus elementos y fijate si podés encontrar cuales rebalsan: sino escribime y te los comento, pero creo que vale la pena que este ejercicio lo hagas vos. 

Una vez arreglado el problema de la resolucion entre 500 y 600px, te diria que te dediques a resoluciones menores. Toda pantalla de más de 320px debería verse bien en tu portfolio. Quizá necesites una segunda media query, y no hay problema si ese es el caso, pero idealmente todo debería estar contenido en tu media para celulares. No necesitas medidas fijas en celular: si tus tarjetas, por ejemplo, miden el 70% del ancho de la pantalla, van a verse bien en celulares muy pequeños y en celulares muy grandes. Esa misma estrategia podés utilizarla para el resto de los elementos. 


- El portfolio debe estar deployado y ser accesible desde una URL 

Cumplido. 

- El repositorio en GitHub debe tener un readme adecuado 

Cumplido. 

### Respeta el diseño dado 

Cumplido. 


### Buena estructura de proyecto 

Usás muchas imágenes en tu proyecto, y viéndolo a primera vista en github no es tan fácil ver cuáles son los archivos principales. Siempre que uses imágenes locales, como en este caso, agregalas a una carpeta que se llame por ejemplo "imgs", "imagenes" o "assets". De esta manera solo los archivos principales - html, readme y css - son los que están en la carpeta principal. La excepción a esta regla es el favicon, que siempre debería ir en la carpeta principal. 

### Código bien indentado 

Cumplido. 

### Comentarios que permiten mejorar la legibilidad del código 

Cumplido en HTML, ausente en CSS para separar las distintas secciones: es algo que ayuda mucho al lector para encontrar lo que busca. 

### Uso correcto de etiquetas semánticas 

Cumplido, excepto por el caso del ul que te mencioné más arriba. 

### Buenos nombres de clases 

Cumplido en general, pero evitá usar cosas como "seccion uno" y "seccion dos", ya que es mejor encontrar nombres descriptivos. Cuando decimos que un nombre de clase debe ser descriptivo, lo decimos en un sentido funcional: qué rol cumple este elemento en el código. Los colores de los elementos, su forma, su estilo, su posición, todas esas cosas pueden cambiar y efectivamente cambian todo el tiempo en las webs que hacemos. La sección que estaba a la arriba mañana estará abajo, por lo que "uno" y "dos" no son buenas guias. 

### Código CSS bien estructurado 

Cumplido. Noto muchos estilos innecesarios o confusos, que te voy indicando en tu archivo de css. 

### Reutilización de estilos 

Cumplido la mayoría de las veces, noto muchos intentos por reutilizar los estilos. La clase "flex" esta muy bien usada. A veces parecés olvidarlo, como en el siguiente caso: 

```css
.imagen-generador-de-memes,
.imagen-match,
.imagen-gastos,
.imagen-reuniones,
.imagen-app,
.imagen-peliculas {
    height: 180px;
    width: 200px;
}
```

Si estos elementos tienen exactamente los mismos estilos, por que tienen distintos nombres de clase? La idea de las clases es justamente que todos los elementos que son iguales tengan el mismo nombre de clase. Podrías haberle dado a cada uno de esos elementos el mismo nombre, "imagen-proyectos" por ejemplo, y sólo tendrías una clase para cada uno de ellos. No repetirnos a nosotras mismas es un principio muy importante en programación, porque en la repetición se encuentran buena parte de nuestros errores. Reutilizá tus clases siempre que puedas. 

Tenés una clase "icono" y una clase "icon": la segunda no la usas en CSS pero aparece en tu HTML. Ojo con eso. 


### Cumple con criterios básicos de accesibilidad 

- Los colores tienen un contraste adecuado 

Cumplido

- Las imágenes tiene el atributo `alt` que corresponde 

Está la intención, pero a fines prácticos esto está incumplido. Como vimos en clase el lector de pantalla dice "Imagen" antes de leerlo asi que agregar "imagen" es repetitivo y molesto para el usuario. En tu seccion para las imágenes de tus proyectos, el lector de pantalla diria: "Imagen: imagen portfolio. Imagen: imagen generador de memes. Imagen: imagen match". Una pésima experiencia para el usuario no vidente. 

El alt debe ser un texto que pueda leer el software, por lo que evitá guiones o simbolos que puedan confundir la lectura. Las descripciones deben ser adecuadas: "imagen match" o "imagen principal" no comunican nada, es casi mejor que no estén a que sean inadecuados. Tu imagen principal le comunica muchisimo a tus usurios videntes acerca de qué se trata esta pagina - una mujer programadora - y tu objetivo al agregar alt en las imagenes es comunicarle lo mismo, o lo más posible, a tus usuarios no videntes: "Mujer junto a un celular, una tablet y un monitor" identifica mejor la imagen y permite que todos entiendan qué es lo que querés comunicar. 


- Los íconos y elementos que no presentan texto agregan la información correspondiente por otros medios (etiquetas aria, texto oculto) 

Tenés aria-label en tus iconos, pero comentamos en clase que el lector de pantalla va a ignorar los iconos a menos que les agreguemos role="img" como atributo, así que a fines prácticos es lo mismo que si no estuviesen. 

- Los íconos y elementos que no necesitan ser anunciados por un lector de pantalla tienen la etiqueta aria
correspondiente 

No veo ejemplos en tu portfolio, pero tampoco veo que sea necesario. 

- Commits con mensajes adecuados 

Cumplido, noto muchos y buenos commits en tu proyecto, lo que siempre se agradece. 

- Cuenta con un favicon

Cumplido, aunque deberia llamarse favicon.ico, dado que ese es el nombre que van a buscar la mayoría de los servicios de hosting. 

### Nota: 7