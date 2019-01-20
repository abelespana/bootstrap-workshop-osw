##Intro: qué es Bootstrap
Es una librería para el desarrollo de proyectos front, enfocada en la maquetación de sitios web. Se compone principalmente de ficheros CSS y JavaScript, estos últimos centrados en la interacción con el DOM (carruseles, menús desplegables) y en la interacción con el usuario (funciones para autocompletar formularios, por ejemplo). 

Estas características hacen que Bootstrap no pueda estar -en mi opinión, pero lo que diga Adri- al mismo nivel que otros *framewors* de desarrollo Front como Angular, React o Vue, que por lo general nos aportan una visión más global del entorno de nuestro proyecto web (con métodos para obtener información, tratar esa información y mostrarla en el DOM, que es de lo que se trata al fin y al cabo). 

Cuando queramos usar Bootstrap en nuestro proyecto, tendremos que añadir el enlace a uno o varios ficheros CSS que contienen todos los estilos que necesitamos, aunque para ciertos efectos es necesario incorporar también la parte de JavaScript de Bootstrap, junto con otras dependencias (jQuery). 

Tenemos diferentes formas de incorporar Bootstrap a nuestro proyecto. La más rápida es añadir el enlace que encontramos directamente en la página web de Bootstrap, aunque esto importa toda la librería y perdemos la interesante opción de personalizar los estilos. 

Para adaptarlo a nuestras necesidades, será necesario descargarse el proyecto desde alguna de las múltiples opciones (GitHub, web oficial, NPM...) y tendremos acceso al código fuente, al que podemos meter mano si sabemos suficiente CSS y algo de Sass. 

**NOTA**: *Hasta donde yo sé, Bootstrap 4 ya usa solo Sass para precompilar, versiones anteriores creo que usaban Less pero no estoy seguro. Lo miraré*

## Breve historia de Bootstrap
Creado por Twitter a principios de esta década (2011). Se puede buscar alguna curiosidad interesante como empresas grandes que lo usan (habrá muchas digo yo), o cosas por el estilo (número de estrellas en Github, etc).  

## Cuándo usarlo
Bootstrap permite construir sitios web de forma rápida y muy muy flexible, con una clara orientación hacia el *mobile first* pero adaptable a medida que crece la pantalla. Es ideal para generar *layouts* y no tener que calcular a mano los diferentes puntos de ruptura (*breakpoints*) que se producen cuando cambiamos de dispositivo. 

Sin embargo, no solo se queda ahí y permite crear sitios web completos sin practicamente escribir una sola línea de CSS, ya que además de con unos estilos y líneas de diseño (tipografías, colores, tamaños de fuentes) cuenta con componentes como carruseles, formularios, menús desplegables. 

##Cuándo no usarlo
Dependiendo de las necesidades del proyecto (principalmente, del diseño que recibamos), podremos decidir si usar Bootstrap o no, o si usarlo solo parcialmente. Es bastante frecuente encontrar con que podemos usar solo una parte de la librería CSS (principalmente el grid o rejilla) o por el contrario recurrir a solo algún elemento concreto (un carrusel, por ejemplo). 

## Funcionamiento general
Bootstrap se compone de clases de CSS. Estas clases llevan aparejadas unos estilos concretos que son los que interpreta el navegador y aplica a nuestro HTML, como haría con cualquier otro elemento clase de CSS. Es importante, eso sí, respetar la estructura HTML que Bootstrap emplea porque de lo contrario algunos estilos pueden no aplicarse bien. 

Especialmente con los componentes como menús de navegación, ventanas desplegables o carruseles, es recomendado copiar el ejemplo HTML que Bootstrap nos ofrece en su documentación y no alterarlo. 

## Grids, container, row y columnas
Bootstrap popularizó un *layout* dividido en 12 columnas. Nosotros podemos decidir cuantas columnas ocupa cada elemento en cada momento, con un máximo de 12. También podemos establecer márgenes por la izquierda que nos permitirá alinear el contenido como queramos en el eje horizontal X. 

**NOTA**: *En un ejemplo práctico, añadir un elemento que ocupe 6 columnas y que deje 3 de margen por la izquierda, que se verá centrado. O los valores que queramos, pero vamos, un ejemplo sencillote de este tipo*

Las columnas en Bootstrap tienen un ancho fijo, como si diéramos a un elemento un ancho fijo de, por ejemplo, `500px` o de un 20% de su contenedor. No es recomendable dar un ancho fijo a los elementos si queremos que nuestro diseño sea flexible (es decir, que se vaya adaptando al ancho de la pantalla), pero sí es válido usar los porcentajes como medida relativa al tamaño de un padre para lograr justo ese efecto de tamaño que responde al cambio del ancho de la pantalla. 

**NOTA**: *No sé hasta que punto se puede añadir aquí un ejemplo sencillo, demostrando que es difícil (por no decir imposible) colocar elementos con anchos fijos y que quede aquello alineado. Es algo básico pero igual así a la gente le queda más claro las ventajas que aporta Bootstrap y en última estancia Flex*

En anteriores versiones de Bootstrap, las columnas tenían un ancho fijo conforme el ejemplo que acabamos de ver. En la versión más reciente, de la 4 para arriba, Bootstrap utiliza Flex para distribuir los elementos... En última estancia, sigue funcionando básicamente igual: un ancho para determinar el tamaño de los elementos y un `margin-left` para dejar espacio por la izquierda, lo que permite centrar elementos si hacemos una sencilla resta. 

**NOTA**: *Claro, aquí ahora está la cosa de si explicar un poco Flexbox por encima o lo que sea. Depende de como veamos que se nos queda de largo, pero me preocupa liar a la gente con propiedades diferentes*

Sin embargo, el tamaño fijo de las columnas de Bootstrap y de los `offset` (márgenes) viene determinado por el padre. Si no tuviese un padre con un ancho concreto, el tamaño de elemento siempre sería relativo al body. Aquí es donde entran en juego los elementos con la clase `container`. 

Al final el contenedor solo sirve para eso. Es un elemento padre que tiene un ancho fijo. Este ancho va cambiando según cambia el tamaño de la pantalla (el responsive de toda la vida, vamos) y es la referencia que emplean las columnas para ubicarse (porque recordemos que las columnas usan un porcentaje al fin y al cabo). El container es la "magia" de Bootstrap, vamos. Si queremos un sitio lo más adaptable posible tenemos como alternativa la clase `container-fluid`, que ocupa el 100% del `body`. 

Justo por debajo del `container` tenemos la clase `row`, que en Bootstrap 4 se encarga de evitar que los elementos se posicionen respetando el ancho uno del otro, porque de lo contrario al ser una clase `flex` tendrían a hacerse más pequeños para que cupiesen todos. 

**NOTA**: *Esto hay que explicarlo con ejemplos porque madre mía lo sencillo que es y el jaleo que parece*

## Media queries, responsive y mobile first
Al final la magia no existe y la única forma de cambiar las propiedades CSS de cualquier elemento en función de unos condicionantes son las @media queries. Tenemos pseudoselectores y demás, pero esa es otra historia. 

Una media querie es una condicion que admite varios parámetros, aunque nos vamos a centrar en los `max-width` y los `min-width`, porque es lo que nos ocupa ya que Bootstrap se centra en el layout horizontal. *Menos bla bla y más ejemplos leñe*

Boostrap trabaja por debajo con media queries y decimos que es mobile first porque se estructura con `min-width`, es decir, que el ancho de los elementos se va modificando en función de cuando crece la pantalla, pero lo que se aplica por defecto si no usamos ninguna clase es la vista móvil. *Esto creo que vale también para los tamaños de tipografía y demás, pero tendría que asegurarme.* 

Una vez comprendido esto, solo debemos ir calculando el número de columnas que queremos que ocupe cada elemento e ir aplicando clases. Si tenemos la clase `col-lg-12` establecemos que con un `min-width` de 992px (pantallas grandes para Boostrap, ya no son tablets ni móviles) ese elemento tendrá un valor del 100% para la propiedad `flex-basis`. Nuevamente, todo esto con ejemplos ya se va viendo. 

## Bootstrap y flex
Al adoptar flex y sus diferentes propiedades para justificar o alinear contenido en los distintos ejes, Bootstrap ha importado muchas de esas propiedades. Ya que vamos a explicar Bootstrap y flex de pasada, igual merece la pena hacerle un hueco a todos estas clases que Bootstrap introduce que son poco más que valores flex, pero así la gente aprende a centrar elementos, etc. 

## Tipografías, etc. 
Aquí contamos el funcionamiento de la tipografía, y de algunas propiedades que van vinculadas al tamaño de letra, por ejemplo los padding relativos, y luego algunas clases auxiliares como las de centrar texto y demás, aunque algunas de estas van incluidas también en el apartado anterior donde hablamos de flex. 

## El resto de Bootstrap, más orientado a componentes
Esta es, en mi opinión, la parte más visual y que produce efectos más "cuquis" (carruseles, menús desplegables, animaciones en botones, etc) pero la más coñazo de trabajar con ella. Hay que respetar la estructura del HTML, que es lógico, pero eso a veces lo hace inflexible. Por otro lado, es posible que yo tenga prejuicios porque esta parte la he usado menos, tendría que coger 3 o 4 de los componentes más famosos y ver un poco puntos positivos y negativos. 

## Como personalizar
Esta parte dependerá del nivel de la gente, yo creo, porque si no saben Sass será necesario explicarlo un poco por encima. En todo caso, podemos descargar Bootstrap el código fuente y preparar unos cuantos ejemplos de como modificaríamos un valor (por ejemplo, un color del botón de la clase `btn-danger` o una cosa así que sea fácil de localizar). 

Hay que diferenciar además entre personalizar (cambiar un estilo, importar solo una parte de Bootstrap) o pisar estilos (por ejemplo, cambiar un color directamente con otra clase en nuestro CSS enlazado después). Esto sería cuestión de poner ejemplos y ver en que casos se puede hacer uno y en que casos se puede hacer otro, pero también puede ser el inicio de un apartado de buenas prácticas que sirva para cerrar el taller. 